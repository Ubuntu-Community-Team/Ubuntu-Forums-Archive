---
title: "Green/Negative Colors throughout the system"
date: 2013-05-05
forum: General Help
---

### Post by romain.astie on 2013-05-05
Hi,

I just installed lubuntu 12.10 on on old laptop I have. It has run lubuntu before, without any problems. However, after reinstalling it, the colors are all funky. This affects the whole system. The lubuntu logo, my wallpaper are green instead of a blue color, I think, and videos play with a similar problem. Upon starting up, the OS loading screen will flash the normal color (grey/black with a blue logo and dots) but then promptly go back to the green color scheme. From what I've read, it could either be a driver problem or a settings problem, however, I didn't set anything to a negative color scheme in any Universal Access application (I don't even have one). The video card is a NeoMagic MagicGraph card (1998, I told you it was old!), so it probably isn't an issue related to the NVIDIA problems that have been going round. What's going on? Anyone fixed this problem before?

---

### Post by dino99 on 2013-05-05
well you need the neomagic driver installed : sudo apt-get install xserver-xorg-video-neomagic
if you have set a xorg.conf, then delete it : sudo apt-get purge /etc/X11/xorg.conf


and reboot and be sure the driver is activated (software-properties -> additional drivers)

---

### Post by romain.astie on 2013-05-05
So I already had the neoMagic driver installed. They're already the newest version, and the output from apt-get says it is set to manually installed (IDK what that means). xorg.conf doesn't exist, I had checked for that in trying to solve problems prior to posting. However, I cant find a menu option that reads software properties  Synaptic says the package is installed, and is the latest version. I have a binary called software-properties-gtk in my /usr/bin folder, and have tried running it from terminal, but it's taking FOREVER... I'll get back to you when it finally loads up.

---

### Post by romain.astie on 2013-05-05
All right, it finally loaded, but there are no drivers listed, and the text underneath says no proprietary drivers are in use. I've tried reinstalling the driver, but nothing happened, which I think is another hint that the OS isn't using the right driver (If i removed the driver, the screen should have gone blank, right?) How can I manually enable the driver?

---

### Post by romain.astie on 2013-05-05
Bump. By using the computer more, I find that it is more like the B and G outputs (of RBG) to the display have been switched. Everything that should be blue is green, and vise-versa. Any ideas how to change this?

---

### Post by romain.astie on 2013-05-05
hi,

I've had problems with my laptop every since updating to 12.10. Blue colors appear green on my screen; my lubuntu logo is green, and the default desktop is green as well. It's as if the G and B signals for the pixels have been swapped. In my other thread, I found that I already have the drivers for my graphics card in the system. ([http://ubuntuforums.org/showthread.php?t=2142223](http://ubuntuforums.org/showthread.php?t=2142223))

However, as mentioned in the thread above, the driver doesn't appear in the Additional Drivers window. This means, I assume, that it isn't recognized nor being used by lubuntu. Also, output from ```
lshw -c video
```
does not show that there is a driver in use for the card. Here is the output:```
*-display UNCLAIMED
description: VGA compatible controller
product: NM2200 (MagicGraph 265AV)
vendor: Neomagic Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: 12
width: 32 bits
clock: 33 mHz
capabilities: pm vga_controller bus_master cap_list
configuration: latency=32 maxlatency=255 mingnt=16
resources: memory:f9000000-f9ffffff memory:fdc00000-fdfffff memory:fdb00000-fdbfffff

```

Anybody have any idea how to load my driver into memory? And more importantly, use it to drive the card, instead of the default ubuntu driver?

---

### Post by Impavidus on 2013-05-06
First of all, I'm not a driver specialist.
Correct driver from the repos is installed, card is detected, driver should work automatically. I even think the driver is used, it is enabled during boot just afer your flash in correct colours. No proprietary driver is available. It could be a bug in the driver for Quantal that went unnoticed by the devs because of the low number of 1998 NeoMagic MagicGraph 265AV cards still in use (yes, I understand it's very obvious when you actually run the system. Maybe someone forgot to check). You can hunt the internet for drivers for your particular model for Quantal and install manually. It won't be easy though, this hardware is simply too old to get proper support. I didn't find any references to it on Linux systems after kernel 2.6.

Besides, it's better to bump your thread less often and edit your last post instead if you really have something to add and there's no reply to the last post you made. When I see you recieved four replies since my previous visit I think: OK, this guy (or girl) is already recieving help, I can skip that thread. Which is not going to help you. One bump per 24 hours is accepted.

---

