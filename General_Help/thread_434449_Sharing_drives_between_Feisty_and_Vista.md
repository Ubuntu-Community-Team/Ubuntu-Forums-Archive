---
title: "Sharing drives between Feisty and Vista"
date: 2007-05-05
forum: General Help
---

### Post by Tuxedo Mask on 2007-05-05
Greetings all,

So I'm trying to share a drive between Ubuntu Feisty Fawn and Windows Vista, and for the most part it seems to be working ok.

For the most part.

For one, whenever I save items to the shared drive in Ubuntu, I cannot see them when I later boot into Vista.  Secondly, this drive has two folders in them that are designated as "Special" folders in Vista (e.g., Pictures); for some reason, these folders are mounted without any write access when I boot into Ubuntu.  Any idea how to get around these issues?  Thanks.

Here's my entire fstab for reference:

# <file system> <mount point>           <type>  <options>                                       <dump>  <pass>
proc            /proc                   proc    defaults                                        0       0
/dev/sda5       /                       ext3    defaults,errors=remount-ro                      0       1
/dev/sda2       /boot                   ext3    defaults                                        0       2
# these 3 are the drives I am trying to mount for sharing between Ubuntu and Vista
/dev/sda9       /home/david/documents   vfat    defaults,utf8,uid=1000,umask=0000,gid=1000      0       0
/dev/sda10      /home/david/music       vfat    defaults,utf8,uid=1000,umask=0000,gid=1000      0       0
/dev/sda11      /home/david/misc        vfat    defaults,utf8,uid=1000,umask=0000,gid=1000      0       0
# /dev/sda7     /mnt/bulin              ext3    defaults                                        0       2
/dev/cdrom       /media/cdrom0          udf,iso9660 user,noauto                                 0       0

---

### Post by seamuso on 2007-05-06
You could always format the shared drive as ext3 and install this ..

[http://www.fs-driver.org/](http://www.fs-driver.org/)

in vista (you have to use compatability mode and assuming 32bit). I use the driver in both xp and vista and read/write from/to my linux volumes. I haven't had any major issues doing this.

---

### Post by lxop on 2007-05-16
Anyone got any other ideas? I have a similar situation, just I can't access my XP "My Documents" folder with r/w. It is on FAT32 btw.

---

### Post by todavies on 2007-05-26
Dealing with these same issues, I decided to make an ntfs partition and share that between linux and windows since the ext3 drivers for windows seem much less stable than ntfs-3g.  Is there any reason why this is a bad idea?

---

