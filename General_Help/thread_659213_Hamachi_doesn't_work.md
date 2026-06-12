---
title: "Hamachi doesn't work"
date: 2008-01-05
forum: General Help
---

### Post by phearsome on 2008-01-05
Hello.
I'm having some problems with hamachi.
I followed this guide: [https://forums.hamachi.cc/viewtopic.php?t=16174&sid=07597a4374736d72520ea82cfa08bb7d](https://forums.hamachi.cc/viewtopic.php?t=16174&sid=07597a4374736d72520ea82cfa08bb7d)
but when I try to use hamachi-init, nothing happens. Nothing at all, not even an error message. 
Did I fail at some point or what?
Thanks in advance.

EDIT: Damn, missed a part,, problem solved.

---

### Post by nickware on 2008-01-14
I had the same problem.  The steps I missed were:

```

$ cd /usr/bin
$ sudo upx -d hamachi
```

---

