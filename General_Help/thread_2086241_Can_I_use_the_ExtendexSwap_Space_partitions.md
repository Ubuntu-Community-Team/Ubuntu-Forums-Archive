---
title: "Can I use the Extendex/Swap Space partitions?"
date: 2012-11-20
forum: General Help
---

### Post by rva1945 on 2012-11-20
Hi:

The HD is a 320GB size. Ext4 (/dev/sda1) is 307 GB, Extended (/dev/sda2) is 13GB and Swap Space (/dev/sda5) is 13GB.

By that I understand that the Extended and Swap Space seem to be the same partitions, am I wrong?

Now, if I boot with a Win boot CD, can I install it in that partition?

I have a W7 running as virtual machine but some devices are not recognized, like the video capture, that's the reason why I need a "true" Windows running.

Thanks

---

### Post by pkadeel on 2012-11-20
No you can not install windows on a linux swap.

---

### Post by mcduck on 2012-11-20
The sda2 is an extended partition, which contains the sda3 swap partition. You can't actually use the extended partition for anything, it's just a  container used to overcome the BIOS restriction of 4 partitions.

(So instead of being limited to 4 partitions, you can have three primary partitions and then one extended partiiton which can contain as many logical partiitons as you want)

Also Windows is not quite happy about living on a logical partition, since you now only have one primary partiton you could resize that (sda1) and make room for another primary partition for Windows.

---

### Post by davidbilla on 2012-11-20
For installing windows, the filesystem has to be FAT32/NTFS. But the swap space is raw memory that doesn't persistently store stuff; as far as I know, it doesn't have a filesystem.

[This link]("http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space") seems to explain swap space very well.

---

### Post by Impavidus on 2012-11-20
Your sda2 is an extended partition, which is a partition containing other partitions. sda5 is contained in sda2. This is the default when installing Ubuntu to the entire disk. If you want to install windows you can better shrink your sda1 partition, make a new partition in the freed-up space and install windows there.

---

### Post by rva1945 on 2012-11-20
> **Impavidus said:**
> Your sda2 is an extended partition, which is a partition containing other partitions. sda5 is contained in sda2. This is the default when installing Ubuntu to the entire disk. If you want to install windows you can better shrink your sda1 partition, make a new partition in the freed-up space and install windows there.

Thanks, now, how can I shrink sda1 and make a new partition safely?

---

### Post by Zimmer on 2012-11-20
> Thanks, now, how can I shrink sda1 and make a new partition safely?

My 2 cents... assuming you have a Win7 installation disk..

First, ensure all your private data..letters music pictures email etc... is backed up to an external disk. 

Then: Read more .. 
[http://members.iinet.net.au/~herman546/p17.html](http://members.iinet.net.au/~herman546/p17.html)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
for a start.

All the Ubuntu community partitioning/drive help is here.

[https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)
and

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

However, you should have a clear idea of what you want to do with the dual boot you are about to undertake. Plan the partitions.
[http://members.iinet.net.au/~herman546/p17.html](http://members.iinet.net.au/~herman546/p17.html)
gives a good clue as to what you should be doing, with specific Win7 advice.

Simplified; Windows wants to be on sda1 and wants a big chunk of space (eg Vista would not let me shrink an existing install below 70gb. so Check how much you need for Win7, you can probably get away with less, do not skimp if you want Windows updates to keep going for a few years and not fill the space).NTFS.

A linux install will be happy with a lot less (especially if you use another partition for your personal data:my recommendation) eg 18gb is plenty.
Suggest Primary partition sda2  and ext4

Create Extended partition(sda3) with remaining space.
Create SWAP partition inside the Extended (it will be named sda5) of a size twice the size of your RAM.

Create one (or more) partition(s) for DATA in the extended partition  sda6 etc..

If you want your Win7 install to see all the data then format the partition(s) to a Windows file system of your choice...

But read more and decide what you want, build in some flexibility.

Install Win7 to sda1. Install Linux to sda2, and save all personal data to the DATA partition(s).

Happy reading, do not rush into this.

---

