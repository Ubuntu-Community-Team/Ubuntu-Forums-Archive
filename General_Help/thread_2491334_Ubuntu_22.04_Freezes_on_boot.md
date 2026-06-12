---
title: "Ubuntu 22.04 Freezes on boot"
date: 2023-10-04
forum: General Help
---

### Post by fixmydriversplease on 2023-10-04
**_[SIZE=4]System specs: [/SIZE]_**

CPU: AMD Ryzen 7 7700
GPU: AMD RX 7900 XT 
GPU Drivers installed using ppa:oibaf/graphics-drivers (as the amdgpu-install from AMD does not work on kernel 6+)
System memory: 2x16 GB DDR5-5200 MHz
Two displays, one connected through HDMI (1920x1080@60), another through Displayport (1920x1080@144)

Dualboot Ubuntu 22.04.3 LTS x Windows 11 Pro
Kernel: 6.5.5-060505-generic (installed using mainline)

[SIZE=4]_**Problem description:**_[/SIZE]

My Ubuntu 22.04 can no longer successfully complete a boot. 
Yesterday, when I booted up the first time everything was normal and functioning properly. I did do some updates & upgrades using apt during that session. 
Later that day I wanted to boot into Ubuntu once again, but the boot process freezes, not even reaching a login screen.
My guess is some amdgpu error, as adding the nomodeset kernel parameter allows me back into my system.

The output of ```
journalctl -b -1 -p 0..4 
```is quite extensive, reporting multiple warnings and errors. The attached log  will eventually continue infinitely printing out the last error about usr/libexec/gdm-x-session[].
 Having inspected several errors myself, and trying different solutions without any result. 

_[SIZE=3]Tried solutions:[/SIZE]_
[LIST]
[*]Reinstalling kernel 
[*]Fallback to older kernel version (v6+) 
[*]Purging & reinstalling ppa:oibaf/graphics-drivers 
[*]Purging & reinstalling ppa:kisak/kisak-mesa 
[*]Adding kernel parameters ```
video=DP-1:1920x1080@60
```, as per [https://gitlab.freedesktop.org/drm/amd/-/issues/1886](https://gitlab.freedesktop.org/drm/amd/-/issues/1886) 
[/LIST]

Is there anyone else that has encountered a similar issue or has an idea as of how to fix it?
Thanks in advance

Full output of journalctl (emerg, alert, crit, err and warns only)
[ATTACH]292820[/ATTACH]

---

### Post by habernir on 2023-10-05
I have installed ppa:kisak/kisak-mesa and after regular update from Ubuntu repo(not from kisak repo)  it's freeze in my PC too.

---

### Post by habernir on 2023-10-06
well i see that its happen since the last update of the "linux-firmware" package

update: yes i can confirm that after downgrade linux-firmware pacakge to 3.14 its start working

---

