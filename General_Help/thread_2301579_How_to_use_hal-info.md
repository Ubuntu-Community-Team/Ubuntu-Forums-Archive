---
title: "How to use hal-info"
date: 2015-11-03
forum: General Help
---

### Post by newcfd on 2015-11-03
I am able to install hal-info. But I can not run lshal since hal is not installed.
When I tried to install hal, it is not available, What is the purpose to have hal-info?

---

### Post by Sweet_Baby_Jamie on 2015-11-03
Hal-info only offers a summary about your hardware.  Most computers newer than a few years don't have or need hal (Hardware Abstraction Layer).

---

### Post by slickymaster on 2015-11-03
Hal is deprecated, since it has become a large monolithic unmaintainable mess, and also duplicates a lot of functionality which are nowadays provided by **udev** and the kernel itself.

---

### Post by Vladlenin5000 on 2015-11-03
As above.

Perhaps if you explain what are you trying to do...

---

### Post by newcfd on 2015-11-03
Thank you guys for the replies.

I am trying to get hardware info(for example: UUID) without using sudo or root privilege for licensing purpose

---

### Post by newcfd on 2015-11-03
How to access or extract data from the summary?

===========================================================================================================
Hal-info only offers a summary about your hardware.  Most computers  newer than a few years don't have or need hal (Hardware Abstraction  Layer).

---

### Post by deadflowr on 2015-11-03
While hal-info is still available for 14.04, hal is not.
But it is attainable via a ppa
[https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal](https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal)
The reason why the user made the ppa is self-explainable.

(I also love the name he gave his page)

EDIT: For fun, here is a launchpad discussion on it's removable:
[https://bugs.launchpad.net/ubuntu/+source/squeeze/+bug/1221254](https://bugs.launchpad.net/ubuntu/+source/squeeze/+bug/1221254)

---

### Post by newcfd on 2015-11-03
Great! Thanks a lot. I like the name too.

---

