---
title: "A GRUB question"
date: 2019-12-02
forum: General Help
---

### Post by ra7411 on 2019-12-02
I've got a new 4tb HD. I partitioned it with a 30gb partition to put an auxillary o/s into.

Is there any way that I can restore (qt5-fsarchiver) my main o/s sda1 into this new sdb1, then use some program that will search for all the Ub o/s'  on the machine and re-write GRUB to give the sdb1 o/s as a boot option?

Thanks

---

### Post by oldfred on 2019-12-02
Best/easiest just to do a new install. 
New drive has to be gpt partitioned. 
Is system UEFI with UEFI installs or BIOS?
I used to add both an ESP & bios_grub so I could configure for either UEFI or BIOS boot. But since only using UEFI for years now, I only have UEFI and add an ESP. If I ever needed BIOS I can add a bios_grub anywhere in the first 2GB of a drive.

New install to sdb drive and sudo update-grub will find all other installs, if all installs are in same boot mode. If not in same boot mode, you cannot boot from grub.

       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive, but smaller partition if just for emergency boot. 

If you want exactly same, you can copy /home (but not your data) and export list of installed apps & reinstall that list. My /home with no data is 207M    ./home. I have all data & some hidden folder like Firefox & Thunderbird in data partition, so very little data in /home.

      
 [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by kevdog on 2019-12-03
@oldfred

What is layout and sizes of your partitions?  I'm only curious.  Over the years I've moved from bare metal to almost doing every install as a VM.  I'm currently using xcp-ng as my hypervisor, and UEFI support within this hypervisor is in its infancy.  They've added UEFI support recently but xcp-ng acknowledges it's still pretty primitive.  As a result I usually format my virtual drives using a GPT partition table and BIOS boot.  I'm curious how you layout your partitions to either accomodate UEFI or BIOS boot.  I'd like to incorporate this strategy if possible.

---

### Post by TheFu on 2019-12-03
I don't use UEFI bios for VM installations. Also, I don't worry about a VM having a virtual GPT disk, since none will ever have over 2TB .... or 100GB of storage.  By that point, it will be accessing NFS storage.

As for installing an fsarchive into a different partition, provided the data fits, it should work.  Then I would boot into a Try Ubuntu flash drive, go into recovery mode and run **grub-install** where I wanted, perhaps over wherever it was already installed, then run **update-grub** to search all the different attached partitions for OSes and install those.  This handles grub, but not the fstab for the restored partition.  Inside that partition, there will be an /etc/fstab file which needs to be modified manually - probably just a / partition and swap (either swap file or swap partition) if the OS boot was legacy BIOS.  A few more partitions if UEFI which will manually need to be merged with any existing ones.  If you are dual booting, having a swap partition is much better than having swapfiles in /. A swap partition can be shared by the different Linux OSes as they boot.

But have you considered using a virtual machine instead?

---

### Post by oldfred on 2019-12-03
TheFu uses & has promoted virtualinstalls. I plan to try one, soon.

This was my partitioning back in 2015. Not changed a lot, but versions of Ubuntu installed have almost all changed.
If you look carefully you will see not all space initially used. I have added more 25 or 30GB  for installs and adjusted size of my data partition.

[https://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](https://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by TheFu on 2019-12-03
Virtualization is a handy tool and many companies use it as the default for all server installations. The installs onto physical hardware is for 1 purpose only - to become a VM host server.

Here's a laptop LVM layout that uses encryption on an SSD:
  [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)
"Why" is included in that link.

For most things and LV (logical volume) can be considered a partition.  A file system is put onto an LV, just like a file system is put onto a partition.  My /home LV is too large in that example.  

LVM is like partitioning that doesn't need a reboot to change and allows growing on live, running, file systems. Growing an LV as-needed is easy, provided that the VG has some empty space available.  LVM is an abstraction layer with many benefits at the cost of some complexity. LVM makes moving from 1 partition to another just a few commands  thanks to *pvmove*.  LVM is useful inside VMs, but it is most useful for physical installations, provided all the storage isn't allocated to LVs.  We never know which parts of a system are going to grow.  Allocate what you need if you use LVM because growing an LV is 5 seconds.  OTOH, resizing a partition takes downtime and almost always ends up with storage in the wrong place.  With enough unused storage, there are multiple ways to shrink an LV, but it is a little pain even if no downtime is needed. 

Using fsarchiver to restore to an LV: 
  [https://ubuntuforums.org/showthread.php?t=2422477&p=13871800#post13871800](https://ubuntuforums.org/showthread.php?t=2422477&p=13871800#post13871800)

---

### Post by kevdog on 2019-12-03
@TheFu

Nice reference post showing your partitions.
Why ext2 for /boot however?  Why not ext3/4?

For virtualization, what are you using as the host OS?

---

### Post by TheFu on 2019-12-03
> **kevdog said:**
> @TheFu

Nice reference post showing your partitions.
Why ext2 for /boot however?  Why not ext3/4?

For virtualization, what are you using as the host OS?

ext2 isn't journaled, but for tiny, mostly read-only, storage, we won't be stuck waiting 45 minutes for an fsck to finish like in the old days.  ext2 won't be as hard on SSD storage, though that wasn't my main consideration.  If it were, I'd have used f2fs.
I suppose moving it to ext3 or ext4 could be done, but really it isn't worth my time/effort.  I don't recall specifically choosing ext2, suppose it was the *default* for full disk encryption + LVM setup?  Using MBR partitioning was also the choice of the installer. A few years ago I tried to force using GPT with full disk encryption + LVM and that efforts failed.  There's the ideal world and there's the world that the Ubuntu installer makes easy. l)

---

### Post by kevdog on 2019-12-03
So I take it you're using Ubuntu, not Debian as the host OS?  
I recently installed Arch within VM -- going through adding ZFS into kernel, partitioning etc.  I've set up Arch about 10 times on previous installs, however I really only go through the process about once every other year.  It seems each time I go through it, I pick up more subtle nuances -- either that or more steps are added to the installation wiki -- I'm not sure.  I've never really tried to install Ubuntu through the installer with complex partitioning.  Maybe I should go through the process again just to refresh myself.

---

