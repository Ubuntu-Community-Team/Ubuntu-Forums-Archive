---
title: "Error when using apt-get"
date: 2018-01-11
forum: General Help
---

### Post by veths on 2018-01-11
Hello, I am relatively new to Ubuntu and I have recently been encountering an error while using apt-get. Any help would be much appreciated.

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
10 not fully installed or removed.
Need to get 0 B/23.5 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing package libfreerdp-utils1.1:amd64 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of libfreerdp-crypto1.1:amd64:
 libfreerdp-crypto1.1:amd64 depends on libfreerdp-utils1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-utils1.1:amd64 is not configured yet.

dpkg: error processing package libfreerdp-crypto1.1:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfreerdp-locale1.1:amd64:
 libfreerdp-locale1.1:amd64 depends on libfreerdp-utils1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-utils1.1:amd64 is not configured yet.

dpkg: error processing package libfreerdp-locale1.1:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfreerdp-core1.1:amd64:
 libfreerdp-core1.1:amd64 depends on libfreerdp-No apport report written because the error message indicates its a followup error from a previous failure.
            No apport report written because the error message indicates its a followup error from a previous failure.
                                               No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                                       crypto1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-crypto1.1:amd64 is not configured yet.
 libfreerdp-core1.1:amd64 depends on libfreerdp-locale1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-locale1.1:amd64 is not configured yet.
 libfreerdp-core1.1:amd64 depends on libfreerdp-utils1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-utils1.1:amd64 is not configured yet.

dpkg: error processing package libfreerdp-core1.1:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfreerdp-cache1.1:amd64:
 libfreerdp-cache1.1:amd64 depends on libfreerdp-core1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-core1.1:amd64 is not configured yet.

dpkg: error processing package libfreerdp-cache1.1:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfreerdp-client1.1:amd64:
 libfreerdp-client1.1:amd64 depends on libfreerdp-core1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-core1.1:amd64 is not configured yet.
 libfreerdp-client1.1:amd64 depends on libfreerdp-locale1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-locale1.1:amd64 is not configured yet.
 libfreerdp-client1.1:amd64 depends on libfreerdp-utils1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-utils1.1:amd64 is not configured yet.

dpkg: error processing package libfreerdp-client1.1:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfreerdp-gdi1.1:amd64:
 libfreerdp-gdi1.1:amd64 depends on libfreerdp-cache1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-cache1.1:amd64 is not configured yet.
 libfreerdp-gdi1.1:amd64 depends on libfreerdp-core1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-core1.1:amd64 is not configured yet.

dpkg: error processing package libfreerdp-gdi1.1:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfreerdp-plugins-standard:amd64:
 libfreerdp-plugins-standard:amd64 depends on libfreerdp-utils1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-utils1.1:amd64 is not configured yet.

dpkg: error processing package libfreerdp-plugins-standard:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of remmina-plugin-rdp:
 remmina-plugin-rdp depends on libfreerdp-client1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-client1.1:amd64 is not configured yet.
 remmina-plugin-rdp depends on libfreerdp-core1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-core1.1:amd64 is not configured yet.
 remmina-plugin-rdp depends on libfreerdp-gdi1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-gdi1.1:amd64 is not configured yet.
 remmina-plugin-rdp depends on libfreerdp-locale1.1 (>= 1.1.0~beta1+git20130629); however:
  Package libfreerdp-locale1.1:amd64 is not configured yet.

dpkg: error processing package remmina-plugin-rdp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of remmina-dbg:
 remmina-dbg depends on remmina-plugin-rdp (= 1.1.2-3ubuntu1); however:
  Package remmina-plugin-rdp is not configured yet.

dpkg: error processing package remmina-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libfreerdp-utils1.1:amd64
 libfreerdp-crypto1.1:amd64
 libfreerdp-locale1.1:amd64
 libfreerdp-core1.1:amd64
 libfreerdp-cache1.1:amd64
 libfreerdp-client1.1:amd64
 libfreerdp-gdi1.1:amd64
 libfreerdp-plugins-standard:amd64
 remmina-plugin-rdp
 remmina-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by cruzer001 on 2018-01-11
```
dpkg: error processing package libfreerdp-utils1.1:amd64 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
```

Not seeing this package in our repository.  What version of ubuntu are you running?

```
lsb_release -a
```

And whats your sources look like?

```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/
```

May just try it
```

sudo apt-get install --reinstall PACKAGE_NAME
```

---

### Post by veths on 2018-01-11
Okay after reinstalling libfreerdp-dev and trying to install a program everything worked great. Thanks!

---

