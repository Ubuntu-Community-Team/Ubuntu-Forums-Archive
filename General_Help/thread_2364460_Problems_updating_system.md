---
title: "Problems updating system"
date: 2017-06-23
forum: General Help
---

### Post by veewee111 on 2017-06-23
Same problem, but not being solved with the same solution.

```
e@e-AY022AA-ABA-p6330f:~$ sudo apt-get update
[sudo] password for e: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Fetched 306 kB in 0s (342 kB/s)                                                
Reading package lists... Done
e@e-AY022AA-ABA-p6330f:~$ sudo apt clean
e@e-AY022AA-ABA-p6330f:~$ sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Fetched 306 kB in 0s (346 kB/s)                                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
e@e-AY022AA-ABA-p6330f:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  hplip-data linux-headers-4.4.0-78 linux-headers-4.4.0-78-generic
  linux-image-4.4.0-78-generic linux-image-extra-4.4.0-78-generic
  python3-notify2 python3-pexpect python3-pil python3-ptyprocess
  python3-renderpm python3-reportlab python3-reportlab-accel
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libperl5.22:i386
The following NEW packages will be installed:
  libperl5.22:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 3,007 kB of archives.
After this operation, 15.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 libperl5.22 i386 5.22.1-9 [3,007 kB]
Fetched 3,007 kB in 0s (3,033 kB/s)         
(Reading database ... 275479 files and directories currently installed.)
Preparing to unpack .../libperl5.22_5.22.1-9_i386.deb ...
Unpacking libperl5.22:i386 (5.22.1-9) ...
dpkg: error processing archive /var/cache/apt/archives/libperl5.22_5.22.1-9_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libperl5.22/changelog.Debian.gz', which is different from other instances of package libperl5.22:i386
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libperl5.22_5.22.1-9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
e@e-AY022AA-ABA-p6330f:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
e@e-AY022AA-ABA-p6330f:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  hplip-data linux-headers-4.4.0-78 linux-headers-4.4.0-78-generic
  linux-image-4.4.0-78-generic linux-image-extra-4.4.0-78-generic
  python3-notify2 python3-pexpect python3-pil python3-ptyprocess
  python3-renderpm python3-reportlab python3-reportlab-accel
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libperl5.22:i386
The following NEW packages will be installed:
  libperl5.22:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3,007 kB of archives.
After this operation, 15.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 275479 files and directories currently installed.)
Preparing to unpack .../libperl5.22_5.22.1-9_i386.deb ...
Unpacking libperl5.22:i386 (5.22.1-9) ...
dpkg: error processing archive /var/cache/apt/archives/libperl5.22_5.22.1-9_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libperl5.22/changelog.Debian.gz', which is different from other instances of package libperl5.22:i386
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libperl5.22_5.22.1-9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
e@e-AY022AA-ABA-p6330f:~$
```

---

### Post by slickymaster on 2017-06-23
Moved to a thread of its own.
 
Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by ian-weisser on 2017-06-23
> **veewee111 said:**
> 
 trying to overwrite shared '/usr/share/doc/libperl5.22/changelog.Debian.gz', which is different from other instances of package libperl5.22:i386


I do not understand why you wish to install multiple instances of perl.
Is that intentional?

---

### Post by veewee111 on 2017-06-23
Not intentional.  Was just trying to follow same solution as the other poster that seemed to have same problem.

---

### Post by ian-weisser on 2017-06-23
Since your problem seems not the same, the first step is for you to undo whatever you did that didn't help.
Failing to clean up before starting a new attempt causes all kinds of problems.

---

### Post by veewee111 on 2017-06-23
OK, how to do that?

---

### Post by ian-weisser on 2017-06-23
We don't know what you did that should be undone.
We were not there.
Only you can tell us that.

Again: Why did you specify that you wanted a 32-bit (i386) version of perl? What were you trying to accomplish? Why did you think 32-bit would get you there?
If you were trying to solve a problem, then what was the problem you were trying to solve?

---

### Post by veewee111 on 2017-06-23
Well did not realize was trying for 32 bit. If had known would have tried for 64 bit.
Initial problem was to get the HP printer working again with the software.  For some reason the software has a history of occasionally deciding to have a CUPS failure.  Then it was to get the printer to print PDF files properly.  Then found the scanner function would not work with the software.  At one point tried to just reload Ubuntu 16.04 via the directions for newbies and right off the bat that did not work.  What responses I was getting back from the software was divergent from the directions.  So it has been several days of trying different solutions.  Then the updating system fails....

---

### Post by ian-weisser on 2017-06-24
Do you have links to these different solutions...particularly the one that suggests you install perl?

---

### Post by veewee111 on 2017-06-24
[https://ubuntuforums.org/showthread.php?t=2360114](https://ubuntuforums.org/showthread.php?t=2360114)

[https://askubuntu.com/questions/901205/package-system-is-broken-16-04](https://askubuntu.com/questions/901205/package-system-is-broken-16-04)

[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

That is the tip of the iceberg of days of stuff tried.  Think at this point it would be easier to dump the whole ubuntu system and reload.

---

