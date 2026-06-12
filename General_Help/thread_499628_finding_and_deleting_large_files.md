---
title: "finding and deleting large files"
date: 2007-07-12
forum: General Help
---

### Post by pan69 on 2007-07-12
Hi guys,


I have a problem with a machine thats almost out of disk space. I know there are some large files somewhere but I'm not sure where they are stored. Is there a (Bash) command I can use to select files above a certain size?

Thanks!

---

### Post by KyleBrandt on 2007-07-12
See this: [http://snippets.dzone.com/posts/show/1491]("http://snippets.dzone.com/posts/show/1491")

Or, if you are feeling lazy, this is what it says:

find / -type f -size +20000k -exec ls -lh {} \; | awk '{ print $9 ": " $5 }' 

To find files over 20 Megs

---

### Post by pan69 on 2007-07-13
Awesome. Thanks a lot!

---

### Post by aysiu on 2007-07-13
Try Filelight. It's in the repositories.

---

### Post by rillip on 2007-07-13
personally enjoy KDirStat (using KDE myself, but it works for anyone, just not as efficient)

edit: also in the repos

---

