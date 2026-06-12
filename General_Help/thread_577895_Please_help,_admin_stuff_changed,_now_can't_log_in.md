---
title: "Please help, admin stuff changed, now can't log in"
date: 2007-10-16
forum: General Help
---

### Post by jhollett66 on 2007-10-16
I was changing some things under administration > users and groups (or something like that) and I changed the name of my user folder.(in advanced).  When I tried to bring up places > home folder it wouldn't work. I restarted and now I cannot log in.  It looks for my home directory but cannot find it, i can only log in a failsafe terminal.  How do I undo this dumbass mistake?  Any help is appreciated.

---

### Post by bodhi.zazen on 2007-10-16
In failsafe mode

mv /home/<new_name> /home/<old_name>

telinit 2

---

### Post by jhollett66 on 2007-10-16
Thanks for the help.  I didn't get back to this thread in time to read your post.

I got an idea from another thread, I fixed the prob by going into the failsafe terminal and editing /etc/passwd, changing /home/<new name> back to <old name>

Appreciate the help though

---

