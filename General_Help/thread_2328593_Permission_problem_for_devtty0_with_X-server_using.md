---
title: "Permission problem for /dev/tty0 with X-server using xinit in 16.04"
date: 2016-06-22
forum: General Help
---

### Post by Mikkel_Kromann on 2016-06-22
Hi.

I have been running my favorite game through its own X-server (forgive me if I'm not using entirely correct wording, I'm by no means a X expert ...) since Ubuntu 13.04 or something.
Everything was running smoothly (and with much better game performance) until I upgraded to 16.04. Now starting my game with xinit results in a permission error:

```
$ xinit /home/mikr/bin/WoWrun64 -- :1 -br
X.Org X Server 1.18.3
Release Date: 2016-04-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.13.0-86-generic x86_64 Ubuntu
Current Operating System: Linux scrat 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-24-generic root=UUID=1346e355-5120-4563-9e27-28d965d357f4 ro quiet splash
Build Date: 18 May 2016  01:07:07AM
xorg-server 2:1.18.3-1ubuntu2.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.33.6
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/home/mikr/.local/share/xorg/Xorg.1.log", Time: Wed Jun 22 20:29:52 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
Fatal server error: 
[COLOR=#ff0000](EE) parse_vt_settings: Cannot open /dev/tty0 (No such file or directory)[/COLOR]
```

For your information, the content of the small script I'm running (WoWrun64) is this:
```
#!/bin/bash
setxkbmap -layout dk
WINEDEBUG=-all WINEPREFIX="/home/mikr/.wineWoW64" nice -n 1 /usr/bin/wine64 /home/mikr/WoW/Wow-64.exe

```
The error message indicates that /dev/tty0 does not exist. However, when ls'ing it, it is certainly there:

```
$ ls -l /dev/tty0
crw--w---- 1 root tty 4, 0 Jun 22 18:56 /dev/tty0
```

A small curiosity - maybe related, maybe not: When I press Ctrl+Alt+1, 2, ..., 6 I don't get up the usual tty's (this worked fine in 15.10). 
Instead, the screen becomes black (except for the mouse pointer, so I guess I must still be in X) and after a couple of seconds it returns to my Gnome desktop.

I've googled pretty extensively without luck, so I guess my problem is somewhat rare.
As I recall, I have software updated Ubuntu several times, so the install is not entirely fresh.

Any hints or suggestions?
Please ask for more debugging output if needed.
Thanks for your time and efforts :)

Mikkel

---

### Post by ventrical on 2016-06-22
If you go into grub could you try to boot from an earlier kernel?


Also .. just in case a package did not break in upgrade process try to do this first:

```

sudo dpkg --configure -a
then
sudo apt-get install -f

```

and then

```


sudo apt-get dist-upgrade


```

but I still think there is a kernel bind that did not happen.

my thoughts only.

regards..

---

### Post by Mikkel_Kromann on 2016-06-22
Hmm, I should have googled for 5 seconds more ...

