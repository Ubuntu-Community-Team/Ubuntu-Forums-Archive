---
title: "Can't find libstdc++-libc6.1-1"
date: 2008-06-11
forum: General Help
---

### Post by wrgb2 on 2008-06-11
Hi,
I get the following error when I try to run an older game, Open Trek, that I just downloaded : error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory .  But when I search in package manager for this package, there are several other versions available, but no libc6.1-1 .  I have all the repositories available except for the ones under the Third Party Software tab.  Where can I find this package, and is it compatible with Ubuntu 8.04?
Thanks,

---

### Post by wrgb2 on 2008-06-11
Bump.  Anybody know the answer to this one?
Thanks,

---

### Post by KingTermite on 2008-06-11
I saw this in another thread today in the programming forum. Hopefully it will set it right for you.

sudo apt-get install libc6-dev

---

### Post by Joeb454 on 2008-06-11
As KingTermite says you can try running ```
sudo apt-get install libc6.1-dev libc6.1
```

If it still doesn't work, you can try running ```
sudo apt-get install build-essential
``` Hope that helps :)

---

### Post by wrgb2 on 2008-06-11
I tried all three suggestions, but still get the same error.  When I ran "sudo apt-get install libc6.1-dev libc6.1" it came back saying that the package was not available.  The program seems to be looking specifically for libc6.1-1 .  Any other suggestions? 
Thanks,
Randy

---

### Post by wrgb2 on 2008-06-11
Anyone know where, or how, I can get libc6.1-1 for this?

---

