---
title: "compiz settings"
date: 2008-04-29
forum: General Help
---

### Post by kolbycrouch on 2008-04-29
so i have compiz running in gnome and kde. I set up my compiz in gnome really well but when i login to a kde session all of the settings are gone, like which plugins im using etc. is there a fix for this because i dont want to set everything up for kde too.

---

### Post by macaholic on 2008-04-29
Well one way to be to export your compiz settings, in CCSM under preferences and export. Then load those exported settings udner KDE and you should ahve all your settings.

---

### Post by Zorael on 2008-04-29
Have you set things up with ccsm? (package name **compizconfig-settings-manager** If so, do the following.

Pop up ccsm, go to Preferences and export your profile. Change Backend to flat-file and import your profile again. Done. Try switching to KDE, and make sure it's set to flat-file in there, too.

---

### Post by kolbycrouch on 2008-04-29
well what i came to figure out (after both of yours help) is that by default gnome uses the Gconf backend and kde uses the kde backend, so all i did was switch to the gconf backend

---

