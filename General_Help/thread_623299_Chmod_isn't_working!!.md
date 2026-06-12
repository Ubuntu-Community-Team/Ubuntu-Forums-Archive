---
title: "Chmod isn't working!!"
date: 2007-11-25
forum: General Help
---

### Post by Flameguthix on 2007-11-25
I switched from Winblowz XP to Ubuntu Feisty Fawn a few weeks ago, and want to use one of the games on that disk with Wine. It all works in wine, but it tries to edit and save a file. I keep trying to change the permissions on the disc or even just the file with chmod 775 disk, but it keeps saying:

```
chmod: changing permissions of disk: Read Only File System
```

I've tried it doing sudo before chmod, doing su before I do it, even putting my username with root grouping, changing ownership of the disk to my username, NOTHING works!! No matter what command I use, nothing changes it from a Read Only File system.

Help??

---

### Post by smartboyathome on 2007-11-25
Windows partitions are read only on fiesty. Gutsy is the first version of Ubuntu to include ntfs-3g. You will have to install this manually on fiesty.

---

### Post by Jose Catre-Vandis on 2007-11-25
If the file is on a disc/iso, and trying to save it back onto the disc/iso, it will be read only? Have you moved all the files onto your HDD and installed from there?

---

### Post by Flameguthix on 2007-11-25
ntfs-3g, can I get it with Add/Remove Programs...?

---

