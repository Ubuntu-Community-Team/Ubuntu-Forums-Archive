---
title: "&quot;The Package System is Broken&quot;"
date: 2014-04-13
forum: General Help
---

### Post by Jhereg10 on 2014-04-13
I attempted to work about 10 levels above my ability with Ubuntu to install GCC for benchmarking purposes.  In the process of installing GLXOSD something apparently mangled.

Using Sudo apt-get install -f does not repair the situation.

Attempting to remove GCC using Ubuntu One gives me the message that "The Package System is Broken".  I can't install any other packages either, because of the problem. 

Example:
> Sudo apt-get install p7zip-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 glxosd-libs-libsensors-support-i386:i386 : Depends: libsensors4:i386 (>= 1:3.0.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

> The following packages have unmet dependencies:

glxosd-libs-libsensors-support-i386:i386: Depends: glxosd-libs-i386 but it is a virtual package
                                          Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.5 is installed
                                          Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
                                          Depends: libstdc++6 (>= 4.4.0) but 4.6.3-1ubuntu5 is installed
                                          Depends: libsensors4 (>= 1:3.0.0) but 1:3.3.1-2ubuntu1 is installed
> 
It suggests "Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"

I've tried sudo apt-get install -f and it is unable to repair the problem.  

Can anyone give an absolute neophyte a hand here?

---

### Post by Jhereg10 on 2014-04-13
Additional info, I have attempted this:

> sudo apt-get clean
sudo apt-get install -f

Result:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsensors4:i386
Suggested packages:
  lm-sensors:i386
The following NEW packages will be installed:
  libsensors4:i386
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 30.7 kB of archives.
After this operation, 138 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libsensors4 i386 1:3.3.1-2ubuntu1 [30.7 kB]
Fetched 30.7 kB in 0s (120 kB/s)       
(Reading database ... 188631 files and directories currently installed.)
Unpacking libsensors4:i386 (from .../libsensors4_1%3a3.3.1-2ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsensors4_1%3a3.3.1-2ubuntu1_i386.deb (--unpack):
 conffile './etc/sensors.d/.placeholder' is not in sync with other instances of the same package
Errors were encountered while processing:
 /var/cache/apt/archives/libsensors4_1%3a3.3.1-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by Jhereg10 on 2014-04-13
Running:
> 
ls /etc/apt/sources.list.d/

Result was:

> nickguletskii200-glxosd-precise.list  
nickguletskii200-glxosd-precise.list.save

Attempted:
> 
sudo rm /etc/apt/sources.list.d/nickguletskii200*
 sudo apt-get update
 sudo apt-get install p7zip-full

And still the same error.

> Unpacking libsensors4:i386 (from .../libsensors4_1%3a3.3.1-2ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsensors4_1%3a3.3.1-2ubuntu1_i386.deb (--unpack):
 conffile './etc/sensors.d/.placeholder' is not in sync with other instances of the same package
Errors were encountered while processing:

---

