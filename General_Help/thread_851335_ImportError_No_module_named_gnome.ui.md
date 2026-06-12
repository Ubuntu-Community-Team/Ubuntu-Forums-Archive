---
title: "ImportError: No module named gnome.ui"
date: 2008-07-06
forum: General Help
---

### Post by Brando569 on 2008-07-06
I just installed kubuntu 8.04.1 on my parent computer and want to compile a new kernel since i know that the default kernel that came with 8.04 was buggy and caused freezes. I know this should probably go in the kernelcheck thread, but it would be buried all the way in the back. 

whenever i try to run kernelcheck i get this error, i fixed it before on my computer but i dont remember how. ive tried installing various gnome libs and even gnome desktop itself (logged into gnome and ran it from there) and kept getting the same error. AFAIK its a dependency problem since it works on my kubuntu 8.04 install but not on theirs since i just installed it last night.

```
Traceback (most recent call last):
  File "/usr/bin/kernelcheck", line 9, in <module>
    import KernelCheck.main, os, gtk, sys
  File "/usr/lib/python2.5/site-packages/KernelCheck/main.py", line 20, in <module>
    import gnome.ui
ImportError: No module named gnome.ui
```

---

### Post by master_kernel on 2008-07-06
This is a bug that will be fixed in the next release; here's a fix:

Edit /usr/lib/python2.5/site-packages/KernelCheck/main.py and remove any lines that contain gnome. There should only be two.

MK

---

