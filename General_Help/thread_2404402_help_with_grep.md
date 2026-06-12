---
title: "help with grep"
date: 2018-10-23
forum: General Help
---

### Post by fredwntr1 on 2018-10-23
Hello i am wondering how to output just number when i use grep with the sensors command.

```
fred@fred-pc:~$ sensors | grep Tdie

Tdie:         +29.2°C  (high = +70.0°C)



```

Tdie is my cpu temp and i am wondering how to just display the current temp and nothing else. thanks in advance.

---

### Post by fredwntr1 on 2018-10-23
```
fred@fred-pc:~$ sensors | grep Tdie | cut -c 16-19
28.4
 
```

and for list cores

```
fred@fred-pc:~$ nproc
12

```

solved my self

---

