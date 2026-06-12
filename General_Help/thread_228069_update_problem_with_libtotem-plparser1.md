---
title: "update problem with libtotem-plparser1"
date: 2006-08-02
forum: General Help
---

### Post by TheRingmaster on 2006-08-02
adept sayed this could be updated but it is giving me an error that says "There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."

is there anyone else with this problem?

---

### Post by thekidder on 2006-08-02
I was having the problem. I went into sources.list and changed ```
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main
``` to ```
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main
```

Not sure if this is the best way to fix it, but it worked for me.

---

