---
title: "Cannot change resolution: need help reading Xorg.0.log"
date: 2007-01-14
forum: General Help
---

### Post by yetanothername on 2007-01-14
There is something wrong with my setup. I have a ViewSonic VP2030b 20" monitor and had set up Ubuntu to work with it fine. (with a little work)
A couple weeks ago I must have done something because the desktop no longer recogised the monitor. After much fiddling I could get a resolution of 680X440 but nothing else is listed in the 'Screen Reolution' dialog.

I have reinstalled the nvidia drivers and gone through the xorg.conf over and over, and do not understand why I cannot see other resolutions.

My main problem is I don't know how to interpret the output from the Xorg.0.log file. It seems to recognise the available resolutions and register(?) them.

Any help would be appreciated, I have been trying to get this working for a while now. ](*,)

---

### Post by majoridiot on 2007-01-14
```
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0291) rev 161, Mem @ 0xf8000000/24, 0xa0000000/29, 0xf7000000/24, I/O @ 0xbc00/7, BIOS @ 0xf9ce0000/17
(--) PCI: (8:0:0) nVidia Corporation unknown chipset (0x0291) rev 161, Mem @ 0xfb000000/24, 0xc0000000/29, 0xfa000000/24, I/O @ 0xec00/7, BIOS @ 0xf9fe0000/17

(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:8:0:0) found
(--) Chipset NVIDIA GPU found
```

i looks like x is finding another video card.  are you running a pci video card on a mobo with
built-in video?  if so, try disabling the onboard video in bios.

---

### Post by yetanothername on 2007-01-16
Thanks, I may well be running with an on-processor GPU unit. I will have a look at the BIOS and play with the settings.

cheers

---

### Post by yetanothername on 2007-01-19
I have looked through the BIOS settings and can find nowhere that allows me to manage the onchip GPU.

---

### Post by majoridiot on 2007-01-19
> **yetanothername said:**
> I have looked through the BIOS settings and can find nowhere that allows me to manage the onchip GPU.

thell us what your motherboard is and we'll help you find. it.

remember, the more information you provide at the outset, the more quickly your problem can
be resolved! :D

---

### Post by yetanothername on 2007-01-22
Yes, sorry about that.
My motherboard is an Asus P5N32-SLE deluxe

The chip I have is an Pentium D @ 3.4GHz (Dual Core) - I have tried a few reviews and forums and can still only guess that the chip even has an onboard GPU.

cheers

---

### Post by majoridiot on 2007-01-22
odd...  no onboard video on that mobo, yet it's seeing GPUs at two different pci addresses.
what is the output of this:

```
lspci
```

---

### Post by yetanothername on 2007-01-24
The lspci output is attached. There seems to be several unresolved references, but I don't know if they are warnings or errors.

In my BIOS there is an option:

Allocate IRQ to PCIVGA
(Assigns IRQ to PCIVGA if card requests IRQ, if FALSE then card requests for IRQ are ignored)

This is set to true by default, and I'm not sure if I should tinker with that.

cheers

---

### Post by warkro on 2007-01-30
Bump

---

### Post by majoridiot on 2007-01-30
> **yetanothername said:**
> The lspci output is attached...

honestly, i've got no clue what to tell you... that lspci list is a MESS.  half of your rig seems to
be unknown... and you are DEFINITELY showing two gpus (or 2 ids for 1)...

```
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0291 (rev a1)
0000:09:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0291 (rev a1)
```

you might try fiddling with that bios setting to see if it helps...

---

### Post by rapidwiz on 2007-01-31
This thread may help

[http://ubuntuforums.org/showthread.php?t=281779](http://ubuntuforums.org/showthread.php?t=281779)

Just run

sudo dpkg-reconfigure xserver-xorg

---

