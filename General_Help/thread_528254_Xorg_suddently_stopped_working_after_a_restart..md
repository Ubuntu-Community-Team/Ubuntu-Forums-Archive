---
title: "Xorg suddently stopped working after a restart."
date: 2007-08-17
forum: General Help
---

### Post by Saxu on 2007-08-17
Hey.

I installed amd64 version of Ubuntu recently on my desktop pc. I installed every update, booted and Ubuntu still worked. After that I installed apache on accident (I was going to install apache2) so I decided to remove it. When I removed it my network connections stopped working => I booted. After that Xorg didn't work anymore. It said

```
kinit: No resume image, doing normal boot
Cannot open log file "var/log/Xorg.0.conf"
```

So im totally lost now :(

Sincerely,
Saxu

---

### Post by g2g591 on 2007-08-17
if you get a command line use this command :
"sudo dpkg-reconfigure xserver-xorg" (without the quotes of course)

---

