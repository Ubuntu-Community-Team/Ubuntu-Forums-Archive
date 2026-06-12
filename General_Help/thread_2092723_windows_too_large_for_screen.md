---
title: "windows too large for screen"
date: 2012-12-08
forum: General Help
---

### Post by iop693 on 2012-12-08
I have noticed that on my netbook (samsung nc110) some program windows appear off of the screen as they are too large. Usually maximising fixes this, but not always. Is there any way to stop this from happening or shrink the windows as it's a bit of a pain? :)

Thanks in advance

---

### Post by Tom Collier on 2012-12-08
Happens a lot on my netbook, when the "save settings" or "apply" or "ok" buttons are not visible and below the bottom of the screen.

I just hold down the Alt key and use the left mouse button to move the window to the point where the mousable commands are visible. Not a permanent window resizing, but it works for me. YMMV.

---

### Post by Dennis N on 2012-12-08
> **Tom Collier said:**
> Happens a lot on my netbook, when the "save settings" or "apply" or "ok" buttons are not visible and below the bottom of the screen.



What version of Lubuntu are you using? I noticed this same problem in both Lubuntu 11.10 and 12.04, where the adjusted size of a window was not retained when reopened the next time. This problem is fixed in Lubuntu 12.10 - resize a program's window and the size is retained until changed by the user, even between sessions. This is also true for the "save as" window.

You work around this to some extent in Lubuntu 11.10 or 12.04 by decreasing the system default font size. This makes the windows smaller in size and they will fit.

---

### Post by Tom Collier on 2012-12-08
Using Lubuntu 12.04 on the netbook. Ubuntu 10.04/WinXP, on an older dual boot Toshiba Satellite with Centrino processor.

(Can't update that info in my profile because I haven't posted 50 times, yet, during the 3 or 4 years I've been on the forum.)

Settled on Lubuntu for the netbook (eeePC HD1200 ATOM processor) when Ubuntu 12.04 was just too big, slow and cumbersome on it.

---

### Post by iop693 on 2012-12-09
I'm on 12.04, the alt and drag works for the moment, thanks for that, shame there isn't really a way of stopping this from hppening.

---

### Post by Dennis N on 2012-12-09
> **iop693 said:**
> I'm on 12.04, the alt and drag works for the moment, thanks for that, shame there isn't really a way of stopping this from hppening.

Your best bet is to switch to Lubuntu 12.10 where these window-size problems and are no longer an issue (see post #3). If you are skeptical, try a live CD session and you will see that window resizing is persistent after reopening.

---

### Post by pj_kare on 2012-12-17
We are using Lubuntu 12:10 on a 1366x768 16:9 19" LCD monitor (1366x768 is it's maximum resolution), In 'Users and Groups' the 'Advanced Settings' window is too tall for the screen, the window cannot be made smaller vertically but can be made even taller, so we have to drag it as far as we can off the top of the screen, and set the Panel (bottom of screen) to "minimize when not in use" to be able to access the 'Cancel' and 'OK' Buttons.

---

### Post by Dennis N on 2012-12-18
> **pj_kare said:**
> We are using Lubuntu 12:10 on a 1366x768 16:9 19" LCD monitor (1366x768 is it's maximum resolution), In 'Users and Groups' the 'Advanced Settings' window is too tall for the screen, the window cannot be made smaller vertically but can be made even taller, so we have to drag it as far as we can off the top of the screen, and set the Panel (bottom of screen) to "minimize when not in use" to be able to access the 'Cancel' and 'OK' Buttons.

This is a known bug affecting gnome-system-tools 3.0.0.

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/1025094](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/1025094)

It was present in Lubuntu 12.04 as well. (The "save as" dialog, which also had a size problem in 12.04, has been fixed in Lubuntu 12.10 to retain its size between uses.)

---

### Post by GafftheHorse on 2013-03-01
I get this problem a lot less now (Ubuntu 12.10) than I did with earlier versions. On 11.10 (or maybe 11.04) during installation, all the installation windows were too long for the screen. Currently the one window that currently bugs me is the file properties in nautilus. There are others (widelands for example), I just use file properties the most often.

In openbox the maximise but is present and is an easy fix, but in Unity, there is only minimise or close.

I hope Ubuntu are sorting this out, for a distro that's aiming towards running on more and more (and varied) smaller screens this problem just reinforces the opinion that linux isn't 'ready' for maintream use. Not that this didn't happen when I had Xp on this netbook (it was on for so short a time and a good while ago I can't recall).

---

