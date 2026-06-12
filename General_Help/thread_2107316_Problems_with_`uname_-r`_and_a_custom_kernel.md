---
title: "Problems with `uname -r` and a custom kernel"
date: 2013-01-21
forum: General Help
---

### Post by andersensam on 2013-01-21
Hey all, I'm currently running Ubuntu 12.10 with a custom kernel on my MacBook Pro 8-1. I compiled the custom kernel in order to use the EFI stub loader built into Linux 3.5+ as the stock kernel didn't offer it. Until about last week, everything was working fine and I was on Linux 3.6.8. After attempting to enable an IPv6 tunnel to HE I realized that I was missing a module and needed to enable it in the kernel config. By that time, kernel 3.7 was released as stable, so I decided to download the new sources and compile with the new modules. The compiling went smoothly and I install the new debs (both headers and image), then went to update my EFI partition. After rebooting, I attempted to load the module through ```
modprobe
``` and got an error that the SIT module couldn't be found. I was positive that I chose to enable it in the kernel config and went to my source directory to check it, and there it was. Since it wasn't loading, I decided to run ```
uname -a
``` which returned the information for the OLD kernel (3.6.8). Just to be sure that I didn't forget to update something, I reinstalled both debs, and ran ```
update-initramfs -c -k mykernel
``` just to be sure. After rebooting again, the old kernel information still shows up. What can I do?

---

### Post by Doug S on 2013-01-21
It is grub that decides which kernel to load, so maybe something is wrong there.
Maybe your kernel name is such that grub didn't know to load it by default.
Maybe grub was set to specifically load not the most recent or highest numbered kernel.
Maybe update-grub was not run after your kernel was installed.
If you re-boot, and get into the grub stuff, is your custom kernel one of the options to manually select and boot?

---

### Post by andersensam on 2013-01-21
> **Doug S said:**
> It is grub that decides which kernel to load, so maybe something is wrong there.
Maybe your kernel name is such that grub didn't know to load it by default.
Maybe grub was set to specifically load not the most recent or highest numbered kernel.
Maybe update-grub was not run after your kernel was installed.
If you re-boot, and get into the grub stuff, is your custom kernel one of the options to manually select and boot?

Thing is, I'm not using GRUB or LiLo at all, I'm loading the kernel through the EFI stub loader.

---

### Post by Doug S on 2013-01-21
> Thing is, I'm not using GRUB or LiLo at all, I'm loading the kernel through the EFI stub loader.I missed that, sorry.

---

### Post by andersensam on 2013-01-25
Deleted

---

### Post by andersensam on 2013-01-25
So, after looking through my files and verifying that all the kernel images and initrds were fine I realized my mistake: I forgot to bless the kernel when I put it on the EFI partition. The drive is HFS+ (as it's on a MacBook), so in order to set the boot properly, you need to "bless" the kernel. I found that the old kernel was actually running as I forgot to set the new kernel!

---

