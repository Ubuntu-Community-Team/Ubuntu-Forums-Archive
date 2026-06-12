---
title: "Dell Inspiron 1100 7.10 screen size"
date: 2007-11-18
forum: General Help
---

### Post by TurboTT on 2007-11-18
I am trying to run Ubuntu on my laptop but cannot get the desktop to fit the screen size. All I can find is that I may have to upgrade to the A32 BIOS. I really don't want to have to do this if I don't have to. Does anyone know how to fix this? Thanks.

---

### Post by bmathis on 2007-11-18
Look for the "monitor section"
Add these lines

> Identifier "Generic Monitor"
HorizSync 31.5 - 50.0
VertRefresh 40-90

You might also need to change your driver from "intel" to "i810"

---

