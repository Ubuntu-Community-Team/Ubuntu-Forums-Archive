---
title: "Cannot install libc6-dev"
date: 2007-02-07
forum: General Help
---

### Post by djerveren on 2007-02-07
I tried to install the **build-essential** meta package on 6.10, but **libc6-dev** cannot be installed:

```
*daniel@beast:~$ sudo apt-get install build-essential*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
  libstdc++6-4.1-dev: Depends: libc6-dev (>= 2.3.6-7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

So, I did as it asked:

```
*daniel@beast:~$ sudo apt-get -f install*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6-dev
Suggested packages:
  glibc-doc manpages-dev
The following NEW packages will be installed:
  libc6-dev
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
4 not fully installed or removed.
Need to get 0B/1852kB of archives.
After unpacking 8061kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 94926 files and directories currently installed.)
Unpacking libc6-dev (from .../libc6-dev_2.4-1ubuntu12.3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libc6-dev_2.4-1ubuntu12.3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libpthread.a', which is also in package libpthread-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev_2.4-1ubuntu12.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Why is there a conflict between two packages owning the same file? (/usr/lib/libpthread.a) Should I temporary try to uninstall **libpthread-dev**, install **libc6-dev** and then reinstall **libpthread-dev**?

Best regards, /Daniel.

---

### Post by DougieFresh4U on 2007-02-07
maybe try this in terminal code **sudo dpkg --configure -a** don't know if it will help but should finish whatever your last installs were):P

---

### Post by djerveren on 2007-02-07
> **DougieFresh4U said:**
> maybe try this in terminal code **sudo dpkg --configure -a** don't know if it will help but should finish whatever your last installs were):P

Still getting errors:

```
*daniel@beast:~$ sudo dpkg --configure -a*
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on libc6-dev | libc-dev; however:
  Package libc6-dev is not installed.
  Package libc-dev is not installed.
dpkg: error processing build-essential (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libstdc++6-4.1-dev:
 libstdc++6-4.1-dev depends on libc6-dev (>= 2.3.6-7); however:
  Package libc6-dev is not installed.
dpkg: error processing libstdc++6-4.1-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++-4.1:
 g++-4.1 depends on libstdc++6-4.1-dev (= 4.1.1-13ubuntu5); however:
  Package libstdc++6-4.1-dev is not configured yet.
dpkg: error processing g++-4.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.1 (>= 4.1.1-2); however:
  Package g++-4.1 is not configured yet.
dpkg: error processing g++ (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 build-essential
 libstdc++6-4.1-dev
 g++-4.1
 g++
```

So, I tried to configure **g++** manually, but that didn't get me far:

```
*daniel@beast:~$ sudo dpkg --configure g++*
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.1 (>= 4.1.1-2); however:
  Package g++-4.1 is not configured yet.
dpkg: error processing g++ (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g++
```

Open to more suggestions. :)

---

### Post by marshall.robert on 2007-02-11
its only a guess, but you could be missing libc6.dev - i found it here: [http://packages.ubuntu.com/dapper/libdevel/libc6-dev:](http://packages.ubuntu.com/dapper/libdevel/libc6-dev:)) 

-rob xx

---

### Post by naiveman on 2007-04-11
I had this same problem installing "gnucash" from the repositories. I couldn't do no new installations and received a message "Software index is broken".

There is a conflict in packages:

**libpthread-dev** (that was installed in my machine) and **libc6-dev** (that I was trying to install when everything messed up).

My solution was to go into the Synaptic package manager. Search for **libpthread-dev**. Choose to *remove completely* and then apply.

The broken index problem was solved.

---

### Post by zvacet on 2007-04-12
```
sudo apt-cdrom add
```
```
sudo aptitude install build-essential
```

because this package is on CD

---

