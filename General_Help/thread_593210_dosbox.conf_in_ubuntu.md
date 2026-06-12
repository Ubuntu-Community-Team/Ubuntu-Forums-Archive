---
title: "dosbox.conf in ubuntu?"
date: 2007-10-26
forum: General Help
---

### Post by UK-Wobbie on 2007-10-26
Hey do any one know where dosbox.conf is in ubuntu?

Thanks

---

### Post by burnttoast11 on 2007-10-27
I believe dosbox creates a default one whenever you start it.  To make your own, type this in dosbox when you first start it. (In Z:\)
```
config -writeconf dosbox.conf
```
This will make the dosbox.conf file in your home/yourname/ directory.  If you want you can create it in another directory.  (I put mine in /home/peder/.dosbox)

Now you can edit this file as you like, but to have dosbox use it, you have to run dosbox with the following parameter.
```
dosbox -conf dir/to/dosbox.conf
```

---

