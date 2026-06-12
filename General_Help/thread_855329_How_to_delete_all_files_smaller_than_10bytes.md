---
title: "How to delete all files smaller than 10bytes?"
date: 2008-07-10
forum: General Help
---

### Post by primky on 2008-07-10
I want to delete all files smaller than 10bytes in specific directory. How can I accomplish that?

---

### Post by primky on 2008-07-10
Isn't there an option with grep to find all files smaller than 10bytes or something?

---

### Post by sisco311 on 2008-07-10
You can use the find command:
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

to move the files in trash(Hardy):
```
find /path/to/dir -type f -size -10c -exec mv {} $HOME/.local/share/Trash/files \;
```

---

