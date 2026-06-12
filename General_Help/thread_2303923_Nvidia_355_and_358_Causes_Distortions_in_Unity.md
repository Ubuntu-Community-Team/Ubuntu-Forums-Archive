---
title: "Nvidia 355 and 358 Causes Distortions in Unity"
date: 2015-11-22
forum: General Help
---

### Post by cranerja on 2015-11-22
Running 14.04 on my GTX 970 with either 355 or 358 causes unity to become distorted, as shown in the attached image.[ATTACH=CONFIG]265734[/ATTACH]
Is there any work around?

Thanks in advance.

---

### Post by efflandt on 2015-11-22
If you are asking about the artefacts in the Unity bar and top bar (not really distortion) I noticed that in nvidia-355 with my GTX 750 Ti after my video card wakes from standby (I do not suspend or hibernate the CPU). Hovering over the top bar clears it up there or clicking on any icon in the Unity bar clears it up in both places. I don't know if that happens on my laptop (GTX 765M) because I usually shut that down when not using it (it boots Ubuntu quickly from mSATA SSD).

So I have gone back to nvidia-352 on my desktop PC. The only anomaly with that is that when the GTX 750 Ti wakes from standby with nvidia-352 and I open a program from the Unity bar (like firefox), it occasionally (not always) seems to open in the background behind the desktop (just a slight shadow of it) and I can no longer click on anything in the top bar. I can go to a tty and uptime shows very low load ave, so it is not like something went into a race condition. No errors in Xorg.0.log or anywhere else that I can tell. Rebooting from the tty resolves it. I don't know if that is the result of not booting after some updates (that do not involve a kernel). Maybe I will go back to nvidia-355 and see if this ever happens with it.

PS: Actually trying nvidia-358 to see how that goes.

---

### Post by cranerja on 2015-11-23
Very well, artifacts. But I do not suspend my desktops and there is no way to remove them. Clicking doesn't do anything, and whenever I switch from dual monitor to single monitor and vice versa it gets worse. Let me know if you have any luck.

---

### Post by efflandt on 2015-11-23
You are right about both nvidia-355 and 358, but I do not use multiple monitors, just a 32" 1080p HDTV (DVI to HDMI). So the only time I notice that is when waking my GTX 750 Ti after it only has been suspended (which I have not done on my laptop). For me the top bar clears up if either I hover over it or the clock updates. Or that and the Unity bar clear up if I click any icon in the Unity bar on left. I do not see mention of any issues in /var/log/Xorg.0.log or dmesg.

I am too busy at the moment shutting down a warehouse, but will do some testing with dual displays sometime after Thanksgiving Thursday (I also have a 22" 1080p HDTV that I could connect with HDMI).

---

