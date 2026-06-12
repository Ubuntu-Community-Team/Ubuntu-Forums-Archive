---
title: "Screenlets Won't Go Away"
date: 2008-06-02
forum: General Help
---

### Post by daemon3 on 2008-06-02
Whenever I log in to my desktop (KDE or Gnome) environment, for some reason I get a bunch of screenlets that pop up on my desktop.  No matter what I do, I can't seem to make the screenlets disappear.  I tried going into Screenlets Manager and deselecting "Autostart at login." for certain screenlets, but the same things keep reappearing.  I've even gone to the command line and killed the screenlets manually, but nothing seems to work.  Please help.  Thanks in advance.

---

### Post by jryprt on 2008-06-02
> **daemon3 said:**
> Whenever I log in to my desktop (KDE or Gnome) environment, for some reason I get a bunch of screenlets that pop up on my desktop.  No matter what I do, I can't seem to make the screenlets disappear.  I tried going into Screenlets Manager and deselecting "Autostart at login." for certain screenlets, but the same things keep reappearing.  I've even gone to the command line and killed the screenlets manually, but nothing seems to work.  Please help.  Thanks in advance.

Open home folder press Ctrl+h look for .config open it go to Screenlets
open it delete any or all in there .

---

### Post by Forlong on 2008-06-02
What's the output of
```
ls $HOME/.config/autostart
```

---

