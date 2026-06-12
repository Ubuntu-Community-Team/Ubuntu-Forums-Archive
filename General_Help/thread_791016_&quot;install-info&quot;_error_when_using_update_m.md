---
title: "&quot;install-info&quot; error when using update manager"
date: 2008-05-11
forum: General Help
---

### Post by karthikkito on 2008-05-11
I'm getting an error when trying to use the download updates tool.

```
Preconfiguring packages ...
(Reading database ... 132238 files and directories currently installed.)
Preparing to replace util-linux 2.13.1-5ubuntu1 (using .../util-linux_2.13.1-5ubuntu2_i386.deb) ...
install-info: No dir file specified; try --help for more information.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing /var/cache/apt/archives/util-linux_2.13.1-5ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
install-info: unrecognized option `--description=System V interprocess communication facilities'
	Try `install-info --help' for a complete list of options.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/util-linux_2.13.1-5ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up emacsen-common (1.4.17) ...
emacsen-common: Handling install of emacsen flavor emacs
install-info: No dir file specified; try --help for more information.
dpkg: error processing emacsen-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: error processing util-linux (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.


```

I got a similar error when trying to apt-get xemacs; when I go to remove it, I get the following:

```

karthik@deepthought:~$ sudo apt-get remove emacsen-common
[sudo] password for karthik: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emacsen-common is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
karthik@deepthought:~$ sudo apt-get remove emacsen-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emacsen-common is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 0B/440kB of archives.
After this operation, 0B of additional disk space will be used.

(Reading database ... 132223 files and directories currently installed.)
Preparing to replace util-linux 2.13.1-5ubuntu1 (using .../util-linux_2.13.1-5ubuntu1_i386.deb) ...
install-info: No dir file specified; try --help for more information.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing /var/cache/apt/archives/util-linux_2.13.1-5ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
install-info: unrecognized option `--description=System V interprocess communication facilities'
	Try `install-info --help' for a complete list of options.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/util-linux_2.13.1-5ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any thoughts on how I can fix my apt-get and updating?

---

### Post by karthikkito on 2008-05-11
In case anyone else has a similar problem, I was able to fix the issue with the following:

```
sudo su
source ~/.profile 
apt-get upgrade
```

---

### Post by skgforu on 2009-04-15
I am getting similar error.

root@sks:~# apt-get install cutecom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  lrzsz
The following NEW packages will be installed:
  cutecom
0 upgraded, 1 newly installed, 0 to remove and 366 not upgraded.
7 not fully installed or removed.
Need to get 0B/485kB of archives.
After this operation, 180kB of additional disk space will be used.
(Reading database ... 110844 files and directories currently installed.)
Preparing to replace util-linux 2.13.1-5ubuntu1 (using .../util-linux_2.13.1-5ubuntu1_i386.deb) ...
install-info: No dir file specified; try --help for more information.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing /var/cache/apt/archives/util-linux_2.13.1-5ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/util-linux_2.13.1-5ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

source ~/.profile. did not solve error.

can anybody help me to solve this?

---

### Post by skgforu on 2009-04-15
sudo mv /usr/local/bin/install-info /usr/local/bin/install-info-gnu

this will solve this problem.

for more information visit this
[http://naveendageek.blogspot.com/2009/03/install-info-no-dir-file-specified-try.html](http://naveendageek.blogspot.com/2009/03/install-info-no-dir-file-specified-try.html)

---

