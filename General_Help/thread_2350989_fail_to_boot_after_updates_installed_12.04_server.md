---
title: "fail to boot after updates installed 12.04 server"
date: 2017-01-29
forum: General Help
---

### Post by fatmann66 on 2017-01-29
I appreciate any suggestions in how to resolve this issue.

installed updates and rebooted  a few days later. 

server is running FDE and normally boots to a prompt to decrypt drive.

instead I get the  attached 

ran boot repair disk.  and rebooted not change. see link for info collected by tool:  [http://paste.ubuntu.com/23891577/](http://paste.ubuntu.com/23891577/)

thanks in advance.
Fatmann66
[ATTACH=CONFIG]273442[/ATTACH]

---

### Post by fatmann66 on 2017-01-30
booted from a live CD and I can decrypt my drives and access them

checked /var/log/syslog and /var/log/kern.log  both  indicated a shutdown; which makes sense as  that was the last thing that happened before  sda5 was encrypted  on shutdown.  

I'm able to see the boot partition1 it mounts as /mnt/boot-sav/sda. not sure where to go from here as I ran the automatic boot repair and it didn't resolve the problem.

anyone have any suggestions?

---

