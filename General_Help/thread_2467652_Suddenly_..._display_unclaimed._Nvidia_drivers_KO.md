---
title: "Suddenly ... display unclaimed. Nvidia drivers KO"
date: 2021-10-03
forum: General Help
---

### Post by joerack2 on 2021-10-03
As topic says... I keep getting this error suddenly and often after a system update.

lshw -C display shows   DISPLAY UNCLAIMED, and nothing works

[COLOR=#333333][FONT=DIN-Web-Pro][SIZE=4]sudo modprobe nvidia   gives modprobe: FATAL
[/SIZE][FONT=var(--ff-mono)][SIZE=4]sudo prime-select nvidia  returns already set...[/SIZE]

if I check additional drives, it says nvidia proprietary 470 installed...

Atm I've just reinstalled 20.04.. I've noticed that installing  this specific app from flatpak  "GTKSTRESSTESTING"

downloads **  org.freedesktop.Platform.GL.nvidia-470-63-01**    and many other versions...

Could this be the culprit?



[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]
[/FONT][/COLOR]

---

