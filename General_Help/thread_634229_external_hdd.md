---
title: "external hdd"
date: 2007-12-07
forum: General Help
---

### Post by mr.farenheit on 2007-12-07
i have an extra external hard drive and was wondering how i could format it so that i can use it for large saves and backing up files. i tried it before and had the problem of it telling me i could only access the drive through root. how would i set it up so it would just be easy to drag and drop?

---

### Post by taurus on 2007-12-07
If you format it as ext3 and mount it to /media/storage, you can change the ownership of /media/storage from root to your login name so you can write to it anytime you want.

```
sudo chown -R **username**:**username** /media/storage
sudo chmod -R 755 /media/storage
```

---

