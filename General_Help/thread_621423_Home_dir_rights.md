---
title: "Home dir rights?"
date: 2007-11-23
forum: General Help
---

### Post by maGot on 2007-11-23
Hello!

I have changed my rights for my home dir so everyone can read it. And now I dont know how to change back to the default rights. How do I do that?

Thanks.

---

### Post by nick_h on 2007-11-23
I think the default is that everyone can read your home directory.  If you want to remove read access then you can use the following:
```
chmod -R o-r *
```

---

