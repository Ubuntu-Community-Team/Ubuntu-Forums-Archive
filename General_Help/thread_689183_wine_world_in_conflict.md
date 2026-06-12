---
title: "wine world in conflict"
date: 2008-02-06
forum: General Help
---

### Post by rmahnovetsky on 2008-02-06
I'm trying to run world in conflict in wine and, I'm getting the error message below does anyone know what could be causing this issue?

/media/OS/Program Files/Sierra Entertainment/World in Conflict$ wine wic.exe
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:win:EnumDisplayDevicesW ((null),0,0x35ce7d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x35ce7d0,0x00000000), stub!
wine: Call from 0x7b840b14 to unimplemented function d3d10.dll.D3D10CreateDevice, aborting
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xab25b0

---

### Post by soxs on 2008-02-06
Did you allready read, what other usaers did to make it run? [http://appdb.winehq.org](http://appdb.winehq.org) (atm offlne)
It's required to use certain additional DLLs and turn off dx10.
which you can read out off: wine: Call from 0x7b840b14 to unimplemented function d3d10.dll.D3D10CreateDevice, aborting
Atm I can't you help furthermore, you have to wait until appdb is up again.

---

### Post by geirha on 2008-02-06
Google has it cached ;)

[http://64.233.183.104/search?q=cache:9xGEV4KRCjwJ:appdb.winehq.org/objectManager.php%3FsClass%3Dversion%26iId%3D9237+wine+world+in+conflict&hl=en&ct=clnk&cd=1](http://64.233.183.104/search?q=cache:9xGEV4KRCjwJ:appdb.winehq.org/objectManager.php%3FsClass%3Dversion%26iId%3D9237+wine+world+in+conflict&hl=en&ct=clnk&cd=1)

---

