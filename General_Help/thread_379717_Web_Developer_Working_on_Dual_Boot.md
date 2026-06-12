---
title: "Web Developer Working on Dual Boot"
date: 2007-03-08
forum: General Help
---

### Post by breezey on 2007-03-08
Hi all,

I have Ubuntu Edgy and Windows XP install as dual boot on my PC. I am a web developer and have a apache server installed on both Ubuntu and Windows XP. My problem is: sometime I work on one OS and another time on another OS. How could I make my files on httpdocs always synchronized? Seems that by default ubuntu only have read access to ntfs partition and Windows XP doesn't even read linux partition.

Any suggestion? I am thinking about having remotely hosted repository (svn or cvs)... is there any free provider of such thing? Thank you.

---

### Post by indytim on 2007-03-08
I don't know if this would work for your application or not.  Moving your Windows servers to a FAT32 partition get you there?

IndyTim

---

### Post by breezey on 2007-03-08
thanks for your reply indytim... but I don't really want to make any change on my windows file system... if I don't really have to.

---

### Post by schwascore on 2007-03-08
Why not try using a USB Flash drive?  It should work for both OS's.

---

### Post by seldenthuis on 2007-03-08
You could also install the drivers from the Linux-NTFS project:
```
sudo apt-get install ntfs-3g
```
If you then change the file system in /etc/fstab from ntfs to ntfs-3g, you have write access  on your Windows partition.

---

