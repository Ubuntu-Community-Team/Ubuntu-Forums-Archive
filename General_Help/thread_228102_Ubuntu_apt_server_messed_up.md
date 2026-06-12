---
title: "Ubuntu apt server messed up"
date: 2006-08-02
forum: General Help
---

### Post by jordanm on 2006-08-02
This has been going on all day when i do an apt-get update; apt-get upgrade:

Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  libtiff4 libtotem-plparser1 totem-xine totem-xine-firefox-plugin
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1593kB of archives.
After unpacking 2679kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libtiff4 3.7.4-1ubuntu3.2 [462kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libtotem-plparser1 1.4.3-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe totem-xine-firefox-plugin 1.4.3-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe totem-xine 1.4.3-0ubuntu1
  404 Not Found [IP: 146.137.96.7 80]
Fetched 462kB in 14s (32.5kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_1.4.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_1.4.3-0ubuntu1_i386.deb)  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/t/totem/totem-xine-firefox-plugin_1.4.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/t/totem/totem-xine-firefox-plugin_1.4.3-0ubuntu1_i386.deb)  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/t/totem/totem-xine_1.4.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/t/totem/totem-xine_1.4.3-0ubuntu1_i386.deb)  404 Not Found [IP: 146.137.96.7 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


It seems like this kind of stuff happens way too often. If ubuntu wants to compete as a commercial distribution this kind of thing is unacceptable.

---

### Post by taurus on 2006-08-02
Maybe the us.archive.ubuntu.com is down so you need to edit your /etc/apt/sources.list and remove the "us" in front of all the lines in there...

```

sudo gedit /etc/apt/sources.list

```
:rolleyes:

---

### Post by jordanm on 2006-08-02
> **taurus said:**
> Maybe the us.archive.ubuntu.com is down so you need to edit your /etc/apt/sources.list and remove the "us" in front of all the lines in there...

```

sudo gedit /etc/apt/sources.list

``` :rolleyes:

only 3 of the updates are not found and the server responds to a ping, so I suspect it is an issue with the setu pof those files in the mirror rather than the mirror itself being down.

---

### Post by veediot on 2006-08-02
Yep, same thing is happening to me. Although it is only with the libtotem-plparser1 package now, as totem-xine is still listed as 1.4.1 in the repo.

---

### Post by jordanm on 2006-08-03
> **veediot said:**
> Yep, same thing is happening to me. Although it is only with the libtotem-plparser1 package now, as totem-xine is still listed as 1.4.1 in the repo.
For my upgrade, the server was back up a few hours ago. Nonetheless, I think this is a very bad image for Ubuntu to portray given that it is competing for commercial servers and that this happens alot.

---

