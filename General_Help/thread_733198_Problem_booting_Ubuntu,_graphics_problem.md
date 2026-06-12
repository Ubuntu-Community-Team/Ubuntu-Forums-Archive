---
title: "Problem booting Ubuntu, graphics problem?"
date: 2008-03-23
forum: General Help
---

### Post by Mortel on 2008-03-23
Alright, so, first off, please forgive me if this is a simple problem or something, I am not that great at actual things like Unix, which is why I installed Ubuntu, to try and learn from experience.  :)

Anyways, the Wubi installation went well.  I made sure not to boot into Ubuntu the first time Wubi wanted me to restart, all that is great.

The problem is, after I actually boot into Ubuntu, it shows files loading for a second or two, and then my monitor goes to a screen saying:

```
"Could not display this video mode"
```

It stays there for about 20 seconds, and then brings me to a screen that says:

```
"Failed to start the X server (your graphical interface).  it is likely that it is not set up correctly, would you like to view the X server output to diagnose the problem?"
```

After hitting yes, it says this:

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: ubuntu 2.6.20-15-generic #2 SMP Sun
(WW) I81O: No matching device section for instance (BUSID PCI:0:2:0) found
(EE) No devices detected
Fatal server error:
no screens found
```

Then after that, I can view another detailed log, but it's way too much to write down.
My video card is a Radeon 9250, and my monitor is a Dell E171FP, according to one of the logs.

Any help for this problem?  Thanks in advance.  :D

---

### Post by ago on 2008-03-24
Press esc at the countdown after selecting Ubuntu, and choose safe graphic mode

---

### Post by Mortel on 2008-03-24
Uhh, that option isn't even there for me...

Is there, like, a special command to boot into graphical safe mode?

---

### Post by ago on 2008-03-24
It's there after the first reboot after running wubi from windows.

If it's not there it means that the installation completed

Then press alt+ctrl+f1

Run

sudo dpkg-reconfigure xserver-xorg

select vesa and leave the other options at default

---

