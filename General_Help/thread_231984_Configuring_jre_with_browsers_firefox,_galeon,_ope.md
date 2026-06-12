---
title: "Configuring jre with browsers: firefox, galeon, opera in ubuntu system"
date: 2006-08-08
forum: General Help
---

### Post by true_friend on 2006-08-08
i have a problem i can not run java applets in browsers.
i have sun java enviroment 5 installed on linux system but can not execute it in browers can some one guide me how to configure browsers with jre????????

---

### Post by Jagot on 2006-08-08
You may just need to tell Ubuntu to use the correct version of Java.  Run this command:

```
sudo update-alternatives --config java
```

Then select the version you want to use and try again.

---

