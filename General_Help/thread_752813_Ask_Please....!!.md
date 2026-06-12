---
title: "Ask Please....!!"
date: 2008-04-12
forum: General Help
---

### Post by D3nn13 on 2008-04-12
hai I'm newuser. I'll ask something... how to clear or delete the history in the terminal??? please answer....!!!:)

---

### Post by santiagoward2000 on 2008-04-12
What should I ask? :)

---

### Post by original_jamingrit on 2008-04-12
Close all open terminals, and then delete the file in your home directory named ".bash_history".  It's a hidden file, so you will need to press Ctrl-H in Nautilus to see it.

---

### Post by Iandefor on 2008-04-12
Run this then close any open terminal sessions:```
rm -v ~/.bash_history
```It's just stored as a file (.bash_history) in your home (~) directory.

---

### Post by prshah on 2008-04-12
> **D3nn13 said:**
> hai I'm newuser. I'll ask something... how to clear or delete the history in the terminal??? please answer....!!!:)

```
history -c
```

---

### Post by K.Mandla on 2008-04-12
Moved to General Help.

---

