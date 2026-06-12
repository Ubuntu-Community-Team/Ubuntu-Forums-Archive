---
title: "Can't Delete Backups Made with ConeZilla"
date: 2016-04-20
forum: General Help
---

### Post by Rick St. George on 2016-04-20
Running UbuntuStudio v14.04 LTS

Have made backups with ConeZilla. Need to delete old BUs. System won't let me copy or delete them. Some of the icons have a transparent X on them.

How can I DELETE them off my computer to free up space? 

Thanks!

---

### Post by Bucky Ball on 2016-04-20
Open a file manager as root is easy. You probably don't have permission. Open a terminal and:

```
gksudo nautilus
```

Delete backups. Close file manager. Don't hang around in there as root as you can cause some serious breakage.

---

### Post by Rick St. George on 2016-04-20
Thanks "BuckyBall" ... its going to take me about 40 minutes. Got to copy a BU to another location and make room to Restore the BU to that partition so I can recover a File with CloneZilla. Then I'll just delete it all. Too bad can't recover a file from a Cone/BU - have to restore it somewhere else first!!!

---

### Post by Bucky Ball on 2016-04-20
So it's working? If so, please mark the thread as solved to help others. 

Good luck with it. ;)

---

