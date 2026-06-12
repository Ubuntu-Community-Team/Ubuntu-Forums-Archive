---
title: "lower performance then when i ran windows? please help."
date: 2013-11-27
forum: General Help
---

### Post by sjoerdmeijer33 on 2013-11-27
hello, i mostly have this problem when im watching series that are i 720P and up. i know my laptop is bad but it should run videos right?
could it be my version of ubuntu (13.4)? please help me as this is really annoying.

---

### Post by sdowney717 on 2013-11-27
what video chip in in it?

mine does fine on video with this older desktop video card
**01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 8400 GS Rev. 2] (rev a1)**

run 'lspci' in terminal will list it out.

```
scott@scott-P5QC:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
**[COLOR="#FF0000"]01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 8400 GS Rev. 2] (rev a1)[/COLOR]**
02:00.0 Ethernet controller: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II / PATA Controller (rev b2)
05:00.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
05:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)
05:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)
scott@scott-P5QC:~$ 

```

---

### Post by sjoerdmeijer33 on 2013-11-27
its a Intel® 945GME x86/MMX/SSE2. so it should be quite bad. but on windows i never had these problems. here it just freezes and then continues a few seconds later with all sorts of clutter on the screen. D: ive had ubuntu for about 5 months now and i think this problem has always been there

---

### Post by philinux on 2013-11-27
> **sjoerdmeijer33 said:**
> its a Intel® 945GME x86/MMX/SSE2. so it should be quite bad. but on windows i never had these problems. here it just freezes and then continues a few seconds later with all sorts of clutter on the screen. D: ive had ubuntu for about 5 months now and i think this problem has always been there

According to a search for linux and that card it does look a bit weak.

This may help but take care to follow the steps carefully. If no change then just remove the ppa from your sources list and any packages you installed. I would take notes. Sorry but no guarantees here.
[http://ubuntuforums.org/showthread.php?t=2072420](http://ubuntuforums.org/showthread.php?t=2072420)

---

### Post by sjoerdmeijer33 on 2013-11-27
thanks! im trying it.

---

### Post by sjoerdmeijer33 on 2013-11-27
nope did not work. but thanks for trying!

---

### Post by Linuxisfast on 2013-11-27
Have you tried a lighter DE like Lubuntu?

---

### Post by VMC on 2013-11-27
> **sjoerdmeijer33 said:**
> hello, i mostly have this problem when im watching series that are i 720P and up. i know my laptop is bad but it should run videos right?
could it be my version of ubuntu (13.4)? please help me as this is really annoying.
Maybe try another player to confirm your issue. I would recommend VLC. There may be a "lighter" player, and VLC seems heavy because of it sheer size, but I find if VLC can't play it nothing will.

---

### Post by sjoerdmeijer33 on 2013-11-27
> **Linuxisfast said:**
> Have you tried a lighter DE like Lubuntu?
no never, but it does seem better and im downloading it now. if i install it, will i loose all my stuff?

---

### Post by sjoerdmeijer33 on 2013-11-27
> **VMC said:**
> Maybe try another player to confirm your issue. I would recommend VLC. There may be a "lighter" player, and VLC seems heavy because of it sheer size, but I find if VLC can't play it nothing will.
sadly thats not it, as i already use VLC

---

### Post by sdowney717 on 2013-11-28
One thing I learned was to separate /home .
That way the os files are in a seperate partition and you never loose your /home files.

---

