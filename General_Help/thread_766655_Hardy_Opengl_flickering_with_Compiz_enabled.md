---
title: "Hardy: Opengl flickering with Compiz enabled"
date: 2008-04-25
forum: General Help
---

### Post by imbjr on 2008-04-25
First, I noticed that Compiz effect transitions in Heron were not as smooth as they are under Gutsy.

Then I fired up glxgears and saw it flicker. Furthermore, if I drag the gears window about, the gears do not keep track with the window as they used to. It's possible to get the gears display area to overlay other windows.

Now, I can resolve this by disabling Compiz or installing XGL server. The server option would appear to be a bit of not-needed from what I've read (I've also seen comments that suggest there is no fix for the problem at hand). Plus: it does tend to slow the fps of the gears right down. Turning of Compiz would be a pity since Gutsy had no problem with it.

I've tried various tweaks of xorg.conf and even made sure the restricted ATI (oh, yes, ATI) drivers are as up-to-date as they can be. But it's not happening.

I considered going back to the versions that Gutsy has, but I'm really unsure how to do that. What I downloaded was giving me dependancy errors.

---

### Post by aspicNOR on 2008-04-25
Hey! I'm experiencing the exact same issues. Try watch a youtube movie in fullscreen. How does that work out for you?

Im on a ATI 1250 (integrated) card. Glxgears gives med around 1600-1700 fps with compiz enabled.

---

### Post by imbjr on 2008-04-25
Apart from the usual shearing, there was no flickering.

I did at one point manage to stop the flickering for full-screen screensaver displays, but I'm not too sure how I did it.

I disabled the prop' drivers at one point and rebooted to be greeted by a white screen that sounded familar. After some resetting of xorg.conf and reloading the prop' drivers I got back to square one.

I'd be tempted to finger Compiz on this, but I've been surprised before as to what was behind a bug.

---

### Post by Lucretia9 on 2008-04-25
See [http://ubuntuforums.org/showthread.php?t=762636](http://ubuntuforums.org/showthread.php?t=762636)

---

### Post by CamboCambo on 2008-04-26
try changing the system effects to none and see if that changes anything?  I just did it and opengl apps are running nice.

---

### Post by imbjr on 2008-04-27
> **CamboCambo said:**
> try changing the system effects to none and see if that changes anything?  I just did it and opengl apps are running nice.

That effectively turns off Compiz, which does indeed fix things. This is appears to be a regression in behaviour.

---

