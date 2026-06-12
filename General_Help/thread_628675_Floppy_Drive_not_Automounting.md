---
title: "Floppy Drive not Automounting"
date: 2007-12-01
forum: General Help
---

### Post by gamerchick02 on 2007-12-01
Hey all,

I'm running Kubuntu Gutsy.

I've been having issues with my floppy drive; ie, I don't even see it in Dolphin or Konqueror.  Nothing shows up in the window in either of those browsers when I insert a floppy into my drive.

Now, I've got an output of my fstab right here:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9f75686a-3ebd-428e-80df-3b23bd4fa3be /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=F008511F0850E5DE /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=72CD-9F9E  /media/sdb2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=6d1b9574-2510-4fab-b709-29dc80cd91bd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

All seems ok, right?

Well, take a look at this:

[IMG]http://farm3.static.flickr.com/2418/2076504353_4a1a0bc4c4.jpg?v=0[/IMG]

If you look at the first line there, for my CD burner, it shows it's mounting on /media/floppy0.  Strange.

This isn't hugely time-dependent, but I like to have everything working on my system.

Amy

---

