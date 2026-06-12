---
title: "How to extend dual boot Ubuntu partition?"
date: 2014-10-17
forum: General Help
---

### Post by madsum on 2014-10-17
Hello,

In my pc I have duel boot system Windows 8.1 and Ubuntu 14.04. Now I would like to extend my current Ubuntu partition. I have already about 50 gb unallocated space. Now I want to marge this space with ubuntu partition. How can I do it without harming current system? Thanks in advance! 

p.s: I'm new in this forum. I may have posted in a wrong place. Please send it to the correct section.

---

### Post by Bucky Ball on 2014-10-17
*Thread moved to **General Help**.*

Welcome. Boot from a Live USB/DVD, whatever you installed from>select 'Try Ubuntu'>once at the desktop, launch Gparted>right click on the partition and resize it.

Should be that easy. Reboot when you've finished. You can't resize the partition your OS is running from so you need a Live boot which is running from the boot media, not the hard drive. ;)

---

### Post by grahammechanical on 2014-10-17
1) backup
2) research partitioning

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

3) make sure that you have backed up the data your really do not want to lose.

I have not had a bad experiencing with resizing but the possibility is always present.

Regards

---

### Post by madsum on 2014-10-17
Yes, I will try it out. If I start Gparted I can see following partitions (plase also check attachment):-


/dev/sda2            ntfs                142 Gib           
unallocated                                 50 Gib
/dev/sda3            exteded          40Gib
/dev/sda5            ext4             / 32 Gib
/deb/sda6            linux-swap      7 Gib

My aim is to marge unalloated 50 GiB with /dev/sda3 exteded and /dev/sda5 ext4. I'm not clear about this partitioning system. But when I installed Ubuntu I assigned 40 GB which must be /dev/sda3 exteded. I want to give enough space for Linux system as well as user area.  

Right now I have no option to modify partition by Gparted. Hopefully when I boot by live cd, it will me option. BTW, is there any chances that it may destroy the whole system. If yes, please advice me what kind caution should there be. Thanks in advance!

---

### Post by Mark Phelps on 2014-10-17
The Extended partition is just a wrapper that contains other partitions inside itself.  You should be able, once you boot from the LiveCD, to expand the Extended partition to the left to take up the unallocated space, and then expand sda5 to the left to fill up the Extended partition.  Since you're not adding or removing partitions, this should present no problems.

---

### Post by fantab on 2014-10-17
The MBR partitioning scheme allows you to have ONLY FOUR Primary partitions... to overcome this limitation we have EXTENDED Partition. An Extended Partition is Primary partition and acts as a container for LOGICAL Partiions. You can have more than 100 Logical Partitions.

You have Ubuntu installed on 32Gib partition, /dev/sda5; you have 7gib swap partition, /dev/sda6; /dev/sda4 is an EXTENDED Partition of 40Gib.

In my experience, it is difficult to move 'unallocated space' into and out of Extended partition with gparted. I've had issues earlier.

I would recommend that you keep things as they are and from the 'unallocated space' make a new partition with either ext4 or ntfs. NTFS parttion can be shared between Ubuntu and Windows; ext4 is linux only.

At a later date when need be to re-install Ubuntu then you can re-create the linux partitions as needed.
A separate /home partition is a good idea, your personal data and system files will be separate.
7Gib SWAP is bit big in my opinion. 2-4Gb is plenty.

---

### Post by yancek on 2014-10-17
> I would recommend that you keep things as they are and from the  'unallocated space' make a new partition with either ext4 or ntfs. NTFS  parttion can be shared between Ubuntu and Windows; ext4 is linux only.


I would agree with the above as a far simpler solution.  The problem with resizing in your situation is that you will need to move the Extended partition (sda3) as well as the Ubuntu partition (sda5) to the left and this will move the location of the boot files and render the system unbootable unless you go through a complicated chroot option.  Resizing is always MUCH easier if the unallocated space is at the end (the right) of the partition.

---

### Post by oldfred on 2014-10-17
I just did very similar change on my old laptop. And I was somewhat surprised it worked.

