---
title: "Can't move windows in Gnome 13.10 Unity"
date: 2014-02-06
forum: General Help
---

### Post by sirrahd on 2014-02-06
Some time in the past week I lost the ability to move windows in Ubuntu 13.10 with Unity. Using the alt-click combination, dragging the titlebar, and right clicking the titlebar and selecting move all don't work. The only way I can move windows is by resizing them into the location I want.

Unfortunately I'm not sure when exactly this started and I haven't had success searching for this problem. Anyone experience this or have an idea of what could be behind it?

---

### Post by deadflowr on 2014-02-06
No idea how you got that, but you can check and see if the move plugin was disabled in ccsm
compizconfig-settings-manager. under the name 'move windows'.

I'm sure there is a quick gsettings command to figure that out, but I'm too lazy to look for it.

---

### Post by sirrahd on 2014-02-07
Wow thanks! Sure enough that fixed it. I installed compizconfig-settings-manager and found 'move windows' was disabled. Very surprising since I've been keeping this install as vanilla as possible.

Thanks so much for your help! I'm new to this forum (despite making an account a long time ago), how do I give you a bean?

---

