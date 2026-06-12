---
title: "Unable to install header"
date: 2018-03-17
forum: General Help
---

### Post by satimis on 2018-03-17
Hi all,

Ubuntu 16.04.4

uname -r```

4.13.0-37-generic

```

sudo apt-get install linux-headers-$(uname -r).```

....
E: unable to locate package linux-header-4.13.0-37-generic
...

```

Please help.  Thanks

---

### Post by Impavidus on 2018-03-17
Your command refers to linux-header**s**-$(uname -r). The response refers to linux-header-4.13.0-37-generic. Maybe you missed an s? Because linux-headers-4.13.0-37-generic exists.

---

