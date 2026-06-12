---
title: "Applications menu"
date: 2007-04-15
forum: General Help
---

### Post by Subban on 2007-04-15
Installed Feisty a few days ago and got just about everything sorted from my dapper install, one last thing I can't sort out.

In Dappper I had a Debian menu entry, in it was a whole heap of apps not in the default menu which made things somewhat easier at times. The trouble is I can't recall how I got it (ran Breezy changed to Dapper at release and not reinstalled since)

I thought I had to : sudo aptitude install menu
and sudo aptitude install menu-xdg

That didn't work, can anyone point me in the right direction?

---

### Post by robertwoes on 2007-04-15
did you try a :
```
$sudo update-menus -v
```
-Robert Woestman

---

### Post by Subban on 2007-04-15
That did it thank you :]

---

### Post by robertwoes on 2007-04-15
please add 'resolved' tag to your post.  I am happy you have everything working now.
Yours.
-Robert Woestman

---

