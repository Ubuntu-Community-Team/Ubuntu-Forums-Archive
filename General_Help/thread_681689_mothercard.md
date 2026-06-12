---
title: "mothercard"
date: 2008-01-29
forum: General Help
---

### Post by epqr on 2008-01-29
how can i find out what my motherboard is in xubuntu?

---

### Post by p_quarles on 2008-01-29
Open a terminal (alt-F1), and run the following command:
```
sudo lshw | grep -A 6 core
```
The output will be a description of your motherboard, including the vendor and model.

---

