---
title: "shell script help"
date: 2008-03-06
forum: General Help
---

### Post by I.You on 2008-03-06
Hi

In order to change a value of a varible in other file,
is it NG?

e.g.
in File1

```
varible=false
```


in File2

```
#!/bin/sh

. File1

varible=true
echo $varible
```


I want to change the varible in File2 to true.
Any help?

---

### Post by syxbit on 2008-03-06
the easier way i can think of is to use 'sed'
it's a find and replace program

---

