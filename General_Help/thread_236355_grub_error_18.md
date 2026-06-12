---
title: "grub error 18"
date: 2006-08-14
forum: General Help
---

### Post by Disastorm on 2006-08-14
I get grub error 18 when I try to start up my computer.  I read its because the boot partition is not in the begginning of the hard drive or something like that.  How can I do that without reformating my first partition, or is there no way?

---

### Post by Mr_Congeniality on 2006-08-14
Sounds like all you need to do is reinstall GRUB.  Shouldn't be a problem, if you have an old Ubuntu 5.10 CD, you should use it to install the GRUB boot, because I'm not sure how to install it using the Ubuntu 6.06 install, being that it is all graphical and all.

---

### Post by raffytaffy on 2006-08-14
post your grub.conf if you can

---

### Post by Disastorm on 2006-08-14
> **Mr_Congeniality said:**
> Sounds like all you need to do is reinstall GRUB.  Shouldn't be a problem, if you have an old Ubuntu 5.10 CD, you should use it to install the GRUB boot, because I'm not sure how to install it using the Ubuntu 6.06 install, being that it is all graphical and all.

are you sure that would work? I got this error after an initial install of ubuntu 6.06 (and grub with that).

---

### Post by Mr_Congeniality on 2006-08-14
The PLOT THICKENS!!!  Are you sure you installed ubuntu on the first disk and on the master boot record?

---

### Post by Disastorm on 2006-08-14
> **Mr_Congeniality said:**
> The PLOT THICKENS!!!  Are you sure you installed ubuntu on the first disk and on the master boot record?
i installed it on hdb and i dunno about master boot record, i just let it install automatically with the gui installer or whatever.  I made 3 partitions one for boot, one for root, and one for swap and I think I made them all logical (I tried some of them as primary before too but still got the same error).  I also have a fourth partition on that hard drive as NTFS which had some files on it so I didn't reformat it.

---

### Post by Mr_Congeniality on 2006-08-14
lol I don't think you need to make another partition for boot.

There should already be an MBR at the beginning of each hard drive.  You should try installing Ubuntu with 2 partitions being the root and swap and then try installing the boot loader on hdb.  This should work.

---

### Post by Disastorm on 2006-08-14
i tried using the automatic installer to automatically partition it before and it did only install 2 partitions a swap and root, but when I did that I had gotten an error 17.

---

### Post by Mr_Congeniality on 2006-08-14
Wow.  This is going to take someone more advanced to give you input on this.  I have installed Ubuntu on my first hard disk.

---

### Post by Disastorm on 2006-08-14
Im not sure if I have RAID but the faq for the installer says i need to disable it if I do or it won't install properly.  When i type in the command though it says  
 * Stopping RAID monitoring services...                                  [fail]

does this mean I don't have it, or its failing to stop for some reason?

---

### Post by silvagroup on 2006-08-14
WORD OF CAUTION - back up those files on your first drive if they are critical. I failed to do that while doing a Dapper install to a sata drive and Dapper for some very mysterious reason decieded to wipe out my primary drive partiton. That was last week, and I am still trying to recover the patition, which was on it's own drive, very similar top what you are attempting to do. You may want to try qparted, that will also show you what you have on your system, and how it is currently partitioned.

---

### Post by NetworkGuy on 2006-08-14
i ran into this problem last week while preparing my laptop.  Grub Error 18 is a cylinder "something" error.  Grub is reporting it can't understand the entire hard drive as one big partition as I read it.   I created a 100MB /boot partition and that did the trick for me.

Hope this helps.

---

### Post by Disastorm on 2006-08-14
> **NetworkGuy said:**
> i ran into this problem last week while preparing my laptop.  Grub Error 18 is a cylinder "something" error.  Grub is reporting it can't understand the entire hard drive as one big partition as I read it.   I created a 100MB /boot partition and that did the trick for me.

Hope this helps.

I read about that but does that boot partition have to be somewhere in the beginning of the drive?  my boot partition is after a 50 gb partition, and i was wondering if its possible for me to move it to the beginning of the hard drive.  Creating the 100 mb boot partition originally got rid of the error 17 but gave me the error 18.

---

### Post by Mr_Congeniality on 2006-08-14
Tsk tsk tsk children.  I don't think you will be needing a boot partition like I said.  Make sure there are only 2 partitions on the hard drive you are wishing to install ubuntu to and one is the root and the other is the swap.  Then try installing the GRUB boot loader to your HDA's (1st hard disk) MBR.

RAID shouldn't be an issue here, my guess is that you're not using it, and the reason why RAID services fails to terminate properly is because you do not have RAID set on your hard drives.

---

### Post by Disastorm on 2006-08-15
OK guys I got it working.  I moved my NTFS partition to the right by 100 megabytes.  then i resized the entire extended partition to have 100 mb outside of it.  then I made the boot partition as a primary partition with the 100 mb and also as the first partition on the hard drive and it works now.

---

