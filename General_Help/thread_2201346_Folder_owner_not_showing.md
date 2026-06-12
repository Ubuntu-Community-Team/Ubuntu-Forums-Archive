---
title: "Folder owner not showing"
date: 2014-01-24
forum: General Help
---

### Post by Abhinav_Kumar_Sinh on 2014-01-24
I created a folder sources in /mnt/user as root and changed its ownership using following command:
chown -v user /mnt/user/sources (while logged in as root).

But when i opened the folder by right clicking it and clicking "Permission" tab, the owner is not showing anything, earlier it was showing root.
Can anybody tell,what is the problem here and what is its solution ? 

I have attached the screenshot here.

Thanks

---

### Post by Dave_L on 2014-01-24
What's the output from:
```
stat /mnt/user/sources
```

---

