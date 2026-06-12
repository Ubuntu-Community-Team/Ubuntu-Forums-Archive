---
title: "Unity issue on old laptop 16.04"
date: 2018-01-10
forum: General Help
---

### Post by e1ektrob0y on 2018-01-10
Hi. I'm running 16.04 on a 10 year old laptop. It's been great until just recently. When I boot up, after the desktop loads, if I click on a program in the side bar or anywhere else for that matter, the entire desktop disappears except the background. 
I can still get to a tty. Did an update and upgrade but it did not fix. 

Any ideas?

---

### Post by cruzer001 on 2018-01-10
Could be time for a lighter distro.

Have you tried booting into your guest session and see if it works?

---

### Post by DuckHook on 2018-01-10
A lot of very smelly stuff has been hitting the fan the last couple of days due to: [https://ubuntuforums.org/showthread.php?t=2381801](https://ubuntuforums.org/showthread.php?t=2381801)

What kernel are you running? Post results of:```
uname -a
```

---

### Post by e1ektrob0y on 2018-01-10
Thanks. I've gone ahead and installed Lubuntu. See how it goes :)

---

### Post by rharry on 2018-01-12
This is probably it..

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1735594](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1735594)

---

