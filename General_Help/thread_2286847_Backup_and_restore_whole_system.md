---
title: "Backup and restore whole system"
date: 2015-07-15
forum: General Help
---

### Post by gurabli on 2015-07-15
Hi,

I'm running Ubuntu Server 14.04 LTS on a small home server, and its running great. I have configured it more or less to my taste and everything works as expected.
I have a 160GB 2.5" drive where Ubuntu is installed, boot, swap and remaining ext4. 

I don't know what is the easiest and best way to do a full backup of the system (the ext4 partition is not important) that I can easily restore if anything goes wrong? On Windows I used to create an image of the whole system partition easily and once something went wrong, I just booted off the pendrive and restored to the previous state. 
I'm not sure how can I do this in Linux? Could you please guide me step by step to make the backup and then how can I restore? 

Is it possible to restore to another drive, as in that case I would make a clone of the system and try some things with the second drive without breaking the system itself.

Thanks!

---

### Post by gdesilva on 2015-07-15
Hi, I use Clonezilla for full disk backups. Clonezilla is free to download and you can create a liveCD. Boot the LiveCD and then follow the instructions for backup or restore. You can do a full disk image or partition images. I am sure there are many other solutions for this task but Clonezilla has worked fine for me.

---

### Post by gurabli on 2015-07-15
Many thanks! Is it possible to do this from a pendrive or CD is required?

And it is basically the same as it is on Windows, create a backup and restore when needed, no additional cli is needed after restoring the system?

I will look into this, I'm asking since I really don't want to find out that the restore is not working once I need it...

---

### Post by Bucky Ball on 2015-07-15
Clonezilla works well, but has disadvantages. If you clone a partition of, say, 500Gb but only 50Gb of it is data, the rest empty, you MUST clone it back to a partition of the same size, 500Gb, regardless of the fact 450Gb of it is empty. I've never done a whole disk, but I would imagine the disk you are cloning back to would need to be the same size as the original disk.

fsarchiver, also in the repositories, does not have this issue. I used that for the last back up and seems to work ok. I haven't plopped it back to another partition so can't be certain, though.

---

### Post by Kai_Pirttimki on 2015-07-15
If you want to easily test & try new things and not to break your production server you might want to consider virtualizing your current installation. Having unlimited supply of identical server copies makes testing quite a lot easier ;)

---

### Post by gurabli on 2015-07-15
Thanks, I'll look into virtualizing. by this basically you refer to creating an image of the current system and using that on a VM? Could you point me to the proper direction of doing this?

---

### Post by leunam12 on 2015-07-15
It is possible to restore a disk to a smaller disk in CLonezilla by choosing the advanced mode (as opposed to beginner) at the beginning and then check the option to skip checking the destination's size. I  think it is possible to do the same with partitions. One limitation that I have seen is that you can only restore to a partition that is the same device name. For instance: you can only restore from sda1 to sda1; if you try to restore an sda1 partition to an sda2 or sdb1 it will give an error. There is a workaround for this that involves changing one of the files in the image in a text editor and changing all the instances of the saved partition name to the desired name.

---

### Post by gurabli on 2015-07-15
Thank you all for your help!

I will try CloneZilla and see the result. If I want to backupt the system, I should select partition (will this include boot and swap too?) 

If I restore, the system will be bootable again?

---

### Post by gdesilva on 2015-07-15
I have backed up separate partitions, instead of the entire disk, and restored them without any issues using Clonezilla. And yes, you can download the ISO file and create a LiveCD. It may be possible to do a LiveUSB but I have not tried this. If you decide to backup just the partitions then mbr will not be backed up. If you want the mbr in tact then you would need to back up the entire disk. For backing up partitions, you would want to select partimage option. Clonezilla allows you to back up Windows partitions as well. 

Yes, it is best to try it out yourself and try one or two other solutions as well.

Just curious, why would you want to back up SWAP, anyway?

---

### Post by gurabli on 2015-07-15
Well, I'm learning a lot regarding Linux and this is one area where I find it difficult to proceed, too many questions and no concrete answers.
If I got this right, on my disk there are 3 partitions: 1) boot 2) swap 3) remaining space with LVM ext4 
I would like to have a backup image to be able to restore everything in case of a system failure (disk failure, or if I mess something up it would be much easier to restore the previous state), and this means the whole system, if I'm not mistaken, the swap too. For me it is important to have a backup that can be restored easily exactly as it was, and that I should not need to create the swap partition manually or to make the system bootable. This is what I need.

---

### Post by gdesilva on 2015-07-15
The simplest solution then is to back up the entire disk - easy! You will find Linux much easier to deal with compared to MicroSquash:lolflag:

---

### Post by gurabli on 2015-07-15
Yes, I will backup the entire disk with CloneZilla and restore if needed. That way I will be sure. I will have to check if the backup image will be the size of occupied space or the size of the whole disk (including free space).

I already like Linux so much more then MS, it is really exciting and much more stable, faster, and... it just works:) 
I already have a home server running Ubuntu Server, a laptop running Ubuntu Vivid, a notebook running Lubuntu, and a desktop running Ubuntu Vivid with W7 dualboot. it was quite hard to adopt after spending so many years with MS (since 286, Ms-Dos), but Linux now clearly wins.

---

### Post by howefield on 2015-07-15
> **gurabli said:**
> Yes, I will backup the entire disk with CloneZilla and restore if needed. That way I will be sure. I will have to check if the backup image will be the size of occupied space or the size of the whole disk (including free space).

Clonezilla will only clone occupied blocks when imaging a supported file system.

---

### Post by gurabli on 2015-07-15
> **howefield said:**
> Clonezilla will only clone occupied blocks when imaging a supported file system.

This is great, I was hoping to hear this!

Thank you all for your help!

---

