---
title: "CCSM not saving settings when Effects Disabled"
date: 2008-05-08
forum: General Help
---

### Post by keithjr on 2008-05-08
Backstory: In the Feisty days of compizfusion, I used GL Desktop to manage my effects settings.  I enjoyed it mostly because it created a tray icon that provided a quick way to switch desktop effects on and off (that is, to quickly re-enable metacity as the window manager).  I occasionally play games (native and Wine/Cedega), and few games will run when compiz is on, so this was a must-have.  GL Desktop, however, was rather limited in the amount of ways one could customize compiz, occasionally requiring a dig into gconf-settings. 

Backstory over.

Now, with Hardy's menus and CCSM installed, I have to go into Appearance and turn off Desktop Effects manually.  Okay, no big deal.  But when I go to turn it back on, all my settings have been reverted to the defaults (Wall instead of Cube, etc).  

CCSM seems to have a profiles system and a way to export and import settings.  But neither of these have any effect.  Switching between profiles still results in my settings being overwritten.

Does anybody have any suggestions for gracefully enabling and disabling compiz that won't blow away my settings?

Thanks in advance.

---

### Post by GOROSSI on 2008-05-08
Have you tried logging out after setting your saved profile it works for me using ccsm under Kubuntu when i turn compiz off for google earth use

---

### Post by Glaxed on 2008-05-08
Do you use the flat-file configuration backend or the default settings?
If not, create a new profile with the backend method within CCSM->Preferences

---

### Post by keithjr on 2008-07-21
> **Glaxed said:**
> Do you use the flat-file configuration backend or the default settings?
If not, create a new profile with the backend method within CCSM->Preferences

I'm using the gconf backend, not flat file.  If I use flat-file, I can't integrate with the desktop, which results in an environment which is severely broken (can't even change the number of cube faces from 2).

GOROSSI, what do you do to turn off compiz, do you disable Effects from the Appearance menu?  I tried logging out after making the changes to the settings, but whenever I re-enable desktop effects, the settings still revert in CCSM despite having a new profile.  Quite frustrating and very buggy.  

Is there an alternative out there?

---

### Post by keithjr on 2008-07-21
[http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/)

By posing the question I asked above, I guided myself to the answer.

If you use fusion-icon, you can quickly switch between compiz and metacity, WITHOUT any loss of settings.

Thanks, all!

---

