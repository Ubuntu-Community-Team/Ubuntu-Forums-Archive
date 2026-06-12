---
title: "rename command + perl regex help"
date: 2008-02-04
forum: General Help
---

### Post by icemanxp on 2008-02-04
Hi I'm a bit new to perl regex and i was trying to perform something along the lines of this:

rename <8 letters><numbers><junk to remove>.avi to <8 letters><numbers>.avi

and I had come up with this

rename -nv 's/(\w{8}\d\d)/$1.avi/' *.avi

however rename states that it will rename it to

<8 letters><numbers>.avi<junk to remove>.avi 

and for the life of me I cannot figure out how to rename and remove that last bit any ideas?

---

### Post by Gordaen on 2008-02-04
rename -nv 's/(\w{8}\d\d)(.*)/$1.avi/' *.avi
That might be what you need.

---

### Post by icemanxp on 2008-02-04
Ah thank you, So you need to split it up into unique parts and then just add one back to remove the other?

---

