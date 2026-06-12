---
title: "Unable to dual boot windows and ubuntu"
date: 2021-12-08
forum: General Help
---

### Post by ischelle on 2021-12-08
I'm new to Linux, and I have some things incompatible that I need to run on Windows - so please bear with me. 

First, I'm running Ubuntu 21.10 on an M.2 SSD. I installed Windows afterwards on a 500GB SSD. I tried setting up grub in several ways:

1) sudo os-prober doesn't output anything.
2) Grub doesn't detect Windows 10 - even when updating, mountaing the SSD, etc. 

lsblk -f output:
```

sda                                                                         
&#9500;&#9472;sda1
&#9474;    ntfs         &#8207;&#8207;&#1513;&#1502;&#1493;&#1512; &#1506;&#1500;-&#1497;&#1491;&#1497; &#1492;&#1502;&#1506;&#1512;&#1499;&#1514;
&#9474;                       02F0CDB7F0CDB0E9                                    
&#9500;&#9472;sda2
&#9474;    ntfs               4280D1EF80D1E985                      441.9G     5% /media/isc
&#9492;&#9472;sda3
     ntfs               C41A5DAD1A5D9D6C                                    
sr0                                                                         
nvme0n1
&#9474;                                                                           
&#9500;&#9472;nvme0n1p1
&#9474;    vfat   FAT32       BB07-59BD                             505.8M     1% /boot/efi
&#9492;&#9472;nvme0n1p2
     ext4   1.0         05453a3a-5a86-4587-b09a-a7c1fcc3ad4b  824.7G     7% /



```

sda1 says "Reserved by the system". I tried adding a manual entry into sda1 and sda2 separately, but no go. I tried setting the entry to run Windows/Boot/EFI/bootmgfw.efi which does exist in SDA2 - 4280D1EF80D1E985 but it gave me an error basically saying to reinstall Windows. 

Running tree inside 

```
ischelle@ischelle:/media/ischelle/&#8207;&#8207;&#1513;&#1502;&#1493;&#1512; &#1506;&#1500;-&#1497;&#1491;&#1497; &#1492;&#1502;&#1506;&#1512;&#1499;&#1514;$ tree.
&#9500;&#9472;&#9472; Boot
&#9474;   &#9500;&#9472;&#9472; BCD
&#9474;   &#9500;&#9472;&#9472; BCD.LOG
&#9474;   &#9500;&#9472;&#9472; BCD.LOG1
&#9474;   &#9500;&#9472;&#9472; BCD.LOG2
&#9474;   &#9500;&#9472;&#9472; bg-BG
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; BOOTSTAT.DAT
&#9474;   &#9500;&#9472;&#9472; bootuwf.dll
&#9474;   &#9500;&#9472;&#9472; bootvhd.dll
&#9474;   &#9500;&#9472;&#9472; cs-CZ
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; da-DK
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; de-DE
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; el-GR
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; en-GB
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; en-US
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; es-ES
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; es-MX
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; et-EE
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; fi-FI
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; Fonts
&#9474;   &#9474;   &#9500;&#9472;&#9472; chs_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; cht_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; jpn_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; kor_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; malgun_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; malgunn_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; meiryo_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; meiryon_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; msjh_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; msjhn_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; msyh_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; msyhn_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; segmono_boot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; segoen_slboot.ttf
&#9474;   &#9474;   &#9500;&#9472;&#9472; segoe_slboot.ttf
&#9474;   &#9474;   &#9492;&#9472;&#9472; wgl4_boot.ttf
&#9474;   &#9500;&#9472;&#9472; fr-CA
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; fr-FR
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; hr-HR
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; hu-HU
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; it-IT
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; ja-JP
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; ko-KR
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; lt-LT
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; lv-LV
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; memtest.exe
&#9474;   &#9500;&#9472;&#9472; nb-NO
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; nl-NL
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; pl-PL
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; pt-BR
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; pt-PT
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; qps-ploc
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; qps-plocm
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; Resources
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootres.dll
&#9474;   &#9474;   &#9492;&#9472;&#9472; en-US
&#9474;   &#9474;       &#9492;&#9472;&#9472; bootres.dll.mui
&#9474;   &#9500;&#9472;&#9472; ro-RO
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; ru-RU
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; sk-SK
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; sl-SI
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; sr-Latn-RS
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; sv-SE
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; tr-TR
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9500;&#9472;&#9472; uk-UA
&#9474;   &#9474;   &#9492;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9500;&#9472;&#9472; zh-CN
&#9474;   &#9474;   &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;   &#9474;   &#9492;&#9472;&#9472; memtest.exe.mui
&#9474;   &#9492;&#9472;&#9472; zh-TW
&#9474;       &#9500;&#9472;&#9472; bootmgr.exe.mui
&#9474;       &#9492;&#9472;&#9472; memtest.exe.mui
&#9500;&#9472;&#9472; bootmgr
&#9500;&#9472;&#9472; BOOTNXT
&#9500;&#9472;&#9472; BOOTSECT.BAK
&#9492;&#9472;&#9472; System Volume Information
    &#9492;&#9472;&#9472; tracking.log



```

