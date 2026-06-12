---
title: "How to recover partitions deleted by mistake?"
date: 2014-06-10
forum: General Help
---

### Post by tassadar2 on 2014-06-10
Hi all,

I have delete a whole disk that contained a linux  installation using "clean" command on Windows using diskpart. After doing  that I realized I had delete the wrong disk.

How could I recover it? I have write nothing nor create any partition on the disk after doing this.

The disk is a SSD.

Many thanks in advance

---

### Post by coffeecat on 2014-06-10
So long as the clean command in diskpart has only removed the partition table - I'm not familiar with that utility - you should be able to recover your partitions using testdisk. If diskpart has zeroed out all of the hard drive, this will not be possible. A couple of links for you:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

The first is the main documentation for testdisk. The second is a bit more chatty and user-friendly, but is somewhat out-of-date now, showing obsolete screenshots. Nevertheless, you might find it useful.

**EDIT**: I didn't realise diskpart was built into Windows. It's been years since I've used Windows. I found this:

[http://support.microsoft.com/kb/300415](http://support.microsoft.com/kb/300415)

> clean [all]

Use the clean command to remove partition or volume formatting from the current in-focus disk by zeroing sectors. By default, only the MBR or GPT partitioning information and any hidden sector information on MBR disks is overwritten. If you specify the all parameter, each and every sector can be zeroed, and all data that is contained on the drive can be deleted.

If you didn't use the all parameter, then you should be OK.

---

### Post by tassadar2 on 2014-06-10
Many thanks for your help, coffeecat,

I've install testdisk in another kubuntu installation and run it, but when I select Analyse it found nothing, then if i select "Quicksearch" it finds an unrecoverable NTFS partition that can't be the one i'm looking for :(

I made the "clean" (not clean all) and then didn't do anything else to the disk, I can't believe it's impossible.
Any help?

Thanks

---

### Post by tassadar2 on 2014-06-10
UPDATE: I have recover the main partition so I have access to the disk when I book from other one.

The problem is I cant book from it, and I see that its because I have recover a /dev/sda1 but it appears as "not assigned" instead of "extended", and I have no recover the linux-swap partition that should be after this main partition

Regards

---

### Post by dragonfly41 on 2014-06-10
This is a similar case to yours ...

[http://www.tomshardware.co.uk/forum/299074-32-accidently-diskpart-clean-command](http://www.tomshardware.co.uk/forum/299074-32-accidently-diskpart-clean-command)

Testdisk should do it.

---

### Post by oldfred on 2014-06-10
Because swap is unformatted space test disk does not always recovery it. Especially if you have a encrypted /home.
But it should boot if swap is only issue with perhaps an error message. Then you can recreate swap, although better to create it from a live installer as gparted may not work inside your working system as it cannot change any mounted partitions.

But if when testdisk restored partitions, it created new UUIDs, you will have to reinstall grub and update fstab with all the new UUIDs.

Post link to bootinfo report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
If you have more than only drive, do not run auto fix. That installs grub to every MBR and usually you only want it in the MBR of the Ubuntu drive.

---

### Post by tassadar2 on 2014-06-10
Many thanks dragonfly,

I've get this:

[IMG]http://i60.tinypic.com/rlm2ad.png[/IMG]

But disk is not booteable. The other disk I have with the same Kubuntu installation is this:

[IMG]http://i58.tinypic.com/2wlyrlv.png[/IMG]

Appart from the size of partitions the difference is obvious, but I have re-run testdisk but it doesn't allow me to set partition as extended neither allow to recover the linux-swap partition.

Regards

---

### Post by tassadar2 on 2014-06-10
Many many thanks, oldfred,

Once in the past I wanted to "clonezilla" this same installation from a 256Gb disk to an smaller one (120) but I couldn't since clonezilla doesn't allow to shrink. This time I got it making a fresh install on a 120Gb disk and then shrinking by myself the system partition from the 256gb disk and once it had the exact size of the fresh install from the 120gb disk I cloned the system partition.

I'm going to try something similar and then I'll tell

regards

---

### Post by tassadar2 on 2014-06-11
I want to thank the help.

I finally recovered the disk, the procedure were:

-Use testdisk to recover main partition
-Installing fresh kubuntu 14.2 onto a new SSD
-Resize recovered partition to exactly match in size with new one on the new installation (using gparted)
-Clone partition to partition with clonezilla
-Restore grub using "boot repair disk"
-Boot on recovered disk
-Modify grub to avoid 10 secons wait screen on every boot.

Regards

---

