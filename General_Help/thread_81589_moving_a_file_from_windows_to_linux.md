---
title: "moving a file from windows to linux"
date: 2005-10-24
forum: General Help
---

### Post by mjkelly on 2005-10-24
I have to move ndiswrapper.tar.gz from my windows partition to my linux partition to get this wireless network card working under linux. Im in a hotel so i dont have any cds or any removable media. I dont have the internet at all under linux. When i log into linnux and try to access the windows partition (mounted /dev/hda1 on /windows) it tells me permission denied. I cant even look at the contents. ??? So i cant move the file that way. Is there a way to move it from using windows? Or can someone tell me why i cant access that /windows partition?

---

### Post by Svictor on 2005-10-24
You should probably have a look at your /etc/fstab file and see if the appropriate options are enables. Here is my line for an ntfs partition (change it to "vfat" if you use fat32).
```
/dev/hda1       /ntfs           ntfs    defaults,user,uid=1000,gid=1000,noauto        0       0

```

As an alternative, you can use one of the ext2 drivers for windows (they will work for ext3 as well).
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm) , at the bottom of the page, there is a list of other drivers ... I can't remember which one I've installed since I haven't been on windows for a while now ... Think it was called ext2ifs.
Good luck !

---

### Post by mjkelly on 2005-10-24
Ive had this question for a while now.

What does ntfs and vfat/fat32 mean? And whats the difference?

Im using windows xp.

---

### Post by Beggar on 2005-10-24
NTFS and fat32 are two different File systems, [info on file systems.]("http://en.wikipedia.org/wiki/File_system")

---

### Post by Moriak on 2005-10-24
[QUOTE=mjkelly]Ive had this question for a while now.

What does ntfs and vfat/fat32 mean? And whats the difference?

Im using windows xp.[/QUOTE]

This should answer most of your questions about MS file systems.

[http://en.wikipedia.org/wiki/FAT32]("http://en.wikipedia.org/wiki/FAT32")

---

### Post by aysiu on 2005-10-24
[QUOTE=mjkelly]Ive had this question for a while now.

What does ntfs and vfat/fat32 mean? And whats the difference?

Im using windows xp.[/QUOTE] Wikipedia's your friend:

[http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS)

And the Ubuntu Guide is also your friend:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

If you're unsure if your Windows partition is NTFS or FAT32, type this in a terminal ```
sudo fdisk -l
``` It'll tell you the name of the partition (something like /dev/hda1) and what type it is.

---

