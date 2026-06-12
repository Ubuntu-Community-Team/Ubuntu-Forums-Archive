---
title: "Graphical or some sort of over load problem"
date: 2015-05-27
forum: General Help
---

### Post by ethan26 on 2015-05-27
Hello, every time I use a program that uses a lot of cpu such as gimp, YouTube on Firefox, OpenJRE running Minecraft, ect it switches to  a black screen that says some weird message something like "switchung to fvbcon". Then it displays a message like "unable to do something" 5 or so times waiting about 5 seconds in between messages then attemps to go back to your original screen but instead random color. i do not know what the problemis but any help is apriciated.
thanks,
Ethan

---

### Post by dino99 on 2015-05-27
have you set a swap partition ?  which graphic card/chipset is used ? what graphic driver is installed ?  is there some warnings/errors logged ?

---

### Post by v3.xx on 2015-05-27
> what graphic driver is installed ?

Ditto

---

### Post by ethan26 on 2015-05-28
You mean inside the computer? The physical card?

---

### Post by v3.xx on 2015-05-28
> **ethan26 said:**
> You mean inside the computer? The physical card?
Try this

Sounds like you can get to a terminal.  Please run this command and post the final output.
```
sudo apt-get install inxi && inxi -b
```
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)
Thankyou

---

### Post by ethan26 on 2015-05-30
```
System:    Host: server Kernel: 3.13.0-32-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Gateway product: E6610
           Mobo: Intel model: N/A version: AAD50908-207
           Bios: Intel version: LA97510J.15A.0285.2007.0906.0226 date: 09/06/2007
CPU:       Dual core Intel Core2 CPU 6600 (-MCP-) clocked at 1596.00 MHz 
Graphics:  Card: NVIDIA NV43GL [Quadro FX 550] 
           X.Org: 1.15.1 drivers: nouveau (unloaded: fbdev,vesa) Resolution: 1280x1024@75.0hz 
           GLX Renderer: Gallium 0.4 on NV43 GLX Version: 2.1 Mesa 10.1.3
Network:   Card: Intel 82573E Gigabit Ethernet Controller (Copper) driver: e1000e 
Drives:    HDD Total Size: 160.0GB (4.2% used)
Info:      Processes: 179 Uptime: 14:00 Memory: 714.8/1999.3MB Client: Shell (bash) inxi: 1.9.17 

```

---

### Post by ethan26 on 2015-05-30
just fyi, i have graphics cards on hand and can change it out. Thanks!

---

### Post by v3.xx on 2015-05-30
> Quadro FX 550
Thats an older but powerful (x16) card.  There are proprietary drivers for it.  I would try one.
Open up your software sources
```
software-properties-gtk
```
and go to 'Additional Drivers'.  See what you have to choose from.

[http://www.psychocats.net/ubuntu/drivers](http://www.psychocats.net/ubuntu/drivers)

---

