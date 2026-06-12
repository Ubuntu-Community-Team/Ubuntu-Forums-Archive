---
title: "fetchmail and procmail"
date: 2007-01-08
forum: General Help
---

### Post by cssutto on 2007-01-08
For some reason, my fetchmail has stopped calling procmail.

I have these lines in my .fetchmailrc:

mda 'procmail -f-'

mda "/usr/bin/procmail -d %s"   # tell fetchmail which MDA to use

Permissions on /user/bin/procmail are 755.

Is it a permission problem?

CSSJR

---

### Post by andrew.46 on 2007-07-05
Hi,

 You are calling procmail twice. Assuming a default install you only need:

```
mda "/usr/bin/procmail -d %T" 
```

comment the other 2 out (by adding # at the beginning of the line) and try again.

                        Andrew

---

