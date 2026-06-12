---
title: "Using GRUB for Windows? Further details in post"
date: 2013-08-05
forum: General Help
---

### Post by peter16 on 2013-08-05
Hello!

I've been trying to install Windows using one of my harddrives as a temporary placeholder for the Windows installation files (I booted the harddrive and installed it that way). However, Windows only seems to want to install the bootloader into the harddrive with the installation files, and not the harddrive with the actual operating system. I intend to re-format the temporary harddrive when the installation is done, so having the bootloader there isn't really optimal.

I've tried to repair it using the Windows repair tool, but it didn't work. Is it possible to use GRUB solely for Windows? Right now I'm on a Ubuntu live cd, but I can't for the life of me find out how to actually use GRUB.

Last time I installed GRUB manually was years ago when I was dealing with Arch Linux, but I assume things work differently with Windows. If I recall correctly, you needed an actual partition for /boot, how would this look in Windows, and should this partition be NTFS as the Windows partition?

Please help!

Thanks in advance, Peter.

---

### Post by NikTh on 2013-08-05
Windows cannot boot without their own bootloader (I think). When you see a custom entry in GRUB, this entry is just a chain-loader to Windows bootloader. Grub points to Windows bootloader and from there, Windows bootloader "taking office". Although these are only my knowledges, someone with more knowledges than mine, might give you a hack or something.

---

### Post by oldfred on 2013-08-05
Windows normally installs its boot loader to the drive set as boot from BIOS. And with Windows 7 it will put its hidden 100MB boot/repair partition on the drive set as boot in BIOS even if install is to another drive. So just set BIOS before installing or repairing Windows and it should put its boot loader in the MBR of that drive.

I have booted my Windows 7 repair flash drive with grub. All I did was install grub to the Windows NTFS partition making sure that /boot/grub was the same as Boot/BCD (in Linux both lowercase or both uppercase ) as normally they would be two different folders in Linux but in Windows case is not important and duplicates are not allowed.

You can just install the Lilo boot loader. Lilo works just like Windows in that it has more boot code in the PBR -- partition boot sector. The MBR just looks for partition with boot flag and jumps to the PBR. If you install just the Lilo boot loader it will directly boot Windows.

       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

---

### Post by peter16 on 2013-08-05
Thank you for your help.


> **oldfred said:**
> 
sudo lilo -M /dev/sda mbr

I tried this, and when I try to boot Windows, I get an error saying that the bootmgr is missing.

---

### Post by oldfred on 2013-08-05
If your Windows is not on sda, then it will not work. Or you do not have the boot flag on the NTFS partition.

Windows boots from MBR to PBR of active (boot flag) NTFS partition and PBR specifies bootmgr in the NTFS partition.
Details here. Is for Vista but 7 & 8 (in BIOS mode) are the same.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by peter16 on 2013-08-05
Of course, I verified which harddrive to use with fdisk before actually running lilo (it just so happened to be sda this time). I activaged the boot flag with gparted before installing Windows, and I assume BIOS has the correct harddrive since that's the harddrive that is being booted. However; the other harddrive also has the boot flag activated, otherwise I won't be able to boot it and install Windows; but this also applies to USB sticks, so I highly doubt that could be the problem. But for some reason, it still puts the bootloader on the wrong harddrive.

I'm also fairly certain that I've done this before, and succeeded.

Thank you.

---

### Post by peter16 on 2013-08-05
A slight update, it may be relevant.

When I installed lilo, it told me that it was important to run liloconfig before running lilo. Doing so resulted in this error message:
> $ sudo liloconfig
E: cannot use uncommon overlayfs found as root device!


I tried to run lilo anyway, which resulted in this:
> $ sudo lilo -M /dev/sdf mbr
Backup copy of /dev/sdf in /boot/boot.0850
The Master Boot Record of  /dev/sdf  has been updated.

Thank you.

---

### Post by oldfred on 2013-08-05
Lilo is a full boot loader and you do not want to install it as it will overwrite the Windows boot code in the Windows PBR. You just want the boot loader part that is in the MBR.

May be best to see all the details:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

