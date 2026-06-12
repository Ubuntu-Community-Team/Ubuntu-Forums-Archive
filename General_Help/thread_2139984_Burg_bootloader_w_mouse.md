---
title: "Burg bootloader w/ mouse"
date: 2013-04-28
forum: General Help
---

### Post by PaperProjects on 2013-04-28
I know that the new Windows 8 bootloader has mouse support, but that bootloader also requires that fast bootup is enabled, which I do NOT want. However, the old Legacy Windows bootloader is incredibly ugly, so I thought I might switch back to Burg. Point is, I want to have mouse control in burg, not that it's actually needed, but I just want to know if it's possible (Yes I know you can use the arrows to control burg). So, I want to either be able to use the new nice looking Windows 8 bootloader WITHOUT fast bootup setting, or have burg with mouse.

Details (may or may not matter):
Computer: Satellite-C855 Laptop
Dual-Booted OS: Windows 8 Enterprise x64, Ubuntu 13.04 amd64
Machine: 64-bit with EFI support.

---

### Post by oldfred on 2013-04-28
I do not think burg even knows about UEFI. It has not been supported for several years. I think last update was 2010?

I know grub is not pretty, but I prefer function.

But some do use EasyBCD to convert Windows to allow it to boot Ubuntu. Windows does not support booting anything other than Windows.

There also are other Boot Managers that are designed for UEFI like Refit and Refind. I think they may have started with the Mac UEFI, but work with any UEFI.

Note that a Boot Manager is not a Boot Loader. It is just a front end and you still need a boot loader.
 Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by PaperProjects on 2013-04-28
I believe burg already has some sort of EFI support refer to googlecode: [https://aur.archlinux.org/packages/burg-efi-x86_64-bzr/](https://aur.archlinux.org/packages/burg-efi-x86_64-bzr/)
So is it possible to add mouse to burg?

---

### Post by oldfred on 2013-04-29
did you see the comment. It is orphaned. 

So unless developer had already added any features you want, you would have to download source and develop changes yourself.

---

### Post by PaperProjects on 2013-04-29
Alright, I give up. I'll mark it as [SOLVED] but if anyone has anything on this topic, please post here.

---

