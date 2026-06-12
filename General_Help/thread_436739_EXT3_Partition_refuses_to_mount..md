---
title: "EXT3 Partition refuses to mount."
date: 2007-05-08
forum: General Help
---

### Post by el_escorpion on 2007-05-08
This is what i get:
> aleks@Fluffy:~$ sudo mount -v /dev/hda2
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/b47f3931-31e4-417b-8e6b-831d940f999c,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


This is what i get when i try fsck.
> aleks@Fluffy:~$ sudo fsck /dev/hda2
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/hda2: clean, 9069/7684096 files, 13685988/15360148 blocks (check in 4 mounts)


Which has me stumped.

---

### Post by tommcd on 2007-05-08
Can you post:
cat /etc/fstab

and
sudo fdisk -l

If it is ext3 you could try "sudo mount -t ext3 /dev/hda2"
You will need to have a mount point for the partition somewhere, like in /mnt or /media.
EDIT: Is it a data partition, and did you set it up when you first installed ubuntu?

---

### Post by el_escorpion on 2007-05-08
> aleks@Fluffy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=290db4bb-9741-4d5b-933b-1e97304f9642 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=3131c5b1-2eb2-4f42-8ff3-8ca3b9769720 /home           ext3    defaults        0       2
# /dev/hda2
UUID=b47f3931-31e4-417b-8e6b-831d940f999c /media/hda2     ext3    defaults        0       2
# /dev/hda1
UUID=88382B8F382B7B78 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=bee170fc-cc1b-442b-8301-6c0739ec0e92 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

And

> aleks@Fluffy:~$ sudo fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551       10199    61440592+  83  Linux
/dev/hda3           10200       12034    14739637+   f  W95 Ext'd (LBA)
/dev/hda4           12035       12161     1020127+  82  Linux swap / Solaris
/dev/hda5   *       10200       11346     9213246   83  Linux
/dev/hda6           11347       12034     5526328+  83  Linux


And yes this is a data partition. Was set up a while back when I first installed Ubuntu.
Also, sudo mount -t /dev/hda2 (to say /media/hda2 which exists)
still yields
> mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

### Post by tommcd on 2007-05-08
I assume /dev/hda6 /home mounts ok? Make sure you have the mount point /media/hda2. The only other thing I can think of is possibly the UUID stuff is causing a problem. You could try to remove it and set up your fstab for hda2 to look like this:

/dev/hda2  /media/hda2 ext3 defaults 0 2

You may need to log out and log back in again for the changes to take effect.
Be sure to remove the # in front of it. 
Please BACKUP your fstab first like this:
"sudo cp -i /etc/fstab /etc/fstab.bak".
If it does not work you can restore fstab like this:
"sudo cp -i /etc/fstab.bak /etc/fstab" You will get a prompt asking you to confirm to rewrite fstab, answer Yes.

---

### Post by el_escorpion on 2007-05-08
Still doesn't work. Doesn't mount, doesn't show up. :confused:

---

### Post by tommcd on 2007-05-08
I'm sorry, but I'm out of ideas. Your fstab looks ok as near as I can tell. It has the same file system and options as your /home. I don't know why /home would work and /media/hda2 would not.
Perhaps /var/log/syslog or dmesg | tail would give some clues.

---

