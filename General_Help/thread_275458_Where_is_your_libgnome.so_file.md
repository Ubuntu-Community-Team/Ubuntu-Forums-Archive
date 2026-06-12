---
title: "Where is your libgnome.so file?"
date: 2006-10-11
forum: General Help
---

### Post by Old Pink on 2006-10-11
Hi there,

Recently upgraded libglade, and a few of my applications are unhappy as they have lost the libgnome.so file, which has moved directories.

Can anyone tell me where their libgnome.so file is, so I can put a copy in the right directory? :) 

- Matt

---

### Post by ronmarley1 on 2006-10-11
/usr/lib/libglade/2.0

---

### Post by Old Pink on 2006-10-11
Hm.

Ok, this has escalated. Usually if I run an app, it doesn't open. Then I have to use LD_PRELOAD to show the application where libgnome.so is.

**But**, if Ron is right, then my libgnome.so file is in the right place, are my applications looking in the wrong place?

**EDIT: **Here is an example of what's happening, and how I use LD_PRELOAD to fix it:
[http://ubuntuforums.org/showthread.php?t=274912](http://ubuntuforums.org/showthread.php?t=274912)

---

### Post by Old Pink on 2006-10-11
No ideas? :|

---

### Post by ronmarley1 on 2006-10-11
I'm stumped...
sorry

---

