---
title: "Please can somebody help me kill a print job?"
date: 2007-04-08
forum: General Help
---

### Post by dryder on 2007-04-08
Hi,

Please can somebody help me kill a print job which won't print or delete and is therefore stopping me deleting the Printer I have setup? It reappears every time I reboot, too.

It does not show in print manager - but the pm icon sits in the status bar because of it. Also, Printers shows the printer has "Printing 1 jobs" underneath it and I need to delete the printer.

Many thanks,
David

---

### Post by quux on 2007-04-08
Hi, 

Try pointing your browser to 

[INDENT][http://localhost:631/jobs](http://localhost:631/jobs)[/INDENT]

and cancel the pending job there. 

HTH

---

### Post by dryder on 2007-04-08
Many thanks quux.

So simple - is this real "in depth" linux/ubuntu? I read a great deal but never found this.

I have copied it to my 'little tricks' book. :-)

david

---

### Post by 11hjpphty76lkjj on 2007-04-09
If you prefer the command line:

```
lpq -a
```

then

```
lprm <jobid>
```

A

---

