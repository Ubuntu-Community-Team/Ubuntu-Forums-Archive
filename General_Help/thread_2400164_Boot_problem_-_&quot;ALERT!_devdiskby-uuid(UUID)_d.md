---
title: "Boot problem - &quot;ALERT! /dev/disk/by-uuid/(UUID) does not exist&quot;, (initramfs)"
date: 2018-09-03
forum: General Help
---

### Post by mari-e on 2018-09-03
I had a no boot device black screen after switching my dell laptop back on after several weeks. Following dell support instructions I went to the Bios menu (tapping the F2 key during the initial boot sequence). In the Bios menu, I switched the boot mode from Legacy to UEFI and restarted. I now have a initramfs prompt and after typing reboot, GRUB is displayed and if I choose the top Ubuntu option, I get a kubuntu screen followed by the initramfs prompt again.
I also ran Diagnostics  and all tests passed (in particular Hardware scan complete with no issues)
(initramfs) exit
ALERT! /dev/disk/by-uuid/e93ad2e1 does not exist. Dropping to a shell!
(initramfs) cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.19.0-80-generic.efi.signed root=UUID=e93ad2e1 ro quiet splash
(initramfs) cat /etc/fstab
cat: can&#8217;t open &#8216;/etc/fstab&#8217;: no such file or directory

---

### Post by oldfred on 2018-09-03
Need more details, just post link to summary report it creates:

       Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by mari-e on 2018-09-03
No sure how to run Boot-repair since I don't have a live Ubuntu session ? Thanks.

---

### Post by oldfred on 2018-09-03
You should always have a flash drive with the current version of installed system for repairs or maintenance. Same with Windows.

Can you boot second line in grub menu, the recovery mode.
Or the next older kernel? Or its recovery mode?

---

### Post by mari-e on 2018-09-03
Booting second line recovery mode doesn't work.
Get stuck into "Loading initial ramdisk ..." when booting next older kernel

---

### Post by mari-e on 2018-09-03
Loading older kernel in recovery mode gives me the same
ALERT! /dev/disk/by-uuid/e93ad2e1 does not exist. Dropping to a shell!

---

### Post by oldfred on 2018-09-03
You just about have to have a Ubuntu live installer to fix it then.
If you have a friend, work, or school with a computer you can download & install Ubuntu to a flash drive that will work.

---

### Post by mari-e on 2018-09-03
OK, does it mean that I will lose my data though ?

---

### Post by oldfred on 2018-09-03
If you can get an Ubuntu live installer, it probably can be repaired.
But you do have good backups? So we can just reinstall if needed?

---

### Post by mari-e on 2018-09-03
I have a backup on an external hard drive but it is a couple of months old...
Will try to boot with the live installer and get back.
Fingers crossed and thanks a lot for your help so far.

---

### Post by mari-e on 2018-09-04
Some success...I chose try ubuntu from the menu and I now have a familiar screen but not sure what to do next !

---

### Post by Yellow Pasque on 2018-09-04
You may want to run 'sudo blkid' and make sure the UUID matches what you're trying to boot.

> root=UUID=e93ad2e1

---

### Post by mari-e on 2018-09-04
No, it doesn't match
sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="UBUNTU 14_0" UUID="562A-D429" TYPE="vfat"

---

### Post by mari-e on 2018-09-04
I have also installed boot-repair but when I run it it recommends to backup data first and I am not sure how to access my data

---

### Post by oldfred on 2018-09-04
This looks like the installer, not your install.
/dev/sda1: LABEL="UBUNTU 14_0" UUID="562A-D429" TYPE="vfat" 				

And that is the older 14.xx version where current version is 18.04 and newer hardware needs the newer version.
Post this, sometimes systems make installer flash drive as sda, and internal drive as sdb. But once you install, remove installer flash drive and reboot the internal drive is then sda.
sudo parted -l

---

### Post by mari-e on 2018-09-04
OK, so should I try to get a new Ubuntu live installer with version 18.04 ? I thought using 14.04 was the reight thing to do as this is the version I had before.
Also, once I boot with the usb, is try ubuntu the right option to choose ?

---

### Post by oldfred on 2018-09-04
To repair it, then 14.04 may be better choice if 14.04 was working without issue.
But 14.04 is scheduled to reach end of live April 2019, so now is a good time to start planning to upgrade to newer version.

Use try Ubuntu which should boot, then use the instructions to add the Boot-Repair ppa and just run the report. Post link it gives as report can be long.

---

### Post by mari-e on 2018-09-04
When I run Boot-Repair I get warning about backing up data first. However I am not sure where my data is, I can&#8217;t see it on any of the drive

---

### Post by oldfred on 2018-09-04
Go ahead and run report. 
We may then see the issues.

The issue of blkid giving messages is probably why you cannot see you data.
You could try this first. Change example with sdb1 to your ext4 partition(s).

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Yellow Pasque on 2018-09-04
> **oldfred said:**
> This looks like the installer, not your install.
/dev/sda1: LABEL="UBUNTU 14_0" UUID="562A-D429" TYPE="vfat"

The UUID is there. It's only 8 digits because it's a FAT partition.

So I would try to boot as normal, except at grub menu, I would use the 'e' key to edit the boot line and replace:
```
root=UUID=e93ad2e1
```
with
```
root=UUID=562ad429
```

---

### Post by mari-e on 2018-09-04
Temujin,

I tried that but I am now getting
ALERT! /dev/disk/by-uuid/562A-D429 does not exist

---

