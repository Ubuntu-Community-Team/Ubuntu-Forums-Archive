---
title: "XP can't see partition formated in Ubuntu"
date: 2008-03-24
forum: General Help
---

### Post by jeeves on 2008-03-24
I formatted one of my partitions with with NTFS using** mkntfs**. The newly formatted partition works fine in Ubuntu, but when I boot up into** XP Home Edition** it does not have a drive letter and is therefore unusable.

I even tried using XP's *Computer Management > Disk Manager* to assign a drive letter the new NTFS partition. I can see the partition in the disk manager, but when right clicking on the partition all the options are grayed out except for "delete logical drive."

Anyone experience something similar on a dual boot system?

---

### Post by Squish on 2008-03-25
I hear that there are differant versions of NTFS, so that could be the problem... otherwise I have no clue, but am interested to see what the answer is.

---

### Post by LaRoza on 2008-03-25
> **jeeves said:**
> I formatted one of my partitions with with NTFS using** mkntfs**. The newly formatted partition works fine in Ubuntu, but when I boot up into** XP Home Edition** it does not have a drive letter and is therefore unusable.

I even tried using XP's *Computer Management > Disk Manager* to assign a drive letter the new NTFS partition. I can see the partition in the disk manager, but when right clicking on the partition all the options are grayed out except for "delete logical drive."

Anyone experience something similar on a dual boot system?

Well, there are several things to consider.

* NTFS isn't open, so the Ubuntu made version is just reverse engineered
* NTFS changes, so this maybe the Vista compatible version
* If you formated it in Windows, both would see it.

---

### Post by jeeves on 2008-03-25
For whatever reason, XP Home Editon did not like the NTFS partitions I formatted in Ubuntu. The way I got around this was to use the disk manager in XP **"delete the logical drive"** in question (this was the only option that was not grayed out in the menu). Of course this destroys all the data, but I had empty NTFS partitions anyway. 

After the logical drive is deleted I was,able to right click the newly created free space in the disk manager and use the built in wizard to format the space with NTFS and assign it a drive letter and name. The newly formatted partition is immediately recognized by widows, and after editing my fstab in Ubuntu too.

---

### Post by LaRoza on 2008-03-25
> **jeeves said:**
> For whatever reason, XP Home Editon did not like the NTFS partitions I formatted in Ubuntu. The way I got around this was to use the disk manager in XP **"delete the logical drive"** in question (this was the only option that was not grayed out in the menu). Of course this destroys all the data, but I had empty NTFS partitions anyway. 

After the logical drive is deleted I was,able to right click the newly created free space in the disk manager and use the built in wizard to format the space with NTFS and assign it a drive letter and name. The newly formatted partition is immediately recognized by widows, and after editing my fstab in Ubuntu too.

Similiar problem with solution: [http://ubuntuforums.org/showthread.php?t=708426](http://ubuntuforums.org/showthread.php?t=708426)

---

### Post by stinger30au on 2008-03-25
load this driver in to windows xp and if the hdd is attached to the pc that xp is running on you can get read/write access to the disc

[http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd](http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd)

---

### Post by LaRoza on 2008-03-25
> **stinger30au said:**
> load this driver in to windows xp and if the hdd is attached to the pc that xp is running on you can get read/write access to the disc

[http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd](http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd)

If the drive were formated in ext2, but it is not.

---

