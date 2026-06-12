---
title: "Cannot see attached hard-drive"
date: 2013-05-04
forum: General Help
---

### Post by horhif on 2013-05-04
Hi

I'm running Ubuntu from a USB drive.

I've also got an attached hard-drive (attached via a USB cable) however, i cannot see it.   when i run "lsusb" from the terminal i see this:  

```


lsusb
Bus 001 Device 002: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 001 Device 005: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 003 Device 002: ID 050d:0846 Belkin Components 
Bus 003 Device 003: ID 06a2:0033 Topro Technology, Inc. USB Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

how  do i go about accessing the Hi-Speed USB to SATA & PATA Combo Bridge?   as i believe that is the hard-drive.

thanks for any advice and help

---

### Post by 2F4U on 2013-05-04
What happens when you disconnect and reconnect the drive? Do you get any error messages in the system log file? What filesystem is on the drive? Did you try a different USB port? Does this drive use a seperate power connection and is it attached? Some hdd's require more power than a USB port can provide.

---

### Post by horhif on 2013-05-04
> **2F4U said:**
> What happens when you disconnect and reconnect the drive? Do you get any error messages in the system log file? What filesystem is on the drive? Did you try a different USB port? Does this drive use a seperate power connection and is it attached? Some hdd's require more power than a USB port can provide.

its a laptop harddrive that works ok when i plug it in to another pc.

there is ms xp on the hard drive.

changing usb ports doesnt do anything either.

thanks for ur help

---

### Post by RenegadeTigger on 2013-05-04
does the HDD show up if you use "sudo fdisk -l" if so it could be a mounting issue, witch you should be able to fix with fstab using "sudo neon /ect/fstab" or "sudo gedit /ect/fstab" its a little complicated to use there are a few guides for it. or theres "sudo gparted" if you dont have it you can use "sudo apt-get install gparted" 
i had the same problem this is how it was solved for me.

---

### Post by horhif on 2013-05-07
this is what i get when i run that command.  i believe it only shows the hard-drive and my attached usb drive. 

> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00210021

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   100663289    50331613+   7  HPFS/NTFS/exFAT
/dev/sda2       125837145   312576704    93369780    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4026 MB, 4026531840 bytes
220 heads, 32 sectors/track, 1117 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     7864318     3932143+   c  W95 FAT32 (LBA)


---

