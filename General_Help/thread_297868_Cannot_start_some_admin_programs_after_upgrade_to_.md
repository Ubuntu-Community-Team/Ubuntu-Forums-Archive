---
title: "Cannot start some admin programs after upgrade to Edgy"
date: 2006-11-11
forum: General Help
---

### Post by DavidTangye on 2006-11-11
On one machine that I upgraded from Dapper to Edgy, the following System -> Administration programs will not start:

[LIST]
[*]Networking
[*]Services,
[*]Shared Folders
[/LIST]


Instead I get an Error dialog box: "The configuration could not be loaded. You are not allowed to access the system configuration."

They used to work under Dapper.

The other items on the System -> Administration menu work.

Any ideas?

---

### Post by towsonu2003 on 2006-11-13
This user seems to have the same problem: [https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/71102](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/71102) I would watch that bug report and see where it goes. I think it will be marked as duplicate of a well known bug (which I couldn't find). If that happens, you'll probably read a workaround for it. 

A comment from you (such as "I experience the same thing and I did this and that to upgrade") to the bug report would probably help?

---

### Post by aysiu on 2006-11-13
What's the output when you launch one of those commands from the terminal? For example ```
gksudo network-admin
```

---

### Post by Fabiano Shark on 2006-11-15
If you installed in OEM mode, run **sudo oem-config-prepare** to clean up the temporary files, so reboot the system and run **gksu users-admin** and give the all privileges you want to your user. ;)

---

### Post by DavidTangye on 2006-11-15
> **Fabiano Shark said:**
> If you installed in OEM mode
thanks for the thought, but no, I installed the alternative iso as a new install and not in OEM mode.

---

