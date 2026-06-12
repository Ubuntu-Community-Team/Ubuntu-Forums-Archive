---
title: "Flickering problems on external monitor after installing Ubuntu 23.10"
date: 2024-04-18
forum: General Help
---

### Post by cypherscouter on 2024-04-18
I just installed ubuntu 23.10 on my thinkpad L13. It works fine on my laptop monitor. But when I connect an HDMI cable to my other monitor, then the screen flickers on the laptop and nothing shows on the other monitor

I know it can't be the problem with the other monitor as I bought it brand new last week, and the cable works fine on this same laptop when I run in windows, and it works fine on other laptops with windows/mac

I already installed the driver with `sudo apt install nvidia-driver-535 nvidia-dkms-535` and rebooted, but that didn't help. I then installed driver 550 and I still have the flickering

This laptop uses an intel Alder Lake-UP3 GT2

I also tried editing `etc/default/grub`  by adding 'nomodeset' or 'radeon.modeset=0' within the quotation marks in the line GRUB_CMDLINE_LINUX_DEFAULT but that didn't help either

can anyone help?

---

