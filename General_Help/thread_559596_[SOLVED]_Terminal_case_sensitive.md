---
title: "[SOLVED] Terminal case sensitive"
date: 2007-09-25
forum: General Help
---

### Post by Kenchu on 2007-09-25
Just wondering if it's possible to remove the case sensitive feature when it comes to navigating with cd? For me to be able to write a letter + tab, the first letter has to be capital (if the folders name is starting with capital letter). I wanna be able to write lowercase.

---

### Post by jamvegan on 2007-09-25
Create or edit the file ~/.inputrc and add the line:
```
set completion-ignore-case on
```

You'll need to close and reopen the terminal for this to take effect.

---

### Post by Kenchu on 2007-09-25
Great, it works. Thanks.

---

