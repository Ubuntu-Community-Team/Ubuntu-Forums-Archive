---
title: "Ready to ditch NTFS partition, worried about boot issues"
date: 2007-02-07
forum: General Help
---

### Post by RChickenMan on 2007-02-07
Hooray for me, it's been ages since I've booted into the dark side and I'm ready to reclaim my disk space.  I'm worried that deleting my NTFS partition will screw things up as far as the bootloader goes.  It is the first partition on my drive, if that makes a difference.  After I delete the partition, I'd like to keep it just as free space as I have plans on building a Linux From Scratch system*.  That poses another question, is unpartitioned space at the beginning of a drive an issue?  I would appreciate it if someone who has been in this situation before could lend some advice.  Thanks.


*I know what you advanced users are thinking:  you're crawling to the forums for something like this and you think you can build Linux system from scratch?  The concern is that my schoolwork depends on my Ubuntu system being bootable, whereas when I create an LFS system, it's just for fun, and I'm not dumb enough to do anything to mess up my Ubuntu system in the process.

---

### Post by kextyn on 2007-02-07
It's possible you would confuse GRUB and not be able to boot into Ubuntu afterwards.  If you have an NTFS partition, then your root partition then GRUB is looking at hd0,1 to boot Ubuntu.  If the root partition because 0 it wouldn't find it.  All you'd have to do is boot to a LiveCD and manually edit the GRUB ( /boot/grub/menu.lst ) to reflect the changes in your hardware (should be just changing hd0,1 to hd0,0).

I just want to mention that I an a newbie to Ubuntu (been using it about a week now lol) but I've already had to go through several issues similar to this.  So I may not be 100% right.

---

### Post by RChickenMan on 2007-02-07
I'm very comfortable editing the GRUB config files and such, this isn't the first time I've done some repartitioning.  This just seems like a special case because it is the first partition on the disk that is going.

---

### Post by kextyn on 2007-02-07
I wouldn't think it would cause any issues besides menu.lst needing to be changed.  It would be like installing Ubuntu with manually configured partitions and putting the swap partition first at the end of the drive, then making the root partition and the end of the free space.  It would be fine untill you decide to make another partition at the beginning and then you'd just have to change the menu.lst again.  I could be wrong but it just doesn't seem like it would be a problem.

---

### Post by bodhi.zazen on 2007-02-07
Well, I think you can delete the ntfs partition without any repercussions. Grub is in the MBR and the Ubuntu partition and not the ntfs partition.

The question is what to do with the space ? 

Make a data partition and edit fstab to mount it ...

Should be no big deal as you sound competent ...

The best thing will be deleting the windows stanza from menu.lst :p :p

---

### Post by RChickenMan on 2007-02-07
Perhaps acquiring a bottle of champagne is a prerequisite to this operation,,,

---

