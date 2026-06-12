---
title: "[SOLVED] Error 15 after uninstalling VirtualBox and updating kernel"
date: 2008-06-06
forum: General Help
---

### Post by mrpeenut24 on 2008-06-06
PLEASE SOMEBODY HELP ME!!

I downloaded the VirtualBox .deb file from their website and installed it.  I decided I no longer needed it so I apt-get remove'd VirtualBox.  This uninstalled the program, but didn't unlink the vboxdrv from the kernel.  I kept getting messages about the module trying to load, but not being found.  I didn't think much about it, and I assumed that when I updated, a new minor kernel would realize it wasn't there and fix it. So today the 2.6.24-18 installed and I got this message: >                               /etc/init.d/dkms_autoinstaller: line 82: /var/lib/dkms/vboxdrv/1.6.0/source/dkms.conf: No such file or directory
vboxdrv (1.6.0): AUTOINSTALL not set in its dkms.conf.I didn't think much of it, just that it was trying to compile it back into the kernel again. No big deal, it just won't load. WRONG! Now whenever I try to boot, it gives me
>  Error 15: File not foundI tried to boot with the older kernel, and it gives me the same error. I've reinstalled grub, but no success. I'm not sure how it could have messed up the older kernel, but I don't know how to recompile it if I can't boot into it.

Someone PLEASE help me!  As of now, my laptop is a paperweight (by which I mean XP only).

---

### Post by mrpeenut24 on 2008-06-06
*Smacks forehead*

I'm not sure how it happened, but I overlooked it, and apparently, SuperGrub didn't catch it.  Somehow, all of the entries in my menu.lst file were changed to (hd0,1) instead of (hd0,0).  I've got my home partition resting there, so I wouldn't have done it.  And there's nothing bootable there, so I don't know why it happened, but apparently, when the newer kernel installed, it changed the menu.lst file to show that *all* of my kernel images were located there.

Anyway it's fixed now, sorry to bother people, and I thought I'd post this in case anyone else had the same problem (also, so no one worried about me ;-)).

---

