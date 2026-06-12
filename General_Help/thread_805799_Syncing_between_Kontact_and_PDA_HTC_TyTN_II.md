---
title: "Syncing between Kontact and PDA HTC TyTN II"
date: 2008-05-24
forum: General Help
---

### Post by jeroenvrp on 2008-05-24
My father and I are trying to achieve a connection/sync between Desktop Kubuntu Hardy & PDA HTC TyTN II (WM). Without positive results unfortunately. 
Could you please help us in the right direction.

When we did a lsusb the device is recognized. 

We followed the procedures in: [www.synce.org/moin/SynceWithUbuntu]("http://www.synce.org/moin/SynceWithUbuntu") 

The mainscreen ¨SynCE KDE PDA Manager¨ presented ´Make sure Sync-Engine is 
running...´ When starting "sync-engine" manually in a terminal that message went away.

We were able to capture the following information with "msynctool ----sync ": The most important info is (I think): "Unable to connect one of the members".
 
Below you will find the beginning of the output followed by the end of same 
output.
The part in between was a lot of the same type of lines.

Beginning of output:

```
DEBUG:SynCE:Connect() called
DEBUG:SynCE:get_changeinfo() called
DEBUG:SynCE:slow sync requested for Contacts
DEBUG:SynCE:slow sync requested for Calendar
DEBUG:SynCE:slow sync requested for Tasks
INFO:SynCE:initiating device synchronization
DEBUG:SynCE:disconnect() called
Synchronizing group "synce-sync" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type synce-opensync-plugin just connected
Member 2 of type kdepim-sync just connected
All clients connected or error
Received an entry 0wCAsaunG1 with data of size 4 from member 2. Changetype 
ADDED
Received an entry 1dj3H3acIy with data of size 4 from member 2. Changetype 
ADDED
Received an entry 1lie1DpEx4 with data of size 4 from member 2. Changetype 
ADDED
Member 1 of type synce-opensync-plugin had an error while getting changes: 
Error during get_changeinfo() method
Member 1 of type synce-opensync-plugin just disconnected
Received an entry 2P8l2wKr4T with data of size 4 from member 2. Changetype 
ADDED
Received an entry 4wLa7JqYhj with data of size 4 from member 2. Changetype 
ADDED
Received an entry 5tPO3Hp5FU with data of size 4 from member 2. Changetype 
ADDED
Received an entry 79QdB0u8sF with data of size 4 from member 2. Changetype 
ADDED
Received an entry 7uE38E3foJ with data of size 4 from 
```

>> deleted part/ many equal looking lines <<

```
eceived an entry libkcal-1543078262.968 with data of size 4 from member 2. 
Changetype ADDED
Member 2 of type kdepim-sync just sent all changes
Member 2 of type kdepim-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error synchronizing: Unable to read from one of the members
```

Following info might also be usefull?

:~$ sync-engine

```
SynCE sync-engine starting up
2008-05-21 22:51:55,792 DEBUG syncengine : running main loop
2008-05-21 22:51:55,793 DEBUG syncengine : creating SyncEngine object
2008-05-21 22:51:55,829 INFO engine.syncengine.kernel : __init__: connected 
devi
ce found
2008-05-21 22:51:55,829 INFO engine.syncengine.kernel : _CBDeviceConnected: 
devi
ce connected at 
path /org/synce/odccm/Device/_68101334_D467_9DD4_F5AC_EBE9A708FA
44_
Entity: line 109: parser error : Comment not terminated
<!-- <AutoSyncCommand>xterm -e msynctool
                        <!-- <AutoSyncCommand>xterm -e msynctool --sync 
wm5sync<
/AutoSyncCommand> -->
                                                                 ^
2008-05-21 22:51:55,844 DEBUG syncengine : installing signal handlers
2008-05-21 22:54:17,060 INFO engine.syncengine.kernel : _CBDeviceDisconnected: 
d
evice disconnected from 
path /org/synce/odccm/Device/_68101334_D467_9DD4_F5AC_EB
E9A708FA44_
2008-05-21 22:54:17,081 INFO engine.syncengine.kernel : _CBDeviceDisconnected: 
i
gnoring non-live device detach
2008-05-21 23:13:46,671 INFO engine.syncengine.kernel : _CBDeviceConnected: 
devi          ce connected at 
path /org/synce/odccm/Device/_68101334_D467_9DD4_F5AC_EBE9A708FA          44_
Entity: line 109: parser error : Comment not terminated
<!-- <AutoSyncCommand>xterm -e msynctool
                        <!-- <AutoSyncCommand>xterm -e msynctool --sync 
wm5sync<          /AutoSyncCommand> -->
                                                                 ^
2008-05-21 23:13:46,672 ERROR dbus.connection : Exception in handler for D-Bus 
s          ignal:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 214, in 
mayb          e_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/SyncEngine/kernel.py", line 186, in 
_CB          DeviceConnected
    self.config.UpdateConfig()
  File "/usr/lib/python2.5/site-packages/SyncEngine/config.py", line 344, in 
Upd          ateConfig
    confdoc = libxml2.parseDoc(cf)
  File "/var/lib/python-support/python2.5/libxml2.py", line 1264, in parseDoc
    if ret is None:raise parserError('xmlParseDoc() failed')
parserError: xmlParseDoc() failed
```

---

