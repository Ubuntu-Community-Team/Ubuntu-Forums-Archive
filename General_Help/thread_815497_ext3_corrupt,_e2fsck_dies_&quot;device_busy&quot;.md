---
title: "ext3 corrupt, e2fsck dies &quot;device busy&quot;"
date: 2008-06-01
forum: General Help
---

### Post by relix on 2008-06-01
Gparted was in the process of moving an ext3 partition 5GB to the right of the disk, to make more free space at the left. It was about halfway (it took 4 hours), when there was a read and write error on the device, and gparted tried a rollback and just stopped doing things, saying it got an error.

I thought "well, there goes my data". I couldn't mount the device anymore and sfdisk didn't even give a partition table, stating weird errors. It looked as if the device had just dissapeared. So I rebooted.

And in the boot-process, fsck replayed a couple of transactions on the partition that I thought was beyond repair, and apparantly, everything was OK again. Amazing! I quickly checked the files and they were all there, the ones I tried weren't corrupted or anything. Nice! Fsck did say there were still some errors though, so I unmounted the partition again, and ran fsck.

Fsck died saying there were unexpected errors, and I should run it manually to fix it. So I did, and after pressing "y" for half an hour on questions like "Inode xxxxxxxxxxx corrupt. Clear? <y>", I quit and started fsck again with the -y option. After 2 hours it was finally done, but now it said something about the superblock being corrupted. I should run e2fsck -b 32768. So I did that, and it said the device was busy and it couldn't continue.

I tried mounting it, and that didn't work. I tried rebooting, but it always gave me the same error "superblock corrupted, run with -b 32768" and always "device or resource busy". I tried running a live-cd, using recovery mode, running fuser on the device to see if anything is accessing it, but I couldn't find anything.

So that's where I'm at right now. Stuck with a device that is perpetually "busy" so I can't restore it. Anyone know what I should try?

PS: The disk the partition is on is still good. Other partitions on the same disk mount flawlessly and pass fsck.

---

### Post by HalPomeranz on 2008-06-02
The only other thing I could think of to try is running fsck with a different alternate superblock.

First you need to figure out where that superblock is in the file system.  You can use "mkfs -n" for this (note that it's VERY important to use the "-n" flag here, because that shows you the output of the command without rebuilding your file system):

```
$ **sudo mkfs -n /dev/sda5**
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
4751360 inodes, 18990830 blocks
949541 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
580 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424

```

Obviously you will need to use the appropriate device for your system in place of /dev/sda5.  Notice at the end of the output there is a list of alternate superblocks.  Just pick the next number in the list and use it in your fsck command (e.g., "fsck -y -b 98304 /dev/sda5" on my example system above).

I hope this works for you.  Good luck!

---

### Post by relix on 2008-06-02
Thanks for your reply HalPomeranz!

I tried it, but even using a differint superblock, the same error popped up: Device or resource busy.

I was so fed up with this that I decided to just image the whole thing using dd and try it on there, hoping that an image of the device wouldn't get those same resource busy errors. Amazingly, this worked! The "standard backup" superblock at 32768 was still corrupt, but using your method to see where the others are, I got e2fsck working correctly this time.

```

dd if=/dev/sda2 of=sda2.img
e2fsck -b 98304 sda2.img

```

e2fsck is now half an hour into checking/repairing (I hope!) the system on sda2.img. When it's done, I'll try to mount it and see if everything is in order. If it is, I'll dd it back again using:

```

dd if=sda2.img of=/dev/sda2

```

I still have no idea why that same error kept popping up, but at least now there's a workaround! Hope this helps some people who are having the same troubles as I did.

---

