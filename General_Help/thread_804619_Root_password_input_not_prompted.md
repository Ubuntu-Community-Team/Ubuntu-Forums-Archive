---
title: "Root password input not prompted"
date: 2008-05-23
forum: General Help
---

### Post by ilano on 2008-05-23
Hi all,

I upgraded to the latest ubuntu 8.04.

Till some time it used to work correctly with respect to prompting for "root" password whenever I try to do some privileged task - e.g. upgrade manager, add-remove programs. But now it does not and the upgrade manager and add/remove simply hang.

What could be the problem here?

~ilano

---

### Post by bodhi.zazen on 2008-05-23
You can look at this thread :

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

In addition to those considerations, you also can have porblems if you change your hostname.

Check the contents of /etc/hostname and /etc/hosts

---

### Post by ilano on 2008-05-26
okay, it was due to my changing the hostname.

but is this an expected behavior?

how do I change the hostname then?

---

