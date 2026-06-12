---
title: "FreeNX PPA Repository for Xenial?"
date: 2016-09-09
forum: General Help
---

### Post by snakyjake on 2016-09-09
How do I install FreeNX server on Ubuntu 16.04 Xenial?

I tried following https://help.ubuntu.com/community/FreeNX and https://launchpad.net/~freenx-team/+archive/ubuntu/ppa, but I'm getting errors:

```
W: The repository 'http://ppa.launchpad.net/freenx-team/ppa/[COLOR="#FF0000"]ubuntu xenial Release' does not have a Release file[/COLOR].
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
jake@vb1:~$ sudo apt-get install freenx-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package freenx-server
```

What is the correct repository for Xenial?

---

### Post by dn1987p on 2016-09-09
It looks to me like there is no released package for xenial (at least in your specified PPA). Did you add it via
```
[COLOR=#333333]sudo add-apt-repository ppa:freenx-team/ppa[/COLOR]
```
or manually?

---

### Post by ajgreeny on 2016-09-09
Precise (12.04) was the last version of Ubuntu that the ppa was for 224 weeks ago and there does not appear to be a newer ppa for anything later than 12.04.

---

### Post by oldos2er on 2016-09-09
> **snakyjake said:**
> What is the correct repository for Xenial?

There isn't one, as ajgreeny said. [X2Go]("http://wiki.x2go.org/doku.php") might be a good alternative, but I have no experience with it.

---

### Post by QIII on 2016-09-09
NoMachine is free for personal use (but no longer open source).  NX beats the pants off of any other protocol.

NoMachine comes with a built-in SSH implementation so it is secure out of the box.

---

### Post by snakyjake on 2016-09-09
I'll look at NoMachine.  Looks like I'll have install using a .deb package and not a managed repository.

[https://help.ubuntu.com/community/NomachineNX](https://help.ubuntu.com/community/NomachineNX)

---

### Post by QIII on 2016-09-09
That's very old and version 3.5 is not available.

Check out [https://www.nomachine.com/](https://www.nomachine.com/)

---

### Post by HhtFBFn on 2017-07-12
X2Go is a good NoMachine fork if you're happy with an older-style desktop like XFCE. (Some modern effects don't work through it.) It runs over SSH, which the current free NoMachine 5 doesn't. It's an update from the old NoMachine 3. [http://wiki.x2go.org/doku.php](http://wiki.x2go.org/doku.php)

---

### Post by QIII on 2017-07-12
Nomachine NX implements a proprietary secure protocol.  And it can also be tunnelled over SSH, which is supported OOTB.

---

