---
title: "Screen Resolution Problems"
date: 2007-04-17
forum: General Help
---

### Post by OpEn_SoUrCe_RoCkS on 2007-04-17
Hi !

**Problem 1** - How do I set up a default screen resolution ?

When I boot in, it always puts my screen at 1024x768, but I would like it to be 1280x1024 default.

**Problem 2** - Now I have to use  	Code:
 	xrandr -s 1280x1024 
 every time, because I can't even change my resolution with the "Monitor and Display" section - it has absolutely no effect when I play with the slider.

How do I fix these problems ?

I'm running Kubuntu latest version.

TIA

---

### Post by SimonHickling on 2007-04-17
Have you tried 
```
 dpkg-reconfigure xserver-xorg
```to set the available resolutions?

---

### Post by OpEn_SoUrCe_RoCkS on 2007-04-18
I did, but I got mixed up because it said that checking all resolutions is the same as checking none.
Do I check the resolution that I want, or every res that I don't want ?

---

### Post by zeekay on 2007-04-18
I'd try just checking all the ones I don't want, since "checking all is the same as choosing none". Try testing it, might work. If it doesn't, try checking just the one you want.

I can't help you much on that, but if it doesn't work, you can go to xorg.conf and edit it manually, but I only recommend that if you really know what you're doing.

---

### Post by SimonHickling on 2007-04-18
Check the ones you want.  If that doesn't work let me know.

---

### Post by strabes on 2007-04-18
What kind of video card do you have?

---

