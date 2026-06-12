---
title: "HOWTO: suspend vaio sz with  Intel 945GM/GMS/GME"
date: 2008-04-30
forum: General Help
---

### Post by freakavoid on 2008-04-30
I just managed to get my vaio sz2xp to suspend on hardy and thought I share it since I couldn't find this solution on the forum.

The problem is wireless network card and all I had to do was edit /etc/default/acpi-support

```
sudo nano /etc/default/acpi-support
```

and add "networking" to STOP_SERVICES to look like this:

```
# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"

```

Afterwards restart acpi

```
sudo /etc/init.d/acpid restart
```

and it should work.
Hope this helps someone.

---

