---
title: "Cannot get the cube to work in Ubuntu Studio 8.04"
date: 2008-05-12
forum: General Help
---

### Post by DaF101 on 2008-05-12
Hey everyone,

I managed to get the Nvidia driver enabled and the desktop effects on my Ubuntu Studio Hardy Heron are up and running, the problem now is, I can't seem to get the Workspace cube for when I am changing workspaces, its simular when I don't have the effects enabled. except the desk space diolog fades in and out. 

If anyone can help me activate the workspace cube it will be greatly appreciated. :)

---

### Post by aroch1 on 2008-05-16
Here's how you do it.

Install the compizconfig-settings-manager package.  Open the settings manager with System->Preferences->Advanced Desktop Effects Settings.

This should show a large list of possible plugins.  By default I believe that Desktop Plane or Desktop Wall is selected as the workspace switcher plugin.  Instead, check the "Desktop Cube" plugin.  This should ask you if you wish to disable one of the other desktop plugins...say yes.  If you want your cube to spin, be sure to enable the "Rotate Cube" plugin, and if you want to put images/colors on the top and bottom of your cube enable the "Cube Caps" plugin.

---

