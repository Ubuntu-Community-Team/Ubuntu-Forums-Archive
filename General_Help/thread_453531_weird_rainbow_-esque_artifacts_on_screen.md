---
title: "weird rainbow -esque artifacts on screen"
date: 2007-05-24
forum: General Help
---

### Post by gulp35 on 2007-05-24
Hi,

I've just installed kubuntu 6.10 on one of my machines, installed the nvidia drivers, and got the screen to work at the correct resolution (1440x900) and now there are rainbow-esque artifacts in the dark regions of anthing on the screen...

I have a Samsung 941BW 19" widescreen monitor... I am not sure if the colors will only show up on this screen so I will try to attach a screenshot later.

lspci
```

00:00.0 Host bridge: nVidia Corporation Unknown device 0070 (rev c1)
00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:05.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:06.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:07.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
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
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
06:08.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

```

I don't remember if it did this when I first installed it. 

The reason I have not upgraded to 7.04 is because my wireless seems to be more finiky with that (Though there is a high probability that it was a network problem and not a ubuntu problem).

Thanks,
   gulp35

---

### Post by gulp35 on 2007-05-24
here is an example of the artifacting that I was trying to explain... It only seems to appear in regions of black.

---

### Post by earobinson on 2007-05-24
screenshot?

---

### Post by gulp35 on 2007-05-24
ok, so it seems that after checking my screenshot on another computers screen, that there is no artifacting on it. I conclude that there is something mal-adjusted with my monitor.

What would cause this type of artifacting?
How could I fix it?

Thanks,
  gulp35

---

### Post by kuja on 2007-05-24
There are a number of things that can cause that, figuring out will take some trial and error. Solution #1: try disabling usplash by removing it from this line in the /boot/grub/menu.lst file:

```

...
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
**# defoptions=quiet splash**

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
...

``` (the line in bold), just remove the word splash.
Afterwards, run this command:
```
sudo update-grub
```

After this, reboot, and see if you still have artifacting.

---

### Post by gulp35 on 2007-05-24
huzzah! no more artifacting! Thank You!

Now if I wanted the boot screen, would it be possible (without bringing the artifacting of course).
or another question.
Why does the boot splash cause this?

THANK YOU :),
-gulp35

---

### Post by kuja on 2007-05-24
Umm, it may be possible, by playing with adding the word splash back, as well as the vga=xxx option. What xxx is is a good question, dependant on your resolution and color depth, you  might also need to play with the usplash conf file with regards to your resolution (in the /etc directory). Getting it to an optimal size AND keeping the artifacting away at the same time may be tricky, but I think it can be done.

---

