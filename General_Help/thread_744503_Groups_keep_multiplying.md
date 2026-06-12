---
title: "Groups keep multiplying"
date: 2008-04-03
forum: General Help
---

### Post by zoopzoop on 2008-04-03
My groups list (System > Administration > Users and Groups > Manage Groups) is behaving quite peculiar. When I go in the first time, everything is okay. Then, when I click on a random group, Properties and OK, without changing anything, my group list doubled! I have exactly the same list, but twice.

Example:

My group list:

root
deamon
bin
sys
...
gdm
slocate
mysql
subversion

I click on subversion, Properties and OK, and my group list is:


root
deamon
bin
sys
...
gdm
slocate
mysql
[ subversion ]
root
deamon
bin
sys
...
gdm
slocate
mysql
subversion

The cursor is still on the group subversion but the list has doubled.

Does anyone have any idea what's going on?

---

### Post by Oldsoldier2003 on 2008-04-04
> **zoopzoop said:**
> My groups list (System > Administration > Users and Groups > Manage Groups) is behaving quite peculiar. When I go in the first time, everything is okay. Then, when I click on a random group, Properties and OK, without changing anything, my group list doubled! I have exactly the same list, but twice.

Example:

My group list:

root
deamon
bin
sys
...
gdm
slocate
mysql
subversion

I click on subversion, Properties and OK, and my group list is:


root
deamon
bin
sys
...
gdm
slocate
mysql
[ subversion ]
root
deamon
bin
sys
...
gdm
slocate
mysql
subversion

The cursor is still on the group subversion but the list has doubled.

Does anyone have any idea what's going on?

if  cat /etc/passwd shows that everything is normal I would chalk it up as a bug and do a bug report explaining how to recreate this glitch,

---

### Post by zoopzoop on 2008-04-05
Done!
[https://bugs.launchpad.net/ubuntu/+bug/212113](https://bugs.launchpad.net/ubuntu/+bug/212113)
Thanks for the tip, Oldsoldier2003!

---

