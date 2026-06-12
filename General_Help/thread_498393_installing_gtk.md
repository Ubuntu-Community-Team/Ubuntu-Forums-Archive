---
title: "installing gtk"
date: 2007-07-11
forum: General Help
---

### Post by lukemack on 2007-07-11
Hi,

Can someone give me the correct apt-get install line for installing gtk? I need it to resolve this configre error:

configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

alternatively, the syntax for adding the correct path?

thanks!

lukemack.

---

### Post by quux on 2007-07-11
Try "sudo apt-get install libgtk2.0-dev". If the application you want to compile is a GNOME application you probably want to "sudo apt-get install gnome-core-devel" as well.

---

### Post by markbusu on 2008-02-22
Cheerz worked!!

---

### Post by slimx3m on 2008-06-21
thanks for this info

---

### Post by flash2lightning on 2008-07-04
thanks so much for this! ive been banging my head around all afternoon on this :)

---

