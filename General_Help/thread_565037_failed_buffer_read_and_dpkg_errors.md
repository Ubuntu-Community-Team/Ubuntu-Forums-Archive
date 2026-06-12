---
title: "failed buffer_read and dpkg errors"
date: 2007-10-01
forum: General Help
---

### Post by billybag on 2007-10-01
trying to install azureus using apt-get install azureus

(Reading database ... dpkg: error processing /var/cache/apt/archives/libbcprov-java_1.33-4_all.deb (--unpack):
 failed in buffer_read(fd): files list for package `libcurl3-gnutls': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libbcprov-java_1.33-4_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

i get a similur error when trying to install freeciv through Synapt package manager


EDIT* Hre is the synapt pack man error for freeciv

E: /var/cache/apt/archives/freeciv-data_2.0.8-3_all.deb: failed in buffer_read(fd)

---

### Post by Seisen on 2007-10-01
Open up the terminal and do this```
cd /var/cache/apt/archives/
``` then ```
sudo rm packagename.deb
``` Do that for each file and then run sudo apt-get update and then try to install those files. Let me know if that fixes the problem.

---

### Post by billybag on 2007-10-01
thanks that worked

---

