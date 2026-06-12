---
title: "Missing Splash Screen"
date: 2018-04-12
forum: General Help
---

### Post by ray42 on 2018-04-12
I'm sure this has been posted about many times.

Get boot text as loading after boot menu. This happened after installing various bit of software (through software installer).

Any concrete ideas on how to fix. I used to run of a USB stick (had the same issue then) but this is on my HDD so I want to avoid experimentation.

---

### Post by dino99 on 2018-04-12
if you does not want the splash screen, then remove 'splash quiet' from /etc/default/grub, save and run 'sudo update-grub'

---

### Post by ray42 on 2018-04-12
Sorry I mean boot text is showing before logo appears.

I get my boot menu, but afterwards get lots boot text before the logo (is that called splash screen?).

---

