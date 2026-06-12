---
title: "Can't create a partion in hard drive"
date: 2022-01-03
forum: General Help
---

### Post by skrach33 on 2022-01-03
Hi,

Been trying to solve this issue, installed a new distro and almost everything went ok, only one hard drive didn't mount, it says that it hasn't any valid partition table. When I tried to write one with gparted it doesn't let me. Tried with parted, fsck and I can't. Used Smartools and it said it had no issue, did Badblocks, no errors. Tried to recover superblocks but noting. Been looking for answers and haven't found nothing specific, but learned a lot.

Sorry if I don't put the right information, don't know to much of Linux. If you need more information I will try to look for it.

This is what I with fsck

> [FONT=monospace][COLOR=#000000]fsck from util-linux 2.34 [/COLOR]
e2fsck 1.45.5 (07-Jan-2020) 
ext2fs_open2: Bad magic number in super-block 
fsck.ext2: Superblock invalid, trying backup blocks... 
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdd 

The superblock could not be read or does not describe a valid ext2/ext3/ext4 
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4 
filesystem (and not swap or ufs or something else), then the superblock 
is corrupt, and you might try running e2fsck with an alternate superblock: 
    e2fsck -b 8193 <device> 
 or 
    e2fsck -b 32768 <device>
[/FONT]

And thanks in advance for any help

---

### Post by sudodus on 2022-01-03
- How is the hard disk drive connected (IDE, SATA, eSATA, USB)?

- What happens if you try with gparted again?

 . save valuable files from the drive to another drive before going ahead
 . unmount all partitions on the drive
 . gparted: create a new partition table (Device - Create Partition Table ...)
 . gparted: create a partition (and select file system)

 . Please describe what works and what fails (and post the error message, if any).

---

### Post by rsteinmetz70112 on 2022-01-03
What does your /etc/fstab look like?
What does  sudo lsblk show?

---

### Post by HermanAB on 2022-01-04
First, fsck doesn’t have anything to do with partition management. Second, the disk must be unmounted to modify the partition table. Third, be careful that you don’t mess up your main drive.  The targeted disk should be /dev/sdb or sdc, not sda - your main disk.

---

### Post by The Cog on 2022-01-04
/dev/sdd is the raw drive, and it is unusual to directly format a drive with a filesystem (though it can be done). The normal thing to do is to write a partition table on the drive and then create partitions, which would then be /dev/sdd1, /dev/sdd2 etc., and then format the individual partitions.

When posting the output of a command, please also always post the command itself so we can check exactly what you are asking, and check for errors.

---

### Post by skrach33 on 2022-01-04
> **sudodus said:**
> - How is the hard disk drive connected (IDE, SATA, eSATA, USB)?

- What happens if you try with gparted again?

 . save valuable files from the drive to another drive before going ahead
 . unmount all partitions on the drive
 . gparted: create a new partition table (Device - Create Partition Table ...)
 . gparted: create a partition (and select file system)

 . Please describe what works and what fails (and post the error message, if any).

Hi, thanks for answering

When I try using gparted it only lets me try to make a partition table but after applying it stays the same (without partition table) . It says its "unallocated" and in information it says a warning "/dev/sda: unrecognised disk label"

The disk is new bought it 3 months ago, but was working fine. All the information was backed up
The disk drive is unmounted, can't mount it

---

### Post by skrach33 on 2022-01-04
> **rsteinmetz70112 said:**
> What does your /etc/fstab look like?
What does  sudo lsblk show?

Hi rsteinmetz70112,

lsblk:
> [FONT=monospace][COLOR=#000000]
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT [/COLOR]
loop0    7:0    0  55.5M  1 loop /snap/core18/2253 
loop1    7:1    0     4K  1 loop /snap/bare/5 
loop2    7:2    0   277M  1 loop /snap/gimp/380 
loop3    7:3    0  61.9M  1 loop /snap/core20/1270 
loop4    7:4    0 391.3M  1 loop /snap/gimp/383 
loop5    7:5    0 164.8M  1 loop /snap/gnome-3-28-1804/161 
loop6    7:6    0  65.2M  1 loop /snap/gtk-common-themes/1519 
loop7    7:7    0 603.1M  1 loop /snap/libreoffice/239 
loop8    7:8    0  43.3M  1 loop /snap/snapd/14295 
loop9    7:9    0 247.9M  1 loop /snap/gnome-3-38-2004/87 
sda      8:0    0   1.8T  0 disk  
sdb      8:16   1 232.9G  0 disk  
|-sdb1   8:17   1   300M  0 part /boot/efi 
|-sdb2   8:18   1   7.8G  0 part  
`-sdb3   8:19   1  97.7G  0 part / 
sdc      8:32   1 931.5G  0 disk  
`-sdc1   8:33   1 931.5G  0 part /home 
sdd      8:48   1 931.5G  0 disk  
`-sdd1   8:49   1 931.5G  0 part 


[/FONT]

And fstab:
> 
[FONT=monospace][COLOR=#18b2b2]# <file system>             <mount point>  <type>  <options>  <dump>  <pass>[/COLOR][COLOR=#000000] [/COLOR]
UUID=1552-4D88                            /boot/efi      vfat    defaults,noatime 0 2 
UUID=6c96748b-609e-4bae-a0d7-faac2c2abc59 /              ext4    defaults,noatime,discard 0 1 
UUID=8f1ac910-0ce7-42db-a611-2546fa938a20 /home          ext4    defaults,noatime 0 2 
tmpfs                                     /tmp           tmpfs   defaults,noatime,mode=1777 0 0

[/FONT]

---

### Post by skrach33 on 2022-01-04
> **HermanAB said:**
> First, fsck doesn’t have anything to do with partition management. Second, the disk must be unmounted to modify the partition table. Third, be careful that you don’t mess up your main drive.  The targeted disk should be /dev/sdb or sdc, not sda - your main disk.

Thanks for answering,

Sorry, wasn't fsck, it was fdisk, didn't work. 

About targeting the correct disk, I have been careful, thanks

---

### Post by skrach33 on 2022-01-04
> **The Cog said:**
> /dev/sdd is the raw drive, and it is unusual to directly format a drive with a filesystem (though it can be done). The normal thing to do is to write a partition table on the drive and then create partitions, which would then be /dev/sdd1, /dev/sdd2 etc., and then format the individual partitions.

When posting the output of a command, please also always post the command itself so we can check exactly what you are asking, and check for errors.

The thing is that I'm no t being able to write a partition table. Can it be that the hardrive is corrupted even if smartools says it's ok?

Greetings

---

### Post by ajgreeny on 2022-01-04
> **skrach33 said:**
> Hi, thanks for answering

When I try using gparted it only lets me try to make a partition table but after applying it stays the same (without partition table) . It says its "unallocated" and in information it says a warning "/dev/sda: unrecognised disk label"

The disk is new bought it 3 months ago, but was working fine. All the information was backed up
The disk drive is unmounted, can't mount it
After creating a partition table the disk will still show as unallocated; to be able to use the disk you need to immediately create one or more partitions or you will still be unable to do anything with the disk.

A partition table does not create partitions; that has to be done separately.

---

### Post by sudodus on 2022-01-04
When using gparted and you have a partition table, you can right-click on a graphic representation of the unallocated drive space and select New, and in a new window select file system (and if you wish a label that is easy to remember), click on the Add button and when it looks good finally click on the tick icon to perform the actions to create a partition with the selected file system. [I]See the attached screenshot.
[/I]
[This link](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS?action=AttachFile&do=view&target=GrowIt.pdf) is not exactly showing how to create a partition, but it shows several screenshots of how to use gparted.

---

### Post by oldfred on 2022-01-04
Separately in post #7 your fstab uses discard.

Discard is a continuous trim

Years ago that started to be not recommended for SSD. You set your own trim.
Now systems automatically do trim, periodically. 


And now I see never recommended for NVMe drives:
[https://wiki.archlinux.org/title/Solid_state_drive/NVMe](https://wiki.archlinux.org/title/Solid_state_drive/NVMe)

---

### Post by rsteinmetz70112 on 2022-01-04
It look to me like /dev/sdd has a partition table with a single partition /dev/sdd1 however I can't tell if there is a filesystem on it or not. To make a drive usable is a multi step process, first you must create a partition table, make a partition then place a file system on the partition before you can mount the drive and use it.

lsblk -f will show what filesystem (if any) is on the device

---

### Post by skrach33 on 2022-01-04
> **ajgreeny said:**
> After creating a partition table the disk will still show as unallocated; to be able to use the disk you need to immediately create one or more partitions or you will still be unable to do anything with the disk.

A partition table does not create partitions; that has to be done separately.

Tried it and it's not possible, tried creating a MS-DOS or gtp, then immediately tried to creat partitions and it doesn't give me the option.

Thanks

---

### Post by oldfred on 2022-01-04
How large is drive?
Screen shot looked like 2TB, but lsblk says 1TB, less overhead. Or is sdd changing depending on if flash drive plugged in?

What does this show.
sudo gdisk -l /dev/sdd

---

### Post by skrach33 on 2022-01-06
> **sudodus said:**
> When using gparted and you have a partition table, you can right-click on a graphic representation of the unallocated drive space and select New, and in a new window select file system (and if you wish a label that is easy to remember), click on the Add button and when it looks good finally click on the tick icon to perform the actions to create a partition with the selected file system. [I]See the attached screenshot.
[/I]
[This link]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS?action=AttachFile&do=view&target=GrowIt.pdf") is not exactly showing how to create a partition, but it shows several screenshots of how to use gparted.

Tried to do it, couldn't. It's like it never did write the partition table.

---

### Post by skrach33 on 2022-01-06
> **oldfred said:**
> Separately in post #7 your fstab uses discard.

Discard is a continuous trim

Years ago that started to be not recommended for SSD. You set your own trim.
Now systems automatically do trim, periodically. 


And now I see never recommended for NVMe drives:
[https://wiki.archlinux.org/title/Solid_state_drive/NVMe](https://wiki.archlinux.org/title/Solid_state_drive/NVMe)

Thanks for the information, never have heard of it, I will investigate. The thing is that it's not about the SSD, maybe it got confused because it changed the device name (don know why) from sdd to sda, but normally it is sda. Its a 2TB HDD.

The SDD is working fine, so if I have some more time I will dig in the information.

---

### Post by skrach33 on 2022-01-06
> **rsteinmetz70112 said:**
> It look to me like /dev/sdd has a partition table with a single partition /dev/sdd1 however I can't tell if there is a filesystem on it or not. To make a drive usable is a multi step process, first you must create a partition table, make a partition then place a file system on the partition before you can mount the drive and use it.

lsblk -f will show what filesystem (if any) is on the device

This is the result of lsblk -f
> [FONT=monospace][COLOR=#000000]
NAME   FSTYPE   LABEL          UUID                                 FSAVAIL FSUSE% MOUNTPOINT [/COLOR]
loop0  squashfs                                                           0   100% /snap/bare/5 
loop1  squashfs                                                           0   100% /snap/core20/1270 
loop2  squashfs                                                           0   100% /snap/gimp/380 
loop3  squashfs                                                           0   100% /snap/gimp/383 
loop4  squashfs                                                           0   100% /snap/gtk-common-themes/1519 
loop5  squashfs                                                           0   100% /snap/core18/2253 
loop6  squashfs                                                           0   100% /snap/gnome-3-28-1804/161 
loop7  squashfs                                                           0   100% /snap/gnome-3-38-2004/87 
loop8  squashfs                                                           0   100% /snap/libreoffice/239 
loop9  squashfs                                                           0   100% /snap/snapd/14295 
sda                                                                                 
sdb                                                                                 
|-sdb1 vfat     NO_LABEL       1552-4D88                             293.4M     2% /boot/efi 
|-sdb2 ext4     Swap           3512f0f4-199f-494b-986a-9fc20ac26af5                 
`-sdb3 ext4     Root           6c96748b-609e-4bae-a0d7-faac2c2abc59   79.4G    12% / 
sdc                                                                                 
`-sdc1 ext4     Home           8f1ac910-0ce7-42db-a611-2546fa938a20     25G    92% /home 
sdd                                                                                 
`-sdd1 ext4     DiscoExtraHome 78c7a091-6b59-4024-87f2-4818abd2f8ca  
[/FONT]

On sda no nothing

---

### Post by skrach33 on 2022-01-06
> **oldfred said:**
> How large is drive?
Screen shot looked like 2TB, but lsblk says 1TB, less overhead. Or is sdd changing depending on if flash drive plugged in?

What does this show.
sudo gdisk -l /dev/sdd

Yes it's 2TB, and yes it's changing.

---

### Post by skrach33 on 2022-01-06
> **oldfred said:**
> How large is drive?
Screen shot looked like 2TB, but lsblk says 1TB, less overhead. Or is sdd changing depending on if flash drive plugged in?

What does this show.
sudo gdisk -l /dev/sdd

gdisk shows:

> [FONT=monospace][COLOR=#000000]
GPT fdisk (gdisk) version 1.0.5 [/COLOR]

Partition table scan: 
  MBR: not present 
  BSD: not present 
  APM: not present 
  GPT: not present 

Creating new GPT entries in memory. 
Disk /dev/sda: 3907029168 sectors, 1.8 TiB 
Model: ST2000DM008-2FR1 
Sector size (logical/physical): 512/4096 bytes 
Disk identifier (GUID): 0C2646B4-8C55-416B-8706-D36822A3B5F8 
Partition table holds up to 128 entries 
Main partition table begins at sector 2 and ends at sector 33 
First usable sector is 34, last usable sector is 3907029134 
Partitions will be aligned on 2048-sector boundaries 
Total free space is 3907029101 sectors (1.8 TiB) 

Number  Start (sector)    End (sector)  Size       Code  Name

[/FONT]

---

### Post by sudodus on 2022-01-06
- How is the drive connected (via old style IDE, newer SATA, eSATA or via USB)?

- If an external drive,
. how is the power supplied? Is there enough power to make it run properly?
. if USB, could there be a compatibility problem with the adapter?

- Did you remember to click on the tick icon (in the gparted interface) to perform the modifications?

---

### Post by skrach33 on 2022-01-07
> **sudodus said:**
> - How is the drive connected (via old style IDE, newer SATA, eSATA or via USB)?

- If an external drive,
. how is the power supplied? Is there enough power to make it run properly?
. if USB, could there be a compatibility problem with the adapter?

- Did you remember to click on the tick icon (in the gparted interface) to perform the modifications?

Ok people, thanks for the attention and sorry for using your time.

When you wrote "click on the tick icon" I went again and opened gparted (with no hope, because of all the failed attempts), and yes there is an icon I didn't click. I don't know if its the "tick icon", but it allowed to do the partition. The mistake was that after writing the partition table I right clicked on the drive and it didn't allow me to make partitions, nor it allowed me in the "Partition" option, maybe because I didn't select the drive.

So I feel ashamed of my blindness and very very grateful of your attention and making me see again.

I hope this will be useful for an other blind

Thanks again

---

### Post by rsteinmetz70112 on 2022-01-08
Don't feel too bad. 
I'm sure everyone here has had similar experiences overlooking something that in retrospect seems blindingly obvious. 
I know I have and I do it several times a week.

---

