---
title: "GRUB defaults line not resetting after installation"
date: 2024-04-27
forum: General Help
---

### Post by tryfan2k2 on 2024-04-27
I'm creating Ubuntu 24.04 images using packer.  My packer installation boot command is `linux /casper/vmlinuz --- autoinstall ds=nocloud-net;seedfrom=http://<ip>".  This works fine in 22.04, and my 24.04 image creates fine. 

When I create a VM from this image, the GRUB_CMDLINE_LINUX_DEFAULT line in 22.04 is just:
GRUB_CMDLINE_LINUX_DEFAULT="quiet"

In 24.04:
GRUB_CMDLINE_LINUX_DEFAULT="autoinstall ds=nocloud-net;seedfrom=http://<ip>"

I'm not sure what's happening here.  The line is not being set by subiquity?  It's using whatever it was initially booted with to populate that line?

Hoping someone can help shed some light on this.

---

