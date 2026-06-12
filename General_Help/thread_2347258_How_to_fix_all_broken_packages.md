---
title: "How to fix all broken packages"
date: 2016-12-23
forum: General Help
---

### Post by horsebox2 on 2016-12-23
When I run ```
apt-get
```, I'm getting a bunch of these kind of messages:



```
dpkg: error processing package r-cran-lattice (--configure): dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-nlme:
 r-cran-nlme depends on r-base-core (>= 3.3.1-1trusty0); however:
  Package r-base-core is not configured yet.
 r-cran-nlme depends on r-api-3; however:
  Package r-api-3 is not installed.
  Package r-base-core which provides r-api-3 is not configured yet.
 r-cran-nlme depends on r-cran-lattice (>= 0.12-11.1); however:
  Package r-cran-lattice is not configured yet.

```

When I run ```
sudo apt-get install -f
```, it tells me that there are: 
> 14 not fully installed or removed.
and they are all these R packages, it lists them at the end:
```
Errors were encountered while processing:
 r-base-core
 r-cran-cluster
 r-cran-foreign
 r-cran-kernsmooth
 r-cran-lattice
 r-cran-nlme
 r-cran-matrix
 r-cran-mgcv
 r-cran-survival
 r-cran-codetools
 r-recommended
 r-base
 r-base-dev
 r-base-html
```
but it doesn't fix anything. All the messages are about one of the dependencies not being configured, heres the full output:
```
**vagrant@lamp:~$ sudo apt-get install -f**Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libntdb1 python-ntdb
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up r-base-core (3.3.2-1trusty0) ...
Preserving user changes to /usr/share/bash-completion/completions/R (renamed from /etc/bash_completion.d/R)...
mv: cannot stat &#8216;/usr/share/bash-completion/completions/R&#8217;: No such file or directory
dpkg: error processing package r-base-core (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of r-cran-cluster:
 r-cran-cluster depends on r-base-core (>= 3.3.1-1trusty0); however:
  Package r-base-core is not configured yet.
 r-cran-cluster depends on r-api-3; however:
  Package r-api-3 is not installed.
  Package r-base-core which provides r-api-3 is not configured yet.


dpkg: error processing package r-cran-cluster (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-foreign:
 r-cran-foreign depends on r-base-core (>= 3.3.1-1trusty0); however:
  Package r-base-core is not configured yet.
 r-cran-foreign depends on r-api-3; however:
  Package r-api-3 is not installed.
  Package r-base-core which provides r-api-3 is not configured yet.


dpkg: error processing package r-cran-foreign (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-kernsmooth:
 r-cran-kernsmooth depends on r-base-core (>= 3.3.1-1trusty0); No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
however:
  Package r-base-core is not configured yet.
 r-cran-kernsmooth depends on r-api-3; however:
  Package r-api-3 is not installed.
  Package r-base-core which provides r-api-3 is not configured yet.


dpkg: error processing package r-cran-kernsmooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-lattice:
 r-cran-lattice depends on r-base-core (>= 3.3.1-1trusty0); however:
  Package r-base-core is not configured yet.
 r-cran-lattice depends on r-api-3; however:
  Package r-api-3 is not installed.
  Package r-base-core which provides r-api-3 is not configured yet.


dpkg: error processing package r-cran-lattice (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-nlme:
 r-cran-nlme depends on r-base-core (>= 3.3.1-1trusty0); however:
  Package r-base-core is not configured yet.
 r-cran-nlme depends on r-api-3; however:
  Package r-api-3 is not installed.
  Package r-base-core which provides r-api-3 is not configured yet.
 r-cran-nlme depends on r-cran-lattice (>= 0.12-11.1); however:
  Package r-cran-lattice is not configured yet.


dpkg: error processing package r-cran-nlme (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-matrix:
 r-cran-matrix depends on r-base-core (>= 3.3.1-1trusty0); however:
  Package r-base-core is not configured yet.
 r-cran-matrix depends on r-api-3; however:
  Package r-api-3 is not installed.
  Package r-base-core which provides r-api-3 is not configured yet.
 r-cran-matrix depends on r-cran-lattice (>= 0.12-11.1); however:
  Package r-cran-lattice is not configured yet.


dpkg: error processing package r-cran-matrix (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-mgcv:
 r-cran-mgcv depends on r-base-core; however:
  Package r-base-core is not configured yet.
 r-cran-mgcv depends on r-cran-nlme; however:
  Package r-cran-nlme is not configured yet.
 r-cran-mgcv depends on r-cran-matrix; however:
  Package r-cran-matrix is not configured yet.


dpkg: error processing package r-cran-mgcv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-survival:
 r-cran-survival depends on r-base-core (>= 3.3.1-1trusty0); however:
  Package r-base-core is not configured yet.
 r-cran-survival depends on r-api-3; however:
  Package r-api-3 is not installed.
  Package r-base-core which provides r-api-3 is not configured yet.
 r-cran-survival depends on r-cran-matrix; however:
  Package r-cran-matrix is not configured yet.


dpkg: error processing package r-cran-survival (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-cran-codetools:
 r-cran-codetools depends on r-base-core; however:
  Package r-base-core is not configured yet.


dpkg: error processing package r-cran-codetools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-recommended:
 r-recommended depends on r-base-core (>= 3.3.2-1trusty0); however:
  Package r-base-core is not configured yet.
 r-recommended depends on r-cran-cluster (>= 1.9.6-2); however:
  Package r-cran-cluster is not configured yet.
 r-recommended depends on r-cran-foreign (>= 0.7-2); however:
  Package r-cran-foreign is not configured yet.
 r-recommended depends on r-cran-kernsmooth (>= 2.2.14); however:
  Package r-cran-kernsmooth is not configured yet.
 r-recommended depends on r-cran-lattice (>= 0.10.11); however:
  Package r-cran-lattice is not configured yet.
 r-recommended depends on r-cran-mgcv (>= 1.1.5); however:
  Package r-cran-mgcv is not configured yet.
 r-recommended depends on r-cran-nlme (>= 3.1.52); however:
  Package r-cran-nlme is not configured yet.
 r-recommended depends on r-cran-survival (>= 2.13.2-1); however:
  Package r-cran-survival is not configured yet.
 r-recommended depends on r-cran-codetools; however:
  Package r-cran-codet
dpkg: error processing package r-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-base:
 r-base depends on r-base-core (>= 3.3.2-1trusty0); however:
  Package r-base-core is not configured yet.
 r-base depends on r-recommended (= 3.3.2-1trusty0); however:
  Package r-recommended is not configured yet.


dpkg: error processing package r-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-base-dev:
 r-base-dev depends on r-base-core (>= 3.3.2-1trusty0); however:
  Package r-base-core is not configured yet.


dpkg: error processing package r-base-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of r-base-html:
 r-base-html depends on r-base-core; however:
  Package r-base-core is not configured yet.


dpkg: error processing package r-base-html (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 r-base-core
 r-cran-cluster
 r-cran-foreign
 r-cran-kernsmooth
 r-cran-lattice
 r-cran-nlme
 r-cran-matrix
 r-cran-mgcv
 r-cran-survival
 r-cran-codetools
 r-recommended
 r-base
 r-base-dev
 r-base-html
E: Sub-process /usr/bin/dpkg returned an error code (1)
vagrant@lamp:~$
```

