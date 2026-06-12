---
title: "Dual Boot Install Fails Due to Grub install error (Cannot find EFI directory)"
date: 2018-02-05
forum: General Help
---

### Post by iiyyaann on 2018-02-05
I wanted to install a dual boot system with Windows 10 and Ubuntu on my machine (specs: Intel Core i3-6100 CPU @ 3.70GHz, 8GB of RAM).

I shrank my Windows partition calling diskmgmt.msc from an elevated PowerShell to get 223.27GB of available space for Ubuntu.
[ATTACH=CONFIG]278444[/ATTACH]

I made sure secure boot and fast boot were disabled.

When installing from a live usb key, I chose "something else" and from the 223.27GB available I created a root Ext4 primary partition at the beginning of the space.

Windows 10 was not detected by the Ubuntu installer and installing Grub failed with a "Cannot find EFI directory" message.

What am I doing wrong?

Thanks.

---

### Post by oldfred on 2018-02-05
Fast boot is an UEFI setting.
In Windows you must also turn off fast start up which is just hibernation.
Linux driver will not mount hibernated NTFS to prevent damage, but then installer cannot even see it.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by iiyyaann on 2018-02-05
> **oldfred said:**
> Fast boot is an UEFI setting.
In Windows you must also turn off fast start up which is just hibernation.


Done. I get the following message:

> "This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later. 
If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here. If you wish to keep the option to boot an existing operating system, you should choose NOT to force UEFI installation here.")

I tried to force UEFI installation and installing Grub failed again. Any clue?

---

### Post by oldfred on 2018-02-05
If you have Windows in BIOS boot mode forcing UEFI install converts drive to gpt and then you have destroyed Windows install as a BIOS Windows only boots from MBR partitioned drives.

Are you installing Debian, not Ubuntu?

Post this from terminal in live installer:
sudo parted -l

How you boot install media for both Windows & Ubuntu (or any system) is then how it installs.
But then system must also be set to boot in that mode with UEFI settings.
Windows only boots from MBR(msdos) with BIOS.
Windows only boots from gpt(GUID) with UEFI. 
Ubuntu can boot from gpt with BIOS or UEFI.

 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by iiyyaann on 2018-02-05
> Are you installing Debian, not Ubuntu?

No, I'm installing Ubuntu

> Post this from terminal in live installer:
sudo parted -l

This is the output I get

```
Model: ATA WDC WD10EZEX-08W (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size   Type     File system  Flags
 1      1049kB  525MB   524MB  primary  ntfs         boot
 2      525MB   760GB   759GB  primary  ntfs
 4      760GB   1000GB  240GB  primary  ext4
 3      1000GB  1000GB  490MB  primary  ntfs         diag


```


> How you boot install media for both Windows & Ubuntu (or any system) is then how it installs.
But then system must also be set to boot in that mode with UEFI settings.
Windows only boots from MBR(msdos) with BIOS.
Windows only boots from gpt(GUID) with UEFI. 
Ubuntu can boot from gpt with BIOS or UEFI.

Thanks for the docs. I'm going to read them and see if I understand the situation better afterwards.

---

### Post by oldfred on 2018-02-05
Still looks like BIOS/MBR configuration.
But you have to have installed Ubuntu in BIOS mode. If UEFI error, may be trying to install UEFI boot files to an ESP (even with MBR) which does not exist.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

With Windows 10 in BIOS mode, you need two repair flash drives. One Windows and one Ubuntu. So keep Ubuntu live installer as repair tool.
Either Windows installer or you can make another repair/recovery flash drive.


 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

Windows likes to turn fast start up back on with updates and then grub will not boot it. And then you have to directly boot Windows. And with BIOS you only have one MBR so have to temporarily install the Windows boot loader, repair Windows and then restore grub. With UEFI you in effect have more than one MBR as every install shares the ESP - efi system partition.

      
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by yancek on 2018-02-05
Since your windows is an MBR/Legacy install, you need to install Ubuntu in the same manner.  The Ubuntu documentation at the link below explains dual booting Ubuntu/windows.  Look specifically at the section down the page a bit,  Identifying if the computer boots in UEFI mode.  You will see a different screen on boot with UEFI than with Legacy.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

