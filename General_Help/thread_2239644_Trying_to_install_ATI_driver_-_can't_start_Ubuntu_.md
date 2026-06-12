---
title: "Trying to install ATI driver - can't start Ubuntu anymore"
date: 2014-08-15
forum: General Help
---

### Post by romain5 on 2014-08-15
Hi,
On my fresh installation of Ubuntu 14.04 I wanted to install the ATI driver for my Radeon HD 7950 (in order to unlock more setting like go up to 120Hz refreshment rate for the screen). I used the graphical GUI to do it and reboot the computer and then I have the warning windows "The system is running in low-graphics mode", and any choice I can make lead to stuck the computer (just a black screen without anything nether prompt).

I can start in recovery mode and try to redo manually the installation with:
```
sudo apt-get remove --purge fglrx*
apt install fglrx
```
But it didn't work.

So I tried to come back to Xorg following [this tutorial]("http://doc.ubuntu-fr.org/radeon"):
> 
sudo sh /usr/share/ati/fglrx-uninstall.sh **<= This one didn't exist**
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon  
sudo apt-get install xserver-xorg-video-radeon
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core 
sudo dpkg-reconfigure xserver-xorg
sudo Xorg -configure

But I can't generate a new *xorg.conf*, I have the error: *"Number of created screens does not match number of detected devices"*
*xrandr* gives:"*Can't open display*"

What can I do to repair this ?
How should I install the proper ATI driver ?

Thank you.

Here is my configuration :
[COLOR=#000000][FONT=Verdana]- Core i5-3570K / 3.80 GHz [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]- MSI Z77A-G45 [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]- Sapphire Radeon HD7950 FleX Version OC - 3 Go [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]- 2*4 Go Kingston DD3 1600 CL9 [/FONT][/COLOR]

---

### Post by romain5 on 2014-08-15
As it was a fresh installation, I finally formated and reinstalled Ubuntu, now the GUI has worked well (a quite well, I can access the administrator panel).

---

### Post by grahammechanical on 2014-08-15
That change of video setting may have had the potential to damage the monitor. Ubuntu reads the EDID (Extended Display Identification Data) in the monitor and uses that information to set the manufacturer's recommended optimum settings.

> **Extended display identification data (EDID) is a data structure provided by a [digital display]("http://en.wikipedia.org/wiki/Digital_display") to describe its capabilities to a video source (e.g.[graphics card]("http://en.wikipedia.org/wiki/Graphics_card") or [set-top box]("http://en.wikipedia.org/wiki/Set-top_box")). It is what enables a modern [personal computer]("http://en.wikipedia.org/wiki/Personal_computer") to know what kinds of monitors are connected to it.**

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

Regards.

---

### Post by romain5 on 2014-08-15
Finally it still doesn't work. :(

I have reinstalled Ubuntu (completely), I have installed the ATI driver with the GUI, reboot two times and begun to work. After shutting down the computer to go away and start it again now, it doesn't work anymore. I am still stuck on the [COLOR=#000000]"The system is running in low-graphics mode" window.

What can I do?
Why is it crashing like that?

Thanks.[/COLOR]

---

