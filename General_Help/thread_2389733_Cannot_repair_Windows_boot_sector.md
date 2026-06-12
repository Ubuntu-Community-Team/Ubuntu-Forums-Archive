---
title: "Cannot repair Windows boot sector"
date: 2018-04-20
forum: General Help
---

### Post by Acharn on 2018-04-20
Using Ubuntu 17.10 Artful Aardvark from USB stick on desktop PC with Windows 7 Ultimate 64-bit installed on HDD. I've come to hate grub. this is the third time it's trashed my Windows boot sector and done something else. I installed Ubuntu 17.10 on a USB stick. Took many tries before I found the BIOS settings that pleased the installer (UEFI Only). Next time I tried to boot from my HDD, I get
```

error: no such device (long serial number)
error: unknown filesystem
Entering rescue mode:
grub rescue> 
```
After that it does nothing. Perhaps there's a grub rescue command that would do something, but I don't know what it is. OK, back to the BIOS, restore the "UEFI & Legacy" "Legacy first", as it was before I installed Ubuntu. Same messages. Inserted Windows 7 installation disk, same messages. Inserted boot-repair disk. Same messages. This is puzzling because it does not seem to be reading the boot sector from the DVD. Tried installing Testdisk.
```
Errors were encountered while processing:
 shim-signed
 grub-efi-amd64-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Got the same errors when I tried to install Brasero so I could burn the latest .iso for boot-repair.
I would really like to be able to boot my Windows installation disks. There are now so many threads on how to repair the mbr that I'm overwhelmed. If I install UEFI on my hard drive, will I then be able to boot from my Windows 7 DVDs? I hope for some advice.

---

### Post by oldfred on 2018-04-21
Windows 7 DVD is BIOS only. You have to copy to flash drive and move/rename a couple of files to make it UEFI bootable.
And how you boot install media UEFI or BIOS, for both Windows & Ubuntu is then how it installs.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Acharn on 2018-04-21
OK, I don't **want** to make it UEFI bootable. I want to be able to boot my hard drive to Windows 7 as before, and I want to be able to boot my Windows 7 DVDs as before. I'm sorry if I wasn't clear. I do not know the PPA for boot-repair, but it's not in the repository available to the Live CD.

ETA: From the Live CD/DVD I am not able to update apt or apt-get.
```

sudo apt-get update
Ign:1 cdrom://Ubuntu 17.10 _Artful Aardvark_ - Release amd64 (20180105.1) artful InRelease
Hit:2 cdrom://Ubuntu 17.10 _Artful Aardvark_ - Release amd64 (20180105.1) artful Release
Hit:4 http://archive.ubuntu.com/ubuntu artful InRelease                        
Get:5 http://security.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]
Get:6 http://archive.ubuntu.com/ubuntu artful-updates InRelease [81.7 kB]      
Fetched 160 kB in 1s (105 kB/s)                                   
Reading package lists... Done
W: chown to _apt:root of file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_artful_InRelease failed - Item::QueueURI (95: Operation not supported)
W: chmod 0600 of file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_artful_InRelease failed - Item::QueueURI (95: Operation not supported)
W: chown to root:root of file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_artful_InRelease failed - 201::URIDone (95: Operation not supported)
W: chmod 0644 of file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_artful_InRelease failed - 201::URIDone (95: Operation not supported)

```

---

### Post by Acharn on 2018-04-21
Further to the above, when I tried to add the boot-repair from the link at the Boot-info page, I det the following error messages:
```

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
 Simple tool to repair frequent boot problems.

Website: https://sourceforge.net/p/boot-repair/home
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or Ctrl-c to cancel adding it.

