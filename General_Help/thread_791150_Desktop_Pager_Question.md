---
title: "Desktop Pager Question"
date: 2008-05-11
forum: General Help
---

### Post by uberlube on 2008-05-11
My question is regarding the desktop pager in KDE and Im sure that many of you have had the same issue. When you activate your advanced desktop effects the pager goes from 4 fields to 8 or 16 depending on how cranky it is. I know how to revert it back to only 4 desktops but Im getting sick of doing this every time I log in. Is there a way to make my changes the default?

---

### Post by amohanty on 2008-05-12
In gnome I installed compizconfig-settings-manager and then started it from the command line: ccsm (in gnome it shows up in System->Preferences->Advanced Desktop Effects Settings).

There click on 'General Settings' goto the 'Desktop Size' tab and change the values to what you like. Keep in mind that the **Horizontal/Vertical Virtual Size** settings applies to **each virtual desktop you have in your non-effects setup**.

HTH
AM

HTH
AM

---

### Post by uberlube on 2008-05-12
That is how you make it show only 4 desktops instead of 8 or 16, I have already done that. What Im trying to do is make it keep those changes for the next time I boot up. Every time I log in I have to go into the settings manager and change it back to 4 - 1 - 1.

---

### Post by uberlube on 2008-05-13
Bump

---

### Post by amohanty on 2008-05-15
sorry for the late response. If you set it via ccsm, it should be saved in your .config/compiz folder somewhere. 

It appears that you log into metacity and then start compiz from the the icon, in which case this could happen. Fire up gconf-editor and post the values of the following keys:

/desktop/gnome/applications/window_manager
in there what are the values for current and default??

AM

---

