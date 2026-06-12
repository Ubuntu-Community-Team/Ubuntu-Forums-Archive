---
title: "Unity global menu's shadow poping in fullscreen apps in 13.04"
date: 2013-05-27
forum: General Help
---

### Post by kill o matic on 2013-05-27
Since installing Raring, whenever a notification pops up while I'm playing a video in fullscreen (such as adjusting the volume/brightness of my laptop with the keyboard shortcuts), I can also see the outline and shadow of the global menu bar for as long as the popup is visible. This happens even whit a clean system booted from the Live USB.

---

### Post by kill o matic on 2013-05-29
Okay, after messing around with compiz settings and screwing up my display royally at one point, I found the culprit. It appears to be the PNG image loading plugin. Turning that off also disables the unity grab handles, but those are off by default anyway. Does anyone know if it's safe to leave the PNG plugin off permanently or if something actually important uses it?

---

