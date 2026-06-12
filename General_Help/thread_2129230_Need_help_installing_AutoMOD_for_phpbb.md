---
title: "Need help installing AutoMOD for phpbb"
date: 2013-03-25
forum: General Help
---

### Post by Zukaro on 2013-03-25
I tried following the FAQ posting on installing AutoMOD but it's not working.  I put all the files from AutoMOD into /etc/phpbb3.

I tried connecting to mydomain.com/phpbb/install and that didn't work, so then I tried mydomain.com/phpbb/install/index.php and that still didn't work (I got a 404 for each).  I looked under /var and /var/www to see if I could find phpbb (rather than phpbb3) but I was unable to, so I'm not sure if I'm just putting it in the wrong directory or if I did something wrong.

I think there could be a problem with the permissions (as last time I copied something over via FTP the permissions didn't allow it to actually function), but I went through those and changed them.

All directory permissions are: drwxrwxr-x
All file permissions are: -rw-rw-r--

Before the change directory permissions were: drwx------
And file permissions were: -rw-------

Also, I'm running this under Ubuntu Server 12.10 (64bit), under Proxmox on a virtual machine (although I think the part about Proxmox is irrelevant).  It's running on my own machine (so I only have the FTP server I set up using vsftpd, and that only goes to my user's home directory).  I access the machine via SSH but do have physical access (physical access will only be useful for Proxmox however).  But in Proxmox there is a VNC viewer (or something like that); basically it lets me view the console without SSH (as if I was at the physical machine).

This is what's in the phpbb3 directory (before installing AutoMOD):
```
database.inc.php
language
styles
apache2.conf
```

And then after (so you can see the stuff I added and how I added it):
```
adm
database.inc.php
docs
install
language
README.md
styles
apache2.conf
develop
includes
install_mod.xml
modx.prosilver.en.xsl
store
umil

```

---

