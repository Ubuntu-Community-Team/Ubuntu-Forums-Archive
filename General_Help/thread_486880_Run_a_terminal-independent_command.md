---
title: "Run a terminal-independent command"
date: 2007-06-28
forum: General Help
---

### Post by JMO707 on 2007-06-28
Hi there.

I recently found the utility of adding an "&" at the end of a command. The thing is that I thought that if some daemon or program were running, they will not depend on that terminal (if I close it, the running thing closes too)

Is there any way to make that?

---

### Post by aJayRoo on 2007-06-28
I think that depends on the specific program (some one correct me if I am wrong). However you can run many commands independently of a terminal by pressing alt-F2 and entering the command in the box that appears. Hope that helps.

---

### Post by stylishpants on 2007-06-28
Just run "disown".  This detaches the last created background job from the terminal.

Type "help disown" for more info.

---

### Post by JMO707 on 2007-06-28
Woha!, thanks!

"Disown" is just what I was looking for =D

---

### Post by bodhi.zazen on 2007-06-29
You might also like screen

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

[http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html](http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html)

[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

---

