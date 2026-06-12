---
title: "removed packages list"
date: 2007-04-01
forum: General Help
---

### Post by sblanzio on 2007-04-01
is it possible to find a list of recently removed packages?

I did a mistake beginning to remove libgl1-mesa-glx. It began removing ark and other useful packages (maybe 10 or 15), so I stopped that.

Unluckly now I don't know which packages are missing, and aptitude doesn't seem to be useful to find out that.

How can I know which packages I removed so that I can install them manually? thanks a lot!

---

### Post by jrib on 2007-04-01
> **sblanzio said:**
> is it possible to find a list of recently removed packages?

I did a mistake beginning to remove libgl1-mesa-glx. It began removing ark and other useful packages (maybe 10 or 15), so I stopped that.

Unluckly now I don't know which packages are missing, and aptitude doesn't seem to be useful to find out that.

How can I know which packages I removed so that I can install them manually? thanks a lot!

If you used aptitude, it keeps a log at /var/log/aptitude

---

### Post by zvacet on 2007-04-01
```
sudo aptitude  libgl1-mesa-glx 
```

---

