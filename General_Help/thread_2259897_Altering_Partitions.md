---
title: "Altering Partitions"
date: 2015-01-07
forum: General Help
---

### Post by gordon99 on 2015-01-07
My laptop is dual booted with Xubuntu 14.04 and Windows 7. I have an NTFS Data partition which, when I installed Xubuntu, I thought I would use a lot. However, I now find I am using my Home partition a lot more than I imagined but am barely using the Data partition. I want to shrink the Data partition from about 90 GB to about 30GB or less and use the freed up space to expand the Home partition. I did log into Disk Management within Windows 7 intending to shrink the Data partition as a first step, but it would only let me shrink the partition by about 50%.  
GParted is installed within Xubuntu but I am unsure how I should go about the transfer. Would someone kindly lead me in the right direction.

---

### Post by mooreted on 2015-01-07
Re-sizing partitions is always iffy. You run the risk of deleting all the data on the hard drive. There are tools like Gparted, Parted Magic and Partition magic that will do it. If it were me, i would back up the data to an external drive, delete all the partitions, create the partitions I want then copy the data back to the drive.

[http://partedmagic.com/using-gparted/](http://partedmagic.com/using-gparted/)

---

### Post by Dennis N on 2015-01-07
You wrote that "GParted is installed within Xubuntu but I am unsure how I should go about the transfer". What is being transfered?

A screenshot of the gparted window showing your partition setup would help others assess the feasibility of any actions. Where partitions are on the drive in relation to each other makes a difference.

---

### Post by grahammechanical on 2015-01-07
Here is some reliable advice that I have seen given on the forum many times.

1) Defrag Windows at least twice using Windows utilities and re-starting windows after each defrag.

2) Use Windows utilities to re-size Windows partitions. There is a reason why the Windows utility is limiting the amount you can shrink that NTFS partition by. Trust the utility to protect you from breaking Windows in some way even though the partition is only used for data.

3) Use Gparted running from a live session to expand the Linux Ext4 partition into the unallocated space left behind when you re-sized the NTFS partition.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

My own personal advice is to do the Gparted actions one at a time. Gparted will let us Queue up actions and set them to run one after the other. But these actions take a long time. So, I like to do each action one at a time to make sure that each action is completed without anything going wrong.

Regards.

---

### Post by gordon99 on 2015-01-10
I am wanting to increase the size of my /home partition by adding some unallocated space I have now made by shrinking my /data ntfs partition. I did this using Windows disk management program. I'm afraid I have struggled, without success as you can see, to attach a screenshot of the GParted window to this reply.  Making a screenshot is not a problem but I can't seem to copy and paste it as one can with documents. Making a "live" usb of GParted with Tuxboot is also proving to be a nightmare. I assume Xubuntu should boot from the usb stick, but not for me. Removing all the logical partitions ( as I believe partitions within an extended partition are called) and re-sizing them from scratch would probably give me even more of a headache. There is a need for evening classes in Linux but I guess there would be insufficient pupils to make it a viable proposition. If I simply back up my /home partition, and then wipe that partition clean by simple deletion, will Gparted extend the partition on command by moving it to join up with the unallocated disk space, or do all the partitions have to be moved around by me like pieces on a chess board ? I do not find GParted help instructions very clear.

---

### Post by yancek on 2015-01-10
In order to expand a partition, you need unallocated space which is contiguous to that partition.  If you can't post and image of gparted, can you boot Xubuntu and post the output of sudo fdisk -l(Lower Case Letter L in the command)?

---

### Post by oldfred on 2015-01-11
If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4.
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

If you change the size of Windows you must immediately reboot so it can run chkdsk. Best to have a Windows 7 repairCD or flash drive in case you cannot reboot.

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by gordon99 on 2015-01-11
As you will see, I have managed to copy the GParted image, though rather larger than I would have preferred. I will get it right one day, maybe. Anyway, it is sda5 which I wish to enlarge by attaching to it the unallocated 45.52 GiB space. The two are separated by the small unallocated 3.48 MiB space and sda7 and therefore not contiguous.
It was sda7 which I shrank using Windows disk management facility without, it seems, damaging Windows. I had hoped to shrink it even more but the Windows would not allow, which surprised me. I will have to get to grips with GParted. 





[ATTACH=CONFIG]259174[/ATTACH]

---

### Post by oldfred on 2015-01-12
While I like separate data partitions for both NTFS & Linux, your sda7 currently has only 1.5GB. That makes it probably easier to copy data to main partition, flash drive or DVD. If vital data perhaps all three like I often do.

Then you can delete sda7 which would make it possible to expand sda5.

You can only do that from live installer or separate gparted ISO liveCD. The little lock symbols show you used gparted from your working install and partitions are mounted. And you cannot unmount your /, so cannot change them from your working install. You may have to unmount swap with swapoff even with live installer but that can be done.

But in general I prefer smaller system partitions for both Windows & Ubuntu. With Ubuntu I use 25GB for / and actually use about 11GB of the 25GB. And then have all data in data partitions. Windows usually requires a large system partition than Ubuntu.

You also can have a separate /home for your data.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by gordon99 on 2015-01-18
My thanks to all who responded to my questions. I am pleased to say I have managed to shrink my /data file and extend my /home file after installing 'GParted Live iso.' on my hard drive (my solved thread 'Launching GParted Live' refers).  I struggled somewhat when I found my shrunk /data partition had, in fact, somehow mounted in '/media'. I had to read up about 'fstab' and how to amend it. Hope I don't have to do it all again as I would probably struggle to remember the necessary steps. I have left GParted Live iso. on my hard drive and in my 'grub' menu.

---

