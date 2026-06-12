---
title: "Ubuntu stopped my external HD working in XP"
date: 2007-02-14
forum: General Help
---

### Post by Psyphre on 2007-02-14
Hi, ive used ntfs externals on ubuntu a few times without any problems. I tried plugging in my fat32 external yesterday and after using ubuntu for a while i booted into XP. Ever since using the HD in ubuntu XP cant recognize it anymore; the other externals (NTFS) work perfect still.
I tried it on my laptop (also ubuntu) but that couldnt detect it either, so last I tried booting into ubuntu again (on my desktop) and my external DID show up there. It seems that once i used it on my desktop ubuntu, no other machine/OS can detect it anymore.

Any help would be greatly appreciated since i have ALOT of data I need in there.
Thx!

---

### Post by Zenguy on 2007-02-14
I had a similar problem this weekend.

One of my external NTFS drive suddenly stopped working. I did not do anything to the drive. Ubuntu Edgy installed some updates the night before, so I suspect it was the cause.

It appeared as though the partition table in the external now showed a Linux EXT3 partition in the middle of the drive. It is a 500 GB drive.

I used a utility called Partition Table Doctor to retrieve the drive. It did a great job getting the data back. It still reports a problem on my main NTFS boot drive, but everything appears to be working normally. Other partition software shows everything fine, so I think it may be a bug with Partition Doctor.

Keep good backups.

---

### Post by Crooksey on 2007-02-14
Are you talking about just plugging it in and it wont mount, or manually mounting it setting all the correct options in your fstab?

---

### Post by Psyphre on 2007-02-14
Thx for the replies, Ive found something peculiar now... In xp it DOES mount afterall, except as a network drive which is very very strange. Not only does it show under the network section, its also as slow as a network drive. Very wierd.

I havent had a chance to check on my laptop's ubuntu yet.

Zenguy: Internet wont work on my ubuntu, so it cant be due to an update.

Crooksey: Just plugging in. Ive never had any problems in XP or ubuntu with externals b4 so I have never manually mounted anything. Also it does automatically mount on my desktop's ubuntu.

---

