---
title: "/bin/mv: Argument list too long"
date: 2006-12-02
forum: General Help
---

### Post by fng on 2006-12-02
seems there is a maximum limit of files you can move with mv.
Anyone knows a workaround?

```
fng@butters:~/Desktop/zipped$ mv * ~/downloads/
bash: /bin/mv: Argument list too long
fng@butters:~/Desktop/zipped$ ls -al | wc -l
8820
fng@butters:~/Desktop/zipped$
```

---

### Post by nixclusive on 2006-12-02
```
cd <destination directory>
tar c <source directory> | tar xv
```

this should help.

---

### Post by reclusivemonkey on 2006-12-03
> **fng said:**
> seems there is a maximum limit of files you can move with mv.
Anyone knows a workaround?

```
fng@butters:~/Desktop/zipped$ mv * ~/downloads/
bash: /bin/mv: Argument list too long

```

You've just told your computer to move everything into ~/downloads. I suspect what you wanted to do was to move everything in ~/Desktop/zipped. In which case you should of used

```

mv ./* ~/downloads/

```

---

