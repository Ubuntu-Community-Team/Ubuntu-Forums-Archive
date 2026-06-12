---
title: "No more than 1GB of ram"
date: 2008-02-13
forum: General Help
---

### Post by russomiche on 2008-02-13
Hello,

My laptop has 2GB of ram but:

russomiche@topolino:~$ free -m
total used free shared buffers cached
Mem: 1011 994 16 0 53 583
-/+ buffers/cache: 357 653
Swap: 956 33 923

That is, my system recognizes only 1GB... please, could you help me?

Regards,

Michele

---

### Post by geirha on 2008-02-13
what does the following command output?
```
sudo lshw -class memory
```

---

