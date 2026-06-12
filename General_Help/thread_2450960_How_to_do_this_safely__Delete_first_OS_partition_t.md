---
title: "How to do this safely :: Delete first OS partition to expand second OS"
date: 2020-09-23
forum: General Help
---

### Post by bojoby on 2020-09-23
How can I do this safely?

sda
sda1 EFI boot
sda2 ext4 old linux
sda4 Linux swap
sda3 ext4 Ubuntu20

Using gpartd.
sda 2 I want to remove (no longer required),  
then expand sda3 to use the unused space on sda.

What do I do with the swap partition?  Or do I move it also forward to the EFI partition? Do remove but leave some space at end?
sda2 is a debian version.
sda4 is ubuntu 20

thanks in advance
bob

---

### Post by TheFu on 2020-09-23
Please post commands and output so we have facts without interpretation.  For example, we need to see the actual block locations. The partition numbers don't necessarily relate to on-disk order.

**sudo fdisk -l /dev/sda** will show what we need. Also, the output from 
**lsblk -e 7 -o name,size,type,fstype,mountpoint** would be helpful from an overview standpoint.

Please use "code tags", because things need to line up in columns.  Anytime you post commands + output, **_[COLOR="#FF0000"]use 'code tags.'[/COLOR]_** 
Hint: Use the "advanced editor"

---

### Post by UltimateCat on 2020-09-24
It might help us if you can take a screenshot of all of your partitions in g-parted and post that.

If not run this command as root and post the output.

```
sudo fdisk -l

```

I wouldn't delete the swap partition.;)

---

### Post by bojoby on 2020-09-24
Thanks for the reply and help.  

```
 sudo fdisk -l /dev/sda

[sudo] password for aj: 
Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: WDC WDS100T2B0A-
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 9E905025-16D4-45A4-8B36-FF13B8732327

Device         Start        End    Sectors   Size Type
/dev/sda1       2048    1050623    1048576   512M EFI System
/dev/sda2    1050624  670836735  669786112 319.4G Linux filesystem
/dev/sda3  703940608 1953523711 1249583104 595.9G Linux filesystem
/dev/sda4  670836736  703940607   33103872  15.8G Linux swap

Partition table entries are not in disk order.
```
```
aj@ajtj:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME     SIZE TYPE FSTYPE MOUNTPOINT
sda    931.5G disk        
&#9500;&#9472;sda1   512M part vfat   /boot/efi
&#9500;&#9472;sda2 319.4G part ext4   
&#9500;&#9472;sda3 595.9G part ext4   /
&#9492;&#9472;sda4  15.8G part swap   
sdb    232.9G disk        
&#9500;&#9472;sdb1   100M part vfat   
&#9500;&#9472;sdb2   128M part        
&#9492;&#9472;sdb3 232.7G part ntfs   
sdc      2.7T disk        
&#9500;&#9472;sdc1 976.3G part ntfs   
&#9500;&#9472;sdc2 971.7G part ntfs   
&#9492;&#9472;sdc3 846.5G part ntfs   
sdd      3.7T disk        
&#9492;&#9472;sdd1   3.7T part ntfs   /media/aj/BkUp
sr0     1024M rom   

```
(I have 3 drives, sda is Linux,  sdb is Mollysoft,  sdc is storage,  sdd is external backup)
      
```
aj@ajtj:~$ sudo fdisk -l

Disk /dev/sdc: 2.75 TiB, 3000592982016 bytes, 5860533168 sectors
Disk model: WDC WD30EZRX-00D
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: A94B91C7-FCBF-4013-9BCC-0C5F5B0E0A1B

Device          Start        End    Sectors   Size Type
/dev/sdc1        4096 2047490047 2047485952 976.3G Microsoft basic data
/dev/sdc2  2047490048 4085250047 2037760000 971.7G Microsoft basic data
/dev/sdc3  4085250048 5860532223 1775282176 846.5G Microsoft basic data


Disk /dev/sdb: 232.91 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 840 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8353537F-490A-491E-80B1-8AD14C0F6D8C

Device      Start       End   Sectors   Size Type
/dev/sdb1    2048    206847    204800   100M EFI System
/dev/sdb2  206848    468991    262144   128M Microsoft reserved
/dev/sdb3  468992 488396799 487927808 232.7G Microsoft basic data


Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: WDC WDS100T2B0A-
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 9E905025-16D4-45A4-8B36-FF13B8732327

Device         Start        End    Sectors   Size Type
/dev/sda1       2048    1050623    1048576   512M EFI System
/dev/sda2    1050624  670836735  669786112 319.4G Linux filesystem
/dev/sda3  703940608 1953523711 1249583104 595.9G Linux filesystem
/dev/sda4  670836736  703940607   33103872  15.8G Linux swap

Partition table entries are not in disk order.

Disk /dev/sdd: 3.65 TiB, 4000752599040 bytes, 7813969920 sectors
Disk model: My Passport 259D
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 78223112-4F4D-4F30-B830-9A780741A60E

Device     Start        End    Sectors  Size Type
/dev/sdd1   2048 7813967871 7813965824  3.7T Microsoft basic data
aj@ajtj:~$ 

```

On sda2 and 3,  a swap file is at /swapfile,    so I'm guessing sda4 was from a prior linux install
and no space was in use.

Thanks.    Bob.

---

### Post by UltimateCat on 2020-09-26
OK, so looking at all of the output, /dev/sda4/ is a linux-swap partition yes. And most likely it is a swap from a prior Linux installation.
If you didn't create that swap during installation most likely the installer/partition mgr did it for you.

If you plan on keeping those distros on /dev/sda2/ 3.19.4 GB and /dev/sda3/ 595.9 GB you might not want to delete that linux-swap partition unless you have plently of RAM.

In order to delete that partition that you want to just make sure in g-parted that you have the correct device selected before you delete the partition.
You can't delete a partition on Linux if your mounted to that partition so I recommend that you use g-parted Live.
[https://gparted.org/livecd.php](https://gparted.org/livecd.php)

Which operating system is at the very top of your Grub Menu when you first boot up?

Are you just trying to free up space on your 1 TB Western Digital HDD?

---

### Post by TheFu on 2020-09-26
Or use any Ubuntu Desktop Installation ISO in the "Try Ubuntu" mode, which includes a current gparted version.

BTW, I would have responded 2 days ago, but without **code tags**, it is too easy for me to make a mistake. The columns still aren't lining up. Code tags are necessary.

---

### Post by UltimateCat on 2020-09-26
Take your time and go slow-;)

Enjoy the rest of the weekend!

---

