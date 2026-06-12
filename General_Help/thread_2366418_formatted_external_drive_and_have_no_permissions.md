---
title: "formatted external drive and have no permissions"
date: 2017-07-17
forum: General Help
---

### Post by flucoe2 on 2017-07-17
Hi,

I formatted an external drive to ext4 and now I don't have the permissions to write on it. How can I make it so the drive is automatically mounted when plugged with the right permissions?

Some information

```

sudo fdisk -l
Disk /dev/sda: 447.1 GiB, 480103981056 bytes, 937703088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D0F2DEFA-BBE2-489D-8045-02D644F2DB7D


Device        Start       End   Sectors   Size Type
/dev/sda1      2048   1050623   1048576   512M EFI System
/dev/sda2   1050624   7051263   6000640   2.9G Linux swap
/dev/sda3   7051264  83048447  75997184  36.2G Linux filesystem
/dev/sda4  83048448 937701375 854652928 407.5G Linux filesystem


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 6EC4F0E0-EE2D-46D7-B71E-C5A6CDB69DFC


Device     Start        End    Sectors   Size Type
/dev/sdb1   2048 1953523711 1953521664 931.5G Linux filesystem




Disk /dev/sdc: 7.3 TiB, 8001563221504 bytes, 15628053167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 715DA6C4-9BF6-4A9E-B472-37C86CD4D260


Device     Start         End     Sectors  Size Type
/dev/sdc1   2048 15628052479 15628050432  7.3T Linux filesystem



```

I'm interested in the third one, /dev/sdc

```
sudo lsblk -fNAME   FSTYPE LABEL      UUID                                 MOUNTPOINT
sdb                                                           
&#9492;&#9472;sdb1 ext4   ExtraDrive 22a72fcc-d80b-4c5f-8954-6f5f8d1fb252 /media/fernando/ExtraDrive
sr0                                                           
sdc                                                           
&#9492;&#9472;sdc1 ext4   Fernando   2055d187-ee30-475a-9ecd-dcee1d2f34bf /media/fernando/Fernando
sda                                                           
&#9500;&#9472;sda4 ext4              b3541b69-1dc1-4512-82b4-a47fdb227a8b /home
&#9500;&#9472;sda2 swap              dde8727b-cb92-4c3c-8c6b-04bc72440f06 [SWAP]
&#9500;&#9472;sda3 ext4              ae4bcc2e-8d4c-45c9-b98f-1f0c3a5163a2 /
&#9492;&#9472;sda1 vfat              A659-2C25                            /boot/efi
```

So, it shows up here as well. But 

```

ls -l
drwxr-xr-x 3 root     root     4096 Jul 17 14:48 Fernando

```

So, I used GParted to format it and the owner seems to be root rather than me. Any way to solve this without having to re-execute commands every time I plug the drive? If no, what should I do every time?

Thanks.

---

### Post by Dennis N on 2017-07-17
You need to change the owner and group of the mount point to your user name.

If your user name is: fernando
Plug the drive in and
```
sudo chown -R fernando:fernando /media/fernando/Fernando
```

will make you owner of any existing folders and files on there, as well as new ones you add later.

You only need to do this once. Next time you should have access.

---

### Post by oldfred on 2017-07-17
If you know drive will always be plugged in when rebooting, you can add it to fstab, but normally you do not add external devices to fstab as if not plugged in, you may have issues booting.

 #if not known to list partitions, change sdc1 to your data partition or create multiples with different mount points, always check drive order. I have had external flash drives change order or my sdf becomes sdb on reboot and every other drive also changed, as I did not plug internal drives in SATA port order. 
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sdc1 /mnt/data
#where sdc1 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data 

Do you really want one partition of 8GB? If using for video recordings you may. But if just data, how are you backing up. And fsck or backups one one very large partition can take a long time.

If you do want to mount in fstab:
      [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by flucoe2 on 2017-07-17
Dennis N, oldfred, thanks!

---

