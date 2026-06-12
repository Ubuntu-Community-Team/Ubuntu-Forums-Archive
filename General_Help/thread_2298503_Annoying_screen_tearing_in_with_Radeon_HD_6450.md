---
title: "Annoying screen tearing in with Radeon HD 6450"
date: 2015-10-11
forum: General Help
---

### Post by nathan84 on 2015-10-11
I have the proprietary drivers installed for my Radeon HD 6450 graphics card (fglrx) and everything works fine when it comes to gaming and all, but on the desktop there is very noticeable screen tearing when moving around windows. I remember I was able to fix this same problem a while back when I was running Ubuntu MATE by going in to the CompizConfig but I can't recall how, the answers I've found online are to enable two options, in "Workarounds" both of which did not fix the issue at all, I tried enabling the "tear free" option in AMD Catalyst Control Center but that just ghenks up my desktop-wide FPS, tried changing "Wait for verticle refresh" slider down to "Off, unless application specific" (As well as all of the other options) but that only helps with the FPS a little bit and I'm not even sure if it fixes the screen tearing.

Edit: Upon further inspection of thinking of when I used Kubuntu, not Ubuntu MATE and the option that I changed was within's Kubuntu's settings, not CompizConfig.

---

### Post by shutterfoot on 2015-10-12
I think what you're looking for in compizconfig would be under OpenGL, the option called "sync to vblank." Hope it helps.

---

