---
title: "Dependency version mismatch"
date: 2016-01-06
forum: General Help
---

### Post by josopeterson on 2016-01-06
I am facing the same issue as delsdog, but the suggested 'update-clean-reinstall' is not solving the problem.

[EMAIL="user@ubuntu:~$"]user@ubuntu:~$[/EMAIL] sudo apt-get clean linux-generic
[EMAIL="user@ubuntu:~$"]user@ubuntu:~$[/EMAIL] sudo apt-get install --reinstall linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic : Depends: linux-image-generic (= 3.2.0.97.113) but it is not going to be installed
                 Depends: linux-headers-generic (= 3.2.0.97.113) but it is not going to be installed
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.96.112) but 3.2.0.97.113 is to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-96-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[EMAIL="user@ubuntu:~$"]user@ubuntu:~$[/EMAIL] 

Any more suggestions?

---

### Post by ian-weisser on 2016-01-06
josopeterson, look carefully at the error messages.
See how they are related?
The error messages are very helpful.

You seem to have a chain of dependency errors caused by several version mismatches. You must replace all of the mismatched metapackages.
It's exactly like above, with more than one package listed on each line.

Try:
```

sudo apt-get update
sudo apt-get clean linux-image-generic linux-generic-pae linux-image-generic-pae linux-headers-generic-pae
sudo apt-get install --reinstall linux-image-generic linux-generic-pae linux-image-generic-pae linux-headers-generic-pae

```

---

### Post by josopeterson on 2016-01-19
ian-weisser, thanks for the reply
unfortunately the suggestions have not solved the problems
by the way - the output might have changed with new information
are you able to determine if any efforts could be made?

after your suggestions I used 'sudo apt-get -f install' - the output from this is also added.

```
user@ubuntu:~$ sudo apt-get install --reinstall linux-image-generic linux-generic-pae linux-image-generic-pae linux-headers-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-3.2.0-97-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
user@ubuntu:~$
```

```
user@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic-pae linux-headers-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic-pae
2 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,344 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-96-generic-pae; however:
  Package linux-headers-3.2.0-96-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.96.112); however:
  Version of linux-image-generic-pae on system is 3.2.0.97.113.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.96.112); however:
  Package linux-headers-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-headers-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@ubuntu:~$ 
```

---

### Post by Bucky Ball on 2016-01-19
*Posts moved to own thread.*

---

### Post by ian-weisser on 2016-01-19
Any sugestions? Sure, plenty.

First, stop using 'apt-get -f install' at every opportunity.
It does something rather different than you seem to expect. It's completely the wrong tool for your problem.

Are you reading the error messages?
Do you understand what the error message is telling you?

---

### Post by Bucky Ball on 2016-01-19
Which Ubuntu release are you using and are you using a 32 or 64bit machine? Just wondering why you are using the PAE kernel. That is for specific circumstances and takes a bit of jumping through hoops to get installed.

Did you try and install the PAE kernel in a running install???

---

### Post by josopeterson on 2016-01-19
Thanks for your good question - and information. I'll try to answer them.
Regarding 'apt-get -f install' I will follow your advice - just wondering why it turns up.
Yes I read the error message - not understanding them 100% - and I am not experienced to know the huge amount of Linux commands for installing/replacing packages.

I am using an Ubuntu 12.04, 32bit, running i VMware. A copy from a colleague I received in the beginning af 2013. I have not faced any problems during almost three years.

No - I have not played around with installing any PAE kernel. I am following the updates released from on running basis.


Please feel free if you have any questions.

---

### Post by mörgæs on 2016-01-22
> **Bucky Ball said:**
> Just wondering why you are using the PAE kernel. That is for specific circumstances and takes a bit of jumping through hoops to get installed.


I thougth all 32 bits kernel were PAE these days. As far as I know the non-PAE was abandoned years ago.
Please correct me if I overlooked something.

---

### Post by Bucky Ball on 2016-01-22
> **mörgæs said:**
> I thougth all 32 bits kernel were PAE these days. As far as I know the non-PAE was abandoned years ago.
Please correct me if I overlooked something.

I should state what I'm getting at more clearly. Is the OP using a 32bit machine? If not, why the 32bit kernel? If 64bit machine, try the 64bit kernel.

---

### Post by mörgæs on 2016-01-22
Yes, agree.

---

### Post by josopeterson on 2016-01-22
Thanks for info. I am ready to follow your advice.

```
user@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise
user@ubuntu:~$ uname -a
Linux ubuntu 3.2.0-97-generic-pae #137-Ubuntu SMP Thu Dec 17 21:37:53 UTC 2015 i686 i686 i386 GNU/Linux

```

Running on a 64-bit laptop in VMware.
Do you have a good link how to upgrade from 32-bit to 64-bit kernel?

---

### Post by mörgæs on 2016-01-22
There is none. You have to do a fresh install of a 64 bit version.

It will also give you the choice between 14.04.3 and 15.10.

---

### Post by josopeterson on 2016-01-25
Since it is an important tool in my daily work I am not keen on starting from fresh.
Is it possible to force an installation of 3.2.0-95? Or similar?

---

### Post by ian-weisser on 2016-01-25
No. 32-bit and 64-bit binary packages are simply incompatible. Diiferent architectures.
Backup your data, document your customizations.
The installer may preserve your filesystem, but will reinstall every single package.

---

