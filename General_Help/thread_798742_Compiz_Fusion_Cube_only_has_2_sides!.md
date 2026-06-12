---
title: "Compiz Fusion: Cube only has 2 sides!"
date: 2008-05-18
forum: General Help
---

### Post by pi.phage on 2008-05-18
My cube only has 2 sides! When I try to change this in 
System > preferences > Simple Compizconfig settings manager it does nothing.

---

### Post by n838901 on 2008-05-18
Right click on the Workspace Switcher located at the bottom right corner of the screen and then select 'Preferences'.  Change the column value to '4'

---

### Post by russo.mic on 2008-05-19
> **n838901 said:**
> Right click on the Workspace Switcher located at the bottom right corner of the screen and then select 'Preferences'.  Change the column value to '4'

Not so much that... instead, try this:

ccsm - general options - desktop size - horizontal virtual size to 4

You do have the compiz settings manager installed?  if not, from a terminal

sudo apt-get install compizconfig-settings-manager

Russo

---

### Post by Forlong on 2008-05-19
> **russo.mic said:**
> Not so much that... 
Why not? It should work just fine.

---

### Post by russo.mic on 2008-05-19
> **Forlong said:**
> Why not? It should work just fine.

well, def not if he's using KDE, and I don't think it works in gnome either. I think that compiz doesn't actually look at how many workspaces you've got available.  it just draws only one.

Russo

---

### Post by Forlong on 2008-05-19
> **russo.mic said:**
> well, def not if he's using KDE
He/she tagged the thread as [ubuntu]
> **russo.mic said:**
> and I don't think it works in gnome either. I think that compiz doesn't actually look at how many workspaces you've got available.  it just draws only one.
The workspace switcher in the GNOME panel is compiz-aware since Gutsy: [http://forlong.blogage.de/article/2007/10/15/Update-on-Compiz-Fusion-by-default-in-Gutsy](http://forlong.blogage.de/article/2007/10/15/Update-on-Compiz-Fusion-by-default-in-Gutsy)

---

### Post by Mieklol on 2008-05-19
Careful with this, as when I installed Compiz I was stumped as to why my cube was two dimensional when I even had four sides. The answer is that you have to enable the cube and its shorcut keys in the Compiz control panel, otherwise it's just a fancy effect instead of an awesome three dimensional cube.

---

### Post by Kevbert on 2008-05-19
Firstly, how many desktop workspaces do you have ? You need 4. Right click on the boxes in the bottom RH corner, select preferences and set to 4 columns.
Next, go to System - Preferences - Advanced Desktop Effects - Double click on Rotate Cube, check its enabled and set Flip Time to 200, Speed to 1.7, Zoom to 0.8. Now go to Desktop Cube, Behaviour, check its enabled, set Acceleration to 4, Speed to 1.7 and Timestep to 1.2.
You should now have a cube when you select a new Workspace when clicking the workspace in bottom RH corner or using Ctrl-Alt-Left or Right arrow.

---

### Post by russo.mic on 2008-05-19
> **Forlong said:**
> He/she tagged the thread as [ubuntu]

The workspace switcher in the GNOME panel is compiz-aware since Gutsy: [http://forlong.blogage.de/article/2007/10/15/Update-on-Compiz-Fusion-by-default-in-Gutsy](http://forlong.blogage.de/article/2007/10/15/Update-on-Compiz-Fusion-by-default-in-Gutsy)

I stand corrected, and I'm not used to the tags yet.

I prefer a triangle anyway.

---

