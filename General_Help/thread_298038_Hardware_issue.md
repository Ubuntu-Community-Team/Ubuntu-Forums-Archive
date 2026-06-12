---
title: "Hardware issue?"
date: 2006-11-12
forum: General Help
---

### Post by somersetsimon on 2006-11-12
I've been having terrible problems with Ubuntu since I started with it about 5 weeks ago. I bought a cheap second hand desktop that had XP installed and bought another cheap 2nd hand hard disk for linux.

The XP installation on the original disk has always been fine. I've installed various versions of Ubuntu/Kubuntu on the 2nd disk about 10 times now. They last about anything from 2 hours to 4 days before failing really badly and requiring a reinstall. The latest one was last night. Ubuntu 6.06 just froze completely. When I rebooted I had loads of messages like 'Buffer IO error on device hdd, logical block 9' and other devices like dm-1. Eventually I got the login screen, but then had a message that the X server couldn't start due to an internal error.

What sort of HD problems could I have that result in the disk being ok for a few days, then suddenly failing? Also, what utilities are there that I could use (linux or windows) that would let me check the disk?

---

### Post by bigken on 2006-11-12
go to makers web site for hdd utilites  sounds like its a bad drive bad sectors ect I wwould save myself the pain and brain damage ditch the drive and get a new one they are as cheep as chips these days ;)

---

### Post by somersetsimon on 2006-11-12
> **bigken said:**
> go to makers web site for hdd utilites  sounds like its a bad drive bad sectors ect I wwould save myself the pain and brain damage ditch the drive and get a new one they are as cheep as chips these days ;)

Thanks for the advice. I'll have a look at Maxtor's website. If there are bad sectors on the drive, then are there Linux utilities that I could run from Ubuntu that would 'quarantine' those sectors and let me just use the good bits?

PS part of my reasons for trying out Ubuntu is to see how cheap I can get a working system for. THe PC was £20. The additional hard disk was about £15 (If I was confident I could just ditch windows altogether and save the extra money). I'm trying to pick up cheap computers and get them useable for our local pre-schools and schools.

---

### Post by bulldog on 2006-11-12
If a hard disk is falling apart,it's gonna fail again,no matter what you do.

You can write around the bad sectors but there will be more and more bad sectors and in the end you lose your data completely.

I've had two times this kind of disk errors and the best thing you can do is to throw it away as far as you can :D 

Once I had a disk that suddenly refused to reboot and it was broken.
That's the best thing you can have because you won't have to hassle with it.
There should not be important data on it,but I don't consider windows as 'important data'.

---

### Post by bigken on 2006-11-12
I agree with bulldog if drive is going bad its not worth trouble ](*,) 
I also think its good thing you are doing for the school :D

---

### Post by somersetsimon on 2006-11-12
> **bigken said:**
> I agree with bulldog if drive is going bad its not worth trouble ](*,) 
I also think its good thing you are doing for the school :D

It's quite easy to pick up old machines that are not useful for windows any more, but quite sufficient for linux. I hope to buy up all the old machines before anyone realises ;)

---

### Post by bulldog on 2006-11-12
> **somersetsimon said:**
> It's quite easy to pick up old machines that are not useful for windows any more, but quite sufficient for linux. I hope to buy up all the old machines before anyone realises ;)

How big is your garage?????

Succes anyway,good work.

---

### Post by somersetsimon on 2006-11-15
> **bulldog said:**
> If a hard disk is falling apart,it's gonna fail again,no matter what you do.

You can write around the bad sectors but there will be more and more bad sectors and in the end you lose your data completely.

I've had two times this kind of disk errors and the best thing you can do is to throw it away as far as you can :D 

Once I had a disk that suddenly refused to reboot and it was broken.
That's the best thing you can have because you won't have to hassle with it.
There should not be important data on it,but I don't consider windows as 'important data'.

A new hard disk is on its way, but I think I might experiment with the old one before I throw it away...

I wiped the old drive and made it my D: drive under windows. I ran a disk checking utilty in windows and it picked up a number of bad sectors. There were only 0.4% of bad sectors on the disk, but they were all within the first 2 or 3% of the disk. I read someone that, when you format a disk in windows, the bad sectors are identified and will not be accessed. Is this correct? If so, I have a plan...

If I put this old drive (or any other drive) into a USB caddy and use it as an external drive, would it automatically be detected and be useable under windows and Ubuntu? This seems to be the way that my USB memory sticks are handled. Windows identifies the filesystem on the USB sticks as NTFS, but I thought that you couldn't write to NTFS in Ubuntu? Are they really FAT32 and should I format an external disk as FAT32 as well?

Let's say I take a 40GB external drive and format it as 2 20GB FAT32 partitions in Windows, should I expect Ubuntu to automatically pick up two new paritions? What would it call them?

Thanks

Simon

---

