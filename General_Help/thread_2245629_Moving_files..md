---
title: "Moving files."
date: 2014-09-25
forum: General Help
---

### Post by redzero36 on 2014-09-25
Anyone know how I can move two txt files with with one command? I'm try not to use a wildcard "*.txt" because it will move the rest of the txt files.

---

### Post by EngieOP on 2014-09-25
This:
```
 mv -t DEST file1 file2
```




From man mv:

       > mv [OPTION]... [-T] SOURCE DEST
       mv [OPTION]... SOURCE... DIRECTORY
       mv [OPTION]... -t DIRECTORY SOURCE...

---

### Post by redzero36 on 2014-09-25
ohh cool thanks. I didn't think of using a option I'm very new to linux. I had thought it was a different command from mv because in the book I'm reading( Practical guide to linux commands) doesn't mention that. I probably should start reading the manual pages from now on. Thanks.

---

### Post by vasa1 on 2014-09-25
@redzero36, You can now mark the thread solved following the instructions here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by EngieOP on 2014-09-25
> **redzero36 said:**
> ohh cool thanks. I didn't think of using a option I'm very new to linux. I had thought it was a different command from mv because in the book I'm reading( Practical guide to linux commands) doesn't mention that. I probably should start reading the manual pages from now on. Thanks.

No problem. :)
*Man is important, Google comes second*

---

