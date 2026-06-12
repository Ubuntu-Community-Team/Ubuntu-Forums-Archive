---
title: "library problem"
date: 2014-06-05
forum: General Help
---

### Post by auryn2 on 2014-06-05
Hi, 

When I try to run a code shows this problem:

/usr/bin/ld: cannot find -llrt
collect2: ld returned 1 exit status

I've been this problem before  and solved modifying the library:

    sudo ln -s /usr/lib/liblapack.so.3gf  /usr/lib/liblapack.so


The poblem is any lrt libray is in the library...

Thanks,

---

### Post by bapoumba on 2014-06-05
Could you please give some context ? Which program/package is this about ?

---

