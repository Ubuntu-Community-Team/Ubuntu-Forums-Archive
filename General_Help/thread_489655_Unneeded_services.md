---
title: "Unneeded services"
date: 2007-07-01
forum: General Help
---

### Post by bowens44 on 2007-07-01
Is there a way to prevent unneeded service from starting?  Serivces like IPv6, ip6tables, everything releated to bluetooth and others. The system services app seems to be way too limited.

---

### Post by Rui Pais on 2007-07-01
you can blacklist modules, preventing from been loaded, adding the names to the file:
/etc/modprobe/blacklist

And you can turn services down. [Check here]("http://ubuntuforums.org/showthread.php?t=89491") some tips.

---

### Post by bowens44 on 2007-07-01
Thanks for the reply. It was just what I was looking for!

---

