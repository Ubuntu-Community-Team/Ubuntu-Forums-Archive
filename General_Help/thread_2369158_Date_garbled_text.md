---
title: "Date garbled text"
date: 2017-08-19
forum: General Help
---

### Post by Cider on 2017-08-19
```
-:/$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial
-:/$ date
×©' ××•×’ 19 14:12:26 IDT 2017
```

Anyone know why my date is garbled text?

---

### Post by vasa1 on 2017-08-19
What does```
LANG=C date
```show?

---

### Post by Cider on 2017-08-19
```
~$ LANG=C date
×©' ××•×’ 19 21:05:22 IDT 2017
```

---

