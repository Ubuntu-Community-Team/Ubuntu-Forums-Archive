---
title: "Broken packages, problem with libudev0"
date: 2014-03-07
forum: General Help
---

### Post by sbassi2 on 2014-03-07
[COLOR=#333333][FONT=Ubuntu Mono]I see on synaptic that I have 2 broken packages:

libudev0
and
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]libudev0:i386
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]
So I did an [/FONT][/COLOR]apt-get -f install as recommended in several sites. But it didn't solve my problem, here is the result:[COLOR=#333333][FONT=Ubuntu Mono]

[/FONT][/COLOR]```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-23-generic linux-headers-3.5.0-23 thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libudev-dev libudev0
The following packages will be upgraded:
  libudev-dev libudev0
2 upgraded, 0 newly installed, 0 to remove and 228 not upgraded.
3 not fully installed or removed.
Need to get 0 B/91.4 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: error processing libudev0 (--configure):
 libudev0:amd64 175-0ubuntu9 cannot be configured because libudev0:i386 is in a different version (175-0ubuntu9.4)
dpkg: dependency problems prevent configuration of libudev-dev:
 libudev-dev depends on libudev0 (= 175-0ubuntu9); however:
  Package libudev0 is not configured yet.
dpkg: error processing libudev-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libudev0:i386 (--configure):
 libudev0:i386 175-0ubuntu9.4 cannot be configured because libudev0:amd64 is in a different version (175-0ubuntu9)
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 libudev0
 libudev-dev
 libudev0:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What can I do?

---

### Post by Portaro on 2014-03-07
your system is a 32 bits installation or 64, I think the error reported is generated because the version of packets is for a 64 AMD and you maybe use 32 bits system.

---