### Post by mari-e on 2018-09-05
[COLOR=#000000][FONT=UICTFontTextStyleTallBody]After I rebooted I could see that the disk with my data was mounted (and I backed it up..).[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleTallBody]I generated the report[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleTallBody][http://paste.ubuntu.com/p/C4HKTbQFsw](http://paste.ubuntu.com/p/C4HKTbQFsw)[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleTallBody]Many thanks[/FONT][/COLOR]

---

### Post by oldfred on 2018-09-05
Please reboot in UEFI boot mode and rerun report. It says you are in BIOS/Legacy/CSM mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
It says UEFI Secure boot may be on, but do not think it really can tell in BIOS boot mode. But make sure Secure boot is off.

Your UEFI boot menu should have two boot modes for flash drive. One is UEFI:flash drive and other is "flash drive"  where flash drive is name, brand or label of flash drive. You want the UEFI one.

If booting in UEFI mode, you should get grub menu with options to either install or run as live system. BIOS boot has purple screen.

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you can boot in UEFI boot mode, and reload Boot-Repair, I would use its advanced mode and check the full uninstall and reinstall options.
       
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
 Some systems need NVMe SSD firmware updated. But often that is only easy from Windows.

---

### Post by lordfrikk on 2018-09-06
Looking at the report I'd guess your OS partition is the only ext4 partition with UUID e93ad2e1-5972-44f5-a3c5-7da4f3d0cdfc. After booting in UEFI mode, press e at the boot menu and replace root=UUID=e93ad2e1  with root=UUID=e93ad2e1-5972-44f5-a3c5-7da4f3d0cdfc.

---

### Post by mari-e on 2018-09-06
Hi, 
Sorry for the confusion, there is no such thing as "e93ad2e1". I was only using it as a shortcut to the longer string e93ad2e1-5972-44f5-a3c5-7da4f3d0cdfc.
So in Grub, the line is already root=UUID=e93ad2e1-5972-44f5-a3c5-7da4f3d0cdfc.

I generated the boot-repair report booting in UEFI mode this time.
[http://paste.ubuntu.com/p/P3HHvCgFgZ/](http://paste.ubuntu.com/p/P3HHvCgFgZ/)

---

### Post by lordfrikk on 2018-09-06
This time your disk is not shown in the report.

---

### Post by mari-e on 2018-09-06
"Your UEFI boot menu should have two boot modes for flash drive. One is  UEFI:flash drive and other is "flash drive"  where flash drive is name,  brand or label of flash drive. You want the UEFI one."
I have two boot sequence :
UEFI: THNSNxxxx NVMe Toshiba 256GB, Par
UEFI: Generic Flash Disk 8.07, Partition 1
(Both are ticked by default)


"If booting in UEFI mode, you should get grub menu with options to either  install or run as live system. BIOS boot has purple screen."
The grub menu doesn't have these options and I don't get a BIOS purple screen.
If I only tick UEFI: THNSNxxxx NVMe Toshiba 256GB,
I get 
Ubuntu
*Advanced options
System setup
Restore Ubuntu 14.04 to factory state

If I only tick UEFI: Generic Flash Disk 8.07, Partition 1
I get
Try Ubuntu without installing
Install Ubuntu
*OEM install
Check disk for defects

---

### Post by mari-e on 2018-09-06
boot-repair doesn't give me any advanced options. I only get the choice to create a BootInfo summary

---

### Post by oldfred on 2018-09-06
Because it is not showing NVMe drive, it has nothing to repair.
But your BIOS boot showed the NVMe drive.
Report is not as good with NVMe. It uses bootinfoscript as first third of report and bootinfoscript has not been updated to support NVMe drives. But BIOS report showed it later in report.

Grub does not give UEFI/BIOS boot option. UEFI and BIOS modes are not compatible. Or once you start booting you cannot change boot modes. 

Many NVMe drives need firmware updates to be fully supported. Do not know about Toshiba NVMe, but trying to update fromware for my Samsung SSD from Linux is not easy or does not work. Better from Windows.
Update, found this:
[https://ssd.toshiba-memory.com/en-amer/download/ssd-utility](https://ssd.toshiba-memory.com/en-amer/download/ssd-utility)

If you remove flash drive and reboot in UEFI mode using Toshiba entry, does it boot, or is issue that UEFI is not seeing drive correctly?

---

### Post by mari-e on 2018-09-06
No, it doesn't boot.I just get the initramfs prompt again

---

### Post by oldfred on 2018-09-06
If updating firmware from Toshiba, does not solve issue you can convert install to BIOS boot.
You then have to boot installer in BIOS mode, use gparted to add a tiny 1 or 2 unformatted partition and give it bios_grub flag (right click).
Then use Boot-Repair advanced mode to uninstall/reinstall grub. You want the grub-pc version for BIOS boot.

I do not know how to make bootable drive from .img files. That is common with Apple Mac and have seen instructions, but not saved them. I think similar to ISO. The bootable image then should still work on both Mac & PC.

---

### Post by mari-e on 2018-09-07
Created a bootable USB flash-drive with SSD to attempt a firmware update.
[https://ssd.toshiba-memory.com/en-am...ad/ssd-utility]("https://ssd.toshiba-memory.com/en-amer/download/ssd-utility")
But the firmware comes up as up-to-date already.

I am now on live boot from usb. Gparted shows one partition, /dev/sda1but the option to create a new one is greyed out...

---

### Post by mari-e on 2018-09-07
I really don't have a clue at the moment :(

---

