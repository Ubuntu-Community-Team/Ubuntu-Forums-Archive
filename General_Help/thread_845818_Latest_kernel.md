---
title: "Latest kernel"
date: 2008-07-01
forum: General Help
---

### Post by McTek on 2008-07-01
How can one identify the latest kernel ver.That has been installed on my machine through up dates.

---

### Post by sdennie on 2008-07-01
Do you mean the latest kernel version in general or the latest Ubuntu kernel version?  All the kernel versions are stored at [www.kernel.org](www.kernel.org) and the front page has information on the latest kernels.  You should be able to find the latest version of the Ubuntu kernel with:

```

sudo apt-get update
apt-cache show linux-image-generic | head | grep Version

```

---

### Post by Vivaldi Gloria on 2008-07-01
```
uname -r
```

shows you the kernel you are using by the way. 

Sometimes ubuntu proposed repo contains a newer version of the kernel that is not available yet in the regular repos.

---

