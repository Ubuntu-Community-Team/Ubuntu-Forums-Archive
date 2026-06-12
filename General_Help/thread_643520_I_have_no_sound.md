---
title: "I have no sound"
date: 2007-12-17
forum: General Help
---

### Post by Mikami on 2007-12-17
Dear everyone at this forum...
I just switched to Ubuntu today... i was on Windows... I think it killed my Sound Driver.... i literally have 0 sound..... this is probably due to the fact that i plainly FORMATTED my drive... if anyone over here can help.. it will be greatly appreciated.. thanks. 


-Mikami

---

### Post by josephcherng on 2007-12-17
it's more likely that you don't have the right driver for the card. give us some info on your computer specs and sound card model. it's usually not too much work to get it working again.

---

### Post by lisati on 2007-12-17
> **Mikami said:**
> Dear everyone at this forum...
I just switched to Ubuntu today... i was on Windows... I think it killed my Sound Driver.... i literally have 0 sound..... this is probably due to the fact that i plainly FORMATTED my drive... if anyone over here can help.. it will be greatly appreciated.. thanks. 


-Mikami

> **josephcherng said:**
> it's more likely that you don't have the right driver for the card. give us some info on your computer specs and sound card model. it's usually not too much work to get it working again.

Are you using the latest Ubuntu (7.10) and are you using a laptop? Knowing this can help point us in the right direction for offering suggestions.

---

### Post by FuturePilot on 2007-12-17
Can you post the output of
```
lspci
```
This will let us know what kind of hardware we are dealing with here.

---

### Post by dsplabs on 2007-12-17
Definitelly need more info to be able to help you. If you go to **System > Preferences > Sound** are there any audio devices listed there? One possibility is that you (and your computer) may be suffering from the *No volume control GStreamer plugins and/or devices found* bug as discussed in this post: [http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/). Please post back with information on what audio hardware you are using and what audio devices were actually picked up by your install.

Cheers
Kamil

---

### Post by Mikami on 2007-12-18
> **FuturePilot said:**
> Can you post the output of
```
lspci
```
This will let us know what kind of hardware we are dealing with here.

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]
03:03.0 Communication controller: Conexant HSF 56k Data/Fax Modem
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)



Thats the readout that it gave me. 
P.S   the torrent my friend gave me was the latest version.

---

### Post by Mikami on 2007-12-19
ok guys.... its been 2 days.... no sound.. no music... im srsly going to kill myself if i cant get my music soon.



Mikami

---

### Post by ed-koala on 2007-12-19
I found this post about your Intel sound on another forum.  It seems to resolve the issue, but as I'm not an expert on Linux you may have a few questions you can ask here if you come to a sticking point.

Hope it helps, your problem seems to be a known bug that is fixable.

---

### Post by ed-koala on 2007-12-19
Ooops, forgot to post the link -

[http://www.linux-on-laptops.com/forum/showthread.php?t=1488](http://www.linux-on-laptops.com/forum/showthread.php?t=1488)

---

### Post by Linuxratty on 2007-12-19
Did that fix it?

---

### Post by Mikami on 2007-12-19
it didnt work folks =(

EDIT: I use a PC not a laptop. (Desktop computer)

---

### Post by Mikami on 2007-12-20
Anyone? the issue still isnt solved.. i used Google, no avail. :´(

---

