---
title: "Suspend Not Working on Edgy"
date: 2006-11-17
forum: General Help
---

### Post by PRGUY85 on 2006-11-17
Hey there:

I have a fully updated Edgy system with Beryl working.  The laptop goes into suspend just fine but it never comes out of it.  When I come out of suspend I can move the mouse but nothing else, with a black screen.  Sometimes not even the mouse cursor is seen.  Yet, rarely it works asking for the password after several clicks of the mouse.  Could it be  problem with Beryl, edgy, suspend function or video drivers?

Thanks.

---

### Post by PRGUY85 on 2006-11-18
Nothing
?

---

### Post by zgornel on 2006-11-19
Try adding in /etc/X11/xorg.conf, Section Device : Option "VBERestore" "true"

---

### Post by PRGUY85 on 2006-11-20
Nope, nothing but black screen and mouse cursor also it seems a bit less buggy now.

---

