---
title: "Shutdown use sudo shutdown -h now?"
date: 2007-04-17
forum: General Help
---

### Post by spankymasterc on 2007-04-17
Is there anyway that i can make the shutdown button use sudo shutdown -h now or should i just a script?

---

### Post by kidders on 2007-04-18
Hi there,

That script may already exist on your system. This is from /etc/acpi/powerbtn.sh on my Ubuntu...

```
...
...
# If all else failed, just initiate a plain shutdown.
/sbin/shutdown -h now "Power button pressed"
```

Depending on what other ACPI-aware applications you are running, you may want to alter it, so it always just shuts everything down though.

---

