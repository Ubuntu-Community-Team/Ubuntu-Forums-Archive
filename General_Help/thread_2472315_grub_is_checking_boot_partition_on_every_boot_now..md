---
title: "grub is checking boot partition on every boot now."
date: 2022-02-23
forum: General Help
---

### Post by makem2 on 2022-02-23
I have a dual boot windows and xubuntu which was working fine until I decided to give windows more space.

On boot grub now gives the message:

"Gave up waiting for suspend/resume device
/dev/nvme1n1p5: clean, 319446/2921984 files, 4990770/9277440 blocks"

Waits a while and then continues to the login screen.

In expanding windows, swap was moved from p5 to p8 and p5 became ubuntu boot /

I have tried running fsck from recovery mode but that finds p5 (boot) to be mounted so can do nothing.

I found that the UUID of swap had changed and corrected it in fstab so that is not the problem.

/etc/fstab:

```

  GNU nano 5.6.1                                          /etc/fstab                                                    
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# / was on /dev/nvme0n1p6 during installation - now on /dev/nvme0n1p5
UUID=a018cecd-ae3a-4e56-8e59-a457c8dd43ab /               ext4    errors=remount-ro 0       1

# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=40DB-4F92  /boot/efi       vfat    umask=0077      0       1

# /home was on /dev/nvme0n1p7 during installation - now on /dev/nvme0n1p6
UUID=e225fd55-cbcb-404b-ac66-27db01e75f91 /home           ext4    defaults        0       2

# swap was on /dev/nvme0n1p5 during installation - now on /dev/nvme0n1p8
# UUID=4fa68444-6c27-420c-9fb6-63ef49510a90 none            swap    sw              0       0
UUID=4ede3f10-e290-4fe4-970a-27537f3a0499 none  swap sw 0       0

# /media/data was on /dev/nvme0n1p6 during installation - now on /dev/nvme0n1p7
UUID=404338594EF4A720 /media/data ntfs-3g permissions   0       1

# terabyte was on /dev/nvme0n1p1 during installation
UUID=1c245acf-a7f1-40a5-9f3a-b5d34f03ee43 /media/terabyte       ext4    defaults        0       2

# ntfs_games on /dev/nvme0n1p2
UUID=6F84951F5D97E1A6   /media/ntfs_games ntfs-3g permissions   0       1

```

cat /proc/cmdline:

```

makem@makems-TUF:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-5.13.0-051300-generic root=UUID=a018cecd-ae3a-4e56-8e59-a457c8dd43ab ro quiet splash vt.handoff=7
makem@makems-TUF:~$

```

/etc/default/grub:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

blkid:

```

makem@makems-TUF:~$ sudo nano /etc/default/grub
[sudo] password for makem: 
makem@makems-TUF:~$ sudo blkid
[sudo] password for makem: 
/dev/nvme1n1p1: LABEL_FATBOOT="SYSTEM" LABEL="SYSTEM" UUID="40DB-4F92" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="3d16b11e-68f4-4c98-a752-9c7e0f57cf99"
/dev/nvme1n1p3: LABEL="Recovery" BLOCK_SIZE="512" UUID="F026DBCE26DB9446" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="96905358-d5bb-403f-873a-9fa0cf546bd9"
/dev/nvme1n1p4: LABEL="Windows" BLOCK_SIZE="512" UUID="CE6CDDE46CDDC77D" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="1011dac3-cce1-4c89-aea4-3b6b5c720e48"
/dev/nvme1n1p5: UUID="a018cecd-ae3a-4e56-8e59-a457c8dd43ab" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="e9ad0e95-fea0-4153-b25d-1f1db0021077"
/dev/nvme1n1p6: UUID="e225fd55-cbcb-404b-ac66-27db01e75f91" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="cdb5364f-150c-4d55-9876-74ef4d535d1b"
/dev/nvme1n1p7: LABEL="data" BLOCK_SIZE="512" UUID="404338594EF4A720" TYPE="ntfs" PARTLABEL="data" PARTUUID="9d5930f0-f0ea-41e3-9ade-951283d95706"
/dev/nvme1n1p8: UUID="4ede3f10-e290-4fe4-970a-27537f3a0499" TYPE="swap" PARTUUID="fc5545b0-02aa-4dfc-b180-8e0485d86893"
/dev/nvme0n1p1: UUID="1c245acf-a7f1-40a5-9f3a-b5d34f03ee43" BLOCK_SIZE="4096" TYPE="ext4" PARTLABEL="terabyteData" PARTUUID="9efc4100-a6dd-4c9a-badd-055d8ba03b2d"
/dev/nvme0n1p2: LABEL="ntfs_games" BLOCK_SIZE="512" UUID="6F84951F5D97E1A6" TYPE="ntfs" PARTLABEL="ntfs_games" PARTUUID="9ddf13a6-64c5-432d-a3ed-df93c094f758"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/nvme1n1p2: PARTLABEL="Microsoft reserved partition" PARTUUID="4cf00a5b-51d4-487e-84ee-477f3c1adb64"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
/dev/loop21: TYPE="squashfs"
makem@makems-TUF:~$

```

fdisk -l:

