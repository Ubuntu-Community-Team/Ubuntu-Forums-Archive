---
title: "Reinstalling Ubuntu on Dual Boot machine"
date: 2018-04-30
forum: General Help
---

### Post by kramericalight on 2018-04-30
Hi all,

Before I do anything foolish I want to take a chance to see if what I am doing is correct.

My current set up is:

1) Ubuntu 18.04 (unusable) on one SSD
2) Windows 7 Ultimate on a separate SSD
3) Two HHDs in raid 1 mirror configuration as a storage for files between the two OS
4) Grub2 as the bootloader

I am going to attempt to reinstall Ubuntu 18.04 using a bootable USB, by overwriting the SSD with Ubuntu. However, I am concerned that by doing this I am going to overwrite the grub2 file, fstab and possibly mess something up making my other drives inacessible. I do not want to lose my data on the other two drives.

I assume I can just reconfigure the grub2 and fstab files after reinstalling Ubuntu, but I am just nervous.


Can someone either tell me what I am doing is kosher before I make a bad situation worse or give/point me to some directions for a similar setup as mine.

Thanks!


Edit
_________________________________________________________________________________________

So after setting the boot order to the bootable USB I created with Ubuntu 18.04. It immediately found the existing Ubuntu and I chose to "Erase Ubuntu 18.04 LTS and reinstall" and it worked its magic and now I am back up running.

Ubuntu has come a long ways with automating to make things more user friendly.

---

### Post by yancek on 2018-04-30
So what's the problem, the install on the SSD of 18.04 doesn't boot?  Are you using the Grub bootloader to boot windows or do you have windows code in the MBR of its Disk?   Is your windows 7 a Legacy install using MBR, that was the default.  Is your Ubuntu install Legacy?  If it was installed UEFI, there is a problem.

Yes reinstalling Ubuntu and Grub will overwrite the files you mention.  You could copy them to a CD/DVD or flash drive.  Can't really tell you any more without more info like what you can boot and how you boot?

---

### Post by kramericalight on 2018-04-30
Yeah I upgraded Ubuntu from 17.10 to 18.04, and cannot get it to boot into GUI. The furthest I was able to achieve is the login screen through grub recovery. and I believe it has something to do with my Xorg.config settings and the fact that I was using AMDGPU-Pro and had to delete it to upgrade.

I am using the Grub2 bootloader. I do remember originally installing 16.04 and having an issue with the efi vs uefi. Looking at my windows boot environment right now in **C:\Windows\Panther\setupact.log[COLOR=#000000][FONT=Arial].[/FONT][/COLOR]** it shows EFI for the "Detected boot environment." 

This had not been an issue for 16.04, 17.04, or 17.10 when I had upgraded the distros, so I am not sure why it would have changed with 18.04.

To double check if Ubuntu get installed as UEFI instead of EFI would this create an issue? Neither are in legacy BIOS.

---

### Post by oldfred on 2018-05-01
UEFI is EFI. Just the newer version. 
It was EFI v1 and used with Intel based Mac, but with some v2 features.
Once updated to v2 (released in 2006) it became UEFI and was the version ( prob 2.3) used with Windows starting about 2012. It is currently version 2.5.

What can be different is whether you boot install media in BIOS boot mode or UEFI boot mode. And then how you boot install media is how it installs. And best to be consistent.

Always good idea to run this when system is working just to document boot configuration. And run some other commands to document what is installed.
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by kramericalight on 2018-05-01
oldfred,

Thank you for your clarifications on EFI vs UEFI.

Below is the link as requested:

[http://paste.ubuntu.com/p/NPxthP5yNT/](http://paste.ubuntu.com/p/NPxthP5yNT/)

Let me know if there is anything to be concerned with. Everything seems to be working fine as of right now.

Thanks!

---

### Post by oldfred on 2018-05-02
It looks like you have installed Ubuntu in both BIOS & UEFI boot mode on a gpt partitioned drive.
With gpt and BIOS boot, you need a bios_grub partition which is 1 or 2MB unformatted with BIOS grub. Then the install of grub to MBR, will use bios_grub for core.img which normally with MBR partitioning is in the sectors just after the MBR but before first partition. That space does not exist with gpt.

Not sure about your Windows. You have Windows boot loaders in MBR, but sdb is now gpt. And Windows is not showing any of the typical UEFI partitions. It looks more like a BIOS/MBR configuration. If you converted drive to gpt you have to reinstall Windows in UEFI mode.
Windows only boots with BIOS from MBR and only with UEFI from gpt.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

It looks like you need to convert Windows drive back to MBR & run Windows repairs if needed.
Ubuntu is currently in UEFI boot mode as you mount ESP in fstab. But if you want to dual boot from grub and Windows is BIOS boot, then you must repair Ubuntu boot.
Create a bios_grub partition on sda and reinstall grub in BIOS boot mode. 

How you boot install media, UEFI or BIOS is how it installs or repairs your installs. UEFI & BIOS are not compatible, once you start booting in one mode you cannot switch. If systems not in same boot mode you can only dual boot from UEFI menu. And then grub cannot boot any other installs not in same boot mode it is in.
 
There are some advantages to gpt. I have all drives as gpt now, but many have both an ESP for UEFI boot and a bios_grub for BIOS boot. So I could reconfigure a drive for either UEFI or BIOS bot.   Very new ones only have ESP as all my working systems are UEFI. 

      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

