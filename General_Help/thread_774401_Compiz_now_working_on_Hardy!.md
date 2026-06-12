---
title: "Compiz now working on Hardy!"
date: 2008-04-29
forum: General Help
---

### Post by Fixman on 2008-04-29
I today installed Ubuntu Hardy Heron, and all works perfectly, except for Compiz that, once I enabled restricted drivers, this message appears:

```

martin@Ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Aborted

```

Any suggestion?

---

### Post by Fixman on 2008-04-29
Nobody? Come on, I can't live without Compiz!

---

### Post by olskar on 2008-04-29
open gconf-editor from the terminal or with Alt+F2 and look upp /apps/compiz/plugins/scale/allscreens/options/initiate_edge and remove that value as it tells you :) Might work after that

---

### Post by Fixman on 2008-04-29
> **olskar said:**
> open gconf-editor from the terminal or with Alt+F2 and look upp /apps/compiz/plugins/scale/allscreens/options/initiate_edge and remove that value as it tells you :) Might work after that

The key is set to "[]", however, if I unset it and open compiz, is sets again (as []), and pops the same error. Can someone give me their value of /apps/compiz/plugins/scale/allscreens/options/initiate_edge, so I can change it to a correct one?

---

### Post by Fixman on 2008-04-29
Can someone give me that key?

---

### Post by olskar on 2008-04-30
I have it set to TopRight.

You should wait a bit longer before bumping your post, its a forum and not a chatroom after all

---

