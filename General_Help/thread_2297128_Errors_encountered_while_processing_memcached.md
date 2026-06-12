---
title: "Errors encountered while processing: memcached"
date: 2015-10-01
forum: General Help
---

### Post by deniswsrosa on 2015-10-01
Hi Guys!

Every time that I try to install something I always got the same error in the end of the installation:

Errors were encountered while processing:
 /var/cache/apt/archives/memcached_1.4.14-0ubuntu9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Does anyone know how to solve it? I tried to delete this file, but it does not worked.


Thanks a lot!

---

### Post by deniswsrosa on 2015-10-01
Even when i try ti run

sudo dpkg --remove --force-remove-reinstreq --force-depends memcached

 I get the following error 

invoke-rc.d: initscript memcached, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 64
Errors were encountered while processing:
 memcached



Any ideias?

---

