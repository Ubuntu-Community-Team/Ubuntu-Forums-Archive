---
title: "dkpg error"
date: 2008-07-08
forum: General Help
---

### Post by ultimatsz on 2008-07-08
```
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

help.

---

### Post by sisco311 on 2008-07-08
Try to replace the corrupted file with a backup:
```
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
```

---

### Post by forger on 2008-07-08
..and then try:
> sudo apt-get -f install; sudo apt-get update

---

### Post by ultimatsz on 2008-07-10
i did it and the same thing occured.. i have no choice to reinstall again ... =(

---

### Post by sisco311 on 2008-07-10
Search for more backups in the /var/backups folder:
[http://www.uluga.ubuntuforums.org/showpost.php?p=5046486&postcount=4](http://www.uluga.ubuntuforums.org/showpost.php?p=5046486&postcount=4)

Replace **status **with **available**, in the commands.

---

### Post by stimpyaw on 2009-03-26
This fix worked for me. THANKS!!

---

