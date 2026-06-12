---
title: "Partioning after 12.04LTS is installed"
date: 2012-12-17
forum: General Help
---

### Post by flyfishingphil on 2012-12-17
I know it's in here somewhere but  can't figure the right terms to use to find it so here are my questions:

1. Is there a real simple way, with instructions written for a simple mind, on how to partition after 12.04LTS is installed. (Don't want to have to start over at initial install and do it all over again. Pretty much have everything set up as I want it after doing re-install to correct multiple problems. Found there are some things I want to do that require Win & IE.)

2. Is there a "trick" I need to know to install Win7 in the second drive?

3. I have gparted but when I click on "unmount", per directions, it says it can't do it and I must unmount manually. Where is the information on unmounting manually, if that is my only choice?

Instruction for a Dummy would be a good way to do this.

Thanks for any assists.

ffp

---

### Post by ajgreeny on 2012-12-17
> **flyfishingphil said:**
> I know it's in here somewhere but  can't figure the right terms to use to find it so here are my questions:

1. Is there a real simple way, with instructions written for a simple mind, on how to partition after 12.04LTS is installed. (Don't want to have to start over at initial install and do it all over again. Pretty much have everything set up as I want it after doing re-install to correct multiple problems. Found there are some things I want to do that require Win & IE.)

2. Is there a "trick" I need to know to install Win7 in the second drive?

3. I have gparted but when I click on "unmount", per directions, it says it can't do it and I must unmount manually. Where is the information on unmounting manually, if that is my only choice?

Instruction for a Dummy would be a good way to do this.

Thanks for any assists.

ffp

[LIST=1]
[*] Installing windows will overwrite grub with the windows bootloader, meaning you will not be able to boot to ubuntu until you have reinstalled grub, easily done with a live CD or USB. See section 13 of [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[*]Is it really a second drive or a separate partition on your single disk?
[*]Is gparted installed to your ubuntu install? If so you will need to forget using that and use the gparted which is already on the live CD because you can't unmount a partition that is in use as you running OS.
[/LIST]
More details please of exactly what disks you have, and their partitions at the moment. Show the output of ```
sudo fdisk -lu
``` and in case you have GPT or UEFI partitions ```
sudo parted -l
``` as well.

---

### Post by flyfishingphil on 2012-12-17
> **ajgreeny said:**
> [LIST=1]
[*] Installing windows will overwrite grub with the windows bootloader, meaning you will not be able to boot to ubuntu until you have reinstalled grub, easily done with a live CD or USB. See section 13 of [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[*]Is it really a second drive or a separate partition on your single disk?
[*]Is gparted installed to your ubuntu install? If so you will need to forget using that and use the gparted which is already on the live CD because you can't unmount a partition that is in use as you running OS.
[/LIST]
More details please of exactly what disks you have, and their partitions at the moment. Show the output of ```
sudo fdisk -lu
``` and in case you have GPT or UEFI partitions ```
sudo parted -l
``` as well.

I HDD in Toshiba laptop. U 12.04 already installed.

For sudo fdisk -lu:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c73c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   482377727   241187840   83  Linux
/dev/sda2       482379774   488396799     3008513    5  Extended
/dev/sda5       482379776   488396799     3008512   82  Linux swap / Solaris

For sudo parted -l

Model: ATA Hitachi HTS54322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  247GB  247GB   primary   ext4            boot
 2      247GB   250GB  3081MB  extended
 5      247GB   250GB  3081MB  logical   linux-swap(v1)

Anything else?

EDIT:  Just went to your grub ref and was redirected to another site saying that one was no longer available. What am I looking for there? Have recent download of 12.04LTS on DVD and istalled from that.

---

