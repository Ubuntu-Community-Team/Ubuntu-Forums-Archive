---
title: "Samba Recycle Bin"
date: 2020-09-01
forum: General Help
---

### Post by BigYellowDog on 2020-09-01
I've enabled the Recycle Bin in a Samba share.  The problem is when I try to delete I delete file in the recycle bin from Windows it goes into a sub folder instead of being deleted.

```

vfs object = recycle
recycle:repository = /home/public/trash/
recycle:touch = Yes
recycle:keeptree = Yes
recycle:versions = Yes
recycle:noversions = *.tmp,*.temp,*.o,*.obj,*.TMP,*.TEMP
recycle:exclude = *.tmp,*.temp,*.o,*.obj,*.TMP,*.TEMP,*.bak,thumb.db,Thumbs.db
recycle:exclude_dir = /trash,/recycle,/tmp,/temp,/TMP,/TEMP
#recycle:exclude_dir = /home/public/trash/

```

---

### Post by Morbius1 on 2020-09-01
I think I understand the question.

> recycle:repository = /home/public/trash/

The recycle repository is a folder relative to the path of the shared folder in the share. So if the share path = /home/public the "trash" bin is specified as:
```
recycle:repository = trash
```
And you don't create the folder samba creates it for you.

---

### Post by BigYellowDog on 2020-09-01
My bad, files are going into the trash folder perfectly.  I want to be able to empty (delete) files from the trash folder.

When I delete a file in the trash folder from Windows it goes to a trash folder in the trash folder.  Not what I want.

---

### Post by Morbius1 on 2020-09-01
It's doing that because you specified an actual path instead of just a folder name.

---

### Post by Morbius1 on 2020-09-01
Let's try this another way.

Go into your share definition and comment out the recycle:repository line:
```
#recycle:repository = /home/public/trash/                      
```
Then restart smbd.

If the path to your share is /home/public samba will automatically create a /home/public/.recycle folder.

When you delete something from the share on the client it will send it to that .recycle folder.

---

### Post by BigYellowDog on 2020-09-01
Thanks that worked.  Don't use an absolute path, otherwise you get a recursive file in the recycle bin when you delete files.

---

### Post by Morbius1 on 2020-09-01
If only I could say things as succinctly as you just did.

---

