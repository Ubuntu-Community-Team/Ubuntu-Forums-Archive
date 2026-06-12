---
title: "Mounting 1TB harddisk?"
date: 2014-05-14
forum: General Help
---

### Post by TheElder777 on 2014-05-14
Hey all. So ubuntu is located on my ssd, which boots and works perfectly. I have a 1TB harddrive that i am trying to mount. At one point it would show up in my filesystems (also in the sidebar), then for some reason the harddisk would not show up, BUT it does show up under "disk utility." I have taken screen shots for you to see what it looks like. I have googled and done my research for this and have gotten nowhere. The reason I am having problems is because what is physically 1 drive is showing up as 2 drives under disk manager, for this reason I am not able to mount it as a regular file. I have some files on the hard disk, I would prefer to keep them.

Can anyone tell me what I should do to be able to access my harddisk? Thank you.

PS: I am running Ubuntu 12.04.4 LTS
[IMG]http://i573.photobucket.com/albums/ss174/creeper81/hd2.png[/IMG]

[IMG]http://i573.photobucket.com/albums/ss174/creeper81/hd1.png[/IMG]

---

### Post by The Cog on 2014-05-14
That looks weird. I wonder if the disk utility has cached some info. The command ```
sudo parted -l
``` may shed more light on the issue.

---

### Post by TheElder777 on 2014-05-14
> **The Cog said:**
> That looks weird. I wonder if the disk utility has cached some info. The command ```
sudo parted -l
``` may shed more light on the issue.
Thank you for your help and time! 
Hmmm... So i just ran that command and here is what I got:

Model: ATA SAMSUNG SSD 830 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  247GB  247GB   primary   ext4            boot
 2      247GB   256GB  8570MB  extended
 5      247GB   256GB  8570MB  logical   linux-swap(v1)




Error: /dev/sdb: unrecognised disk label                                  


Error: Can't have a partition outside the disk!   

-----------------------------------------------------------------------------
This is interesting... I don't know what to make of it though : (

Any suggestions?


PS: I just edited my original post! I had the same image twice, now I have two unique images (as it should be).

---

### Post by oldfred on 2014-05-15
It does not look like you have a 1TB drive but two 500GB drives and they are RAID, LVM or Windows equivalent of LVM that is dynamic partitions. Dynamic partitions do not work with Linux.

Post this
sudo fdisk -lu

---

### Post by TheElder777 on 2014-05-15
> **oldfred said:**
> It does not look like you have a 1TB drive but two 500GB drives and they are RAID, LVM or Windows equivalent of LVM that is dynamic partitions. Dynamic partitions do not work with Linux.

Post this
sudo fdisk -lu
That's weird, because at one point this 1TB hard disk WAS working on my ubuntu machine. Oh well. A while back however, this harddisk did have win7 on it.

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002927f


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   483377151   241687552   83  Linux
/dev/sda2       483379198   500117503     8369153    5  Extended
/dev/sda5       483379200   500117503     8369152   82  Linux swap / Solaris


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0a0b0000


Disk /dev/sdb doesn't contain a valid partition table
fdisk: unable to seek on /dev/sdc: Invalid argument

---

### Post by oldfred on 2014-05-15
Fdisk only shows sdb as 500GB and says it is unpartitioned. And it does not show sdc at all?
Whatever software you had to make that seen as one drive must have been damaged or drive sdc has issues. Often when one drive has issues with that type of configuration the entire or both drives lose all data.

---

### Post by TheElder777 on 2014-05-15
> **oldfred said:**
> Fdisk only shows sdb as 500GB and says it is unpartitioned. And it does not show sdc at all?
Whatever software you had to make that seen as one drive must have been damaged or drive sdc has issues. Often when one drive has issues with that type of configuration the entire or both drives lose all data.

Yes, this is what I got! I don't believe the drive is damaged physically, it is new... So would you say I should go ahead and format it? Or what would be the correct approach to fixing this issue?

Thank you.

---

### Post by oldfred on 2014-05-15
If you did not have data to recover, then yes partition both sdb & sdc. If never going to be Windows, I suggest gpt partitioning. Windows only boots from gpt with UEFI, but anything since XP will read gpt partitioned drives if you have a NTFS formatted partition.

If only using Linux use ext4 formatting. I do like to have extra partitions as I like to have an install on every drive. That way when one fails I do have another way to quickly boot. 

But If using ext4 you will have to add to fstab to auto mount and set ownership & permissions so you can read & write to them.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[URL="https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT"]https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT

[/URL]
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....



[URL="https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT"]
[/URL]

---

### Post by TheElder777 on 2014-05-15
Thanks a lot for the help. Will I be able to make the disk appear as one file rather than two?

EDiT: If i wanted to recover the data on the disk, would that be possible? If yes, will it be a difficult task?

---

### Post by oldfred on 2014-05-15
The way to make it appear as one large drive is LVM, but then if either drive fails you lose all data.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

I prefer reliability.

And I am willing to have to resize some partitions if necessary, but my data partitions on another drive have yet to need resizing. But every user has different needs so what is best for me, is not even best for me a couple of years later. :) 

