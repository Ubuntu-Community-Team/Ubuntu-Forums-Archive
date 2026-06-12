---
title: "Editing xorg.config"
date: 2008-06-18
forum: General Help
---

### Post by nsivin on 2008-06-18
I have recently upgraded to Hasty, and am trying to configure my monitor so I can use portrait mode as I did in the last version. I have already installed the NVIDIA drivers, but screen rotation is not an option in PREFERENCES, SCREEN RESOLUTION. I have tried to edit xorg.config, but I am puzzled about how to do it. There are two copies in my system, and I have no idea about which to edit or how to open either one in gedit. Can someone give me simple, straightforward instructions?

---

### Post by mali2297 on 2008-06-18
Open it with
```

gksudo gedit /etc/X11/xorg.conf

```
(via the terminal or the run dialog)

I can't give you any instructions on what lines you should add to the file though.

---

### Post by sisco311 on 2008-06-18
> **mali2297 said:**
> Open it with
```

gksudo /etc/X11/xorg.conf

```(via the terminal or the run dialog)

I can't give you any instructions on what lines you should add to the file though.

```

gksudo **gedit **/etc/X11/xorg.conf

```

---

