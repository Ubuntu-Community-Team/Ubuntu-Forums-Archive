---
title: "Latest Upgrades Broke Desktop Effects/Compiz-Fusion"
date: 2008-06-16
forum: General Help
---

### Post by jpw27 on 2008-06-16
I just installed some upgrades via update-manager, and after I restarted, Desktop Effects and Compiz-Fusion had broken.  Going into System >> Preferences >> Appearance and changing from "None" to anything else causes the tops of all windows to disappear, as does running "compiz --replace", and none of the Compiz Fusion plug-ins work.  "emerald --replace" does nothing visible.

Video card is an nVidia 8800GT with drivers 173.14.09.

Packages that involved in the upgrade that broke it.
```

Upgraded the following packages:
cpp (4:4.2.3-1ubuntu5) to 4:4.2.3-1ubuntu6
deskbar-applet (2.22.1-0ubuntu1) to 2.22.2.1-0ubuntu1
evolution-exchange (2.22.1-0ubuntu1) to 2.22.2-0ubuntu1
g++ (4:4.2.3-1ubuntu5) to 4:4.2.3-1ubuntu6
gcc (4:4.2.3-1ubuntu5) to 4:4.2.3-1ubuntu6
gdc (4.2.3-1ubuntu5) to 4.2.3-1ubuntu6
gij (4:4.2.3-1ubuntu5) to 4:4.2.3-1ubuntu6
gnome-cards-data (1:2.22.1.1-0ubuntu3) to 1:2.22.2.1-0ubuntu1
gnome-games (1:2.22.1.1-0ubuntu3) to 1:2.22.2.1-0ubuntu1
gnome-games-data (1:2.22.1.1-0ubuntu3) to 1:2.22.2.1-0ubuntu1
language-pack-en (1:8.04+20080415) to 1:8.04+20080527
language-pack-en-base (1:8.04+20080415) to 1:8.04+20080527
libgcj-bc (4.2.3-1ubuntu5) to 4.2.3-1ubuntu6
libgcj-common (1:4.2.3-1ubuntu5) to 1:4.2.3-1ubuntu6
libldap-2.4-2 (2.4.7-6ubuntu4.1) to 2.4.7-6ubuntu4.2
libldap2-dev (2.4.7-6ubuntu4.1) to 2.4.7-6ubuntu4.2
liblircclient-dev (0.8.3~pre1-0ubuntu7) to 0.8.3~pre1-0ubuntu7.1
liblircclient0 (0.8.3~pre1-0ubuntu7) to 0.8.3~pre1-0ubuntu7.1
libparted1.7-1 (1.7.1-5.1ubuntu9) to 1.7.1-5.1ubuntu9.1
openssl-blacklist (0.1-0ubuntu0.8.04.4) to 0.3.3+0.4-0ubuntu0.8.04.1
openvpn (2.1~rc7-1ubuntu3.2) to 2.1~rc7-1ubuntu3.3
parted (1.7.1-5.1ubuntu9) to 1.7.1-5.1ubuntu9.1
pciutils (1:2.2.4-1.1ubuntu3) to 1:2.2.4-1.1ubuntu4
pm-utils (0.99.2-3ubuntu9) to 0.99.2-3ubuntu10
xserver-xorg-core (2:1.4.1~git20080131-1ubuntu9) to 2:1.4.1~git20080131-1ubuntu9.2
xserver-xorg-video-intel (2:2.2.1-1ubuntu13) to 2:2.2.1-1ubuntu13.4

Upgraded the following packages:
app-install-data (0.5.10.2) to 0.5.10.3
evolution (2.22.2-0ubuntu1.2) to 2.22.2-0ubuntu1.3
evolution-common (2.22.2-0ubuntu1.2) to 2.22.2-0ubuntu1.3
evolution-plugins (2.22.2-0ubuntu1.2) to 2.22.2-0ubuntu1.3
file (4.21-3) to 4.21-3ubuntu1
gnome-app-install (0.5.2.7-0ubuntu1) to 0.5.2.8-0ubuntu1
gnome-applets (2.22.2-0ubuntu1) to 2.22.2-0ubuntu2
gnome-applets-data (2.22.2-0ubuntu1) to 2.22.2-0ubuntu2
klibc-utils (1.5.7-4ubuntu3) to 1.5.7-4ubuntu4
libdeskbar-tracker (0.6.6-0ubuntu3) to 0.6.6-0ubuntu3.8.04.1
libklibc (1.5.7-4ubuntu3) to 1.5.7-4ubuntu4
libmagic1 (4.21-3) to 4.21-3ubuntu1
libpolkit-gnome0 (0.7-2ubuntu1) to 0.7-2ubuntu1.1
libtracker-gtk0 (0.6.6-0ubuntu3) to 0.6.6-0ubuntu3.8.04.1
libtrackerclient0 (0.6.6-0ubuntu3) to 0.6.6-0ubuntu3.8.04.1
notification-daemon (0.3.7-1ubuntu11) to 0.3.7-1ubuntu11.2
policykit-gnome (0.7-2ubuntu1) to 0.7-2ubuntu1.1
tracker (0.6.6-0ubuntu3) to 0.6.6-0ubuntu3.8.04.1
tracker-search-tool (0.6.6-0ubuntu3) to 0.6.6-0ubuntu3.8.04.1

```

