---
title: "How to switch gdm vs entrance (E17)?"
date: 2005-06-10
forum: General Help
---

### Post by Neo40 on 2005-06-10
Hello,

I have installed E17 cvs like this howto:
[http://www.ubuntuforums.org/showthread.php?t=30525&highlight=E17](http://www.ubuntuforums.org/showthread.php?t=30525&highlight=E17)

I would like to use entrance instead gdm. I did exactly what this howto said: [https://vogelweith.homeftp.net/Linux/e17.php](https://vogelweith.homeftp.net/Linux/e17.php)
But when I restart, I still have gdm. 
Anyone can help?

Thanks!

---

### Post by Neo40 on 2005-06-10
[QUOTE=Neo40]Hello,

I have installed E17 cvs like this howto:
[http://www.ubuntuforums.org/showthread.php?t=30525&highlight=E17](http://www.ubuntuforums.org/showthread.php?t=30525&highlight=E17)

I would like to use entrance instead gdm. I did exactly what this howto said: [https://vogelweith.homeftp.net/Linux/e17.php](https://vogelweith.homeftp.net/Linux/e17.php)
But when I restart, I still have gdm. 
Anyone can help?

Thanks![/QUOTE]

EDIT: I can't test it right now, but I think I have to: rc-update add xdm default ??

---

### Post by ner0tic on 2008-01-07
i'm pretty sure (i haven't needed to try it) that you can just do:
```
sudo dpkg-reconfigure gdm
```

and just select entrace

---

