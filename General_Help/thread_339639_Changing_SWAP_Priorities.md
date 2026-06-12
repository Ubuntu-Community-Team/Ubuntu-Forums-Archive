---
title: "Changing SWAP Priorities"
date: 2007-01-16
forum: General Help
---

### Post by golem3 on 2007-01-16
I now know how to make swaps, turn them off/on, etc...but how do I change the SWAP priorities? For example, I have an old USB stick I want to use first, but it's second priority when I 

$ cat /proc/swaps

I get 

Filename                                Type              Size       Used    Priority
/dev/hda5                               partition       3984080 7648    -1
/dev/sdc1                               partition       507736   0         -2

NOW, I am assuming that -1 means 1 and -2 means 2, for the priorities...is that right? And BTW, the sdc1 is my USB stick. 

Thanks in Advance.

---

### Post by kidders on 2007-01-16
Hi there,

You can set swap filesystem priorities in /etc/fstab with something like **/dev/sdc1 none swap sw,pri=0 0 0**

Incidentally...> I am assuming that -1 means 1Priority -1 means priority -1.

---

### Post by golem3 on 2007-01-17
Thanks for the help.

---

### Post by kidders on 2007-01-17
No problem. :-)

---

