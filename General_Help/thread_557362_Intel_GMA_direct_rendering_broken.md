---
title: "Intel GMA direct rendering broken"
date: 2007-09-22
forum: General Help
---

### Post by tgvail on 2007-09-22
Hi everyone--

I recently tried to install beryl on my computer, which made everything go too slow, so I tried to uninstall it. Now my computer will not work with any good graphics (default screen effects, wine games like D2 and War3, etc). I have tried to reconfigure with "sudo dpkg-reconfigure -phigh xserver-xorg" and reinstall xserver-xorg-video-i810, but it is still not working.

Does anyone have any suggestions to get this working again?

Thanks

---

### Post by tgvail on 2007-09-22
any ideas?

---

### Post by beyboo on 2007-09-23
here are some wild ones. 

1) Clean up everything Beryl by doing a search in synaptic and deleting.
2) Any old snaps of your old xorg.conf files which you can compare with. you need to maybe paste your xorg.conf file for a peek. glxinfo output would also help.

---

