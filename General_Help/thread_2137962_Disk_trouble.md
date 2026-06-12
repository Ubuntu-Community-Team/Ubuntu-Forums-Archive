---
title: "Disk trouble?"
date: 2013-04-22
forum: General Help
---

### Post by ArminasAnarchy on 2013-04-22
So, yeah, after trying to install Xubuntu 12.04 for about the sixth time and it repeatedly failing, I come to you!

A run through of what the issues are (bear with me):

Installation proceeds smoothly (using the alternative .iso image, I prefer the text based installer, and the GUI has been buggy in the past). When asked where I want to install GRUB, I select the MBR on /dev/sdb (that's the default, and presumably the installer would have the sense to load the install medium as /dev/sda right?). Pleased as punch up till now (no issues detecting/configuring network hardware etc. - which is usually a hitch, wireless and Linux has come on a *lot* even since I've been using it, but there's still work to be done).

Reboot -> "DISK BOOT FAILURE. INSERT SYSTEM DISC AND PRESS ENTER". Cue irritated grunt, but no worries (I think), GRUB's probably just installed incorrectly. I'll just re-do the installation and hopefully it'll behave this time.

Again, no luck. I've just had a problem on my laptop with corrupted GPT (now fixed, thankfully). So I assume the problem can be fixed in the same way - download and boot PartedMagic, use GParted to fix the table, wipe the disk for good measure, and re-install. GParted through out some weird error messages but otherwise seemed to be happy.

Well, following that process - I'm here. It failed again, and presumably those "weird error messages" are the fault.  I go to create a new partition table and the error that pops up is:[CENTER][U][B]
Libparted bug found![/B][/U]
Invalid partition table -recursive partition on /dev/sdb.

[/CENTER]
(Options are "Cancel" and "Ignore", I've just gone for "Ignore" previously.)


I googled this and came across something on the ArchForums (which always scares me a little - I'm reasonably comfortable with Ubuntu - but I've not got the long list of commands memorised to install/use Arch). It said something about the MBR being screwed - which makes senses - and that it must have been done with some low level tool like dd. The solution offered on this forum (in another thread) was wipe the disk and see where you end up - I used PartedMagic's "Erase Disk" tool to try that (there was even an option to use dd - which I selected - thinking "if dd broke it, dd should un-break it" - wrongly, it seems). As stated, no luck.

So - help appreciated! Using the US English keyboard layout (the default in Parted Magic) is absolutely doing my head in, so the sooner the better :P. Obviously having no OS on this computer isn't the best, either, and I'm afraid I've caved, letting my grief from siblings moaning that they can't play games on the PC, become your grief :P

Worse comes to the worse, I'm going to see if the partitioning tool  used during the Windoze 7 setup can make any more sense and correct the  problem. Is this a pointless waste of time?

PS - quick note on the HDD, but this shouldn't be relevant. It's an old 80GB IDE drive scavenged out of a computer with <256MB DDR RAM and an ancient CPU I'd never heard of (being only 20, that probably isn't THAT surprising, but hey!). As far as I'm aware, it previously had a copy of Windoze XP on it, but it might have been '98 or ME. I never booted it - the PSU's kettle cord port was messed up, and didn't want to give the coffin-dodging hardware the chance to go up in flames. The thing hadn't been on in a while, but since data is writing smoothly (AFAIK) during installation - and it's being detected as present in the system, the disk can't be completely beyond repair. Can it? :(

---

### Post by Cheesemill on 2013-04-22
Does the machine you're installing on use UEFI or BIOS?

If your trying to install on a GPT partitioned disk with a BIOS system then did you create the required Grub BIOS partition?
[https://wiki.archlinux.org/index.php/GRUB2#GUID_Partition_Table_.28GPT.29_specific_instructions](https://wiki.archlinux.org/index.php/GRUB2#GUID_Partition_Table_.28GPT.29_specific_instructions)

---

### Post by ArminasAnarchy on 2013-04-22
BIOS, AFAIK. The computer's from around 2006/7 -  which is too old for the likelihood of it being UEFI to be high, right?

And in any case - that wouldn't explain the GParted bug, would it?

Also - with Xubuntu being the only system installed, that shouldn't matter?

From what I've read that kind of issue wouldn't throw out the weird error messages and/or explain the problem.

I did make the installation medium on a UEFI computer - but it would be stupid (not to mention incredibly irritating) if that was the cause of my trouble :P

---

### Post by Cheesemill on 2013-04-22
It doesn't matter if you only have the one OS.

If you are booting with BIOS and a GPT partitioned disk then you ***have*** to have a grub BIOS boot partition otherwise grub has nowhere to put its files. Failure to create this partition will mean that grub doesn't get installed which would cause the issue that you are seeing. Note that this isn't the same thing as having a separate /boot partition.

If you don't have a good reason for using GPT with your drive (>2TB or >4 primary partitions) then you could just use the old msdos format instead. In gparted select the drive then go to Device > Create Partition Table > OK.

Which device is gparted complaining about? You may well find that it's the USB stick that you are installing from ***not*** your hard drive. I come accross this error all the time when using gparted but it only complains about my USB device.

---

### Post by ArminasAnarchy on 2013-04-22
Just in case it's relevant - I also used the PartedMagic "Disk Erase" tool to "External( Erase MBR ): Zap (destroy) MBR and GPT data structures. That was before running the dd thing, which was before trying to run the install clean (again) :(

fdisk -l gives the following output:

root@partedmagic:~# sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000937c9

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 8074 MB, 8074035200 bytes
64 heads, 32 sectors/track, 7700 cylinders, total 15769600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x643a3365

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           0      630783      315392   17  Hidden HPFS/NTFS

Disk /dev/sdb1: 322 MB, 322961408 bytes
64 heads, 32 sectors/track, 308 cylinders, total 630784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x643a3365

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           0      630783      315392   17  Hidden HPFS/NTFS

According to [this]("https://bbs.archlinux.org/viewtopic.php?id=149001") link, the issue is because the MBR basically isn't there - it starts at sector 0 and the first 512bytes need to be for the MBR. But how to fix this? Is there a way to manually move the partition from 0 and replace it with a (working) MBR?

---

### Post by ArminasAnarchy on 2013-04-22
It's the /dev/sda which (according to the fdisk -l output) looks like the HDD to me (I certainly don't have an 80GB USB stick!).

That's the thing, the error with GParted occurs when I go to Device>Create Partition Table. And just ignoring the issue doesn't seem to fix it (that's what I did previously). Clearly this isn't just one of those bugs you can ignore in that hope that it'll go away since I can't even boot the OS :(

---

### Post by ArminasAnarchy on 2013-04-22
I've just thrown the dice and gone for the Internal Secure-Erase option in PartedMagic's "Erase Disk" program.

44 mins till completion, apparently it could brick it if it hits a firmware bug - so I'm a little nervous about this but since an Internet search hasn't revealed much, and the drive is ancient (and not necessarily working anyway, I'm assuming it is, but current evidence does seem to suggest the contrary :P), I guess I don't lose too much if it does break down. We'll see where we end up, and I'll check in in an hour or so.

---

### Post by ArminasAnarchy on 2013-04-22
Nothing. :( Also ran a disk check using the utilities in PartedMagic, it came back clean.

---

