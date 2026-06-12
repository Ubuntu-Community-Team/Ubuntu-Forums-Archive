---
title: "cut option unknown"
date: 2012-12-05
forum: General Help
---

### Post by joach on 2012-12-05
I 

I'm trying to create my first LSF, and there is a command at the start of the tutorial I can't understand : 

```
echo -n "Binutils: "; ld --version | head -n1 | cut -d" " -f3-bison --version | head -n1
```

There is an option ```
f3-bison
``` I find bizare because 
if i just run 
```
test@test:~$ ld --version | head -n1
```

i get :

```
GNU ld (GNU Binutils for Ubuntu) 2.22
```

There is not any ```
bison
```

thanks

---

### Post by joach on 2012-12-05
Sorry it was two lines 
It's ok

---

