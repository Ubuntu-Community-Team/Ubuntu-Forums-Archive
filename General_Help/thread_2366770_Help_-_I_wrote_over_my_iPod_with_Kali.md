---
title: "Help - I wrote over my iPod with Kali"
date: 2017-07-21
forum: General Help
---

### Post by Rick St. George on 2017-07-21
HELP ... I screwed up!

Was making a bootable USB stick with Kali.iso file, using DD in terminal.
At the same time I was charging my iPod. I wrote over my iPod.

Any ideas how to get it back?  

I get the following message is it will not mount.

> 
Error mounting /dev/sdc1 at /media/stephen/Kali Live: Command-line `mount -t "iso9660" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500" "/dev/sdc1" "/media/stephen/Kali Live"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.


thanks!
Rick

---

### Post by oldos2er on 2017-07-21
Please post the full dd command you ran.

---

### Post by Rick St. George on 2017-07-21
```
ddif=kali-linux-2017.1-i386.iso of=/dev/sdc bs=512k
```

Note: it should've been to /dev/sdd

---

### Post by Rick St. George on 2017-07-21
Fortunately I have Win7 on my Laptop. Installed iTunes and restored it automatically.
Sorry for any inconveinance. Case closed.

---

