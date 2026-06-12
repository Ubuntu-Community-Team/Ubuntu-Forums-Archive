---
title: "Desktop effects broken"
date: 2008-06-18
forum: General Help
---

### Post by prashantjois on 2008-06-18
I think a recent update broke my desktop effects. When I go to System->Preferences->Appearance and try and enable "Extra" in visual effects, I get the error "Desktop effects could not be enabled".

When I manually run compiz --replace I get the following message:

> 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 


When I run compiz-check, I get the following:

> 
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8600 GT (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 



user techstop on [this thread]("http://ubuntuforums.org/showthread.php?t=831414") says that the xorg update is responsible for this.  However, I have not been able to find the issue that's being referred to.

I didn't mention is explicitly but I hadn't changed anything when this happened, that's why I'm speculating that it's an update that broke things.

Can anyone point me in the right direction?

Thanks

---

### Post by Forlong on 2008-06-21
Reinstalling the nvidia driver is said to help in that case.

Hope it helps.

---

