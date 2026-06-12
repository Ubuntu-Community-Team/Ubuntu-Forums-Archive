---
title: "Ubuntu 12.10 Not Booting - Stops at &quot;loading initial ramdisk&quot;"
date: 2013-04-08
forum: General Help
---

### Post by Sam Flo on 2013-04-08
I've been dual-booting Ubuntu 12.10 and Windows 8 on my machine.

This morning I selected Ubuntu in GRUB, the menu disappeared and nothing happened.

So I thought I'd go into recovery mode and fix whatever was preventing the OS from booting. However, the boot just stops at "loading initial ramdisk" and sits there with a blinking underscore.

What confounds the mind is that, to my knowledge, I've done *nothing* that should affect the ability of the OS to boot. Everything worked perfectly last night. I haven't installed anything in weeks, I haven't messed with any drivers, and I haven't done anything particularly exotic while in Ubuntu. I pretty much exclusively use the OS to do assignments in a Data Structures course I'm taking, which really only involves creating and running .c files and extensive use of valgrind.

I'm pretty unfamiliar with GRUB, so if there's some sort of script or report I'm supposed to provide, then point it out and I'll be happy to get it.

Thanks in advance,
[INDENT]~Sam Flo[/INDENT]

---

### Post by oldfred on 2013-04-08
BIOS install or UEFI install? May be best to see details. Or if minor fixes this can automatically do them.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

