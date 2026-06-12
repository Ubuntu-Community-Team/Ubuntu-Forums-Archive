---
title: "nforce430 and GeForce 6150 in Feisty?"
date: 2007-06-16
forum: General Help
---

### Post by gobeavs on 2007-06-16
I'm looking to build a mythtv setup around a motherboard with the nforce430 chipset and Geforce 6150 onboard video, but I've seen that there have been some issues with linux and those parts before. Are those problems resolved? Does anyone have experience with ubuntu on the nforce430? Specifically, I would need audio, video, and networking to work. I'm looking for a (relatively) hassle-free setup, so any advice would be appreciated. Thanks.

EDIT: Just FYI the motherboard I'm looking at is the ASUS M2NPV-VM.

---

### Post by PhatStreet on 2007-06-16
I don't have your motherboard, but I've never had any problems with your video card, with the nv modules or the official ones.

---

### Post by likwid on 2007-06-17
I use a motherboard as you descibe, an asus a8n vm-csm. Everything works fine except the nvidia display drivers. I had to disable renderaccel in xorg.conf, otherwise firefox fonts were badly messed up. Glx  doesn't work, although maybe some tweaking might help? As far as video playback however, no problems.

My recommendation therefore would be to buy a cheap passively cooled vga. That's what i ended up doing.

---

