---
title: "open crontab -e with vi editor"
date: 2006-10-21
forum: General Help
---

### Post by cccc on 2006-10-21
hi

howto configure dapper drake to open crontab -e with **vi** editor ?

kind regards
cccc

---

### Post by Sir_Yaro on 2006-10-21
```
export VISUAL=vi
```

---

### Post by ayoli on 2006-10-21
```
export EDITOR=vi && crontab -e
```
works even with gedit

---

### Post by cccc on 2006-10-21
or:```

update-alternatives --config editor
```

---

