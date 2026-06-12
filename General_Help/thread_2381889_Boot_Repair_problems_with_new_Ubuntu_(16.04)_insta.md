---
title: "Boot Repair problems with new Ubuntu (16.04) install"
date: 2018-01-06
forum: General Help
---

### Post by hundred1906 on 2018-01-06
The essence of my problem is getting a new Ubuntu install to dual boot with a legacy Windows 10.

The specific issue right now is that Boot-Repair is returning the following message:

> GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.

Ubuntu is a pretty fresh 16.04 64 bit install onto /dev/sda, using a guided install. The format is GPT.

So how come I am getting the above message and what should I do now as the instruction is not entirely clear to me, particularly the second part? And why do I need this when my system has clearly booted up to this point?

I am obviously in above my head.

The reason I am running Boot-Repair at all is that Grub refused to recognize the Windows install (pre-existing separate MBR drive which was disconnected during the Ubuntu install) and running Boot-Repair is often quoted as a solution.

---

### Post by oldfred on 2018-01-06
You must have had a Windows install in UEFI mode that uses gpt?
But reinstalled Windows in BIOS mode that uses MBR(msdos)?

Windows does not correctly convert a drive from gpt to MBR as it leaves the backup gpt partition table at end of drive. MBR has no backup partition table.
So Linux tools see both MBR and backup gpt and do not know what to do. 

Windows only boots in UEFI mode from gpt, and only in BIOS mode from UEFI.
Generally best to have Ubuntu in same boot mode as Windows, but with newer hardware also better to use the newer UEFI/gpt configuration. BIOS/MBR goes all the way back to the original PC 35 years ago and had repeatedly been patched, while then well known, its still old.

If you want BIOS boot from gpt drive you need a 1 or 2MB unformatted partition with the bios_grub flag (if parted or gparted) or code ef02 if using gdisk.
Then reinstall grub.

I add both the ESP - efi system partition and bios_grub partition to all new drives. Then if later I want to change boot mode, I just need to reinstall grub, not totally back up & repartition drive to add a partition. UEFI suggests ESP be first, but many systems have it as second or third partition but still near beginning of drive.

       Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[URL="http://www.rodsbooks.com/gdisk/advice.html"]http://www.rodsbooks.com/gdisk/advice.html
[https://askubuntu.com/questions/500359/efi-boot-partition-and-biosgrub-partition](https://askubuntu.com/questions/500359/efi-boot-partition-and-biosgrub-partition)
[/URL]

---

### Post by hundred1906 on 2018-01-06
Hmm. The windows drive is MBR and boots OK on it's own, at least it did yesterday. As far as I know it is a Windows 7 original with Windows 10 updated onto it. I don't know how it would have transited from GPT to MBR and do not see any evidence for that on the drive.

The addition is a GPT SSD drive with a fresh Ubuntu 16.04 install. It's first partition is mounted at /boot/efi . I thought the issue lies with Grub (or whatever) on that drive. I was expecting that OS-Prober would find the Windows install and create a Grub menu item for it.

So maybe I have two problems (1) the boot config on the SSD is corrupted even though the install is just two days old. (2) OS-Prober is somehow failing to register the Windows drive and set up.

My usual system in use is Ubuntu. I havn't used Windows much for years.

---

### Post by oldfred on 2018-01-06
If you have an ESP, then you probably installed Ubuntu in UEFI boot mode.
But then booted live installer in BIOS boot mode and added Boot-Repair. It then would want to install the BIOS version of grub which on a gpt drive needs the bios_grub partition.

If Windows is BIOS boot, best for now to have Ubuntu in BIOS boot mode. So shrink any partition by 2MB and add an unformatted bios_grub partition and use Boot-Repair (Booted in BIOS mode) to totally reinstall grub.

Eventually you may want UEFI, so leave ESP gpt on the Ubuntu drive. It is not really that large to use much of drive space.

---

### Post by hundred1906 on 2018-01-06
Thank you oldfred. What I have right now is the following:
> 
sudo fdisk -l 
Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 5B8F0A4E-2065-430B-B471-3478A4A8C439

Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 222169087 221118464 105.4G Linux filesystem
/dev/sda3  222169088 234440703  12271616   5.9G Linux swap


Disk /dev/sdb: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: FBE80B9A-D592-4C55-BFCE-3AD217872D3B

Device     Start       End   Sectors   Size Type
/dev/sdb1   2048 500117503 500115456 238.5G Linux filesystem


Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x041e6c01

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdc1            2048  31459327  31457280    15G 27 Hidden NTFS WinRE
/dev/sdc2  *     31459328  31664127    204800   100M  7 HPFS/NTFS/exFAT
/dev/sdc3        31664128 504215551 472551424 225.3G  7 HPFS/NTFS/exFAT
/dev/sdc4       504215552 976771071 472555520 225.3G  7 HPFS/NTFS/exFAT

/dev/sdb is a data only drive used for storing images and I think can be safely ignored.

What you are saying I think is that sda1 needs to be moved up and a new partition created at the start of the disk. Not sure exactly how I define the new partition ... Then change my bios settings to come up in BIOS mode?

---

### Post by oldfred on 2018-01-06
Just shrink sda1 by 1 or 2 MB and then in that space add the unformatted partition with bios_grub flag.

---

### Post by hundred1906 on 2018-01-07
oldfred thank you for the advice - unfortunately it did not solve the problem as the resultant system would not boot. When I ran GParted it reported a mismatch between the actual drive sector size and what Ubuntu thought it was. This was my start again moment - too much was going wrong - and I rebuilt from scratch as the simplest option

I don't know where it went wrong previously but recall that I started by using a USB but that kept failing to complete the install (common problem apparently), so I then switched to a DVD for the build. Somewhere in that sequence maybe the resultant build screwed up.

After todays straight out of the box rebuild I ran > sudo update-grub
This found my Windows 10 drive and when I restarted the system the Grub menu came up with Windows as a start option - all good.:)

Next boot however the Grub menu does not show and the system goes straight into Ubuntu. Oh well.

---

### Post by oldfred on 2018-01-07
May be best to see new details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Usually the sector size issue is with the flash drive you have as the installer, and that can be ignored.

---

