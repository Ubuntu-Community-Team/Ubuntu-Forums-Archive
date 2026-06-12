---
title: "Random restart of computer with ubuntu 22.04.3 LTS"
date: 2024-01-05
forum: General Help
---

### Post by achodankar on 2024-01-05
Whenever the computer is idle, it randomly restarts entirely. Sometimes when i am working, it restarts also. Is there a solution to this issue?

---

### Post by uchihaveha on 2024-01-07
I have The same problem, which started two weeks ago. I have Windows 11 alongside, and no restarts on this system, the problem is only on Ubuntu. I installed Ubuntu 23.10 from scratch doesn't help. Sometimes, it can work for 4 hours without restarts. Sometimes it happens every 5 minutes. I think there is some problem with Nvidia drivers or in the SSD Samsung 980 Pro because Windows is on another drive.

---

### Post by aug7744 on 2024-01-07
You are using nvidia driver binary, proprietary or nouveau ?

---

### Post by MAFoElffen on 2024-01-07
I'm really not sure if it is NVidia or Samsung 980 Pro related...

I have 5 system here on 22.04, all Gnome Based DE's. Only 1 of the 5 systems has a problem, where it will intermittently go into a suspend mode. It has nvivia-driver-390 and 2 Samsung 870's. None of the dconf settings or power profiles seem to be able to prevent it. I have to turn on Gnome Extension Caffeine to keep it from going into suspend.

Another that does not have this problem had nvidia-driver-535, 2 x Samsung 980 Pro's and a 980 Pro. Two other without the problem are Intel iGPU's. The last one is Raspberry Pi4.

Nothing in my logs point to a rhyme or reason why.

---

### Post by uchihaveha on 2024-01-07
I have tried all versions of Nvidia drivers. 470 looks more stable for me, less restarts. Nouveau didn't try because it made my display flicker when I used it. It happened to me on an Asus laptop with Nvidia 3060 after more than one year of stable work.

---

### Post by uchihaveha on 2024-01-08
It looks like there is some problem with the energy saver mode. Today, I worked without restarts. I have enabled the performance mode (New feature 23.10) and disable [COLOR=#0C0D0E][FONT=-apple-system]aspm[/FONT][/COLOR]


[LIST=1]
[*]sudo gedit /etc/default/grub
[*][FONT=inherit]Edit grub. Add pcie_aspm=off at the end of GRUB_CMDLINE_LINUX_DEFAULT. Line will be like this:[/FONT]
[FONT=inherit]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off"[/FONT]
[*][FONT=inherit]sudo update-grub[/FONT]
[*]reboot
[/LIST]

---

