---
title: "[SOLVED] my nvidia is annoying me"
date: 2007-07-22
forum: General Help
---

### Post by mrreality13 on 2007-07-22
Hi All,
Im running 7.04
every time i re boot my pc i have to start from scratch with , "sudo nvidia-settings" to get ny tv out to work (card is a 7600 gs pci-e)
should'nt i have an nvidia settings button in my prefrences tab?
thanx in advance.:)

---

### Post by MrHippocampus on 2007-07-22
Try and see if running just "nvidia-settings -l" (thats an L btw) works, after setting the right configuration options with "nvidia-settings", without sudo.

If that works you can set it to run every time you login (I cant remember where you do this, im not in ubuntu at the moment, its something to do with gnome session I think).

---

