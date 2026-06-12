---
title: "Permission denied ... installing 915 resolution"
date: 2007-08-18
forum: General Help
---

### Post by minulescu on 2007-08-18
user@user-laptop:~/Desktop/915resolution-0.5.3$ **make install**
cp 915resolution /usr/sbin
cp: cannot create regular file `/usr/sbin/915resolution': Permission denied
make: *** [install] Error 1

Although I am switched to root.

What the hell?

---

### Post by ajgreeny on 2007-08-18
Switched to root?  You need to put **sudo** in front of the command and it should then work.
sudo cp 915resolution /usr/sbin
There is no root account in ubuntu by default, so I'm a bit confused by your meaning of "switched to root".
Have a good looi at:-
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

