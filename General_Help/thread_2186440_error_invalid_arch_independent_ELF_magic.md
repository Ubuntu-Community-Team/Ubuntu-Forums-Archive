---
title: "error: invalid arch independent ELF magic"
date: 2013-11-07
forum: General Help
---

### Post by goldstein2034 on 2013-11-07
Hi everyone, 

I have installed Ubuntu 12.04 in a new laptop at my work, and I have been trying the whole day to make it work... I will explain step by step the problems:

1) I installed Ubuntu 12.04 along side windows 7, already installed in the laptop. I didn't do (yet) windows recovery CD as I though there were not going to be any problems...

2) After the installation, Ubuntu worked perfectly, but I could not launch windows 7. The error was "error: invalid EFI file path".

3) I remember I had the same problems in another laptop, so I installed (inside Ubuntu) boot-repair and runned the "recommended repair". During this process, it asked in which drive to install grub, and I think I messed it up there. I selected the first option (I'm not sure which drive! I guessed that the "default" option would be the already selected one) and continued with the instalation.

4) Now I can't boot either in Ubuntu or Windows... it prompts "error: invalid arch independent ELF magic".

So, I have been searching and "playing" with "grub-install --boot-directory" and trying to understand the output of "sudo fdisk -l" but I have another problem... This laptop has a second hard disk (a small SSD, tipical in ultrabooks) of 32 Gb... and I don't know where the hell is Ubuntu installed... I don't know if Ubuntu default installation is intelligent enough to install the "/boot" inside the SSD and home folder in the normal HD... and I don't know where is grub installed now... the only think I know is that my bosses bought a new laptop and now is bricked... :P

I know that there is a LOT of info around, but I am afraid to worsen the problem even more... So I would be delighted if someone could help me...

Thank you!

---

### Post by oldfred on 2013-11-07
It sounds like you may have installed Ubuntu in BIOS/CSM/Legacy boot mode which would work, but then from grub menu you could not boot Windows as BIOS & UEFI are not compatible. Once you start to boot in one mode you cannot switch. But you can directly boot from UEFI/BIOS if you change boot mode to the same as your install. Not the easiest way to dual boot.

Error message is typical of incompatible versions of grub. Or newer install and old MBR or using MBR to try to boot efi install or vice-versa. 

Boot-REpair can convert a BIOS install of Ubuntu to UEFI by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI).

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

If you an Ultrabook with the small SSD, you need to see link in my signature. There are not just the install issues but dual video also. 
To get grub2 to install correctly you need to remove the Intel SRT RAID meta-data on drive before running Boot-Repair. That confuses grub as with RAID it installs differently but you really have to have a standard install into the efi partition.

From one of the links:
 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

If you are primarily a Windows user you probably want to re-enable the Intel SRT. But if not, many have just installed Ubuntu's / (root) to SSD to make Ubuntu fast. A couple of users have posted with larger SSDs that SRT only used part, so they did both.

---

### Post by goldstein2034 on 2013-11-08
Thank you so much for your answer!

I saved the link that boot-repair gives you for your log, so here it is:  [http://paste.ubuntu.com/6376670/](http://paste.ubuntu.com/6376670/)

I think I advanced a bit because I can already enter both windows and Ubuntu (yay!!) but in a very anoying way. At statup, I enter into de booting options, and these options appear:

- USB CD/DVD ROM Drive (UEFI)
- Ubuntu
- Root from EFI file
- USB CD/DVD ROM Drive - HL -DT -STDVDRAM GT51N
- Notebook Hard Drive

If I select "Notebook Hard Drive" my beloved grub appears, and it works perfectly (both Windows 7 and Ubuntu) so boot-repair did the job. I guess the only step missing is to set the "Notebook Hard Drive" option as default... but I don't know how to do that...

I didn't understand too well the dmraid part, but it appears ubuntu starts really fast so I think the installation did the trick. Once the grub is repaired I think I will be happy... :)

---

### Post by oldfred on 2013-11-08
Your Windows is installed in BIOS/CSM/Legacy boot mode, but HPs utilites all refer to .efi. So you must have an UEFI with CSM. Then the Ubuntu installer may boot in either UEFI mode or BIOS mode and it looks like you probably installed Ubuntu in UEFI mode. Boot-Repair then converted you back to BIOS mode?

There should be settings to select default boot, but not sure how it works with each type of system.

It also looks like this is an Ultrabook? That has the small (yours is 32GB) SSD which was for Intel SRT to make Windows 8 faster. Did Windows 7 get reinstalled in BIOS mode? 
But you installed Ubuntu to the SSD. 
While I use 25GB for all my / (root) partitions I then have large data partitions on my rotating hard drive. 
You should not hibernate Windows nor write directly into the Windows system partition normally. I suggest mounting it read only in fstab and create a shared NTFS data partition to use read/write for both systems.

---

### Post by goldstein2034 on 2013-11-11
I am really getting crazy with this problem... I tryed to restore the pc to fabric (using ****** windows recovery) and nothing was solved (memember guys... NEVER believe windows will solve your problems...).

Every time I restart my computer I need to enter bios & choose the boot, or the error will prompt (invalid arch independent ELF magic). I guess I need to select as default the hard disk where grub is installed... but I don't know how to do that, not even where is my grub... I know I'm not an experienced user and all... but this is an issue in repair-boot should really take into account...

---

### Post by oldfred on 2013-11-11
It now with UEFI depends on whether you are in UEFI mode or BIOS mode.

In BIOS mode Boot-Repair will normally automatically install the correct version of grub to all hard drives. Often better to uncheck auto repair and choose which system to install to which MBR if a multi-drive system.

In UEFI Boot-Repair will update the efi partition. But some UEFI have been modified by vendor to only boot Windows, so Boot-Repair may rename the Windows file to really be grub2's shim with the Microsoft signing key to get grub to boot. Then grub can boot Windows from its backed up name.

But in all cases it is a lot easier to dual boot if both systems are UEFI or both BIOS boot. You can boot from UEFI/BOIS but may have to turn on UEFI or CSM/BIOS to match install. Some auto switch. But you cannot dual boot from grub menu as once you start to boot in one mode you cannot switch.

Boot-Repair can fix most Ubuntu boot issues, but can only fix some minor Windows issues.
       Windows 8 UEFI fixes
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
Repair Windows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.ms-windows.info/Help/bootmgr-not-found-bootrec-rebuildbcd-17554.aspx](http://www.ms-windows.info/Help/bootmgr-not-found-bootrec-rebuildbcd-17554.aspx)

---

