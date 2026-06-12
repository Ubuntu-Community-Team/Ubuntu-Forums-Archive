---
title: "Where are flatpak apps installed?"
date: 2021-09-21
forum: General Help
---

### Post by mickee384 on 2021-09-21
I know where snaps are installed, but I am curious as to where any flatpak apps are installed.

---

### Post by mickee384 on 2021-09-21
found it

flatpak list

---

### Post by deadflowr on 2021-09-21
I get *unknown option* for that command.
But flatpak apps are downloaded and installed to /var/lib/flatpak/app.

Read more on flatpak's here: [https://docs.flatpak.org/en/latest/flatpak-command-reference.html]("https://docs.flatpak.org/en/latest/flatpak-command-reference.html")

---

### Post by Dennis N on 2021-09-21
For anyone interested,
```
flatpak --help
```
reveals common commands
```
flatpak list --app
```
will list only the applications installed.

---

