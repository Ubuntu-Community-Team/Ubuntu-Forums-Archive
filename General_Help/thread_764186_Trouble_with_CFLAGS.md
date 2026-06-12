---
title: "Trouble with CFLAGS"
date: 2008-04-23
forum: General Help
---

### Post by paul.schorfheide on 2008-04-23
I'm trying to use set my CFLAGS to "-g -Wall -pedantic", so I added the following to .bashrc
```

export CFLAGS="-g -Wall -pedantic
export CXXFLAGS="${CFLAGS}"

```
When I run gcc, it doesn't use the flags unless I manually type in gcc $CFLAGS sample.c

Any ideas?

---

