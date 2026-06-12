---
title: "Uninstalled Wubi, but..."
date: 2007-10-21
forum: General Help
---

### Post by Planets on 2007-10-21
Hello,

I've uninstalled Wubi, but "Ubuntu-Linux" is still in my boot menu. Any ideas on how to remedy this?

---

### Post by ago on 2007-10-21
It's a bug that has been fixed in newer releases. To uninstall manually run regedit and delete the key: 

HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Ubuntu

---

### Post by Planets on 2007-10-21
Hm, I don't seem to have "Ubuntu" there.

---

### Post by ago on 2007-10-21
Maybe wubi depends on what version it is

---

