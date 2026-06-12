---
title: "Need to automount 2 identical NTFS USB drives."
date: 2007-09-15
forum: General Help
---

### Post by drywater on 2007-09-15
Hi,
I have 2 external USB harddrives which are identical.  I need them each to consistently mount at a predefined mount points.  I have renamed them in linux so that they can be mounted by name, which works, if I plug them in AFTER ubuntu loads.  If I leave them plugged in when I reboot I get an error telling me I can enter my password to manually correct the error or hit Ctrl-D to continue.  The following is the log that was saved this morning:

```
Log of fsck -C -R -A -a 
Sat Sep 15 07:39:38 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Bad magic number in super-block while trying to open /dev/sdb1

/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/sda1: clean, 1918/19546112 files, 1617047/39072080 blocks
/dev/hdc1: clean, 1053/7340032 files, 12221924/14653280 blocks
fsck died with exit status 8

Sat Sep 15 07:39:38 2007
----------------
```

After it boots usually 1 of the two drives is mounted, but never both.  Rebooting with them unplugged fixes it but then I need to manually replug them in again.

I assume this error is because these drives are NTFS and NOT any kind of EX2/3.  These drives are occasionally used on other systems so I would rather not format them to ext3, but can I get them to automount by device name upon boot while still keeping NTFS?

Or am I better to format to ext3?

Thanks!

---

### Post by logos34 on 2007-09-15
With them plugged in, run the following commands:

**mount **
[B]
cat /etc/fstab[/B]

---

