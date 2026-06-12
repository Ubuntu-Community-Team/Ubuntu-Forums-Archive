---
title: "Multiple Desktops Not Working In Hardy"
date: 2008-05-05
forum: General Help
---

### Post by amtur_poet on 2008-05-05
I just installed ubuntu hardy, but the multiple desktop feature doesn't work anymore. I can't switch between desktops. Is there any way to fix this?

---

### Post by macaholic on 2008-05-05
Are you sure you are clicking the right keystrokes, check in CCSM to double check.

---

### Post by tommyhakinen on 2008-05-06
if you have not installed compiz-fusion, install it first.

> sudo apt-get install compizconfig-settings-manager

if you already have Compiz-Fusion installed, go to System > Preferences > Advanced Desktop Effects Settings. Look for General Options, then choose the Desktop Size tab. Change the Horizontal Virtual Size to 4.

Then press Alt + F2, then enter this:

> compiz --replace 

good luck

Regards,

tommy

---

