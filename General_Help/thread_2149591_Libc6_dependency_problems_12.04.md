---
title: "Libc6 dependency problems 12.04"
date: 2013-05-29
forum: General Help
---

### Post by dmt_z23 on 2013-05-29
Hello everyone, I am new to Ubuntu so I apologise in advance for lack of basic knowledge.The issue is that as soon as I try to install the updates available I get the following message :

installArchives() failed: Error in function: 
SystemError: E:Internal Error, No file name for libc6
dpkg: dependency problems prevent configuration of libc6-dev-i386:
 libc6-dev-i386 depends on libc6-dev (= 2.15-0ubuntu10.4); however:
  Package libc6-dev is not configured yet.
dpkg: error processing libc6-dev-i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libc6 (--configure):
 libc6:amd64 2.15-0ubuntu10.4 cannot be configured because libc6:i386 is in a different version (2.15-0ubuntu10.3)
dpkg: dependency problems prevent configuration of libc-dev-bin:
 libc-dev-bin depends on libc6 (>> 2.15); however:
  Package libc6 is not configured yet.
 libc-dev-bin depends on libc6 (<< 2.16); however:
  Package libc6 is not configured yet.
dpkg: error processing libc-dev-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-i386:
 libc6-i386 depends on libc6 (= 2.15-0ubuntu10.4); however:
  Package libc6 is not configured yet.
dpkg: error processing libc6-i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lib32asound2:
 lib32asound2 depends on libc6-i386 (>= 2.7); however:
  Package libc6-i386 is not configured yet.
dpkg: error processing lib32asound2 (--configure):
 dependency problems - leaving unconfigured

Any ideas what could be happening?

---

### Post by kyutums on 2013-11-02
Try the following commands:
> dpkg -i /var/cache/apt/archives/*.deb
dpkg --configure -a

---

