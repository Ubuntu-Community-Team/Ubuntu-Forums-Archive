---
title: "batch remove the last 9 characters from folders names?"
date: 2014-10-07
forum: General Help
---

### Post by sohlinux on 2014-10-07
Hello, How can I batch remove the last 9 characters from folders names?

for example I have many folders as follows

jhgtyuioplgdrtghnbjk after will be jhgtyuioplg

yt00:hnbfdkk ioiuyui after will be yt00:hnbfdk

qw jh dd0ddyyt:jkopi after will be qw jh dd0dd

thanks

---

### Post by Vaphell on 2014-10-07
```
for d in *; do mv "$d" "${d%?????????}"; done
```
or 
```
rename 's/.{9}$//' *
```

if the folders are mixed with files, then some condition to narrow down is required eg
```
[[ -d "$d" ]] || continue
```


edit: it's possible to glob dirs only with */ but it would require accounting for that additional char (eg 10x'?' / .{10})

---

### Post by sohlinux on 2014-10-07
perfect. thanks :)

---