gpg: keybox '/tmp/tmpkmn9h7uc/pubring.gpg' created
gpg: /tmp/tmpkmn9h7uc/trustdb.gpg: trustdb created
gpg: key 32B18A1260D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1
OK
Ign:1 cdrom://Ubuntu 17.10 _Artful Aardvark_ - Release amd64 (20180105.1) artful InRelease
Hit:2 cdrom://Ubuntu 17.10 _Artful Aardvark_ - Release amd64 (20180105.1) artful Release
Hit:4 http://archive.ubuntu.com/ubuntu artful InRelease                        
Get:5 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu artful InRelease [15.4 kB]
Get:6 http://security.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]    
Get:7 http://archive.ubuntu.com/ubuntu artful-updates InRelease [81.7 kB]      
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu artful/main amd64 Packages [1876 B]
Get:9 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu artful/main Translation-en [2036 B]
Fetched 180 kB in 2s (83.2 kB/s)                    
Reading package lists... Done
W: chown to _apt:root of file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_artful_InRelease failed - Item::QueueURI (95: Operation not supported)
W: chmod 0600 of file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_artful_InRelease failed - Item::QueueURI (95: Operation not supported)
W: chown to root:root of file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_artful_InRelease failed - 201::URIDone (95: Operation not supported)
W: chmod 0644 of file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_artful_InRelease failed - 201::URIDone (95: Operation not supported)

```
I could download the boot-repair .iso from sourceforge, but it wouldn't help, because brasero is no longer included on the Live DVD and I can't install it.

---

### Post by oldfred on 2018-04-21
The live installer is not updateable except in memory. So it cannot write to flash drive.
And if you left update gui process running (or it crashed) and then tried to use terminal to add Boot-Repair, update process would fail as only one program can run updates at once. There is a lock key written, sometimes you have to manually erase lock key if an update program crashes. 
With live installer just reboot and immediately run the commands to add Boot-Repair.

If Windows 7 is in BIOS boot mode, Ubuntu must be in BIOS boot mode, or else you have issues.
Need to see summary report to know your configuration.

---

### Post by Acharn on 2018-04-22
OK, for reasons I don't know I became unable to boot from the Ubuntu Live DVD too, so I had to take the PC to the shop and have them reinstall Windows 7. I'm going to have to be very, very careful in the future about trying to install Ubuntu onto a USB Stick. Is there a tutorial anywhere about how to do it?

---

### Post by oldfred on 2018-04-22
Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

       
 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode
[https://help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)
[https://ubuntuforums.org/showthread.php?t=2299040](https://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by Acharn on 2018-04-23
Oh, thank you very much for all your trouble.  This looks helpful. One clarification, I am not trying to make a bootable live installer, I am trying to fully install Ubuntu onto a USB stick. Since the arrival of USB 3.0 this has an acceptable speed. I have done this in the past, but since 16.04 I have had multiple problems. I don't use Linux much right now, but I expect Windows 7 will end support eventually and I will be forced to use only Linux. I quite like Ubuntu, but I don't want to install it on my hard drive yet.

---

### Post by oldfred on 2018-04-23
You install to any external drive just like any other install, but must use Something Else.
And if BIOS install must select the external drive as location to install grub bootloader. Its a combo box on partitioning screen. 
If UEFI you must partition in advance and include the ESP - efi system partition (FAT32) as grub does not let you set install to external drive. You can manually reconfigure after install.

I do use gpt partitioning for all new drives. Only if installing Windows (which you cannot do to external drive) and want BIOS do you need the now 35 year old MBR(msdos) partitioning. All my 16GB or larger flash drives are gpt.And I then include the ESP for UEFI and a bios_grub for BIOS boot, so I can reconfigure for either UEFI or BIOS using gpt.

I also have full installs to flash drives, now all are UEFI. My newest install with 18.04 to a new flash drive has been an issue. Flash drive is extremely slow, almost like it is USB2, not the USB3 it is labeled as. Install & writes to flash drive is slow. My installs to SSD take 10 min, but flash drive is normally nearly an hour. But this new flash drive seems to be over 2 hours. Still testing it.Writing speed tests show it slightly lower than other flash drives.

Process has not changed much with last few versions.
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not highlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond) 

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

