---
title: "Windows install deleted linux partitions. WHY?!?!?"
date: 2014-07-09
forum: General Help
---

### Post by Kr0nZ on 2014-07-09
So recently I wanted to reinstall windows, something I like to do a couple times a year.

After cleaning up unused partitions using gparted, leaving only my ubuntu partition and home partition intact, I rebooted and booted from a windows 7 USB drive (which didn't work the first couple times, so I had to boot back into ubuntu, so I know my ubuntu partition was still working correctly after the clean up), I proceeded with the windows install and everything went normally. Then I booted into my Ubuntu live usb, to do what I was just expecting would be to reinstall grub, but I first decided to check gparted and to my surprise all my ext3 partitions were gone, only my newly created windows drives and the linux swap drive were visible, my swap partition was actually moved forward about 10GB because it was initially at the very end of my drive. 

After some Googling I did find a utility called testdisk, which allowed my to recover my home partition but my ubuntu system drive was gone (it actually found a 20gb, but examining the files inside it seemed to have become corrupt).

I tried Googling this partition disappearing problem but all i could find was reports of grub needing to be reinstalled, which wasn't the problem I was having, i already knew grub would need fixing.

Now what I would like to know is how this happened so I could avoid it in the future?
Ive installed windows after linux many times but have never had this problem happen before.

I first thought that maybe windows rewrote the partition table, but then why would my swap drive still be there albeit in a different location.

---

### Post by Impavidus on 2014-07-09
That's the Windows installer. When it repartitions the drive and encounters something it doesn't know, it can do strange things. Remarkable that it didn't destroy your swap partition. But good that you could recover your /home partition. Reinstalling Ubuntu should be easy.

It seems that this problem can be prevented by using gparted to create the ntfs partitions for Windows. Then the Win installer doesn't have to create partitions, just allow it to format them. Then it shouldn't delete Linux partitions.

---

### Post by Bucky Ball on 2014-07-09
A/ A legal copy of Windows?
B/ Installed in UEFI or Legacy?
C/ If legacy, how many partitions do you have on the drive now? (Win 7 I think uses three, and if you had two already, you can only have four partitions.)

If you left two partitions on the drive and it was a legacy drive/install, then attempted to install three Windows 7 partitions, that could be your problem, but never seen this happen because of it before. Always a first time.

Windows needs to be on a primary partition, so I generally leave a primary partition at the beginning of the drive and create an extended partition with the rest of the space. You can have as many logical drives/partitions inside an extended on as your system can handle, theoretically. The extended partition still only counts as one partition, like a container for the logical partitions.

PS: I leave free space for the Windows partition and create the NTFS partition for Windows during the Win install, not using Gparted prior to it.

---

### Post by yancek on 2014-07-09
> Windows needs to be on a primary partition

Actually, only the boot files need to be on a primary.  The 7forums link below (posts 7 and 8) give some info on that.  The case is with two versions of windows (xp and 7) and this has been the case for some time.  I had windows 98 years ago and installed windows 2K and found to my surprise the w2K boot files were on the w98 partition and the w2k system files on a logical partition.  

[http://www.sevenforums.com/installation-setup/25603-install-win7-logical-partition.html](http://www.sevenforums.com/installation-setup/25603-install-win7-logical-partition.html)

---

### Post by kurt18947 on 2014-07-09
> **Impavidus said:**
> That's the Windows installer. When it repartitions the drive and encounters something it doesn't know, it can do strange things. Remarkable that it didn't destroy your swap partition. But good that you could recover your /home partition. Reinstalling Ubuntu should be easy.

It seems that this problem can be prevented by using gparted to create the ntfs partitions for Windows. Then the Win installer doesn't have to create partitions, just allow it to format them. Then it shouldn't delete Linux partitions.

I ran into an issue with Win7 creating two partitions.  I mentioned it here and Old Fred said that Win7 will create two partitions when installing to unallocated space.  If you first create an NTFS partition like impavidus suggests, it should only need/use one partition.  I didn't know about not deleting a linux partition when installing to a predefined NTFS partition.  That's handy to know, thanks.

---

### Post by oldfred on 2014-07-09
I have seen several cases where installs erased just the Linux partition in the extended partition but left swap. Several were able to recover the Linux partition, one or two did not.

Best to run export of partition table if MBR or run bootinfoscript or Boot-Repair reports to fully document partitions so you can easily recover them.

Only for MBR(msdos)
 Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

This backs up gpt partition table but is not a text file like sfdisk's.

 sgdisk --backup=table /dev/sda

---

