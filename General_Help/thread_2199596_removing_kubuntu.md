---
title: "removing kubuntu"
date: 2014-01-14
forum: General Help
---

### Post by Brotell1950 on 2014-01-14
Hi all I have installed a copy of Kubuntu on an external drive how do I remove i, the program tells me I am not root so no permissions.

Regards

Terry

---

### Post by maestrobwh1 on 2014-01-14
IF there is nothing else on the drive, reformat it or if you really don't care to use the installation of Kubuntu you could also just change the permissions

terminal
```
sudo chown -R (username) /path/to/mounted/drive
```

then delete the contents via a file manager 

or, you could do 

```
sudo rm -rf /path/to/eternal/drive/*
```

BE CAREFUL OF THE LAST COMMAND and make sure your path is correct, because it will delete everything in the directory, with no way of really recovering anything.

---

### Post by Brotell1950 on 2014-01-14
neither of these commands let me have access

Terry

---

### Post by Brotell1950 on 2014-01-15
Solved the problem used gparted to remove the partition

Terry

---

