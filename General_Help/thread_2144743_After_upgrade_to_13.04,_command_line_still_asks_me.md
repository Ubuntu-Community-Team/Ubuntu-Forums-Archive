---
title: "After upgrade to 13.04, command line still asks me to do-release-upgrade"
date: 2013-05-13
forum: General Help
---

### Post by NanakiXIII on 2013-05-13
Hey all,

I recently upgraded a machine from 12.10 to 13.04 and while nothing appears to be broken, I have an odd issue. When I ssh into the machine, I get the following message:

```
Welcome to Ubuntu 13.04 (GNU/Linux 3.8.0-19-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.
```

That seems a bit contradictory. I tried running do-release-upgrade but it doesn't do anything:

```
~$ do-release-upgrade
Checking for a new Ubuntu release
No new release found

```

Any thoughts? I'm just worried the upgrade may be incomplete or something.

---

### Post by Frogs Hair on 2013-05-13
If you have synaptic installed check what version of update-manager-core is installed . I have 1:0.186 and the package manages release upgrades.

---

### Post by NanakiXIII on 2013-05-13
I have the same version, so I guess that's not it.

---

### Post by philinux on 2013-05-13
> **NanakiXIII said:**
> I have the same version, so I guess that's not it.

Just double check this file. It's contents should be as below.

```
cat /etc/lsb-release 
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"

---

### Post by NanakiXIII on 2013-05-13
It looks fine:

```
~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"
```

---

### Post by philinux on 2013-05-13
See this.

[http://askubuntu.com/questions/287939/update-available-message-after-installing-update](http://askubuntu.com/questions/287939/update-available-message-after-installing-update)

---

### Post by NanakiXIII on 2013-05-13
Yup, that did it, thanks for finding that for me!

---

