---
title: "Gparted clone gpt parts, smaller drive?"
date: 2015-03-01
forum: General Help
---

### Post by maestrobwh1 on 2015-03-01
I have ubuntu (yeah) on a GPT drive, EFI dual boot Windows 8. It is on a 320 GB drive.  I wish to go to a 240 GB SSD.  I have found some posts around the web about using a combo of clonezilla and gparted on MBR drive.  It is somewhat oddly involved.  

Question:
I assume that UEFI with GPT would just boot if I copied the two FAT partitions at the beginning of the drive with gparted before copying and shrinking the other partitions (win 8, data partition, recovery and ubuntu?) to the exact sequence on the SSD? 

Yes, No, Maybe?  Ubuntu would probably play nice and boot, but should Windows 8 theoretically still boot?

---

### Post by oldfred on 2015-03-01
Do not know about Windows.

But gpt must only be copied on a full drive basis not a partition. You can copy the data with cp or rsync, not not tools that copy internal structure like dd or image copies. Gpt has internal GUID as well as UUID that must match partition table at beginning of drive and backup at end of drive.

       Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)
Do not use dd with gpt partitions. Whole drive ok if old drive not used anymore, or no duplicates.
But do not use dd for copies from MBR to gpt partitioned drives, can use cp -a
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)
Restore full drive dd backup - resync gpt partition tables and fsck pursuvant
[http://ubuntuforums.org/showthread.php?t=2145563](http://ubuntuforums.org/showthread.php?t=2145563)

With Ubuntu a new install is really the best alternative & copy /home over if you want it on SSD.
Windows also has internal data. Most of the image type backup tools work to restore back to the same partition and drive and may install to a new drive, but then depends on UUIDs and with gpt GUIDs. Check carefully on image copies and how they work.

---

### Post by maestrobwh1 on 2015-03-01
I found this: I need another set of eyes to verify that I should be able to do this, as I am somewhat sure of what I am doing but GPT is somewhat foreign to me: [http://kudzia.eu/b/2013/07/cloning-gpt-disk-to-a-smaller-drive/](http://kudzia.eu/b/2013/07/cloning-gpt-disk-to-a-smaller-drive/)

Looks I can boot via Ubuntu live media, use Gparted to copy the HDD partitions to SSD once GPT table is created on it then shrink each partition, then follow series of gdisk commands to repair GPT table?  

Or I can just get a larger disk and dd the whole 320GB HDD but I don't really need a 500 GB disk in my small laptop and could save the $80 between the 240 and the next common size up, 480-512 GB SSD drives.  A decent 240 GB Crucial drive is about $99.  The larger sizes are around $180

I figure I could just create a new partition table in old HDD drive so I could use it as external device.

---

