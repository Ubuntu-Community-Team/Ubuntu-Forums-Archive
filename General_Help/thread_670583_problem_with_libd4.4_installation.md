---
title: "problem with libd4.4 installation"
date: 2008-01-17
forum: General Help
---

### Post by zea_ on 2008-01-17
Hi, 

When i try to install anything in my box i get this error message and can't install the software:

```


Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libdb4.4_4.4.20-8.1ubuntu3.1_i386.deb (--unpack):
 files list file for package `hal-info' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libdb4.4_4.4.20-8.1ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Can anybody help me?

 thanks

---

### Post by zea_ on 2008-01-18
After a little visit at the #ubuntu andi5 suggestme to take a look at the file /var/lib/dpkg/info/hal-info.list. I found a very strange last line, formed whit "@^".  i just cut that line and run again apt-get upgrade.

---

