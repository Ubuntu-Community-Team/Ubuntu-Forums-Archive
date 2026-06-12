---
title: "Startx wont work"
date: 2017-11-11
forum: General Help
---

### Post by warmango on 2017-11-11
Simply put, im using Linux Subsystem for Windows, which used 16.04, but when i try to use STARTX, i receive this error 
```
X.Org X Server 1.18.4Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
Current Operating System: Linux DESKTOP-P02JORL 4.4.0-43-Microsoft #1-Microsoft Wed Dec 31 14:42:53 PST 2014 x86_64
Kernel command line: BOOT_IMAGE=/kernel init=/init ro
Build Date: 13 October 2017  01:57:05PM
xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.33.6
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/home/Zach/.local/share/xorg/Xorg.1.log", Time: Sat Nov 11 07:31:43 2017
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE)
Fatal server error:
(EE) xf86OpenConsole: Switching VT failed
(EE)
(EE)
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
(EE) Please also check the log file at "/home/Zach/.local/share/xorg/Xorg.1.log" for additional information.
(EE)
(EE) Server terminated with error (1). Closing log file.
```

im trying to launch either the Lubuntu Desktop environment, or the MATE, whichever i can get to load, id be happy

---

### Post by efflandt on 2017-11-11
I am just trying to wrap my head around what you are actually running, since it mentions Microsoft. Is this something that is supposed to run in Microsoft Windows, or Wubi (no longer supported), or in a virtual machine in Windows? Linux typically uses vt1-vt6 for text terminals and vt7 for X, but your system is apparently having a problem switching to vt7 for X. What hardware do you have, including graphics hardware and drivers?

I have run various Linux versions in (Oracle) Virtualbox, but on an Ubuntu host, I have not run Windows in virtualbox or virtualbox on a Windows host. If you run something under Windows, it could be exposed to Windows vulnerabilities and slowness (with all the antivirus and malicious software scanning and checking for and installing updates). I recently had a low end Win10 laptop spend 8 hours alternately hogging my Internet and 100% disk access, and even after settling down some, alternating between 40% cpu time and 100% disk access installing major updates for about 8 hours including rebooting several times. Fortunately the laptop also dual boots Ubuntu 16.04, so I can use my Java stock/option trading platform (thinkorswim) in Ubuntu on that laptop while Chromecasting investing education (not available in Linux) from my Android phone to the 32" 1080p HDTV I use as a monitor for my desktop PC.

---

### Post by Holger_Gehrke on 2017-11-11
A short google for "Linux subsystem for windows xserver" led me to [this article]("https://www.howtogeek.com/261575/how-to-run-graphical-linux-desktop-applications-from-windows-10s-bash-shell/"). You need an xserver on Windows to run graphical Linux applications in the Linux subsystem for Windows.

Holger

---

### Post by warmango on 2017-11-11
Windows 10 provides a Feature called "Windows Subsystem for Linux," Which allows you to run a full Ubuntu Bash Shell, within windows, no restrictions other than having no Native GUI support

---

