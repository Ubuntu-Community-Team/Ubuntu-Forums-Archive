---
title: "Ubuntu-Debian relationship"
date: 2008-05-12
forum: General Help
---

### Post by voytechs on 2008-05-12
I'm making my library ([http://jnetpcap.sf.net](http://jnetpcap.sf.net)) available on multiple platforms and a little unfamiliar with ubuntu/debian relationship.

As I understand it, Ubuntu is based on debian.

My question is if I build my package on debian will it install cleanly under any ubuntu OS?

---

### Post by p_quarles on 2008-05-12
> **voytechs said:**
> I'm making my library ([http://jnetpcap.sf.net](http://jnetpcap.sf.net)) available on multiple platforms and a little unfamiliar with ubuntu/debian relationship.

As I understand it, Ubuntu is based on debian.

My question is if I build my package on debian will it install cleanly under any ubuntu OS?
No. You'll have to test -- and possibly rebuild -- on each distribution you want to support. There's a good likelihood that it will work, but no way of knowing without verifying it.

---

### Post by voytechs on 2008-05-12
> **p_quarles said:**
> No. You'll have to test -- and possibly rebuild -- on each distribution you want to support. There's a good likelihood that it will work, but no way of knowing without verifying it.

Ok, thanks. I wasn't sure if that would work at all, but it sounds like it will. And of course it will be tested on all the platforms before its released :) I have plenty of jUnit test cases to do that.

---