[https://bugs.launchpad.net/ubuntu/+source/xinit/+bug/1562219](https://bugs.launchpad.net/ubuntu/+source/xinit/+bug/1562219)

However, the workaround described there 

[http://kodi.wiki/view/HOW-TO:Autostart_Kodi_for_Linux](http://kodi.wiki/view/HOW-TO:Autostart_Kodi_for_Linux)

seem to be for some sort of service with a very elaborate startup script and stuff going into systemd configuration and such.

Can someone explain to me just the most necessary bits of this workaround to get a simple program running?


/Mikkel

---

### Post by ventrical on 2016-06-22
ahhh systemd

You could try to install upstart and boot that way. It will come up in grub.

```

sudo apt-get install upstart

```

and then reboot.
Choose upstart and see if that helps.

regards..

Ok.. looked at your links. Perhaps installing upstart will not work.

regards..

---

### Post by Mikkel_Kromann on 2016-06-22
> You could try to install upstart and boot that way. It will come up in grub.

Ehrm ... Thank ... But my PC is just a normal Ubuntu desktop, which I use for other stuff than gaming as well.
As I understand upstart, this package will automatically start specified programs on boot.
That is not what I need.

But if you can point to specific features of upstart that will help with my permission problem, I'm all ears ...

---

### Post by ventrical on 2016-06-22
Specific feature is that your previous install before upgrade was booting from upstart.
Perhaps the program you are trying to run will not work with systemd , as has been often the case since it's inception into ubuntu. So the alternative is to install upstart for more legacy programs or apps that will cough and sputter on systemd.


regards..

> **Mikkel_Kromann said:**
> Hi.

A small curiosity - maybe related, maybe not: When I press Ctrl+Alt+1, 2, ..., 6 I don't get up the usual tty's (this worked fine in 15.10). 
Instead, the screen becomes black (except for the mouse pointer, so I guess I must still be in X) and after a couple of seconds it returns to my Gnome desktop.


Mikkel

Could you please install:

```

sudo apt-get inxi

```

and then post the results of:

```

inxi -Fxz

```

I am curious about your graphics adapter.. if it be nVidia ..etc..

Regards..

---

### Post by Mikkel_Kromann on 2016-06-22
It sure is NVidia.
The game I'm running is World of Warcraft ...
I can also say that when I run the game from inside my desktop I have no problems, besides a bit decreased performance.

```
$ inxi -Fxz
System:    Host: scrat Kernel: 4.4.0-24-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3) Distro: Ubuntu 16.04 xenial
Machine:   Mobo: MSI model: P67S-C43 (MS-7673) v: 1.0 Bios: American Megatrends v: V1.10 date: 03/31/2011
CPU:       Quad core Intel Core i5-2500 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 26340
           clock speeds: max: 3700 MHz 1: 1601 MHz 2: 1599 MHz 3: 1894 MHz 4: 1625 MHz
Graphics:  Card: NVIDIA GF114 [GeForce GTX 560] bus-ID: 01:00.0
           Display Server: X.Org 1.18.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 560/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 361.42 Direct Rendering: Yes
Audio:     Card-1 NVIDIA GF114 HDMI Audio Controller driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-3 SteelSeries ApS driver: USB Audio usb-ID: 001-007
           Sound: Advanced Linux Sound Architecture v: k4.4.0-24-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 05:00.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 500.1GB (43.3% used) ID-1: /dev/sda model: SAMSUNG_HD502HJ size: 500.1GB temp: 30C
Partition: ID-1: / size: 14G used: 7.1G (55%) fs: ext4 dev: /dev/sda5
           ID-2: swap-1 size: 4.00GB used: 0.04GB (1%) fs: swap dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.0C mobo: N/A gpu: 0.0:37C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 216 Uptime: 3:03 Memory: 1397.3/3924.5MB Init: systemd runlevel: 5 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.35
```

---

### Post by ventrical on 2016-06-22
> **Mikkel_Kromann said:**
> It sure is NVidia.
The game I'm running is World of Warcraft ...
I can also say that when I run the game from inside my desktop I have no problems, besides a bit decreased performance.

```
$ inxi -Fxz
System:    Host: scrat Kernel: 4.4.0-24-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3) Distro: Ubuntu 16.04 xenial
Machine:   Mobo: MSI model: P67S-C43 (MS-7673) v: 1.0 Bios: American Megatrends v: V1.10 date: 03/31/2011
CPU:       Quad core Intel Core i5-2500 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 26340
           clock speeds: max: 3700 MHz 1: 1601 MHz 2: 1599 MHz 3: 1894 MHz 4: 1625 MHz
Graphics:  Card: NVIDIA GF114 [GeForce GTX 560] bus-ID: 01:00.0
           Display Server: X.Org 1.18.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 560/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 361.42 Direct Rendering: Yes

```


All I know is that I had big problems with nVidia driver while running ubuntu-gnome desktop on xenial. In fact it broke one install completely.

  Perhaps I am a little out of my league here. I am more a development tester but  the best work-a-round we  do is remove the nVidia drivers and install nouveau... but it appears, according to your output from inxi, that everything is working so it is a permissions problem and I will set back a bit and let someone else respond. I certainly do not think that nVidia driver will produce the result you are reporting.

My apologies for being a little off track here.

Regards..

---

### Post by Mikkel_Kromann on 2016-06-22
Thanks for your efforts, Ventrical :)
I agree that it is probably not an nVidia issue - after all the game runs fine when not started in its own X-server.

Do you think it would be a better idea, if I also contributed to the bugtracker link I posted, and confirmed the bug with my issue?
I'd be willing to help and test out various proposals - it's just that I'm not qualified enough to dream up solutions myself.

---

### Post by ventrical on 2016-06-22
> **Mikkel_Kromann said:**
> Thanks for your efforts, Ventrical :)
I agree that it is probably not an nVidia issue - after all the game runs fine when not started in its own X-server.

