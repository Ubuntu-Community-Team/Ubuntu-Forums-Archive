---
title: "Strange Partition Table"
date: 2013-03-23
forum: General Help
---

### Post by chenzhao123 on 2013-03-23
I am a newbie to Linux and have Ubuntu and Windows8 on my computer. Several days ago my computer crashed with disk errors and I have to reinstall Ubuntu. I used Acronis Disk Utility in Windows to delete and format the spaces where Ubuntu used to be. These regions now appears to be unallocated under windows. In live Ubuntu, however, gparted cannot recognize the partition table and reports overlapping. The output of the fdisk -l command shows a strange partition table, where /dev/sda1 spans the entire disk.
Does anybody have some ideas to fix this problem?
Thank you!
#####################################################################
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9bf9cbf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       191816100   948092039   378137970    5  Extended
/dev/sda2   *   730288192   939384809   104548309    7  HPFS/NTFS/exFAT
/dev/sda3       948099072   976771071    14336000    7  HPFS/NTFS/exFAT
/dev/sda5       191816169   527381819   167782825+   7  HPFS/NTFS/exFAT
/dev/sda6       939384873   948092039     4353583+  82  Linux swap / Solaris

---

### Post by agillator on 2013-03-23
It appears your utility created an extended partition and put everything else in it. A disk can have only four physical partitions. That is why most of the time you will find the last (fourth) partition being what is called an extended partition. In there are logical partitions. You look at them as partitions, but the system really does not. You can have as many logical partitions in the extended partition as you wish since they are not real partitions. That is why the partitions appear to be overlapping. If you actually map it out, you will find that sda2-6 all lie within sda1. Of course they, the logical partitions, are treated for our purposes as real physical partitions. If fdisk in Linux is reporting the actual layout as you describe, gparted should also. It may complain that there is only an extended partition, but it should still show and work with what is there. Based on this, what is really being shown? Is gparted really not identifying anything and giving up or what?

---

### Post by deadflowr on 2013-03-23
Your partitions just look weird.

Look over this page to see if it will help:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by chen123 on 2013-03-23
Gparted only shows an entire disk (500GB) without partition. And for this reason, I could not install it to the desired "partition". Is there any solutions?

Thank you!

---

### Post by fantab on 2013-03-24
Can you boot Windows8?

You should read the link in post #3 about [FIXPARTS]("http://www.rodsbooks.com/fixparts/"). It is a utility to fix faulty or corrupt partitions and partition tables.

After running fixparts you can use Gparted from Ubuntu LiveUSB/DVD to recreate the partitions. If you are installing Windows then I suggest you use Windows Install disk to create and format Windows partitions.

---

### Post by oldfred on 2013-03-24
+1 on fixparts.

While your actual partitions by sectors do not seem to overlap, you cannot have a primary partition sda1 thru sda4 inside the extended partition. It looks like sda2, a primary is inside sda1, the extended. Fixparts should sort that out.

I might make a backup of partition table first.
       First backup partition table.
sudo sfdisk -d /dev/sda > parts_sda.txt

---

### Post by chen123 on 2013-03-25
Thank you all! The problem is finally solved by fixparts.

---

