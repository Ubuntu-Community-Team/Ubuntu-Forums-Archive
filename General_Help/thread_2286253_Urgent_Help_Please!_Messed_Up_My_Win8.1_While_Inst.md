---
title: "Urgent Help Please! Messed Up My Win8.1 While Inst Ubuntu"
date: 2015-07-10
forum: General Help
---

### Post by alex418 on 2015-07-10
So I have a Dell Venue 11 Pro tablet with Windows 8.1, and I've been wanting to learn about Linux so I've spent the the last 8ish hours trying to install Ubuntu alongside.

After many different attempts and searches and thought screw it, so I chose the 'Something else' option while installing and allocated 20gb for Ubuntu, 2 for swap and a mb for the boot thingy. This was seemingly out of my entire harddrive space, 256gb of SSD.

I assumed it would use up 20gb out of the 40 I had unallocated, all went well untill my next restart where it said something about partion tables and booted straight into Ubuntu.

Normally I wouldn't care and just stick with my nice new OS, I thought I had nothing of value on my Windows install. Untill I realized that I had store every. single. photo of my son that I had copied over to sort through so my phone wouldn't be such a mess.

Is there any way I can get the photos back? They're the only thing I have left of him.

Thanks for any help.

---

### Post by oldfred on 2015-07-10
Never make major changes to a computer without good backups. Actually you always should have good backups. After a couple of hard drive total failures, I am a bit better at backups.

Is Windows still on system. But if you left it hibernated it is difficult to mount the NTFS partition from Linux.
Also it sounds like you may have installed Ubuntu in CSM/BIOS boot mode as that would require the bios_grub boot partition. So Windows may still boot if you go into UEFI and turn UEFI on, and CSM off.

Post this from Ubuntu to confirm partitions are still on drive.
sudo parted -l

---

### Post by alex418 on 2015-07-11
Hey thanks for replying, here is the log:

Model: ATA LITEONIT LJT-256 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  20.5GB  20.5GB  ext4
 2      20.5GB  20.5GB  1049kB                        bios_grub
 3      20.5GB  22.5GB  2000MB  linux-swap(v1)

---

### Post by Mark Phelps on 2015-07-11
> Is there any way I can get the photos back? They're the only thing I have left of him.

Not easily -- since your partition list shows NO Windows partitions at all!

Your best bet to recover the photos at this point is the following:
1) STOP using the drive .. period.  Every time you use the drive, you write to it and that is risking overwriting the very files you want to recover
2) Remove the drive from your PC and find a working Windows PC.
3) On the Windows PC, download and install Active@File Recovery.  The trial version will install and let you see what it can find
4) Connect your drive to the Windows PC
5) Run the file recovery app in Superscan mode -- this could take a LONG time.  Last time I used it, it took 14 hours to completely scan a 1.5TB drive
6) When the scan is done, see if it found the files you wanted to recover
7) If it did, then go online and purchase a license to do the recovery.

And in future, NEVER force the installation of an OS onto a drive that you haven't first backed up!

---

