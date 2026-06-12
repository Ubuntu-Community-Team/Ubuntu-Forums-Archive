---
title: "Sudoers.d works on two boxes but not on a third one"
date: 2013-05-02
forum: General Help
---

### Post by aemadrid on 2013-05-02
I have setup 3 quantal machines exactly the same way and got sudo working for one user just fine by editing /etc/sudoers.d/my_user so my_user could run some commans without asking for a password:

my_user ALL = (ALL) ALL
my_user ALL = NOPASSWD: /sbin/some_command, /usr/bin/another_command

But for some reason one of the boxes started asking for a password for those commands. 

I have tried copying the code to /etc/sudoers but it didn't work either.

What can I do to fix this? Have you seen this happening before?

---

