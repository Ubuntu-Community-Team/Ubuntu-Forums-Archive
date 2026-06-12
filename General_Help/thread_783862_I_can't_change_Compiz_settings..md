---
title: "I can't change Compiz settings."
date: 2008-05-06
forum: General Help
---

### Post by chrispche on 2008-05-06
If I go into Appearance and click extra. Compiz runs on it's default settings. If I want to enable the cube. Compiz shuts down and freezes.

My vidia card is intel experimental 865.

---

### Post by marufaberlin on 2008-05-06
is there an advanced desktop effects item in gnome-control-center? If not, look in synaptic for compiz-config-settings-manager (think that's what its called).

---

### Post by NightwishFan on 2008-05-06
Yes install compizconfig-settings-manager if it is not already. Also you can try running compiz from the terminal to see what is the problem when you try to enable.

```
compiz --replace
```

---

### Post by chrispche on 2008-05-06
I have everything required for compiz installed. It was working before I done a brand new install. That was on an upgraded Gutsy to Hardy.

---

### Post by chrispche on 2008-05-06
> **NightwishFan said:**
> Yes install compizconfig-settings-manager if it is not already. Also you can try running compiz from the terminal to see what is the problem when you try to enable.

```
compiz --replace
```

Ok I get this:

chrispche@chrispche-desktop:~$ compiz --replace 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2572 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

chrispche@chrispche-desktop:~$

---

