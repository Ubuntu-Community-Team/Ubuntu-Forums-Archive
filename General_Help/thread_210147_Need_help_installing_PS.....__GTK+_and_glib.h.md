---
title: "Need help installing P/S.....  GTK+ and glib.h"
date: 2006-07-06
forum: General Help
---

### Post by hemes on 2006-07-06
Hi,

I am currently trying to install Player/Stage 

[http://playerstage.sourceforge.net/](http://playerstage.sourceforge.net/) 

and and having problems installing the second of the two programs.  Durring $ ./configure, I get a warning about not having a suitable version of GTK+ (GTK+-2.4 or higher requierd).  Then, if I try to $ ./make, I get an error glib.h: no such file or directory.  I know glib is instlled, it seems that the make file can't find it.  

Any help would be greatly appreciated!

Thanks,
Brett

---

### Post by taurus on 2006-07-06
You need to install the development packages for those libraries if you want to build something from source.  So, fire up synaptic and search for them.  Make sure you install the "-dev" packages...

---

### Post by hemes on 2006-07-06
yeah... I tried that.  I installed almost everything that says glib or gtk+ ](*,)

---

### Post by taurus on 2006-07-06
Then why don't you post the complete printout of the message when you run ./configure...

---

### Post by hemes on 2006-07-06
No problem, I'll put it up as soon as I get home from work ~4:30pm central time.  I really appreciate your help.

---

### Post by hemes on 2006-07-07
GOT IT!!  Somehow I missed the libgtk2.0-dev package...  :confused: 

Thanks again,
Brett

---

