---
title: "Very quick question re. permissions"
date: 2008-02-23
forum: General Help
---

### Post by speedsix on 2008-02-23
I have a script owned by root with the suid/sgid bits set yet it cannot perform any root only tasks i.e smbmount when run by a regular user? Works fine run by root.

---

### Post by angrboda on 2008-02-23
...which behaviour is wanted. The script inherits the rights and permissions of the user calling it. Otherwise a simple script could do a lot of harm in your system. If it is absolutely needed you might want to alter the script to ask for the password for root operations. But be carful with that: Be sure to limit admin access to the intended task only. You have been warned...

---

### Post by pointone on 2008-02-23
I had a problem in Debian where it wasn't possible to set the SUID bit on a non-binary file (some security issue). I ended up converting my Bash script to a simple C script, compiling, and it worked fine afterwards.

I can only assume Ubuntu shares the same "feature".

---

