---
title: "Files stuck in trash"
date: 2008-05-01
forum: General Help
---

### Post by insane_alien on 2008-05-01
Now, i have encountered this problem before on previous versions of ubuntu. What i did to solve it then was to open a root version of nautilus and obliterate the .trash folder.

well, i tried that but i can't ind the .trash folder to obliterate it. :redface: can anyone tell me either where it has moved to or how to get rid of a file you don't have permissions for(even though it IS my file).

---

### Post by soxs on 2008-05-01
Trash is no located @ ```
/home/YOURUSERNAME/.local/share/Trash/
```
To clean it up: ```
sudo rm -vf /home/YOURUSERNAME/.local/share/Trash/*
``` Which will simply remove any .info or anything that is located in your usertrash. Has worked for me any(?)/everytime.

---

### Post by insane_alien on 2008-05-02
cheers man. would have took me forever to find on my own.

---

