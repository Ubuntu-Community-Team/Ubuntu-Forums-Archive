---
title: "sudo stopped working for admin"
date: 2007-10-04
forum: General Help
---

### Post by brenth on 2007-10-04
Hey all, I have been messing with getting my machine connected to a ldap server, and after alot of messing with all the pam files, it is working. But the problem is, now administrator can not sudo. Everything looks correct in /etc/sudoers and /etc/groups, and a "groups administrator" returns that administrator is in the admin group. I also have root running on the box, and root is totally fine, but I am not sure why administrator is not working anymore. There is nothing in any log file at all (auth.log, messages, nothing)

Basically, when I run a sudo command sudo command as administrator it asks for my password and then goes back to the prompt, without doing anything.

Anyone have any ideas?

---

### Post by distroman on 2007-10-04
If you have not already done so then maybe have a look here.
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

