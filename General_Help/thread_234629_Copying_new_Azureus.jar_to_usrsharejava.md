---
title: "Copying new Azureus.jar to /usr/share/java/"
date: 2006-08-11
forum: General Help
---

### Post by kapkorn on 2006-08-11
I looked up my problem and it says to copy the new cvs .jar file into this directory, however it being a locked directory I need sudo access to it so I assume I have to go through the command line.


What command would I use to copy this file that I downloaded to that directory and overwrite the previous file.



Thanks.

---

### Post by foxy123 on 2006-08-11
```
sudo cp <file> /destination/directory
```

---

### Post by Jagot on 2006-08-11
Or you could launch nautilus as root and drag and drop.  Hit alt+f2 then type:

```
gksudo nautilus
```

---

### Post by kapkorn on 2006-08-11
Thanks guys worked perfect.

---

