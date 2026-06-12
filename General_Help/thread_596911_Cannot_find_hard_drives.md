---
title: "Cannot find hard drives"
date: 2007-10-30
forum: General Help
---

### Post by KanadianKozak on 2007-10-30
This is a very weird problem, I'm not entirely sure how or why it happened, but here is what I know.

Currently in my computer I have 2 IDE drives.  The master drive has a primary partition with Windows XP and another partition with media files.  The secondary partition has Ubuntu, and 3 other partitions with different files.  I was having some grub errors (error 17, to be specific), and I was able to work everything out and fix my problem.  After I fixed everything, my brother decided that since my Ubuntu was not on the primary partition of the secondary drive, I should reinstall it on the primary partition.  He used Power Quest Partition magic to delete my Ubuntu partition, and move over what was on the primary partition to the extended.  

After that, I had another grub error 17.  So I reinstalled Ubuntu onto the primary partition of the secondary hard drive.  Here is when things started to get weird.  After the reboot, it brought up the grub menu.  I went to choose XP, and it just brought me back to the grub menu again.  I tried to load Ubuntu, and it worked perfectly, except that it doesn't see my hard drives.  Instead, it sees a floppy drive (which I don't have), my two cd-rom drives, my Filesystem, and my C:/ drive, which is my windows drive, and none of my other hard drives.  I can't mount my C:/ though, so I can't access any of my information off of it.  Also, if I go "cd /dev" and then "ls hd*" it prints off a list of all my hard drives and my partitions.  And, when I boot off the Ubuntu live cd, it also shows all my partitions, although it is impossible for me to mount them there as well.  If there is anything anyone knows about this that can help me, it would be great!

Kanadian Kozak

---

### Post by KanadianKozak on 2007-10-30
I went into the windows recovery mode and used fixmbr.  Now I can access all the NTFS partitions that share a hard drive with linux, the extended partition on the windows partition, but as for windows itself, I still cannot load it.  When I try to boot windows with grub, it says very quickly and briefly says loading stage2, and then it brings me back to the grub menu.  Also, if I try to mount the drive while in ubuntu, it says failed to mount drive with these details:
Unexpected clusters per mft record (-127).  Failed to mount '/dev/hda1':  Invalid argument The device '/dev/hda1' doesn't have a vaild NTFS.  Maybe you selected the wrong device?  Or the whole disk instead of a partition (e.g. /dev/hda, not /dev/hda1)?  Or the other way around?

---

