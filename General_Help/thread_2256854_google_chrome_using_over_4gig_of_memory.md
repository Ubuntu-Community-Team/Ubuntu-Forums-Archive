---
title: "google chrome using over 4gig of memory"
date: 2014-12-15
forum: General Help
---

### Post by mcsheffrey on 2014-12-15
Ever since the last software update I did, google chrome starts using all of the memory, and hangs my laptop.
Have to shut it down and retart it to continue, seems to work ok for a little while, then starts again.
Anyone else have thsi problem, I am running  ubuntu 14.04, 64-bit.
Roy

---

### Post by ajgreeny on 2014-12-15
What updates did you install?

If you're not sure run ```
grep -iw upgrade /var/log/dpkg.log.1 /var/log/dpkg.log
``` to show a list of upgraded packagers with the date and versions involved.

---

### Post by mcsheffrey on 2014-12-15
These are the chrome updates:
mcsheffrey@mcsheffrey-Inspiron-1545:~$ grep -iw upgrade /var/log/dpkg.log.1 /var/log/dpkg.log|grep chrome
/var/log/dpkg.log.1:2014-11-02 16:24:34 upgrade google-chrome-stable:amd64 37.0.2062.120-1 38.0.2125.111-1
/var/log/dpkg.log.1:2014-11-26 15:52:12 upgrade google-chrome-stable:amd64 38.0.2125.111-1 39.0.2171.71-1
/var/log/dpkg.log:2014-12-11 12:17:36 upgrade google-chrome-stable:amd64 39.0.2171.71-1 39.0.2171.95-1
mcsheffrey@mcsheffrey-Inspiron-1545:~$ grep -iw upgrade /var/log/dpkg.log.1 /var/log/dpkg.log|grep chrome
/var/log/dpkg.log.1:2014-11-02 16:24:34 upgrade google-chrome-stable:amd64 37.0.2062.120-1 38.0.2125.111-1
/var/log/dpkg.log.1:2014-11-26 15:52:12 upgrade google-chrome-stable:amd64 38.0.2125.111-1 39.0.2171.71-1
/var/log/dpkg.log:2014-12-11 12:17:36 upgrade google-chrome-stable:amd64 39.0.2171.71-1 39.0.2171.95-1

---

### Post by ajgreeny on 2014-12-15
That just shows that chrome updated on Dec 11th.
I was wondering what else you updated on that date, so please run the same command but replace the "grep chrome" with "grep 2014-12-11" so we can see all packages from that update, just in case this is a problem from some other package, eg the new kernel 3.13.0-43.

PS: I'm not saying it is likely to be the new kernel; that is just an example.

---

