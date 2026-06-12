---
title: "Sound only with root. [Resolved]"
date: 2007-01-22
forum: General Help
---

### Post by Bider on 2007-01-22
I am unable to receive sound through my regular user account, It is only available if i run an application which can play media files as root. Any ideas on how i can enable it for the non root account?.

---

### Post by aysiu on 2007-01-22
```
sudo adduser bider audio
``` should do it.

---

### Post by Bider on 2007-01-22
Yea i also noticed i had lack of privileges on this account aswell, fixed that to.

thanks for the help.

---

### Post by aysiu on 2007-01-22
A privileged (administrative) user named *username* should belong to these groups:
*username* adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

---

### Post by Keymone on 2007-09-17
what if it does not helps?

---