I mount partitions in /mnt/data or /mnt/shared and then link folders inside those mounted partitions into /home so it looks like they are part of /home.

      
 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by TheElder777 on 2014-05-15
> **oldfred said:**
> The way to make it appear as one large drive is LVM, but then if either drive fails you lose all data.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

I prefer reliability.

And I am willing to have to resize some partitions if necessary, but my data partitions on another drive have yet to need resizing. But every user has different needs so what is best for me, is not even best for me a couple of years later. :) 

I mount partitions in /mnt/data or /mnt/shared and then link folders inside those mounted partitions into /home so it looks like they are part of /home.

      
 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

Thank you so much. I have learned a great deal of information! After reading your links and methods, I think I will format to gpt and link data folders to hdd folders. 
I have two questions however:

In post #2 of this thread: [http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) (one of the links you provided)
"srs5694" says that one should create a partition for the BIOS boot loader. My question is would I still need to do this if I will NOT be using the hdd for booting OS?

My second question, why would my harddisk show up as two disks? Would that mean that the hard disk contains two magnetic plates?


EDIT1: So I just formatted used GUID scheme and went with ext4. I then got this message: "Warning: The partition is misaligned by 3072 bytes. This may result in very poor performance. Repartitioning is suggested." What would I have to do in this case?
EDIT2: I just want to clarify that this HDD that I am formatting will only be used for data storage, not for OS!

---

### Post by TheElder777 on 2014-05-16
So I was able to fix all my issues by installing gparted, deleting and then creating new ext4 partitions. I am now able to mount them and use them. I am left with only one problem. I would like to have them automount on startup. I did some research and found that I had to edit my fstab file, here is what i included ([http://askubuntu.com/questions/164926/how-to-make-hdds-mount-at-startup-in-ubuntu-12-04):](http://askubuntu.com/questions/164926/how-to-make-hdds-mount-at-startup-in-ubuntu-12-04):) 
UUID=<e2bcf1c8-5ae5-4b9c-979c-300ba5268da6> </home/Proton> <ext4> uid=<1000>,gid=<1000>,umask=0022,auto,rw 0 0

I reset my computer and was greeted with the Ubuntu logo and a message beneath, here is the message:
"The disk drive for /home/proton is not ready yet or not present.      Continue to wait, or press S to skep mounting or M for manual recovery."

What would I need to do to fix this issue? I will be googling in the mean time. Thank you.

EDIT: SOLVED!!! I downloaded Storage Device Manager (aka pysdm) played with options and it edited my fstab for me, I was able to see what I had done wrong. 

Thank you so much for all the help!!! Off to linking folders now.

---

### Post by m-dw on 2014-05-16
Another approach to combining the physical disks into a single volume would be to assemble the two disks as a RAID 0 array using mdadm.

Sorry, just read rest of thread, ignore.

---

### Post by oldfred on 2014-05-16
I do not suggest pysdm anymore.
You may want  to review the settings used in this as they are generally better.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

    
If you have already mounted with fstab, just use those mounts not the example shown which includes manual mounting. You only can mount a partition once. You just need the chown & chmod with your mounts. use this to see mount.
mount

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

I created all the folders in my data partitions first, copied data from my old install into those folders and then added the links.

I sometimes put another install on my sdc drive, but install grub to sda or sdb so I can directly boot it from one time boot key. If you install grub to either data drive you will need the 1 or 2MB bios_grub partition. But as long as just data you do not.
But I am use gpt on all new drives, and I include both an efi partition since that should be near beginning of drive and a bios_grub partition as I like to have an install on every drive. I include efi partition as (for last 2 years) have planned on a new UEFI based system.
      
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by TheElder777 on 2014-05-16
> **oldfred said:**
> I do not suggest pysdm anymore.
You may want  to review the settings used in this as they are generally better.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

    
If you have already mounted with fstab, just use those mounts not the example shown which includes manual mounting. You only can mount a partition once. You just need the chown & chmod with your mounts. use this to see mount.
mount

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

I created all the folders in my data partitions first, copied data from my old install into those folders and then added the links.

I sometimes put another install on my sdc drive, but install grub to sda or sdb so I can directly boot it from one time boot key. If you install grub to either data drive you will need the 1 or 2MB bios_grub partition. But as long as just data you do not.
But I am use gpt on all new drives, and I include both an efi partition since that should be near beginning of drive and a bios_grub partition as I like to have an install on every drive. I include efi partition as (for last 2 years) have planned on a new UEFI based system.
      
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

Thanks again. I edited my fstab and used uuids rather than directories to refer to the drives (as the link u provided), i am assuming this makes it more stable to os updates... After linking my folders I also had to edit my ~/.config/user-dirs.dirs file to make my "Music," "Pictures," and so on, folders be the default folders. I also mounted the hdd to /media ([http://askubuntu.com/questions/22215/why-have-both-mnt-and-media](http://askubuntu.com/questions/22215/why-have-both-mnt-and-media)) .

---

