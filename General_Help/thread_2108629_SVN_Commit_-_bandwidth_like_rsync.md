---
title: "SVN Commit - bandwidth like rsync?"
date: 2013-01-25
forum: General Help
---

### Post by sdpagent on 2013-01-25
Hello all,
Apologies if my title is a bit vague, but I would like to know whether SVN sends the 'full' file when it has been changed a tiny bit, or whether it just sends what has 'changed' like rsync does. I realize that it will only send the files that have changed but this is about whether it has to send the entire file again, or if it can be 'clever' and just notify the repo of the changes over the network?

Stu

---

### Post by omeomi on 2013-01-25
SVN only works with full files AFAIK, so no that is not possible.

---

