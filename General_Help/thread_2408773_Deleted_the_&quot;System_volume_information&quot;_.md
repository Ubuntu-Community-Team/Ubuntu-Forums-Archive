---
title: "Deleted the &quot;System volume information&quot; folder from my USB"
date: 2018-12-22
forum: General Help
---

### Post by kaur99 on 2018-12-22
Hello,im on Ubuntu 16.I accidentally deleted the system volume information from my USB and then did a quick format.Now im unable to use my USB,plugging in the USB shows:
Error mounting /dev/sdb1 at /media/amandeep/Kali Live: Command-line `mount -t "iso9660" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500" "/dev/sdb1" "/media/amandeep/Kali Live"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.


a friend had used my usb before to load kali in his system,pretty sure kali is just in the name now.Need urgent help.Thanks.

---

### Post by Impavidus on 2018-12-23
Something went wrong when formatting the usb drive. Have you tried gparted to format it again? Maybe you first have to wipe the first megabyte. [mkusb](https://help.ubuntu.com/community/mkusb) has a safe option for that.

---

