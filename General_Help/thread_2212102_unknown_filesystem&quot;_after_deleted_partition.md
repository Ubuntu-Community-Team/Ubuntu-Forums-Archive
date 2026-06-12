---
title: "unknown filesystem&quot; after deleted partition"
date: 2014-03-19
forum: General Help
---

### Post by Nagmani_Bhushan on 2014-03-19
Hey all,


Recently dual booted windows 7 with ubuntu 10.10. I later, realizing i was running out of hard drive space, I deleted the partition which had ubuntu on it while running windows. Later windows auto rebooted my computer and, where grub usually popped up, it said:


error: unknown filesystem.
grub rescue>


I checked on another thread but it was a different scenario, they hadn't deleted the ubuntu partition.


please help me on this i am thankful to you..

---

### Post by Mark Phelps on 2014-03-19
IF you installed Ubuntu to a separate partition, and did this after Win7 was already in place, it's likely that you overwrote the disk MBR in the process.

That MBR was not rewritten when you removed Ubuntu, so it still points there by default.

Had you asked about this first, we would have told you to use Win7 Backup feature to create a Repair CD -- which you could have then used to rewrite the MBR -- PRIOR to removing Ubuntu -- and you wouldn't have this problem.

Since you can't get into Win7 now, you can't create that repair CD.  Instead, you have the option of PURCHASING the CD ISO image from the link, and then burning it to CD: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

You will need to download that ISO file and burn a CD using it.  Once you have that, boot using it and run STartup Repair three times -- that's right, three times.

That said, if you installed Ubuntu inside Windows, you removed a Windows partition in the process, and that is a very different problem to fix.

If you're not sure which scenario applies, then boot from Ubuntu install media, get to a desktop, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one) -- that will list out the partitions on the drive.

---

### Post by efflandt on 2014-03-20
If you have regular msdos partitions (that sudo fdisk -l can see) you should be able to restore a standard DOS/Win mbr with syslinux's mbr.bin from an Ubuntu iso booted from CD/DVD or USB:```
sudo dd bs=440 count=1 conv=notrunc if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```Otherwise see [http://www.syslinux.org/wiki/index.php/Mbr](http://www.syslinux.org/wiki/index.php/Mbr) for some other mbrs including gpt, but note that the path to the other syslinux related bin files is /usr/lib/syslinux/

I have used this method in a couple of cases to restore a Windows mbr, like after temporarily trying Ubuntu on a laptop I was setting up for someone, or when for some reason Windows needed to have control of the mbr while installing a service pack. I also used that after installing grub on a partition instead of the mbr when Windows programs storing data in what they thought was an unused part of the mbr kept messing up grub2. Although, grub2 has since been updated to get around Windows programs (in my case Dell DataSafe) that are known to do that.

I would not try this with Windows 8 since I am not familiar with UEFI or Secure Boot and how that all works.

---

