---
title: "zsh question"
date: 2008-03-09
forum: General Help
---

### Post by sorak on 2008-03-09
okay, so ive got zsh colorizing stderr, which i like a lot. the code is as follows:

```
#colorize stderr
exec 2>>(while read line; do
  print '\e[91m'${(q)line}'\e[0m' > /dev/tty; done &)
```

only problem is this makes some scripted interfaces act strange... stderr gets reported on new lines because the prompt gets written to my tty first, and when being asked questions in bash scripts, i cant see the question until i respond.

anybody know how to do this more gracefully?

---

### Post by Brunellus on 2008-03-17
I am moving this thread to a more appropriate subforum.

---

