---
title: "[SOLVED] Set terminal Time Zone?"
date: 2007-11-21
forum: General Help
---

### Post by sci-fi guy on 2007-11-21
I have my time zone set to Pacific Time in the Date/Time Manager, but the terminal acts like I am three time zones to the east. What gives?

---

### Post by bingoUV on 2007-11-21
> **sci-fi guy said:**
> I have my time zone set to Pacific Time in the Date/Time Manager, but the terminal acts like I am three time zones to the east. What gives?

Which terminal? Does graphical terminal emulator also do this? or only the ctrl-alt-F1 terminal?

Set the TZ environment variable appropriately. I am not sure, but I guess it is PST8PDT. Google for the correct value. Then, in ~/.bashrc
```

export TZ=PST8PDT

```

---

### Post by sci-fi guy on 2007-11-21
This happens in the graphical terminal window. Haven't tried it in Ctrl-Alt-F1.

---

