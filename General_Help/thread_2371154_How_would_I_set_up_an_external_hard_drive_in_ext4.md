---
title: "How would I set up an external hard drive in ext4?"
date: 2017-09-11
forum: General Help
---

### Post by Evil Wayz on 2017-09-11
Lately I have had a real problem with my external hard drives getting bad sectors and not being able to fix them because they are NTFS and i don't own a windows computer.  I have acquired a 4tb drive that I plan to replace two 2tb external drives with.  As a experiment i tried chmod 777 on a 1tb external drive and it didn't work.  When I plugged it in it would suddenly become read only after a few minutes

I am running 17.04 with the standard kernel and xubuntu desktop.

---

### Post by TheFu on 2017-09-12
Don't use NTFS.  Format the new disk with ext4, copy all the files over.

I'd check the SMART data for the problem disks.  Could easily be they are failing.  What do the system logs show? Any disk errors?  Always, always, always start troubleshooting by looking at the log files for warnings and errors.  Always.

---

### Post by SeijiSensei on 2017-09-12
Try formatting the "experimental" drive as ext4 first.  With it connected, run the command "sudo blkid" which will list all the partitions on all your devices.  Let's suppose the external drive appears as /dev/sdb1.  Then run
```

sudo mkfs -t ext4 /dev/sdb1

```
If the formatting program starts to show a lot of errors, you can force it to check for bad blocks and mark them unusable with
```
sudo mkfs -c -t ext4 /dev/sdb1
```
This is very time-consuming.  It could take a day to complete.

Disk partitions have a type code, so to be nit-picky this will leave you with an ext4 filesystem on a partition marked for NTFS or FAT32.  I suspect that won't really matter, but if you want to be certain, you can change the partition type with fdisk.

```
sudo fdisk /dev/sdb
```

Note that I'm using /dev/sdb and not /dev/sdb1 here because fdisk works on the whole device.

fdisk uses a bunch of single-letter commands.  To quickly change the partition type, type "t".  If you have multiple partitions on the device, you'll be asked for the partition's number.  In this case you would type "1" when prompted.  You'll then be asked to enter the appropriate hex code for the partition type, which is "83" for a Linux partition.  Type "w" to save the changes to the disk.

---

### Post by Evil Wayz on 2017-09-12
> **TheFu said:**
> Don't use NTFS.  Format the new disk with ext4, copy all the files over.

I'd check the SMART data for the problem disks.  Could easily be they are failing.  What do the system logs show? Any disk errors?  Always, always, always start troubleshooting by looking at the log files for warnings and errors.  Always.

The drive has physical errors, I believe from running it without enough power.  (It is usb powered and was running off a Raspi, a mistake I will not make in the future.)

SHould I try just copying the files over or using something a little more hardcore like dd or ddrescue?

---

### Post by TheFu on 2017-09-12
> **Evil Wayz said:**
> The drive has physical errors, I believe from running it without enough power.  (It is usb powered and was running off a Raspi, a mistake I will not make in the future.)

SHould I try just copying the files over or using something a little more hardcore like dd or ddrescue?

I'd try with **rsync** first. Work at the file level.

dd/ddrescue work at the device or partition level and we aren't there yet, at lesat I'm not convinced.  If the USB power is stable/sufficient now, I doubt there are issues from that.  The SMART data will let you know if there are major issues with the disk, but it doesn't know anything about file systems.  I'd use ddrescue, BTW, if that is where you are and probably at the partition level.

What do you mean by "the drive has physical errors"? - the only way I know to cause it is dropping it while the platters are spinning, hitting it hard while the drives are spinning or if it has been running for 5+ yrs and a few HW defects have happened from use over time.

---

### Post by Evil Wayz on 2017-09-12
> **TheFu said:**
> I'd try with **rsync** first. Work at the file level.

dd/ddrescue work at the device or partition level and we aren't there yet, at lesat I'm not convinced.  If the USB power is stable/sufficient now, I doubt there are issues from that.  The SMART data will let you know if there are major issues with the disk, but it doesn't know anything about file systems.  I'd use ddrescue, BTW, if that is where you are and probably at the partition level.

What do you mean by "the drive has physical errors"? - the only way I know to cause it is dropping it while the platters are spinning, hitting it hard while the drives are spinning or if it has been running for 5+ yrs and a few HW defects have happened from use over time.


The good folks over at the testdisk/photorec forum said the combination of testdisk deep searching read errors and the clicking/beeping nose i was hearing was a sure sign of the heads contacting the platters.  That was the term they used, "physical error."

As soon as I found the 5000 or so bad sectors from test disk, the drive was removed from use until i could find a drive to back it up to.

---

### Post by TheFu on 2017-09-12
> **Evil Wayz said:**
> The good folks over at the testdisk/photorec forum said the combination of testdisk deep searching read errors and the clicking/beeping nose i was hearing was a sure sign of the heads contacting the platters.  That was the term they used, "physical error."

As soon as I found the 5000 or so bad sectors from test disk, the drive was removed from use until i could find a drive to back it up to.

How do I say this ... way to bury the lead, dude.

You are screwed.  When a drive gets that bad, it is time to 
a) use your backups
b) take it to a professional data recovery shop and hope they have the skills to replace the heads. Think - $3500+

In most situations, restoring from a recent backup is the only possible answer.

---

### Post by Evil Wayz on 2017-09-12
The manufacturer thinks that once the power problem is correctly, their proprietary tools might be of some use.  Its a 2tb drive with 500 or so gb left on it, maybe i will get lucky.  It was still readable at the time of testing. 

I had a drive spitting out SMART failure errors every half an hour once, and i formatted it and it was still working when i gave it to my ex about two years later.

If anyone is interested, I found a data recovery place in michigan that only charges 300 bucks and they send your data back on a new drive.  If they cant recover the data, they charge you 30 bucks and shipping back to you. 

what can I say, I'm an optimist.  :D

---

### Post by Evil Wayz on 2017-09-16
> **SeijiSensei said:**
> 
fdisk uses a bunch of single-letter commands.  To quickly change the partition type, type "t".  If you have multiple partitions on the device, you'll be asked for the partition's number.  In this case you would type "1" when prompted.  You'll then be asked to enter the appropriate hex code for the partition type, which is "83" for a Linux partition.  Type "w" to save the changes to the disk.

I did this and now the drive isn't recognizable. Not in Gnome Disks or Gparted. Or Fdisk.

OK it popped back up againm but that mkfs command output this:

```
wolf@bubba-laptop:~$ sudo mkfs -c -t ext4/dev/sdc1
Usage: mkfs.ext2 [-c|-l filename] [-b block-size] [-C cluster-size]
	[-i bytes-per-inode] [-I inode-size] [-J journal-options]
	[-G flex-group-size] [-N number-of-inodes] [-d root-directory]
	[-m reserved-blocks-percentage] [-o creator-os]
	[-g blocks-per-group] [-L volume-label] [-M last-mounted-directory]
	[-O feature[,...]] [-r fs-revision] [-E extended-option[,...]]
	[-t fs-type] [-T usage-type ] [-U UUID] [-e errors_behavior][-z undo_file]
	[-jnqvDFSV] device [blocks-count]

```

---

