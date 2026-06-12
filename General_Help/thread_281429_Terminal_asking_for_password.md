---
title: "Terminal asking for password"
date: 2006-10-21
forum: General Help
---

### Post by boris357 on 2006-10-21
When I get to the terminal program and type "su" at the prompt it ask me for a pasword. I was not asked to input a root user password when installing Ubuntu. Is this an error in the program? abug? I don't know but I hope some one has an answer or I will have to install another version of LINUX.Is there a program that will read passwords in linux? If so, where do I get one?

Thank you.

---

### Post by aysiu on 2006-10-21
You don't type *su*.

You use *sudo* instead.

**su** (becoming root and using the root password): ```
su
password:
aptitude update
aptitude install tagtool
exit
exit
``` **sudo** (temporarily assuming root privileges using your user password since you belong to the admin group): ```
sudo aptitude update
password:
sudo aptitude install tagtool
exit
``` For more info, go here:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