I do recommend smaller system partitions and larger shared data partition(s).

But in my case I had not booted XP for several years and wanted to eliminate the shared NTFS and combine all data into a new ext4 data partition. My NTFS data was a primary which I deleted and made unallocated. Moving extended left on took a couple of seconds. But moving my / partition left ended up as a copy and gparted took forever. Old laptop is not speedy anyway. And I was able to reboot with lots of errors on missing data partitions, but was able to change fstab can correct that easily.

If using gparted from live installer, you also have to unmount swap with swapoff or extended partition is also mounted. And best not to queue changes but run each change so you know if it worked or not, before going to next change.

---

### Post by yancek on 2014-10-17
The link below is to the GParted manual section on "moving a partition".  I would suggest reading it and the various links on that section of the page before beginning.  It is a higher risk than other partitioning as it includes moving data and obviously takes much longer than just creating/deleting partitions.  Since the boot files will be moved, I expect the OP would need to chroot to that partition and re-install and update grub, second link below.  It would be much easier for a new user to just create another partition.

[http://gparted.org/display-doc.php?name=help-manual#gparted-move-partition](http://gparted.org/display-doc.php?name=help-manual#gparted-move-partition)

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

I posted this solution as one of several options to someone in a similar situation and he posted back that it was successful, although it took quite some time.  Hope you have no power outages if you try it.

---

### Post by madsum on 2014-10-18
Hello all,

Thanks a lot for sharing your knowledge. I learnt a lot about Linux partitioning system. Perhaps there were mixed suggestion. As a new Linux user I must go with the easiest and safest available option. I got few more questions about it.

I think I should make ntfs partition from these unallocated 50 GB. Because I wish to share files between Linux and windows. My question is that if I make ntfs how ubuntu going to use these free space when Ubuntu will be low in space. Is it going to be automatically or I have to do some setting from Ubuntu os side. 

Currently I have /dev/sda2 ntfs where 98 GB unused. I should be able to use it in Ubuntu. How can I install application in that place from Ubuntu? Because whenever I install app by command line all goes to Linux side of installation. It doesn't offer me to select where I want to install.
 
Second question about huge 7 GB swap file system. How can I reduce it and take this space /dev/sda5  ext4 or ntfs side. So that I have more space to use?

---

### Post by Bucky Ball on 2014-10-18
You won't be installing apps to an NTFS partition. All installed apps go to / partition, which is you Linux OS partition. ;)

That will be EXT*, probably EXT4.

---

### Post by fantab on 2014-10-18
> Currently I have /dev/sda2 ntfs where 98 GB unused. I should be able to  use it in Ubuntu. How can I install application in that place from  Ubuntu? Because whenever I install app by command line all goes to Linux  side of installation. It doesn't offer me to select where I want to  install.
 
Second question about huge 7 GB swap file system. How can I reduce it  and take this space /dev/sda5  ext4 or ntfs side. So that I have more  space to use?

Open Terminal [ctrl+alt+t], run the following command and post its output here:
```
sudo parted -l
```

---

### Post by yancek on 2014-10-18
You can just create another separate ntfs partition from that unallocated space after sda2 or from windows you can extend the windows partition sda2 to include the unallocated space and you can then use it from both windows or Ubuntu.  30GB for your Ubuntu filesystem should be more than enough for applications and system files.  Put data such as movies, pictures, music, etc. on one of the other partitions rather than the Ubuntu filesystem.  You need an entry in the /etc/fstab file for it to be accessible on boot.

---

### Post by madsum on 2014-10-18
This data is for  [COLOR=#000000]**fantab. **[/COLOR] wants so see it. 

  
dev@ma:~$ sudo parted -l
[sudo] password for dev: 
Model: ATA WDC WD2500BEKT-6 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  368MB  367MB   primary   ntfs            boot
 2      368MB   153GB  153GB   primary   ntfs
 3      207GB   250GB  42,9GB  extended
 5      207GB   242GB  34,5GB  logical   ext4
 6      242GB   250GB  8438MB  logical   linux-swap(v1)

---

### Post by madsum on 2014-10-18
The main reason I thought to extend this partition is to host a virtual windows 8 on Uburntu. So can I use virtualbox/vmware's virtual host machine data in this ntfs side of the partition?

---

### Post by yancek on 2014-10-18
> So can I use virtualbox/vmware's virtual host machine data in this ntfs side of the partition? 		

I don't use VirtualBox enough to give a definitive answer but I don't think this would work.  When you download VirtualBox, there are different downloads for windows and Linux and the Linux download I would expect to need a Linux filesystem.  Might take a look at the virtualbox forums and see what you can find there.

[https://forums.virtualbox.org/viewforum.php?f=7](https://forums.virtualbox.org/viewforum.php?f=7)

---

### Post by fantab on 2014-10-18
If re-installing Ubuntu is an option then Re-install Ubuntu after setting up your partitions as you want. Since partitioning is something we don't do often, it is worth the effort to set it up as needed.
Backup all your important DATA.

Use Gparted from a live Ubuntu disk and delete all linux partitions and the Extended partition.
Re-create partitions for Ubuntu. It will be a good idea to keep your 'system files' separate from 'personal data'. So I suggest you create a separate /home partition.
The Ubuntu installer does not partition for /home, so you have do it yourself using the 'Something Else' option during install.

Suggested partition scheme:
/dev/sda3 : 20-25Gb Primary Ext4 Ubuntu '/' [for system files]
/dev/sda4 : Extended Partition with all the remaining space.
/dev/sda5 : ??Gb Logical Ext4 Ubuntu '/home' [For user files and personal data]
/dev/sda6 : 2-4Gb SWAP.

If you want to share a partition between Windows and Ubuntu then it should be formatted with NTFS as Windows cannot understand Ext4.
/dev/sda3 : ??Gb Primary NTFS [shared partition between Win and Ubuntu]
/dev/sda4 : Extended Partition with all the remaining space.
/dev/sda5 : 30-35Gb Logical Ext4 Ubuntu '/' 
/dev/sda6 : 2Gb SWAP

After you choose 'Something Else' option to manually target Ubuntu install to the partition you want, you have to use the following options:
Select the partition you want to install Ubuntu to by clicking on the 'Change' button.
Use as = ext4 journaling
Mountpoint = '/' (for separate /home use moutpoint = /home) If using NTFS then you don't have to do anything to it, just leave it as it is.
Format= yes

Then continue with your installation.

---

### Post by madsum on 2014-10-19
> **yancek said:**
> I don't use VirtualBox enough to give a definitive answer but I don't think this would work.  When you download VirtualBox, there are different downloads for windows and Linux and the Linux download I would expect to need a Linux filesystem.  Might take a look at the virtualbox forums and see what you can find there.

[https://forums.virtualbox.org/viewforum.php?f=7](https://forums.virtualbox.org/viewforum.php?f=7)

I installed vmware application in Linux partition. When I use vmware to create a virtual win 8 guest, I used ntfs partition for the guest. It is working. But it is much slower comparing windows. Earlier I used windows hosting a Ubuntu guest. I increased ram to check whether speedup the guest. But it hang the host machine (Ubuntu).

Could it be the reason that I installed guest in ntfs file system and this delay is for ntfs?

---

### Post by madsum on 2014-10-19
> **fantab said:**
> If re-installing Ubuntu is an option then Re-install Ubuntu after setting up your partitions as you want. Since partitioning is something we don't do often, it is worth the effort to set it up as needed.
Backup all your important DATA. 

Yes, I'm planning to re-install Ubuntu. While re-install, can I choose ntfs instead of ext4 for whole Ubuntu installation? How recommended is it to have Ubuntu file system ntfs instead of ext4? In terms of performance.

---

### Post by fantab on 2014-10-19
> **madsum said:**
> Yes, I'm planning to re-install Ubuntu. While re-install, can I choose ntfs instead of ext4 for whole Ubuntu installation? How recommended is it to have Ubuntu file system ntfs instead of ext4? In terms of performance.

NO. Linux won't install to NTFS. NTFS is a Microsoft proprietory.

---

