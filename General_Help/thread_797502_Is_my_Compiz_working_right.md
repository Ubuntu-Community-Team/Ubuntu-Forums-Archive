---
title: "Is my Compiz working right?"
date: 2008-05-17
forum: General Help
---

### Post by planetmn on 2008-05-17
Hi,
I just installed 8.04 (gnome) and wanted to play around with the Compiz effects.  I went through the instructions and installed the Compiz icon.  I've set up for the cube, but I can't make the cube appear.  Is there some special key combination that needs to be pressed?  Presseing ctrl-alt and dragging the mouse doesn't do anything.

If I do an alt-tab, I get a standard window switcher.  Is it possible that compiz isn't installed properly?

Thanks,
dave

---

### Post by macaholic on 2008-05-17
How did you install compiz? If it is the ubuntu way, what level of effects do you have enabled?

---

### Post by Kevbert on 2008-05-17
Firstly, how many desktop workspaces do you have ?  You need 4.  Right click on the boxes in the bottom RH corner, select preferences and set to 4 columns.
Next, go to System - Preferences - Advanced Desktop Effects - Double click on Rotate Cube, check its enabled and set Flip Time to 200, Speed to 1.7, Zoom to 0.8.  Now go to Desktop Cube, Behaviour, check its enabled, set Acceleration to 4, Speed to 1.7 and Timestep to 1.2.
You should now have a cube when you select a new Workspace when clicking the workspace in bottom RH corner or using Ctrl-Alt-Left or Right arrow.

---

### Post by planetmn on 2008-05-17
> **macaholic said:**
> How did you install compiz? If it is the ubuntu way, what level of effects do you have enabled?

I installed compizconfig-settings-manager using Synaptic.  I have effects set to Extra.

I wasn't able to enable desktop cube or rotate cube so I looked at the preferences-> plugins list and saw that they weren't in the list, I added them and was able to enable them, set the settings to kevbert's suggestions and it works.  Thanks!

-dave

---

