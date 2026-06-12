---
title: "Problem with Package Manager on Ubuntu"
date: 2008-05-15
forum: General Help
---

### Post by evillgerbil on 2008-05-15
Ok, so my package manager gives me this error when I try to download or install anything

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



Anybody know how to solve this? I'm fairly stupid to computer lingo(I know, "then why use Linux?") so if somebody could help and explain a little bit what I'd have to do to fix, I would much appreciate it. Thanks!

---

### Post by wolfen69 on 2008-05-15
in terminal: (applications>accessories>terminal) copy and paste the following and hit enter then password-
```
sudo dpkg --configure -a
```

---

### Post by evillgerbil on 2008-05-15
Fixed it. Thank you very much and have a great day!

---

