---
title: "addr2line from binutils version issue"
date: 2008-01-24
forum: General Help
---

### Post by RSBhan on 2008-01-24
Hi, all.

I have recently compiled the genome assembly program Arachne (in case anyone is familiar with this program) on my 64-bit machine.  The program requires the use of addr2line, one of the programs from binutils.

Unfortunately, I get an error message when I try to run the program saying:

```
It appears that you have an old version of addr2line.
It does not support the -i option.
Abort.
```

I'm not sure if this message is coming from the OS or from the program.  I checked the version of addr2line and found it's 2.18 and it does, in fact, support the -i option.  I have tried removing and reinstalling the binutils package to no avail.

Does anyone know why I might be getting this error and some possible solutions to try?  Thanks in advance.

---

