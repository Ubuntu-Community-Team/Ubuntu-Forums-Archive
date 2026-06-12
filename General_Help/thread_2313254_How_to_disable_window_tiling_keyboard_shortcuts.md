---
title: "How to disable window tiling keyboard shortcuts?"
date: 2016-02-10
forum: General Help
---

### Post by Edward_Fish on 2016-02-10
Recently I reinstalled Ubuntu 14.04. I used to have *Ctrl-Super-Arrowkeys* bound to switching workspaces, but for some reason they are currently bound to snapping windows to the edges of the screen.
I've looked in *System Settings > Keyboard > Shortcuts*, *gnome-tweak-tool* and *unity-tweak-tool* and I can't figure out where the option for *Ctrl-Super-Left/Right *is. I can find *Ctrl-Super-Up/Down* though.

So I want to make *Ctrl-Super-Arrowkeys* switch workspaces and I want *Super-Arrowkeys* to snap windows. How do I reconfigure these buttons?

---

### Post by CantankRus on 2016-02-11
Use **compizconfig-settings-manager** (ccsm).
The tiling shortcuts are in the grid plugin.

---

### Post by Edward_Fish on 2016-02-13
Eeh. I'm pretty sure it was ccsm that wrecked Unity and made me reinstall in the first place :/

---

### Post by buzzingrobot on 2016-02-13
Unity is implemented as a Compiz plugin, so, yes, making random changes with CCSM can have unexpected results. However, disabling keystroke shortcuts won't.

You can also install the Unity Tweak Tool and use it to disable tiling altogether. That's what I do, along with hot corners, magnification, etc.

---

