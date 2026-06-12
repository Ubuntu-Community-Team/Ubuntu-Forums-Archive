---
title: "Firefox Cyclic Freezes"
date: 2008-05-06
forum: General Help
---

### Post by meuge on 2008-05-06
Since a day or two ago, I've been getting a problem, wherefore Firefox3 will periodically (up to 3-4 times/minute) stall and the window will go black for 5 seconds or so, after which it will go back to working. While it hangs, the system is very slow, and often appears hanged as well. If Firefox is not restarted, the cycles get more frequent (it'll take 3-5 minutes of using FF3 for the first cycle, 2-3 minutes before the next... all the way up to Firefox hanging every few seconds). 

Please help.

---

### Post by daverich on 2008-05-06
yup same here.

ff3 is working like crap here.

Kind regards

Dave Rich

---

### Post by meuge on 2008-05-06
> **daverich said:**
> yup same here.

ff3 is working like crap here.

Kind regards

Dave Rich

Found a work-around here:
[http://ubuntuforums.org/showpost.php?p=4889218&postcount=2](http://ubuntuforums.org/showpost.php?p=4889218&postcount=2)

Seems the problem has to do with Firefox's security and the fact that it tries to authenticate "attack sites".

[quote=airwolf]Disable Firefox checking for attack sites and suspected forgery sites in Preferences -> Security.

Close Firefox and delete ~/.mozilla/firefox/[profile].default/urlclassifier*.sqlite[/quote]

This seems to be working for me... at least for now.

---

