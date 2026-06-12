---
title: "Reconfigure system without APT?"
date: 2007-02-01
forum: General Help
---

### Post by AndreasJ on 2007-02-01
I recently got my filesystem (ext3) corrupt. No important data that couldn't be recovered was lost. But some of the system files and apt-get filesystem hierarchy was destroyed. Almost everything in /var related to apt-get (dpkg) and some other systemfiles. I would like to recover apt-get and after that reconfigure the entire system.  I get segmentations fault now and then and the system is somewhat flaky.

---

### Post by bustanil on 2007-02-01
**dpkg-reconfigure** maybe?

---

### Post by AndreasJ on 2007-02-01
I managed to fix APT. But I can't reconfigure the system with dpkg-reconfigure. My "/var/lib/dpkg/available" is empty.

---

### Post by bapoumba on 2007-02-02
Mmm ... I may be wrong, but unless you can get it from a similar install, i'm not sure you can recover it. In any case, I would be interested to find out if it is possible.

---

### Post by konst88 on 2007-02-02
Maybe:
```
sudo aptitude reinstall dpkg

```

---

### Post by az on 2007-02-02
> **AndreasJ said:**
> But some of the system files and apt-get filesystem hierarchy was destroyed. Almost everything in /var related to apt-get (dpkg) and some other systemfiles. I would like to recover apt-get and after that reconfigure the entire system.  I get segmentations fault now and then and the system is somewhat flaky.


I don't think there is a reliable way to recover from that.  I may be wrong, but you would have to audit your installed packages by looking at your filesystem to see what binaries and libs are there and then cross-referencing them to the corresponding packages.  Then you would have to rebuild the package database - I don't know of a package or a tool that can do this.

I think that since you have recoverd any valuable data, it would be more sensible to just reinstall.  You cannot be sure of the integrity of any of the remaining bits on your system anyway...  Even if the files are there, they may not be intact.

Good luck!

---

### Post by AndreasJ on 2007-02-02
I could get the installed packages with "dpkg --get-selections". That helped me to recover my system even when a lot of system files where missing. I wrote a script that reinstalled every package.

```

#!/bin/bash

packageList=(`dpkg --get-selections | awk '$2 ~ /^install/ { print $1 ; }'`)
for i in ${packageList[@]}; do
    echo "Reinstalling package: $i"
    apt-get -fy --reinstall install $i
done

```

After creating some missing directories finally my system is up and running again. Everything seems to work, no hickups so far.

Thanks for your help and comments.

---

