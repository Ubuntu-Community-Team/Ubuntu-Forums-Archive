---
title: "repository problem"
date: 2007-01-31
forum: General Help
---

### Post by joelk989 on 2007-01-31
E: Malformed line 35 in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory

whenever I try to update the repository I get the same problem, can't get any repository to work

any suggestions?

---

### Post by llamakc on 2007-01-31
1. make sure you do not have another process locking it: ie: a Terminal window running `apt-get` or `aptitude`, or Synaptic|Adept running.

2. cut/paste your /etc/apt/sources.list file. The error is telling you where the problem is. I'd open it in your favorite text editor and compare that line's syntax with the lines above/below it. One extraneous character will muck the process up.

---

### Post by joelk989 on 2007-01-31
Thank you, I had to manually make line 40 and 41 comments (#) and it fixed my problem.

---

