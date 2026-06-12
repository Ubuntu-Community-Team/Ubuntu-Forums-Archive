---
title: "No Dual Boot screen"
date: 2014-10-13
forum: General Help
---

### Post by mn_voyageur on 2014-10-13
Let me preface this post by saying that I typically wipe the HDD and install Ubuntu.

Today, I was asked to install Ubuntu, but leave Windows 7 on the machine.

However, once complete, I am not seeing the start-up screen that allows you to chose which OS.  The system boots straight to Windows 7.

Any suggestions?

Thanks,
MarkN

---

### Post by Dennis N on 2014-10-13
How is Windows installed, in UEFI mode or BIOS mode? The install mode for Ubuntu has to be the same as Windows 7 install mode --- Grub2 on a BIOS system cannot see an OS installed in UEFI mode.  This is one possibility.

---

### Post by nerdtron on 2014-10-13
> Today, I was asked to install Ubuntu, but leave Windows 7 on the machine.

How did you install Ubuntu? What option did you choose on the installation screen?

---

### Post by jamesisin on 2014-10-13
If you are logged into Ubuntu, you would run sudo update-grub.  If (as Dennis N mentioned above) they are using the same boot system, this should add Win7 to the Grub menu.  You may, however, need to use something like boot-repair (which I keep installed on dual-boot systems because it's useful).

---

### Post by mn_voyageur on 2014-10-13
I do not know how Windows was installed.  I assume that it came with the computer.

I am not familiar with UEFI mode.

I can access the BIOS.  

I installed Uuntu from a Live USB.

What additional information do you need?

Thanks,
MarkN

---

### Post by mn_voyageur on 2014-10-13
Aparently, the Linux partition is not flagged for booting.

Using a "live CD" (actually a USB) I am able to see the files on the partition that I loaded Ubuntu.  

When I run fdisk -l, the following is returned:

/dev/sdb5       392359936   593014783   100327424   83  Linux
/dev/sdb6       593016832   599164927     3074048   82  Linux swap / Solaris

---

### Post by nerdtron on 2014-10-13
> I installed Uuntu from a Live USB.

What additional information do you need? 

I'm asking how did you install Ubuntu and not windows 7.

What option did you choose on the installation type of Ubuntu?

And post the COMPLETE output of
```
 sudo fdisk -l
sudo parted -l

```

---

### Post by oldfred on 2014-10-13
Grub does not use boot flag.

Windows has to have boot flag on the NTFS primary partition that has its boot files. A few BIOS require a boot flag on a primary partition just to let system boot, so we still suggestion one on a primary partition, even if no Windows. 

But you do have to install grub to the MBR like sda of a BIOS/MBR system for BIOS to find boot loader. You do not install grub to a partition like sda5. And never to a NTFS partition.

---

### Post by mn_voyageur on 2014-10-14
I installed Ubuntu from a USB drive.  (I am running the Live CD at this time.)

 sudo fdisk -l

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0393754d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sdb2          409600   392357989   195974195    7  HPFS/NTFS/exFAT
/dev/sdb3       599164928   625139711    12987392    7  HPFS/NTFS/exFAT
/dev/sdb4       392359934   599164927   103402497    5  Extended
/dev/sdb5       392359936   593014783   100327424   83  Linux
/dev/sdb6       593016832   599164927     3074048   82  Linux swap / Solaris

Partition table entries are not in disk order

sudo parted -l

Model: ATA TOSHIBA MK3263GS (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  210MB  209MB   primary   ntfs         boot
 2      210MB   201GB  201GB   primary   ntfs
 4      201GB   307GB  106GB   extended
 5      201GB   304GB  103GB   logical   ext4
 6      304GB   307GB  3148MB  logical
 3      307GB   320GB  13.3GB  primary   ntfs

One of the early Ubuntu installation screens asks, if you want to install Ubuntu inaddition to Windows.  It also indicates that the hdd will have to be partioned.

MarkN

---

### Post by yancek on 2014-10-14
Your windows and Ubuntu Linux partitions are all showing so if you are only seeing windows on boot, you did not install the Ubuntu Grub2 to the master boot record.  The link below explains several methods you can use to do this:

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by stalkingwolf on 2014-10-14
my experience is  its a problem with the default resolution.  try this, run the grub boot repair disk. 
 the first screen asks if you want to update grub pic a choice yes or no.
the next is repair the boot.  select advanced options.
select grub options
check select uncomment Grub_GFX Mode.
when its done reboot and you should have the grub menu.

---

