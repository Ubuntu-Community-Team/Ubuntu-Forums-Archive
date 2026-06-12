---
title: "How to start tftpd-hpa at boot time?"
date: 2013-02-11
forum: General Help
---

### Post by DavidA2011 on 2013-02-11
Hi
 
I am running Ubuntu 12.04 LTS. I have configured tftpd-hpa to provide a tftp server on this o/s. I start the service as follows:
 
[FONT=Calibri]$ sudo service tftpd-hpa restart[/FONT]
 
[FONT=Calibri]and the server works ok.[/FONT]
 
[FONT=Calibri]How can I configure this service to start automatically at boot time please?[/FONT]
 
[FONT=Calibri]BR[/FONT]
 
[FONT=Calibri]David[/FONT]

---

### Post by Bufeu on 2013-02-11
> **DavidA2011 said:**
> Hi
 
I am running Ubuntu 12.04 LTS. I have configured tftpd-hpa to provide a tftp server on this o/s. I start the service as follows:
 
[FONT=Calibri]$ sudo service tftpd-hpa restart[/FONT]
 
[FONT=Calibri]and the server works ok.[/FONT]
 
[FONT=Calibri]How can I configure this service to start automatically at boot time please?[/FONT]
 
[FONT=Calibri]BR[/FONT]
 
[FONT=Calibri]David[/FONT]Use rc.local: [http://porteus.org//tutoriels/47-porteus-tweaks/133-howto-tweak-your-boot-up-with-rclocal.html](http://porteus.org//tutoriels/47-porteus-tweaks/133-howto-tweak-your-boot-up-with-rclocal.html)

---

### Post by Bufeu on 2013-02-11
Add the commands to the file (rc.local) you want to ran at startup. **All the commands in rc.local will run at root.**

---

### Post by DavidA2011 on 2013-02-12
Thanks for your replies.
 
I added:
 
service tftpd-hpa restart 
 
to rc.local as suggested.  After I reboot, the service is running as expected (verified by running status).  However, the tftp server does not then work.  I have to run:
 
sudo service tftpd-hpa restart 
 
from the command line and then the server works.
 
Any suggestions what is going on here please? 
 
David

---

### Post by DavidA2011 on 2013-02-12
Turns out this is a known bug:
 
[https://bugs.launchpad.net/ubuntu/+source/tftp-hpa/+bug/522509](https://bugs.launchpad.net/ubuntu/+source/tftp-hpa/+bug/522509)
 
I changed the entry in rc.local to:
 
[FONT=Courier New]sleep 30[/FONT]
[FONT=Courier New]service tftpd-hpa restart[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New][FONT=Tahoma][SIZE=2]and it now works.[/SIZE][/FONT][/FONT]

---

