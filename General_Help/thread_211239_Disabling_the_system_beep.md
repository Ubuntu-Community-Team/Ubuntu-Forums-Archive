---
title: "Disabling the system beep"
date: 2006-07-08
forum: General Help
---

### Post by halfthelaw on 2006-07-08
Is there any way to disable the system beep?

---

### Post by Max Luebbe on 2006-07-08
I just disconnect my pc speaker from the motherboard.

Probably the simplest non-technical answer I can think of.

---

### Post by tonyr on 2006-07-08
**System->Preferences->Sound**, under the **System Beep** tab,
uncheck **Enable system beep**.

---

### Post by shanepardue on 2006-11-10
> **tonyr said:**
> **System->Preferences->Sound**, under the **System Beep** tab,
uncheck **Enable system beep**.
Why's my system beep tab grayed out? It won't let me edit these preferences.
I'm running Edgy for the record.

---

### Post by ohgod on 2006-11-10
Not sure why your system beep option is grayed out, but here's how I disabled the beep on my box:

```

sudo gedit /etc/rc.local

```
then add this line to the file (ABOVE the exit 0 line):
```

modprobe -r pcspkr

```

---

