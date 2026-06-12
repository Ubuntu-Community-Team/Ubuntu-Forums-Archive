---
title: "Ubuntu with laptop &amp; RAID pci/Optane"
date: 2020-02-28
forum: General Help
---

### Post by box02-0 on 2020-02-28
Hi.

I have a Dell 7791 Laptop which has a 512gb PCI nvme drive that works in conjunction with Intel Optane 32gb caching. It appears that if I want to use this pci/optane combo, I must be in RAID. In this context, RAID mode just means that the Intel Rapid Storage controller is active; not a true multi drive RAID.

I&#8217;ve partitioned an EXT4 partition on the laptop, ready for Ubuntu. I&#8217;ve built an 18.04 ISO USB from my Desktop.

I have been told that Ubuntu will not work in a RAID setup, even though this isn&#8217;t really RAID. Before I try to boot the ISO on the Laptop, is there anything I should be doing?


I would like to add a 1TB SATA SSD to the laptop and install Ubuntu on it? Would I then be able to boot either from the Windows PCI  or  the Ubuntu SATA? Or would that blasted RAID flag still get in the way?

The laptop is for my wife. I don&#8217;t have any use for Windows, but I am trying to encourage her to migrate to Ubuntu, and the dual boot option is the only way she will do so.

Any help will be greatly appreciated.

Thanks,
M...

---

### Post by box02-0 on 2020-02-29
Anyone?

---

### Post by CelticWarrior on 2020-02-29
First thing you should do is to run a live session and check whether or not all the storage devices are recognized.
It may not due to Intel RST not having support in Linux but, if I'm not mistaken or confused, I remember someone here not complaining about that problem in a similar configuration.

So...
If all the drives are recognized or at least the 512GB NVME (ideally the Optane part shouldn't be user accessible and work only for the same purpose as in Windows) you're good to go.
If not, it means you need to change the mode to AHCI (and before that install AHCI support in Windows) if you want to install the dual-boot.

This is the only consideration so, when you ask about > Would I then be able to boot either from the Windows PCI  or  the Ubuntu SATA? it makes no sense and it shows you aren't familiar with UEFI and how it boots: It always boots from the ESP (EFI System Partition) that is already present and includes entries for Windows and eventually special boot modes and/or diagnostic and recovery environments. This will be used for Ubuntu as well irrespective of where Ubuntu is installed, one or more drives/partitions is irrelevant.

Yes, you'll be able to boot both Ubuntu and Windows from Grub, as long as you can install Ubuntu.

---

### Post by box02-0 on 2020-03-01
Hi.

Are you saying I always have to boot from the pci/optane drive?

My understanding is that hitting F12 on booting allows to boot from another drive? So if I have an internal 2nd drive, like my bootable Ubuntu, I would never be able to boot from it?

Would I ever be able to boot from an external sata drive plugged in thru the USBC port?

If not, then what is the point of changing the boot sequence via F12?

I am really confused.

Thanks,
M...

---

### Post by oldfred on 2020-03-01
Intel Optane - See Intel response that no performance difference between RAID & AHCI.
[https://communities.intel.com/thread/121155](https://communities.intel.com/thread/121155)
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)

Dell 7791 UEFI update & some settings
[https://ubuntuforums.org/showthread.php?t=2431450&page=3](https://ubuntuforums.org/showthread.php?t=2431450&page=3)

If you install the AHCI drivers into Windows you can use AHCI for both Windows & Ubuntu.
Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation](https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation) & 
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)
AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)

---

### Post by CelticWarrior on 2020-03-01
You want to boot Operating Systems - Ubuntu or Windows -, not "drives" :P and in any case it would be partitions...

Your line of thinking has been carried over from the time computers had BIOS and drives used MBR ("msdos") partitioning type. Even then not entirely applicable although there were indeed advantages in having different bootloaders in different drives for dual-boot.
You need to understand the different boot processes of BIOS vs. UEFI.

Until recently, there were only BIOS/MBR.
In those systems BIOS starts, does POST, reads the bootloader in the MBR of the drive set as the primary boot device (failing that it will try others in order if available). That bootloader "points" to a system partition from where all the remaining boot process and OS loading takes place. 
Only one bootloader can be installed in the MBR so, when installing a dual-boot, Grub would be installed instead of the Windows bootloader (we can't use that because it only boots itself or other Windows if present) and would boot both Ubuntu and Windows.  
So, with a single drive, we would necessarily work with Grub only. If for some reason Grub failed (e.g. Ubuntu has been deleted) we wouldn't be able to boot Windows either unless we reinstalled the original Windows bootloader booting from Windows media into the recovery/repair environment.
With two or more drives we could keep the Windows bootloader intact. We would simply change the boot drive order to another one where we would install Ubuntu and that drive only would have Grub installed, with the ability of booting Ubuntu and Windows in other drive. Pleased note, we would always be booting *from* the boot drive's MBR into both OSes regardless of where they were installed, using Grub. But because we left the Windows bootloader intact in the original boot drive we could easily change back to that one in BIOS and boot Windows directly.
So, even with BIOS/MBR, the boot process doesn't necessarily starts in the same physical drive where the OS we were booting was installed (and both Windows and Ubuntu installations can have partitions in multiple drives) and that's why I say your reasoning is applicable to old BIOS/MBR machines but only partially, you're focusing too much in physical drives.

[CENTER][B]
== Most of the stuff above isn't applicable to UEFI ==

[/B][/CENTER]
... and you have UEFI and, because you also have a NVME drive, the Legacy/CSM route isn't an option for you (you don't want that anyway). **In your case all OSes must be installed in UEFI mode**.

