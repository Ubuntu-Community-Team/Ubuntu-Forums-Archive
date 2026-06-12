---
title: "synaptic package manager error"
date: 2007-12-03
forum: General Help
---

### Post by qadiey on 2007-12-03
i'm try to install emerald theme manager,but at several time,the connection of internet is suck and disconnected..then,i'm try back to open the synaptic package manager after the connection is ok...But it can't open and notice that:

An error occured
The following details are provided:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what i should do?
:confused:

---

### Post by FuturePilot on 2007-12-03
Try
```
sudo dpkg --configure -a
```

---

### Post by forestpixie on 2007-12-03
try this in terminal (apps >accessories)

```
sudo dpkg --configure -a
```

---

### Post by qadiey on 2007-12-03
thank..it ok now..:)

---

### Post by forestpixie on 2007-12-03
can you mark thread solved please

---

### Post by DiscGo on 2008-02-03
[IMG]http://i51.photobucket.com/albums/f375/DiscGolfDiver/Website/error.png[/IMG]



I was just coming on with the same problem. 


I obvisously still don't understand a lot of ubuntu but I love all the support. Thanks a lot! That was a quick fix.

---

