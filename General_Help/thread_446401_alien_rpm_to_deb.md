---
title: "alien rpm to deb"
date: 2007-05-16
forum: General Help
---

### Post by thedevilisbad on 2007-05-16
I'm trying to get my printer to work but I'm not sure how to use alien to convert rpm to deb. he's the thread I found to fix my problem sorta... [http://ubuntuforums.org/showthread.php?p=2283194](http://ubuntuforums.org/showthread.php?p=2283194)

any help would be great

thanks,
Aaron

---

### Post by earobinson on 2007-05-16
what happens when you try, ```
man alian
``` will give you the commands manual

---

### Post by taurus on 2007-05-16
```
alien filename.rpm
sudo dpkg -i filename.deb
```

---

### Post by Marsolin on 2007-05-17
```
sudo alien --scripts -i filename.rpm
```

Remove the -i if you only want to convert and don't also want to install the package.

---

