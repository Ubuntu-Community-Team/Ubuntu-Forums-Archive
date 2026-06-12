---
title: "Does using a Ubuntu Live CD modify an NTFS partition in any way?"
date: 2016-11-06
forum: General Help
---

### Post by delerious2 on 2016-11-06
I booted up my Windows 10 computer using an Ubuntu 16.04 LTS Live CD.  I was clicking around some of the Windows NTFS partitions, but I was only viewing directory contents.  I did not write anything to any of the NTFS partitions.  Then I told Ubuntu to shut down the computer.  Then I powered the computer back on, and booted into Windows 10.  It immediately said "Scanning and repairing E:".  The E drive was one of the NTFS partitions that I accessed in Ubuntu.  

I have rebooted my Windows 10 a ton of times, and this is the first time I've ever seen a "Scanning and repairing" message.  I have to think that Ubuntu did something with that partition, otherwise why would Windows 10 want to scan/repair it?

---

### Post by RobGoss on 2016-11-06
Hello and welcome to the forum, Ubuntu Live session **will not, **make any changes to your Windows system partitions **unless,** the user had made those changes to any partitions. If you were only using the live CD and did not make any changes to your Windows partition then everything should be as it was before you ran that live session  

Question? when you boot in to your Windows desktop is everything still running as it was before you ran that Live session?

---

### Post by The Cog on 2016-11-06
I invite others to correct me if I'm wrong, but I think that as soon as you mount an NTFS partition, this sets a flag marking it as needing a scan and fix next time windows uses the partition. This is regardless of whether you make any changes such as renaming, moving deleting or adding files/folders, and is done just as a precaution. So it's something I would expect to see happen, and it would not worry me.

---

### Post by RobGoss on 2016-11-06
**The Cog,** I believe you are correct I see this on one of my dual boot machines but I've never really worried about it because I know it's a Windows feature just checking the system

---

### Post by Impavidus on 2016-11-06
Changing the partition (better not do that) or mounting it read-write mode may modify things on the ntfs partition. Mounting it read-only will not.

---

### Post by delerious2 on 2016-11-06
> **RobGoss said:**
> Question? when you boot in to your Windows desktop is everything still running as it was before you ran that Live session?

Everything seems OK.  Although the E drive is the HP_TOOLS partition, which I believe contains diagnostics tools that are only available from the BIOS.


> **The Cog said:**
> I invite others to correct me if I'm wrong, but I  think that as soon as you mount an NTFS partition, this sets a flag  marking it as needing a scan and fix next time windows uses the  partition. This is regardless of whether you make any changes such as  renaming, moving deleting or adding files/folders, and is done just as a  precaution. So it's something I would expect to see happen, and it  would not worry me.

Maybe the flag is only set on FAT32 partitions?  I had actually clicked around on the C and D drives, which are NTFS partitions, as well as the E drive which is a FAT32 partition (not NTFS as I originally thought).  But I only saw the "scanning and repairing" message for the E drive, not the C and D drives.


> **Impavidus said:**
> Changing the partition (better not do that) or  mounting it read-write mode may modify things on the ntfs partition.  Mounting it read-only will not.

The C, D, and E drives were mounted automatically when Ubuntu booted up.

---

### Post by sgage on 2016-11-06
> **The Cog said:**
> I invite others to correct me if I'm wrong, but I think that as soon as you mount an NTFS partition, this sets a flag marking it as needing a scan and fix next time windows uses the partition. This is regardless of whether you make any changes such as renaming, moving deleting or adding files/folders, and is done just as a precaution. So it's something I would expect to see happen, and it would not worry me.

I have dual booted Windows and Linux for years, and have never seen this behavior. I essentially use my Windows partition, which of course in NTFS, as a data partition to share between Windows and Linux, so it is getting hammered from Linux all the time, and I never had it ask for a chkdsk at my next Windows boot.

---

### Post by cariboo on 2016-11-07
> **sgage said:**
> I have dual booted Windows and Linux for years, and have never seen this behavior. I essentially use my Windows partition, which of course in NTFS, as a data partition to share between Windows and Linux, so it is getting hammered from Linux all the time, and I never had it ask for a chkdsk at my next Windows boot.

I had exactly the opposite experience, when this laptop was setup in a dual boot configuration, almost every time I booted Windows 10, it went through the check and repair sequence before booting windows. I very rarely accessed the windows partitions. I solved the problem by getting rid of Windows. :)

---

### Post by mastablasta on 2016-11-07
> **delerious2 said:**
> 
The C, D, and E drives were mounted automatically when Ubuntu booted up.

no, they weren't. you see them in file manager, but they are not actually mounted.

try unmounting the disk before boot see if that makes a difference. also mounting as read only might remove the issue. it really could be some windows feature.

---

### Post by delerious2 on 2016-11-14
> **mastablasta said:**
> no, they weren't. you see them in file manager, but they are not actually mounted.

try unmounting the disk before boot see if that makes a difference. also mounting as read only might remove the issue. it really could be some windows feature.

Ah you're right, they only mount once you click on them.

Well I did try booting up with the Ubuntu CD a few more times and mounted the Windows partitions without unmounting them to see if I could reproduce the issue, and I don't see that "Scanning and repairing" message anymore when I boot up Windows.  So it will remain a mystery as to why it happened that one time.

---

### Post by alexjpowell on 2016-11-14
I used to dual boot, a long time ago (when I was a kid and would play games)
Whenever I booted into Windows after a few weeks of using Ubuntu it would always be really slow for some reason

---

### Post by mastablasta on 2016-11-14
> **alexjpowell said:**
> 
Whenever I booted into Windows after a few weeks of using Ubuntu it would always be really slow for some reason


that's because antimalware is run and it can eat up all resoruces. if you have it on all the time and windows only then this is run peruiodically in the backgorund not all at once so it is much less noticable. also if you leave it without boot it iwll suddenly attempt to do all updates an disnce in old windows these are done by each program individually  they will all run their update systems at once. so it can slow it all down. 

i know this because there was a period i would use mostl ylinux on my little laptop. but then i needed to use it for some MS office work. specs of the PC arent' that great and it was all slow as hell until it updated all the stuff and did all the scanning. after that was all done, it was not much slower than linux.

---

