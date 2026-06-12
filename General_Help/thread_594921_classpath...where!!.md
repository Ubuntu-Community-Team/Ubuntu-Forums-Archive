---
title: "classpath...where?!?!?"
date: 2007-10-28
forum: General Help
---

### Post by Keps on 2007-10-28
hi, i installed jdk 6 from synaptic. obviusly it installed the packet and setted the environment(classpath, path and java_home).
Now i have to install the jmf, and i have to add to classpath also the directory of jmf.
The problem is that i don't know where synaptic setted the classpath, so i don't know where modify it.
Someone can solve my problem?

Thank to all

---

### Post by taurus on 2007-10-28
You can create a new one in ~/.bashrc.

```
gedit ~/.bashrc
```
It should look something like

```
CLASS_PATH=/path_to_where_the_stuff_is
export CLASS_PATH
```

---

### Post by Keps on 2007-10-29
thank you!!!
:):):)

---

