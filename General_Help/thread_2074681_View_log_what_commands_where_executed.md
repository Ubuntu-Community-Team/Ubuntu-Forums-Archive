---
title: "View log what commands where executed?"
date: 2012-10-22
forum: General Help
---

### Post by PrinzLangweilig on 2012-10-22
Hi,

is there a log, which saves what commands where executed in the shell e.g. via ssh?

---

### Post by whatthefunk on 2012-10-22
Yeah, history.
Go to a terminal and simply type "history"  If you want to make it easier to read:
```
history | less
```

If you want to search for something (example "banana")
```
 history | grep banana
```

---

### Post by PrinzLangweilig on 2012-10-22
in which file is it stored? and how can i configure it?

---

### Post by Lars Noodén on 2012-10-22
Another way to work with the history is to use the file ~/.bash_history, it is where history gets its data from.

---

### Post by whatthefunk on 2012-10-22
> **PrinzLangweilig said:**
> in which file is it stored? and how can i configure it?

What exactly do you want to configure?

---

### Post by PrinzLangweilig on 2012-10-22
Solved, just wanted to know how i can set nr of commands.

---

