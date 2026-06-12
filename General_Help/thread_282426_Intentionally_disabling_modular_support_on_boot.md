---
title: "Intentionally disabling modular support on boot"
date: 2006-10-22
forum: General Help
---

### Post by jaradronald on 2006-10-22
Who can tell me how to remove the automatic module support for the following (or disable the autoloading of the drivers on boot):
 
pcmcia services
scsi services
firewire services
hp printing
cups
 
I don't use any of these sub-systems on my "Oldworld" G3 Powerbook, and I want to disable them on the boot to decrease my boot time and free up some system RAM. I'm thinking it has something to do with /etc/init.d but I'm just saying that because that's how I start/stop my system services (ftp, http, ssh, etc...). :-k Not sure if the pcmcia services are related to other 'daemons' in their load processing.
 
I could uninstall the modules using apt-get, but i dont' necessarily want to remove the driver support, just disable it on boot since none of my sub-systems are currently using it.
 
And FYI, I don't need a lecture about how USB uses SCSI or how my hard drive might be firewire... Thanks for the info, but I know my sub-systems well enough to see what drivers I need and which I don't. And on the bright side, even if I do break something I can always just go back and re-enable the module from the shell (or undo whatever it is I need to do in the first place).
 
Much appreciated!

---

### Post by lloyd_b on 2006-10-22
> Who can tell me how to remove the automatic module support for the following (or disable the autoloading of the drivers on boot):

pcmcia services
scsi services
firewire services
hp printing
cups

I don't use any of these sub-systems on my "Oldworld" G3 Powerbook, and I want to disable them on the boot to decrease my boot time and free up some system RAM. I'm thinking it has something to do with /etc/init.d but I'm just saying that because that's how I start/stop my system services (ftp, http, ssh, etc...). Not sure if the pcmcia services are related to other 'daemons' in their load processing.

Take a look at this HowTo:

[http://www.ubuntuforums.org/showthread.php?t=89491]("http://www.ubuntuforums.org/showthread.php?t=89491")

Lloyd B.

---

### Post by az on 2006-10-22
> **jaradronald said:**
> Who can tell me how to remove the automatic module support for the following (or disable the autoloading of the drivers on boot):
 
pcmcia services
scsi services
firewire services
hp printing
cups
 
I don't use any of these sub-systems on my "Oldworld" G3 Powerbook, and I want to disable them on the boot to decrease my boot time and free up some system RAM. I'm thinking it has something to do with /etc/init.d but I'm just saying that because that's how I start/stop my system services (ftp, http, ssh, etc...). :-k Not sure if the pcmcia services are related to other 'daemons' in their load processing.
 
I could uninstall the modules using apt-get, but i dont' necessarily want to remove the driver support, just disable it on boot since none of my sub-systems are currently using it.
 



If you have a pcmcia bus on your computer, you can find which module it is and then blacklist it (/etc/modprobe.d)  The same goes for scsi and firewire, but that will hardly save you any ram.  Maybe a few k.  

Hp and cups are not kernel modules, but services that you can dissable as noted above.

---

