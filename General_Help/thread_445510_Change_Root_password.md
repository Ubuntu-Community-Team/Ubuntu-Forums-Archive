---
title: "Change Root password?"
date: 2007-05-16
forum: General Help
---

### Post by knvb1123 on 2007-05-16
Hello.
I was setting up a Feisty Fawn machine for my younger brother.
I set up beryl and noticed that my account was only able to use it.
Too lazy, as all people are to some degree, I changed my account's name password and rights. I deleted his.

Now I'm stuck with:

Root
Keehun

Keehun is my account that I lowered previlages so that my brother wouldn't screw up the computer.

However, I din't enable the root account before I did so.

Is there a way that I could somehow revert or climb back to able to administrate?
I really don't want to reinstall Linux, yet complex beryl installation as it is right now.

Thank You,
Keehun Nam

---

### Post by aysiu on 2007-05-16
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo) will help you recover admin privileges for Keehun.

---

### Post by asipi on 2007-05-17
unfortunatelly some apps like e.g samba swat need the root account to be pw protected :( so sometimes it definetly needed...

try sudo -i, then you get root prompt, and use passwd to change the pw

---

