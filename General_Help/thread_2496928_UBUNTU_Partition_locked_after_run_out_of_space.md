---
title: "UBUNTU Partition locked after run out of space"
date: 2024-04-17
forum: General Help
---

### Post by gui09 on 2024-04-17
Hi,

I am using ubuntu 20.22 installed on SSD driver with 250 GB.

Last month my driver run out of space, and later on the partition was locked.

I tried to use a usb-driver to reinstall ubuntu, but it does not identify the locked partition.

All I get is this busybox screen:

[HTML]Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=xxx does not exist. Dropping to a shell!

BusyBox v1.30 (Ubuntu x) built-in shell (ash)xx
Enter 'help' for a list of built-in commands.

(initramfs)_



[/HTML]


I've tried to follow some steps proposed by other forums like this one:


[LIST=1]
[*]Enter reboot in the prompt
[*]Goto BIOS setup
[*]Goto SATA Configuration
[*]Change to AHCI
[*]save and restart.
[/LIST]
[FONT=inherit]
But my F12 screen does not allow to change SATA configuration (frozen option)[/FONT]

---

### Post by ActionParsnip on 2024-04-17
Boot to Ubuntu liveCD and you can delete casual user data if /home is on the same filesystem as the rootfs. Alternatively you can chroot to the installed OS and run commands to clean up the file system etc as if the system on the internal disk was booted.

---

### Post by gui09 on 2024-04-17
I tried to use a usb-driver to reinstall ubuntu (Try ubuntu without installing option), but it does not identify the locked partition. Using gparted, I does not locate the main partition that is locked:


    root@ubuntu:~# fdisk -l
    Disk /dev/loop0: 2.2 GiB, 2409508864 bytes, 4706072 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    
    
    Disk /dev/loop1: 32.3 MiB, 33869824 bytes, 66152 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    
    
    Disk /dev/loop2: 55.4 MiB, 58130432 bytes, 113536 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    
    
    Disk /dev/loop3: 61.8 MiB, 64770048 bytes, 126504 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    
    
    Disk /dev/loop4: 65.1 MiB, 68259840 bytes, 133320 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    
    
    Disk /dev/loop5: 219 MiB, 229638144 bytes, 448512 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    
    
    Disk /dev/loop6: 241.4 MiB, 253087744 bytes, 494312 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    
    
    Disk /dev/loop7: 2.5 MiB, 2605056 bytes, 5088 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    
    
    Disk /dev/sda: 3.8 GiB, 4037017600 bytes, 7884800 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disklabel type: dos
    Disk identifier: 0x4c050c47
    
    Device     Boot   Start     End Sectors  Size Id Type
    /dev/sda1  *          0 4910399 4910400  2.3G  0 Empty
    /dev/sda2       4840192 4844991    4800  2.4M ef EFI (FAT-12/16/32)
    
    
    Disk /dev/loop8: 704 KiB, 720896 bytes, 1408 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes






All I get is this busybox screen:




    Gave up waiting for root device. Common problems:
    -Boot args (cat /proc/cmdline)
      -Check rootdelay= (did the system wait long enough?)
    -Missing modules (cat /proc/modules; ls /dev)
    ALERT! UUID=xxx does not exist. Dropping to a shell!
    
    BusyBox v1.30 (Ubuntu x) built-in shell (ash)xx
    Enter 'help' for a list of built-in commands.
    
    (initramfs)_




Using:
(initramfs) cat /proc/modules


I get the attached image output:
[IMG]https://i.stack.imgur.com/RZOkw.jpg[/IMG]

---

### Post by Rubi1200 on 2024-04-17
Where was Ubuntu installed? On sda1?

Have you tried fsck from the liveUSB?

---

### Post by gui09 on 2024-04-17
You mean these steps ?



[LIST]
[*]boot to a Ubuntu Live DVD/USB
[*]open a terminal window by pressing Ctrl+Alt+T
[*]type sudo fdisk -l
[*]identify the /dev/sdXX device name for your "Linux Filesystem"
[*]type sudo fsck -f /dev/sdXX, replacing sdXX with the number you found earlier
[*]repeat the fsck command if there were errors
[*]type reboot
[/LIST]

Is there a easy way to check where ubuntu is installed from the busybox ?

---

### Post by oldfred on 2024-04-17
Please use Code tags for all terminal or text output. Easy to add with Forum's Go Advanced editor and # icon.
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]

And please do not post screen shots in line, Use paper clip icon in Go Advanced Editor.
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

Does your UEFI/BIOS show another drive? You are only showing loop (snap) devices & flash drive.

To see details without snaps confusing them.
[FONT=monospace][COLOR=#000000]lsblk -e 7 -f[/COLOR]


[/FONT]

---

