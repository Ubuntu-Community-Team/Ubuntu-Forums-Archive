---
title: "man-db/auto-update"
date: 2022-02-28
forum: General Help
---

### Post by stevenfriedrich-twc.com on 2022-02-28
Sometimes I use apt install, and I get this message: Not building database; man-db/auto-update is not 'true'.

Where is this man-db/auto-update configuration item?

---

### Post by Xian on 2022-03-02
The relevant file needs to be restored for that warning to cease. 

You can do it from a terminal with command:
```
sudo touch /var/lib/man-db/auto-update
```

---

