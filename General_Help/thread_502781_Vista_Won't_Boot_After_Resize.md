---
title: "Vista Won't Boot After Resize"
date: 2007-07-17
forum: General Help
---

### Post by NTITech on 2007-07-17
Using a GParted LiveCD, I shrunk my Vista partition to make room for a Linux partition.  Now when I try to boot Vista, it just hangs on the boot screen.  EVEN THE VISTA DVD HANGS WHILE BOOTING!!!  Is there any way I can boot up Vista again (without having to re-install)?  The weird thing is that I can mount my Windows Vista partition (in gparted) and read the files on it (so I can make a backup).  I do not want to re-install Vista, what should I do?

P.S. I read something about Vista using a different version of NTFS, and that the position of the partiton is important or something...

---

### Post by splintercellguy on 2007-07-17
Bad idea! Good time to backup the files off the NTFS, anything Linux that touches Vista's NTFS will screw it up.

EDIT: I'm not totally positive on whether GPartEd really screws up the Vista, I read a suggestion of running chkdsk on the VIsta part.

---

### Post by Uncle Spellbinder on 2007-07-17
No real help here, but For future reference, you can resize you partitions from within Vista.  Administrative Tools > Computer Management > Disk Management.  Quick and painless in my case.

---

### Post by NTITech on 2007-07-17
So, is there any way to fix this?  Or should I just backup and re-install...

---

### Post by bigken on 2007-07-17
have tried to repair using the vista cd ?

the dvd hanging has nothing to do with resizing the partition

---

### Post by NTITech on 2007-07-17
I cant load the vista dvd...

But, I found this page: [http://forum.linux-ntfs.org/viewtopic.php?t=559](http://forum.linux-ntfs.org/viewtopic.php?t=559)

So, maybe I CAN fix it :P

I'll try and report back...

---

### Post by chadlewis on 2007-07-17
I've done this same thing about three times now - resized a drive in my dual boot configuration only to have Vista and the Vista install CD become completely unresponsive. What you need to do is boot with a Windows XP disc, let all the drivers and whatnot load, then choose the repair windows option. It'll ask you for your password, put in garbage all three times it does, then it automagically fixes your MBR. I know it sounds weird, but dozens of people on these forums have tried it, including myself, and it's the only thing I've found that works.

---

### Post by bigken on 2007-07-17
the right way to do it with a winxp cd is boot form it and at the prompt select R for recovery console 

select your partition ie 1 for vista 

when it asks for a password just hit enter unless you have a admin password 

then type fixmbr enter 
fixboot enter 
exit enter

---

### Post by stchman on 2007-07-17
> **NTITech said:**
> Using a GParted LiveCD, I shrunk my Vista partition to make room for a Linux partition.  Now when I try to boot Vista, it just hangs on the boot screen.  EVEN THE VISTA DVD HANGS WHILE BOOTING!!!  Is there any way I can boot up Vista again (without having to re-install)?  The weird thing is that I can mount my Windows Vista partition (in gparted) and read the files on it (so I can make a backup).  I do not want to re-install Vista, what should I do?

P.S. I read something about Vista using a different version of NTFS, and that the position of the partiton is important or something...

This may be a too late thing but Vista has the ability to shrink partitions within Vista.  Also before you ever shrink a partition you need to run a chkdsk /f on all NTFS partitions and run a defrag.

---

### Post by NTITech on 2007-07-18
Thanks for all your help guys..... but I just re-installed Vista :P

---

### Post by bigken on 2007-07-18
I feel that this one more reason to go totally Linux if Microsoft were more friendly 
towards other operating systems I would consider duel booting but as they aren't all five pc's in my home are totally linux

---

### Post by tbasherizer on 2007-07-21
I have the same problem, and I've tried to use the WinXP install disc to fix stuff, but the Administrator password that I have entered is not good, apparently. I have an Asus 49J-A1 notebook, by the way. I thought that I could just install WinXP and run the commands from the installed OS, but then I'd have to reset the GRUB, and I'm too lazy right now to do that. Please Help. I have some photoshop work that I can't do right now. that is almost ready for publishing on deviantart.

---

### Post by raul_ on 2007-08-27
> **bigken said:**
> the right way to do it with a winxp cd is boot form it and at the prompt select R for recovery console 

select your partition ie 1 for vista 

when it asks for a password just hit enter unless you have a admin password 

then type fixmbr enter 
fixboot enter 
exit enter

it DOES work! :lolflag:

what planet are you from?

---

