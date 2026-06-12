---
title: "Ajenti not working"
date: 2014-12-06
forum: General Help
---

### Post by deb2 on 2014-12-06
I have a fresh install of Ubuntu and Ajenti but I can't get Ajenti to work.

When I run [FONT=courier new]netstat -tlnp | grep 8000[/FONT] I get: [FONT=courier new]tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN      1873/python[/FONT]

When I try to connect on [https://127.0.0.1:8000](https://127.0.0.1:8000) I get: [FONT=courier new]The connection was interrupted[/FONT] and when I try again I get: [FONT=courier new]The connection was reset[/FONT]

A fresh install of Ubuntu doesn't block any ports by default.

---

### Post by max-pittsley on 2014-12-19
Same problem here, would love to know if you found a solution.

Edit: It looks like the problem comes from not using HTTPS.

---

