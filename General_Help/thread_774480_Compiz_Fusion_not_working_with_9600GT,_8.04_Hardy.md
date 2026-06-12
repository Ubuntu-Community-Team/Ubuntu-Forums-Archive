---
title: "Compiz Fusion not working with 9600GT, 8.04 Hardy"
date: 2008-04-29
forum: General Help
---

### Post by dejanh on 2008-04-29
The system installed fine, but no restricted driver was installed (or apparently found :s).  I then installed the nVidia 173.08 beta driver and now I have graphics acceleration, but none of the Compiz Fusion effects are working.  Can anybody shed some light on this?

---

### Post by Zorael on 2008-04-29
What is the terminal output of the following command?
```
$ compiz --replace &
```

---

### Post by dejanh on 2008-04-29
Here is the output...

Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0622 (rev a1) (prog-if 00 [VGA controller])
04:00.0 0300: 10de:0622 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by Zorael on 2008-04-29
And it doesn't work? That looks just about right. Do you have any plugins enabled?

You may want to grab the **compizconfig-settings-manager** package through Synaptic or via a terminal to get the "real" and more advanced settings manager; ccsm. Should pop up in your menus, else just run 'ccsm' from a run box (Alt+F2).
```
$ sudo aptitude install compizconfig-settings-manager
```

---

### Post by dejanh on 2008-04-29
Hey, thanks for your help.  I got it to work.  It was some conflicting Compiz pluggins that were causing others to not work.  All seems to be in order now.

:)

---