I tried to add manual entries, but it either doesn't find [FONT=Menlo]bootmgfw.efi or does absolutely nothing. I tried telling Windows to use grub using [/FONT]```
[FONT=Menlo]bcdedit /set {bootmgr} path \EFI\Ubuntu\grubx64.efi[/FONT]
```

At this point, I have no idea what to do. I tried reinstalling Windows, fixing the installer, etc.


sudo update-grub:
```
Sourcing file `/etc/default/grub'Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.13.0-22-generic
Found initrd image: /boot/initrd.img-5.13.0-22-generic
Found linux image: /boot/vmlinuz-5.13.0-19-generic
Found initrd image: /boot/initrd.img-5.13.0-19-generic
Adding boot menu entry for UEFI Firmware Settings
done

```

I went over 20 different codes, but *currently* my custom script looks like:

```
#!/bin/shexec tail -n +3 $0
menuentry 'Windows 10' {
  savedefault
  search --no-floppy --set=root --file /EFI/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}
```

---

### Post by oldfred on 2021-12-08
You have an ESP for Ubuntu, but not sure then if Windows used that ESP for its boot files.
How you boot install media, UEFI or BIOS is then how it installs.
And UEFI & BIOS are not compatible, once you start to boot from UEFI, you cannot switch. Or grub can only boot other installs in same boot mode.
Also grub can only boot working Windows. Windows cannot be hibernated (also fast start up sets hibernation flag) nor need chkdsk.

Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO (unless 21.10)
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2021-12-09
You will need to post the info from the boot rep;air script suggested by oldfred.

Did you use the 'Custom' install option in the windows installer?  Did you have the Ubuntu drive attached when you installed windows?

>   but no go. I tried setting the entry to run  Windows/Boot/EFI/bootmgfw.efi which does exist in SDA2 -  4280D1EF80D1E985 but it gave me an error basically saying to reinstall  Windows.  

sda2 is an ntfs filesystem and that file to boot windows UEFI (bootmgfw.efi) needs to be on a vfat partition marked as boot and efi which yours is not.  
nvme0n1p1 is  apparently the boot/efi partition used by Ubuntu.  THe boot repair output should have answers to these and other questions.

---

### Post by ischelle on 2021-12-09
> **oldfred said:**
> You have an ESP for Ubuntu, but not sure then if Windows used that ESP for its boot files.
How you boot install media, UEFI or BIOS is then how it installs.
And UEFI & BIOS are not compatible, once you start to boot from UEFI, you cannot switch. Or grub can only boot other installs in same boot mode.
Also grub can only boot working Windows. Windows cannot be hibernated (also fast start up sets hibernation flag) nor need chkdsk.


Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install, not Boot-Repair ISO (unless 21.10)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


