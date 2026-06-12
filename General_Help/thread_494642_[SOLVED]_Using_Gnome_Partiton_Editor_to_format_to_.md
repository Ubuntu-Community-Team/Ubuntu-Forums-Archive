---
title: "[SOLVED] Using Gnome Partiton Editor to format to NTFS. Help Appreciated"
date: 2007-07-07
forum: General Help
---

### Post by wwwqwerty on 2007-07-07
Allrite so here is the deal:
I need to format my second hard drive to NTFS so as I can install Windows XP on it, but I have searched all over the internet and I found GP editor. But when I tried to format it to NTFS it wouldn't let me it was blanked out.(See attachment for a screen shot.) Does anyone know why it does this and how to fix it? Or if there is another way to format it to NTFS I wouldn't mind if you told me. If you want send me an im and we can talk about it one on one through im.

Thank you in advance :D

---

### Post by louieb on 2007-07-07
You need the NTFS plugin. Easiest thing to do is get the live CD or better yet get the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") GParted is on it and other good stuff too.

---

### Post by OzzyFrank on 2007-07-07
Hmm, never seen Gparted needing an NTFS plugin... but yeah, I reckon the Live CD is the best bet, coz it should work from there. I reckon the Live CD is a great tool even for people not interested in Ubuntu, simply coz you can quickly boot to a friendly desktop, go to System > Administration > Gnome Partition Editor and partition drives easily from there. SystemRescueCD is a good tool, but hardly worth downloading just for the partitoner when the Live CD has it.

---

### Post by longlegs on 2007-07-07
Hi ,
when you install xp or vista the install process will format the partition to ntfs.
Good luck!
longlegs

---

### Post by wwwqwerty on 2007-07-07
> **louieb said:**
> You need the NTFS plugin. Easiest thing to do is get the live CD or better yet get the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") GParted is on it and other good stuff too.

See I have the live cd, made it yesterday, but I'm a little bit confused on how to use it. Which option do I choose to do a NTFS format? BUt thanks I will look and see if i can find that plugin your talking about.

---

### Post by OzzyFrank on 2007-07-07
Boot to the desktop, then go to **System > Administration > Gnome Partition Editor**, then choose to partition it as NTFS. Unless I am mistaken, it is as easy as that.

---

### Post by wwwqwerty on 2007-07-07
Allrite thanks man Ill see if it works.

---

### Post by louieb on 2007-07-08
> **OzzyFrank said:**
>  SystemRescueCD is a good tool, but hardly worth downloading just for the partitoner when the Live CD has it.

Setting up a PC with a working operating system to dual boot by shrinking, adding, moving, formatting partitions, replacing the MBR code is pretty major stuff. Any one of the those steps can and has turned many a computer into a doorstop. The Ubuntu live CD is a very good install CD but as a rescue CD it is far down the list. 

The [System Rescue CD]("http://www.sysresccd.org/Main_Page") is worth every bit of time it takes to download it and the 50 cents for the blank CD to burn it on. Since I fool around and break things here are a few other CDs I keep around to save my butt aggravation.
 [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") [Puppy Linux]("http://www.puppylinux.org/user/viewpage.php?page_id=1") [Knoppix Linux]("http://www.knoppix.net/") [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") 

And to defrag an Windows NTFS partition in preparation  to shrink it [JkDefrag: A better windows defragmenter.]("http://kessels.com/JkDefrag/index.html")

---

### Post by wwwqwerty on 2007-07-08
Hey thanks i used the system rescue cd worked like a charm. But I found out what the problem was, the hard drive windows was being installed on was a slave drive, so im just switching them out then it should be fixed. Thanks fro all the help.

---

### Post by kthxbai2u on 2007-12-11
Ubuntu 7.10:

> Parted currently supports DOS, Mac, Sun, BSD, GPT, MIPS and
PC98 disklabels/partition tables, as well as a 'loop' (raw
disk) type which allows use on RAID/LVM. Filesystems which
are currently fully supported are ext2, ext3, fat (FAT16
and FAT32), ReiserFS (with libreiserfs) and linux-swap.
Parted can also** detect and remove** HFS (Mac OS), JFS, ***NTFS***,
UFS (Sun and HP), XFS and ASFS/AFFS/APFS (Amiga) filesystems,
but ***cannot ******create, resize or check these filesystems yet***.

ripped straight from my synaptic package manager. I need to reformat a drive to NTFS so I can mount it with linux and restore a drive... Can anyone help?

---

### Post by rsambuca on 2007-12-12
gParted definitely can create ntfs partitions.  I have done so.

---

### Post by fjgaude on 2007-12-13
> **rsambuca said:**
> gParted definitely can create ntfs partitions.  I have done so.

My Gparted in Gutsy doesn't show that it can create NTFS partitions, only detect them. Version is 0.3.3. Do you have a later version?

Okay, I went to a CD that had version 0.3.4 and it features NTFS creation. Ubuntu Gutsy repos doesn't have that version yet.

---

### Post by stchman on 2007-12-13
> **fjgaude said:**
> My Gparted in Gutsy doesn't show that it can create NTFS partitions, only detect them. Version is 0.3.3. Do you have a later version?

Okay, I went to a CD that had version 0.3.4 and it features NTFS creation. Ubuntu Gutsy repos doesn't have that version yet.

I have created NTFS partitions using gparted on the LiveCD.  Done it many times.

---

### Post by fjgaude on 2007-12-13
The LiveCD must have version 0.3.4 on it... the released version of Ubuntu has 0.3.3. Weird.

---

### Post by atlfalcons866 on 2007-12-13
did you install ntfsprogs?

> sudo apt-get install ntfsprogs

---

### Post by fjgaude on 2007-12-13
> **atlfalcons866 said:**
> did you install ntfsprogs?

No, but I just did... oh I see says the blind man. Thanks for pointing this out. May come in handy one of these days.

My 0.3.3 version of GParted now has all the features with ntfs as it has for ext3. We learn something new every day, eh?

Thanks again.

---

