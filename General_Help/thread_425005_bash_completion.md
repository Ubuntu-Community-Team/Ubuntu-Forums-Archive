---
title: "bash completion"
date: 2007-04-27
forum: General Help
---

### Post by asubedi on 2007-04-27
Bash used to complete filenames when wildcards were used in front of some text. Forexample if I had test.txt in my folder, less *.txt<TAB> would complete the filename. However, after a clean Feisty install, this feature no longer works. It works if   I don't use any wildcards. For example, less test<TAB> would work.

Does anyone know how to get tab completion working with wildcards?

TIA

---

### Post by disposable on 2007-05-03
Just tried it on Feisty and it worked. That's cool! I didn't know you could do that. :) This was on an Edgy-to-Feisty upgrade with bash 3.2.13(1)-release and GNOME Terminal 2.18.0.

---

### Post by erdewit on 2007-07-23
Just  put these lines in $HOME/.inputrc:
```

set show-all-if-ambiguous on
set visible-stats on

```

---

