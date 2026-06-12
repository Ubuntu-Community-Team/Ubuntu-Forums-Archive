---
title: "what could have made the keyboard not responding?"
date: 2013-01-27
forum: General Help
---

### Post by freemant on 2013-01-27
Hi,

I am using Ubuntu 12.10 and it has been working fine. However, after install vmware workstation 9.01 and removing (by mistake) and installing the kernel again, it fails to boot. The last message displayed is "Detecting battery state...". The USB keyboard also stops working (including Ctrl-Alt-F1 and Ctrl-Alt-Del).

I've tried booting from the liveCD and installing an older kernel, updating grub2, reconfiguring udev, installing nvidia-current (which should have nothing to do as my computer uses the Intel chipset on the motherboard) and disabling the vmware services, but none has any effect on the boot.

Even single mode fails to boot. The last message is "Begin running /scripts/init-bottom".

I can dual boot into Kubuntu 12.04 and it works perfectly fine. So this is not a hardware problem.

Any idea on how to troubleshoot? Thanks!

---

### Post by freemant on 2013-01-27
Found the problem! Installing the linux-image-extra package fixes the problem. Presumably it contains the needed USB keyboard driver.

---

