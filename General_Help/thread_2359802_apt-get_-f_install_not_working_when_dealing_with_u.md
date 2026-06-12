---
title: "apt-get -f install not working when dealing with unmet dependencies"
date: 2017-04-27
forum: General Help
---

### Post by jimheyvo on 2017-04-27
Hello, I have been struggling with resolving an issue regarding unmet dependencies stemming from golang-1.6

At this time I have tried every method for resolving this issue, but am continually met with:

You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 golang-1.6 : Depends: golang-1.6-go (>= 1.6.2-0ubuntu5~16.04.2) but 1.6.2-0ubuntu5~16.04 is installed
E: Unmet dependencies. Try using -f.


and when trying sudo apt-get -f install i am met with:

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  golang-1.6-go
Suggested packages:
  bzr mercurial subversion
The following packages will be upgraded:
  golang-1.6-go
1 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
2 not fully installed or removed.
Need to get 0 B/20.3 MB of archives.
After this operation, 3,072 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 320421 files and directories currently installed.)
Preparing to unpack .../golang-1.6-go_1.6.2-0ubuntu5~16.04.2_amd64.deb ...
Unpacking golang-1.6-go (1.6.2-0ubuntu5~16.04.2) over (1.6.2-0ubuntu5~16.04) ...
dpkg: error processing archive /var/cache/apt/archives/golang-1.6-go_1.6.2-0ubuntu5~16.04.2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/go-1.6/src', which is also in package golang-1.6-race-detector-runtime 0.0+svn252922-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/golang-1.6-go_1.6.2-0ubuntu5~16.04.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

At this point I can no longer install anything via apt-get as I am met with the golang-1.6 error. In addition I cannot download and install any updates via the Ubuntu Software center or Software Updater, as I receive a:

"The package system is broken" dialog box.  

I have tried every possible solution at this point and am losing my mind.  Any idea?

---

### Post by jimheyvo on 2017-04-28
Finally was able to resolve this by -f removing golang-1.6-race-detector runtime.

---

