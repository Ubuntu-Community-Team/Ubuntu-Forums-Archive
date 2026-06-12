---
title: "trap ctrl c ?"
date: 2007-03-20
forum: General Help
---

### Post by bruenig on 2007-03-20
Could someone explain trap. There is no man page and google searches have not been to helpful.

Maybe explain the syntax and give me an example of how you would trap ctrl+ c.

Thanks.

---

### Post by Mr. C. on 2007-03-20
> **bruenig said:**
> Could someone explain trap. There is no man page ...


Sure there is.
```
man bash | less -p 'trap.*sigspec'
```

MrC

---

### Post by bruenig on 2007-03-21
Thanks.

---

