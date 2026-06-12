---
title: "Configuring ATI card from console. No X."
date: 2007-10-01
forum: General Help
---

### Post by JesterDev on 2007-10-01
Having a bit of a brain freeze here. I switched out my nVidia card for my ATI X1300 Pro due to some issues with nVidia. So anyway it's been awhile since I've touched this box, but not I cannot get into X. I can only boot into the console. 

I cannot for the life of me remember how to configure my card from the console. Not worried about specific drivers at the moment, just want to get X running then I'll work on getting the drivers installed.

Any help seriously appreciated.

---

### Post by 67GTA on 2007-10-01
sudo dpkg-reconfigure xserver-xorg

You can select your card driver and set other options. If your not sure of an answer, just hit enter.

---

