---
title: "Dual Boot 16.04 i386 and 18.04 amd64"
date: 2020-03-01
forum: General Help
---

### Post by rsteinmetz70112 on 2020-03-01
I have a computer that had 16.04 LTS i386 on. I installed additional drives in it and installed 18.04 LTS amd64 on the new drives. 

The GRUB update recognizes the 18.04 installation and allows me to select either system and under the advanced options different kernels.

When I first did this I could select any of the options on either version and they would work.

After a while the 18.04 kernels would not longer boot and any of the advanced options causes a kernel panic. 

The following may not be exact;
```
Please append correct"root=" boot option
kernel panic not syncing VFS unable to mount root fs on unknown-block(0,0)

```
I can load any of the file systems and read them. I have fscked them and they appear healthy. 

This appears to be a grub problem but I can't figure out how to fix it.

I would be willing to reinstall the 18.04 side if that helps but I'd like to understand what went wrong to prevent it from happ0ening again.

---

### Post by CelticWarrior on 2020-03-01
This may have been triggered b y a kernel update in 16.04. It then took over Grub and may have incorrect settings for 18.04.

At the Grub menu you can try to select 18.04 and press 'e' to edit and check the information there.

---

### Post by rsteinmetz70112 on 2020-03-01
Thanks,

That may have happened but;

I've been able to chroot and install-grub into teh 18.04 side resulting in a different grub menu order and
install-grub on the 16.04 side and get the menu back without being able to boot into 18.04

I'm beginning to wonder if initramfs on the 18.04 side is messed up. 
I have been unable to rebuild initramfs in a chroot environment due to various error messages.
I haven't been able to apt update/upgrade 18.04 due to problems.

---

### Post by oldfred on 2020-03-01
Boot-Repair may default to first install it sees.
Best to use advanced options and install the grub from 18.04 to MBR if BIOS based system.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

In your 16.04 install you can use this to uncheck everything, so grub is not reinstalled on updates.
#to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short

---

### Post by rsteinmetz70112 on 2020-03-02
> **oldfred said:**
> Boot-Repair may default to first install it sees.
Best to use advanced options and install the grub from 18.04 to MBR if BIOS based system.
I've already reinstalled GRUB on both teh 16.04 and 18.04 systems and the only difference I see is the order the different options are listed in. 
> May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I think you lost me I'll check out the links nd see if I can figure it out.

> In your 16.04 install you can use this to uncheck everything, so grub is not reinstalled on updates.
#to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

```
# sudo dpkg-reconfigure grub-pc
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-109-generic
Found initrd image: /boot/initrd.img-4.4.0-109-generic
Found linux image: /boot/vmlinuz-4.4.0-104-generic
Found initrd image: /boot/initrd.img-4.4.0-104-generic
Found linux image: /boot/vmlinuz-4.4.0-103-generic
Found initrd image: /boot/initrd.img-4.4.0-103-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 18.04.2 LTS (18.04) on /dev/mapper/system-root
done
```

I typically install grub on all drives, just in case. 

> #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 

From 16.04 install:
/root  is on a a lvm2 volume.

```
# debconf-show grub-pc
  grub2/device_map_regenerated:
  grub-pc/hidden_timeout: false
  grub-pc/install_devices_disks_changed:
  grub-pc/install_devices_failed: false
  grub-pc/postrm_purge_boot_grub: false
* grub-pc/install_devices:
* grub-pc/install_devices_failed_upgrade: false
  grub-pc/kopt_extracted: true
  grub2/linux_cmfline_default: quiet splash
* grub-pc/chainload_from_menu.lst: true
  grub-pc/timeout: 5
* grub2/linux_cmdline:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub2/kfreebsd_cmdline:
  grub2/force_efi_extra_removable: false
* grub-pc/mixed_legacy_and_grub2: true
  grub-pc/disk_description:
  grub2/linux_cmdline_default:
  grub-pc/partition_description:
  grub2/update_nvram: true
* grub-pc/install_devices_empty: true
```

