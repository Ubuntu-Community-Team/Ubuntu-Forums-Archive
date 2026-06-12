---
title: "error installing gv-3.7.4"
date: 2019-03-15
forum: General Help
---

### Post by toolman1 on 2019-03-15
I get this error...

yada, yadao, yada

```
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c gv '/usr/local/bin'
/usr/bin/install: cannot create regular file '/usr/local/bin/gv': Permission denied
Makefile:706: recipe for target 'install-binPROGRAMS' failed
make[3]: *** [install-binPROGRAMS] Error 1
make[3]: Leaving directory '/home/toolman/Downloads/gv-3.7.4/src'
Makefile:982: recipe for target 'install-am' failed
make[2]: *** [install-am] Error 2
make[2]: Leaving directory '/home/toolman/Downloads/gv-3.7.4/src'
Makefile:976: recipe for target 'install' failed
make[1]: *** [install] Error 2
make[1]: Leaving directory '/home/toolman/Downloads/gv-3.7.4/src'
Makefile:616: recipe for target 'install-recursive' failed
make: *** [install-recursive] Error 1
```

---

### Post by Impavidus on 2019-03-15
You cannot put anything in /usr/local/bin because you need root permissions for that. You can try it with sudo.

But why would you install gv 3.7.4 from source? It's in the repositories.

---

### Post by toolman1 on 2019-03-15
I'm brand new to Linux. I did find it in a repository and installed it. Thanks for your help.

---

