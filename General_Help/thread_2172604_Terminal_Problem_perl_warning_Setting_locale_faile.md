---
title: "Terminal Problem: perl: warning: Setting locale failed."
date: 2013-09-05
forum: General Help
---

### Post by JnPson on 2013-09-05
My server has english locale and my desktop has swedish. I keep getting this error while upgrading/installing.
```
perl: warning: Setting locale failed.    
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LC_TIME = "sv_SE.UTF-8",
    LC_MONETARY = "sv_SE.UTF-8",
    LC_ADDRESS = "sv_SE.UTF-8",
    LC_TELEPHONE = "sv_SE.UTF-8",
    LC_NAME = "sv_SE.UTF-8",
    LC_MEASUREMENT = "sv_SE.UTF-8",
    LC_IDENTIFICATION = "sv_SE.UTF-8",
    LC_NUMERIC = "sv_SE.UTF-8",
    LC_PAPER = "sv_SE.UTF-8",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory


```
I wonder how to get rid of this problem? 

Regards JnPson

---

### Post by JnPson on 2013-09-07
Bump

---

### Post by bluefrog on 2013-09-07
try to add your swedish locale to your server and /or add english locale to your desktop

sudo locale-gen sv_SE.UTF-8
sudo locale-gen en_US.UTF-8

---

### Post by JnPson on 2013-09-07
Brilliant. It fixed the error. Thank you.

---

