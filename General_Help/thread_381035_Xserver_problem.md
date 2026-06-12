---
title: "Xserver problem"
date: 2007-03-10
forum: General Help
---

### Post by celticbhoy on 2007-03-10
I updated X.org to version 7.2.0.0 last night, and can no longer get xserver to run. when I boot up I get :-

[R200 Setup]  X window system version 7.2.0.0

X version mismatch     detected X.org 7.2.0.0    required X.org 7.1.0.0

I know that this problem is of my own doing, but I want to know if there is any way to downgrade the version to 7.1.0.0 or if I will have to re-install.

---

### Post by tribble222 on 2007-03-10
If you updated it using a package manager, you should be able to somehow force the old version.  I know how to do it in synaptic but that won't help you since you can't get X to start.  There must be some way to force a version in apt-get or aptitude however.

---

### Post by STREETURCHINE on 2007-03-10
if you had backup from recovery mode you can 

     ```
sudo cp /etc/X11xorg.conf.backup /etc/X11/xorg.conf
```

if no backup 

    ```
sudo dpkg-reconfigure xserver-xorg
```

 then 

     ```
sudo apt-get update
```

then restart x

     ```
startx
```

---

### Post by dreadlord_chris on 2007-04-08
> **tribble222 said:**
> If you updated it using a package manager, you should be able to somehow force the old version.  I know how to do it in synaptic but that won't help you since you can't get X to start.  There must be some way to force a version in apt-get or aptitude however.

from the **man** pages:

To select a particular version of the package,  append &#8220;=<version>&#8221; to the package name: 
for instance, &#8220;aptitude install apt=0.3.1&#8221;. Similarly, to select  a package from a particular archive, append &#8220;/<archive>&#8221; to  the package name: for instance, &#8220;aptitude install apt/experimental&#8221;.

---

