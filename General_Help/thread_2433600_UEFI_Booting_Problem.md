---
title: "UEFI Booting Problem"
date: 2019-12-21
forum: General Help
---

### Post by Mr Fredrick on 2019-12-21
Hi All,

When I run the following command:

```
$ [ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"
```

my system reports that it is booting in legacy mode, when I want it to do so in UEFI.

My partition table is as follows:

```
Model: ADATA SX8200PNP (nvme)
Disk /dev/nvme0n1: 2048GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system    Name                  Flags
 1      1049kB  538MB   537MB   fat32          EFI System Partition  boot, esp
 2      538MB   539MB   1049kB  grub2 core.img                       bios_grub
 4      539MB   410GB   410GB   ext4
 3      410GB   2048GB  1638GB  ext4           Home Partition ext4
```

Also when I hit F2 at start-up and go into the BIOS settings utility no UEFI boot options are listed in the Boot Order dropdown.

How can I force the system back to UEFI booting and get the BIOS settings utility to list UEFI boot options.

Thanks in advance.

MrFred.

---

### Post by oldfred on 2019-12-21
You have both an ESP for UEFI boot and a bios_grub for BIOS boot.
If booting in BIOS mode, you have the BIOS version of grub2, grub-pc. 

If you want UEFI boot you have to un-install grub-pc and install grub-efi-amd64. Often easier to use Boot-Repair's advanced options, booting flash drive in UEFI mode.
       [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If  in your install, note if reinstall of grub does not finish correctly you will not be able to reboot.
      
 sudo apt purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub 
            sudo apt install grub-efi-amd64-signed 
    
  sudo grub-install /dev/nvme0n1      --uefi-secure-boot
sudo update-grub 
    [URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by Dennis N on 2019-12-22
> my system reports that it is booting in legacy mode, when I want it to do so in UEFI.
You won't be able to boot an operating system in UEFI mode unless it was installed in UEFI mode - which happens when the installation media is booted in UEFI mode.

---

### Post by Mr Fredrick on 2019-12-22
Hi oldfred,

Thanks for the timely response.

In a previous attempt to fix this problem I booted to a USB and ran Disk-Repair but it kept reporting an error and wouldn't actually repair anything. Is it possible to do the repair without using that utility, for instance, if I exactly follow the list of commands:

```
sudo apt purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt install grub-efi-amd64-signed

sudo grub-install /dev/nvme0n1 --uefi-secure-boot
sudo update-grub
```

that you gave in your reply instead, will that fix the problem?

Sorry but just a bit confused and I don't want to end up with an un-bootable system.

Mr Fred.

---

### Post by yancek on 2019-12-22
You might be better off getting boot repair from the link below and using the 2nd option described on that page to get the ppa while booted into Ubuntu, run it by selecting the Create BootInfo Summary option and do NOT  make any changes.  It should give you a link and you should be able to review the output or post the link here so that members can view it and make suggestions.  Too little info in your posts.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What type hardware are you using, what manufacturer?  How old/new is it?   Not knowing what hardware you have, I don't know what the F12 key does.  Does it give you simply boot options or is this how you access the BIOS firmware to make permanent changes?  You have a GPT disk so probably it is EFI capable so I would suggest you look around a little more for references to UEFI after accessing the BIOS.  If there are none then I don't suppose it is EFI capable.  Also, the information you posted above shows that sda1 is an EFI partition.  If the install was EFI, you should be able to mount that partition and take a look at it to see if you have the proper Ubuntu EFI files.  If there is no directory named ubuntu there then you won't be able to boot EFI.

Did you try disabling Legacy/CSM in the BIOS firmware and rebooting to see if it boots EFI?  If you do this, make note of the steps so you can change back if it doesn't help. 

The link below is to the Ubuntu documentation on converting Ubuntu into UEFI mode so if you are feeling lucky...?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-12-22
If you are going to use the chroot method from a live installer into your system, you have to also mount the ESP - efi system partition.

        chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

---

### Post by Mr Fredrick on 2019-12-22
Thanks for your responses,

Here is the link to the info about my system gathered by Boot Repair:
[https://paste.ubuntu.com/p/H4FMGbxFGG](https://paste.ubuntu.com/p/H4FMGbxFGG)

Information about my hardware is in the signature of my posts

I have already attempted to fix the problem by following the advice on this page:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

specifically in the "Converting Ubuntu into UEFI Mode"

I followed its advice after booting from a USB however when I click "Apply" with the "Separate /boot/efi partition:" option selected, I always get an error. Should I run Boot Repair from a USB or not when attempting this?

*Did you try disabling Legacy/CSM in the BIOS firmware and rebooting to see if it boots EFI?*

Yes, I have done this many times but it makes no difference.

---

### Post by oldfred on 2019-12-22
Best to boot live installer in  UEFI mode to make UEFI repairs.
>         BIOS is EFI-compatible, but it is not setup in EFI-mode for this installed-session. 
    

have you updated UEFI from ASRock?
And SSD firmware?

This may have some more info:
       Asrock B450M Steel Legend - turn UEFI Secure Boot off  
[https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine](https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine)

With nVidia, you need nomodeset to boot.
But very newest Ubuntu will offer to install nVidia as part of proprietary drivers.

Boot-Repair uses bootinfoscript as part of report, but bootinfoscript has not been updated to show NVMe drives, so not all your data in report.


       
 AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
AMD Releases BIOS Fix To Motherboard Partners For Booting Newer Linux Distributions July 2019
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2)
400 series chipsets need BIOS/UEFI update for Ryzen 3000, 500 seires standard with 3000
[https://ubuntuforums.org/showthread.php?t=2430149&p=13904266#post13904266](https://ubuntuforums.org/showthread.php?t=2430149&p=13904266#post13904266)

---

### Post by Mr Fredrick on 2019-12-23
> have you updated UEFI from ASRock?
And SSD firmware?

My system is brand new, it was put together in Sept of this year when the BIOS and all drivers were updated to their latest versions. 

When I first took possession it booted as expected in UEFI mode but since then I have for other reasons reinstalled Ubuntu a few times and also partially re-partitioned the disk i.e. to add a home partition, etc. It seems that it has been these changes that have inadvertently caused the system to now boot in Legacy Mode. 

Note: I have already turned the UEFI Secure Boot option off and the Legacy Mode option also.

> Boot-Repair uses bootinfoscript as part of report, but bootinfoscript has not been updated to show NVMe drives, so not all your data in report.

Boot Info Script was not installed on my system, I have now installed it and re-run Boot Repair, the new report it generated is here:
[https://paste.ubuntu.com/p/2dYYWVjpm8/](https://paste.ubuntu.com/p/2dYYWVjpm8/)

I have generated a separate Boot Info report, its results are here:
[https://paste.ubuntu.com/p/SqRCbvpXvW](https://paste.ubuntu.com/p/SqRCbvpXvW)

---

### Post by strangerthanbland on 2019-12-23
@yancek in my experience it be possible to reboot directly into the correct set of menus via `sudo systemctl reboot --firmware-setup`... well on most systems utilizing systemd, no need to know what *F<n>* button should be pressed during boot.


___


@Mr Fredrick I've recently had to add a drive to my own list of boot options, here's some of the highlights;

- once in the correct menu (see above comment about rebooting), **and** with UEFI enabled, look for a `Boot` *tab,* (Left/Right arrow keys usually be able to select it)

- within the `Boot` *tab* look for an option such as `File Browser Add Boot Option` and select it

- should be a pop-up menu titled something like `Select Media Driver`, select the correct drive (likely you'll have one to choose from)

- next there'll likely be a pop-up titled something like `Select Media File`, at which point selecting `<EFI>` *should* update that pop-up with a list of files

- still within the `Select Media File` menu look for something similar to `grubx64.efi` and select that

- there should then be a prompt to name the boot option, so input a descriptive name

- the pop-up should then disappear, dropping ya back into the `Boot` *tab*, at which point it'll then be possible to set the `Boot Option Priorities` by selecting the name previously entered (Up/Down arrow keys) and then moving it up the list (usually with the Space-Bar)

- look about for text stating how to Save and Exit (often F10) and press that key to do just that

Provided that things where selected and correctly configured, and that the OS was originally setup with EFI the system should reboot into the drive with the highest priority.


One note about Boot Repair, it should only be used via a Live USB or CD, attempting to repair a system that is currently active will likely result in errors or if forced many hours of frustration. So long as Ubuntu was installed with UEFI enabled it should be possible to fiddle with boot menus, avoiding the need of Boot Repair... that all stated it still would be a good idea to make backups prior to following any of the above tips.

---

### Post by Mr Fredrick on 2019-12-23
I'm now attempting to fix the problem by using Boot Repair running from a USB. I shutdown my desktop and then restart and then I hit the F11 key to bring up the boot menu choices, which are:

ubuntu (ADATA SX8200PNP)
NVME: ADATA SX8200PNP
USB: Zipp 4GB 8.07
UEFI: Zipp 4GB 8.07
UEFI: Zipp 4GB 8.07, Partition2

I select the fourth option:
UEFI: Zipp 4GB 8.07

This starts Ubuntu from the USB. I then attempt to install Boot Repair but I encounter many problems in doing so as it complains about broken packages, etc, etc... I have been unable to overcome the problems.
So now I am trying to create a bootable Boot Repair USB following this advice:
[https://www.fosslinux.com/1521/boot-repair-for-ubuntu-linux-mint-and-elementary-os-can-fix-bootloader-issues.htm](https://www.fosslinux.com/1521/boot-repair-for-ubuntu-linux-mint-and-elementary-os-can-fix-bootloader-issues.htm)

---

### Post by oldfred on 2019-12-23
The Boot-Repair ISO was based on an older version of Lubuntu or Debian, so may not work with newer computers. That is why we normally suggest booting with the Ubuntu live installer that you are using to install.

If live installer does not boot in UEFI mode then that needs to be resolved.
What version of Ubuntu?

Also since you know about bootinfoscript can you run the version that was updated to include nvme drives?
       Support NVMe and MMC devices bug oldfred request
[https://github.com/arvidjaar/bootinfoscript/issues](https://github.com/arvidjaar/bootinfoscript/issues)
See post by baedacool of proposed fixed version. Link in pull request
[https://github.com/baedacool/bootinfoscript](https://github.com/baedacool/bootinfoscript)

You need to check that you have latest UEFI.
The AMD fixes for use with 19.10 are recent & required. AMD released to vendors, but then it took a month or two before vendors rolled out fixes in there UEFI updates.
       AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
AMD Releases BIOS Fix To Motherboard Partners For Booting Newer Linux Distributions July 2019
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2)

---

### Post by Mr Fredrick on 2019-12-23
Hi oldfred,

Following your advice I downloaded bootinfoscript from:
[https://github.com/baedacool/bootinfoscript](https://github.com/baedacool/bootinfoscript)

and ran it, the results are below:

```
                  Boot Info Script 0.77      [10 June 2018]


============================= Boot Info Summary: ===============================


============================ Drive/Partition Info: =============================

no valid partition table found
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop10                                             squashfs   
/dev/loop11                                             squashfs   
/dev/loop12                                             squashfs   
/dev/loop13                                             squashfs   
/dev/loop14                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/nvme0n1p1   31AC-C2B5                              vfat       
/dev/nvme0n1p2                                                     
/dev/nvme0n1p3   96ffb52d-b7e4-400b-9180-63ad09b88628   ext4       home
/dev/nvme0n1p4   9b451ec2-d2c7-42df-aac3-cd6840606448   ext4       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root 13 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part4 -> ../../nvme0n1p4
lrwxrwxrwx 1 root root 13 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part4 -> ../../nvme0n1p4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/fuse        /run/user/1000/doc       fuse       (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/nvme0n1p3   /home                    ext4       (rw,nosuid,nodev,relatime)
/dev/nvme0n1p4   /                        ext4       (rw,relatime,errors=remount-ro)
```

although these values don't seem to be any different than that in previous versions. Please let me know if these results contain the information that you require.

I am using Ubuntu 19.10

I have abandoned my attempt to use this version of Boot Repair:
[https://www.fosslinux.com/1521/boot-...der-issues.htm](https://www.fosslinux.com/1521/boot-...der-issues.htm)
since due to my very slow internet connection it would take several hours to do so, so I'm back to solving this problem by another method.

Regarding the UEFI drivers and fixes, I will now check this out and update if I can, but I don't think that this is the problem since I have already installed the OS successfully in UEFI mode.

---

### Post by oldfred on 2019-12-23
It looks like you ran the standard bootinfoscript as badercool just shows fork.

I do not totally understand github and all the forked versions, but it looks like badercool just has forked standard bootinfoscript. I know before he had posted a version with nmve fixes in the bug report and I thought that was what was in his fork.

Now I see in arvidjaar's github another copy that says NVME.
And in baedacool's github is another version by Peter Maier with nvme-support.
I need to compare those two nvme versions, and then file bug report with Yann on Boot-Repair to use one or the other, or if same, either one. Then Boot-Repair will support NVMe devices.

Not now sure if these are different or not, but cannot test as I do not have NVMe drive.
       baedacool & Peter Maier
[https://github.com/baedacool/bootinfoscript/blob/nvme-support/bootinfoscript](https://github.com/baedacool/bootinfoscript/blob/nvme-support/bootinfoscript)
arvidjaar 
[https://github.com/arvidjaar/bootinfoscript/blob/nvme/bootinfoscript](https://github.com/arvidjaar/bootinfoscript/blob/nvme/bootinfoscript)

---

### Post by Mr Fredrick on 2019-12-23
Hi oldfred,

I downloaded bootinfoscript from:
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

The results are:
```

                 Boot Info Script 0.78      [09 October 2019]


============================= Boot Info Summary: ===============================


============================ Drive/Partition Info: =============================

no valid partition table found
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop10                                             squashfs   
/dev/loop11                                             squashfs   
/dev/loop12                                             squashfs   
/dev/loop13                                             squashfs   
/dev/loop14                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/nvme0n1p1   31AC-C2B5                              vfat       
/dev/nvme0n1p2                                                     
/dev/nvme0n1p3   96ffb52d-b7e4-400b-9180-63ad09b88628   ext4       home
/dev/nvme0n1p4   9b451ec2-d2c7-42df-aac3-cd6840606448   ext4       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root 13 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part4 -> ../../nvme0n1p4
lrwxrwxrwx 1 root root 13 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part4 -> ../../nvme0n1p4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/fuse        /run/user/1000/doc       fuse       (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/nvme0n1p3   /home                    ext4       (rw,nosuid,nodev,relatime)
/dev/nvme0n1p4   /                        ext4       (rw,relatime,errors=remount-ro)
```

which seem to be identical to the previous version.

---

### Post by oldfred on 2019-12-23
The two links I have in post #14 are not the standard bootinfoscript. Slight differences.

Both add this: 
> All_Hard_Drives=$(echo /dev/hd+([a-z]) /dev/sd+([a-z]) /dev/xvd+([a-z]) /dev/vd+([a-z]) [COLOR=#ff0000]/dev/nvme+([0-9])n+([0-9])[/COLOR] 2>> ${Trash});

---

### Post by Mr Fredrick on 2019-12-23
Hi oldfred,

OK. Checking out the bootinfoscript files that I have downloaded for the string:

> All_Hard_Drives=$(echo /dev/hd+([a-z]) /dev/sd+([a-z]) /dev/xvd+([a-z]) /dev/vd+([a-z]) /dev/nvme+([0-9])n+([0-9]) 2>> ${Trash});

using Geany has turned it up in only one of the files. I also noticed that because of the way Geany saves files on my system (it converts tabs to spaces) this changes some sections of the files to text when it should be code. I have fixed the problem now and the routines run correctly.

Hopefully this is the output you require:
```

                Boot Info Script 0.75      [14 November 2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/nvme0n1 and looks at sector 
    1050624 of the same hard drive for core.img. core.img is at this location 
    and looks for (,gpt4)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------

nvme0n11: ______________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-mFNACboh/nvme0n11: unknown filesystem type ''.

nvme0n12: ______________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Unknown
    Boot sector info: 

nvme0n13: ______________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-mFNACboh/nvme0n11: unknown filesystem type ''.
mount: /tmp/BootInfo-mFNACboh/nvme0n13: unknown filesystem type ''.

nvme0n14: ______________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-mFNACboh/nvme0n11: unknown filesystem type ''.
mount: /tmp/BootInfo-mFNACboh/nvme0n13: unknown filesystem type ''.
mount: /tmp/BootInfo-mFNACboh/nvme0n14: unknown filesystem type ''.

============================ Drive/Partition Info: =============================

Drive: nvme0n1 _____________________________________________________________________
Disk /dev/nvme0n1: 1.88 TiB, 2048408248320 bytes, 4000797360 sectors
Disk model: ADATA SX8200PNP                         
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/nvme0n11                  1 4,000,797,359 4,000,797,359  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/nvme0n11                2,048     1,050,623     1,048,576 EFI System partition
/dev/nvme0n12            1,050,624     1,052,671         2,048 BIOS Boot partition
/dev/nvme0n13          800,995,328 4,000,786,431 3,199,791,104 Data partition (Linux)
/dev/nvme0n14            1,052,672   800,995,327   799,942,656 Data partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop10                                             squashfs   
/dev/loop11                                             squashfs   
/dev/loop12                                             squashfs   
/dev/loop13                                             squashfs   
/dev/loop14                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/nvme0n1p1   31AC-C2B5                              vfat       
/dev/nvme0n1p2                                                     
/dev/nvme0n1p3   96ffb52d-b7e4-400b-9180-63ad09b88628   ext4       home
/dev/nvme0n1p4   9b451ec2-d2c7-42df-aac3-cd6840606448   ext4       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root 13 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part4 -> ../../nvme0n1p4
lrwxrwxrwx 1 root root 13 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part4 -> ../../nvme0n1p4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/fuse        /run/user/1000/doc       fuse       (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/nvme0n1p3   /home                    ext4       (rw,nosuid,nodev,relatime)
/dev/nvme0n1p4   /                        ext4       (rw,relatime,errors=remount-ro)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on nvme0n11


Unknown BootLoader on nvme0n12


Unknown BootLoader on nvme0n13


Unknown BootLoader on nvme0n14



=============================== StdErr Messages: ===============================

hexdump: /dev/nvme0n11: No such file or directory
hexdump: /dev/nvme0n11: No such file or directory
hexdump: /dev/nvme0n12: No such file or directory
hexdump: /dev/nvme0n12: No such file or directory
hexdump: /dev/nvme0n13: No such file or directory
hexdump: /dev/nvme0n13: No such file or directory
hexdump: /dev/nvme0n14: No such file or directory
hexdump: /dev/nvme0n14: No such file or directory
```

---

### Post by oldfred on 2019-12-23
It added info, but looks like it left out the p in some places so/dev/nvme0n1p1 became/dev/nvme0n11. 
And then in some other places gave error  which may be just because it cannot find partition nvme0n11?

The other script looked similar but more complete in searching for additional drives and two digit partitions.

[https://github.com/baedacool/bootinfoscript/blob/nvme-support/bootinfoscript](https://github.com/baedacool/bootinfoscript/blob/nvme-support/bootinfoscript)
       RELEASE_DATE='12 February 2019';
```
All_Hard_Drives=$(ls /dev/hd[a-z] /dev/hd[a-z][a-z] /dev/sd[a-z] /dev/sd[a-z][a-z] /dev/xvd[a-z] /dev/vd[a-z] /dev/vd[a-z][a-z] /dev/nvme[0-9]n[0-9] /dev/nvme[0-9]n[0-9][0-9] /dev/nvme[0-9][0-9]n[0-9] /dev/nvme[0-9][0-9]n[0-9][0-9] 2>> ${Trash}); 

    
```

---

### Post by Mr Fredrick on 2019-12-23
Hi oldfred,

Here is another more recent version:
```
      
 Boot Info Script 0.79      [12 February 2019]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/nvme0n1 and looks at sector 
    1050624 of the same hard drive for core.img. core.img is at this location 
    and looks for (,gpt4)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------

nvme0n11: ______________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 

nvme0n12: ______________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Unknown
    Boot sector info: 

nvme0n13: ______________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 

nvme0n14: ______________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: nvme0n1 _____________________________________________________________________
Disk /dev/nvme0n1: 1.88 TiB, 2048408248320 bytes, 4000797360 sectors
Disk model: ADATA SX8200PNP                         
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/nvme0n1p1                  1 4,000,797,359 4,000,797,359  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/nvme0n11                2,048     1,050,623     1,048,576 EFI System partition
/dev/nvme0n12            1,050,624     1,052,671         2,048 BIOS Boot partition
/dev/nvme0n13          800,995,328 4,000,786,431 3,199,791,104 Data partition (Linux)
/dev/nvme0n14            1,052,672   800,995,327   799,942,656 Data partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop10                                             squashfs   
/dev/loop11                                             squashfs   
/dev/loop12                                             squashfs   
/dev/loop13                                             squashfs   
/dev/loop14                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/nvme0n1p1   31AC-C2B5                              vfat       
/dev/nvme0n1p2                                                     
/dev/nvme0n1p3   96ffb52d-b7e4-400b-9180-63ad09b88628   ext4       home
/dev/nvme0n1p4   9b451ec2-d2c7-42df-aac3-cd6840606448   ext4       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root 13 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-ADATA_SX8200PNP_2J3420178124-part4 -> ../../nvme0n1p4
lrwxrwxrwx 1 root root 13 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Dec 24 06:36 nvme-nvme.1cc1-324a33343230313738313234-414441544120535838323030504e50-00000001-part4 -> ../../nvme0n1p4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/fuse        /run/user/1000/doc       fuse       (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/nvme0n1p3   /home                    ext4       (rw,nosuid,nodev,relatime)
/dev/nvme0n1p4   /                        ext4       (rw,relatime,errors=remount-ro)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on nvme0n11


Unknown BootLoader on nvme0n12


Unknown BootLoader on nvme0n13


Unknown BootLoader on nvme0n14



=============================== StdErr Messages: ===============================

hexdump: /dev/nvme0n11: No such file or directory
hexdump: /dev/nvme0n11: No such file or directory
hexdump: /dev/nvme0n12: No such file or directory
hexdump: /dev/nvme0n12: No such file or directory
hexdump: /dev/nvme0n13: No such file or directory
hexdump: /dev/nvme0n13: No such file or directory
hexdump: /dev/nvme0n14: No such file or directory
hexdump: /dev/nvme0n14: No such file or directory
```

---

### Post by oldfred on 2019-12-24
Has same error.

But they show you installed in BIOS boot mode as you have grub in MBR of the NVMe drive and have a bios_grub partition.
And it looks like you have an ESP as first NVMe partition is labeled as EFI system partition and elsewhere as vfat.
You should be able to install or reinstall grub in UEFI boot mode and just not ever boot in BIOS mode. 
Once converted to UEFI boot mode the grub in MBR will not work, but should never be used, so we do not erase it. If you did then boot in BIOS mode, you get grub> error command line.

have you tried installing grub from inside install as in post #2?
Or chroot with mounting of ESP. Better to be in UEFI boot mode, not not sure that is absolutely required. But you may also then have to download grub-efi-amd64. I saw some discussion by developers that each version of grub excluded the other version and they were planning on allowing both versions to be downloaded.

---

### Post by Mr Fredrick on 2019-12-24
Hi oldfred,

> But they show you installed in BIOS boot mode as you have grub in MBR of the NVMe drive and have a bios_grub partition.
And it looks like you have an ESP as first NVMe partition is labeled as EFI system partition and elsewhere as vfat.

Yes, I already know that I have both an EFI partition AND a BIOS partition, as it were.

I now realise that this problem occurred when I installed Ubuntu for a second time. The initial install went correctly and it booted in UEFI mode, as expected, but when I reinstalled I must have selected the 3rd option from these choices when I pressed F11 at the start of the second install:
```

1 - ubuntu (ADATA SX8200PNP)
2 - NVME: ADATA SX8200PNP
3 - USB: Zipp 4GB 8.07
4 - UEFI: Zipp 4GB 8.07
5 - UEFI: Zipp 4GB 8.07, Partition2
```
This then installed Ubuntu in Legacy mode, and I've been stuck with it ever since. I should have selected the 4th option.

I can see now that Boot Repair is not going to assist me, I require another technique to over come this.

So, how do I re-install Grub from inside a Live USB that is booted in UEFI mode? Will doing that be enough to overcome the problem, for example won't I be missing some files like: /sys/firmware/efi, that are necessary for UEFI. Presently I don't have these files on my install?

---

### Post by oldfred on 2019-12-24
I know Boot-Repair does it with a mini-version of chroot. It just has you walk thru the steps it cannot automate.

I think just installing grub-efi-am64 includes as dependencies everything you need. But have not converted from inside an install myself. And your configuration variables are written into harddrive for operating system as you boot. Fast Boot in UEFI skips that step assuming everything is the same.

And thanks for posting all the bootinfoscripts. I will go back and post bug on the error in the output. I will probably link to this thread so they can see details.

---

### Post by Mr Fredrick on 2019-12-28
Hi oldfred,

I have attempted to reset my system to UEFI booting using this series of commands:

```

1 - sudo apt purge grun-pc grub-common
2 - sudo mv /boot/grub /boot/grub_backup
3 - sudo mkdir /boot/grub
4 - sudo apt install grub-efi-amd64-signed
5 - sudo grub-install /dev/nvme0n1 --uefi-secure-boot
6 - sudo update-grub

``` 
as explained in a previous post in this thread.

All goes well until command 5 when I get the error message:
"failed to get canonical path of /dev/nvme0n1p1"

Because of this and because I have already purged grub I am now unable to boot into my system without a Live USB.

This is the advice I found on StackExchange which I used to set-up the environment on the Live USB for chrooting:
```

sudo mount /dev/sdXXX /mnt
sudo mount /dev/sdXY /mnt/boot
sudo mount /dev/sdXX /mnt/boot/efi
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
grub-install /dev/sdX
update-grub
=========================================================================
Note : sdX = disk | sdXX = efi partition | sdXY = boot partition | sdXXX = system partition 

```

Which I have translated into:
```

sudo mount /dev/nvme0n1p4 /mnt
sudo mount /dev/nvme0n1p1 /mnt/boot/efi
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done

```
and various combinations of the above but nothing has worked.

Could you please tell me how I do set-up the correct mounts?

My partition table is:
```

Disk /dev/nvme0n1: 1.88 TiB, 2048408248320 bytes, 4000797360 sectors
Disk model: ADATA SX8200PNP                         
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 08F811AE-11BF-495E-870C-C9A7756F2E0A

Device             Start        End    Sectors   Size Type
/dev/nvme0n1p1      2048    1050623    1048576   512M EFI System
/dev/nvme0n1p2   1050624    1052671       2048     1M BIOS boot
/dev/nvme0n1p3 800995328 4000786431 3199791104   1.5T Linux filesystem [home partition]
/dev/nvme0n1p4   1052672  800995327  799942656 381.5G Linux filesystem [root partition]

Partition table entries are not in disk order.

```

Thanks in advance.

MrFred.

---

### Post by vidtek on 2019-12-28
Chroot:

This is what I use on a regular basis, boot from an usb stick with just the Ubuntu  UEFI .iso, Then:

in a terminal in live session make a password for root:

```
sudo passwd root
```

I usually just hit the spacebar twice-we do not care about security in a live recovery environment. 

Then:
```
blkid
```

That gives you details of your drives and partitions.

You then need to mount your o/s partition (call it sda5)  and your EFI partition (call it sda1)

```
mount /dev/sda5 /mnt
mount /dev/sda1 /mnt/boot/efi
mount --bind /dev /mnt/dev
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
chroot /mnt /bin/bash
```

You may or may not require the /bin/bash bit, depends on your system.

You are now in your chroot environment.

```
grub-install /dev/sda  #note no partition number
update-grub
```

if it finishes with no errors, exit the chroot (ctrl-d)
and unmount all previously mounted
```
umount /mnt/sys
umount /mnt/proc
umount /mnt/dev/pts
umount /mnt/dev
umount /mnt/boot/efi
umount /mnt
```

Sometimes you will be unable to unmount /mnt, don't worry just reboot anyway and you should be up and running.

Best of luck, Tony.

---

### Post by oldfred on 2019-12-28
I expect vidtek's full chroot to work, but just for info:

I think the install from inside your install did  not work then, as error was not finding ESP.
Normally fstab has an entry to mount the ESP.

this is mine but a SATA drive, but using UUIDs device would not matter.
```
# /boot/efi was on /dev/sda1 during installation
#UUID=FD76-E33D  /boot/efi       vfat    umask=0077      0       1
UUID=F626-A4D4  /boot/efi       vfat    defaults      0       1

```
```

fred@bionic-z97:~$ lsblk -f /dev/sda
NAME   FSTYPE LABEL   UUID                                 MOUNTPOINT
sda                                                        
&#9500;&#9472;sda1 vfat           F626-A4D4                            /boot/efi

```


I have two ESP mounts as I change 0077 to defaults. This may be not as secure. Before 14.04 Ubuntu used defaults, and Boot-Repair still changes it. You cannot edit or change settings in ESP with 0077 setting and I typically do another install and it overwrites my /EFI/ubuntu/grub and I have to manually edit it back to be my main working 18.04 install.

---

### Post by vidtek on 2019-12-28
> 
I have two ESP mounts as I change 0077 to defaults. This may be not as secure. Before 14.04 Ubuntu used defaults, and Boot-Repair still changes it. You cannot edit or change settings in ESP with 0077 setting and I typically do another install and it overwrites my /EFI/ubuntu/grub and I have to manually edit it back to be my main working 18.04 install.

Oldfred-

That's a neat trick, something I wish I had thought of months ago.  It just never occurred to me!:D  Thanks.

---

### Post by oldfred on 2019-12-28
I am debating going back to using 0077 as it probably is a security issue. Normal Linux partitions have ownership & permissions and prevent execute unless specifically allowed. But Windows formats only have settings based on mount, and defaults leaves it open.

Found I have to reboot to reset as just remounting from fstab, does not seem to reset. So as long as I am regularly having to edit grub in ESP, I like having that flexibility.

But then I have yet to implement UEFI Secure Boot on any system. They all are desktops, so a little less concern.

---

### Post by Mr Fredrick on 2019-12-28
This is the output from the various commands as I have run them:

```

ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p4 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p1 /mnt/boot/efi
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ chroot /mnt /bin/bash
chroot: cannot change root directory to '/mnt': Operation not permitted
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo apt purge grub grub-pc grub-common
sudo: unable to resolve host ubuntu: Name or service not known
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'grub' is not installed, so not removed
Package 'grub-common' is not installed, so not removed
Package 'grub-pc' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gir1.2-ges-1.0 libges-1.0-0 python-mysql.connector python-protobuf
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
root@ubuntu:/# sudo mv /boot/grub /boot/grub_backup
sudo: unable to resolve host ubuntu: Name or service not known
mv: cannot stat '/boot/grub': No such file or directory
root@ubuntu:/# sudo mkdir /boot/grub
sudo: unable to resolve host ubuntu: Name or service not known
root@ubuntu:/# sudo apt install grub-efi-amd64-signed
sudo: unable to resolve host ubuntu: Name or service not known
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ges-1.0 libges-1.0-0 python-mysql.connector python-protobuf
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  grub-common grub-efi-amd64 grub-efi-amd64-bin grub2-common os-prober
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed
  grub2-common os-prober
0 to upgrade, 6 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/3665 kB of archives.
After this operation, 28.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
Selecting previously unselected package grub-common.
(Reading database ... 277156 files and directories currently installed.)
Preparing to unpack .../0-grub-common_2.04-1ubuntu12.1_amd64.deb ...
Unpacking grub-common (2.04-1ubuntu12.1) ...
Selecting previously unselected package grub-efi-amd64-bin.
Preparing to unpack .../1-grub-efi-amd64-bin_2.04-1ubuntu12.1_amd64.deb 
...
Unpacking grub-efi-amd64-bin (2.04-1ubuntu12.1) ...
Selecting previously unselected package grub2-common.
Preparing to unpack .../2-grub2-common_2.04-1ubuntu12.1_amd64.deb ...
Unpacking grub2-common (2.04-1ubuntu12.1) ...
Selecting previously unselected package grub-efi-amd64.
Preparing to unpack .../3-grub-efi-amd64_2.04-1ubuntu12.1_amd64.deb ...
Unpacking grub-efi-amd64 (2.04-1ubuntu12.1) ...
Selecting previously unselected package grub-efi-amd64-signed.
Preparing to unpack .../4-grub-efi-amd64-signed_1.128.1+2.04-1ubuntu12.1
_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.128.1+2.04-1ubuntu12.1) ...
Selecting previously unselected package os-prober.
Preparing to unpack .../5-os-prober_1.74ubuntu2_amd64.deb ...
Unpacking os-prober (1.74ubuntu2) ...
Setting up grub-common (2.04-1ubuntu12.1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/grub-initrd-
fallback.service &#8594; /lib/systemd/system/grub-initrd-fallback.service.
Created symlink /etc/systemd/system/rescue.target.wants/grub-initrd-fall
back.service &#8594; /lib/systemd/system/grub-initrd-fallback.service.
Created symlink /etc/systemd/system/emergency.target.wants/grub-initrd-f
allback.service &#8594; /lib/systemd/system/grub-initrd-fallback.service.
update-rc.d: warning: start and stop actions are no longer supported; fa
lling back to defaults
Running in chroot, ignoring request.
Setting up os-prober (1.74ubuntu2) ...
Setting up grub-efi-amd64-bin (2.04-1ubuntu12.1) ...
Setting up grub2-common (2.04-1ubuntu12.1) ...
Setting up grub-efi-amd64 (2.04-1ubuntu12.1) ...

Creating config file /etc/default/grub with new version
Installing for x86_64-efi platform.
Installation finished. No error reported.
Setting up grub-efi-amd64-signed (1.128.1+2.04-1ubuntu12.1) ...
Installing for x86_64-efi platform.
Installation finished. No error reported.
Processing triggers for man-db (2.8.7-3) ...
Processing triggers for install-info (6.6.0.dfsg.1-2ubuntu2) ...
Processing triggers for systemd (242-7ubuntu3.2) ...
root@ubuntu:/# sudo grub-install /dev/nvme0n1 --uefi-secure-boot
sudo: unable to resolve host ubuntu: Name or service not known
Installing for x86_64-efi platform.
Installation finished. No error reported.
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu: Name or service not known
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-24-generic
Found initrd image: /boot/initrd.img-5.3.0-24-generic
Found linux image: /boot/vmlinuz-5.3.0-23-generic
Found initrd image: /boot/initrd.img-5.3.0-23-generic
Found linux image: /boot/vmlinuz-5.3.0-18-generic
Found initrd image: /boot/initrd.img-5.3.0-18-generic
grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
Adding boot menu entry for EFI firmware configuration
done
root@ubuntu:/# exit

```

I am still in the live USB environment and have yet to reboot. I'm putting this output here as a means of saving it somewhere.

MrFred

---

### Post by Mr Fredrick on 2019-12-28
NOTE: see my previous post, just above.

I have removed the live USB and rebooted, fingers crossed... .... ....., it REBOOTED, HOORAY!!

I then ran the following:
```

[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```

response:
```

UEFI mode
```

so I am now able to reboot AND to do so in UEFI mode, which is why I started this thread in the first place, so thanks **oldfred** and **vidtek**.

MrFred.

PS. I notice however that the /boot/efi folder is empty, should that be so?

---

### Post by oldfred on 2019-12-28
Not empty, you just do not have permission to see it. :)

Usually your fstab mounts the ESP with 0077 permissions which is no permissions at all.
Before 14.04 it used defaults, and if you run Boot-Repair it will change it to defaults. 
I think 0077, is for security reasons as FAT32 does not support any of the Linux ownership & permissions & may allow an executable or change in boot.

If you use live installer, you should see /EFI/ubuntu & /EFI/Boot in the ESP.

---

### Post by Mr Fredrick on 2019-12-28
Hi oldfred,

This is my /etc/fstab file, I added the /boot/efi line myself. Some posts on the internet forums advise that the last value be: "2", while others suggest: "1".
In your opinion, which is correct?

```

UUID=31AC-C2B5                            /boot/efi       vfat    0 2
UUID=9b451ec2-d2c7-42df-aac3-cd6840606448 /               ext4    errors=remount-ro 0       1
UUID=96ffb52d-b7e4-400b-9180-63ad09b88628 /home           ext4    nodev,nosuid     0     2
/swapfile                                 none            swap    sw              0       0
```

---

### Post by oldfred on 2019-12-28
Someone posted that now it does not matter with systemD.

From 
man fstab

>       The sixth field (fs_passno).
              This field is used by fsck(8) to determine the  order  in  which
              filesystem  checks  are  done at boot time.  The root filesystem
              should be specified with a fs_passno of  1.   Other  filesystems
              should  have  a fs_passno of 2.  Filesystems within a drive will
              be checked sequentially, but  filesystems  on  different  drives
              will  be  checked at the same time to utilize parallelism avail&#8208;
              able in the hardware.  Defaults to  zero  (don't  fsck)  if  not
              present.


---

### Post by vidtek on 2019-12-29
Mr Fred-  Glad it all works for you now.

Checkout @oldfred's signature for definitive info on booting, UEFI and partitioning problems.
He is the resident guru to whom we all defer!

Cheers, Tony.

---

