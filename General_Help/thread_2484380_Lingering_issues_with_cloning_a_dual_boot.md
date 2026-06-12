---
title: "Lingering issues with cloning a dual boot"
date: 2023-02-24
forum: General Help
---

### Post by JustSomeCanuck on 2023-02-24
I made a post about this last week, but it looks like I need some more specific advice. I have a computer with a 1 TB HDD with a dual boot of Windows 10 and Ubuntu 22.04. I'm trying to move both OSes to a 1 TB SSD. All of my important data and programs are backed up, and I'm planning to use the HDD for general data storage after everything is on the SSD. The HDD is divided equally between Windows and Ubuntu.

I've figured out that the best way to go about this is to clone the Windows partitions, do a fresh install of Ubuntu on the SSD, and then restore my data as needed from the backup. I'm able to do all of this, but I can't seem to get both Ubuntu and Windows running easily. Boot Repair doesn't seem to help.

The Windows 10 was upgraded from Windows 7, and it seems to be running in Legacy BIOS mode even though the computer has UEFI.

I'm certain that I am close to getting this to work. These are my two main concerns:

1) Does the SSD have to be in MBR mode, GPT mode, or does it matter? It's currently in GPT mode, because it seemed I had to do that to set up the required number of partitions.

2) Do I have to run the Ubuntu live USB in Legacy mode because of the Windows installation? I've looked into this myself and it seems the answer is yes, but I want that confirmed.

At the moment, I can open Ubuntu on the SSD with no issues, but selecting Windows just returns me to the GRUB menu. I can provide results from terminal commands or details about the partitions if needed.

---

### Post by oldfred on 2023-02-24
A few Windows 7 systems were UEFI, most were BIOS boot.
Windows only boots in BIOS mode from MBR(msdos)
Windows only boots in UEFI mode from gpt partitioned drives and has a lot more partitions.

Ubuntu will boot in either mode from either type of partitions. But if on same drive as Windows needs to be in same boot mode.
If Ubuntu on its own drive, best to use gpt whether UEFI or BIOS, but booting is easier if mode is same as Windows. 

If hardware is UEFI, as all systems in last 10 years are, best to use UEFI boot on gpt drives for all systems.

If Ubuntu on gpt drive in BIOS mode, you need a bios_grub partition. If UEFI boot mode, you need an ESP on what ever drive system sees as first drive. When first starting conversion from old BIOS system to new UEFI system I had both ESP & bios_grub on almost every drive.

If you post link to summary report from Boot-Repair we can see the details of your install.

---

### Post by JustSomeCanuck on 2023-02-24
Thanks for the quick reply.

Sounds like I need the SSD set up as MBR, then install Ubuntu in legacy mode. That's how the HDD is configured for the dual boot, and it works fine (just at HDD speed). I think my mistake was booting the live USB in UEFI mode.

I do have this Boot Repair report, but it's from when I returned the computer to running off the HDD (only because that works, and the computer was needed), so I'm not sure how helpful it is: [https://paste.ubuntu.com/p/DSvgTYyzb5/](https://paste.ubuntu.com/p/DSvgTYyzb5/)

Before that, Boot Repair was warning me that I needed to switch the boot from Legacy to UEFI, so I didn't run it.

I'm hoping the limited number of partitions won't be an issue. It did work on the HDD when I first set up the dual boot, after all.

---

### Post by tea for one on 2023-02-24
I don't think that my suggestion will be exactly what you want to read but nevertheless:-

Reinstall both Windows 10 and Ubuntu in UEFI mode with GPT
This will be more robust for the future
It eliminates extended partitions
It allows emergency booting from EFI shell
You can install rEFInd boot manager - an elegant tool to aid booting either OS

---

### Post by oldfred on 2023-02-24
I agree with tea for one's suggestion as now would be a good time to convert to UEFI boot for all systems.

At minimum use gpt for Ubuntu only drive and add both an ESP - efi system partition as FAT32 and a tiny 1MB unformatted partition with bios_grub flag for BIOS boot. Then drive can easily be converted from BIOS to UEFI. For Linux the only difference between UEFI & BIOS is the version of grub and a few settings it changes when installing grub. So if you have both gpt supporting partitions, it can be easy to convert.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[gpt Advantages]([http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

Also if staying with BIOS, install Windows boot loader to Windows drive and grub to Ubuntu drive.
Grub only boots working Windows and sometimes you have to directly boot Windows from UEFI/BIOS boot menu. Easy to do with UEFI as you have both boot loaders in the ESP (or you can have an ESP on every drive).

---

### Post by JustSomeCanuck on 2023-02-26
Last question, if anyone can answer it: for using Windows when I need it, as long as I select it on the SSD from GRUB it will boot off of the SSD? Or do I need to change a setting in Windows for that?

As I said above, I will be setting up the HDD to be simple storage when I'm sure everything is working from the SSD.

---

### Post by DuckHook on 2023-02-26
I know I'm not really answering your question and what follows is something of an evangelical exercise for me, but with that fair warning out of the way:

I don't know why more Linux users don't nuke their Windows partition altogether and just run Windows in a VM.

This forum is filled with people running into obscure, arcane problems because they dual boot and MS keeps adding more junk that cripples bootloaders, prevents updates, etc. By hiving off Windows into its own VM and leaving the host to Linux alone, you not only get a more secure host, but a simpler setup that avoids so much complexity. Windows cannot screw up your host when it is confined to its own scruffy little virtual corner where it can play king&#8209;of&#8209;the&#8209;hill all it wants.

Moreover, VMs allow Windows to be snapshotted and rolled back&#8212;invaluable features that have saved my bacon a number of times, especially when it comes to something as finicky, fussy and unforgiving as Windows.

If you are a gamer who must have physical access to the HW, then all bets are off. You are stuck with dual boot. But for everyone else, the VM solution is more elegant, stress&#8209;free and trouble&#8209;free.

/rant.

---

### Post by jeremy31 on 2023-02-26
I just use a USB HDD enclosure and run clonezilla ISO on flash drive to clone from one drive to the other.  I have done it 3 times in the past couple years and haven't had any problems but it does make an exact copy of the drive contents so booting again with both the HDD and SSD connected could cause boot issues with grub but I never tried that to confirm.  Just make sure you select the correct source and destination devices when running clonezilla.

You could likely run clonezilla from an Ubuntu ISO on USB and accomplish the same

---

### Post by JustSomeCanuck on 2023-02-26
I fully expect this is the last version of Windows I'll be using, and sometime in the not-too-distant future I will have completely switched over to Linux, so this arrangement only needs to last a few more years. Probably until it's time to upgrade the ol' beast :)

---

