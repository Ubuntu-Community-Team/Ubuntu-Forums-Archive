---
title: "desktop environment is not working"
date: 2019-01-18
forum: General Help
---

### Post by EZZ9 on 2019-01-18
I updated to 18.04 from 16 and picked Unity because I've always used it and don't want to lose all the things I'm use to.
But now I have a black screen no working desktop, I can't see my wallpaper or files that are on it.

---

### Post by Autodave on 2019-01-18
Upgrading from one release to another often causes problems.  I learned a long time ago to just do new installs after backing everything up to an external source.  Can you give us some info on your machine?

You can download 18.04 and make a boot disk: this will at least allow you to get into the machine and copy files that you need to keep.

---

### Post by oldrocker99 on 2019-01-18
Ubuntu MATE has a setting called "Mutiny" which is very close, in appearance and features, to Unity, FWIW.

You can just type```
sudo apt install mate-core mate-desktop-environment
```

MATE is lightweight, stable, and very configurable. There are also "Redmond" (Windows 7-like interface) and "Cupertino" (OSX). The default desktop is the same environment as the GNOME 2 interface I fell in love with back i 2008.

*Highly* recommended.

---

### Post by EZZ9 on 2019-01-19
some info on your machine? What info do you need?

---

### Post by #&amp;thj^% on 2019-01-19
Just some friendly advice with font colors>>>stay with the normal (Default) font size and color.
A good way to obtain system info is:
```
inxi -Fxz
```
If needed->> to install inxi use:
```
sudo apt install inxi
```
Good Luck.
You may want to start with the information provided here: [https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-unity-desktop-on-ubuntu-18-04-bionic-beaver-linux)

---

### Post by EZZ9 on 2019-01-20
OH great my copy and paste is not working right either. Sorry That is why the fonts are changing.
 I ran inxi -Fxz but now i'm going to copy and paste it here. I can't type all that. OK that looks good at my end. Hope it looks right when I post.


OK I see it reads Desktop:Gnome 3.28.3
but at the start up when signing in I picked Unity.

 Host: hermann Kernel: 4.15.0-43-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.3 (Gtk 3.22.30-1ubuntu1)
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop System: Hewlett-Packard product: HP Compaq 6000 Pro MT PC serial: N/A
           Mobo: Hewlett-Packard model: 3048h serial: N/A
           BIOS: Hewlett-Packard v: 786G2 v01.09 date: 08/25/2009


CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) 
           arch: Penryn rev.10 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11969
           clock speeds: max: 3000 MHz 1: 2094 MHz 2: 2370 MHz
Graphics:  Card: Intel 4 Series Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel Q45/Q43
           version: 2.1 Mesa 18.0.5 Direct Render: Yes
Audio:     Card-1 Intel 82801JD/DO (ICH10 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Logitech Webcam B500 driver: USB Audio usb-ID: 001-004
           Sound: Advanced Linux Sound Architecture v: k4.15.0-43-generic
Network:   Card: Intel 82567LM-3 Gigabit Network Connection
           driver: e1000e v: 3.2.6-k port: 1100 bus-ID: 00:19.0
           IF: enp0s25 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1162.3GB (52.1% used)
           ID-1: /dev/sda model: ST3160815AS size: 160.0GB temp: 38C
           ID-2: /dev/sdb model: WDC_WD10EURX size: 1000.2GB temp: 35C
           ID-3: USB /dev/sdg model: SM/xD size: 2.1GB temp: 0C
Partition: ID-1: / size: 144G used: 82G (60%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 3.21GB used: 2.28GB (71%)
           fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 270 Uptime: 4 days Memory: 3077.0/5832.7MB
           Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 


I've been doing some reading some say it's the video drivers and to uninstall them, then reinstall them. but on the 2 pages I read this does not fix the problem. So I did not bother trying, also the info was a little vague on the how to. So I did not want to take the chance.

---

### Post by EZZ9 on 2019-01-24
No solution??

---

### Post by #&amp;thj^% on 2019-01-24
Can you give us the return from:
```
cat /etc/systemd/system/display-manager.service
```

---

### Post by EZZ9 on 2019-02-25
[Unit]
Description=Light Display Manager
Documentation=man:lightdm(1)
Conflicts=getty@tty7.service plymouth-quit.service
After=systemd-user-sessions.service [email]getty@tty7.servic[/email]e plymouth-quit.service


[Service]
# temporary safety check until all DMs are converted to correct
# display-manager.service symlink handling
ExecStartPre=/bin/sh -c '[ "$(basename $(cat /etc/X11/default-display-manager 2>/dev/null))" = "lightdm" ]'
ExecStart=/usr/sbin/lightdm
Restart=always
BusName=org.freedesktop.DisplayManager

OK back home now.
I've tried a few thing still not working I also see menus flickering.

---

