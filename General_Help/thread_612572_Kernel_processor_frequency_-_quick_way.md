---
title: "Kernel processor frequency - quick way ??"
date: 2007-11-14
forum: General Help
---

### Post by stoive on 2007-11-14
hi all, heres the deal.

i'm running mythbuntu, and i have a winfast dtv1000 tuner card with remote control.  i have gotten the remote control working, but it acts like the buttons stick down.  this has been traced to the kernel frequency being set to 250HZ by default.

I need it to be 1000 HZ.

can i do it by editing the "config-2.6.22-14-386" file and changing the config_hz=250 to 1000 and update it ???

otherwise, do i need to rebuild the kernel ?

how can i rebuild the kernel using the same kernel source as mythbuntu uses (7.10) where do i get it from as i had problems when i changed the kernel to 2.6.23.  i rebuilt it last night but for some reason its not booting up using the settings as config_hz=250 is still in place :(

---

