---
title: "Apache2 starting problem"
date: 2006-11-25
forum: General Help
---

### Post by BornInChaos on 2006-11-25
Hi...well I'm using Ubuntu / insted of my old windows xp/ for some time and I\"m happy with it.Yesterday I installled apache2 .Everything went smoothly , but here is what I get when i start it

dimitar@dimitar-desktop:~$ apache2
(13): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

Any ideas ?

---

### Post by cilynx on 2006-11-25
what do you get if you:
```
sudo apache2ctl start
```

---

