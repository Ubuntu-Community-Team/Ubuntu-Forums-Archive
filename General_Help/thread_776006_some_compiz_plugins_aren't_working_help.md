---
title: "some compiz plugins aren't working help"
date: 2008-04-30
forum: General Help
---

### Post by Khuezy on 2008-04-30
When I check 3d windows, it unchecks by itself.
THx:mad:

---

### Post by klange on 2008-04-30
Did you upgrade from Gutsy and happen to have compiled 3d Windows for it?
Check to make sure you don't have an extra 3d windows plugin in ~/.compiz/plugins

---

### Post by Khuezy on 2008-04-30
I just upgraded from Gutsy, when i check 3d windows, it freezes for awhile and unchecks it by itself.

Then my firefox browser is frozen also.

---

### Post by klange on 2008-04-30
Run Compiz from the terminal ('compiz') and activate 3d Windows. Post whatever (relevant) messages appear in the terminal.

---

### Post by Khuezy on 2008-05-01
khue@Khuezy:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:01d8 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

