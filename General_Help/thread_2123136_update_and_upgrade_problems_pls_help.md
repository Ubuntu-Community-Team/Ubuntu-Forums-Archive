---
title: "update and upgrade problems pls help"
date: 2013-03-07
forum: General Help
---

### Post by keiko112 on 2013-03-07
Hi i have a problem on my ubuntu server when i should run a update or upgrade i get this 
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by apt-get)
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libapt-pkg-libc6.7-6.so.4.6)
some one pls help me

i run 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"

and is it a way to upgrade to new versjon whitout delet my stuff on it its very important that i dont mess this more up :)


i solved this and upgrade to new versjon now ty all

---

### Post by Cheesemill on 2013-03-07
Deleted

---

### Post by keiko112 on 2013-03-07
ok ty i will do that i think :)

---

### Post by schragge on 2013-03-07
Your apt-get is built against specific libstdc++6 version and requires this version to run. You'll see what versions are defined for your libstdc++6 by running
```

objdump -p /usr/lib/libstdc++.so.6|sed -n '/Version definitions/,/^$/p'

```

But trying to repair an important library on a system running an old OS release nearing its end of life is simply not worth it. Backup your data and install a newer Ubuntu version (12.04 LTS perhaps)

---

