---
title: "applying a patch"
date: 2008-01-02
forum: General Help
---

### Post by Partyboi2 on 2008-01-02
I am trying to apply a patch to startupmanager but am not sure if I am doing it right. This is what I have done.
I have downloaded the source package.
then downloaded the patch from here
[http://launchpadlibrarian.net/11109327/startupmanager.bzr.diff](http://launchpadlibrarian.net/11109327/startupmanager.bzr.diff)
and tried applying the patch
> karl@karl-desktop:~/startupmanager-1.9.9$ patch -p0 < /home/karl/startupmanager.bzr.diffbut it spits out
```
patching file bootconfig/grub_legacy.py
patch: **** malformed patch at line 15: 
```Am I doing this right? or is it a error with the patch itself.
thanks.

---

### Post by ~LoKe on 2008-01-02
Make sure these lines:
```
-            return titles[default_boot]
+            if default_boot < len(titles):
+                return titles[default_boot]
+            return titles[0]
```
Have no spaces before the +/- on your end.

---

### Post by Partyboi2 on 2008-01-02
That part all seems to be ok. Do you think this is a problem with the patch?

---

### Post by ~LoKe on 2008-01-02
> **Partyboi2 said:**
> That part all seems to be ok. Do you think this is a problem with the patch?

Everything seems to point towards that.  I'm not expert on patching, but that error message is pretty clear.

---

### Post by Partyboi2 on 2008-01-02
You probably got more idea about patches then I do. :lolflag:
I thought it probably was something wrong with the patch. Thanks for the a second opinion.

---

