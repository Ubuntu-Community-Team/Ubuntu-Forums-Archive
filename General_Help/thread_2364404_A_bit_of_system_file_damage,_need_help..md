---
title: "A bit of system file damage, need help."
date: 2017-06-22
forum: General Help
---

### Post by shag00 on 2017-06-22
I installed RealVNC the other day to overcome some persistent bandwidth issues with Vino server. During the installation it somehow removed /root/.config/ folder and I lost some functionality some of which I have repaired but I have 2 outstanding issues:
1/ The trash can has disappeared and;
2/ The delete command in the gksudo nautilus drop down menu has disappeared.

Can anyone tell me what else has likely been deleted please.

---

### Post by howefield on 2017-06-23
Have a look in /var/log/apt/ for clues.

Sounds like you have done more than install VNC, can you describe how you installed it.

---

