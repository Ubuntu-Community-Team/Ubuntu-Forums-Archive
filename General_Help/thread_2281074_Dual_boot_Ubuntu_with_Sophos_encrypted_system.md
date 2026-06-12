---
title: "Dual boot Ubuntu with Sophos encrypted system"
date: 2015-06-04
forum: General Help
---

### Post by m.s.krijgsman on 2015-06-04
Hi All,

I'm using a laptop from my work.
Internal disk is devided into 2 partitions both encrypted with Sophos full disk encryption.
Next to this I have ssd drive in a tray, running ubuntu.
This normally works quite well.
However once in a while grub overwrites /dev/sda instead of sdb
When this happens I have to re-install my complete laptop (windows side) because our helpdesk can't restore the sophos bootloader.

Is there any way I can backup this bootloader, so I can restore this when grub overwrites this ?

Thank you in advanced.

---

### Post by oldfred on 2015-06-04
You do have permission from work to do this?

If BIOS with MBR the boot loader is inside the MBR which has both boot code and partition table.
       Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master](https://help.ubuntu.com/community/WindowsDualBoot#Master) Boot Record backup and re-replacement
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1

But better to fix grub. Grub normally defaults its install to sda.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by m.s.krijgsman on 2015-06-05
Not sure wether I'm allowed to do this or not.
As long as I don't loose too much time over reinstalling windows ;)

I'm allowed to use my laptop for personal use.

Also I've adjust the configuration.
Thank you for you guidance.
Grub was indeed pointing to 2 devices.
So fixed this to only point to the correct device.

---

