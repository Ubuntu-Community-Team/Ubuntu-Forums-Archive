---
title: "Error: dependencies could not be resolved (Software Center)"
date: 2013-04-13
forum: General Help
---

### Post by patagriff on 2013-04-13
I run Unbuntu 12.10 x86_AMD64 on my Acer Aspire 5515. When attempting to installthe Wine Windows Program loader from the Software Center, it could not perform the install and gave me the following error message.

The following packages have unmet dependencies:


wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20.1 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is a virtual package

My level of sophistication with Ubuntu has not risen such that I know how to deal with these issues. 

Would someone please allow me the benefit of their experience and advise me as to how I can fix this? Thank you in advance for any assistance you may provide.

P. Griffith- Out of wine in Tacoma

---

### Post by zombifier25 on 2013-04-13
Have you tried running an repo update?
```
sudo apt-get update
```

If it still doesn't work, add the Wine PPA. [Instructions](http://www.winehq.org/download/ubuntu)

---

