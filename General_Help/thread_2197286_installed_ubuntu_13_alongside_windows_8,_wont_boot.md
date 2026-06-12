---
title: "installed ubuntu 13 alongside windows 8, wont boot ubuntu anymore"
date: 2014-01-03
forum: General Help
---

### Post by jaredwanders on 2014-01-03
i tried the ubuntu boot repair, it would not load upon boot, if i enter the boot menu no matter what i choose it loads windows.  confused, and want the use of the other half of my computer back.  any help is much appreciated, thank you.

---

### Post by PopsTheSailor on 2014-01-05
During boot up, you might have to change your system to boot off of the DVD driver before the hard drive. That way Boot Repair hopefully will boot up and you can fix it.

---

### Post by Bucky Ball on 2014-01-05
Booted from the Ubuntu LiveDVD, run these commands in a terminal:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair  
sudo apt-get update
sudo apt-get install boot-repair
```

Boot Repair is now in your applications. Find it, launch it, choose the 'Recommended' option. You can also create a Boot Repair CD and boot from that, changing the BIOS to boot from the optical drive as advised previously. Get the CD ISO from the first link here: 

Get Boot Repair:
[http://sourceforge.net/projects/boot-repair/?source=directory](http://sourceforge.net/projects/boot-repair/?source=directory)

Use BR:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread (BR creator):
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

