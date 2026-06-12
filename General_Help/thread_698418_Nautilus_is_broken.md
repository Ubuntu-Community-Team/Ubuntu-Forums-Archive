---
title: "Nautilus is broken"
date: 2008-02-16
forum: General Help
---

### Post by iancvt55 on 2008-02-16
Hi

I was trying to move a folder into /etc

somehow I messed up Nautilus and this is what I now get:

ian@vulcan607:~$ sudo nautilus
sudo: /etc/sudoers is mode 0666, should be 0440
ian@vulcan607:~$ gksudo nautilus
ian@vulcan607:~$

Help!

Thanks

---

### Post by chrisccoulson on 2008-02-16
Boot in to recovery mode. Then:
```
chmod 440 /etc/sudoers
reboot
```

---

