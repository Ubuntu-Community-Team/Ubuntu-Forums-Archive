---
title: "General questions"
date: 2007-04-19
forum: General Help
---

### Post by mocqueanh on 2007-04-19
I'm a new user of Linux Ubuntu, so dont know much of Ubuntu, plz help me these questions:
1) where can i know all commands of termial in Ubuntu ?
2) My USB is in file system FAT32, but when i put in PC, Ubuntu recoginze it and can see all files of my USB.
But why Ubuntu cant recognize the partitions of my Win XP , they're FAT32 as USB, too.
3) I cannot play all music and movie file types(DAT, MP3, WMA...) in Ubuntu, it always says: no decoder to play.
Where can i obtain decoder for Ubuntu, such as Codec Pack for Win ?
4) What is Sudo, and how to know all commands of Sudo ?

---

### Post by Paul41 on 2007-04-19
> 1) where can i know all commands of termial in Ubuntu ?

I usually just do a web search for these. You could start here: [http://www.ss64.com/bash/](http://www.ss64.com/bash/)

> 2) My USB is in file system FAT32, but when i put in PC, Ubuntu recoginze it and can see all files of my USB. But why Ubuntu cant recognize the partitions of my Win XP , they're FAT32 as USB, too.

Are you sure you XP partitions are FAT32? By default they would be NTFS. Anyway, this might help.  [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

> 3) I cannot play all music and movie file types(DAT, MP3, WMA...) in Ubuntu, it always says: no decoder to play. Where can i obtain decoder for Ubuntu, such as Codec Pack for Win ?

For these you need to install the restricted formats codecs. [https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29)
This can also be done using Automatix. [http://www.getautomatix.com/](http://www.getautomatix.com/)

> 4) What is Sudo, and how to know all commands of Sudo ?
Using sudo gives you temporary root access, which means you have access to install programs, access all files and things like this. sudo doesn't have its own special commands. Instead you use sudo in front of commands when you need extra priviledges. For example:
```
sudo apt-get update
```
If you tried to do apt-get update with out sudo you wouldn't have permission.

I hope this helps.

---

### Post by Brucevdk on 2007-04-19
> **Paul41 said:**
> 
Are you sure you XP partitions are FAT32? By default they would be NTFS. Anyway, this might help.  [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)


If the Windows partition does happen to be NTFS, I recommend following [HOWTO: NTFS with read/write support using ntfs-3g (easy method)]("http://ubuntuforums.org/showthread.php?t=217009"). You can verify this by executing *sudo fdisk -l* in a terminal.

---

### Post by mocqueanh on 2007-04-20
Ok, and one more question, i've download an applation from linux.softpedia.com.
After decompress it, i dont know how to install it.
In Ubuntu, the Add/Remove program only update programs from server, and doesnt support install app from source(install offline)
:confused:

---

### Post by Paul41 on 2007-04-20
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

