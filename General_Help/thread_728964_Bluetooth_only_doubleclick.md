---
title: "Bluetooth only doubleclick"
date: 2008-03-19
forum: General Help
---

### Post by xMaximex on 2008-03-19
I installed Hardy on my Gutsy.

My bluetooth mouse is only double click. Everytime I single click it does a double click.

Any way to fix that ?

I removed and reinstalled all bluez and bluetooth package, repaired my mouse and it still double click

---

### Post by rushman2 on 2008-03-27
I also had same problems.

After some research I found that in xorg.conf I have 'Configured mouse' and 'EvDevMouse' both enabled.

When I commented 'Configured Mouse' and restarted X I got back my single click ;)

I hope this will help.

---

