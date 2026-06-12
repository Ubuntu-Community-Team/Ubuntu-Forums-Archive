---
title: "Cannot get scripts to execute on startup"
date: 2007-02-28
forum: General Help
---

### Post by speedsix on 2007-02-28
I place a working script into /etc/init.d and run the 'update-rc.d myscript defaults' command which makes the shortcut but my script never seems to start on boot?

The script works fine if I execute it manually. Script is owned by root and executable.


Thanks

Dom

---

### Post by speedsix on 2007-02-28
I modified /etc/init.d/skeleton and it works now.

---

