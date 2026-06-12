---
title: "I can't get the trial to work."
date: 2008-05-18
forum: General Help
---

### Post by MarcusGarvey on 2008-05-18
I wanted to do the trial thing from the CD where you don't have to install it to try it out. It gets all the way to the login part, I hear the sound for it after it logs in... and before the sound finishes, my screen goes black and I can't do anything. The mouse is there and I can move it, and if I use the scroll wheel I see two boxes in the middle of the screen. Sometimes it will also just go back to the login screen and try to login again.

---

### Post by MarcusGarvey on 2008-05-18
Any ideas on what the problem is and how to fix it?

---

### Post by Sef on 2008-05-18
1) What are your system specs, including your video card?

2) Don't bump threads unless 24 hours have gone by.  Otherwise you could get an infraction.

3) The Live CD is not a trial version.  It is an operating system that runs off of the cd.  Installing it is an option after booting.  If you so desire, you can just run the live cd without installing the os at all.

---

### Post by MarcusGarvey on 2008-05-18
> **Sef said:**
> 1) What are your system specs, including your video card?

2) Don't bump threads unless 24 hours have gone by.  Otherwise you could get an infraction.

3) The Live CD is not a trial version.  It is an operating system that runs off of the cd.  Installing it is an option after booting.  If you so desire, you can just run the live cd without installing the os at all.

I thought the Live CD had certain things disabled? Also I did not know the rule on bumping, sorry.

[Here is my PC.](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00619308&lc=en&cc=us&product=1843651&dlc=en)

---

### Post by phidia on 2008-05-19
> **MarcusGarvey said:**
> I thought the Live CD had certain things disabled? Also I did not know the rule on bumping, sorry.

[Here is my PC.](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00619308&lc=en&cc=us&product=1843651&dlc=en)

You have an ATI Radeon GPU/video card. To enable the best quality video read the how to [here]("http://ubuntuforums.org/showthread.php?t=515573"),
and view more ATI card specifics [here]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti").

If you don't have a GUI desktop on start up you can try opening commandline. Press the  Alt+Ctrl+F1 keys and then type dpkg-reconfigure xserver-xorg. You can generally leave any question you don't know blank. What you want to do is select the vesa driver for you card and then when you have a gui desktop refer to the links for installing the proprietary ATI driver.
Hope that helps.

---

