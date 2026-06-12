---
title: "About partitions &amp; What makes a partition &quot;bootable&quot;, or not?"
date: 2020-06-12
forum: General Help
---

### Post by kurja on 2020-06-12
When 20.04 came out I bought a new ssd and installed the OS on that without touching the partitioning settings during install, while I kept my old ssd with it's home/user folders in the machine and mounted that to new /home.

My old disk is now sda, with bootable partition sda1, extended partition sda2 and swap partition sda5.

New disk is sdc, with four partitions, 530MB W95 FAT32 sdc1 which is not auto-mounted at startup and apparently does nothing(?), and another 530MB W98 FAT32 partition sdc2 which is mounted at startup at /boot/efi. And Extended partition sdc3 and Linux partition sdc5 mounted at filesystem root.


[LIST]
[*]What is the purpose of FAT partition sdc1?
[*]I have not yet removed anything from sda. Can I safely remove all files and folders (except for the home folder)? What of sda2 and sda5?
[*]At boot, I am given the option to start the old OS from sda. How is the presence of a bootable partition detected, will this option disappear by removing old system files from sda1?
[/LIST]

Here's fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=3a8229ee-2f5c-400d-a073-cde036d2b049 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=BF4E-4407  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/disk/by-id/wwn-0x5000c500360b0f77-part1 /mnt/tiedostot auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0

/dev/disk/by-uuid/f43c34c0-730f-484c-be30-b2042c008858 /mnt/old_ssd auto nosuid,nodev,nofail,x-gvfs-show 0 0

#home folders from old_ssd
/mnt/old_ssd/home/pojat /home/user2 none bind 0 0
/mnt/old_ssd/home/k /home/user1 none bind 0 0

#no need for this (sdc1)?
/dev/disk/by-id/wwn-0x50026b76835b44ee-part1 /mnt/wwn-0x50026b76835b44ee-part1 auto nosuid,nodev,nofail,noauto 0 0

```

---

### Post by oldfred on 2020-06-12
Not sure why you have two FAT32 partitions.

But it looks like you have mixed UEFI and BIOS installs and used MBR where UEFI highly recommends and Windows only installs in UEFI mode to gpt partitioned drives. Ubuntu does let you install in UEFI mode to MBR partitioned drives, but should not. Drive must not have been blank or it would have used gpt for an UEFI install. It only installs in UEFI mode to MBR drives when drive is already MBR. 
So was it MBR with FAT32 partition(s) that installer resized or changed?

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by kurja on 2020-06-12
> **oldfred said:**
> Not sure why you have two FAT32 partitions.

But it looks like you have mixed UEFI and BIOS installs and used MBR where UEFI highly recommends and Windows only installs in UEFI mode to gpt partitioned drives. Ubuntu does let you install in UEFI mode to MBR partitioned drives, but should not. Drive must not have been blank or it would have used gpt for an UEFI install. It only installs in UEFI mode to MBR drives when drive is already MBR. 
So was it MBR with FAT32 partition(s) that installer resized or changed?

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Install on sda would likely be BIOS, as it was originally installed on older hardware which afaik did not have UEFI. Fstab says `# /boot/efi was on /dev/sda2 during installation` though...

I installed 20.04 on a brand new disk (sdc). However, I did do the install twice - I installed another de and ended up with a bit of a mess, and figured that it would be easiest to just reinstall. Perhaps this is the reason for two FAT partitions, but as for why there was one to begin with, if it's only for bios installs - I don't know, I didn't really even think of bios vs uefi at the time. I suppose it is possible that firmware has been set to 'legacy', which afaik may force bios install. But if that's the case, where did uefi install come from :? I should check firmware settings and update this post.

---

### Post by oldfred on 2020-06-12
The firmware setting is for an installed system.

How you boot install media, UEFI or BIOS/Legacy/CSM is then how it installs.
The ISO and most tools that create an installer from the ISO will allow boot in either mode & UEFI boot menu will show two entries to boot flash drive.
A few install tools have you select UEFI/gpt or BIOS/MBR when it creates installer, so it then only is in one mode or the other.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Lots more UEFI info in link in my signature.

I am to the point of only suggesting using MBR, if you want or have to have a BIOS install of Windows on same drive. Otherwise you might as well use gpt, but then need either an ESP - efi system partition or a bios_grub partition to support chosen boot mode of install. 

I have used gpt since 2010 when I converted first 160GB drive and installed Ubuntu to that. Then all new drives & even larger flash drives have become gpt.

---

### Post by kurja on 2020-06-12
I looked at firmware options for booting the usb stick I installed 20.04 from, and it offers bios or uefi - I must have chosen one when doing the install without paying too much attention, and ended up with bios. This would explain the fat partitions I ended up with, however everything is working at the moment so I'm going to leave that as-is. I'll need to remember to pay more attention to this the next time I do a new install.

As I'm now booting from sdc, and do not intend to boot the older version of ubuntu from sda in the future, can I safely remove all files therein but for the home folder, and remove sda2 and sda5 and extend sda1 to thus freed space? I am assuming yes, and that the lines `# / was on /dev/sda5 during installation`and `# /boot/efi was on /dev/sda2 during installation` are not relevant to this?

---

### Post by oldfred on 2020-06-12
The # comments are as the drive is seen during install. If only drive or first in SATA port order, it normally will be sda. But drives can change. My USB flash drives as sdc, become sda if I reboot and then every drive changes. Or if I unplug a drive and plug into a different SATA port it may change.
Or that is why Linux uses UUIDs to keep track of drives and partitions, not device like /dev/sdXY.

---

