---
title: "Partitioning 2nd HD that's now ntfs"
date: 2015-09-26
forum: General Help
---

### Post by ra7411 on 2015-09-26
I thought this would be easy, but Gparted doesn't seem to facilitate what I want to do.

1) New computer w/ a new 2tb HD that I installed Ubuntu 14.04 onto. Everything went ok.

2) I installed a 1tb ntfs HD  and copied lots of old w8.1 ntfs files over to my 2tb HD (ext format).

3) I want to re-partition and reformat this old 1tb ntfs HD, which has a .3tb partition and a .7tb partition, into a 1tb partition ext formatted drive.  

Gparted won't let me extend either of the the existing ntfs partitions to the whole disk, and get on with things.

So, how do I do this? I can go the terminal route or Gparted. 

Thanks

---

### Post by Dennis N on 2015-09-26
Make a new partition table (MS-DOS or GPT) on the 1 TB drive using gparted. The drive will then be unallocated space. Then create your ext4 partition in the unallocated space.

---

### Post by ra7411 on 2015-09-26
THanks, that worked.

Something else- after re-partitioning the 1tb hd, I now have a 3rd HD of 243 MiB, with some files like lost+found, grub, memtest86+.bin etc.

I don't think it existed previously. What is it, and which HD is it actually on?

---

### Post by oldfred on 2015-09-26
Do you have UEFI boot, or did you use full drive LVM or LVM with encryption and then also have a separate /boot partition. Otherwise separate /boot partitions not normally suggested for desktop installs.

Post these:
sudo parted -l
cat /etc/fstab

---

### Post by ra7411 on 2015-09-26
[COLOR=#000000]>Do you have UEFI boot, or did you use full drive LVM or LVM with encryption and then also have a separate /boot partition. Otherwise separate /boot partitions not normally suggested for desktop installs.<

It's a regular BIOS. I don't know what LVM is and I haven't used encryption on anything so far. The new drive was previously installed as an ntfs w/ 2 partitions, I re-partioned and formated as ext4 - I didn't do anything fancy.
[/COLOR]
>
[COLOR=#000000]Post these:[/COLOR]
[COLOR=#000000]sudo parted -l[/COLOR]
<

ra@raub:~$ sudo parted -l
Model: ATA Hitachi HDS72202 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   2000GB  2000GB  extended
 5      257MB   2000GB  2000GB  logical                lvm




Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 8565MB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  8565MB  8565MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 1991GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  1991GB  1991GB  ext4

[COLOR=#000000]Do you have UEFI boot, or did you use full drive LVM or LVM with encryption and then also have a separate /boot partition. Otherwise separate /boot partitions not normally suggested for desktop installs.[/COLOR]

[COLOR=#000000]>
Post these:[/COLOR]

[COLOR=#000000]cat /etc/fstab
[/COLOR]<

ra@raub:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=fc4e02a7-cf03-4524-b211-546e1e2af19b /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0




xxxxxxxxx

---

### Post by oldfred on 2015-09-26
Well, you do have LVM, not sure if you also have encryption, but I do not know much about either.

You cannot use gparted on LVM in your sda install, but should be able to use gparted on your sdb drive. It shows you have an ext4 partition.

Generally then with an ext4 data partition you have to give yourself ownership and permissions to use it. You have to create a mount point first also.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[URL="https://wiki.archlinux.org/index.php/Fstab"]https://wiki.archlinux.org/index.php/Fstab
[/URL]
 [URL="https://help.ubuntu.com/community/FilePermissions"]https://help.ubuntu.com/community/FilePermissions

      [/URL]
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

If you want to auto mount with fstab, so every time you reboot it is there, you can do this. Really only a good way to mount if internal drive.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.




    [URL="https://help.ubuntu.com/community/FilePermissions"]
[/URL]

[URL="https://wiki.archlinux.org/index.php/Fstab"]
[/URL]

---

### Post by ra7411 on 2015-09-26
Oldfred,

I have no idea what you're addressing. I did get the second HD partitioned and formatted using Gparted.

I was asking about a HD that shows up in Dolphin; I don't think it was present before I did the re-partition of the 2nd HD.

It shows up as: 234 MiB Hard Drive, [COLOR=#000000]with some files like lost+found, grub, memtest86+.bin etc.  It is mounted.

It doesn't show up in Disks.

I was just wondering what it was and where it came from.


[/COLOR]

---

### Post by oldfred on 2015-09-26
That is then your /boot partition.
Small size difference often different tools including or not the extra 5% that Linux file systems reserve or the difference between MiB vs MB.

---

### Post by ra7411 on 2015-09-26
ok, thanks, I guess I won't mess with it.

Do you know if a disk image can be run from Disks, during a regular session, or does it require using a boot disc of some sort?

---

### Post by oldfred on 2015-09-26
Disks does not run anything, just partitioning and edition of partitions.
If you want to boot a live install you need to install ISO to DVD or flash drive. You can also use grub2 to loopmount an ISO on a hard drive or flash drive and install to another drive.

---

