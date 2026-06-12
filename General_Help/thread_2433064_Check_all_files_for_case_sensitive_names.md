---
title: "Check all files for case sensitive names"
date: 2019-12-13
forum: General Help
---

### Post by petrokh on 2019-12-13
Hi everybody.
I want to run a sync between two linux computers via one drive. 
Since onedrive filenames are not case sensitive I want to run a check if between my thousands of files there are any witch will conflict between themselves. Is there any way to do it?
Thank you.
Petro.

---

### Post by Holger_Gehrke on 2019-12-13
This will find all files with the same name except for case, no matter in what directory they are:
```

find ~ -type f -printf '%p\t%f\n'|sort -k2 --field-separator='PUT A LITERAL TAB HERE' -f|uniq -D -i -f1|cut -f 1

```
How this works: it finds all files in your home directory and its subdirectories and prints the names once complete with path and once without. Then it sorts in a case insensitive way by the second field (name without path) using a tabulator as field separator (to enter a tabulator on the command line you need to hit ctrl-v (next key **v**erbatim) followed by the tab). Then it throws out all lines where the second field isn't repeated in the next or previous line again using a case insensitive comparison. Finally it cuts off the second field (name without path) for readability.

If you're only interested in cases where the name is the same except for case inside the same directory it actually becomes simpler:
```

find ~ -type f -printf '%p\n'|sort -f|uniq -D -i

```

Holger

---

