---
title: "MySQL -- &quot;Can't get stat of  ... (Errcode: 13)&quot;"
date: 2013-05-26
forum: General Help
---

### Post by weyland42 on 2013-05-26
Trying to import data from a csv file. Done this many times before. but perhaps not with this MySQL version -- 5.5.31 on Ubuntu 12.04.

```
mysql> load data infile '/media/vertex/00-gwd/gwd-regs-20130526.delim.out' into table gwdreg fields terminated by ';'; 
ERROR 13 (HY000): Can't get stat of '/media/vertex/00-gwd/gwd-regs-20130526.delim.out' (Errcode: 13)
```

Both file and directory have 777 permissions.

I've seen this problem mentioned on the web many times, but the solutions suggested don't work for me. (Including LOCAL -- not allowed in 5.5.31.)

(I can't get into my MySQL forum account for help because they insist on Oracle registration now, which I did, but it rejects my login attempts even with the correct id and pw. Given up trying.)

---

