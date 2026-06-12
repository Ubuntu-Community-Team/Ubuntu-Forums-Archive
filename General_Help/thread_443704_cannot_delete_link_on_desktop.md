---
title: "cannot delete link on desktop"
date: 2007-05-14
forum: General Help
---

### Post by leashy on 2007-05-14
I have a couple links that I created on my desktop that cannot be removed. The links are to folders on a separate hard drive. I created them by right clicking on the folder in nautilus and clicking "make link". I then copied the link onto the desktop. Now whenever i try to remove the links it says "Error "Not on the same file system". I tried to deleted it from the root and nothing happens. Its almost like it thinks I'm asking it to delete the folder itself. Anyone have an idea of what to do?

---

### Post by taurus on 2007-05-14
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by leashy on 2007-05-14
Found the answer to my question. This worked:

I went to terminal and did: 

rm filename

---

### Post by craig.brisbane on 2007-10-16
I did the same as above in creating a link. The output of  "ls -la" is  

lrwxrwxrwx 1 craig craig        22 2007-10-15 23:28 Link to Graphics 

What do I do to remove the link

---

### Post by gsoundsgood on 2007-11-27
from a terminal

```

cd Desktop
rm Link to Graphics

```

easy. but shouldn't need to be done from terminal

---

### Post by taurus on 2007-11-27
> **gsoundsgood said:**
> from a terminal

```

cd Desktop
rm Link to Graphics

```

easy. but shouldn't need to be done from terminal

Your second command won't work since there is no such thing as Link.  You need to use

```
rm "Link to Graphics"
-or-
rm Link\ to\ Graphics
```

---