I didn't install this package myself (I'm using a prebuilt Vagrant VM, R is a programming language, thats all I know about it), so I don't know these packages are all from the same bundle or not. Is there a way to find that out? As in can I find out what the core package is, so I can just run apt-get remove o tahwn it, and try reinstalling it? Additionally, is there a way to fix all unconfigured packages on a mass scale? I remember dpkg being able to do something like this, but I can't remember the command.

---

### Post by cc31296 on 2016-12-23
what shows:
apt-get remove r-cran-lattice

please post the outcome back in this forum.
DO NOT confirm the deletion

---

### Post by ian-weisser on 2016-12-23
> **horsebox2 said:**
> [...]I don't know these packages are all from the same bundle or not. Is there a way to find that out?
apt-cache policy

A quick look indicates to me that they seem to be custom, not standard Ubuntu from the Ubuntu repositories. Without access to where they came from, it may be difficult to reinstall.

But perhaps you don't need to reinstall. Look again at the very first error - the error that prevents r-base-core from configuring:
> **horsebox2 said:**
> Setting up r-base-core (3.3.2-1trusty0) ...
Preserving user changes to /usr/share/bash-completion/completions/R (renamed from /etc/bash_completion.d/R)...
mv: cannot stat ‘/usr/share/bash-completion/completions/R’: **No such file or directory**
dpkg: error processing package r-base-core (--configure):
 subprocess installed post-installation script returned error exit status 1
Perhaps you can simply add a dummy file for the script to detect?



> **horsebox2 said:**
> Additionally, is there a way to fix all unconfigured packages on a mass scale?
Apt is already trying to do this for you. Let it.

---

