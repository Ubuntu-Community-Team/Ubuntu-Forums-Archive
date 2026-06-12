---
title: "apt-get install cannot open .deb files, open(2) fails with EPERM"
date: 2014-10-16
forum: General Help
---

### Post by thomas_anderson2 on 2014-10-16
I've been roped into keeping a couple servers running, for which I get Ubuntu LTS primed and ready:
```
Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-24-generic x86_64)
```
On one of those machines, I installed some upgrades and apt-get started spewing errors at me. Sure enough, the upgrades didn't run through and everything was left in a half-done limbo. The "meta-admin" above me took the machine in, saying that some important system packages were broken. Fast-forward by a couple weeks and on to the other machine. My guy wanted Tomcat 7 instead of the installed 6, so I diligently tried to install it, only to be greeted by the very same errors:
```
After this operation, 691 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main libservlet3.0-java all 7.0.52-1ubuntu0.1 [293 kB]
Get:2 http://de.archive.ubuntu.com/ubuntu/ trusty-updates/main libtomcat7-java all 7.0.52-1ubuntu0.1 [3649 kB]
Fetched 3943 kB in 2s (1711 kB/s)        
E: **Could not open file /var/cache/apt/archives/libservlet3.0-java_7.0.52-1ubuntu0.1_all.deb - open (1: Operation not permitted)**
E: Unable to determine file size for fd -1 - fstat (9: Bad file descriptor)
E: Read error - read (9: Bad file descriptor)
E: Internal error, could not locate member control.tar.{gzbz2xzlzma}
E: Prior errors apply to /var/cache/apt/archives/libservlet3.0-java_7.0.52-1ubuntu0.1_all.deb
E: Prior errors apply to /var/cache/apt/archives/libtomcat7-java_7.0.52-1ubuntu0.1_all.deb
debconf: apt-extracttemplates failed: No such file or directory
(Reading database ... 66373 files and directories currently installed.)
Removing tomcat6 (6.0.39-1) ...
 * Stopping Tomcat servlet engine tomcat6                                                                        [ OK ] 
Removing tomcat6-common (6.0.39-1) ...
Removing libtomcat6-java (6.0.39-1) ...
dpkg: warning: while removing libtomcat6-java, directory '/usr/share/tomcat6/lib' not empty so not removed
dpkg-split: error: unable to read part file `/var/cache/apt/archives/libservlet3.0-java_7.0.52-1ubuntu0.1_all.deb': Operation not permitted
dpkg: error processing archive /var/cache/apt/archives/libservlet3.0-java_7.0.52-1ubuntu0.1_all.deb (--unpack):
 subprocess dpkg-split returned error exit status 2
Selecting previously unselected package libtomcat7-java.
(Reading database ... 66229 files and directories currently installed.)
Preparing to unpack .../libtomcat7-java_7.0.52-1ubuntu0.1_all.deb ...
Unpacking libtomcat7-java (7.0.52-1ubuntu0.1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libservlet3.0-java_7.0.52-1ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Now, /var/cache/apt/archives is on / and there seem to be no disk errors (if the SAN the machines are on had such a problem, all (insert preferred place of eternal suffering) would have broken loose by now). The question remains how in the world open(2) would even fail with EPERM, seeing as I seriously doubt "The O_NOATIME flag was specified, but the effective user ID of the caller did  not  match  the owner of the file and the caller was not privileged" is the problem here. Wiping /var/cache/apt did not solve the issue, either (as one might expect). Googling the error turns up nothing and the only explanation for this I could come up with is that the kernel somehow got borked. I sure hope someone can tell me that it's not... :P

Any thoughts? I would appreciate it...

Sincerely,
Thomas Anderson

---

### Post by ian-weisser on 2014-10-16
Perhaps the deb file was corrupted.

Delete the file from /var/cache/apt/archives
Then try again so apt will download a fresh copy.

---

### Post by thomas_anderson2 on 2014-10-16
As I stated in my original post, I already tried removing the cached files, but the problem remained. Both from this and from the "Operation not permitted" message, I surmise that the problem is likely not with the file itsself, but with the mechanisms that spring into action when dpkg tries to access it -- which is what worries me...

---

