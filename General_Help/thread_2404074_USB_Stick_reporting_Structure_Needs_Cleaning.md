---
title: "USB Stick reporting Structure Needs Cleaning"
date: 2018-10-19
forum: General Help
---

### Post by jrloucks on 2018-10-19
Installed Ubuntu 18.4.1 on Thinkpad for a friend.  Friend has a 64GB USB Stick that has backup files on it.  Unfortunately, system is reporting "Structure Needs Cleaning".

> **This location could not be displayed.**

Sorry, could not display all the contents of "...": Error when getting information for file "/media/ross/,,,":
Structure needs cleaning.

Thanks in advance.

---

### Post by #&amp;thj^% on 2018-10-19
This was reported here: [https://ubuntuforums.org/showthread.php?t=2348768](https://ubuntuforums.org/showthread.php?t=2348768)
with good outcomes. 
Good Luck

---

### Post by jrloucks on 2018-11-02
Ok, so my attempt to umount and use fsck:

> ross@ross-ThinkPad-T430:~$ sudo umount /media/ross/e4f54258-1a04-4f47-b784-e788190123ef
[sudo] password for ross: 
ross@ross-ThinkPad-T430:~$ sudo fsck "/media/ross/e4f54258-1a04-4f47-b784-e788190123ef/Tipton California"
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
fsck.ext2: No such file or directory while trying to open /media/ross/e4f54258-1a04-4f47-b784-e788190123ef/Tipton California
Possibly non-existent device?
 

So I reinstall the USB drive via File Manager, and re-try fsck:

> ross@ross-ThinkPad-T430:~$ sudo fsck "/media/ross/e4f54258-1a04-4f47-b784-e788190123ef/Tipton California"
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
fsck.ext2: Structure needs cleaning while trying to open /media/ross/e4f54258-1a04-4f47-b784-e788190123ef/Tipton California

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

ross@ross-ThinkPad-T430:~$

So I try alternate superblock:

> ross@ross-ThinkPad-T430:~$ sudo e2fsck -b 8193 "/media/ross/e4f54258-1a04-4f47-b784-e788190123ef/Tipton California"
e2fsck 1.44.1 (24-Mar-2018)
e2fsck: Structure needs cleaning while trying to open /media/ross/e4f54258-1a04-4f47-b784-e788190123ef/Tipton California

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

ross@ross-ThinkPad-T430:~$ 

I'll admit here that I may be using incorrect terminal command syntax.  But I am trying...

---

### Post by Holger_Gehrke on 2018-11-03
You're trying to check the mount point instead of the device. To get the device name, enter 'lsblk -f'. Look for the UUID of your USB Stick (should be 'e4f54258-1a04-4f47-b784-e788190123ef') in the fourth column. You'll find the device name in the first column. Then do 'sudo e2fsck /dev/xxxx', replacing xxxx with the device name.

Holger

---

### Post by jrloucks on 2018-11-03
Thanks HG.

Turns out the device name was sdb1, so umount sdb1, then a handful of sudo e2fsk /dev/sdb1 commands (there were a lot of errors/cleaning necessary) so command aborted 2-3 times.  But now, at long last, the USB contents (>256GB) have been 'recovered' for a very good friend.  He will be overjoyed.

Excellent!

---

