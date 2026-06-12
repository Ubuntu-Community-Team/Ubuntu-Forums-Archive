---
title: "Boot.ini error - Win2k/Ubuntu dual boot"
date: 2008-01-30
forum: General Help
---

### Post by equality7 on 2008-01-30
Sorry if this one has been posted and solved before... On start-up I'm getting a boot.ini error and Windows automatically starts, no choice of OS can be made. I'm running Win2k and downloaded Wubi from Cnet, not sure which version of Ubuntu I have now. I've had it for awhile and made multiple updates.

Here is my boot.ini file:

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect
C:\="Microsoft Windows" 
c:\grldr="Ubuntu"

Is this how the boot.ini should appear?

---

### Post by logos34 on 2008-01-30
take out the line

C:\="Microsoft Windows" 

see if that helps

---

