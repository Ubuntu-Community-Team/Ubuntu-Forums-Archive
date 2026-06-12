---
title: "Synaptic Always Wants The CD To Install"
date: 2005-07-02
forum: General Help
---

### Post by XDevHald on 2005-07-02
By any chance would anyone know how to get Synaptic from asking for the 5.04 CD? It's really annoying.


Thanks,
Steve

---

### Post by PMO6022 on 2005-07-02
[QUOTE=BB]By any chance would anyone know how to get Synaptic from asking for the 5.04 CD? It's really annoying.


Thanks,
Steve[/QUOTE]
 In the file /etc/apt/sources.list, comment out the line referring to the cd.  It is probably the first line in the file.

---

### Post by XDevHald on 2005-07-02
[QUOTE=PMO6022]In the file /etc/apt/sources.list, comment out the line referring to the cd.  It is probably the first line in the file.[/QUOTE]
 Beautiful, thank for the quick reply :D

---

