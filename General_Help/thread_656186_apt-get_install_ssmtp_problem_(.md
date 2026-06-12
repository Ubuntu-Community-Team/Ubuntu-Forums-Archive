---
title: "apt-get install ssmtp problem :("
date: 2008-01-02
forum: General Help
---

### Post by swigrid on 2008-01-02
Hi,

do you know what to do with this?

```

Setting up ssmtp (2.61-11) ...
export: 44: #: bad variable name
dpkg: error processing ssmtp (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ssmtp
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

thank you

---

### Post by swigrid on 2008-01-02
solved by:

```

dpkg --purge ssmtp
apt-get install ssmtp

```

---

