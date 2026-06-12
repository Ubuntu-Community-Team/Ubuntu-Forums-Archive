---
title: "Kubuntu Usplash Looks Odd"
date: 2007-01-15
forum: General Help
---

### Post by jlacroix on 2007-01-15
Kubuntu Usplash during bootup and shutdown looks very horrible, as if it is the low color version, if there is one.

Screenshot attached.

I noticed that only the 64-bit Kubuntu Usplash looks like this (I have the 64-bit version installed right now) and not the 32-bit version (which I used to have installed). 

Minor problem I know, but I wanna get rid of it.

---

### Post by crispy_420 on 2007-01-15
You can always completely remove usplash via apt. Then you will have scrolling text instead. Is that what you're looking for?

---

### Post by jlacroix on 2007-01-15
No, not exactly. I'm saying that the Kubuntu Usplash on my PC looks HORRIBLE. I just upgraded my PC, before Usplash looked cool, now since the upgrade, it shows less colors, the bar doesn't even animate properly.

---

### Post by Quillz on 2007-01-15
> **crispy_420 said:**
> You can always completely remove usplash via apt. Then you will have scrolling text instead. Is that what you're looking for?
Is it possible to replace the splash screen with another image, as opposed to removing it?

---

### Post by jlacroix on 2007-01-16
I vaguely remember a config file somewhere, perhaps my problem is related to something like that?

---

### Post by crispy_420 on 2007-01-18
It is possible to change usplash colors or even change the image completely. I have yet to try since stability is my main concern (don't want to mess my boot). Worst case scenario, if you screw up, you can always go to command line and remove usplash via apt.

But there is another option called spashy. Some other distros use it as it said to be easy to customise. Just what I've heard as I have yet to try.

---

### Post by jlacroix on 2007-01-18
I found a config file at /etc/usplash. I have no idea what to do with it though. Here's what's in it now:

```
# Usplash configuration file
xres=1024
yres=768

```

---

### Post by crispy_420 on 2007-01-18
Just an guess but that is the resolution of the splash. 1024x768

Just search the forums for a guide on customizing usplash. But if I remember correctly, you are limiting by color depth. As I said before, tweak it and if you mess up all that will happen is a old school boot (eg. no colors and just scrolling text).

---

