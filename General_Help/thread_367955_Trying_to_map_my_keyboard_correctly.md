---
title: "Trying to map my keyboard correctly"
date: 2007-02-22
forum: General Help
---

### Post by ljoslin on 2007-02-22
I have a toshiba Satalite L25 and I am trying to get the super key/left alt to work correctly.  If anybody has an idea on how I can do this please do share!  Thanks!

---

### Post by DagMan on 2007-02-24
If you know what script the key is calling on (and it might do it as root which would require you to add an entry to the sudoers file to let it run without a password) or can figure it out, perhaps it is in /etc/acpi or some other function that you want to use, then you can use xbindkeys-config to map the keycombo to the command and run xbindkeys at startup so still works after reboot.

Hope that helps you out.

---

