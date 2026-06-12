---
title: "Lubuntu automatically closing programs when locking computer"
date: 2014-04-28
forum: General Help
---

### Post by Numa_slk on 2014-04-28
I have just installed Lubuntu on on my Toshiba Satellite. it works fine. But whenever I lock my laptop pressing ctrl+alt+del and then unlock it, I find that all my opened programs have been closed.   How can I fix this?

~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"
NAME="Ubuntu"
VERSION="14.04, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

---

### Post by bapoumba on 2014-04-28
ctrl-alt-del logs you out of your session (I tried it :p) and ctrl-alt-l the L letter) that is supposed to lock the screen does not work : [https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1286686](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1286686)

---

