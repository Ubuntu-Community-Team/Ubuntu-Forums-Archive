---
title: "How did Linux get on sdc when I insalled it on sdb"
date: 2013-05-19
forum: General Help
---

### Post by LCBradley3k on 2013-05-19
[COLOR=#000000][FONT=Arial]I typed $fdisk -l into the terminal to see my partitions.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]When I installed Linux I installed it on sdb, which shows up, but for some reason it says Linux under sdc.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]This is what it looks like.[/FONT][/COLOR]

[IMG]http://i.imgur.com/YOEBzIg.png[/IMG]

Now sdc:
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][IMG]http://i.imgur.com/nztl3GB.png[/IMG][COLOR=#000000][FONT=Arial]

The reason I'm digging into this is because I'm trying to get my Linux Mint option in my Windows boot manager to work. Currently it just says "Windows failed to start", when I click on my Linux in the boot manager.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Although I can still get Linux to run, because when my external Hard Drive is plugged in with Linux on it, and I click on Windows 7 in the boot manager, it runs Linux.[/FONT][/COLOR]

---

### Post by oldfred on 2013-05-19
Sometimes when you plug a flash drive in, it becomes sda or sdb and hard drives get moved to other names. It is why they now use UUIDs as drives may change device numbering.

But you sdb partition does not look correct. That looks more like random data in the MBR partition table that fdisk is trying to convert to a partition table list?

Is sdb a MBR(msdos) partitioned drive or perhaps something else like gpt, or dynamic partitions in Windows?

---

### Post by CatKiller on 2013-05-19
You don't even have to plug anything in for the assignments to change; it's just whichever drive happens to spin up first and claim the earlier name.

UUIDs are a much better prospect.

---

### Post by LCBradley3k on 2013-05-19
> **oldfred said:**
> Sometimes when you plug a flash drive in, it becomes sda or sdb and hard drives get moved to other names. It is why they now use UUIDs as drives may change device numbering.

But you sdb partition does not look correct. That looks more like random data in the MBR partition table that fdisk is trying to convert to a partition table list?

Is sdb a MBR(msdos) partitioned drive or perhaps something else like gpt, or dynamic partitions in Windows?
That was the problem, I did have a flash drive in.

sdb is where I installed Linux Mint to originally.

I've been having trouble booting from it in my Windows Boot Manager. I have Linux on an external hard drive.

When the HDD is plugged in and I click on "Windows 7" in the boot manager, it loads Linux.
When the HDD is not plugged in and I click on "Windows 7", it loads Windows 7.

I made a Linux option using EasyBCD in Windows, but it doesn't work. It just says Windows failed to start

It says there is a problem with AutoNeoGrub0.mrb.

Any idea on how I could fix this?

---

### Post by oldfred on 2013-05-19
I do not know EasyBCD. It uses grub4dos to chain load to another grub installed. Usually you have to have grub in a PBR - partition boot sector to make it work. And grub2 does not work well in a PBR. But if you have another hard drive you have another MBR. You really should not need EasyBCD then. Leave Windows boot loader on the Windows drive and grub on the Ubuntu drive.

       [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

If you want to know what is where and possibly fix grub.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

