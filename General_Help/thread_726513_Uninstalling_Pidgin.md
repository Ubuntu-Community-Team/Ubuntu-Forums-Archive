---
title: "Uninstalling Pidgin"
date: 2008-03-16
forum: General Help
---

### Post by psychofish25 on 2008-03-16
I ran sudo apt-get remove pidgin and it did its thing, but for some reason it still opens when I type pidgin in terminal. I went to /usr/bin and pidgin was nowhere to be found. Does ubuntu cache uninstalled programs and save them until you restart? I'm just a bit confused.

Thanks,
Jordan

---

### Post by PeterJS on 2008-03-16
Run:
```

which pidgin

```
to find out where pidgin is installed. Or stringing a few steps together you can run:
```

apt-file search `which pidgin`

```
to find out which package the pidgin binary is associated with.

---

