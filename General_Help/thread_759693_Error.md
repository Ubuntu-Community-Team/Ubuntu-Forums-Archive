---
title: "Error"
date: 2008-04-19
forum: General Help
---

### Post by Simplicity7 on 2008-04-19
Whenever I try to run the synaptics package manager I get this message and I'm not sure what to do. I'm fairly new so I apologize.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by ibutho on 2008-04-19
Run gnome-terminal and enter the command
```
sudo dpkg --configure -a
```

---

### Post by dashnak on 2008-04-19
> **Simplicity7 said:**
> Whenever I try to run the synaptics package manager I get this message and I'm not sure what to do. I'm fairly new so I apologize.

E: dpkg was interrupted, **you must manually run 'dpkg --configure -a' to correct the problem**. 
E: _cache->open() failed, please report.
Doing that will surely help. Run that command, in a terminal.

---

