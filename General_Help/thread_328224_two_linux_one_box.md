---
title: "two linux one box"
date: 2006-12-30
forum: General Help
---

### Post by anv on 2006-12-30
I have two hard disks eachone has different linux distro, one has fedora and one has ubuntu. this far I have used them as separate but if I'd like to choose them from grub how should I proceed?

---

### Post by dcstar on 2006-12-30
> **anv said:**
> I have two hard disks eachone has different linux distro, one has fedora and one has ubuntu. this far I have used them as separate but if I'd like to choose them from grub how should I proceed?

You need to edit the /boot/grub/menu.lst file and manually add in the other disk settings.

Do a forum search and you should find something with detailed instructions to help you.

---

### Post by koenn on 2006-12-30
run ```
sudo update-grub
```
maybe it detects both OS's and makes boot meny entries for them automatically. 
make a backup copy of /boot/grub/menu.lst first

---

