---
title: "cannot do a git clone download"
date: 2017-06-21
forum: General Help
---

### Post by ubto66 on 2017-06-21
ubuntu 14.04 64bit
[https://blog.fossencdi.org/nonfree-firmware-android.html](https://blog.fossencdi.org/nonfree-firmware-android.html)

git clone [https://code.fossencdi.org/firmwares_nonfree.git](https://code.fossencdi.org/firmwares_nonfree.git) says
```
Cloning into 'firmwares_nonfree'...
remote: Counting objects: 67, done.
remote: Compressing objects: 100% (62/62), done.
remote: Total 67 (delta 34), reused 0 (delta 0)
Unpacking objects: 100% (67/67), done.
Checking connectivity... done.
warning: remote HEAD refers to nonexistent ref, unable to checkout.

$

```

The folder is created. Nothing downloaded.
How do I download the files? Does not have to be git clone. Thanks.

---

### Post by steeldriver on 2017-06-21
As explained here [warning: remote HEAD refers to nonexistent ref, unable to checkout]("https://stackoverflow.com/a/15631690/4440445") you can list the available branches using

```

$ git branch -a
  remotes/origin/cm-13.0

```

then checkout the wanted (in this case, the only) branch by name

```

$ git checkout cm-13.0
Branch cm-13.0 set up to track remote branch cm-13.0 from origin.
Switched to a new branch 'cm-13.0'
$ 
$ ls
espresso3g-fwinfo  espressowifi-fwinfo  firmwares.sh  i9100-fwinfo  i9300-fwinfo  i9305-fwinfo  maguro-fwinfo  n7000-fwinfo  n7100-fwinfo

```

---

### Post by ubto66 on 2017-06-21
Thanks.
I read [https://stackoverflow.com/a/15631690/4440445](https://stackoverflow.com/a/15631690/4440445). I was not able to understand it.
The part of files I would like to get, are the samsung i9100 firmware files.
Can you tell how to download these specific files?

I tested the [https://github.com/TheMuppets](https://github.com/TheMuppets) link. I downloaded the samsung files. Apparently you cannot use them as they are.

---

