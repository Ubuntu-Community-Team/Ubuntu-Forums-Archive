---
title: "Run program at startup"
date: 2007-06-05
forum: General Help
---

### Post by Ubivetz on 2007-06-05
Hi All!

I need to run xbindkeys at system startup. Actually I don't know, whether I need to run X11 before or not. I tried to put xbindkeys in ~/.profile. It works, but for one user. But I need xbindkeys working at GDM login. I tried to put xbindkeys to /etc/X11/xinit/xintirc and /etc/profile. It didn't work.

---

### Post by rax_m on 2007-06-05
[http://applications.linux.com/article.pl?sid=07/01/10/176226](http://applications.linux.com/article.pl?sid=07/01/10/176226)


not sure if this helps you.. it recommends putting it in the .bashrc file in your home directory.

---

### Post by Ubivetz on 2007-06-05
> **rax_m said:**
> [http://applications.linux.com/article.pl?sid=07/01/10/176226](http://applications.linux.com/article.pl?sid=07/01/10/176226)


not sure if this helps you.. it recommends putting it in the .bashrc file in your home directory.
~/.bashrc is not my way - I need xbindkeys for **all users**.

---

