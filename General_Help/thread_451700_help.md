---
title: "help"
date: 2007-05-22
forum: General Help
---

### Post by tednugent on 2007-05-22
I tried to upgrade to 7.04 keep getting this message'E:Type '“deb' is not known on line 54 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

---

### Post by benmoreassynt on 2007-05-22
> **tednugent said:**
> I tried to upgrade to 7.04 keep getting this message'E:Type '“deb' is not known on line 54 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

You need to edit /etc/apt/sources.list to remove what sounds like a bad line in your repositories.

Do something like
 ```
sudo gedit /etc/apt/sources.list
```

and find line 54. If the problem is obvious, fix it (create a backup of sources.list first in case of unforeseen problems), or quote it here.

The word "deb" should not normally be a problem if part of a proper line. Can you therefore quote line 54 from your sources.list to see what the problem is?

---

