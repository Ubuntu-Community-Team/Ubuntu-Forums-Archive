---
title: "Killing defunct daemons/apps"
date: 2007-06-04
forum: General Help
---

### Post by x1a4 on 2007-06-04
Hi,

How do I kill defunct daemons/apps?  As root I already tried 

kill -STOP <pid>
kill -TERM <pid>
kill -KILL <pid>
kill -ABRT <pid>
kill -QUIT <pid>

using both the shell's built-in and /bin/kill

Thank you.

---

### Post by croto on 2007-06-05
Hi,

AFAIK there is no way of killing defunct processes (zombies). They're just processes that finished running and they're waiting for the parent to kill them. Something you can try is killing the parent. But zombie processes don't hurt, so you can safely let them be there.

I might be wrong though...

---

