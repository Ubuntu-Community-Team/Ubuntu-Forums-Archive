---
title: "Messages"
date: 2013-12-02
forum: General Help
---

### Post by borgward on 2013-12-02
Where are the messages that appear on the screen at startup saved? I want to see the entire message, not just error messages.

---

### Post by bashiergui on 2013-12-02
What messages? The BIOS booting up? Describe them.

---

### Post by borgward on 2013-12-02
I guess so. Thats the messages that appear on the screen as the machine is booting up. Sorry, did not know the proper nomenclature for them.

---

### Post by Dennis N on 2013-12-02
The terminal command:

```
dmesg | more
```

will show you kernel messages produced during startup. Maybe these are what you want. Press space bar to see the next bunch of lines.

There are other recorded logs in **/var/log**

---

### Post by oldos2er on 2013-12-03
/var/log/boot.log

---

