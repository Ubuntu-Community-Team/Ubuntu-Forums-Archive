---
title: "Re: New screen some issues"
date: 2016-04-22
forum: General Help
---

### Post by per_kllstrm on 2016-04-22
I finally got my dell 34" ultrawide yesterday, i unplugged my old main monitor and plugged in the new one, i  got 2 screens connected. It all works as it supposed to except i cant seem to be able to change the wallpaper for some freakin reason, its like the system still thinks my old main screen is connected or something...

heres my xrandr output if that might be to any help: [http://pastebin.com/UW9utsHT](http://pastebin.com/UW9utsHT)

xorg.conf: [http://pastebin.com/21f0NmUw](http://pastebin.com/21f0NmUw)

And while im at it, how do i overclock my new monitor in linux? works fine at 80hz in windows. i cant add custom resolutions with xrandr to the screen i got problem with it says
xrandr --verbose --addmode DP-4.8 "3440x1440_80"

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  49
  Current serial number in output stream:  50
 
this is what i used to add the new mode xrandr --newmode "3440x1440_80"  571.75  3440 3712 4088 4736  1440 1443 1453 1510 -hsync +vsync




might add that im using xubuntu if that makes any difference

After some digging around: when i go to settings editor and displays, only my 2nd screen shows up there... not the main screen

Gotta add: i get login loop after computer has been in sleep... I have to login like 5-6times before i get into the os again, after each login try it goes back to sleep what can theese problems be related to? is it the nvidia driver causing this just cause i changed one of the monitors?

After removing nvidia driver the problem was kinda solved i could change wallpaper etc but had no resolutions to choose from, i installed the newest nvidia drivers this time and the login loop is gone but the other issues is still there... This is so annoying, basically all the settings i try to apply to the screen gets applied to xScreen0 instead of DP-4.8

---

### Post by Bucky Ball on 2016-04-23
Are you installing these drivers from 'Additional Drivers'? If not, suggest you remove whatever you've installed and try the preferred NVidia driver in 'Additional Drivers'. See how that goes. 

Which version/flavour of ubuntu are you using?

---

### Post by per_kllstrm on 2016-04-23
First i used the ones found in additional drivers, uninstalled them and installed newest via apt-get and same issue... I use xubuntu 14.04, however when i uninstalled the driver IT seemed to work buti only had 800x600 resolution on my 3440x1440 screen haha

---

### Post by Bucky Ball on 2016-04-23
```
sudo lshw -C video
```

Output please.

---

### Post by per_kllstrm on 2016-04-23
description: VGA compatible controller
       product: GM200 [GeForce GTX 980 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:327 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff


If this might help:
xfce 4.10
nvidia 358.16

DP-2 is my second screen and DP-4.8 is the main screen
and here is xfconf-query -c xfce4-desktop -lv output: [URL="http://pastebin.com/juN8sbth"]http://pastebin.com/juN8sbth


[/URL]

---

### Post by Bucky Ball on 2016-04-23
I think you're going to need to add a PPA for the drivers for that GPU or try 16.04 LTS. Have you done some research? With a brief look [I found this]("http://ubuntuforums.org/showthread.php?t=2318069&p=13459174"), which may be of some help.

I have the GTX 970 which works faultlessly, and with CUDA, in both 14.04 and 16.04. The drivers in Additional Drivers work for that one.

---

### Post by per_kllstrm on 2016-04-23
> **Bucky Ball said:**
> I think you're going to need to add a PPA for the drivers for that GPU or try 16.04 LTS. Have you done some research? With a brief look [I found this]("http://ubuntuforums.org/showthread.php?t=2318069&p=13459174"), which may be of some help.

I have the GTX 970 which works faultlessly, and with CUDA, in both 14.04 and 16.04. The drivers in Additional Drivers work for that one.


The thing is, everything worked flawless with my old monitor, i got this issue when i switched to my new one i have searched the whole freakin google haha

---

### Post by Bucky Ball on 2016-04-23
Oh, right. Then that is peculiar. Are you using the same driver as you were when things were working fine? Can you get it back to the original setup, with the original monitor plugged into the *same* physical output on the GPU as it was. Once that's all working fine, as it was, plug the new monitor into a different socket on the GPU. I'm presuming they are both HDMI and your GPU has a couple of HDMI sockets.

Get it back to where it was working with the original monitor only then add to that. You can swap desktop placement around with the software if things are in the wrong places logically. As long as the actual monitors are working as they should. A few ideas ...

---

### Post by per_kllstrm on 2016-04-23
I guess i could do that, my screens is displayport only got 1 hdmi but 3 displayport :)

> **Bucky Ball said:**
> Oh, right. Then that is peculiar. Are you using the same driver as you were when things were working fine? Can you get it back to the original setup, with the original monitor plugged into the *same* physical output on the GPU as it was. Once that's all working fine, as it was, plug the new monitor into a different socket on the GPU. I'm presuming they are both HDMI and your GPU has a couple of HDMI sockets.

Get it back to where it was working with the original monitor only then add to that. You can swap desktop placement around with the software if things are in the wrong places logically. As long as the actual monitors are working as they should. A few ideas ...

so freakin wierd, it works flawless with old monitor, it shows up in settings editor etc, its like the new monitors hardware is not supported or something....

THIS is wierd, even tho my old monitor is Displayport 1.2, and my new is, disabling displayport 1.2 in the monitors menu seems to have solved the problem...

however i still cant add custom resolutions...

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  47
  Current serial number in output stream:  48

---

### Post by Bucky Ball on 2016-04-23
You still have the NVidia driver installed? Check Nvidia x Server Settings GUI (should be in your Applications) and see what you can do there, if you haven't already.

---

### Post by per_kllstrm on 2016-04-23
> **Bucky Ball said:**
> You still have the NVidia driver installed? Check Nvidia x Server Settings GUI (should be in your Applications) and see what you can do there, if you haven't already.

Cant add custom resolutions there as i can in windows... :/

---

