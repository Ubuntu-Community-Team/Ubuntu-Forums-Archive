---
title: "Share GnuCash between two installations?"
date: 2014-01-19
forum: General Help
---

### Post by pme 72 on 2014-01-19
Is it possible to share one instance of GnuCash from two different hard drives? There are two hard drives in my desktop with Ubuntu 13.10 & XP on one and Xubuntu 12.04 and a storage partition on another. Ubuntu is my main work place and has GnuCash. Can I load GnuCash on Xubuntu and share the database and have the same functionality from both distributions without having to update each instance separately? If so would I need to download and install the identical version on both?

---

### Post by ian-weisser on 2014-01-19
You won't easily get identical versions for 13.10 and 12.04.
```
$ rmadison -u ubuntu gnucash
 gnucash | 1:2.4.10-1        | precise/universe | source, amd64, armel, armhf, i386, powerpc
 gnucash | 1:2.4.13-1ubuntu1 | saucy/universe   | source, amd64, armhf, i386, powerpc

```

Can you share a single data file between the 12.04 and 13.10 versions of GnuCash?
Yes, but it's not recommended. Backup frequently. Risk of data corruption.

---

### Post by pme 72 on 2014-01-20
Thank you ian-weisser, that is what I needed to know.

---