Do you think it would be a better idea, if I also contributed to the bugtracker link I posted, and confirmed the bug with my issue?
I'd be willing to help and test out various proposals - it's just that I'm not qualified enough to dream up solutions myself.

Yes .. thats  a great idea. No qualifications needed here :) Your experience is the only prerequisite.  Also .. just wait .. i am sure someone will chime in. I know the problem you are talking about and I even think I fixed it once but I am tired right now and I forget :) You have to edit some xinit file...ummm xinit.r or an xinit.d file ... if somebody doesn't  reply or you haven't fixed it by then I'll  try to dig  up what I did.
Regards..

---

### Post by ventrical on 2016-06-22
Please see this post:

[http://ubuntuforums.org/showthread.php?t=2321892](http://ubuntuforums.org/showthread.php?t=2321892)

Could I suggest look at:

```

[COLOR=#c20cb9]**sudo**[/COLOR] gedit [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]X11[COLOR=#000000]**/**[/COLOR]Xwrapper.config

```

and change

```

allowed_users=console

to

allowed_users=anybody

```

the above from : [https://www.maketecheasier.com/run-multiple-x-sessions-without-virtualization](https://www.maketecheasier.com/run-multiple-x-sessions-without-virtualization)

regards..

---

### Post by Mikkel_Kromann on 2016-06-23
Thanks for the tip - unfortunately, no luck.
I also tried with the following option (which I found somewhere else):
```

need_root_rights = yes
```

No luck with that either.

Also tried to delete .Xauthority in my home folder (as suggested in the link you provided), but also no luck there.

---

### Post by Xo-Mige on 2016-06-25
I solved this problem for me with by installing [xserver-xorg-legacy]
the [(EE) parse_vt_settings: Cannot open /dev/tty0 (No such file or directory)]

(I don't know how to change colors here!! er..) 
in my /etc/X11/Xwrapper.config
```
# Xwrapper.config (Debian X Window System server wrapper configuration file)
#
# This file was generated by the post-installation script of the x11-common
# package using values from the debconf database.
#
# See the Xwrapper.config(5) manual page for more information.
#
# This file is automatically updated on upgrades of the x11-common package
# *only* if it has not been modified since the last upgrade of that package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command as root:
#   dpkg-reconfigure x11-common
allowed_users=anybody
```

```

sudo apt install xserver-xorg-legacy

```

I hope that helps you :popcorn:

---

### Post by Mikkel_Kromann on 2016-06-26
Thanks Xo-Mige.

That completely solved the problem.
Seems that this might be related to NVIDIA drivers (which I have) ...

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1525735](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1525735)

---

### Post by ram.sundar on 2016-10-19
I am having the same problem. I have lubuntu(14.04) installed on an old dell laptop. When I tried to install legacy xserver, I get the error "E: Package 'xserver-xorg-legacy' has no installation candidate".
lspci shows I have a Intel Express integrated graphics controller. Not sure if that is the problem. Should I try an old version of lubuntu or should I go for ubuntu.

Thanks
Ram

---

### Post by cariboo on 2016-10-19
> **ram.sundar said:**
> I am having the same problem. I have lubuntu(14.04) installed on an old dell laptop. When I tried to install legacy xserver, I get the error "E: Package 'xserver-xorg-legacy' has no installation candidate".
lspci shows I have a Intel Express integrated graphics controller. Not sure if that is the problem. Should I try an old version of lubuntu or should I go for ubuntu.

Thanks
Ram

14.04 is to old to use xserver-xorg-legacy, if you want to try the solution posted in this thread, you need to upgrade to 16.04.

If you don't know if a package is available for your version use:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

I get the following result for xserver-xorg-legacy:

[http://packages.ubuntu.com/search?keywords=xserver-xorg-legacy&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=xserver-xorg-legacy&searchon=names&suite=all&section=all)

---

