---
title: "GRUB......Problems after Forsight install"
date: 2008-05-07
forum: General Help
---

### Post by jeffsa12 on 2008-05-07
I installed Forsight Linux onto two existing partitions on my 1st hd. I installed it **without** a boot loader, because it wouldn't let me install grub on it's root partition.

Now I can't boot any of my Linux Os's without using Super Grub disk to boot the partition directly.  I have had problems in the past overwriting grub stage 1 in the MBR boot loader section, and have always been able to fix things, with my super grub disk, or by just restoring grub via the following commands. 

      [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,6) 
 (hd0,8) .... this should read hd0,8 inside ( )

grub> root (hd0,6)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0)"...  19 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+19 p (hd0,6)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> 

Nothing is working for a fix this time. I did notice that Forsight, which is a RedHat derivative, had a different boot loader available along with grub. Even though I definitely chose to NOT install a boot loader, the installer created 2 small partitions on unallocated space on my 2nd hd. One was called /boot, the other, I dont recall but it was some strange file format, not reiserfs, ext2 or3. I just deleted them both after the boot problems

I disconnect my other 2 hd's trying to get my Ubuntu 8.04 booting again. Im' at a loss!!! 

Ubuntu 8.04 root is on hda7, and I want to use it's grub to boot all the Linux distros.

Below is my current fdisk-l results with just the first hd connected.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5436    43664635+   7  HPFS/NTFS
/dev/sda3            5437       19457   112623682+   f  W95 Ext'd (LBA)
/dev/sda5            5437        7646    17751793+   b  W95 FAT32
/dev/sda6            7647        7910     2120548+  82  Linux swap / Solaris
/dev/sda7            7911        8837     7446096   83  Linux
/dev/sda8            8838       11068    17920476   83  Linux
/dev/sda9   *       11069       11995     7446096   83  Linux
/dev/sda10          11996       12922     7446096   83  Linux
/dev/sda11          12923       19457    52492356    b  W95 FAT32
jeff@jeff-ubu804-desktop:~$ 

I keep my 3 windows installs on my 3rd hd. I select it to boot first in bios options during reboot when I want to boot into windows Vista, XP mce, or XP pro so that Vista,s boot loader handles Windows booting completely separate from grub. I disabled and no longer use the Win OS on the NTFS partition on 1st hd. The fat32 partitions are for storage/sharing between OS's. I create a separate root and home partition for each Linux OS

---

### Post by jeffsa12 on 2008-05-08
Ok...

I got things working again. It seems the IPL of my first HD MBR is not functioning for some reason yet to be determined. 

I just installed grub (the part that's in the MBR's IPL) to my second HD with the command:

grub> setup (hd1)

Tried to boot.....not!! Got into grub command line and:

grub> find /boot/grub/stage1

The output was:

(hd0,6)
(hd1,6)
(hd1,8)

This is when I figured out that grub (the part that's in the MRB's IPL) thought it was in the first HD rather than the second and was calling the first hd1, which is second!!!

I just changed the grub HD paths in my /boot/grub menu.lst file in Ubuntu 8.04, first HD to reflect the error as follows:

(hd1.6) changed to (hd0,6) 
(hd0,6) changed to (hd1,6) 
(hd0,8) changed to (hd1,8) 

So this got everything booting again. 

Now I have to get up to speed on grub device map to fix this right....

FYI:   Forseight linux uses no UUID numbers in the fstab file....interesting. Foresight's family tree started at RedHat.

When I type hd1,8 as (hd1,x) where x=8 the (hd1,8) shows up on the post.

---

