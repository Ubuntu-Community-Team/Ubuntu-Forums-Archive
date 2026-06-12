---
title: "total size of files"
date: 2008-06-30
forum: General Help
---

### Post by cliffer_ny on 2008-06-30
Hi,
I have a directory full of files created not the same day, I would like to know the size per day of the total of the files:

like : ls -l | grep 26 | ...

Any idea ?

Thx for the help
Cliff

---

### Post by cliffer_ny on 2008-06-30
ls -l | grep "whatever" | awk '{sum+=$5} END {print sum}'

---

### Post by ghostdog74 on 2008-06-30
there's no need for grep if you use awk because awk can do what sed/grep/wc etc can.
```

ls -l | awk '/whatever/{sum+=$5} END {print sum}'

```

---

