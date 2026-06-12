---
title: "how tto add user to group without GUI"
date: 2008-01-09
forum: General Help
---

### Post by gnychis on 2008-01-09
Hi all,

I am trying to add users to groups without a GUI, because I am SSHing in to the machine.  I edited /etc/group and rebooted the machine and the groups are still not in effect.  Is there something I am missing?

Thanks!
George

---

### Post by geirha on 2008-01-09
editing /etc/group should work, though the file is very picky on the syntax, if you add a space in the wrong place it won't work. The easiest way to add a user to a group in CLI (on ubuntu) is ```
sudo adduser *username* *group*
```

---

### Post by keelerm on 2008-01-09
As root
```
usermod -G <group ids here> <user name here>
```

---

