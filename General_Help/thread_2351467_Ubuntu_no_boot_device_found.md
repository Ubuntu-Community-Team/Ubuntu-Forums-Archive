---
title: "Ubuntu: no boot device found"
date: 2017-02-03
forum: General Help
---

### Post by clay7 on 2017-02-03
Hello - I have Ubuntu 14 on an internal hard drive, and Windows 10 on another internal HD. Ubuntu is full-disk encrypted with LUKS. I switched the sata cable to the Windows 10 HD to run Windows, but when I switched the cable back to the Ubuntu HD, no boot device could be found. 

Here's what gparted is showing: [http://imgur.com/a/vCmZc](http://imgur.com/a/vCmZc)

Any ideas? Thank you,

---

### Post by oldfred on 2017-02-03
UEFI drives & UEFI do not like drives unplugged.
UEFI loses the boot info.
Is Windows UEFI boot or BIOS boot?

You can use efibootmgr to add back the entry.
You may want to also add the fallback or hard drive entry in /EFI/Boot/bootx64.efi. Many UEFI find that entry automatically as that is how all fash drives boot, but can be also used on internal drive.

Boot-Repair can also do a full re-install of grub which will also run the commands to add the entry.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
Boot-Repair should do this, if you check the 'use the standard efi file'
 Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186) 

entry without -d and -p parameters defaults to sda, so you may not need them.
      
 sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number.
[http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected](http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected)

---

### Post by clay7 on 2017-02-10
Thank you. The system is UEFI. The only drive plugged in now is the Ubuntu HD. I used Boot-Repair on a USB with the default options (I didn't see an option to use the standard efi file) and it said "boot successfully repaired." It also gave me this URL of the report: [http://paste.ubuntu.com/23971245/](http://paste.ubuntu.com/23971245/)  

However, when I rebooted with just the HD, I got the same error message about not being able to find a boot device. 

Which steps should I try now? Thanks again for your help.

---

### Post by oldfred on 2017-02-10
I think you have to boot Boot-Repair in UEFI boot mode to have UEFI fix options.

Better to use Ubuntu live installer of same version as you used to install and then add Boot-Repair.
Boot in UEFI mode not BIOS mode. Usually better to make sure UEFI secure boot is off.

What brand/model system?

Many now are like HP, Sony, Toshiba & others only UEFI boot "Windows Boot Manager". Using description as part of UEFI boot is a violation of the UEFI standard. 
But there are many work arounds.

Some if only booting Windows change the actual file used to boot with "Windows Boot Manager" description to actually boot Windows.
Some that want to dual boot use the fallback or hard drive entry which varies by system but UEFI: hard drive or something similar. That entry in UEFI must be /EFI/Boot/bootx64.efi which Boot-Repair will update if in UEFI mode.

Re-run report with UEFI boot.

---

### Post by clay7 on 2017-02-11
Ok - I used an Ubuntu 14.04.3 live USB to boot (same version is on the affected HD), and when that was up, I added the boot-repair repository, installed boot-repair, and ran it. But, when everything was done and I rebooted, a boot device could not be found. The report is [http://paste.ubuntu.com/23976518](http://paste.ubuntu.com/23976518)  

The BIOS version is "AMI UEFIx64 2.3". It's on a Biostar MB on a computer I put together myself. 

I have not tried this yet:
> sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number.

Given my paste report and that the affected HD is sda, which partition should I use for the "Y" parameter above?

---

### Post by oldfred on 2017-02-11
14.04.3 is obsolete. You need to update to 14.04.5.
 [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr) 

Your ESP  is sda1, so you can leave off the -d & -p parameters as it defaults to sda1.

---

### Post by clay7 on 2017-02-11
Thank you. I put 14.04.5 on the USB, booted to the live USB, installed boot-repair, and ran:
> sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu

then rebooted and I got:
> Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key

Any ideas?

On a side note, I'm curious as to how using a separate HD with Win10 on it and then going back to the other HD with Ubuntu caused this problem. At no time was more than one HD plugged in to the MB or PSU so I wonder how the Ubuntu drive just suddenly lost its boot capability. Would reseting the MB help?

Anyway, thanks again for your help.

---

### Post by oldfred on 2017-02-11
UEFI uses NVRAM to store UEFI boot menu entries.
But when you unplug a drive it loses those entries. Many UEFI vendors configure system to auto find the Windows entry and may update UEFI to have it. But they do not necessarily look for other entries in UEFI which they should.

So if you  are regularly unplugging & replugging drives you need to have live installer handy and know the efibootmgr commands required to readd entries.
Many systems do find the fallback or hard drive entry. That is /EFI/Boot/bootx64.efi. That often on a hard drive is just a copy of the Windows .efi boot file. We can make that a copy of shim, so then your default hard drive entry will boot Ubuntu. But not all systems keep hard drive boot entry.

In Boot-Repair's Advanced mode, check the "use the standard efi file" which is /EFI/Boot/bootx64.efi. It copies shim to be that file.
Then see if UEFI knows to boot hard drive.
sudo efibootmgr -v

I added my own entry, not sure if I unplug drive if it would still find it or not.
```
Boot0002* UEFI OS    HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xfa000)/File(\EFI\BOOT\BOOTX64.EFI)..BO

```

If only booting Ubuntu you can also add a Windows entry which really boots shim/ubuntu. UEFI checks description not actual file booted. And vendors check to see if description is "Windows boot Manager"

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1. 
     sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

But UEFI internally uses the gpt GUID to know which partition is the ESP. so a Windows entry to boot your Ubuntu using shim may corrupt booting of Windows as its GUID for ESP is different when you plug in another drive with different gpt(GUIDs).

---

### Post by clay7 on 2017-02-11
I tried it manually. Here's my command history and the output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   625142447   312571223+  ee  GPT

Disk /dev/sdb: 8103 MB, 8103395328 bytes
47 heads, 21 sectors/track, 16035 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11d56fa6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15826943     7912448    b  W95 FAT32
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0D31-09DB" TYPE="vfat" 
/dev/sda2: UUID="85975a6f-bdf6-4615-9afc-a780a39ac5b1" TYPE="ext2" 
/dev/sda3: UUID="54b8a1ad-f9bf-45dd-ae8e-dd3d05db134c" TYPE="crypto_LUKS" 
/dev/sdb1: UUID="3B7B-E085" TYPE="vfat" 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
```

Does the "WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted." explain why the above tries haven't worked? If so, what should I do?

---

### Post by oldfred on 2017-02-11
You are using the older version of Ubuntu that has an old version of fdisk that does not support gpt.
Back then we used gdisk which was for gpt drives. You can also use parted or gparted. Fdisk is just saying it cannot show the gpt partitions.

But your tried to install the BIOS boot version of grub or grub-pc. With a gpt partitioned drive you must have a 1 or 2MB unformatted partition with the bios_grub flag (if gparted) or code ef02 if using gdisk. 
Or if using UEFI boot version of grub, grub-efi-amd64, you must have an ESP - efi system partition which is FAT32 formatted with boot flag, usually 300 to 500MB, but you can get by with smaller like 100MB as that is what Windows default is. But grub in UEFI mode only installs to the ESP on the drive seen as sda. 
Or drive in SATA0 port. Best to keep drives in port order and start at SATA0. If you skip ports it can lead to issues.

       [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

