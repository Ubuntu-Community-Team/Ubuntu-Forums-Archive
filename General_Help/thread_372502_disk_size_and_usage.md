---
title: "disk size and usage"
date: 2007-02-28
forum: General Help
---

### Post by rjfioravanti on 2007-02-28
How can I figure out how much space is taken and free on my hard drive from the terminal? 

Also, when I do ls -l, every folder comes up as being size 4096, which is fine, but is there a way to recursively look down the directory hierarchy to see how large the folder is with all its contents?

Thanks

---

### Post by taurus on 2007-02-28
```
df -h
du -h ~
```

---

### Post by highneko on 2007-02-28
Terminal command:
```
[COLOR="DimGray"]# If you want recursive then:[/COLOR]
ls -lhR
[COLOR="DimGray"]# If you want a good way then:[/COLOR]
sudo du -ch --max-depth=0 .

```

---

