---
title: "Foolish move on my part, misuse of usermod, please help"
date: 2007-05-05
forum: General Help
---

### Post by MusashiX90 on 2007-05-05
I just used usermod without looking further into it, and as a result, it removed me from every group I was previously in, causing me not to be able to use "sudo" and "gksudo".  Any solutions?

---

### Post by bapoumba on 2007-05-05
Hello,
boot in recovery mode, you'll be root with a **#** prompt.
```
# adduser <your_login_here> admin
reboot
```

You can add yourself to the following groups (first user created is in these groups by default)
```
~$ groups
bapoumba adm dialout cdrom floppy audio dip video plugdev netdev lpadmin powerdev scanner admin
```
Skip "bapoumba" which is my login ^^

---

