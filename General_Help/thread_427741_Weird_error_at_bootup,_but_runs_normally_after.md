---
title: "Weird error at bootup, but runs normally after"
date: 2007-04-29
forum: General Help
---

### Post by rabid emu on 2007-04-29
First off I'm running Ubuntu Edgy.  I recently installed Feisty on another partition, and this problem started happening right afterward so they might be related.  At the end of bootup, it says that the filesystem check failed, with this error:

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=c7d06dfa-7380-4bdf-98ec-8a6b32598886'
fsck died with exit status 8

and then it brings me to a root terminal.  If I just say "exit" it boots up normally and nothing seems wrong at all while using Ubuntu.  This happens at every bootup of Edgy.  The first time this happened, I ran fsck on both my edgy and feisty filesystems, and both returned no errors.

Here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=887f8e46-d0f9-4244-9ca3-305ad53aefd1 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/sda1
UUID=FCF02538F024FA92 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/sda5
UUID=c7d06dfa-7380-4bdf-98ec-8a6b32598886 /media/sda5     ext3    defaults      
  0       2
# /dev/sda3
UUID=b66dc0fa-5430-43a1-8322-53e1370ef9cb none            swap    sw            
  0       0
# /dev/sda6
UUID=0922b791-0081-4fd0-9521-532fb4128bb0 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Edgy is running off sda2.  sda1 is my windows partition, sda5 is my feisty partition.

Anyone know what's going on?

---

### Post by orb9220 on 2007-04-29
> # /dev/sda5
UUID=c7d06dfa-7380-4bdf-98ec-8a6b32598886 /media/sda5 ext3 defaults
0 2

Is this a usb? Sata? Sata2? for a temp fix you could change the 2 on the end to 0 which would turn off disk check for that drive on startup

---

