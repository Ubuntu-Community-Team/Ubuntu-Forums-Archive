---
title: "[SOLVED] 3D windows don't work anymore"
date: 2008-06-26
forum: General Help
---

### Post by Darkade on 2008-06-26
A couple of months ago I had enabled the Cube effect, and the 3D windows. I got tired of it and disabled both, I was just using the wall.

Today I decided to enabled them both again, and just cube would work, whenever I try to enable 3D windows, it hangs a couple of seconds and then unmarks it self. Any ideas why could this be?
thanks :D

---

### Post by Rocket2DMn on 2008-06-27
Can you please post the output of
```
lspci | grep VGA
compiz --replace
```
You can revert to Metacity with
```
metacity -- replace
```
Also, what version of Ubuntu are you using?

---

### Post by Darkade on 2008-06-27
Thanks I'll post that at night since I'm at work right now.

Compiz works fine, it's just that the 3D windows will not enable.

---

### Post by Rocket2DMn on 2008-06-27
OK, that may be a bug with the plugin, I'm going to have you run the settings manager from terminal, then post the output when you try and enable the 3d windows.
```
ccsm
```

---

### Post by Darkade on 2008-06-27
I've done that and there's no output when I try to enable 3D windows. actually there's no output at all :S:S

---

### Post by Darkade on 2008-06-27
Don't know if it will help. I must say again that the rest of my compiz is working fine.
```
ivan@icarus-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by Darkade on 2008-06-28
Never mind, I uninstalled it, remove all config files and the comple the latest version... just for fun, it's working fine. thanks anyway :lolflag:

---

