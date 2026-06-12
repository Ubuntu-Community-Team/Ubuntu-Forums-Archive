---
title: "Problem with rx480"
date: 2018-07-26
forum: General Help
---

### Post by innerd on 2018-07-26
[COLOR=#111111][FONT=Ubuntu]I can't boot my Ubuntu 18.04 machine without using nomodeset in grub, to start the live usb for the installation I needed that command too and without it the system stucks with a weird screen.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried to update the drivers, a fresh install and even use the AMDGPU drivers from amd (in this case the system doesnt start at all).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Can you help me?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here the output of lspci -knn | grep VGA -A3:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]2d:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480] [1002:67df] (rev c7) Subsystem: PC Partner Limited / Sapphire Technology Ellesmere [Radeon RX 470/480/570/580] [174b:e353] Kernel modules: amdgpu 2d:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 580] [1002:aaf0][/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Right now i dont have the Amdgpu drivers installed because i was forced to reinstall again.[/FONT][/COLOR]

---

### Post by innerd on 2018-08-09
Some help??

---

