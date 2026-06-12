---
title: "Messed up my Ubuntu Partition"
date: 2008-05-29
forum: General Help
---

### Post by M4rotku on 2008-05-29
Hello,

I made a big mistake, very stupid of me.  I was repartitioning my hdd to give my Vista partition only 40 gigs(haha), a transitional NTSF partition 15 gigs to switch files between the two, and my Ubuntu partition 175 gigs.  As usual, I left my laptop on overnight to make these changes.  Unfortunately, I forgot the plug the laptop in and it ran out of power while it was resizing my Ubuntu partition.  Now, the Grub has an error and I cannot access any of my partitions.  I am running off of the live cd.

I know that I could probably fix this by reformatting and erasing my Ubuntu partition and reinstalling, but that would be a huge pain.  Is there any way that I can fix my Ubuntu partition?

The following is the message that I receive when I try to grow my Ubuntu partition into the the unallocated space.  The filesystem is listed as an ext2.  This is what I get when I try to grow:

"Group descriptors look bad...trying backup blocks

The superblock could not be read or does not describe a correctect ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
"

Can anyone help?

Much thanks,
M4rotku

---

### Post by bingoUV on 2008-05-29
did you try e2fsck that it said?

---

### Post by M4rotku on 2008-05-29
I haven't tried it, I have no idea how to go about executing such a command from the live cd.  Can you tell me the exact code that I would enter into the terminal on the live cd?  That would be very much appreciated.

Thanks,
M4rotku

---

### Post by M4rotku on 2008-05-29
Ok, I looked at the command again and tried to run it and entered:

```
ubuntu@ubuntu:~$ sudo e2fsck -b 8193 /dev/sda3
```

and got the following response:

> 
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Bad magic number in super-block while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>



So it doesn't seem like that's going to work unless I did it wrong.
Will I have to reinstall?

Much thanks, 
M4rotku

---

### Post by bingoUV on 2008-05-29
No, you did right. This superblock was also corrupted, so cannot repair using this. Instead of 8193, try these locations 24577;40961;57345;73729. Maybe it can find a backup superblock.

---

### Post by M4rotku on 2008-05-29
None of those locations worked.  Is there anything else that can be done?

I had just gotten my filesystem the way I wanted it :(


Much thanks,
M4rotku

---

