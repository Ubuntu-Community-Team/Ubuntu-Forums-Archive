---
title: "amsn freezes on start up"
date: 2007-06-15
forum: General Help
---

### Post by Redbomber on 2007-06-15
Amsn was working great until I extracted some plugins to /usr/share/amsn/plugins as I read in another post.  Now on start-up, I get an update plugin window that I cannot select close or install.  I removed the plugins from the folder, still freezes (now the plugins I put into the folder don't appear).  Then uninstalled with aptitude remove then reinstalled - same deal.  Then I performed complete removal inc. preferences with Synaptic and then reboot then reinstall - same thing.  Can I remove all traces of Amsn completely and start again somehow?

---

### Post by loathsome on 2007-06-15
You could try compiling it yourself - as a bonus, you'll also get a nice-looking aMSN with anti-aliasing! :KS

» [http://ubuntu.loathsome.us/doc/compile-amsn](http://ubuntu.loathsome.us/doc/compile-amsn)

---

### Post by Redbomber on 2007-06-15
Thanks.  I'm trying that.  But ./configure (about halfway down the page) command not found when run in terminal

---

### Post by loathsome on 2007-06-15
What are you trying to configure?

---

### Post by Redbomber on 2007-06-15
I'm following the guide.

sudo ./configure --prefix=/usr/local/tcltk


Apparently this tells script  to install TCL 8.5 into /usr/local/tcltk

---

### Post by Redbomber on 2007-06-15
Ignore that.  It was I got it.  I'm not in the correct directory.  That's what happens a 1am.  So I run

```
sudo ./configure --prefix=/usr/local/tcltk
```

in the /unix directory and that seem to work fine.  When I do sudo make, it says no make file found.

---

### Post by loathsome on 2007-06-15
Hm, that shouldn't happen.

You sure you're in the right directory? (unix) .. again? :p

---

### Post by loathsome on 2007-06-16
Also note that the configure script for OpenSSL is called «config», not «configure»

---

