---
title: "Ubuntu 14.04 - Many updates, daily - is it normal?"
date: 2015-05-23
forum: General Help
---

### Post by 9dor on 2015-05-23
Hi,

I'm having many updates, daily, for my Ubuntu 14.04 system.

Is it normal? It started in the last couple of weeks, not sure when.
Some of the updates require a restart, so I guess they are a kernel-related updates.

Here are images of my current system configuration:

"**Ubuntu Software**" tab:
[[IMG]http://s9.postimg.org/hab3elam3/Ubuntu_Software.jpg[/IMG]]("http://postimg.org/image/hab3elam3/")

"**Updates**" tab:
[[IMG]http://s28.postimg.org/6hr5ekiop/Updates.jpg[/IMG]]("http://postimg.org/image/6hr5ekiop/")

"**Other Software**" tab:
[[IMG]http://s11.postimg.org/97exv37j3/Other_Software.jpg[/IMG]]("http://postimg.org/image/97exv37j3/")

* There's also an Authentication tab, but I'm not sure whether I should post it (??)

**The Ubuntu version is:**

```
$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"
NAME="Ubuntu"
VERSION="14.04.2 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.2 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/
```

**System info:** (PC name omitted)
```
$ uname -a
Linux 3.13.0-53-generic #88-Ubuntu SMP Wed May 13 18:10:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

Thank you.

---

### Post by ajgreeny on 2015-05-23
I suggest you enable the partners repository, as I have, and see if that makes any difference to the situation

You will, however, probably be about to get yet another kernel upgrade to **Linux  3.13.0-53-generic #[COLOR=#ff0000]89[/COLOR]-Ubuntu SMP Wed May 20 10:34:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux**, and yes, there do seem to have been a lot of upgrades recently, and more kernels in this 3.13 series than sometimes happens.

Just go with it; so far none of them has caused me any problems.

---

