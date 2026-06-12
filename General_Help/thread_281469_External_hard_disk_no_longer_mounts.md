---
title: "External hard disk no longer mounts"
date: 2006-10-21
forum: General Help
---

### Post by RogerD on 2006-10-21
Hi

I've got a Western Digital My Book external hard drive. Up to now, it automatically appears on the desktop whenever I switch on. Suddenly it's stopped doing this.

When I click on Places>computer, I see the My Book icon complete with the Gnome footprint icon (not sure if there's any significance in the icon). When I right click on 'open', I get the message: 'Uanble to mount the selected volume'. 'Show more details' gets me:

error: directory/medi/mybook not empty
error: could not execute pmount.

I know the drive is still working, as it's OK in Windows.

It looks as though I've failed to unmount the drive at some stage, but when I look in /media, this is what I get:

roger@roger-desktop:~$ cd /media
roger@roger-desktop:/media$ ls
cdrom  cdrom0  hda1  My  My Book
roger@roger-desktop:/media$

Which suggests My Book is indeed mounted - it's in dark blue, just like hda1. I'm a bit puzzled by the My (in black text) in front of My Book.

I thought it might be worth trying to umount My Book, but this is what I get:

roger@roger-desktop:~$ cd /media
roger@roger-desktop:/media$ ls
cdrom  cdrom0  hda1  My  My Book
roger@roger-desktop:/media$ sudo umount "My Book"
umount: My Book: not mounted
roger@roger-desktop:/media$

Which, to me, is totally weird - one minute my system is saying a drive is mounted (probably); the next it's saying it isn't.

I'm not sure if it's relevant, but this is my fstab file:

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

All help and advice will be much appreciated.

Roger D





.

---

### Post by Kateikyoushi on 2006-10-21
> error: directory/medi/mybook not empty

This says /medi/mybook and you list the /media directory.
Do you have a /medi directory ?

---

### Post by RogerD on 2006-10-21
> **Kateikyoushi said:**
> This says /medi/mybook and you list the /media directory.
Do you have a /medi directory ?

Thanks for the response, and well spotted, but it's just a typo

It should be /media/mybook.

---

