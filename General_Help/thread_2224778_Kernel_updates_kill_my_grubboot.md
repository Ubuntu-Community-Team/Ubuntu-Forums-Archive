---
title: "Kernel updates kill my grub/boot"
date: 2014-05-18
forum: General Help
---

### Post by paul68 on 2014-05-18
Hi,

I'm running an Ubuntu server install from 13.04. When 14.04 was released, I did an upgrade first to 13.10 and then to 14.04. Everything seemed to work flawlessly. However, I am noticing a very strange issue when the kernel is updated. When I reboot I get a grub error about LVM volume of ID not being found. I then have to boot from a live cd, chroot and reinstall the kernel package before also doing a grub reinstall (and reinstalling grub again to the MBR). After that, everything works again. I'm actually not sure if the kernel reinstall is required but thought it better to do anyhow.

What I don't understand is, shouldn't the post install triggers auto update grub? Why would grub die in the way it does when the LVM Id of the disk hasn't changed? Any ideas how I can debug further? It's very frustrating to have to do this every time a kernel is updated.

Thanks,

---

### Post by oldfred on 2014-05-18
I do not know LVM.
Is system UEFI or BIOS.
Do you have a separate /boot outside lvm or just the LVM. Default installs of LVM seem to use a separate /boot, but I do not know if that is standard or not.

May be best to see details. Post link to BootInfo report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It may be that grub cannot find the correct reinstall location? 
This is for standard installs and the grub location is the drive. Not sure with LVM whether install is to LVM or MBR?

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by paul68 on 2014-05-20
Hi,

In answer to your questions:

1. It's a Gigabyte Brix 1037u. Unsure if it is UEFI or standard boot and I can't check as I am away at the moment. Official specs don't specify.
2. Not using a separate /boot. /boot is in / . 

I couldn't install boot-repair on 14.04. Getting a 404 error when trying to receive repository details. Output of other commands are below:

> paul@brix:~$  sudo debconf-show grub-pc
  grub2/device_map_regenerated:
  grub-pc/chainload_from_menu.lst: true
  grub2/linux_cmdline_default: quiet splash
  grub-pc/disk_description:
  grub-pc/partition_description:
  grub-pc/install_devices_disks_changed:
  grub-pc/mixed_legacy_and_grub2: true
  grub2/kfreebsd_cmdline:
* grub-pc/install_devices: /dev/disk/by-id/ata-M4-CT032M4SSD3_00000000131803771B8E
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/install_devices_failed: false
  grub2/linux_cmdline:
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/install_devices_empty: false
  grub-pc/kopt_extracted: false
  grub-pc/hidden_timeout: false
  grub-pc/timeout: 10
paul@brix:~$  sudo grub-probe -t device /boot/grub
/dev/sda1
paul@brix:~$



So, from above, I can see:

it looks like install_devices is different from he output of the second command. 

Anything here that helps?

Thanks for replying!

---

### Post by oldfred on 2014-05-20
This just specifies the drive and is not showing a partition.
 grub-pc/install_devices: /dev/disk/by-id/ata-M4-CT032M4SSD3_00000000131803771B8E

This shows where:
/dev/sda1

But sda1 may only be correct if UEFI and efi partition is sda1 as you do not install grub to partition if BIOS/CSM.

---

### Post by paul68 on 2014-05-23
Thanks for the reply. When I reinstall grub manually, I do so to /dev/sda1 and that seems to fix it.

Should install_devices also be /dev/sda1 then?

---

### Post by oldfred on 2014-05-23
You can reset the grub install_devices entry with this:

 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

