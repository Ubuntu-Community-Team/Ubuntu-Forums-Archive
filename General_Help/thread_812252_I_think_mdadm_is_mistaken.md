---
title: "I think mdadm is mistaken"
date: 2008-05-29
forum: General Help
---

### Post by Kissell on 2008-05-29
So, I've got a ext3 software RAID (money decision), and I keep getting a drive kicked out of the array.  

I do > mdadm --detail /dev/md0  and one of the disks is missing.  

I check the disk using > badblocks -s -v -w /dev/sde  and it comes back clean, no bad blocks.

Is there a way I can see why it's being kicked out of the array?  some more detailed information about why that disk was removed?  

Cause the disk shows to be clean, then I add it back, but it gets kicked out again later, and I don't know why it kicks it out.

---

### Post by fjgaude on 2008-05-29
My experience with mdadm over the years, especially the last three, is that the program is solid, reliable.

One reason the drive gets declared as bad is because it is. Drives have been known to have random errors due to marginal platters and non-solid electronics.

How large are the drives, their manufacturer, and how old are there?

---

### Post by Kissell on 2008-05-29
It's 11 disks in a RAID-6.  

All 11 drives are 750GB Seagate SATA2 Barracudas.

I'm actually currently getting two disks knocked out...  one of those two I have replaced under hardware warranty 4 times already.  Some of those times it did report badblocks...  which is really frustrating, that they keep sending me a refurbished drive that has bad blocks within the first few weeks.  But, now after replacing this one several times, it doesn't report any bad blocks, but it's still being kicked out.  

Is there a way I can see more about why it was kicked out of the array?  All I know is that when I look at the array with mdadm it says "removed" where that drive used to be.

---

### Post by fjgaude on 2008-05-29
Well, I'm no expert... the only way I know of for testing disk is **ckdisk** and **testdisk**. The latter might be what you are looking for. It's in the repostitory.

This may be a sign of the times... I'm on my fifth Seagate ST3320613ST 320GB drive, all in the last six weeks. Bad electronics, not platters.

It happens... I've gone for about four years without a drive failure, but then, it happens... <sigh>

---

