---
title: "Apt-get update is almost endless"
date: 2008-04-17
forum: General Help
---

### Post by descentspb on 2008-04-17
On an Ubuntu 7.10 Server machine, when launching apt-get update i have a following output, instead of a normal one:

```

&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:389 http://ru.archive.ubuntu.com gutsy Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:390 http://ru.archive.ubuntu.com gutsy Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:391 http://ru.archive.ubuntu.com gutsy Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:392 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:393 http://ru.archive.ubuntu.com gutsy Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:394 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:395 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:396 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:397 http://security.ubuntu.com gutsy-security Release.gpg [191B]
...
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1549 http://ru.archive.ubuntu.com gutsy-updates Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1550 http://ru.archive.ubuntu.com gutsy-updates Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1551 http://ru.archive.ubuntu.com gutsy-updates Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1552 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1553 http://ru.archive.ubuntu.com gutsy-updates Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1554 http://ru.archive.ubuntu.com gutsy-updates Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1555 http://ru.archive.ubuntu.com gutsy-updates Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1556 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1557 http://ru.archive.ubuntu.com gutsy-updates Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1558 http://ru.archive.ubuntu.com gutsy-updates Release.gpg [191B]

```

and this is almost endless. What can the reason be? Maybe some ports get blocked by the outer firewall? Apt-get install works perfectly.

---

### Post by mick8985 on 2008-04-17
It can't be a port thing because it's just http, same as web browsing. Try commenting out the sources.list and just testing it on a different repository instead of the Russian (maybe?) mirrors you are using.

---

### Post by descentspb on 2008-04-17
Done that. Same thing again, just no russian repos in the list.

```
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:47 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:48 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:49 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:50 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:51 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:52 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:53 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:54 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:55 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:56 http://security.ubuntu.com gutsy-security Release.gpg [191B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:57 http://security.ubuntu.com gutsy-security Release.gpg [191B]
```

---

### Post by descentspb on 2008-04-17
And btw when installing packages it says, that the packages are not checked.

---

### Post by descentspb on 2008-04-18
bump

---

### Post by descentspb on 2008-04-21
bump

---

### Post by descentspb on 2008-04-24
and a bump again!

---

### Post by descentspb on 2008-04-29
:)

---

### Post by descentspb on 2008-04-30
Please someone answer!

---

### Post by descentspb on 2008-05-06
bump :(

---

