---
title: "Find all install packages ?"
date: 2013-12-04
forum: General Help
---

### Post by kiran1247 on 2013-12-04
Hi,

Please do help me on how to find/search ( commands to use )  all installed softwares in ubuntu 12.04 ?

Thanks.

---

### Post by Zill on 2013-12-04
Open a terminal and enter the following code:
```
dpkg --get-selections > installed-software
```
This will produce a text file called "installed-software" listing all installed packages.

---

### Post by philinux on 2013-12-04
You can use this to create a text file.

```
dpkg --get-selections > packages.txt
```

---

### Post by kiran1247 on 2013-12-04
Thanks.

Where does this "installed-software" file gets created ? Path ?

---

### Post by philinux on 2013-12-04
Your home folder.

---

### Post by kiran1247 on 2013-12-04
Yep , thanks.

I can see the file under my home folder.

---

