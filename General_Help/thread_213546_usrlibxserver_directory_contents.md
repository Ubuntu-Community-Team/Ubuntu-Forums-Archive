---
title: "/usr/lib/xserver directory contents"
date: 2006-07-11
forum: General Help
---

### Post by domf on 2006-07-11
Following a rather extended process getting 3D accelaration working on my ATI card and due to a rather, err, "unfortunate" (read stupid) typo I moved everything in /usr/lib to /usr/lib/xserver, this resulted in some rather strange behaviours!

Having worked out (eventually) what I'd done I've copied all files from /usr/lib/xserver to /usr/lib to get my system functioning again.

I now need to find a way to identify what is not intentionally in /usr/lib/xserver so that they can be deleted.

Any ideas as to the "normal" contents of this directory (/usr/lib/xserver) under Dapper Drake?

Any and all help appreciated as I'd really rather not have to start from scratch again!

thx



Dom

---

### Post by tseliot on 2006-07-11
> **domf said:**
> Any ideas as to the "normal" contents of this directory (/usr/lib/xserver) under Dapper Drake?
I don't have that folder and I'm running Dapper 32 bit

---

### Post by domf on 2006-07-11
Thanks - it is possible I created the folder.....  I've now renamed the folder, rebooted and all seems ok.  If someone else also running Dapper 32 could confirm that they do NOT have a /use/lib/xserver directory I would appreciate it.


Looks like I got away lightly!


Dom

---

### Post by nanotube on 2006-07-11
i don't have /usr/lib/xserver either. the closest i have is /usr/lib/xorg

---

### Post by hanzomon4 on 2006-07-11
I have /usr/lib/xserver.. the only thing thats there is a file named SecurityPolicy
I hava a 32bit system.

---

### Post by domf on 2006-07-11
Thanks all.  I've recreated the /usr/lib/xserver directory & moved SecurityPolicy into it from /usr/lib

All seems ok.


Dom

---

