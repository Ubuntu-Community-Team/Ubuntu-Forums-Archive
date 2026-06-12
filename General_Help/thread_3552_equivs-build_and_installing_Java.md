---
title: "equivs-build and installing Java"
date: 2004-11-07
forum: General Help
---

### Post by d1zzy on 2004-11-07
Hi all

I'm trying to install Java using the instructions found [here](http://wiki.osuosl.org/display/DEV/Java+on+Debian) and I've gotten down to the bit where you do the equivs-builds bit, but equivs-build doesn't seem to be installed on my machine and I can't seem to find it through Synaptic.

Any ideas?

Cheers,

---

### Post by WW on 2004-11-07
I suspect that you didn't do "Step 0", which is the step above "Install Java SDK":

```
sudo apt-get update
sudo apt-get install kaffe equivs java-common java2-common
```

(I added **sudo** in front of the commands.)
The packages kaffe, equivs, and java2-common are in the "universe" component of the Ubuntu repository, so you will have to enable "universe" to get them.

---

### Post by p!=f on 2004-11-07
[QUOTE=d1zzy]Hi all

I'm trying to install Java using the instructions found [here](http://wiki.osuosl.org/display/DEV/Java+on+Debian) and I've gotten down to the bit where you do the equivs-builds bit, but equivs-build doesn't seem to be installed on my machine and I can't seem to find it through Synaptic.

Any ideas?

Cheers,[/QUOTE]
 And how about this? ;)

```

 * 14:52:05 * pef @ agonicus *
[~] > apt-cache search equivs
equivs - Circumvent Debian package dependencies

 * 14:55:10 * pef @ agonicus *
[~] > dpkg -L equivs | grep equivs-build
/usr/share/man/man1/equivs-build.1.gz
/usr/bin/equivs-build

```

---

### Post by d1zzy on 2004-11-07
Yes that did it! That'll teach me to read it properly!

Thanks,

---

