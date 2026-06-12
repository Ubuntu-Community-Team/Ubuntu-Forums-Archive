---
title: "bash pgup  history completion... how to enable?"
date: 2007-04-20
forum: General Help
---

### Post by thinkliberty on 2007-04-20
I just installed unbuntu to see if I would like it better than the other distros that I have used in the past.  One feature I use all the time that comes as a default function in my last distro is bash's page up and page down text completion from bash_history.

Is there an easy way to enable this in ubuntu?

---

### Post by nemarasu on 2007-04-20
just out of curiosity, would you type this in a term:

echo $SHELL 

and let me know what it says?

---

### Post by nimatar on 2007-04-25
Decomment the following lines from /etc/inputrc:
```
# alternate mappings for "page up" and "page down" to search the history
 "\e[5~": history-search-backward
 "\e[6~": history-search-forward
```

---

