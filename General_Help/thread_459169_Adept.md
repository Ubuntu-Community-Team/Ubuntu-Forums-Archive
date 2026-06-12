---
title: "Adept"
date: 2007-05-30
forum: General Help
---

### Post by royjg2 on 2007-05-30
Greetings community

Adept froze installing update, i tough i had closed it but now every time i open system, message tells me i cannot install anything with adept, it is already running or equivalent is
Is there a line command i can use to make sure it is closed and ready for further use
Thank you \\:D/

---

### Post by taurus on 2007-05-30
See if it is running in the background.  If it is, then you can kill it.

```
ps -A
```
or-
```
sudo killall adept
```

---

### Post by royjg2 on 2007-05-30
Greetings
Problem fixed with "sudo dpkg --configure -a" found in magasine since I was responsible for interrupting installation
Many thanks for quick reply
:-({|=

---

