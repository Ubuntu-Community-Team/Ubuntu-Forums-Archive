---
title: "ubuntu 32 or 64?"
date: 2008-06-16
forum: General Help
---

### Post by galil77 on 2008-06-16
what is the quickest way to find out if an existing installation of ubuntu is 32 or 64 bit?
Thanks.

---

### Post by sdennie on 2008-06-16
Just type:

```

uname -m

```

If it is not i686 then it should be 64bit.

---

### Post by geirha on 2008-06-16
You could also check what arch a binary is compiled for. i.e.
```
file /bin/bash
```
It should say either "32-bit" or "64-bit" in the third field.
```
file /bin/bash | cut -d' ' -f3
```

---

