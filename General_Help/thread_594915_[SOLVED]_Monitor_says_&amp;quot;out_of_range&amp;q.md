---
title: "[SOLVED] Monitor says &amp;quot;out of range&amp;quot;"
date: 2007-10-28
forum: General Help
---

### Post by hp59dk on 2007-10-28
I have a problem with the "ATI accelerated graphics driver".

My graphics card is RV370 5B60 [Radeon X3000 (PCIE)]

My flat panel screen is "e-yama" model "17JN1-S", 50/60Hz


I have installed Ubuntu a couple of times now, It is all right until I allow the restricted driver to run. After that I have no access to my computer after the log in screen. It only says "out of range".

1) What can I do about it?

2) How can I go back to the Open Source driver if it doesn't work?

3) Should I/can I "tell" Ubuntu what sort of screen I have?

There is others here with similar problems, but I can't figure out if the advise there apply to my problem. I am sorry if there is already an answer ... 

Thank You for any help
Yours Hans Pedersen

---

### Post by taurus on 2007-10-28
Press <Ctrl><Alt>F2 to log in a console.  Then, you can either edit /etc/X11/xorg.conf or reconfigure your X again with

Edit:
```
sudo nano -Bw /etc/X11/xorg.conf
```
Save it with <Ctrl>o and exit with <Ctrl>x.

Reconfigure X:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by hp59dk on 2007-10-28
Thank You Taurus.
Shoud I do this before I activate the ATI driver?

---

### Post by taurus on 2007-10-28
Only do it if X all screws up and you cannot boot into GUI login screen.

---

### Post by hp59dk on 2007-10-29
I am editing xorg.conf. The sections "monitor" and "Screen"  says:

Section "Monitor"
Identifier "generic monitor"
Option "DPMS"
Horizsync 30-70
Vertrefresh 50-160
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
Monitor "Generic Monitor"
Defaultdepth 24


Well .... what should i write instead?

Any help is most welcome

Yours Hans Pedersen

---

### Post by Maestro23 on 2007-10-29
> **hp59dk said:**
> I am editing xorg.conf. The sections "monitor" and "Screen"  says:

Section "Monitor"
Identifier "generic monitor"
Option "DPMS"
Horizsync 30-70
Vertrefresh 50-160
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
Monitor "Generic Monitor"
Defaultdepth 24


Well .... what should i write instead?

Any help is most welcome

Yours Hans Pedersen

Are those the correct Horiz/Vert specs for you flat panel?  If not, get the correct specs and input them there.

---

### Post by hp59dk on 2007-10-29
Google gave me nothing, and the only information i have is the 50/60 Hz on the label of the flat panel. I try these numbers.

I tried both methods, but i am not clever enough to configure it. Now it is running in low graphics mode.

I make a new install, and I will never touch the ATI driver again ... not tonight at least :)

Hans Pedersen

---

### Post by hp59dk on 2008-01-05
I am now addressing my problem again.
Some programs (Second Life) is crashing without the restricted driver.

I activated the restricted driver.
Again the "out of range" problem appears.
This post helps me: [http://ubuntuforums.org/showthread.php?t=651235](http://ubuntuforums.org/showthread.php?t=651235) 
So I at least can come back to the Ubuntu driver and log in. The restricted driver was disabled.
I enabled it again, and now everything is working!

---

