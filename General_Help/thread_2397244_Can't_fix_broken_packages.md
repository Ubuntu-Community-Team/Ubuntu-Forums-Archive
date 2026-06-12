---
title: "Can't fix broken packages"
date: 2018-07-27
forum: General Help
---

### Post by DBQ on 2018-07-27
Hi everyone.

I am having a broken package issue that I cannot seem to fix:

```
After this operation, 7,324 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 python3-lib2to3 all 3.6.5-3 [76.6 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 python3-distutils all 3.6.5-3 [141 kB]
Fetched 217 kB in 0s (1,392 kB/s)          
Extracting templates from packages: 100%
(Reading database ... 404840 files and directories currently installed.)
Removing libdouble-conversion1v5:amd64 (2.0.1-3ubuntu2) ...
Selecting previously unselected package libdouble-conversion1:amd64.
(Reading database ... 404836 files and directories currently installed.)
Preparing to unpack .../libdouble-conversion1_2.0.1-4ubuntu1_amd64.deb ...
Unpacking libdouble-conversion1:amd64 (2.0.1-4ubuntu1) ...
Preparing to unpack .../python3-lib2to3_3.6.5-3_all.deb ...
Unpacking python3-lib2to3 (3.6.5-3) ...
dpkg: error processing archive /var/cache/apt/archives/python3-lib2to3_3.6.5-3_all.deb (--unpack):
 trying to overwrite '/usr/lib/python3.6/lib2to3/Grammar.txt', which is also in package libpython3.6-stdlib:amd64 3.6.5-5~16.04.york1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../python3-distutils_3.6.5-3_all.deb ...
Unpacking python3-distutils (3.6.5-3) ...
dpkg: error processing archive /var/cache/apt/archives/python3-distutils_3.6.5-3_all.deb (--unpack):
 trying to overwrite '/usr/lib/python3.6/distutils/README', which is also in package libpython3.6-stdlib:amd64 3.6.5-5~16.04.york1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python3-lib2to3_3.6.5-3_all.deb
 /var/cache/apt/archives/python3-distutils_3.6.5-3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried using sudo apt-get install -f without avail (the same error just repeats).

Any help is appreciated.

Thanks!

---

### Post by wyliecoyoteuk on 2018-07-27
try sudo dpkg -C
it might give more info

---

### Post by mc4man on 2018-07-27
It appears you upgraded from 16.04 to 18.04 without purging that python 3.6 ppa first. (very bad idea..

So either locate (/var/cache/apt/archives/)  or if not there  download the bionic package (python3-lib2to3_3.6.5-3_all.deb) and install with dpkg i.e
sudo dpkg -i --force-overwrite /path/to/packagename
So you could try 
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/python3-lib2to3_3.6.5-3_all.deb
```
If not found then you'll need to get it from launchpad or reaquire to /var...  (use sudo apt-get upgrade as apt-get caches .debs , apt doesn't.

You should also locate & either replace or remove any other packages from that ppa, noting that some python packages can not be removed without screwing up your install..

---

### Post by poorguy on 2018-07-27
I'd copy and save whatever files and folders needed / wanted and do a clean install.

Just my 2 cents.

---

### Post by DBQ on 2018-07-27
Thank you so much! mc4man, your suggestion helped!

---

