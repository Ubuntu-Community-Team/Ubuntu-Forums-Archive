---
title: "Help!! I did a stupid thing!"
date: 2007-11-06
forum: General Help
---

### Post by Skweek on 2007-11-06
I was messing around with CCSM on my Gutsy installation and twiddled with the opacity settings in "General" - now all of my windows are totally transparent!!! :oops:  What file do I need to edit to restore/disable transparancy?

---

### Post by Jose Catre-Vandis on 2007-11-06
Can you logout and log back in with a default session (without compiz) then you can run ccsm again and change the settings.

You can also toggle Opacify with
```
SUPER+O
```

---

### Post by Skweek on 2007-11-06
Thanks, Jose - I solved my problem by renaming ~/.gconf/apps/compiz/general/screen0/options/%gconf.xml to %gconf.xml_  followed by a logout/login

---

