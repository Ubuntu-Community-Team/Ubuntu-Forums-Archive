---
title: "replacement"
date: 2006-09-01
forum: General Help
---

### Post by Sasuke on 2006-09-01
my sister *noob* deleted my /dev/null so now i need to get it replace, does anyone know how to?

---

### Post by ayoli on 2006-09-01
you may try:

```
sudo mknod -m 666 /dev/null c 1 3 
```
and then,
```
sudo chown root:mem /dev/null
```

more info in:
```
man null
```

regards.

---

### Post by Ramses de Norre on 2006-09-01
Don't give your sister root priviliges when she does things like that ;)

---

