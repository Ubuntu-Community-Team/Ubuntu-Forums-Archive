---
title: "Kernel assertion failure"
date: 2007-03-15
forum: General Help
---

### Post by PerH on 2007-03-15
Hi!

Today Edgy (kernel: 2.6.17-11-generic) stopped responding and I was unable to issue any commands to it, (though I could switch virtual terminal with <Control><Alt>F1-F7).
I was working with OpenOffice over AFS when it happened. After a hard reboot my syslog said something like this:

```

...
Mar 15 08:48:52 pers kernel: [17186438.036000] afs: file server 130.237.227.136 in cell nada.kth.se is back up (multi-homed address; other same-host interfaces may still be down)
Mar 15 08:51:48 pers kernel: [17186614.516000] Assertion failure in journal_start() at fs/jbd/transaction.c:270: "handle->h_transaction->t_journal == journal"
Mar 15 08:51:48 pers kernel: [17186614.516000] ------------[ cut here ]------------
Mar 15 08:51:48 pers kernel: [17186614.516000] kernel BUG at fs/jbd/transaction.c:270!
...

```

I'm attaching the rest of the relevant part of the log. This seems to be some kind of kernel error. Should I report this to someone? If so how do I do it?

// Per Hermansson

---

