---
title: "Read NTFS hard drives"
date: 2019-09-09
forum: General Help
---

### Post by dtree46 on 2019-09-09
Have 3 NTFS hard drives that need to be available to Ubuntu 18.04 LTS.

Are there instructions or tutorials available online?

If not, any help appreciated.

dlw

---

### Post by TheFu on 2019-09-09
Google found this: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
"ubuntu ntfs fstab" was the search I used.

---

### Post by oldfred on 2019-09-09
Are they internal drives?

Used with Windows 8 or 10? 
If so fast start up must be off or hibernation flag will prevent the Linux NTFS driver from writing into the NTFS to prevent damage to hibernation.

Post these:
sudo parted -l
       lsblk -o name,mountpoint,label,size,fstype,uuid | egrep -v "^loop"

If internal drives, you can mount with fstab.
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by ajgreeny on 2019-09-09
Are these drives internally connected or USB external drives?

Be aware that if used in Windows but not removed properly (if USB drives) they will not be available to you from any Linux OS.  If internal drives from a dual boot system of Win 8 or Win 10 it is imperative that you disable fast start, ie, a similar state to hibernation, on the Windows OS or these drives will be detected by a Linux OS as still in use and therefore not mountable.

EDIT:
Too slow and beaten to it by oldfred.

---

### Post by dtree46 on 2019-09-09
> **oldfred said:**
> Are they internal drives?

Used with Windows 8 or 10? 
If so fast start up must be off or hibernation flag will prevent the Linux NTFS driver from writing into the NTFS to prevent damage to hibernation.

Post these:
sudo parted -l
       lsblk -o name,mountpoint,label,size,fstype,uuid | egrep -v "^loop"

If internal drives, you can mount with fstab.
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Yes, 2 - 1tb hard drives internal. 1 - 250gb hard drive external.pa

```
Model: Maxtor OneTouch (scsi)
Disk /dev/sdd: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                          Flags
 1      17.4kB  134MB  134MB               Microsoft reserved partition  msftres
 2      135MB   250GB  250GB  ntfs         Basic data partition          msftdata


Model: Generic- SD/MMC/MS PRO (scsi)
Disk /dev/sde: 31.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.9GB  31.9GB  primary  fat32        boot, lba
```

```
dlw@don-750:~$ lsblk -o name,mountpoint,label,size,fstype,uuid | egrep -v "^loop"
NAME   MOUNTPOINT                      LABEL        SIZE FSTYPE   UUID
sda                                                 477G          
&#9492;&#9472;sda1 /                                            477G ext4     bf66b372-953c-4e7d-a789-d6c355ca6d49
sdb                                               931.5G          
&#9492;&#9472;sdb1                                 New Volume 931.5G ntfs     28583D89583D5732
sdc                                               931.5G          
&#9492;&#9472;sdc1                                 Windows    931.5G ntfs     0EB04BDD6829B695
sdd                                               232.9G          
&#9500;&#9472;sdd1                                              128M          
&#9492;&#9472;sdd2 /media/dlw/250gb                250gb      232.8G ntfs     58CABE14CABDEE7E
sde                                                29.7G          
&#9492;&#9472;sde1 /media/dlw/32GB                 32GB        29.7G vfat     C4F8-640A
sr0                                                1024M

```
Does this help?

```
/dev/sda1: UUID="bf66b372-953c-4e7d-a789-d6c355ca6d49" TYPE="ext4" PARTUUID="1982e6bb-01"
/dev/sdb1: LABEL="New Volume" UUID="28583D89583D5732" TYPE="ntfs" PARTUUID="87dac546-01"
/dev/sdc1: LABEL="Windows" UUID="0EB04BDD6829B695" TYPE="ntfs" PARTUUID="a0a9043e-01"
/dev/sdd1: PARTLABEL="Microsoft reserved partition" PARTUUID="f80480fe-d551-420f-9c4b-666529d8b3bf"
/dev/sdd2: LABEL="250gb" UUID="58CABE14CABDEE7E" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="dc3dd7ff-9f46-4f5c-9981-9e0cc1efcef3"
```

---

### Post by oldfred on 2019-09-09
Generally best not to mount external in fstab as if not present, boot may be delayed while it looks for it or it may not boot. TheFu knows some parameters for mount if only required, but do not know if that works with NTFS.

       For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 

You have to create mount points, best not to use spaces with Linux. I converted even when still using XP to CamelCase, under_score, or justonelabel.
I also have changed from defaults to either relatime for HDD or noatime for SSD.

Another set of suggested parameters.
      
 [https://ubuntuforums.org/showthread.php?t=2420861&p=13865822#post13865822](https://ubuntuforums.org/showthread.php?t=2420861&p=13865822#post13865822)
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,fstype=ntfs,uid=1000,gid=1000,fmask=0002,dmask=0002
The big_writes mount option does help performance greatly. 

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 

Add entries to fstab like examples above, but use your UUIDs from sdb1 & sdc1
After creating mount points which do not have to be same as label.
      
 ** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

for more info on parameters, q to exit:
man mount
man fstab

---

### Post by dtree46 on 2019-09-10
Problem solved except for the 32gb SD card. See attached photo.
It is there. when opened the data on it does not show.
That is where the backups are and need to opened.
How can this data be recovered?

---

### Post by TheFu on 2019-09-10
Please be aware that using a GUI to temporarily mount NTFS or FAT32 or exFAT storage will cause a 30% or so performance hit.  I don't know of any methods short of using one of these 3 methods to solve it:
[LIST]
[*]fstab
[*]manual mount
[*]using autofs
[/LIST]

Each of my listed methods allows performance options that the GUI methods do not support.  About 8 months ago, the Gnome team tried to make their access faster. It was reported, but I haven't seen any newer information that it succeeded or that it has made it into any distro release at this point.

---

