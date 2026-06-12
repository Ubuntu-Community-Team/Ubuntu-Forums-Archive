---
title: "how to list only configuration files ?"
date: 2008-07-02
forum: General Help
---

### Post by news75 on 2008-07-02
Hi,
I know, with ls -a I can see every files but I would like see only
configuration files (files that begin with dot) how to do ?
I can't find an option in man ls... the only way is with grep ?

  thanks for helps
  
      news75

---

### Post by jpeddicord on 2008-07-02
Not a tutorial, so moved to General Help.

---

### Post by brian_p on 2008-07-02
> **news75 said:**
> Hi,
I know, with ls -a I can see every files but I would like see only
configuration files (files that begin with dot) how to do ?
I can't find an option in man ls... the only way is with grep ?

Is

```
ls -dl .*
```

of any use?

---

### Post by news75 on 2008-07-04
wow, great, exactly what I was looking for! thankyou very much

---