How is it different? 
For starters, bootloaders are no longer limited to the very small space of the MBR - with any modern OS in BIOS/Legacy (and MBR) only the first stage of the boot process happened in MBR, everything else would have been read from /boot if using Grub or the Windows system partition if using the Windows bootloader) -, bootloaders are enow saved in the ESP - EFI System Partition -, a small FAT32 partition labelled "EFI" and different ones can co-exist peacefully, which is a huge advantage and brilliant.
So, now the boot process goes like this: UEFI starts, does post, reads bootloders from the ESP and finally releases control to the OS set as default. Again, and more than ever, where the OSes are actually installed isn't relevant, the boot process is always started in the EFI partition and then the selected bootloader does its thing.
Typically we'll use Grub as before which in turn can boot Ubuntu or chainload to the Windows EFI bootloader which in turn boots Windows. But now, even with a single drive, we are just a UEFI setting change away from booting Windows directly with the ability to change back to "Ubuntu" (which is Grub and can boot Ubuntu and Windows). Many UEFIs conveniently allow overriding the configured boot with a one time boot menu (F12 in yours). Very useful to boot installation media.

More information about UEFI and dual-booting: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

With all this I hope it's clear why I said you're thinking it wrong. Your system requires additional steps in preparation for installing Ubuntu. Again, you need to make sure the drive where the EFI partition resides is "visible" in the Ubuntu live session (booting from a USB stick) but this really isn't related to the UEFI boot process and requirements commented above, it's a specific situation of your computer. If not visible then yes, you'll have to change the mode to AHCI (and the Optane drive will probably show up as usable too but the caching feature will be lost. Before doing it you must install AHCI support in Windows or it won't boot in AHCI mode; also disable Fast Startup - i suggest you google both - in Windows and Fast Boot in UEFI. Disabling Fast Startup and Fast Boot should be done irrespective of the RAID/AHCI situation, to be clear. 

Why is it important for the Ubuntu installer to "see" the original drive correctly? Because otherwise you won't be able to setup a proper dual-boot, you would be limited to the UEFI settings to select Windows or Ubuntu and in order to do that you'd need to change two settings in UEFI each time you want to change OSes. Without the original drive "visible" to the installer it will install the bootloader to a new EFI partition in the only drive visible, the added 1TB SATA drive. It works to boot Ubuntu only and that is if you change the boot drive priority in UEFI and then - a different setting - select "Ubuntu" as the default OS (it will be the only one because UEFI is reading the EFI partition in the new drive and that one contains entries to Ubuntu only). If you want to boot Windows you'd have to do the reverse, change the boot drive priority back to the original internal NVME drive (it will boot Windows only because that's all it has, the Ubuntu EFI bootloader was installed elsewhere). This is really very far from ideal.

So, the proper way is to have the Ubuntu EFI bootloader installed in the same EFI Windows is (we already know they can co-exist, two or more, by design), keep the exact same boot drive priority and, in a different setting, select "Ubuntu" instead of "Windows bootloader manager" (the installer itself should change this setting but sometimes it doesn't so we have to do it manually). Again, this will boot Grub first allowing you to select either Ubuntu or Windows (and at any time it can be changed back to "Windows" resulting in booting Windows directly, UEFI is so much more convenient).
You may or may not need to do manual partitioning (the "something else..." option in the installer). Usually not if you're just adding a new blank drive, the "Install alongside..." option should a) pick the unallocated space in the added drive and partition it automatically, for your convenience (nowadays it will take all the space in a single / (root) partition) and b) detect the existing EFI in the original drive and install the bootloader there. You can, of course and as mentioned, do a different manual partitioning like with a separated /home, etc. but in that case you must also select the EFI partition (in "something else") to use and with EFI type (it won't give an option to format and you wouldn't want that obviously) along with all your other partitions for Ubuntu.

In summary, dual-booting in your computer isn't easy or trivial but not that hard either, as long as you prepare it correctly before installing Ubuntu. And also strongly recommended by our resident expert @oldfred , UEFI update -and- firmware update (if available) for all the SSDs involved and particularly for the NVME, before anything else, from Windows which also benefits from this updates. And, I'm afraid it may have other peculiarities I'm unaware of, but at least the basics are covered, I hope, in this much larger than usual post.

---

### Post by box02-0 on 2020-03-01
Thank you so much for that very informative post.
M.....

---

