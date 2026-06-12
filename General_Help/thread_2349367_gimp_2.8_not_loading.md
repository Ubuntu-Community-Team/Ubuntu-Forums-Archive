---
title: "gimp 2.8 not loading"
date: 2017-01-13
forum: General Help
---

### Post by UncleMonty on 2017-01-13
I recently installed ubuntu 16.04 (64 bit). For some reason when I attempt to load GIMP I get this:

 [ATTACH=CONFIG]273190[/ATTACH]

(I've tried reinstalling it, and xkill doesn't get rid of it).

---

### Post by howefield on 2017-01-13
Try deleting (or renaming) the templates folder in ~/.gimp-2.8

```
mv ~/.gimp-2.8/templates ~/Documents
```

---

### Post by UncleMonty on 2017-01-13
> **howefield said:**
> Try deleting (or renaming) the templates folder in ~/.gimp-2.8

```
mv ~/.gimp-2.8/templates ~/Documents
```

Excellent suggestion - I took it one further and deleted the whole thing - it now works perfectly. Thanks.

---

### Post by howefield on 2017-01-13
> **UncleMonty said:**
> Excellent suggestion - I took it one further and deleted the whole thing - it now works perfectly. Thanks.

:)

Cool, thanks for marking as solved and glad it is sorted.

---

