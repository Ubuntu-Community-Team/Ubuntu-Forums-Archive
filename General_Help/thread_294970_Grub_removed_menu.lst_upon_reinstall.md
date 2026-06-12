---
title: "Grub removed menu.lst upon reinstall"
date: 2006-11-07
forum: General Help
---

### Post by jaywhy13 on 2006-11-07
I tried to install lilo using liloconfig and it returned an error. So before I rebooted I ran grub-install /dev/sda and rebooted.

No apparently my menu.lst file is gone and grub gives me this primitive menu. 
I tried rescue mode from the breezy cd since it's the only one that allows me to reinstall grub without asking questions. 

When I get a rescue shell and type grub-install /dev/sda I get
grub-probefs: error: Cannot get the real path of '/dev/sda'
Auto-detection of a file system module failed
Please specify the module with the option --modules explicitly...
I have NO clue what that means

Please help.... Got an assignment working on and I need Grub to be back up!!!!! Pleassseeeeeeee  :confused:

---

### Post by jaywhy13 on 2006-11-07
Oh ... its the command line that comes up... just the command line alone loads up

---

### Post by jaywhy13 on 2006-11-07
can anyone assist...??? this is REALLY important

---

### Post by Bigbluecat on 2006-11-07
Try the following guide from Herman:

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

And i recommend keeping a copy of Super Grub Disk handy:

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

---

### Post by jaywhy13 on 2006-11-07
> **Bigbluecat said:**
> Try the following guide from Herman:

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

And i recommend keeping a copy of Super Grub Disk handy:

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

Iiite... I got grub reinstalled and stuff... but grub refuses to use the configfile at /boot/grub/menu.lst. I have to manually load it using "configfile ..." and then choose my OS

---

### Post by jaywhy13 on 2006-11-08
Thanks guys... it's working some how now

---

