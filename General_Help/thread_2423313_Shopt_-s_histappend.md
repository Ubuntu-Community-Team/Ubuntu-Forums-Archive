---
title: "Shopt -s histappend"
date: 2019-07-20
forum: General Help
---

### Post by COKEDUDE on 2019-07-20
What is the point of this? Whenever I close my shell it appends to the history file without adding this. I have never seen it overwrite my history file. 

```
# When the shell exits, append to the history file instead of overwriting it
shopt -s histappend
```

---

### Post by TheFu on 2019-07-21
open 3 shells on the same machine.
work for 2 days.
close 1, then open a new shell.  What happened to the history you needed in the other 2 shells?

---

