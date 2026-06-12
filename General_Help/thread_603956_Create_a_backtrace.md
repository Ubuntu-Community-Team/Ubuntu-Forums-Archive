---
title: "Create a backtrace"
date: 2007-11-05
forum: General Help
---

### Post by Irontux on 2007-11-05
Sorry for my awful english.

I don't understand how create a backtrace.

I have read this wiki:
[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)
[https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)

I must install -dbgsym package before write this string?
```
gdb <program> 2>&1 | tee gdb-<program>.txt
(gdb) handle SIG33 pass nostop noprint
(gdb) set pagination 0
(gdb) run <arguments, if any>
```

@ end, what is procedement for create a backtrace?

Thanks a lot.

---

### Post by Cochise on 2007-11-05
type run: applications name

and it´ll start the back trace

---

### Post by Irontux on 2007-11-05
Sorry, but I don't understand.

---

