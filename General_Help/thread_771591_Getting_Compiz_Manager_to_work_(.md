---
title: "Getting Compiz Manager to work :("
date: 2008-04-27
forum: General Help
---

### Post by illumi on 2008-04-27
I have a problem with a new fresh 8.04 install with compiz.

"compiz --replace"


```
$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0341 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

I'm not entirely sure what i should be poking about here to get it to work properly.. Any ideas?

---

### Post by Sef on 2008-04-28
What are your systems specs, including your graphics card?

---

### Post by illumi on 2008-04-28
Specs:

Athlon 2800+ (32bit)
2Gb 3200 RAM
Nvidia Gforce FX5700 Ultra
Creative X-Fi

Restricted drivers installed and enabled.
Brand new 8.04 install, compiz worked earlier with 7.10.
The path/file it says to remove a value from isn't there, which is strange..

Any ideas?

---

