---
title: "tcl dict package"
date: 2007-10-30
forum: General Help
---

### Post by pedrotuga on 2007-10-30
After i updated to fiesty i haven't ben able to use a very handy application called **tksqlite**
i need the **tcl dict module**.

Here's the trace so you can see exactly what i am missing.

```
$ ./tksqlite.tcl
Error in startup script: can't find package dict
    while executing
"package require dict"
    invoked from within
"if {[info tclversion] < 8.5} {
package require dict
}"
    (file "./tksqlite.tcl" line 123)
```

When can i get this package? In which deb package does it comes?

---

