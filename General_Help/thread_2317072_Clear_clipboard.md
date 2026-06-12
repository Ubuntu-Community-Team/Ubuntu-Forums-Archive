---
title: "Clear clipboard"
date: 2016-03-13
forum: General Help
---

### Post by SamInside on 2016-03-13
Is there a command to clear the clipboard in Xfce?

---

### Post by howefield on 2016-03-13
Install xsel and..

```
xsel -bc
```

---

### Post by zvppifhqp on 2016-03-13
xsel  -bc works
* does not clear the short hand highlight -> middle click copy/paste trick (i love that trick so much it annoys me ever time i use windows)

---

### Post by vasa1 on 2016-03-13
Do you have *xfce4-clipman* installed?

---

### Post by SamInside on 2016-03-13
```
xsel -bc
``` does work, thanks!  > **zvppifhqp said:**
> * does not clear the short hand highlight -> middle click copy/paste trick It actually does! I had a look at the manual and you just have to leave out the "b": ```
xsel -c
``` This will clear the so called *primary selection*.

> **vasa1 said:**
> Do you have *xfce4-clipman* installed? No. xsel worked fine. I guess you can use either one or the other?

---

### Post by vasa1 on 2016-03-13
> **SamInside said:**
> No. xsel worked fine. I guess you can use either one or the other?
In that case, you can mark the thread [SOLVED] as described here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


I don't use Xubuntu and I don't know if *xfce4-clipman* is installed by default.

---

### Post by SamInside on 2016-03-13
> I don't use Xubuntu and I don't know if *xfce4-clipman* is installed by default. It isn't.

---

