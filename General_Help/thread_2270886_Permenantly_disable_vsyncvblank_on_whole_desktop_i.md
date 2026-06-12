---
title: "Permenantly disable vsync/vblank on whole desktop in openGL games?"
date: 2015-03-26
forum: General Help
---

### Post by realflow100 on 2015-03-26
I'm extremely ticked off having my FPS drop from 60 to 55 then to 5FPS constantly while doing normal things while playing Minecraft (Vsync is already disabled in-game and the FPS slider is set to "Max FPS/Unlimited" but its forced by the OS somehow!!)

I would love to permanently disable vsync as i dont care whether frames overlap (i dont want my FPS dropping constantly causing massive lag spikes and frame drops causing my game to be unplayable)

i tried compiz but it wants composite turned on when i enable the openGL plugin and disable vsync in there and that basically cancels out what i want to do in the first place! Why!!!! Ugh. Please help??


Im on Lubuntu at the moment (latest)

---

### Post by QIII on 2015-03-26
Hello!

It would be helpful if you could tell us the specs of your machine, particularly the graphics adapter and whether you are using an open source or proprietary driver.

Cheers!

---

### Post by realflow100 on 2015-03-26
I have 4GB of ram and celeron j1900 quad core 2.42Ghz and Intel HD Graphics (Bay Trail arcitecture) (NOT a series like HD 3000 it has no series number after HD its the lowest of the Intel HD series but its still good enough to get more than 60FPS for sure! i can even run shader mod with 30FPS in minecraft so that says something!)

it says "Intel Open Source Technology Center"
Then it says Mesa DRI Intel bay trail
3.0 Mesa 10.3.2

---

### Post by CantankRus on 2015-03-26
Install inxi.
```
sudo apt-get install inxi
```

Then post the output of ...
```
inxi -b
```

eg
```
glen@Trusty:~$ inxi -b
System:    Host: Trusty Kernel: 3.16.0-33-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at 3800.00 MHz 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.16.0 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.113
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1250.3GB (12.9% used)
Info:      Processes: 240 Uptime: 4:26 Memory: 1413.2/3934.9MB Client: Shell (bash) inxi: 1.9.17 
```

---

### Post by realflow100 on 2015-05-11
sorry for late reply but here it is

```
foxxie@foxxie-Aspire-XC-603G:~$ inxi -b
System:    Host: foxxie-Aspire-XC-603G Kernel: 3.16.0-30-generic x86_64 (64 bit) 
           Desktop: LXDE (Openbox 3.5.2) Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Acer model: Aspire XC-603G Bios: American Megatrends version: P11-B2L date: 10/13/2014
CPU:       Quad core Intel Celeron CPU J1900 (-MCP-) clocked at 2172.255 MHz 
Graphics:  Card: Intel ValleyView Gen7 X.Org: 1.16.0 drivers: intel (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Mesa DRI Intel Bay Trail GLX Version: 3.0 Mesa 10.3.2 (note by me. supports GL 4.0 under windows so the drivers limiting the GPU)
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 758.2GB (0.5% used)
Info:      Processes: 163 Uptime: 12 min Memory: 497.2/3773.9MB Client: Shell (bash) inxi: 1.9.17 


```

---

### Post by realflow100 on 2015-06-06
Hello? Anyone have any clue how to disable vsync being forced in all openGL programs in LUbuntu? Mainly minecraft? (The option is DISABLED in-game but my FPS is still LOCKED at 60FPS and constantly dropping to like 15FPS every time i walk 2 feet! and its REALLY annoying me

---

### Post by realflow100 on 2015-06-11
Help? anyone? D:

---

