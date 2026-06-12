---
title: "I messed up, how do I do a system repair?"
date: 2008-04-22
forum: General Help
---

### Post by michaelfougnie on 2008-04-22
Ubuntu 7.10. When ever I try to open Synaptic Package Manager or Add/Remove Applications, it comes up with this error:

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by dicecca112 on 2008-04-22
this should fix it [http://ubuntuforums.org/showthread.php?p=3595003](http://ubuntuforums.org/showthread.php?p=3595003)

---

### Post by Zorael on 2008-04-22
edit: Well, mine was a workaround, above poster's was a fix. Ignore me.
[quote=Me, right now]Hmm, sounds like you just need to rename or delete **/etc/apt/sources.list.d/medibuntu.list**.

```
$ cd /etc/apt/sources.list.d
$ sudo mv medibuntu.list medibuntu.list.disabled
```

:>[/quote]

---

### Post by michaelfougnie on 2008-04-22
> **dicecca112 said:**
> this should fix it [http://ubuntuforums.org/showthread.php?p=3595003](http://ubuntuforums.org/showthread.php?p=3595003)
Thank you!

---

