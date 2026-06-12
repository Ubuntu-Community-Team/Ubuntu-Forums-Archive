---
title: "Can't see pictures in Google Earth"
date: 2015-05-01
forum: General Help
---

### Post by RogerDavis on 2015-05-01
I have the below installed on Ubuntu 14.04.

Google Earth  7.1.4.1529
Build Date  3/30/2015
Build Time  10:42:27 pm
Renderer  OpenGL
Operating System  Linux (3.13.0.0)
Video Driver  X.Org
Max Texture Size  16384x16384
available video memory  information not available
Server  kh.google.com

I think this is the 64 bit version, but I can't prove it to myself.

But the real question is: when I click on one of the picture icons, it only shows the white box with nothing in it except a bit of text identifying the location.

How do I fix this?

---

### Post by CantankRus on 2015-05-01
To help others help you, install **inxi** (a sys info script).
```
sudo apt-get install inxi
```
Then run **inxi -b** and post output.

How did you install Google Earth?
Have you seen the [**_[COLOR="#B22222"]help wiki[/COLOR]_**]("https://help.ubuntu.com/community/GoogleEarth")?
Just had a quick look and noticed there is an issue running in compiz?

Do you have another desktop session installed that uses a different window manager?
If not you can install **gnome-session-flashback** and test in the GNOME Flashback (Metacity) session.

---

### Post by RogerDavis on 2015-05-01
roger@roger-desktop:~$ inxi -b
System:    Host: roger-desktop Kernel: 3.13.0-51-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Intel model: DZ77BH-55K version: AAG39008-400
           Bios: Intel version: BHZ7710H.86A.0057.2012.0208.1904 date: 02/08/2012
CPU:       Quad core Intel Core i7-3770 CPU (-HT-MCP-) clocked at 1600.00 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Cape Verde PRO [Radeon HD 7750 / R7 250E] 
           X.Org: 1.15.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Gallium 0.4 on AMD CAPE VERDE GLX Version: 3.0 Mesa 10.1.3
Network:   Card: Intel 82579V Gigabit Network Connection driver: e1000e 
Drives:    HDD Total Size: 1000.2GB (6.9% used)
Info:      Processes: 230 Uptime: 1:27 Memory: 2961.9/16015.4MB Client: Shell (bash) inxi: 1.9.17 

Installed Google Earth from Terminal using gdebi after downloading the supposedly 64 bit .deb package 

I'm using Gnome, installed from the Software Center

---

### Post by CantankRus on 2015-05-01
Are you using gnome-shell or unity?
If you install wmctrl ....
```
sudo apt-get install wmctrl
```

You can then get your current session and window manager with...
```
echo -e "Session: $DESKTOP_SESSION \nWindow Manager: $(wmctrl -m | awk '/Name:/{print $2}')"
```

The wiki I pointed to earlier says this....
> The 64bit debian package depends on ia32-libs which is deprecated and no longer available as of 13.10 Saucy. 
Use the 32bit package and multiarch-support.

Also found [**_[COLOR="#B22222"]THIS GUIDE[/COLOR]_**]("http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html") on installing google earth in 14.04 64bit. Essentially you install the 32bit google-earth package.

---

### Post by mc4man on 2015-05-01
see - 
[http://ubuntuforums.org/showthread.php?t=2196304&p=12892342&viewfull=1#post12892342](http://ubuntuforums.org/showthread.php?t=2196304&p=12892342&viewfull=1#post12892342)

---

### Post by RogerDavis on 2015-05-01
See below for the working answer :

[https://productforums.google.com/forum/?utm_medium=email&utm_source=footer#!msg/maps/yP-kFwxfVJM/rXSpxRQdEFAJ](https://productforums.google.com/forum/?utm_medium=email&utm_source=footer#!msg/maps/yP-kFwxfVJM/rXSpxRQdEFAJ)

---

