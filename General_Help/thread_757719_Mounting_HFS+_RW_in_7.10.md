---
title: "Mounting HFS+ RW in 7.10"
date: 2008-04-17
forum: General Help
---

### Post by svenole on 2008-04-17
I've been using a USB disk with HFS+ partition for some time for backup. The reason for HFS+ is that I backup my Mac to  the same drive. This has worked well for some time. 

The other day, I did a stupid thing. I booted my ubuntu 7.10 laptop with the USB drive connected. For some reason the machine did an fsck on this filesystem  with the result that I've not been able to mount the drive ReadWrite again. This has happened before and then I had to scratch the disk and recreate the HFS+ filesystem on the Mac to be able to mount it rw on the ubuntu-system again. 

I've made sure that journaliing is disabled. The MAC system is running Tiger. 

I was thinking that somebody must have seen this before. I've tried to make the Mac repair the filesystem, but have not been able to create a situation where that has been necessary (unplugged the drive several times while writing to it.. ). I do not know a way to force the mac to repair a filesystem (write new superblocks).

---

### Post by mrsteveman1 on 2008-04-17
disk utility can do all that stuff in OS X.

Open it, select the drive/partition on the left you want to fix, in the first aid tab click the verify/repair disk buttons. This runs an fsck on the filesystem.

If you need to reformat, click the erase tab, select mac os extended (not journaled if you want to use it with linux), and click erase. Make sure you do this to the right disk though.

---

### Post by svenole on 2008-04-17
Well.  

I've tried the diskutility in Mac osX several times. However the repair does not do an actual repair since there is nothing wrong with the filesystem. As mentioned in the original post, I've tried to make the filesystem incosistent by unplugging the disk while writing to it. I have not had any success with that.  The whole point was  not to recreate the whole filesystem... ;-)

The whole problem is the read only mount on the ubuntu laptop. I do not really understand why ubuntu does not mount this disk read write after doing a fsck.hfsplus on it. This makes not sense. I do suspect that ubuntu thinks that journaling is turned on despite the fact that osX reports it to be turned off. 

- Sven

---

### Post by mrsteveman1 on 2008-04-17
Well, i suppose you can always boot into single user mode and run a forced fsck from OS X, this should test the entire filesystem and not just check if its unclean.

When you boot single user mode (hold command-s on startup), it should give you directions on checking the filesystem.

If the filesystem itself is clean, and journaling is in fact off (sometimes you have to do it a few times from the commandline in OS X), then the linux kernel is simply not reading things write. Not sure what the solution is in that case :D

---

### Post by svenole on 2008-04-18
The problem was solved by using the fcsk_hfs command on the Mac with the -r option. This forces the Mac to write new data to the HFS+ filesystem which makes the ubuntu system able to mount this filesystem rw again. 

This does not change the fact that there has to be a major bug in the ubuntu hfsplus code. A fsck on an HFS+ filesystem under ubuntu will make the system unwriteable.

---

### Post by mrsteveman1 on 2008-04-18
The HFSplus stuff in the linux kernel is known to have problems. The journaling stuff in OS X isn't actually in HFS+, its a virtual layer on top of the filesystem, so it would have to be implemented like that in the linux kernel which seems unstable at the moment (hence the no writing stuff).

As long as you can fix the filesystem and not loose data by using apples tools in OS X things should be fine, just don't trust the filesystem 100%, keep backups of anything you are afraid to loose.

---

