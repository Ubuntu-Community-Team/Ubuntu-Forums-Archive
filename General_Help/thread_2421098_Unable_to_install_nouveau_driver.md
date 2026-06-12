---
title: "Unable to install nouveau driver"
date: 2019-06-16
forum: General Help
---

### Post by Edward_Diener on 2019-06-16
In 18.04 I am trying to install the nouveau driver "xserver-xorg-video-nouveau-hwe-18.04", version "1:1.0.15-3~18.04.1". But when I add it I get a conflict, but I have no idea what is conflicting. When I look at the dependencies one of the lines reads:

```
Conflicts: xserver-xorg-video-nouveau-hwe-18.04
```

How can a package conflict with itself ?

There is a "xserver-xorg-video-nouveau", version "1:1.0.15-2" package I can install, but this looks like an earlier version of the one above.

---

### Post by Frogs Hair on 2019-06-16
Post the output of the of the following command.

 ```
apt-cache policy xserver-xorg-video-nouveau
```

---

### Post by Edward_Diener on 2019-06-16
> **Frogs Hair said:**
> Post the output of the of the following command.

 ```
apt-cache policy xserver-xorg-video-nouveau
```

```
apt-cache policy xserver-xorg-video-nouveau
xserver-xorg-video-nouveau:
  Installed: (none)
  Candidate: 1:1.0.15-2
  Version table:
     1:1.0.15-2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages


```

---

