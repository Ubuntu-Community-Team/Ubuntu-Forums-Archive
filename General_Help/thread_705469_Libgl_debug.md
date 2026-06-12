---
title: "Libgl_debug"
date: 2008-02-23
forum: General Help
---

### Post by baudday on 2008-02-23
I found another thread like this, but he ended up being sent to another forum because his was a Mac specific issue.

Anyway, I have an ATI Radeon X850 graphics card, and would really like to play WoW. I ended up getting it successfully installed, but it runs really, really slowly, to the point where you couldn't even play. So I was looking for solutions and noticed on one guide, the first step is to run
```
glxinfo | grep rendering
```
and that should give me an answer of yes if my computer is ready to run WoW. However I get this,
```
No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```
I tried doing this, 
```
export LIBGL_DEBUG=verbose
```
but that didn't work, and it's still No. I was wondering if anyone could help me on this, I'm almost certain this is the reason why the game is running so slow.

---

### Post by baudday on 2008-02-24
no one can help me?

---

### Post by pointone on 2008-02-24
When you set LIBGL_DEBUG=verbose, you'll need to examine the full output of glxinfo to find the verbose parts. If you're still grepping, it'll only give you the line with "rendering" in it.

I always recommend following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") for ATI drivers.

---

### Post by baudday on 2008-02-24
well i used that guide, and got to where you have to reboot, and now it's all messed up. the max resolution i can set it to is 800x600, and i'm using a 1280x1024 monitor. Also, it now starts in safe graphics mode every time.

---

### Post by baudday on 2008-02-24
alright, it's fixed as far as that problem goes, but the original problem still exists

---

