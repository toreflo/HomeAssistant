+-------------------------+
|  Shelly MQTT info       |
+-------------------------+

Shelly will subscribe to the following topics, accepting commands:
  - shellies/command which can be used to send a "broadcast" command to all devices on this MQTT exchange
  - <topic_prefix>/command where <topic_prefix> is usually unique per device
  - <topic_prefix>/command/<component:id> where individual components accept specific commands
   
Shelly publishes on:
  - shellies/announce Shelly's device info in response to announce
  - <topic_prefix>/status the entire device status as response to status_update published on <...>/command
  - <topic_prefix>/announce Shelly's device info in response to announce
  - <topic_prefix>/status/<component:id> the entire component status
  - <topic_prefix>/error/<component:id> an informative error message if an MQTT command could not be processed
  
Commonly-accepted commands are:
  - status_update to trigger the component to publish it's status
  - announce - causes information as returned from Shelly.GetDeviceInfo to be published on the announce topics

Ex, to get IP addr: publish "announce" on topic "shellies/shelly1-lucina/command"