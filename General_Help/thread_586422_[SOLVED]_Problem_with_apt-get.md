---
title: "[SOLVED] Problem with apt-get"
date: 2007-10-22
forum: General Help
---

### Post by PmDematagoda on 2007-10-22
I seem to be having a slight problem with apt-get, whenever I try to do anything that concerns removing or installing packages, it gives me this message as well:-

```
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up kazehakase (0.4.3-1ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing kazehakase (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 kazehakase
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Could anyone please help me solve this problem as this is a bit of a bother.

Thanks

---

### Post by GrammatonCleric on 2007-10-22
Try running...

```

sudo apt-get -f install

```


-GC

---

### Post by PmDematagoda on 2007-10-22
No, the problem still persists.

---

### Post by GrammatonCleric on 2007-10-22
So you tried to install  kazehakase and it did not complete install? Have you tried removing kazehakase?

```

sudo apt-get remove kazehakase -f

```

-GC

---

### Post by PmDematagoda on 2007-10-22
Tried, was close, but still no success:-
```

(Reading database ... 124162 files and directories currently installed.)
Removing kazehakase ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing kazehakase (--remove):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 kazehakase
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by GrammatonCleric on 2007-10-23
Hmmm...Try..

```

sudo dpkg --force-all -i  

```if that doesn't work try...

```

sudo rm /var/lib/dpkg/info/kazehakase*

```

---

### Post by PmDematagoda on 2007-10-23
It works great now, thank you so much GrammatonCleric for all your help.:)

---

