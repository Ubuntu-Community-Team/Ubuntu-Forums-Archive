---
title: "Can not parse config file '/etc/avg.conf'"
date: 2007-12-02
forum: General Help
---

### Post by cccc on 2007-12-02
hi

I have installed AVG 7.5 from:

[http://free.grisoft.com/doc/5390/us/frt/0?prd=afl](http://free.grisoft.com/doc/5390/us/frt/0?prd=afl)

under gutsy, but cannot update signatures due to the following error:```

Update process failed.
Reason: Can not parse config file '/etc/avg.conf'.
```

I cannot find **avg.conf** in /etc or in /opt/grisoft/avg7/etc:```


# find / -type f -name avg.conf
#

# ls -la /opt/grisoft/avg7/etc
razem 20
drwxrwxr-x  4 avg avg 4096 2007-12-03 03:24 .
drwxrwxr-x 10 avg avg 4096 2007-12-03 03:24 ..
drwxrwxr-x  2 avg avg 4096 2007-12-03 03:24 antispam
drwxrwxr-x  2 avg avg 4096 2007-12-03 03:24 init.d
-rw-r--r--  1 avg avg  250 2006-10-04 17:05 notify.eml

```

knows someone howto get avg.conf ?

---

### Post by cccc on 2007-12-03
could someone post me pls avg.conf from AVG 7.5 ?

---

### Post by cccc on 2007-12-03
this problem is solved now !

remove complete avg inclusive config files using synaptic manager, download and install it again.

---

