---
title: "Lost partition"
date: 2014-06-29
forum: General Help
---

### Post by IceblueGen3 on 2014-06-29
Hi

I seem to have lost a 400GB partition full of data. I recently did a new install of Ubuntu 14.04, replacing the existing 12.04 partition with the new installation. This was a few weeks ago but I have recently noticed that a second partition which was located on the same physical disk is now missing. I am not sure if the second partition disappeared during the installation or more recently, as I have not really tried to access the second partition until a few days ago. How can I go about trying to recover the data on the second partition? The original setup was as follows:

Partition 1: 80 GB ext3 (or possible ext4) with Ubuntu 12.04 installed
Partition 2: 400 GB NTFS with various media and other data stored

The file system now looks like this (as per disk info):

Partition 1: 255 MB ext2 
Partition 2: 500 GB Extended partition
Partition 5: 500 GB LVM2 PV

The physical disk size is 500 GB. Currently is shows approximately 60 GB used and 420 GB free on the disk. I need to try to recover anything that may still be there. Could anybody advise how to go about doing this?

---

### Post by yancek on 2014-06-29
Based on the information you posted, it looks like you have overwritten everything when you did the installation using LVM.  You could run the command:  sudo fdisk -l to see if you have any ntfs partitions.  If you are using GPT for booting, use GParted to see if there are ntfs partitions.  You might be able to recover some files using the TestDisk software.  If you have been using the computer for several weeks, I wouldn't have much hope.

---

### Post by oldfred on 2014-06-29
With the 12.04 alternative installer it always was clear the the LVM install by default was a full drive install. The newer instructions in the 14.04 installer do not make that clear, but it still is a full drive install.

If you want to attempt to recover any data, stop using system. All activity is overwriting more data. And that new install is LVM makes it more complex as that is not standard partitions.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)


 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by IceblueGen3 on 2014-06-30
I have checked fdisk and there is no NTFS partition listed. I'm going to try GetDataBack as I have used this previously. Hopefully I can at least recover some of the files.

I'm just really annoyed that this happened as I read about people having this problem when installing 14.04 and checked carefully before making my selection, but as oldfred stated they don't seem to make it clear enough during the install.

---

