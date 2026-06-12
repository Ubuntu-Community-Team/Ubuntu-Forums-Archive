---
title: "Get code for package updates"
date: 2017-11-11
forum: General Help
---

### Post by iqdesigner on 2017-11-11
Hi

Where I can find information on how I can get code for a new update of a package?
Is there any documentation for that process?

For example, today I get an update for lshw

```
The following packages will be upgraded:
*** lshw ****
....
Unpacking lshw (02.17-1.1ubuntu3.4) over (02.17-1.1ubuntu3.3)

changelog

lshw (02.17-1.1ubuntu3.4) xenial; urgency=medium

  * d/p/fix-segfault-in-privileged-containers.patch:
    Fix lshw crashes with SEGV in privileged containers (LP: #1699161)
    (cherry-picked from EZix upstream commit [7b99d35])

 -- Eric Desrochers <eric.desrochers@canonical.com>  Mon, 30 Oct 2017 07:39:31 -0400

```


How I get the code that fix the latest issue?


Thanks

---

### Post by ajgreeny on 2017-11-11
What command produced that terminal output?

It is not clear what is wrong or what you were doing from your post, so please tell us the whole story with as much information as you can, including your OS details, version and GUI type, ie unity, gnome, xfce, etc etc., and your hardware, as much as you know.

From the version of lshw shown I suspect it is Ubuntu 16.04, but it would be helpful to know as much as you can tell us.

---

### Post by Yellow Pasque on 2017-11-11
You mean like this? [https://launchpadlibrarian.net/343699439/lshw_02.17-1.1ubuntu3.3_02.17-1.1ubuntu3.4.diff.gz](https://launchpadlibrarian.net/343699439/lshw_02.17-1.1ubuntu3.3_02.17-1.1ubuntu3.4.diff.gz)
There is a diff from the previous version on Launchpad on the package page: [https://launchpad.net/ubuntu/+source/lshw](https://launchpad.net/ubuntu/+source/lshw)

---

### Post by ajgreeny on 2017-11-11
Ah! Got it; you are asking about the source code which I can not help with, I'm afraid.

---

### Post by iqdesigner on 2017-11-14
Hi and sorry for the delay!

> **ajgreeny said:**
> What command produced that terminal output?

It is not clear what is wrong or what you were doing from your post, so please tell us the whole story with as much information as you can, including your OS details, version and GUI type, ie unity, gnome, xfce, etc etc., and your hardware, as much as you know.

From the version of lshw shown I suspect it is Ubuntu 16.04, but it would be helpful to know as much as you can tell us.

ajgreeny the output was from apt-get with some modifications to show what I want (code for lshw)

> **Temüjin said:**
> You mean like this? [https://launchpadlibrarian.net/343699439/lshw_02.17-1.1ubuntu3.3_02.17-1.1ubuntu3.4.diff.gz](https://launchpadlibrarian.net/343699439/lshw_02.17-1.1ubuntu3.3_02.17-1.1ubuntu3.4.diff.gz)
There is a diff from the previous version on Launchpad on the package page: [https://launchpad.net/ubuntu/+source/lshw](https://launchpad.net/ubuntu/+source/lshw)

Temüjin, yes this is one way to get the diff. The OS is 16.04 xenial, so it is the correct one.
Does this process supported from shell?

Thanks

---

### Post by Yellow Pasque on 2017-11-14
I think you can use bzr to accomplish what you want, but I'm more familiar with git, so don't have commands to give you off the top of my head.

---

