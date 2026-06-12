---
title: "Do rpms work"
date: 2004-10-27
forum: General Help
---

### Post by phoolgobi on 2004-10-27
hey all,
so i am all excited about getting started with ubuntu but i am on dial up so i had to order the cds through shipit.

anyways, i have been a long time exclusive redhat user. first rh9 and now fc2. so i got tons of packages as rpms. would these work in ubuntu or would i need to download these again...

thanx

ps: has the shipping of the discs started yet?

---

### Post by adbak on 2004-10-27
RPMs *will* work, they just may not work as well as they could.  I believe that the package Alien is installed by default and you can convert RPMs to DEBs by using ```
 alien <filename>.rpm 
``` to make a <filename>.deb package.

Although you can convert RPMs to DEBs, you don't need to.  Most RPMs should be in .deb form in Apt or Synaptic.  So yes, you will have to download them again, but with the advantage of having them work better on your computer.

---

### Post by eNiNjA on 2004-10-27
```
sudo alien -d <filename>.rpm
```

---

