---
title: "Can't boot live CD on desktop"
date: 2008-06-26
forum: General Help
---

### Post by brons2 on 2008-06-26
I've installed Ubuntu on my old work laptop and my new home laptop with good results.  

I tried to boot up an AMD64 live CD on my desktop at home and it locked up while trying to load Gnome.  I got the Heron and my mouse pointer worked but otherwise I couldn't do anything.  The menu bars at the top and bottom were strangely corrupted.  I had to hold the power button down to reboot.  

I'm thinking maybe this is because of the GeForce 7800GT card in the system, other people have talked about the open source drivers for nVidia not being the best.

System Configuration:
eVga NF-41 board (NForce4)
Opteron 165 (Dual core, 1.8, 1MB L2)
GeForce 7800GT, PCIe x16
2GB Kingston Value RAM
120GB Maxtor internal, 160 GB Maxtor external (USB2)
DVD-Rom
DVD-RW
Realtek/AC97 sound
Gigabit NForce NIC

...maybe I should try a 32 bit CD?

I should mention, this machine is like a rock in Windows XP.  It's fast, stable and runs games well enough considering the video card is about 2 generations old.  It overclocks like a mofo too, stock vCore is 1.35 or so, move it to 1.4 and you can do 2.91 on air.  (but right now I'm running it at stock clockings)

So, any suggestions?  Try a 32 bit CD perhaps?

---

### Post by Darkade on 2008-06-26
In the LiveCD boot menu press F4 (or whatever is the key asigned to "Other boot options") then select Safe graphics mode. If your desktop loads fine then It's probably your Nvidia card. But there are probably workarounds

---

### Post by earthmeLon on 2008-06-26
If that doesnt work, hit F6 instead and delete "quiet" and "splash" from the boot line :D

---

### Post by brons2 on 2008-06-26
> **Darkade said:**
> In the LiveCD boot menu press F4 (or whatever is the key asigned to "Other boot options") then select Safe graphics mode. If your desktop loads fine then It's probably your Nvidia card. But there are probably workarounds

That worked, thanks.  I'm posting via the LiveCD on the machine in question right now.  

If I want to install, how do I designate it to use this graphics mode all the time?  Or at least until I install the non-GPL nVidia drivers?

---

### Post by brons2 on 2008-06-26
output from lspci:

ubuntu@ubuntu:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
ubuntu@ubuntu:~$

---

### Post by Darkade on 2008-06-26
I had a similar problem and just tried the install. It kindda worked. I had a functional desktop, and after that I just had to enable restricted drivers for my graphics card. So go ahead. if it doesn't work there's sure a way to make it work

---

### Post by brokenLockpick on 2008-07-13
I feel I should post an alternate method for users searching the forum since I have similar specs and had the same problem. Using amd64, with opteron 148 (2.2GHZ single core) and a 7800gt.

I hit F4 and selected safe graphics mode then hit F6 and added to the beginning of the line fb=false (which reportedly disables the frame buffer).

Still can't get the restricted nvidia drivers to work properly but that's another story.

---

