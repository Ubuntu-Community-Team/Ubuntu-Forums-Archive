---
title: "Volume"
date: 2005-06-29
forum: General Help
---

### Post by maltje on 2005-06-29
suddenly,I think after an update, the volume of my system is at the max,but it is very quiet!!!!
Please help.

---

### Post by tomchuk on 2005-06-29
Run alsamixer from a terminal and make sure all your mixer levels are where you want them to be. Might be that your master mixer is at the maximum, but PCM is quite low.

---

### Post by maltje on 2005-06-29
Halelujah;thnx it is ok now.any idee how that happens???

---

### Post by tomchuk on 2005-06-29
Between reboots your mixer levels are saved and restored with the command "alsactl store/restore". Sometimes an upgrade will cause the mixer levels to be reset. You can always make sure that they're getting stored by issuing the command (with sudo) manually, but things should be working fine on their own now.

---

