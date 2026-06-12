---
title: "All my files are gone and no in recycle  bin can i recvover"
date: 2007-02-09
forum: General Help
---

### Post by CameronCalver on 2007-02-09
Hello everyone someone on our computer deleted like all of my stuff acidentally and deleted them out of recycle bin.
Is there a way i get get them back somehow?

---

### Post by mrpeenut24 on 2007-02-09
What format is your disk? (reiserfs, ext3, etc.)

---

### Post by meng on 2007-02-09
> **CameronCalver said:**
> Hello everyone someone on our computer deleted like all of my stuff acidentally and deleted them out of recycle bin.
Is there a way i get get them back somehow?
Yeah, give that guy an atomic wedgie.
Oh, wait on, you mean you want to get the FILES back ... ah.
(Sorry to make light of your tragedy, but you have to see the funny side.)

Seriously, my first bit of advice is DON'T touch that computer at all until you've worked out a strategy for recovering those files ... I hope you're using another computer to post in the forum, for example. If it's very important, get professional help.

---

### Post by mrpeenut24 on 2007-02-09
DEFINITELY!!! Do not install, download, move, or otherwise change any files on that computer.  This includes temp files, so you probably want to use internet from another computer.  I've got a good bit of experience in HDD recovery.  The first thing to do is figure out the file system.  Once you have that, you'll want to get a boot recovery disk, unless the files are on an external/non-system drive.  You can try to google 'recover files (filesystem)'.  I haven't done much recovery in linux, so I don't know how easy it is for their fs's, but if you can get the boot disk, or install a program on an external/flash drive, you should be able to run it & recover what you need no problem, assuming you haven't overwritten the sectors.

---

### Post by dannyboy79 on 2007-02-09
use knoppix and dd_rescue to make an image and then you can mount the image and take out files that you want.

---

### Post by mrpeenut24 on 2007-02-09
That's another good idea, however, if it's a large hd, it's often more trouble than it's worth.

---

### Post by CameronCalver on 2007-02-09
ok i dont no what format it is its just my /home folder on my standard ubuntu install so what  program do you guys recommend

---

### Post by mrpeenut24 on 2007-02-09
Is this the only OS on your hd?  Try ```
sudo fdisk -l
``` and paste the output.

---

### Post by CameronCalver on 2007-02-09
yeh only 1 os

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19079   153252036   83  Linux
/dev/hda2           19080       19457     3036285    5  Extended
/dev/hda5           19080       19457     3036253+  82  Linux swap / Solaris
calver@ubuntu:~$

---

### Post by mrpeenut24 on 2007-02-09
Sorry....do 'blkid' (BLKID)

---

### Post by CameronCalver on 2007-02-09
ok this is what i got 

calver@ubuntu:~$ blkid
/dev/evms/hda5: UUID="d8ed5b8c-e4fb-467b-bea2-5fe767a74afc" TYPE="swap" 
/dev/evms/hda1: UUID="2b602861-dfff-4ceb-95d3-8245f59e4c2b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda1: UUID="2b602861-dfff-4ceb-95d3-8245f59e4c2b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="d8ed5b8c-e4fb-467b-bea2-5fe767a74afc" TYPE="swap"

---

### Post by mrpeenut24 on 2007-02-09
<grimaces>
ext3 is a nearly impossible to recover file system.  Basically, when a file is deleted, the sectors are overwritten instead of just marked as 'deleted'.  If the files are REALLY important, you might want to make an image, and see if you can get it professionally recovered, or if you feel confident enough, you can google "recover files ext3".  [Here's]("http://linux.sys-con.com/read/117909.htm") a page that talks about the difficulty of recovering the files as well as attempting to do it on your own.

---

### Post by CameronCalver on 2007-02-09
yeh well luckyly  it wasnt on my computer and it was on there computer so there fault

---

### Post by mrpeenut24 on 2007-02-10
hehehe so I assume that the files weren't terribly important?

---

