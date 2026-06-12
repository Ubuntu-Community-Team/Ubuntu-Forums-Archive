---
title: "&amp;&amp; vs ; in terminal"
date: 2006-10-07
forum: General Help
---

### Post by GStubbs43 on 2006-10-07
This is just out of curiosity... what is the difference, if anything, between these? For example, when doing a update and upgrade, which is better?

```
sudo aptitude update && sudo aptitude upgrade
``` or
```
sudo aptitude update ; sudo aptitude upgrade
``` or
```
sudo aptitude update
``````
sudo aptitude upgrade
``` ?

---

### Post by skymt on 2006-10-07
"a ; b" means do a, then do b.

"a && b" means do a, and if a has no errors, do b.

---

### Post by GStubbs43 on 2006-10-07
oooh... so && is usually better to do.

---

### Post by taurus on 2006-10-07
> **GStubbs43 said:**
> oooh... so && is usually better to do.

Yes, especially if you need to install something from source...

```

./configure && make && sudo checkinstall

```

---

### Post by Ayman on 2006-10-07
There is also:
```
a || b
```

Which means: Do a, if it fails, do b.

---

