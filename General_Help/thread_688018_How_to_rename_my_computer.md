---
title: "How to rename my computer?"
date: 2008-02-04
forum: General Help
---

### Post by FastMady123 on 2008-02-04
I chose the name "Geek" during installing because some geeks use GNU/Linux. I want to change the name to Ubuntu. How to do that?

---

### Post by Gordaen on 2008-02-04
Have you tried editing /etc/hostname?

---

### Post by shutslar on 2008-02-04
try changing it in 2 places:

1>   /etc/hostname
2>  /etc/hosts

You can do this by opening a terminal and executing the following commands and making your chagnes.

```

sudo gedit /etc/hostname

```

```

sudo gedit /etc/hosts

```

---

