---
title: "[SOLVED] Sorting Packages by Installed Size"
date: 2007-11-04
forum: General Help
---

### Post by haldean on 2007-11-04
Hi! I'm slowly running out of space on my root partition, and so I wanted to remove some of the larger packages taking up space that I don't use anymore. I know there's a way to see the installed size of a package using apt-cache show, but I was wondering if there was a way to get a list of all of the packages installed and sort it by installed size. Thank you very much for your help!

Will

---

### Post by haldean on 2007-11-04
Never mind... I got it.
```
dpkg-query --show --showformat='${Package;-50}\t${Installed-Size}\n' | sort -k 2 -n
```

---

### Post by Cygnus on 2007-12-07
If I run this, then uninstall one of the listed packages and run the command again, the package is still listed. How do I avoid that ?

Also it would be nice if the different ui's made sure you could list installed packages by size, it's a very useful feature.

---

### Post by Cygnus on 2008-05-12
> **Cygnus said:**
> If I run this, then uninstall one of the listed packages and run the command again, the package is still listed. How do I avoid that ?

Found that this command works for that, even though the output is not so nice looking:

```

dpkg-query --show --showformat='${Package;-50}\t${Installed-Size} ${Status}\n' | sort -k 2 -n |grep -v deinstall 

```

---

