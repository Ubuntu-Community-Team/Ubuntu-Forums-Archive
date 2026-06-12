---
title: "Dual Monitor Extended Desktop won't work"
date: 2008-03-27
forum: General Help
---

### Post by iThinkergoiMac on 2008-03-27
So I'm trying to get my IBM R50 to extend my desktop onto an external monitor. Windows decides to play all nice and dandy with it, but I can't get Ubuntu (7.10) to extend to it at all. It's not a terribly wonderful monitor, but it would be perfect for those times I want to put all the Gimp palettes on a different monitor (or watch a movie and browse the web).

It does function with Ubuntu, but only as a clone of the current monitor. And that only works if I start up the computer with it attached. The "Screens and Graphics" control panel shows the "secondary monitor" as disabled. My only option is to make it my main monitor, but if I apply those settings, it doesn't work either.

Any ideas?

---

### Post by overdrank on 2008-03-27
> **iThinkergoiMac said:**
> So I'm trying to get my IBM R50 to extend my desktop onto an external monitor. Windows decides to play all nice and dandy with it, but I can't get Ubuntu (7.10) to extend to it at all. It's not a terribly wonderful monitor, but it would be perfect for those times I want to put all the Gimp palettes on a different monitor (or watch a movie and browse the web).

It does function with Ubuntu, but only as a clone of the current monitor. And that only works if I start up the computer with it attached. The "Screens and Graphics" control panel shows the "secondary monitor" as disabled. My only option is to make it my main monitor, but if I apply those settings, it doesn't work either.

Any ideas?

Hi and what is the model of the graphics card?

---

### Post by virtuallinux on 2008-03-27
Well, if you've got an Nvidia card, we should be able to get you up and running without too much fuss, if it's Intel or ATI or anyone else, I'm afraid I won't be very helpful.  I can tell you one thing though, I've never had much luck with dual monitors using Ubuntu's "Screens and Graphics" dialogue.  Hopefully that will improve with time.

---

### Post by iThinkergoiMac on 2008-03-27
I have an ATI Radeon Mobility 7500. 32MB VRAM.

I have managed to get Compiz Fusion enabled, if that makes a difference.

---

### Post by virtuallinux on 2008-03-27
Well, I've not got much experience with ATI and Ubuntu, and a google search of "Ubuntu ATI 7500 Multiple Displays" didn't seem to turn up much (although you still may want to try it).  The best I can to for now is to refer you here:
[http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174")

---

### Post by iThinkergoiMac on 2008-03-27
I'll have to try the MergedFB at some point... I think it looks the most promising. I'll be sure to post back if it works or not.

---

### Post by iThinkergoiMac on 2008-03-27
MergedFB doesn't like me much... trying Xinerama...

---

### Post by iThinkergoiMac on 2008-03-27
Xinerama didn't work either. But it got closer... kind of.

First off, Xinerama forced my display to 800x600 (native res is 1400x1050), and caused the secondary monitor to always go in sleep mode. If I turned it off and back on, I would get a brief flash of the current desktop (clone).

So... that's it for tonight, I'll try again tomorrow if I have time. If not tomorrow or the day after, this will probably have to wait until the summer when I get back from school. At which point 8.04 will be out and I might have more luck with that.

---

