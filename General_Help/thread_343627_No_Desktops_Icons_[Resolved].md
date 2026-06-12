---
title: "No Desktops Icons [Resolved]"
date: 2007-01-21
forum: General Help
---

### Post by Graham1 on 2007-01-21
Hi All

My desktop seems to be empty :(. No trash can or disk drive :confused:. How can I get these back?

:)

---

### Post by brt on 2007-01-21
i would try:

```
killall nautilus
```

---

### Post by Graham1 on 2007-01-21
Tried that but still blank I'm afraid.

:)

---

### Post by David Corrales on 2007-01-21
You can add those via the gconf tool. Go to System Tools/Configuration Editor. If it doesn't exist, launch **gconf-editor** from a command line.
In there, go to apps/nautilus/desktop. There you'll find checkboxes to enable/disable the desktop icons you want :)

---

### Post by Graham1 on 2007-01-21
Thanks David, that did the job.

:)

---

### Post by David Corrales on 2007-01-22
woot!

---

