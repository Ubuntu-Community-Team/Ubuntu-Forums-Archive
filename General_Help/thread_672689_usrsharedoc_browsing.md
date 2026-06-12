---
title: "/usr/share/doc browsing"
date: 2008-01-19
forum: General Help
---

### Post by mzembe on 2008-01-19
What's the best way to browse the documentation, is there some kind of 'info' or 'man' technique that can browse the gzipped docs?

---

### Post by sumguy231 on 2008-01-20
There's probably a better way, but zcat will let you read the text without extracting it first so you can just do a 'zcat changelog.gz | less' for a quick read.

---

### Post by nick_h on 2008-01-20
There is also zless.
```
zless changelog.gz
```

---

### Post by sumguy231 on 2008-01-20
Thanks, I wasn't aware of that one. It saves me a few characters over the first solution.

---

### Post by mzembe on 2008-01-21
I was hoping something like ksystemlog, or a web browser would also work, it seems like I remember browsers automatically parsing gz files that weren't tar archives.. not any more. I'm beginning to doubt that I remember correctly it's been so long. 
I dragged a changelog onto ksystemlog and my memory usage steadily climbed to nearly a gig before I killed it. :lolflag:

---

### Post by nick_h on 2008-01-21
I'm not sure what you actually want.  You can use nautilus to browse the directory structure.  Double clicking on an archive will show its contents in File Roller.  Then you can click on a file in File Roller to open it in gedit.

Firefox has similar functionality.

---

