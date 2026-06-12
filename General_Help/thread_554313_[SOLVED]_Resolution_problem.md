---
title: "[SOLVED] Resolution problem"
date: 2007-09-18
forum: General Help
---

### Post by S3loth on 2007-09-18
Hello. I just installed Ubuntu, and I'm having some problems with my resolution. I have an HP w19b monitor that can go up to 1440x900, however, all Ubuntu will let me go to is 800x600. I am extremely new to Ubuntu and Linux, so if somebody could explain things in absolute newbie terms, it would be much appreciated.

---

### Post by arkara on 2007-09-18
try to install the graphics card driver
on the upper right you will see a chipset icon
click on it and it will propaply have the right graphics driver for install..
if you have nvidia or ati click on it type the root pass and then it will download and install the drivers automatically
the onnly thing you have to do next is a reboot

---

### Post by S3loth on 2007-09-18
Sorry, but the only thing I see in the upper right is the clock, networking, volume, and the power buttons. Also, I'm not sure what kind of graphics card I have, how do I find out?

---

### Post by w4ett on 2007-09-18
From the terminal type:

```
lspci
```

Paste the results back here so we can have a look.

---

### Post by alienexplorers on 2007-09-19
Use ENVY script to load your drivers.  Then once they are loaded you can use nvidia-settings to set your resolution to what you want.  You may need to remove your current drivers using ENVY before installing the new ones.  If after loading the drivers you still cannot get the resolution you want then yo might have to add a modeline to your monitor section of your xorg.conf file.  I have a link to a modeline maker in my sig.  happy computing.

---

### Post by S3loth on 2007-09-19
Here's what happened when I typed in lspci:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
03:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem

---

### Post by w4ett on 2007-09-19
You have an Nvidia chipset:

> 00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)

You will probably have to enable the restricted divers for the Nvidia chipset.

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by S3loth on 2007-09-19
> **w4ett said:**
> You have an Nvidia chipset:



You will probably have to enable the restricted divers for the Nvidia chipset.

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

THANK YOU! The first option worked! Seriously, thanks a lot! :)

---

### Post by w4ett on 2007-09-19
Super...Good Luck and...........Please mark yout thread "Solved"...

---

