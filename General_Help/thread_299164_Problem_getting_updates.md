---
title: "Problem getting updates"
date: 2006-11-13
forum: General Help
---

### Post by scallywag on 2006-11-13
**I don't know if anyone can help with this, but I can't do updates on Ubuntu because I get an error message:**


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

**When I run the above code I get this:**

root@kevin-laptop:/home/kevin# dpkg --configure -a
Setting up flashplugin-nonfree (7.0.68~ubuntu2~dapper1) ...
Downloading...
[B]
And it just stays there forever[/B]

---

### Post by yabbadabbadont on 2006-11-13
Try removing flashplugin-nonfree.  I think it would be "dpkg -r flashplugin-nonfree".

---

### Post by scallywag on 2006-11-13
That seems to have solved the problem for now. thamks for your help

---

