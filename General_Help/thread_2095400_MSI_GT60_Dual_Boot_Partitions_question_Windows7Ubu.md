---
title: "MSI GT60 Dual Boot Partitions question Windows7/Ubuntu 12.04"
date: 2012-12-16
forum: General Help
---

### Post by z0mi3ie on 2012-12-16
Hey everyone,

 I am posting pictures for easy understanding of  my probleml. I'm trying to install Ubuntu 12.04 on my GT60, which is by default on RAID 0. I  have shrunk the C drive 80 GB for the Ubuntu install through the Windows Partition manager. I formatted it to  drive F and with the name Linux. I understand that I would have to  reformat this with the Ubuntu Live CD to ext3 or ext4 when I'm ready to  install, with the 3 partitions for Linux etc. 

BUT my problem is  that in Ubuntu and GParted off of the live cd my D data drive is coming up as unallocated  space and my F Linux drive is coming up as unallocated space. Please  take a look at the pictures I have supplied if this is unclear. Has  anyone run into this issue or can point me in the right direction? Is  this a problem with RAID 0? 

Windows Partition Editor Screen shot: [http://imgur.com/yAPZu](http://imgur.com/yAPZu)
GParted from Ubuntu Live CD: [http://imgur.com/bT8pE](http://imgur.com/bT8pE)

I  have burnt all the recovery disks and have a copy of Windows Home  Premium in case I need to reinstall with the product key. 

Any  help would be greatly appreciated! I really want to have Linux for  school and windows for gaming set up on the same rig. 

Please let me know if there is anything you guys need as far as read outs and testing. I've been reading stuff on the net all day about this but am coming up empty.

---

### Post by Ghiro82 on 2012-12-16
First you have to format the partition called "linux" in FAT or FAT 32.
Then install Ubuntu in that partition. The dual boot should be automatic, if you install ubuntu and windows in only one hdd

---

### Post by oldfred on 2012-12-16
By creating partitions in Windows you have converted to dynamic partitions which does not work with Linux. It is a Windows proprietary way to work around the 4 primary partition limit in MBR partitions.

Per Microsoft it is a one way convsion. The only way to convert back to to totally back up (which you should do anyway), repartition, reinstall and restore all your data. Some third party tools may convert without reinstalling.

       Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

   Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by z0mi3ie on 2012-12-17
Thank you for the links to those tools. What I had done was deleted my data partition and had 500GB of unallocated space. I loaded up Ubuntu and created a partition in ext3 for it and went on with the installation.

I ran into a problem at the end though. 

I think because I am on RAID0 the bootloader could not be written to /dev/sdb, and I could only enter dev/dm-4. This failed to install GRUB as well. 

Does anyone have Ubuntu installed on a RAID0 setup? I'm afraid I may have to break RAID0, and use the recovery disk to install to one of the drives, and then start there with the installation of ubuntu.

---

### Post by oldfred on 2012-12-17
Dynamic is not RAID.

Best to see exactly where you are at:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemic](https://help.ubuntu.com/community/UbuntuSecureRemic)
[http://paste.ubuntu.com/1287871/](http://paste.ubuntu.com/1287871/)

---

### Post by LordHades on 2013-02-16
I know its a little late but I actually got it to work so..:) 

I successfully set it up on my gt60 with RAID0 still functioning. I first created the partition using GParted and formatted it as ext4. However keep in mind that you won't see this partition in Windows, not without 3rd party software at the very least. Then you might want to install it there. Also, the installer actually detected that my disks were in RAID0.

Note that the only downside to this was that I was unable to create a swap partition because I already had 4 primary partitions and couldn't format another. But with 10+ GB of RAM, you probably won't need it unless you're doing some very specific stuff. This also means that you won't be able to hibernate since you have no swap.

---

### Post by millsryn on 2013-03-12
I have the same issue, however I'm able to install but it doesn't work when I get to the bootloader installation. I've tried specifying a point in the array but to no avail. How did you overcome this, or was this never an issue?

---

### Post by LordHades on 2013-03-12
Here is what I had set up before installing Ubuntu (64-bit),

- Initially had Windows 7. But I partitioned the drive into one 550 GB and the rest on the other. Both were initially NTFS. You can use GParted for this (using a live disk). 

- Installed Windows 8 fresh on the partition that had Windows 7 (Overwrite it, you need to supply drivers during installation). Leaving the other partition as it is.

- Format the second partition to ext4. It should already **see both disks as one large disk.**

- After getting that working, I launched the Ubuntu live disk and **the setup saw my hard disks in RAID 0 (one large disk). Install it to the ext 4 partition. **I was unable to make a swap partition but I'm doing fairly well without it. If you absolutely need one, you'll have to figure out a way to make another primary partition.
[B]
-Install the bootloader to the beginning of the array. I don't exactly remember the options it gave me, but I'm sure I can tell you which one it is if you show me a screen shot.[/B]

Let me know if you need anything else. A few things to keep in mind before you dive into this, 

- I was unable to get the Killer LAN working on Ubuntu. There is allegedly a way to do this by editing certain drivers and so but I was not very successful at it and frankly I was perfectly fine with just the Intel wifi card.

- I attempted to get Optimus working for graphics switching using bumble-bee. However I ended up turning my graphic card on permanently when in Ubuntu. I would much rather switch back to integrated since this has an effect on battery performance.

Good luck installing!

LH

-

---

### Post by LordHades on 2013-04-06
OK, I fixed my graphic card problem by reinstalling bumblebee so that shouldn't be a problem anymore.

---

