---
title: "How can I gain acces to files in my Windows partition from within Ubuntu?"
date: 2008-06-03
forum: General Help
---

### Post by charlescarroll1 on 2008-06-03
I have installed Ubuntu 8.04 inside of Windows.  How can I gain access to files in my Windows partition from within Ubuntu?

---

### Post by markbusu on 2008-06-03
By default... Ubuntu will automatically Mount the the Windows Drive for you so you can access the content of that disk.. However i am not sure if this is also done in WUBI...

Is the Disk NTFS?

Give us the output of the following command

```
sudo mount
```

Mark

---

### Post by iaculallad on 2008-06-03
Start by checking the /host or /media directories for your windoze partition.

---

### Post by iwallet on 2008-06-03
go to /host
then users, and from there you should know where to go ;)

---

### Post by MetalManiacMat on 2008-06-03
Installed with Wubi = /host
Installed on a dedicated partition = /media

---

### Post by charlescarroll1 on 2011-07-29
Thanks iaculallad. My "windoze" files were in the /host directory.

):P

---

