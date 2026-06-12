---
title: "Composite help with ATI"
date: 2008-03-05
forum: General Help
---

### Post by MrQBerrt on 2008-03-05
Thanks to some other threads I've almost gotten compiz working with my rig.  But I have one last problem.  When I run "compiz" I get the following:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4152 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3360x1050) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 

```

Obviously the problem is that my resolution is set too high for my graphics card.  Are there any work arounds for this that allow me to keep using native resolution on both of my LCDs?  I have a radeon 9600 and I'm running 2 LCDs.  One is native 1680x1050 and the other is native 1280x1024.  I have them setup using MergedFB.

One thing I was thinking is that maybe Xinerama or BigDesktop mode for the dual heads would make it so compiz didn't see one BIG resolution and that might help.  Any thoughts on that?

---

### Post by pointone on 2008-03-05
You could create ~/.config/compiz/compiz-manager and add the line "SKIP_CHECKS=yes" to prevent Compiz from running checks at startup.

---

### Post by boeing777 on 2008-03-05
Goto: System -->Administration -->Software Sources

Under "Ubuntu Software" tab
-->Check all the checkboxes

Under "Updates" tab
--> check all the checkboxes

then go back and then try to enable it again,

---

