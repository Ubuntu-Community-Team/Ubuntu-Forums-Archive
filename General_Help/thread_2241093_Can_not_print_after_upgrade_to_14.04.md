---
title: "Can not print after upgrade to 14.04"
date: 2014-08-24
forum: General Help
---

### Post by nederbelg on 2014-08-24
Hi,

After upgrading to ubuntu 14.04 I can not print anymore...
I have installed Cups again. But when going to System Settings > Printers it says that the Printing Service is not available.

Here some ouput generated at the command line. (I did some searching, but the info is already beyond my understanding):

me@ubuntu-studio-1:~$ sudo ps -ae | grep cups
[sudo] password for me: 
 1293 ?        00:00:00 cups-browsed
me@ubuntu-studio-1:~$ sudo cat /var/log/dmesg | grep 'cups'
[    5.421040] type=1400 audit(1408868853.000:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=925 comm="apparmor_parser"
[    5.421044] type=1400 audit(1408868853.000:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=925 comm="apparmor_parser"
[    5.421296] type=1400 audit(1408868853.000:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=925 comm="apparmor_parser"
[    5.436402] init: cups main process (930) terminated with status 1
[    5.436407] init: cups main process ended, respawning
[    5.438804] init: avahi-cups-reload main process (958) terminated with status 1

Thanks in advance for your help!

---

### Post by kc1di on 2014-08-24
can you go to a browser FireFox or chromium and in the address line type the following.
```
localhost:631
```

see if that brings you to the cups page?
if it does try re-installing your printer under CUPS for Administrator column  add printer button on that page. follow the instruction given. (it may ask for your password)
if it adds your printer go to Printers tab
under maintenance button click print test page. 
see if it works.

---

### Post by nederbelg on 2014-08-24
Dave,

Firefox gives the following error message:

Unable to connect
Firefox can't establish a connection to the server at localhost:631.

Regards,
Bert

---

### Post by nederbelg on 2014-08-25
I noticed I didn't have a cupsd.conf file. I copied a cupsd.conf (for wrong cups version) file from some internet post. That way I could connect using localhost:631. There I changed to the default cupsd.conf file for my cups version (1.7).
Trying to print a testpage I noticed a filtererror for my lexmark prevail 705 driver. I removed the printer and drivers and tried to reinstall.

The Ubuntu Software Center (14.04) states:
There isn’t a software package called “lexmark-inkjet-legacy” in your current software sources.

Whereas it was present under 12.04.

So I downloaded the driver from the lexmark site. There I had to choose 12.04, since 14.04 wasn't listed.
Installing lexmark-printer-utility-1.0-2.i386.deb with the software center, I get the error: 
```
The package is of bad quality; Lintian check results for /tmp/lexmark-printer-utility-1.0-2.i386.deb:
E: lexmark-printer-utility: control-file-has-bad-owner postinst root/bin != root/root 
E: lexmark-printer-utility: control-file-has-bad-owner prerm root/bin != root/root 
```

The same happens with the ppd-file, lexmark-inkjet-legacy-1.0-1.i386.deb

Looking forward to your suggestions!
bert

---

