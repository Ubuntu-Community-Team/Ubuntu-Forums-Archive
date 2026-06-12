---
title: "Weird folders in /tmp"
date: 2007-09-30
forum: General Help
---

### Post by alexweb on 2007-09-30
hi.

I've noticed about some weird stuff in my /tmp folder
Here is it: 
```
ls -l /tmp/
total 1
drwx------ 3 root root  72 2007-09-30 19:16 0967197169
```

I'm getting new folder after each reboot. Each time folder name consists of different numbers. This folder if owned by root and has only empty .qt folder inside

Which program is creating such folders. 

BTW: lsof /tmp/0967197169 gave me nothing

---

