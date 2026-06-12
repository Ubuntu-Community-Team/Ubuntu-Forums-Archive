---
title: "make - &quot;make: *** No rule to make target 'modules'.  Stop.&quot;"
date: 2023-06-10
forum: General Help
---

### Post by bobby-bouche on 2023-06-10
I was following this guide to compile brotli modules for nginx 1.24 on ubuntu 22.04

Guide:
[https://devpress.csdn.net/cicd/62ec24ec89d9027116a1043d.html](https://devpress.csdn.net/cicd/62ec24ec89d9027116a1043d.html)

when i run the make command i get this.

```
make: *** No rule to make target 'modules'.  Stop.
```

i never encountered this error before as it would work previously without issues.

What does this issue mean and how can i resolve this?

---

### Post by bobby-bouche on 2023-06-10
issue resolved.

sudo ./configure --with-compat --add-dynamic-module=../ngx_brotli
the issue was the ../ so i removed it then compiled it with make. issue resolved.

---

### Post by TheFu on 2023-06-10
Please use the Thread Tools button to mark this thread solved, so we don't waste our time.

---

