---
title: "Created 2nd partition in root folder for data was that wrong?"
date: 2007-04-22
forum: General Help
---

### Post by MontyV on 2007-04-22
Ok I installed Ubuntu Feisty 7.04 and created these partitions during installation:

20GB - Primary - ext3 (Mount Point "/")
35GB - Logical - ext3 (Mount Point "/data")
1GB - Swap

Now I cannot add data to the second partition.  I'm guessing I shouldn't have done that and added that data folder to the /usr/local folder right?  Either way can I move the data folder into my "Home" folder without having to reinstall everything once again so I can access the data folder?

Please help.

- Monty

---

### Post by yabbadabbadont on 2007-04-22
You just need to give your user permission to write in the /data folder.  Using "daffy" as an example user run, in a terminal window, the following:
```
sudo chown daffy:daffy /data
```
After that, the "daffy" user will have permission to create/delete/modify files and folders inside of /data.

---

### Post by MontyV on 2007-04-22
> **yabbadabbadont said:**
> You just need to give your user permission to write in the /data folder.  Using "daffy" as an example user run, in a terminal window, the following:
```
sudo chown daffy:daffy /data
```
After that, the "daffy" user will have permission to create/delete/modify files and folders inside of /data.

Excellent.  Worked like a charm.  Thank You.

---

