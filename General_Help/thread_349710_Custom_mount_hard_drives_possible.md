---
title: "Custom mount hard drives possible?"
date: 2007-01-30
forum: General Help
---

### Post by tictacman on 2007-01-30
I have two ntfs partitions located /media/windows /media/backup, they are mounted automatically.  Sometimes I use them but mostly I don't.  Is it possible to set it up so  instead I can right click on one of the folders in /media/ and select mount?

At the moment I can umount them that way, but there is no option to mount them again once this done.

Here is my fstab set up:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=43cdf8d7-d10b-47cc-a94e-ed6ce3bda1d9 /               ext3    defaults,erro$
# /dev/sda3
UUID=82dd120c-8276-4ce9-a8a8-66013503503e /home           ext3    defaults     $
# /dev/sdb5
UUID=5AC0F147C0F12A41 /media/backup   ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/sda1
UUID=D6CC049ACC0476D1 /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/sda5
UUID=c9eaac10-cf13-44c0-a16e-67daa4528306 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by tictacman on 2007-01-31
No takers?

Ok here's the only solution I can come up with for now but, perhaps someone has a better one.

Keep my settings as they are, umount the drives by right clicking when I get into kde, and then when I need them restarting fstab by using the command:

mount -a .

Not a very elegent workaround but it will have to do for now.

---

### Post by randiroo76073 on 2007-01-31
The only things I put in my media folder are my floppy & ext USB hdd, all my other partitions are in "mnt" and I can access them as needed:)  I attached a txt file for editing fstab that was very helpful[unfortunately, lost link]

---

