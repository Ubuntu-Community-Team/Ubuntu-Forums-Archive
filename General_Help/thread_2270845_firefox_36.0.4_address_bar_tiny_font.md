---
title: "firefox 36.0.4 address bar tiny font"
date: 2015-03-25
forum: General Help
---

### Post by Nutria on 2015-03-25
Hi,

xubuntu 14.04

After updating last night from v36.0.?? to 36.0.4, the font in the address bar got **really** small.  Anyone else notice that?  Attached is an example.

```
[SIZE=2]$ apt-cache policy firefox
firefox:
  Installed: 36.0.4+build1-0ubuntu0.14.04.1
  Candidate: 36.0.4+build1-0ubuntu0.14.04.1
  Version table:
 *** 36.0.4+build1-0ubuntu0.14.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     28.0+build2-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages[/SIZE]
```

---

### Post by andrew.46 on 2015-03-26
Looks ok to me; my own 36.0.4 screenshot attached...

---

### Post by Ko_Char on 2015-03-26
It looks very similar to the font I use.
remove the padauk font if you don't use that language

fonts-sil-padauk

---

### Post by Nutria on 2015-03-26
> **andrew.46 said:**
> Looks ok to me; my own 36.0.4 screenshot attached...

It turns out that the Old Address Bar add-on is incompatible with 36.0.4.

---

