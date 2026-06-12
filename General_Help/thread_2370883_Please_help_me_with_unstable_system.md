---
title: "Please help me with unstable system"
date: 2017-09-08
forum: General Help
---

### Post by jmh72 on 2017-09-08
I hate to look a gift horse in the mouth, but I seriously have to reinstall Ubuntu, and its derivatives, on a constant basis. It's great that it's free, but it's not great that I can't get anything serious done.

I really need help. This is a production machine that took a long time to set up, and it's acting unstable.

By unstable these are some of the symptoms I mean:

[LIST]
[*]The system keeps locking up.
[*]Links in my browser won't react to clicks.
[*]Ubuntu keeps report errors to HQ. (I turned these errors off and don't know how to turn it back on.)
[*]Cascading freezes: One program will suddenly crash (inkscape), and then one after the other, all programs freeze, and I have to do a hard reset.
[*]Booting up suddenly takes much longer. The screen goes black for up to a minute, where as it didn't before.
[*]Booting down takes up to five minutes with constant "stop job" warnings.
[*]The mouse starts acting without clicks: It starts highlighting text by itself and moving scrollbars by itself.
[/LIST]

All kinds of buggy situations...

I don't know what I can tell you at this point that would help. I have plenty of hardware: 12gb ram, 1 TB of space, 2+ Ghz processor.
Ubuntu 17.04. I've tried Mate, Cinnamon, XFEC4 desktops, Link Mint 16+, Ubuntu 14+. It seriously took me a week to set up this dual-boot system (win7), the servers (apache2 + MySQL), along with all the design and communication software I need, and remote server and network location configurations.

I really appreciate you helping me get to the bottom of this. Something is really wrong when you have to wipe out your computer and start from scratch every 3 months or less.

PS: I have moderate experience as I switched to Linux about 5 years ago.

Thanks!

---

### Post by vasa1 on 2017-09-08
If you can manage to install *inxi*, please post the output of```
inxi -Fxzc0
```

---

### Post by jmh72 on 2017-09-08
Thank goodness! Someone replied quickly. I just had to hard reset again, and trying to post this message was difficult, because all the links in Chrome and Firefox won't work.

I just did an minor upgrade and received this error message. I have no idea if it has any relevance, but I've reinstalled xfe-themes as that was the suggestion.

```
Unpacking xfe-themes (1.42-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-oGFqDa/12-xfe-themes_1.42-1_all.deb (--unpack):
 trying to overwrite '/usr/share/xfe/icons/gnome-theme/a_16x16.png', which is also in package xfe 1.42-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
```

The output for [COLOR=#000000][FONT=&amp]inxi -Fxzc0 is:

[/FONT][/COLOR]```
System:    Host: rhino-Latitude-3540 Kernel: 4.10.0-33-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: MATE 1.18.0 (Gtk 3.22.11) Distro: Ubuntu 17.04
Machine:   Device: portable System: Dell product: Latitude 3540 v: A06
           Mobo: Dell model: 0MC4K5 v: A00 UEFI: Dell v: A06 date: 04/17/2014
Battery    BAT1: charge: 22.1 Wh 100.0% condition: 22.1/28.0 Wh (79%)
           model: SDI DELL XRDW246O status: Full
CPU:       Dual core Intel Core i5-4210U (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9578
           clock speeds: max: 2700 MHz 1: 2400 MHz 2: 2400 MHz 3: 2668 MHz
           4: 2623 MHz
Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.org 1.19.3 drivers: modesetting (unloaded: fbdev,vesa)
           tty size: 80x24 Advanced Data: N/A for root
Audio:     Card Intel 8 Series HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.10.0-33-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 3000 bus-ID: 01:00.0
           IF: enp1s0 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           driver: ath9k bus-ID: 02:00.0
           IF: wlp2s0 state: down mac: <filter>
           Card-3: Atheros usb-ID: 001-009
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 1254.3GB (7.5% used)
           ID-1: /dev/sda model: ST500LM000 size: 500.1GB temp: 42C
           ID-2: USB /dev/sdb model: USB_Disk size: 4.0GB temp: 0C
           ID-3: USB /dev/sdc model: External_USB_3.0 size: 750.2GB temp: 0C
Partition: ID-1: / size: 229G used: 50G (23%) fs: ext4 dev: /dev/sda4
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 60.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 3300
Info:      Processes: 274 Uptime: 5 min Memory: 2369.1/11926.5MB
           Init: systemd runlevel: 5 Gcc sys: 6.3.0
           Client: Shell (bash 4.4.71) inxi: 2.3.8
```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by jmh72 on 2017-09-08
Bump

---

### Post by wildmanne39 on 2017-09-08
Please be patient, you can bump your post once every twelve hours, remember we are a community of volunteers in different time zones and the person that knows the answer may not be on yet.

---

### Post by cmcanulty on 2017-09-08
try some troubleshooting apps. First gnome-system-monitor it will give you cpu and ram for each running process. Sometime one errant app is grabbing 100% cpu. Also top and install  htop which has an interactive interface. I believe top in included in ubuntu.

[https://www.lifewire.com/linux-top-command-2201163]("https://www.lifewire.com/linux-top-command-2201163")

[URL="http://hisham.hm/htop/[/URL]

to turn error reporting on or off sudo or gksu to /etc/default/apport and set enabled to =1 or to turn off set enabled to =0

---

### Post by jmh72 on 2017-09-08
> **wildmanne39 said:**
> Please be patient, you can bump your post once every twelve hours, remember we are a community of volunteers in different time zones and the person that knows the answer may not be on yet.

Okay. Thanks for that information. I appreciate it.

---

### Post by jmh72 on 2017-09-08
> **cmcanulty said:**
> to turn error reporting on or off sudo or gksu to /etc/default/apport and set enabled to =1 or to turn off set enabled to =0

Brilliant! Thank you for that. I turned them back on. I tried htop a few days ago. I couldn't find anything using more that 13% of system resources, and it lasted for a second or so.

In the meanwhile. I've removed every desktop that isn't MATE, and I'm going for a reboot now as soon as I reinstall MATE.

---

### Post by sp40140 on 2017-09-08
You shouldn't be running PRODUCTION server with database server AND apache on a laptop along with other applications. Laptop / mobile cpus aren't designed for this type of workload. 
From experience I can guess that it's related to over heating hardware when under load as laptops are not good with heat management compared to desktops.
Have you been able to reproduce the issues on win7 side? if not, are you running same workload on win 7?
This could also be related to failing hardware like RAM or HDD. But that can be easily reproduced in win7.
Also, when you say you have tried multiple flavors, have you cleanly installed those os? If so, it's very unlikely that all the os have same problems.

Also, Why would you have a prod server dualboot?

Edit:
You can check /var/log directory for any errors/flags.

---

### Post by jmh72 on 2017-09-08
I understand. MySQL came with LAMP. Perhaps I should have said development machine. I do a lot of design work and video conferencing on this laptop. Apache2 is for web development only. Unless I'm looking at something on localhost, I don't think about servers at all. The rest of my work is done in copy and images. So I'm using Libreoffice/Inkscape/Gimp a lot. The only cron I've set up is a nightly backup to an external drive. Besides email apps, PIM, graphics, writing, surfing, sometimes small audio and video jobs, this thing really isn't that stretched. But my whole life is in this computer. I can't use a desktop. I travel too much.

I've never come across signs of overheating. 

As far as flavors... they don't all exhibit the same symptoms, and the installs are always fresh. I checked the integrity of this download, then downloaded it again after another faulty install, and checked again. It passed both times. There are different problems each time with each flavor. However, the one consistent problem I have is that I cannot maintain a stable platform using Ubuntu on any laptop I've owned, and I don't know why. (I haven't had a desktop in over 13 years.)

There are no problems on the Windows 7 side that are occurring in the Ubuntu side. Windows 7 is fine, although really bulky, super slow, and everyone on the planet is trying to sell you something. :-)

I use dual-boot because some of the remote platforms I need to use only work with a Windows OS.

---

### Post by ian-weisser on 2017-09-08
> **jmh72 said:**
> ```
Unpacking xfe-themes (1.42-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-oGFqDa/12-xfe-themes_1.42-1_all.deb (--unpack):
 trying to overwrite '/usr/share/xfe/icons/gnome-theme/a_16x16.png', which is also in package xfe 1.42-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
```

Those apt errors indicate a self-inflicted package conflict instead of an instability problem with Ubuntu or Linux.
The package *12-xfe-themes_1.42-1_all.deb* is incompatible with your installed version of Xfce.
This kind of incompatibility problem happens with non-Ubuntu sources, or wrong-version Ubuntu sources.

I've been using Linux and Ubuntu for over a decade. It's rock solid...if your computing practices are solid.
If you are repeatedly suffering instability, then we gently offer reconsidering your design and practices.

---

### Post by cmcanulty on 2017-09-09
Did you go into synaptic-status box near left bottom, click installed near top left , then edit-fix broken packages?

---

### Post by jmh72 on 2017-09-11
Thanks everyone. I'm still interested in talking about this. If my admin skills are that bad, does anyone know of an admin simplified guide?... I honestly don't need rocket science.

As for broken packages, thanks for the suggestion. There are none.

---

### Post by cmcanulty on 2017-09-11
A good book is "Linux Administration A Beginner's Guide" by Wale Soyinka


a bit more advanced

"A Practical Guide to Linux Commands, Editors, and Shell Programming" by Mark G. Sobell

---

