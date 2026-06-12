---
title: "&quot;Make&quot; a C program, missing header files"
date: 2007-06-24
forum: General Help
---

### Post by Kissack on 2007-06-24
When I tried to make a progamme after some changes (and since moving it to 7.04 from a different distro) I get an error:

gcc -g -pg -O -DUNIX -DHTML -c ged2www.c
In file included from ged2www.c:4:
load.h:3:18: error: stdio.h: No such file or directory
In file included from ged2www.c:4:
load.h:5: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
load.h:6: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
etc.

It appears the 'standard' c .h files are not installed and i am not sure which package provides them

can you help?

tia

-- 
Allan

---

### Post by ebash on 2007-06-24
Try installing the package 'build-essential', it should install the header files that you need.

```
sudo apt-get install build-essential
```

---

### Post by Kissack on 2007-06-24
Brilliant.  Compiles a treat now, thanks for your quick and accurate reply

-- 
Allan

---

