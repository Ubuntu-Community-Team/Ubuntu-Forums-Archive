---
title: "Can I restore from a backup made using a previous version of Ubuntu"
date: 2019-03-13
forum: General Help
---

### Post by jbh54enwiler on 2019-03-13
My PC's hard drive is showing signs of serious wear.  I'm planning on buying a new hard drive soon, but just in case I don't get around to it before Ubuntu 19.04 drops, I want to know if it's possible to restore (Onto a new hard drive) a backup of Ubuntu 18.10 onto a new 19.04 system without messing anything up.

---

### Post by HermanAB on 2019-03-13
Yes you can.

However, it is usually much easier and faster to do a fresh install than to install and old and tired backup.

---

### Post by monkeybrain20122 on 2019-03-13
Yes create a backup with fsarchiver (in the repo) then just restore the .fsa file to the new hard drive. I used to move system from one machine to another that way. If you move from mbr to uefi you may have to manually create a vfat boot partition in your new hd and may have to reinstall grub after the restore. [http://www.fsarchiver.org/quickstart/](http://www.fsarchiver.org/quickstart/)

---

### Post by monkeybrain20122 on 2019-03-13
> **HermanAB said:**
> Yes you can.

However, it is usually much easier and faster to do a fresh install than to install and old and tired backup.

If you don't have any customization and run on a vanilla system and your system is not destroyed by some bad updates,--if it was then a reinstall still going to get the same bad updates. And a fresh install is definitely not faster than restoring from backup since even for vanilla system you still have to install software.

---

