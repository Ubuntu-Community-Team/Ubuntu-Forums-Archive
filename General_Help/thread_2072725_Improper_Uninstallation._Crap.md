---
title: "Improper Uninstallation. Crap"
date: 2012-10-18
forum: General Help
---

### Post by theopfor on 2012-10-18
I feel that I'm always screwing things up... When I installed Ubuntu, I gave it half of my hard drive. So now I'm back using Windows because of Steam. My Windows partition got to only have 11 gigs left and I was only using 14 gigs in Ubuntu. After getting tired of gparted, not knowing if anything was working, I went into Windows to try to make the partition smaller, so I got mad and just deleted it. I used another program to add the empty space to the Windows partition. My computer restarts to do the action and grub gives me an error.

The way I understand the error is that grub can't find the Ubuntu files that allow me to choose which OS to use. All I have is a Ubuntu usb to work with. How do I uninstall grub?


Thanks ahead of time.

---

### Post by SlugSlug on 2012-10-18
If your getting rid of ubuntu and sticking with Windows you need to repair the MBR

It's different for XP and 7 so google which OS you have and fix mbr

---

### Post by oldfred on 2012-10-18
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

You can easily install this into the liveCD or download a full repairCD. It will prompt you to install a 'Windows like' boot loader that will work for you.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by theopfor on 2012-10-18
It works now! Thanks!!!

---