```

makem@makems-TUF:~$ sudo fdisk -l
Disk /dev/loop0: 104.97 MiB, 110071808 bytes, 214984 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 80.71 MiB, 84627456 bytes, 165288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 50.96 MiB, 53432320 bytes, 104360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 80.92 MiB, 84848640 bytes, 165720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 54.24 MiB, 56872960 bytes, 111080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 65.21 MiB, 68378624 bytes, 133552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 65.1 MiB, 68259840 bytes, 133320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme1n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: INTEL SSDPEKNW512G8                     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 176110A6-54C5-4712-B23C-642A1CA0CB04

Device             Start        End   Sectors   Size Type
/dev/nvme1n1p1      2048     534527    532480   260M EFI System
/dev/nvme1n1p2    534528     796671    262144   128M Microsoft reserved
/dev/nvme1n1p3    796672    1820671   1024000   500M Windows recovery environment
/dev/nvme1n1p4   1820672  383305727 381485056 181.9G Microsoft basic data
/dev/nvme1n1p5 391118848  465338367  74219520  35.4G Linux filesystem
/dev/nvme1n1p6 465338368  608917503 143579136  68.5G Linux filesystem
/dev/nvme1n1p7 608917504 1000214527 391297024 186.6G Microsoft basic data
/dev/nvme1n1p8 383305728  391118847   7813120   3.7G Linux swap

Partition table entries are not in disk order.


Disk /dev/nvme0n1: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: CT1000P5PSSD8                           
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 762FCE7F-0ADE-4302-A04D-E403F581DD7C

Device             Start        End    Sectors   Size Type
/dev/nvme0n1p1      2048  923379711  923377664 440.3G Linux filesystem
/dev/nvme0n1p2 923379712 1953523711 1030144000 491.2G Microsoft basic data


Disk /dev/loop8: 247.91 MiB, 259948544 bytes, 507712 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 80.08 MiB, 83968000 bytes, 164000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 219 MiB, 229638144 bytes, 448512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 61.89 MiB, 64897024 bytes, 126752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 82.9 MiB, 86925312 bytes, 169776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 55.51 MiB, 58204160 bytes, 113680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 164.76 MiB, 172761088 bytes, 337424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 82.89 MiB, 86917120 bytes, 169760 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 219 MiB, 229638144 bytes, 448512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 61.91 MiB, 64917504 bytes, 126792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 248.76 MiB, 260841472 bytes, 509456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 10.95 MiB, 11485184 bytes, 22432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop20: 43.59 MiB, 45703168 bytes, 89264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop21: 55.49 MiB, 58183680 bytes, 113640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
makem@makems-TUF:~$

```
Any pointers to a trusted guide would be appreciated.

---

### Post by yetimon_64 on 2022-02-23
> **makem2 said:**
> ..."Gave up waiting for suspend/resume device
/dev/nvme1n1p5: clean, 319446/2921984 files, 4990770/9277440 blocks"...

Since you have moved swap from "p5" to "p8" check the file /etc/initramfs-tools/conf.d/resume it will likely have the old UUID for the swap partition. You need to put the new UUID for the swap partition into this file and use the "update-initramfs" command. I have had this issue after changing partition layouts in the past.

---

### Post by makem2 on 2022-02-24
> **yetimon_64 said:**
> Since you have moved swap from "p5" to "p8" check the file /etc/initramfs-tools/conf.d/resume it will likely have the old UUID for the swap partition. You need to put the new UUID for the swap partition into this file and use the "update-initramfs" command. I have had this issue after changing partition layouts in the past.

Thank you.

Yes I thought that too but in 21.10 I don't have a /etc/initramfs-tools/conf.d/resume.

/etc/initramfs-tools/conf.d is empty.

```

makem@makems-TUF:~$ cd /etc/initramfs-tools/conf.d
makem@makems-TUF:/etc/initramfs-tools/conf.d$ ls -la
total 8
drwxr-xr-x 2 root root 4096 Feb 24 00:29 .
drwxr-xr-x 5 root root 4096 Feb 24 00:38 ..
makem@makems-TUF:/etc/initramfs-tools/conf.d$

```

I updated update-initramfs after amending the UUID of swap in fstab and this made the grub boot much quicker. However, it sill does the check.

```

makem@makems-TUF:/etc/initramfs-tools/conf.d$ swapon
NAME           TYPE      SIZE USED PRIO
/dev/nvme1n1p8 partition 3.7G   0B   -2
makem@makems-TUF:

```

This is the correct partition.

```

makem@makems-TUF:~$ grep swap.*sw /etc/fstab
UUID=4ede3f10-e290-4fe4-970a-27537f3a0499 none    swap sw    0    0
makem@makems-TUF:~$ sudo blkid | grep swap
[sudo] password for makem: 
/dev/nvme1n1p8: UUID="4ede3f10-e290-4fe4-970a-27537f3a0499" TYPE="swap" PARTUUID="fc5545b0-02aa-4dfc-b180-8e0485d86893"
makem@makems-TUF:~$

```

It is now not a real problem but obviously is is not correct and I wonder where 'resume' has gone or if it could/should be resurrected.

---

