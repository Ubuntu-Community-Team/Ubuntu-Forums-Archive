---
title: "ls command"
date: 2006-10-30
forum: General Help
---

### Post by robcarr2 on 2006-10-30
Hey,

I am using ls -s -h to view file sizes but it just shows 32k for all my folders, I want to see the size of the folders contents all added up.

Anyone know how to do it?

---

### Post by skierkegaard on 2006-10-30
du -hs /path/to/directory

---

### Post by robcarr2 on 2006-10-30
Still only shows 32k next to the folders :(

---

### Post by volanin on 2006-10-30
But the command is really this:

du -hs *

It will show the size of all the folders in the current directory.
If it is still 32K, maybe your folders are empty!
(Or full of only symbolic links)

---

### Post by robcarr2 on 2006-10-30
Cheers for that :) works like a beaut

---