I installed Ubuntu(I am on 21.10), then installed Windows through a custom run - I chose the proper SSD. 


As for trying to use boot repair or Boot-Info - after following the terminal commands in the guides I'm not locating any of the packages, I'm getting errors like these:


> 
E: The repository 'http://ppa.launchpad.net/gezakovacs/ppa/ubuntu impish Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu impish Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.



So I'm trying to get UNetbootin instead... however that's also an outdated github showing these errors. I'm only sharing this to make sure that this is normal. 


Anyways, I installed it the ISO onto a USB and booted it and ran Boot-Info as you suggested

[https://pastebin.ubuntu.com/p/zS5zWysR83/](https://pastebin.ubuntu.com/p/zS5zWysR83/)

---

### Post by oldfred on 2021-12-09
Boot-Repair does not seem to have a ppa available for 21.10, so downloading ISO is the only choice is using that version.

You have Windows in the old BIOS boot mode using MBR partitioning.
Microsoft has required vendors to install in UEFI boot mode with gpt partitioning since 2012, so all hardware since then is UEFI based.
This would be preferred choice if new install or you have good backups. 

You have several choices.
You can just always boot from UEFI boot mode. You may have to switch UEFI from UEFI to BIOS/CSM/Legacy, but newer systems now seem to recognize install mode and will boot.

You can totally reinstall Windows. The conversion from MBR to gpt will totally erase everything on that drive, all partitions. Or have good backups.
Supposed there are some tools to convert, but a few have posted they tried, failed & just reinstalled anyway.

If you want to dual boot from grub, you can convert the Ubuntu install from UEFI to BIOS. Ubuntu will boot in UEFI or BIOS mode from gpt partitioned drives, but you have to use gparted to add a tiny 1 or 2MB unformatted partition with bios_grub flag for BIOS installs on gpt partitioned drives. Then totally reinstall grub. No reinstall required, just grub install.There are two versions of grub, grub-efi-amd64 for UEFI and grub-pc for BIOS/CSM/Legacy boot.

---

### Post by tea for one on 2021-12-10
> **oldfred said:**
> You have Windows in the old BIOS boot mode using MBR partitioning.
Microsoft has required vendors to install in UEFI boot mode with gpt partitioning since 2012, so all hardware since then is UEFI based.
This would be preferred choice if new install or you have good backups.

Please follow [COLOR="#0000FF"]oldfred's[/COLOR] advice - backup your Windows data and re-install Windows 10 in UEFI mode.

Each OS on a separate drive is ideal.
If possible, remove your Ubuntu drive before re-installing Windows 10 so that only the [COLOR="#0000FF"]target[/COLOR] drive is visible.
You can then boot either OS from the UEFI boot menu.

More info here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ischelle on 2021-12-10
Well, I have failed making this work. 

First off, I downloaded the ISO from Windows and used Rufus to install it making sure UEFI is selected. Previously, I used the Microsoft creation tool when creating the bootable USB - but given that it has no option for UEFI or otherwise I tried RUFUS. 

It just doesn't boot. If only boots in legacy mode.(not when using Rufus) I tried following guides online like turning safe boot off, disabling CSM, and so on... The USB simply doesn't load Windows(except if I don't use UEFI). So at this point, I'm kinda stuck. 

I tried making the bootable myself but UEFI is incompatible with exFAT - and Windows ISO contains files > 4GB. UEFI is also incompatible with NTFS so I'm completely out of my depth here. My hardware should be modern enough - my Motherboard is an ASUS B350M-K which is only a few years old, definitely older than 2012.

---

### Post by tea for one on 2021-12-10
> **ischelle said:**
>  UEFI is also incompatible with NTFS.
That is not correct.

A Windows USB Installation device using Rufus will create two partitions.
One is FAT16 and the other is NTFS as shown below
```
edited@edited:~$ sudo parted -l
[sudo] password for edited: 
Model: UDISK PDU01-8G 8AH2.0 (scsi)
Disk /dev/sdb: 8087MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                 Flags
 1      1049kB  8086MB  8084MB  ntfs         Main Data Partition  msftdata
 2      8086MB  8086MB  524kB                UEFI:NTFS            msftdata
```

Anyway, we know that your PC is UEFI enabled because you have installed Ubuntu in UEFI mode.
Here are a some suggestions to try and boot your Windows 10 Installer:-

Power off PC completely
Windows must not be hibernated
Attach Windows USB installer
Power on and tap the dedicated boot menu key 

Try another USB stick
Use a different USB port on your PC
Use mkusb in Ubuntu to remake the install device
[https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive](https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive)

Do you possibly need to update UEFI firmware?

---

### Post by oldfred on 2021-12-10
I have not installed Windows but have one system with Windows just for TV. I do not back it up as it only has a couple of bookmarks.
But when Windows updates, I also download that newer version of the ISO and create a new installer.
I noted that the Windows installer has tools to split the .wim file which is over 4GB and does not otherwise fit on a FAT32 formatted flash drive.
For UEFI boot, you have to have an ESP that is FAT32.

Your UEFI should give you two options to boot flash drives. One is clearly UEFI and other is just name of flash drive which then is the BIOS/CSM/Legacy boot. Just always boot in UEFI mode. But you must use FAT32 for flash drive.

---

### Post by ischelle on 2021-12-11
> **tea for one said:**
> That is not correct.

A Windows USB Installation device using Rufus will create two partitions.
One is FAT16 and the other is NTFS as shown below
```
edited@edited:~$ sudo parted -l
[sudo] password for edited: 
Model: UDISK PDU01-8G 8AH2.0 (scsi)
Disk /dev/sdb: 8087MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                 Flags
 1      1049kB  8086MB  8084MB  ntfs         Main Data Partition  msftdata
 2      8086MB  8086MB  524kB                UEFI:NTFS            msftdata
```

Anyway, we know that your PC is UEFI enabled because you have installed Ubuntu in UEFI mode.
Here are a some suggestions to try and boot your Windows 10 Installer:-

Power off PC completely
Windows must not be hibernated
Attach Windows USB installer
Power on and tap the dedicated boot menu key 

Try another USB stick
Use a different USB port on your PC
Use mkusb in Ubuntu to remake the install device
[https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive](https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive)

Do you possibly need to update UEFI firmware?

OK, so I've done all of those things - the thing that worked is the UEFI firmware. Apparently it needed to be updated.
 I was finally able to boot and install Windows. Despite me specifically not choosing my Ubuntu drive, Windows seemed to have encroach itself onto my M.2 SSD. Fine, as long as it'll work.

I ran update-grub and no OS. However, running os-prober for the first time actually pointed me towards the Windows boot.

```
/dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi

```
 
My new lsblk -f values:

```


sda                                                                         
&#9492;&#9472;sda1
     ntfs               40D83221D832161E                                    
sdb                                                                         
&#9500;&#9472;sdb1
&#9474;    ntfs         CCCOMA_X64FRE_HE-IL_DV9
&#9474;                       3E0E382E0E37DE19                       23.4G    18% /media/isc
&#9492;&#9472;sdb2
     vfat   FAT12 UEFI_NTFS
                        09BA-0F01                               134K    87% /media/isc
sr0                                                                         
nvme0n1
&#9474;                                                                           
&#9500;&#9472;nvme0n1p1
&#9474;    vfat   FAT32       BB07-59BD                             480.5M     6% /boot/efi
&#9492;&#9472;nvme0n1p2
     ext4   1.0         05453a3a-5a86-4587-b09a-a7c1fcc3ad4b  813.4G     8% /



```


Edit:
I had DISABLE_OS_PROPER flag set to true in grub config. After commenting that line grub managed to find Windows on its own and I am successfully dual booting now.

Thanks for the help guys!

---

