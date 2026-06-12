---
title: "Compiz starts, but no effects; after Hardy upgrade"
date: 2008-04-25
forum: General Help
---

### Post by justmoon on 2008-04-25
Let me get right to it.

ATI X1900XTX
Ubuntu 7.10 upgraded to 8.04 yesterday
FGLRX 8.3 installed from repo

Output of glxinfo | grep direct:
```
direct rendering: Yes
```

Output of running compiz:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7249 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1600) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present.
```

When you start it, it runs, with the *slight* limitation there are no window borders and none of the effects work. Clicking on windows to bring them to the front does work though.

Any ways to fix the problem or at least get more information about it very welcome! Thanks!

---

