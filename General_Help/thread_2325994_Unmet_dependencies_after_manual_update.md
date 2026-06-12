---
title: "Unmet dependencies after manual update"
date: 2016-05-27
forum: General Help
---

### Post by alexander70 on 2016-05-27
Hello,

Please, help me with one thing. Recently I updated squid to 3.5 version. After that I can not use apt-get install for any package, I receive this:

 /etc/squid3# apt-get install tftp-hpa Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 squid : Depends: squid3 (= 3.3.8-1ubuntu6.4) but 3.5.13-0ubuntu1 is to be installed
 tftp-hpa : Conflicts: tftp but 0.17-18ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

What should I do? If I'll use apt-get -f install, squid 3.5 will be downgraded automatically to 3.3.8? Thank you.

---

### Post by slickymaster on 2016-05-27
Hi alexander70, welcome to the forums.

Did you try to run what the package manager suggested```
sudo apt-get -f install
```

---

### Post by alexander70 on 2016-05-27
I'm afraid of automatic roll-back to previous version of squid. "apt-get -f.." save my current (newer) version?

---

