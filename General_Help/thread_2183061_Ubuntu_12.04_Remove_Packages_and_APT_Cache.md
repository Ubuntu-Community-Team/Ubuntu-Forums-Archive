---
title: "Ubuntu 12.04 Remove Packages and APT Cache"
date: 2013-10-23
forum: General Help
---

### Post by ac98521 on 2013-10-23
What happens when I remove the package configs and APT Cache? I saw it in the UBUNTU TWEAK.

---

### Post by oldos2er on 2013-10-23
Which package configs are you referring to, /etc or /home/user ? ```
sudo apt-get purge <package name>
``` removes configuration files from /etc, those in the home folder must be manually deleted by the user.

Clearing the APT cache means deleting all package files in /var/cache/apt/archives, where they are normally stored when downloaded. You can do so with ```
sudo apt-get clean
```

All this info and more can be found with ```
man apt-get
```

---

### Post by ac98521 on 2013-10-23
wll deleting them remove all the installed files?

---

### Post by oldos2er on 2013-10-23
Deleting the stored package files will not delete the corresponding programs that are already installed.

---

### Post by ac98521 on 2013-10-24
how about APT cache?

Also, will this affect my system in a negative way after deleting them?

---

### Post by oldos2er on 2013-10-24
> **ac98521 said:**
> how about APT cache?


I thought that's what we were talking about. /var/[COLOR=#ff0000]cache[/COLOR]/apt/archives IS the APT cache.

> **ac98521 said:**
> Also, will this affect my system in a negative way after deleting them?

Already answered this above, no. If you're talking about program config files in /etc, I don't see any reason you would remove them if you're not uninstalling their programs at the same time. *If* you remove just config files it might impact your system negatively, yes.

If you could explain what your goal is it might help.

---

