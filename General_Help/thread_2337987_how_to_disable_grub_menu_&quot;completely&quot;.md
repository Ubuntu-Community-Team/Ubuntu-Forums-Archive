---
title: "how to disable grub menu &quot;completely&quot; ?"
date: 2016-09-23
forum: General Help
---

### Post by muhammed_ozbilici on 2016-09-23
i want to disable it, never show up after power off, restart computer , any circumstances ... i changed these, but still coming 
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true

---

### Post by oldrocker99 on 2016-09-23
After you edited grub did you enter this?```
sudo update-grub
```

It's essential after editing grub.

---

### Post by muhammed_ozbilici on 2016-09-23
yes i did, but sill showing.

---

### Post by Jimysbil on 2016-09-23
Have you try:
```
GRUB_TIMEOUT=0
```

And then again:
```
update-grub
```

---

### Post by muhammed_ozbilici on 2016-09-28
nope, still same

---

