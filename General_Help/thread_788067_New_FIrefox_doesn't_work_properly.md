---
title: "New FIrefox doesn't work properly"
date: 2008-05-09
forum: General Help
---

### Post by slinky89 on 2008-05-09
Hello,

I upgraded Ubuntu, with the upgrade I also getted a new version of Firefox: Mozilla Firefox 3 Beta 5. Although this version doesn't work properly so I actually wanna go back to the older version but I don't know how. Just installing a older version gives a error.


Slinky

---

### Post by Zorael on 2008-05-09
Do you want an older build of Firefox 3 or an installation of Firefox 2?

If you want FF2, just install the **firefox-2** package. If you want to get rid of FF3, just remove the **firefox-3.0** package. In Synaptic, Adept, or package manager of choice.


Terminal command to completely replace (install ff2 and remove ff3):
```
$ sudo aptitude purge firefox-3.0 firefox-2+
```

---

### Post by slinky89 on 2008-05-09
I will try the terminal command because the other way you suggest didn't work.

---

### Post by sailor2001 on 2008-05-09
better suggestion would be to install 'seamonkey' and forget about firefox

---

