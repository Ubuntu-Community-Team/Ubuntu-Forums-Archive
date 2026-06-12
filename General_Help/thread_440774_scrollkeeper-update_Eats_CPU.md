---
title: "scrollkeeper-update Eats CPU"
date: 2007-05-11
forum: General Help
---

### Post by kadath on 2007-05-11
A process called "scrollkeeper-update" often pops up and grinds my system to a halt when installing/uninstalling apps and updates. I ran a search on the forum about this, but little came up. What's the deal with this?

I'm running Feisty on a Dell Inspiron 5100 with a 2.8GHz Pentium 4 and 768 MB RAM. I also had this issue with Edgy.

---

### Post by kadath on 2007-05-12
So no one else has this problem?

---

### Post by cecil_T on 2008-02-23
I just ran into the same issue with Gutsy on a Dell 5150 3GHz P4 w/ 1GB RAM.  I just finished an update and this process is pinning my CPU now for about 10 minutes and counting.  Though this is the first time I've noticed it across multiple machines.

There does seem to be a related bug:
[https://bugs.launchpad.net/ubuntu/+source/scrollkeeper/+bug/44535](https://bugs.launchpad.net/ubuntu/+source/scrollkeeper/+bug/44535)

---

### Post by john280z on 2008-03-08
I just applied the fix in Bug #44535, works great. No more wasted cpu cycles!

johnm

---

