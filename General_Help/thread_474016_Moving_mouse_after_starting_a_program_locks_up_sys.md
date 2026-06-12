---
title: "Moving mouse after starting a program locks up system"
date: 2007-06-14
forum: General Help
---

### Post by jcsewell on 2007-06-14
I have a new install of Feisty, all updates installed.  If I click on an icon in my launcher area and then immediately move my mouse, the entire system locks up hard.  The mouse stops moving and the animated busy cusrsor stops animating.  The system doesn't respond to left or right clicks and no key presses.  numlock and capslock won't even toggle.  The only way out is to hit reset on the tower.

I have most frequently seen with firefox, but other programs do it too.  I installed Thunderbird and put it on the launcher and it does to too.

It seems if I click the laucnher and am very careful not to move my mouse, the program starts and seems to run OK.  It only seems to be a problem if I move the mouse immediately when starting a program.

Where should I look to troubleshoot this?


-James

---

### Post by shae on 2007-06-14
could you post the results of these:
```
cat /var/log/Xorg.0.log |grep EE
```
```
cat /var/log/Xorg.0.log |grep WW
```

---

### Post by jcsewell on 2007-06-14
jsewell@jsewell-desktop:~$ cat /var/log/Xorg.0.log |grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
jsewell@jsewell-desktop:~$ cat /var/log/Xorg.0.log |grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
jsewell@jsewell-desktop:~$

---

### Post by shae on 2007-06-14
What video card are you running?

---

### Post by jcsewell on 2007-06-14
jsewell@jsewell-desktop:/var/log$ cat Xorg.0.log |grep -i nvidia
(**) |   |-->Device "nVidia Corporation G70 [GeForce 7600 GS]"
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xd0000000/24, 0xc0000000/28, 0xd1000000/24, I/O @ 0xa000/7, BIOS @ 0xd2000000/17
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,

---

### Post by jcsewell on 2007-06-24
The problem seems to be somewhat more complex.  I've now noted at least two lockups on the login screen after being left for some time with inactivity.  So something is seriously hosed on this system.

What log files should I be checking and what do I want to see?

Since my last post, I have re-installed the system with an Edgy release CD.  My original install was with a Feisty beta CD which I then upgraded all packages and thought that put me at full released Feisty.  To make sure there was no Feisty beta cruft, I re-installed with the released Edgy CD, upgraded all packages to get to most up-to-date Edgy, then did the dist-upgrade with the package manager to 7.04.

I guess the next thing to do is to re-install using the released Feisty CD (I've just been too lazy to download and burn it until now).  I suppose there could be still cruft from Edgy that's hosing me up.


-James

---

