---
title: "GNU ddrescue, possible to make directory for output file?"
date: 2013-12-21
forum: General Help
---

### Post by gherd1 on 2013-12-21
Hi,
I will be attempting to image 2 HDD's that were part of a Raid0 array using GNU ddrescue.
As a trial I have been trying to image a usb stick using ddrescue with the output going to a 1Tb external hdd.
The external hdd has other data on it.
Can I create a directory on the external so that ddrescue only writes the data in there or is it as it seems that the destination device must be empty or data there will be overwritten by ddrescue?
I am new to Ubuntu but enjoying the experience and the learning curve, I am using it off a live usb which I created for the purpose of imaging the hdd's, now I think I will stick with it in future - its refreshing.
Many thanks for any assistance.

---

### Post by TheFu on 2013-12-21
dd and ddrescue work at the device level.  While you can tell it to write to a file, it is highly doubtful that will have the intended results.  dd and ddrescue are extremely powerful tools. Think of them as bit-for-bit copy tools. They know about bits, not files, not directories.  They know about the bits that make up files and directories only, not the logical structures.  I hope that is clear.

As someone knew to Ubuntu, I'd like to point out that almost every command on Linux has a built-in manual page with very detailed information.  
**man dd**
**man ddrescue**
The bad thing about man pages is they are not easy to understand for someone new to Linux/UNIX. After about 6 months of reading them, the lightbulb will come on and you'll wonder why it took so long to understand. 


Perhaps mounting the USB stick and copying the files over would be better?

---

### Post by gherd1 on 2013-12-21
Hey,
Thanks for the prompt reply.
Yer the Usb 'copy' was a trial run for when I come to ddrescue' bit for bit' as you say the 2x 120GB Hdd's. I wanted to understand it better before i started gambling with the precious data I am trying to recover.
It seems then that the destination device must be empty and you cant as I wrongly thought output to a seperate directory.
Many thanks !

---

### Post by gherd1 on 2013-12-21
Can i not use GParted  to create a new partition on the large external and then point my ddrescue output to that new partition only?

---

### Post by TheFu on 2013-12-21
I don't know, but ....
gparted partitions should be fine. I wouldn't worry about them at all.
ddrescue works at the bit level, so as long as you point to the input partition (not the drive device) AND point to the output partition (not the drive device) AND the sector sizes on both physical disks are the same (512b or 4K), then I wouldn't be worried.  OTOH, if the sector sizes are different, I'd do lots more research to understand what may or may not work.  Everything could be completely fine - I just don't know.  

Also, the target partition needs to be at least as large as the source partition. Anything less and I'd expect bad things to happen.

Perhaps someone smarter than me will chime in?

---

