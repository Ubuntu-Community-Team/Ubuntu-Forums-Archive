---
title: "how do i customize the effects on 8?"
date: 2008-04-26
forum: General Help
---

### Post by guySch on 2008-04-26
hallo i just installed ubuntu 8.4

what program makes all the effects?...
and how can i customize it?
should i install beryl ?

how do i install beryl? i didnt find beryl on the package manager....

please help

---

### Post by sanus|art on 2008-04-26
Search for 'compiz' in synaptic or go [here]("https://help.ubuntu.com/community/CompositeManager/CompizFusion").

P.S.
Also check if your graphic card is supported.

---

### Post by Zorael on 2008-04-26
Also, Beryl has been superseded by Compiz. :>

---

### Post by guySch on 2008-04-26
hi tnx for the reply.

i did what it said in that tutorial and this is what happend:

> guy@desktopL:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:00f2 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly


now what do i need to do?

---

### Post by GandalfDaGraay on 2008-04-26
Install the [compizconfig-settings-manager](http://packages.ubuntu.com/hardy/compizconfig-settings-manager) package. This will add the Advanced Desktop Effects item to your Preferences menu.

All of the effects are installed with 8.04; you just need the manager to customize them. Kind of silly that it doesn't come installed with the distro, if you ask me...

---

