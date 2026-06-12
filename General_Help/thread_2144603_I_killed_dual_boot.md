---
title: "I killed dual boot"
date: 2013-05-12
forum: General Help
---

### Post by jhford on 2013-05-12
First, I installed Raring, but then learned it would only be supported for 9 months. So, I opted for 12.04 LTS. I also thought my original Raring partition was too large. Here's my screwup. I booted 12.04 from a USB stick, loaded GParted and deleted the Ubuntu 64 GB partition, and installed 12.04.

My current partition setup is:
sda1 ntfs (Windows 7) 399.08 gb flagged as boot

sda3 is extended containing:
sda6 29.80 gb -- Ubuntu 12.04
unallocated 34.89 gb
sda5 linux-swap 1.99 gb
unallocated 1.02 mb

On boot, grub loads with a Windows 7 entry, but Window7 won't boot.

I have tried booting with the Windows 7 repair disk, but it can't locate the Windows 7 OS. Therefore, bootrec /fixmbr and bootrec /fixboot don't work.

Also, chkdsk /f fails.

Some help would be greatly appreciated. I don't really want to re-install Windows 7.

Thanks in advance.

---

### Post by oldfred on 2013-05-13
Boot-Repair cannot fix Windows issues, but may show us what the issue is.

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

