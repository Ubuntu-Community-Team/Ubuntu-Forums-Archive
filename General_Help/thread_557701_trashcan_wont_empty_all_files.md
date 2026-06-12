---
title: "trashcan wont empty all files"
date: 2007-09-23
forum: General Help
---

### Post by swiftor on 2007-09-23
i have files in the trashcan when in nautilis when i use go->trash but if i navigate to home/usr/.trash its empty. in the terminal i have tryed sudo rm -rf ~/.Trash/* but the files remain. any ideas?

---

### Post by por100pre1 on 2007-09-23
First, to delete your whole .Trash folder is not a good idea. Second, try this:

```
gksudo nautilus
```

and browse /root/.Trash to see if theres anything there. Press Ctrl+H to see hidden files.

Sorry for the delay.

---

