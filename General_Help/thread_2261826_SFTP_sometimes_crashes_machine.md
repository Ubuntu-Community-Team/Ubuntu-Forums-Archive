---
title: "SFTP sometimes crashes machine"
date: 2015-01-21
forum: General Help
---

### Post by brendand2 on 2015-01-21
I inherited responsibility for a budget file server of sorts, an old pc with three 4TB ext4 formatted external usb drives, Kubuntu 12.04 LTS.  Occasionally(but too frequently for comfort) the machine crashes when sftp is being used to transfer files, both pushing to another server, and being pulled(from yet another server). The file sizes are 1-4GB. The crash forces me to cold reboot the machine.

The last line in the syslog before crashing was:
```
Jan 20 14:50:28 georgs avahi-daemon[954]: Invalid response packet from host ...
Jan 20 14:50:41 georgs avahi-daemon[954]: Invalid response packet from host ...
```
However, this message also appears even when the stfp transfer does not result in a crash.
Does anyone have any suggestions on how I might further diagnose this issue?

Thanks

---

### Post by TheFu on 2015-01-21
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=556461](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=556461) seems to be a known bug, but it probably isn't impacting your system, based on all the other reports about it and nobody else locking up.
I've seen where some NICs are crashed by certain traffic - often VoIP traffic hitting the interface.   [http://blog.krisk.org/2013/02/packets-of-death.html](http://blog.krisk.org/2013/02/packets-of-death.html) explains more and has links for where to start with research.

Can you switch from sftp to scp?  They do encryption differently with scp designed for streaming, I believe, so it should be a little less overhead.

BTW, I own a NIC that can be crashed. To avoid it, I moved out VoIP equipment to a different subnet as a precaution. It never crashed here.

---

### Post by brendand2 on 2015-01-21
Thanks. This machine is only used for file storage, so VoIP does not factor in. I can ask users to use scp(or rsync) and see if that helps.

---

