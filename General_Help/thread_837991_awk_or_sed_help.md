---
title: "awk or sed help"
date: 2008-06-23
forum: General Help
---

### Post by dapim on 2008-06-23
dashj,ikpoi,klop,9,B
masd,cvbb,asd,8,I

i wish to remove the second colum, how do i do it with sed or awk or any other way?

---

### Post by geirha on 2008-06-23
```
$ echo -e "dashj,ikpoi,klop,9,B\nmasd,cvbb,asd,8,I" |cut -d, -f1,3-
dashj,klop,9,B
masd,asd,8,I

```
Neither sed, nor awk, but it does what you want I think.

---

### Post by nick_h on 2008-06-23
With awk you could use:
```
awk -F, 'BEGIN {OFS=","} {print $1,$3,$4,$5}' testfile
```

---

