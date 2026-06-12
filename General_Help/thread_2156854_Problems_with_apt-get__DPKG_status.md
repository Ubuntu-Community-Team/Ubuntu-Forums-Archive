---
title: "Problems with apt-get / DPKG status"
date: 2013-06-23
forum: General Help
---

### Post by elactic on 2013-06-23
Hi there,

I am having trouble with installing software at the moment.
When I want to install something (inkscape in this example), the result is a huge list of warnings and errors. It became super long, so i put it on pastebin:
[http://pastebin.com/Mm9FbR3w](http://pastebin.com/Mm9FbR3w)
I have been having the long list of warnings for a while, but until now I was was still able to install things...
I tried to fix it but made it worse, unfortunately I cannot remember all the things I did so far so i better not bias you...
It'd be great if you had some ideas.

Best

---

### Post by dino99 on 2013-06-23
start by cleaning the system: clean/autoclean/autoremove/bleachbit
then reconfigure: sudo dpkg-reconfigure -phigh -a
and update again, then : sudo apt-get -f install

---

### Post by elactic on 2013-06-23
Hi, thanks for the quick response!
I did
```

sudo apt-get clean
sudo apt-get autoclean

```
Both without any trouble.
```

sudo apt-get autoremove

```
produced the following:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing libglapi-mesa:amd64 (--configure):
 package libglapi-mesa:amd64 9.1.3-0ubuntu0.3 cannot be configured because libglapi-mesa:i386 is at a different version (9.1.3-0ubuntu0.2)
dpkg: error processing libgl1-mesa-dri:amd64 (--configure):
 package libgl1-mesa-dri:amd64 9.1.3-0ubuntu0.3 cannot be configured because libgl1-mesa-dri:i386 is at a different version (9.1.3-0ubuntu0.2)
dpkg: dependency problems prevent configuration of libgbm1:amd64:
 libgbm1:amd64 depends on libgl1-mesa-dri; however:
  Package libgl1-mesa-dri:amd64 is not configured yet.


dpkg: error processing libgbm1:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libegl1-mesa:amd64:
 libegl1-mesa:amd64 depends on libgbm1 (>= 7.11~1); however:
  Package libgbm1:amd64 is not configured yet.


dpkg: error processing libegl1-mesa:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libegl1-mesa-drivers:amd64:
 libegl1-mesa-drivers:amd64 depends on libegl1-mesa (= 9.1.3-0ubuntu0.3); however:
  Package libegl1-mesa:amd64 is not configured yet.
 libegl1-mesa-drivers:amd64 depends on libgbm1 (>= 7.11~1); however:
  Package libgbm1:amd64 is not configured yet.
 libegl1-mesa-drivers:amd64 depends on libgl1-mesa-dri; however:
  Package libgl1-mesa-dri:amd64 is not configured yet.
 libegl1-mesa-drivers:amd64 depends on libglapi-mesa (= 9.1.3-0ubuntu0.3); however:
  Package libglapi-mesa:amd64 is not configured yet.


dpkg: error processing libegl1-mesa-drivers:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libgl1-mesa-glx:amd64 (--configure):
 package libgl1-mesa-glx:amd64 9.1.3-0ubuntu0.3 cannot be configured because libgl1-mesa-glx:i386 is at a different version (9.1.3-0ubuntu0.2)
dpkg: dependency problems prevent configuration of libgles2-mesa:amd64:
 libgles2-mesa:amd64 depends on libglapi-mesa (= 9.1.3-0ubuntu0.3); however:
  Package libglapi-mesa:amd64 is not configured yet.


dpkg: error processing libgles2-mesa:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxatracker1:amd64:
 libxatracker1:amd64 depends on libgl1-mesa-dri; however:
  Package libgl1-mesa-dri:amd64 is not configured yet.


dpkg: error processing libxatracker1:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgl1-mesa-dev:
 libgl1-mesa-dev depends on libgl1-mesa-glx (= 9.1.3-0ubuntu0.3); however:
  Package libgl1-mesa-glx:amd64 is not configured yet.


dpkg: error processing libgl1-mesa-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Setting up aptitude (0.6.8.1-2ubuntu2) ...
update-alternatives: error: cannot scan directory `/var/lib/dpkg/alternatives': No such file or directory
dpkg: error processing aptitude (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of asymptote:
 asymptote depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.


dpkg: error processing asymptote (--configure):
 dependency problems - leaving unconfigured
Setting up liblapack3 (3.4.2-1~exp3) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            update-alternatives: error: cannot scan directory `/var/lib/dpkg/alternatives': No such file or directory
dpkg: error processing liblapack3 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python-numpy:
 python-numpy depends on liblapack3 | liblapack.so.3 | libatlas3-base; however:
  Package liblapack3 is not configured yet.
  Package liblapack.so.3 is not installed.
  Package liblapack3 which provides liblapack.so.3 is not configured yet.
  Package libatlas3-base is not installed.


dpkg: error processing python-numpy (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 libglapi-mesa:amd64
 libgl1-mesa-dri:amd64
 libgbm1:amd64
 libegl1-mesa:amd64
 libegl1-mesa-drivers:amd64
 libgl1-mesa-glx:amd64
 libgles2-mesa:amd64
 libxatracker1:amd64
 libgl1-mesa-dev
 aptitude
 asymptote
 liblapack3
 python-numpy
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Last but not least
```

sudo dpkg-reconfigure -phigh -a

```
produced
```

/usr/sbin/dpkg-reconfigure: python-central is broken or not fully installed.

```

Edit:
Oh and bleachbit removed a lot of stuff;)

Unfortunately, still no change.
For example

```

johannes@jasper:~$ sudo apt-get -f install 
[sudo] password for johannes: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
13 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing libglapi-mesa:amd64 (--configure):
 package libglapi-mesa:amd64 9.1.3-0ubuntu0.3 cannot be configured because libglapi-mesa:i386 is at a different version (9.1.3-0ubuntu0.2)
dpkg: error processing libgl1-mesa-dri:amd64 (--configure):
 package libgl1-mesa-dri:amd64 9.1.3-0ubuntu0.3 cannot be configured because libgl1-mesa-dri:i386 is at a different version (9.1.3-0ubuntu0.2)
dpkg: dependency problems prevent configuration of libgbm1:amd64:
 libgbm1:amd64 depends on libgl1-mesa-dri; however:
  Package libgl1-mesa-dri:amd64 is not configured yet.


dpkg: error processing libgbm1:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libegl1-mesa:amd64:
 libegl1-mesa:amd64 depends on libgbm1 (>= 7.11~1); however:
  Package libgbm1:amd64 is not configured yet.


dpkg: error processing libegl1-mesa:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libegl1-mesa-drivers:amd64:
 libegl1-mesa-drivers:amd64 depends on libegl1-mesa (= 9.1.3-0ubuntu0.3); however:
  Package libegl1-mesa:amd64 is not configured yet.
 libegl1-mesa-drivers:amd64 depends on libgbm1 (>= 7.11~1); however:
  Package libgbm1:amd64 is not configured yet.
 libegl1-mesa-drivers:amd64 depends on libgl1-mesa-dri; however:
  Package libgl1-mesa-dri:amd64 is not configured yet.
 libegl1-mesa-drivers:amd64 depends on libglapi-mesa (= 9.1.3-0ubuntu0.3); however:
  Package libglapi-mesa:amd64 is not configured yet.


dpkg: error processing libegl1-mesa-drivers:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libgl1-mesa-glx:amd64 (--configure):
 package libgl1-mesa-glx:amd64 9.1.3-0ubuntu0.3 cannot be configured because libgl1-mesa-glx:i386 is at a different version (9.1.3-0ubuntu0.2)
dpkg: dependency problems prevent configuration of libgles2-mesa:amd64:
 libgles2-mesa:amd64 depends on libglapi-mesa (= 9.1.3-0ubuntu0.3); however:
  Package libglapi-mesa:amd64 is not configured yet.


dpkg: error processing libgles2-mesa:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxatracker1:amd64:
 libxatracker1:amd64 depends on libgl1-mesa-dri; however:
  Package libgl1-mesa-dri:amd64 is not configured yet.


dpkg: error processing libxatracker1:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgl1-mesa-dev:
 libgl1-mesa-dev depends on libgl1-mesa-glx (= 9.1.3-0ubuntu0.3); however:
  Package libgl1-mesa-glx:amd64 is not configured yet.


dpkg: error processing libgl1-mesa-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Setting up aptitude (0.6.8.1-2ubuntu2) ...
update-alternatives: error: cannot scan directory `/var/lib/dpkg/alternatives': No such file or directory
dpkg: error processing aptitude (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of asymptote:
 asymptote depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.


dpkg: error processing asymptote (--configure):
 dependency problems - leaving unconfigured
Setting up liblapack3 (3.4.2-1~exp3) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            update-alternatives: error: cannot scan directory `/var/lib/dpkg/alternatives': No such file or directory
dpkg: error processing liblapack3 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-numpy:
 python-numpy depends on liblapack3 | liblapack.so.3 | libatlas3-base; however:
  Package liblapack3 is not configured yet.
  Package liblapack.so.3 is not installed.
  Package liblapack3 which provides liblapack.so.3 is not configured yet.
  Package libatlas3-base is not installed.


dpkg: error processing python-numpy (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-central ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Errors were encountered while processing:
 libglapi-mesa:amd64
 libgl1-mesa-dri:amd64
 libgbm1:amd64
 libegl1-mesa:amd64
 libegl1-mesa-drivers:amd64
 libgl1-mesa-glx:amd64
 libgles2-mesa:amd64
 libxatracker1:amd64
 libgl1-mesa-dev
 aptitude
 asymptote
 liblapack3
 python-numpy
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

