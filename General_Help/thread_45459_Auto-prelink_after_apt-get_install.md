---
title: "Auto-prelink after apt-get install ?"
date: 2005-06-30
forum: General Help
---

### Post by Youssef on 2005-06-30
Is there anyway to make prelink -avmR run after each apt-get and dpkg -i ? I think Yoper does it.

---

### Post by intangible on 2005-06-30
To make it run after every apt-get action (apt-get install, apt-get remove), add this line to **/etc/apt/apt.conf** (create that file if it doesn't exist)

```
DPkg::Post-Invoke {"echo Running prelink, please wait...;prelink -avmR";}
```

That will also run inside synaptic.

Dunno how to make it run after every dpkg command though.

---

