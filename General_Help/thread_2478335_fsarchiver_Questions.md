---
title: "fsarchiver Questions"
date: 2022-08-23
forum: General Help
---

### Post by artist-wavenet on 2022-08-23
Does fsarchiver record a partitions exact bit pattern, and restore the same when rollback is done, similar to what an iso file would? Or is there no mechanism to assurance files will be rollbacked to the same location they were when archived?

I have Ubuntu working on a RAIDed, an natively encrypted, ZFS file system. The latest version of how I did this can be downloaded from:
[https://www.mediafire.com/file/2w8mdb96tbzslub/Ubuntu_22.04_Root_on_ZFS_Encryption.odt/file](https://www.mediafire.com/file/2w8mdb96tbzslub/Ubuntu_22.04_Root_on_ZFS_Encryption.odt/file)

I attempted to use the fsarchiver to create backups of an EFI partition. This partition was created using these commands:

  ```
SSD1=/dev/disk/by-id/nvme-eui.002538ba11517132
sgdisk     -n 1:1M:+512M   -t 1:EF00 $SSD1
mkdosfs -F 32 -s 1 -n  EFI ${SSD1}-part1
mkdir /boot/efi
echo /dev/disk/by-uuid/$(blkid -s UUID -o value ${SSD1}-part1) \
/boot/efi vfat defaults 0 0 >> /etc/fstab
mount /boot/efi
grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck –no-floppy
```

The command, and command result, for my attempt to use fsarchver to create an archive if /boot/efi

```
root@stephen:~# umount /boot/efi/
root@stephen:~# fsarchiver -o savefs /home/stephen/efi_backup_SSD1  /boot/efi/
oper_save.c#1200,oper_save(): /boot/efi/ is not a valid block device
```

Why is not the SSD partition, which has a mount point at /boot/efi/ not considered a block device?

I seek to backup the efi partition before I do a risky installation that might corrupt it. Can this backup be done with fsarchiver?

---

### Post by Holger_Gehrke on 2022-08-23
> **artist-wavenet said:**
> 
```
root@stephen:~# umount /boot/efi/
root@stephen:~# fsarchiver -o savefs /home/stephen/efi_backup_SSD1  /boot/efi/
oper_save.c#1200,oper_save(): /boot/efi/ is not a valid block device
```

Why is not the SSD partition, which has a mount point at /boot/efi/ not considered a block device?

I seek to backup the efi partition before I do a risky installation that might corrupt it. Can this backup be done with fsarchiver?

That's just it, it's a mount point, not a block device. Just because it's in the fstab as the mount point for your ESP doesn't mean that's what's currently mounted there. You could have mounted something else there. 'fsarchiver' wants an actual block device, something like /dev/sda1 or /dev/nvme1p1.

And if I read the documentation for fsarchiver right, it doesn't do bit exact copies. It stores the files with their content and with all the attributes and some of the metadata for the filesystem but it doesn't store what blocks the data occupies. This is intentional since one of the use cases is restoring the image to a smaller file system or to a different file system.

---

### Post by artist-wavenet on 2022-08-24
I got a list of devices, and then attempted to archive the desired devices. I got the same error:

```
root@stephen:~# fsarchiver probe
[======DISK======] [=============NAME==============] [====SIZE====] [MAJ] [MIN]
[sda             ] [HGST HUH721212AL               ] [    10.91 TB] [  8] [  0]
[sdb             ] [HGST HUH721212AL               ] [    10.91 TB] [  8] [ 16]
[nvme0n1         ] [Samsung SSD 980 PRO 2TB                 ] [     1.82 TB] [259] [  0]
[nvme1n1         ] [Samsung SSD 980 PRO 2TB                 ] [     1.82 TB] [259] [  7]

[=====DEVICE=====] [==FILESYS==] [======LABEL======] [====SIZE====] [MAJ] [MIN] 
[sda1            ] [zfs_member ] [hpool            ] [    10.91 TB] [  8] [  1] 
[sdb1            ] [zfs_member ] [hpool            ] [    10.91 TB] [  8] [ 17] 
[zd0             ] [swap       ] [<unknown>        ] [   256.00 GB] [230] [  0] 
[nvme0n1p1       ] [vfat       ] [EFI              ] [   512.00 MB] [259] [  1] 
[nvme0n1p3       ] [zfs_member ] [bpool            ] [     2.00 GB] [259] [  2] 
[nvme0n1p4       ] [zfs_member ] [rpool            ] [     1.74 TB] [259] [  3] 
[nvme0n1p5       ] [<unknown>  ] [<unknown>        ] [  1000.00 KB] [259] [  4] 
[nvme0n1p6       ] [zfs_member ] [hpool            ] [    10.00 GB] [259] [  5] 
[nvme0n1p7       ] [zfs_member ] [<unknown>        ] [    64.00 GB] [259] [  6] 
[nvme1n1p1       ] [vfat       ] [EFI              ] [   512.00 MB] [259] [  8] 
[nvme1n1p3       ] [zfs_member ] [bpool            ] [     2.00 GB] [259] [  9] 
[nvme1n1p4       ] [zfs_member ] [rpool            ] [     1.74 TB] [259] [ 10] 
[nvme1n1p5       ] [<unknown>  ] [<unknown>        ] [  1000.00 KB] [259] [ 11] 
[nvme1n1p6       ] [zfs_member ] [hpool            ] [    10.00 GB] [259] [ 12] 
[nvme1n1p7       ] [zfs_member ] [<unknown>        ] [    64.00 GB] [259] [ 13] 
root@stephen:~# fsarchiver -o savefs /home/stephen/efi_backup_SSD nvme0n1p1 nvme1n1p1
oper_save.c#1200,oper_save(): nvme0n1p1 is not a valid block device

```

---

### Post by Holger_Gehrke on 2022-08-25
The device files are in /dev/ normally. I don't think you've got a device file for the partition you're trying to image in ~/ unless you created one using 'mknod'. So the command should probably be something like
```

fsarchiver savefs /home/stephen/efi_backup_SSD /dev/nvme0n1p1 /dev/nvme1n1p1

```
Admittedly, the error message is a bit strange - it should probably be something like 'device file not found'. The way it's worded it sounds like there is a (normal) file named nvme0n1p1 in the current working directory.

Holger

---

### Post by HermanAB on 2022-08-25
Bear in mind that fsarchiver does not work will all file systems.  I would not use it with either ZFS or XFS for example, since those file systems have their own tools for the purpose.

---

### Post by VMC on 2022-08-25
I agree with HermnAB. Definitely not ntfs. I only use it on my ext4.

---

### Post by artist-wavenet on 2022-08-25
Thank you Holger_Gehrke for you answer, which did work. I have now a command sequence the works, which is:
```

                        mount -o remount,ro /dev/nvme0n1p1

 fsarchiver -o savefs /home/stephen/efi_backup_SSD \
                      /dev/nvme0n1p1 /dev/nvme1n1p1
 mount -o remount,rw /dev/nvme0n1p1
  
 # Note: nvme1n1p1 is not remounted read only because it was never mounted,
 # and so there is not a need to, and there is an error if attempted.
 # nvme1n1p1 nevertheless got backed up according to the fsarchiver
 # command’s output statistics.
```.

Now I need to back up the BIOS partition which is in Partition #5. I know a file's sector locations within a an efi partition are not important. I am not at all sure if this is also true for a BIOS partition. Is it?

I suspect my installation procedure never put anything in the BIOS partition because "fsarchiver probe" shows this to be of an unknown format, and there is nothing obvious to me in the installation procedure I did that shows an MBR, or anything else, was put there. If the fsarchiver cannot identify the format, does that necessarily mean nothing is there? If something is there I want to back it up. What is the best way to do that?

---

### Post by artist-wavenet on 2022-08-25
Thank you Holger_Gehrke for you answer, which did work. I have now a command sequence the works, which is:
```

mount -o remount,ro /dev/nvme0n1p1
fsarchiver -o savefs /home/stephen/efi_backup_SSD \
                      /dev/nvme0n1p1 /dev/nvme1n1p1
mount -o remount,rw /dev/nvme0n1p1
 
# Note: nvme1n1p1 is not remounted read only because it was never mounted,
# and so there is not a need to, and there is an error if attempted.
# nvme1n1p1 nevertheless got backed up according to the fsarchiver
# command&#8217;s output statistics.
```
Now I need to back up the BIOS partition which is in Partition #5. I know a file's sector locations within a an efi partition are not important. I am not at all sure if this is also true for a BIOS partition. Is it?

I suspect my installation procedure never put anything in the BIOS partition because "fsarchiver probe" shows this to be of an unknown format, and there is nothing obvious to me in the installation procedure I did that shows an MBR, or anything else, was put there. If the fsarchiver cannot identify the format, does that necessarily mean nothing is there? If something is there I want to back it up. What is the best way to do that?

---

### Post by Holger_Gehrke on 2022-08-25
Is [this]("https://en.wikipedia.org/wiki/BIOS_boot_partition") what you're talking about when you mention a BIOS partition ? If so, then something is strange. Did your system start out as a BIOS system and get updated to UEFI with a new main board ? You should either have UEFI and an ESP or BIOS and a BIOS partition but not both. A BIOS partition is normally raw code that gets loaded into memory by the first stage of grub from the MBR and then gets executed. Should be 30+ kb of code followed by garbage / zeroes. If you still want to image it, read the manual for 'dd'. It should be something like 'dd if=/dev/nvme0n1p5 of=biospart.img bs=1M count=1'. You could run it through gz, bzip2 or xz to save some disk space.

Holger

---

### Post by pbear42 on 2022-08-25
You can confirm it's a BIOS boot partition with **parted**.  Nothing wrong with having both a BBP and an ESP.  I do that as a matter of course for full install USB drives. And now standard Ubuntu procedure for erase-and-install on BIOS systems.
```
pbear@ubuntu-22-04:~$ sudo parted -l
[sudo] password for pbear: 
Model: ATA VBOX HARDDISK (scsi)
Disk /dev/sda: 64.4GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  2097kB  1049kB                                     bios_grub
 2      2097kB  540MB   538MB   fat32        EFI System Partition  boot, esp
 3      540MB   64.4GB  63.9GB  ext4
```
This is a VBox VM in default (legacy boot) mode.  Notice file system is blank.  That's because it's unformatted (one of the options in GParted, btw).  What you're looking for is the bios_grub flag.

Frankly, I think it would be easier to reinstall the BIOS boot loader than figure out how to backup and restore it, but that's your decision obviously.

---

### Post by artist-wavenet on 2022-08-26
Yes, that is the BIOS I am talking about. There iare both a BIOS partition (partition 5), and and EFI partition (partition 1). It is that way because my procedure is a customized version of this one:
  [URL="https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html"]https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html
[/URL]
Mine is customized for my hardware, plus my desire to have both RAID, and encryption.

In Step 2.3 there is this:
> **Note:** While the Ubuntu installer uses an MBR label for legacy (BIOS) booting, this HOWTO uses GPT partition labels for both UEFI and legacy (BIOS) booting. This is simpler than having two options.  It is also provides forward compatibility (future proofing).  In other words, for legacy (BIOS) booting, this will allow you to move the disk(s) to a new system/motherboard in the future without having to rebuild the pool (and restore your data from a backup). The ESP is created in both cases for similar reasons.  Additionally, the ESP is used for /boot/grub in single-disk installs, .....

I do not think it  likely my SDDs will ever have to be booted by a mother board that has BIOS, and needs an MBR. However, although my knowledge of this gets better as I work out problems doing this, I still do not know well what I am doing with it, and so I depend very much on those instructions. I therefore alter those instructions as little as possible to just generally avoid trouble with it as much as I can.

---

### Post by artist-wavenet on 2022-08-26
Thank youpbear42 for your most helpful suggestion. This is the relevant line in the result I got:
 ```
5      24.6kB  1049kB  1024kB                     bios_grub
```
This is the verification I was seeking. It shows I do have an MBR written in Partition 5.

If I were to back this up I would have to do so in a way that would make possible the same bit patterns in the same sectors. If this is going to be too difficult I am going to pass on backing this up. There is risk in what I am going to do next, but I doubt very much it will put at risk the MBR.

---

### Post by sudodus on 2022-08-26
There is no file system in the bios_grub partition. For that reason you should **clone** it to an image file (for example using **dd** or **cp** or **cat**; please doublecheck the command because there is no 'final checkpoint' and if you get things wrong, you might overwrite valuable data).

An alternative to backup the whole drive in an optimal way is to use [Clonezilla](https://askubuntu.com/questions/958242/fastest-way-to-copy-hdd/958248#958248).

---

### Post by pbear42 on 2022-08-26
> **artist-wavenet said:**
> If this is going to be too difficult I am going to pass on backing this up.
To clarify, I assume sudodus and holger's suggestions will work.  What would worry me is restore, and I wouldn't rely on it unless tested.  Instead, I'd have written down somewhere I can count on being available during a restore scenario instructions for reinstalling the BIOS boot loader.  I would plan to run the instructions from a live session and would save them in a plain text file.

On the other hand, I'm very comfortable with installing Grub manually (have done it many times).  If you are not, this strategy might not be a good fit for you.

---

