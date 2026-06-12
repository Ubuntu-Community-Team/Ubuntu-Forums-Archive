---
title: "Strange update error"
date: 2007-01-26
forum: General Help
---

### Post by abelthorne on 2007-01-26
Hello,
I've run "apt-get upgrade" to update my system a few minutes ago and there were two new packages: *app-install-data-commercial* and *linux-libc-dev*.

During installation, I got error messages (which never happened to me before):
```
Préparation du remplacement de app-install-data-commercial 6.1 (en utilisant .../app-install-data-commercial_6.2_all.deb) ...
Dépaquetage de la mise à jour de app-install-data-commercial ...
Préparation du remplacement de linux-libc-dev 2.6.17.1-10.34 (en utilisant .../linux-libc-dev_2.6.17.1-50.50_i386.deb) ...
Dépaquetage de la mise à jour de linux-libc-dev ...
Paramétrage de app-install-data-commercial (6.2) ...
Caching application data...
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 69, in ?
    generate_cache()
  File "/usr/sbin/update-app-install", line 49, in generate_cache
    menu.createMenuCache(options.cache_dir)
  File "/usr/lib/python2.4/site-packages/AppInstall/CoreMenu.py", line 28, in createMenuCache
    menu = xdg.Menu.parse(os.path.abspath(os.path.join(self.menudir, "applications.menu")))
  File "/var/lib/python-support/python2.4/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/var/lib/python-support/python2.4/xdg/Menu.py", line 856, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/var/lib/python-support/python2.4/xdg/Menu.py", line 856, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/var/lib/python-support/python2.4/xdg/Menu.py", line 856, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/var/lib/python-support/python2.4/xdg/Menu.py", line 856, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/var/lib/python-support/python2.4/xdg/Menu.py", line 862, in __genmenuNotOnlyAllocated
    menuentries = rule.do(tmp["cache"].getMenuEntries(menu.AppDirs), rule.Type, 1)
  File "<string>", line 6, in do
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc3 in position 44: ordinal not in range(128)

Paramétrage de linux-libc-dev (2.6.17.1-50.50) ...
```

Sorry for the french language, the corresponding strings are normal. The problem starts at "traceback".

What happened, on which package, have I broken something, will I have issues with the OS and how to fix the problem ?

I've tried to upgrade again but I get no new updates.

---

### Post by tr333 on 2007-01-26
try doing 'sudo apt-get update' first to update the package list.

---

### Post by abelthorne on 2007-01-26
Already did it, in fact (each time I use apt-get upgrade, I update the packages list first).

---

### Post by emmet on 2007-01-26
I'm get a similar problem with the same package. 

The app-install-data-commercial package appears in the software update list on the installer, but when I click on the button to "Install Updates" it doesn't actually do anything but refresh the list.

Very strange...

Emmet

---

### Post by abelthorne on 2007-01-27
Just powered my computer on for today, got updates notification in which there was the same package again. And it has the same errors again... :(

---

