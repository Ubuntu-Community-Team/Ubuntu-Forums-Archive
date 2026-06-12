---
title: "pulseaudio issue"
date: 2019-11-28
forum: General Help
---

### Post by alain.roger on 2019-11-28
Hi,

today when i restart my computer i checked logs and discovered that pulseaudio has some new issues.

here are the errors:
[[IMG]https://i.ibb.co/xhpRRfp/2019-11-28-pulse-audio-issue.png[/IMG]]("https://ibb.co/2qDffsD")

yesterday i had an issue with MPD.service and i had to remove it.
However, sound works perfectly on my computer.

so what's going on ?

thx

---

### Post by alain.roger on 2019-11-28
ok i solved it by just removing the bluetooth module as following:
```
sudo apt r[COLOR=#333333][FONT=monospace]emove pulseaudio-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]module-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]bluetooth[/FONT][/COLOR]
```

and unchecking in KDE settings: bluetooth integration

---

