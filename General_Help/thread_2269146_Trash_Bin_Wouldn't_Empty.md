---
title: "Trash Bin Wouldn't Empty"
date: 2015-03-13
forum: General Help
---

### Post by terrell2 on 2015-03-13
Hi community. One day i was in nautilus in sudo mode and when i try to delete things in the regular user mode in the trash bin in nautilus, It says i dont have permission to do so. And when i try to get into nautilus as sudo user, It cant see or it says "This location can't be displayed". What do i do?

---

### Post by deadflowr on 2015-03-14
Let's look at the what the Folder containing the Trash folder says
post the output for
```
ls -l ~/.local/share/ | grep Trash
```

---

### Post by terrell2 on 2015-03-14
THat command gives me this

drwx------  5 doral doral   4096 Mar  6 00:57 Trash

---

### Post by terrell2 on 2015-03-15
Never mind. I'll just reinstall ubuntu then. Thank you

---

