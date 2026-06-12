---
title: "No background on all of my settings windows?"
date: 2015-01-19
forum: General Help
---

### Post by cascade2 on 2015-01-19
[img]http://i.imgur.com/L35wM9x.png[/img]
[img]http://i.imgur.com/ZG2sRi0.png[/img]
Anyone have a clue as to how I can fix this? Thank you.

---

### Post by CantankRus on 2015-01-26
Does the same occur if you log in to the guest account?
Was it like this immediately after install or occur later?

Would also be helpful if you installed these small applications to provide some system info.
Install via terminal...
```
sudo apt-get install wmctrl inxi
```

Then in terminal run the following and copy and paste your output....
```
wmctrl -m && inxi -b
```
eg my output
```
[COLOR="#008000"]**glen@Trusty:~$**[/COLOR] **wmctrl -m && inxi -b**
Name: Compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
System:    Host: Trusty Kernel: 3.13.0-39-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at 1800.00 MHz 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.113
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1250.3GB (12.0% used)
Info:      Processes: 226 Uptime: 10 min Memory: 1017.6/3935.1MB Client: Shell (bash) inxi: 1.9.17
```

---

### Post by mooreted on 2015-01-26
Looks frustrating. I have never seen that before. I wonder if you changed themes if that would help. Or look through CCSM settings.

---

### Post by purecharger on 2015-01-28
I have the exact same issue and it is frustrating to no end. Even in a Guest session I have the same problem.

[ATTACH=CONFIG]259559[/ATTACH]

---

