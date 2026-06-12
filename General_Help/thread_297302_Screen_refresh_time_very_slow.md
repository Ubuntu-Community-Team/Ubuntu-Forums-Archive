---
title: "Screen refresh time very slow"
date: 2006-11-10
forum: General Help
---

### Post by akaney on 2006-11-10
I am a newb, so forgive me if this is in the wrong forum.  I have just installed 6.10 on an Acer e360 desktop system.  Everything seems to be working, except whenever I move a window, or scroll a webpage, the window has to redraw itself.  I am guessing this is a problem with the videocard driver and/or the refresh rate set on the system.  

My question is:

1.) How do I find out what video card I have in my system?  I believe it is a ATI X600 video card.  If that is what I have, how do I change the driver for the system?

2.) The refresh rate on my system appears to be set at 75Hz.  I have seen a few posts on how to change the rate, but they all seem very complicated.  Is it really that hard?

---

### Post by taurus on 2006-11-10
Open a terminal, Applications -> Accessories -> Terminal, and type

```
lspci
```

---

### Post by akaney on 2006-11-10
It appears that I have a nvidia chipset in the computer.  I am a little confused now, when I open a system window, such as the add remove programs box, everything works fine.  When I open firefox, and scroll down the page, there is a slight hesitation between each "page".  It does not scroll down smoothly.  If I move a window on the desktop, it jerks, and does not move smoothly with the mouse.  I have a hard time putting this into words, so I would have an even harder time trying to find an answer.  Has anyone else experienced something like this?

---

### Post by taurus on 2006-11-10
You need to install a driver for your graphic card!  Now, what graphic card do you have?  What is the output of that command then?

```
lspci
```

---

### Post by akaney on 2006-11-11
When I do that command, I get the following information:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by OffHand on 2006-11-11
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)

That is your video card. You can either install the Nvidia drivers using Synaptic or install the drivers from the Nvidia website. I recommend starting with the drivers from Synaptic.

```
sudo aptitude install nvidia-glx nvidia-kernel-common nvidia-settings
```

---

### Post by akaney on 2006-11-11
OK, I just did the command, which uninstalled my old driver, and installed my new driver.  Do I need to restart the computer or anything?  It is still doing the same thing as before.

---

### Post by OffHand on 2006-11-11
> **akaney said:**
> OK, I just did the command, which uninstalled my old driver, and installed my new driver.  Do I need to restart the computer or anything?  It is still doing the same thing as before.

Whats the output of ```
glxinfo
```

If you do not see the driver and direct rendering do the following:
Logout and press ctrl+alt+backspace.

If you x-server fails to start you will need to do this:

1 press ctrl+alt+F1

2 login

3 ```
sudo /etc/init.d/gdm stop
```

4 ```
sudo dpkg-reconfigure xserver-xorg
```

Answer all the questions. If you do not know the answer choose the default answer.

5 ```
sudo /etc/init.d/gdm start
```

---

