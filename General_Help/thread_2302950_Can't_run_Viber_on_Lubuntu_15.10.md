---
title: "Can't run Viber on Lubuntu 15.10"
date: 2015-11-14
forum: General Help
---

### Post by rezbd on 2015-11-14
Installed Viber on Lubuntu 15.10 64-bit, but can't open it. When I  click on the icon, it shows: *Failed to change to directory '' (No such  file or directory)*

 When I run 'viber' on terminal, it shows:
 ```
viber: error while loading shared libraries: libgstapp-0.10.so.0: cannot open shared object file: No such file or directory


```

---

### Post by rezbd on 2015-11-15
The problem is partially solved. When I click on the 'Viber' icon from the menu, it shows: [I]Failed to change to directory '' (No such file or directory)
[/I]I only can run Viber from terminal doing:
```
cd Viber
```
```
./Viber.sh
```

---

### Post by Adrian_Ho on 2015-12-25
Not sure why you're getting a shared library error, but the other issue is a long-standing one with a simple fix.

Edit [FONT=courier new]/usr/share/applications/viber.desktop[/FONT] with root privileges and change:

```
Path=
```

to:

```
Path=*<Viber_install_dir>*
```

If you installed with the Viber-supplied deb, *[FONT=courier new]<Viber_install_dir>[/FONT]* would be [FONT=courier new]/opt/viber[/FONT].

---

