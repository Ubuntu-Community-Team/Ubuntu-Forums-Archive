---
title: "Ubuntu freezes randomly at boot"
date: 2012-10-21
forum: General Help
---

### Post by nemarona on 2012-10-21
I'm having trouble restarting my laptop after upgrading to 12.10. The laptop shuts down and then is not able to load Ubuntu, but after two or three tries it boots normally.

A clean install of 12.10 also didn't help.

My hardware configuration is the following:
Dell XPS 15z running Kubuntu 12.10 amd64
Processor: Intel Core i7 2.80 GHz x4
Memory: 7,70 GB
I'm not using any proprietary drivers.

I'm using the "acpi=noirq" boot option, as recommended in [Ubuntu Hardware Support]("https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z"), because otherwise the keyboard is not responding.

If you need any more info, please ask.

Thanks in advance for any help!

---

### Post by dino99 on 2012-10-21
do you get some usefull errrors/warnings logged ?
i think you can add acpi=force too.

lot of users have a modemmanager/network-manager issue at shutdown, maybe you get it also.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1066484](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1066484)

to let you know what happen when shutting down, remove "splash" from boot line (/etc/default/grub, then sudo update-grub) to see the comments.

---

### Post by nemarona on 2012-10-22
> **dino99 said:**
> to let you know what happen when shutting down, remove "splash" from boot line (/etc/default/grub, then sudo update-grub) to see the comments.

I did as suggested; deleted "splash" from /etc/default/grub and then run sudo update-grub. Here's the output to that:
```
sudo update-grub
Generando grub.cfg ...
Se encontró una imagen linux: /boot/vmlinuz-3.5.0-17-generic
Se encontró una imagen initrd: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Encontrado en Windows 7 (loader) en /dev/sda2
^[[B^[[B^[[Bhecho
```
The next restart proceeded flawlessly. I will continue to monitor this, in any case.

Thanks for the help!

---

### Post by nemarona on 2012-11-03
For the first time in weeks I booted today into Windows (the HDMI port does not work in Ubuntu). After rebooting, the laptop wouldn't boot into Ubuntu again, and I had to restore the "splash" option in order to get it working.
Will keep an eye on subsequent reboots to see if the original problem reappears.

---

