---
title: "Bootloader cann't be seen, even after custom kernel installation"
date: 2013-11-19
forum: General Help
---

### Post by akashhajari on 2013-11-19
I tried installing my custom kernel on Ubuntu 12.04 LTS(64 bit). I wanted custom kernel's entry in boot-loader along-side existing kernel.
But every time,after installing custom kernel, no boot-loader seen and it directly selects newer custom kernel.
Also custom kernel doesn't work properly.

Procedure I followed is:
After copying existing kernel's .config from /boot/ to custom kernel's source, I followed make menuconfig, make ,make modules_install, make install, update-grub.
Then I checked **/boot/grub**/ **grub.cfg**, the file had both menu entries for existing as well as custom kernel. But existing kernel's entry was in previous kernel's structure in same file.
After this, when I rebooted system, directly custom kernel got selected. And trying this whole procedure for 3 times, every time custom kernel selected and that also doesn't work.Custom kernel either has display problem or no input sense problem.

So, Please suggest me, Is it correct to copy .config from /boot/config-`uname -r` and how to get boot-loader with existing and new custom kernels entry.

Thanks,
Akash Hajari.

---

