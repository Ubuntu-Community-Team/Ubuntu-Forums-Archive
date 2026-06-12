---
title: "Grayed out screen, semi crashing, computer slow down."
date: 2017-07-06
forum: General Help
---

### Post by gmolivier on 2017-07-06
This has happened before, on and off.
Using Ubuntu 16.04.  (Problem happened with earlier versions, also)
Every thing slows...almost like a slow-motion crash.  Monitor grays-out, then back, then out.  
I click on a link and it takes long time for link to open.  Videos stutter.
So, do i need more ram or something...plenty hard drive space.
Tried three browsers: Chromium, Chrome, Firefox...all same.
This problem comes and goes over years time.  

Any...ANY...solutions?

thanks,
 
gmo

---

### Post by CatKiller on 2017-07-07
The windows going grey isn't a symptom, it's an indicator. It's provided by the Fading Windows plugin of Compiz. It shows that the window is not currently responding to requests from the window manager. If you don't like the effect, you can just disable that plugin.

We can't say if your computer needs an upgrade. Anything could be causing your browsers to be unresponsive. You might be visiting slow servers, or you could be using Flash, or you could be not using hardware acceleration with whatever videos you're trying to view, or something else could be running at the same time. Or your computer could just be slow. More RAM would only help if you're regularly running out. **htop** is quite useful for monitoring how much RAM you're using and which processes are causing the most processor load.

---

