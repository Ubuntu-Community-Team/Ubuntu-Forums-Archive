---
title: "building binary nvidia drivers"
date: 2006-12-07
forum: General Help
---

### Post by fettuohi on 2006-12-07
Hi, I'm looking for a guide how-to build the binary nvidia drivers from run package offered at nvidia.com. Anybody got a guide how-to do that?

Regards

André

---

### Post by halfvolle melk on 2006-12-07
For all Ubuntu flavors, look here:
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by fettuohi on 2006-12-07
Thanks but this seems to describe a script that does everything. I just need the part how-to build because I want to do a custom installation of the driver, i.e. with changes in the run package.

Regards

André

---

### Post by reclusivemonkey on 2006-12-07
> **fettuohi said:**
> Thanks but this seems to describe a script that does everything. I just need the part how-to build because I want to do a custom installation of the driver, i.e. with changes in the run package.

Regards

André

I believe you need "build-essential" installed to do this. Download the nvidia drivers, then you can run with

```

sudo sh NVIDIA*.run

```

I believe if you use the -A flag on nvidia-installer once it has installed you can see all the advanced options.

---

### Post by fettuohi on 2006-12-07
How do I build the deb package itself?

Regards

André

---

