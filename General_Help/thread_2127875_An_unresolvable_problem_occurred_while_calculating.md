---
title: "An unresolvable problem occurred while calculating the upgrade..."
date: 2013-03-21
forum: General Help
---

### Post by Sandy106 on 2013-03-21
I'm getting this error on my 10.04  machine in Update Manager and every search I've come up with doesn't fix it. I've spent 4 hours fighting with Ubuntu to try to fix this, any ideas?

An unresolvable problem occurred while calculating the upgrade.


Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

---

### Post by cortman on 2013-03-21
What is the output when you run

```
sudo apt-get upgrade
```


This will give more useful output.
Are you trying to upgrade the distro to a newer version or just upgrade the packages?

---

### Post by Sandy106 on 2013-03-21
sandy@sandy-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  transmission-common transmission-gtk
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

I'm just trying to update the packages.

---

### Post by ibjsb4 on 2013-03-21
I believe cortman meant to post

```
sudo apt-get update
```

---

### Post by schragge on 2013-03-21
Try to remove transmission packages, then re-install them:
```

sudo apt-get remove ^transmission
sudo apt-get install transmission

```

---

### Post by cortman on 2013-03-21
There is more information on "kept-back" packages and how to upgrade them with aptitude [here]("http://askubuntu.com/questions/601/the-following-packages-have-been-kept-back-why-and-how-do-i-solve-it").

---

