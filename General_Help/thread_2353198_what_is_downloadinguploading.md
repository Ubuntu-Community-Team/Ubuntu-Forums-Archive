---
title: "what is downloading/uploading"
date: 2017-02-19
forum: General Help
---

### Post by jgw on 2017-02-19
Sometimes a machine will start downloading, or uploading (mostly downloading).   Sometimes I can't figure out what is doing what.  I try and turn off whatever but I still can't tell what is going on or what files(s) are being messed with.  I was wondering if there is a command which would tell me these things.

Thank you...............

---

### Post by The Cog on 2017-02-19
```
sudo netstat -pt
```
will show you the current TCP connections and which program has them open.

---

### Post by jgw on 2017-02-19
Thank you!

---