The first chunk was the first time I ran it, than after that all installed I hit "Check", and the second chunk came up for upgrades.  Obviously, xserver-xorg-core and xserver-xorg-video-intel are candidates for the problem, but I don't know if/how I can undo those updates.

---

### Post by techstop on 2008-06-16
Do a search. It's been discussed plenty of times. The xorg update is responsible. Just reinstall your video driver to fix it.

---

### Post by jpw27 on 2008-06-17
That was one of the things I already tried.  I installed 173.14.09 and 173.08, and neither of them worked.  "compiz --replace" and "emerald --replace" have the same effects under each driver.

---

### Post by techstop on 2008-06-17
OK, sorry, try running the Compiz-Check script found here;

[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by jpw27 on 2008-06-17
Compiz-Check output:
```

jason@jason-ubuntu:~/Desktop$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8800 GT (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

Extra info which may or may not be related (ignore if not):  After the upgrades, when using kernel 2.6.24.7 (the one I normally use), after booting up Ctrl + Alt + F1-6 does not bring up a terminal.

---

### Post by techstop on 2008-06-17
And so when you run "compiz --replace" or "emerald --replace" in a terminal, do you get any error messages?

EDIT: Why is your kernel so old? The latest is;

2.6.24-19-generic

---

### Post by jpw27 on 2008-06-17
"compiz --replace" results in loss of window decoration, but no output.  (Is there a verbose option, "-v" isn't recognized".  "emerald --replace" just sits there and does nothing, also with no output.

Regarding my kernel, I use the kernels from kernel.org.  Sound is iffy for me with 2.6.25 kernels, so I use 24.7, which is the newest 24 kernel.  However, as I said, tty's are broken with 24.7, so I'm just using 2.6.24-16-generic, which is the newest Ubuntu kernel I have.

---

### Post by techstop on 2008-06-17
So when I run compiz --replace in a terminal (ie Applications>Accessories>Terminal) I get the following;

```
compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:01d8 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

Are you telling me you get nothing at all? 

If your window decorations are disappearing, it sounds like compiz is running, but not emerald.

Try to install compizconfig-settings-manager, then open it up under System>Preferences>Advanced Desktop Effects Settings.

Open the Window Decorations plugin, then enter

```
emerald --replace
```

in the command text box. Log out, restart X with Ctrl + Alt + Backspace, then log back in. Hopefully compiz should be working and you should have your window decorations.

---

### Post by jpw27 on 2008-06-17
Yes, I get nothing when running "compiz --replace".  It seems like Compiz has started, because the screen restarts, and than all my open windows reappear with no decoration and no keyboard shortcuts work.  All of my settings are still in ccsm, so that's working, it's just that starting Compiz results in no window decoration and Compiz Fusion not actually working.

---

### Post by techstop on 2008-06-17
OK, I'm beat then. Sorry. :confused:

---

### Post by jpw27 on 2008-06-17
No problem, thanks for the help.

---

### Post by jpw27 on 2008-06-18
Just for the record, using the compiz-git script and than running "fusion-icon" fixed it for me.  I don't know what the problem was, but it worked :)

Edit:  FWIW, I also see some significant speed increases between 173.08 and 173.14.09 (with the latter being the better).  Also, a recompile/install of the 2.6.24.7 kernel fixed the tty problem.

---

