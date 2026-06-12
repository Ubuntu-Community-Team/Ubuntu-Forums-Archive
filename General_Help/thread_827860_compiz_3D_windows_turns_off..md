---
title: "compiz 3D windows turns off."
date: 2008-06-13
forum: General Help
---

### Post by fela on 2008-06-13
Whenever i turn on 3d windows, it just turns back off automatically before i have a chance to turn the cube and see it. Has anyone else had this bug?

---

### Post by issih on 2008-06-13
Hmmn, odd, could you try opening a terminal and running:

```
compiz --replace
``` 

then post the output here, hopefully that will help us see where it is going wrong.

It is also probably worth running compiz check:

[http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz+check](http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz+check)

---

### Post by fela on 2008-06-13
here is the output:

$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:01d3 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

---

### Post by issih on 2008-06-13
can you run compiz check too ?

That error about the scale plugin appears to have been resolved yesterday according to launchpad, so doing an update might be worth it, but I really doubt that is whats causing your issue.

---

### Post by LifeTheHound on 2008-07-25
Actually, this happens with many people and is a known problem: [http://forum.compiz-fusion.org/showthread.php?t=8299](http://forum.compiz-fusion.org/showthread.php?t=8299)

---

