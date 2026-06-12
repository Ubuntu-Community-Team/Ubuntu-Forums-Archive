---
title: "Redirecting Pointers Noob problem"
date: 2007-02-07
forum: General Help
---

### Post by Tuxgrrrl on 2007-02-07
Greetings ALL.
We need to temporarily redirect Pythons pointer from version 2.4 to version 2.3 and we seem to be doing something wrong. We have read and reread and reread everything we could get on ln and still cant figure it.
This is Edgy6.10, Edu-->Kubuntu.


Python 2.3 is in /usr/local/bin

when given $ ls -l /usr/local/bin/python*
-rwxr-xr-x 2 root root 3002090 2007-02-04 09:56 /usr/local/bin/python
-rwxr-xr-x 2 root root 3002090 2007-02-04 09:56 /usr/local/bin/python2.3

When given
# ls -l /usr/bin/python*
lrwxrwxrwx 1 root root      24 2007-02-04 13:35 /usr/bin/python -> /usr/local/bin/python2.3
-rwxr-xr-x 1 root root 1019680 2006-10-11 14:52 /usr/bin/python2.4
-rwxr-xr-x 1 root root 1145032 2006-10-06 08:23 /usr/bin/python2.5
-rwxr-xr-x 1 root root    1276 2006-10-06 08:23 /usr/bin/python2.5-config
lrwxrwxrwx 1 root root       9 2006-12-02 10:42 /usr/bin/python.orig -> python2.4


BUT...
when given
# dpkg -i cpia-control_0.5.1-2_i386.deb
 ...
dpkg: dependency problems prevent configuration of cpia-control:
 cpia-control depends on python (<< 2.4); however:
  Version of python on system is 2.4.3-11ubuntu3.


Can some kind soul please tell us what we are doing wrong?

Thanks for your time.

---

