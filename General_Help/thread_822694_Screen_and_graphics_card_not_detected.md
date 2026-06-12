---
title: "Screen and graphics card not detected"
date: 2008-06-08
forum: General Help
---

### Post by rollinroll on 2008-06-08
Hi i have an Nvidia 8600GTS graphics card.  I just installed Hardy over my existing Gutsy installation and everything seemed to work fine but when i restarted and booted from the ubuntu partition i just got an error wich says Screen and graphics card not detected... Seems like some driver problems so i reinstalled the nvidia driver and its still not working!
Hope i can get some help over here!
Thanks!

---

### Post by nickdbliss on 2008-06-08
are u able to use terminal? I would like to see the result of this command 

#lspci

---

### Post by rollinroll on 2008-06-08
> **nickdbliss said:**
> are u able to use terminal? I would like to see the result of this command 

#lspci
Thanks for the reply, this is what i got

00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
07:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)

---

### Post by nickdbliss on 2008-06-08
07:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)


That shows your graphic card is being detected. There is some problem with the driver. It might occured couse you installed over your previous OS.

---

### Post by rollinroll on 2008-06-08
So is there something i can do?

---

### Post by nickdbliss on 2008-06-08
yeah you have to reconfigure your graphic card adapter. Fingers crossed. :)

Try this command at the terminal

#sudo nvidia-glx-new-config enable

---

### Post by nickdbliss on 2008-06-08
If that doesnt work use this one

#sudo dpkg-reconfigure xserver-xorg

It will take a while, so do u mind if i take some nap? lol. jk

---

### Post by rollinroll on 2008-06-08
Hmmm.... Wierd, i got command not found...

Edit> okay i got your second command to work but i dont un derstand a ****

---

### Post by nickdbliss on 2008-06-08
well, i thought so. Just finish it and lemme know if it solves the problem. If not i am here dude.

---

