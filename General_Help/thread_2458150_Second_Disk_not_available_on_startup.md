---
title: "Second Disk not available on startup"
date: 2021-02-17
forum: General Help
---

### Post by omanidos on 2021-02-17
Good evening,

I recently (re)installed Ubuntu 20.04 on my PC with two disks. Since then I am unable to launch the games that I have installed on the second disk until I navigate to it in the file browser.

Is there something I can do to avoid that step?

---

### Post by CelticWarrior on 2021-02-17
Yes, mount it at the startup.

---

### Post by dinkidonk on 2021-02-17
You probably need to add the drive to /etc/fstab:

```
/dev/sdXY /path/to/mount/point auto 0 0
```

---

### Post by omanidos on 2021-02-18
I added the drive to the fstab file and now it works immediately.

Thanks for the help.

---