It will show drive model & serial number
> to see similar drive info
```
sudo lshw -C Disk -short

# lshw -C Disk -short
H/W path       Device      Class       Description
==================================================
/0/13/0.0.0    /dev/sda    disk        1TB TOSHIBA HDWD110
/0/14/0.0.0    /dev/cdrom  disk        SCSI CD-ROM
/0/15/0.0.0    /dev/cdrw   disk        DVD A  DH20A6L
/0/16/0.0.0    /dev/sdb    disk        1TB TOSHIBA HDWD110
/0/17/0.0.0    /dev/sdc    disk        1TB TOSHIBA HDWD110
/0/18/0.0.0    /dev/sdd    disk        1TB TOSHIBA HDWD110
```


Unfortunately this is production computer and I can't take it down to test GRUB any time I want.

---

### Post by oldfred on 2020-03-02
It did not show a drive for grub-pc to install into.
Are you using UEFI? As that would not use grub-pc nor have a drive to re-install into.

It looks like you used LVM for at least one of your installs. 
I do not really know LVM.

---

### Post by CelticWarrior on 2020-03-02
And if UEFI you can also boot 18.04 directly (its Grub) via UEFI settings > Boot menu or equivalent. If with that it boots fine in 18.04...

---

### Post by rsteinmetz70112 on 2020-03-03
> **oldfred said:**
> It did not show a drive for grub-pc to install into.
Are you using UEFI? As that would not use grub-pc nor have a drive to re-install into.

No this system was installed long before UEFI and upgraded for over a decade replacing various hardware and software. I believe it started as Ubuntu 6.04, but I forget. That's the reason it's still i386 for 16.04

I installed 18.04 amd64 with the intention of migrating/duplicating all of the settings in 18.04 but here I am.

grub-pc is on the root drive. The device is /dev/mapper/hamlet-root -> /dev/dm-0

From the 16.04 install;
```
#  apt install grub-pc
Reading package lists... Done
Building dependency tree
Reading state information... Done
grub-pc is already the newest version (2.02~beta2-36ubuntu3.23).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

> It looks like you used LVM for at least one of your installs. 
I do not really know LVM.

Both installs use mdadm and lvm2. Each install has it's own fstab.

```
# lsblk
NAME               MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                  8:0    0 931.5G  0 disk
&#9492;&#9472;sda1               8:1    0 931.5G  0 part
  &#9492;&#9472;md1              9:1    0 931.4G  0 raid1
    &#9500;&#9472;system-root  252:1    0   150G  0 lvm
    &#9500;&#9472;system-home  252:2    0 465.7G  0 lvm
    &#9492;&#9472;system-xtra  252:3    0 315.7G  0 lvm
sdb                  8:16   0 931.5G  0 disk
&#9492;&#9472;sdb1               8:17   0 931.5G  0 part
  &#9492;&#9472;md0              9:0    0 931.4G  0 raid1
    &#9500;&#9472;hamlet-root  252:0    0   140G  0 lvm   /
    &#9500;&#9472;hamlet-home  252:4    0 395.7G  0 lvm   /home
    &#9492;&#9472;hamlet-files 252:5    0 395.7G  0 lvm   /files
sdc                  8:32   0 931.5G  0 disk
&#9492;&#9472;sdc1               8:33   0 931.5G  0 part
  &#9492;&#9472;md0              9:0    0 931.4G  0 raid1
    &#9500;&#9472;hamlet-root  252:0    0   140G  0 lvm   /
    &#9500;&#9472;hamlet-home  252:4    0 395.7G  0 lvm   /home
    &#9492;&#9472;hamlet-files 252:5    0 395.7G  0 lvm   /files
sdd                  8:48   0 931.5G  0 disk
&#9492;&#9472;sdd1               8:49   0 931.5G  0 part
  &#9492;&#9472;md1              9:1    0 931.4G  0 raid1
    &#9500;&#9472;system-root  252:1    0   150G  0 lvm
    &#9500;&#9472;system-home  252:2    0 465.7G  0 lvm
    &#9492;&#9472;system-xtra  252:3    0 315.7G  0 lvm
```

---

