---
title: "awk, view the 3rd field of every line"
date: 2008-06-29
forum: General Help
---

### Post by dapim on 2008-06-29
view the 3rd field of every line,

asd,dfgdf,listen,opex


i have this, but return empty??
awk -F "\",\"" '{print $3}' file.csv

---

### Post by brian_p on 2008-06-29
> **dapim said:**
> view the 3rd field of every line,

asd,dfgdf,listen,opex


i have this, but return empty??
awk -F "\",\"" '{print $3}' file.csv

```
awk -F "," '{print $3}' file.csv
```

---

### Post by nick_h on 2008-06-29
or even just:
```
awk -F, '{print $3}' file.csv
```

alternatively use the *cut* command:
```
cut -d, -f3 < file.csv
```

---

