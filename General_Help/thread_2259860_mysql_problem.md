---
title: "mysql problem"
date: 2015-01-07
forum: General Help
---

### Post by johnnybgoode on 2015-01-07
what's wrong with this sentence:

mysql> insert into boeken values('Fortuna's dochter','W. Schoenenberger');
    '> 
Is it the " ' " in Fortuna's ?? If it is, How do I proceed?

---

### Post by kpatz on 2015-01-07
Escape the apostrophe with a backslash.  Such as:

```
insert into boeken values('Fortuna\'s dochter','W. Schoenenberger');
```

---

