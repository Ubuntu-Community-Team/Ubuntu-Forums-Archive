---
title: "error when trying to install updates"
date: 2024-03-05
forum: General Help
---

### Post by guine on 2024-03-05
I've been getting this error when trying to update packages recently
```
The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

linux-tools-6.5.0-21: Depends: libcap2 (>= 1:2.10) but 1:2.66-4ubuntu1 is installed
                      Depends: libpci3 (>= 1:3.8.0) but 1:3.10.0-2 is installed
                      Depends: libudev1 (>= 183) but 253.5-1ubuntu6.1 is installed
                      Depends: zlib1g (>= 1:1.2.3.3) but 1:1.2.13.dfsg-1ubuntu5 is installed
                      Depends: linux-tools-common but it is not installed
```

I've tried reverting back on the selected repositories just in case I had any 3rd party repositories installed with no luck and also tried to install linux-tools-common but get this error 
```
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-tools-common_6.5.0-21.21_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Any ideas on how to fix this. The error with updating came not long after installing at least some of if not all of the listed packages for running some checks with -d perf over the weekend so I'm not sure if uninstalling any of those would be helpful and/or a good idea no that I got that issue straightened out.

---

### Post by Bashing-om on 2024-03-05
guine - hummmmm ....

Something here not adding up
As I get on my 22.04 install:
> 
sysop@x2204mini:~$ apt search linux-tools-6.5.0-21
Sorting... Done
Full Text Search... Done
linux-hwe-6.5-tools-6.5.0-21/jammy-security,jammy-updates 6.5.0-21.21~22.04.1 amd64
  Linux kernel version specific tools for version 6.5.0-21

linux-lowlatency-hwe-6.5-tools-6.5.0-21/jammy-security,jammy-updates 6.5.0-21.21.1~22.04.1 amd64
  Linux kernel version specific tools for version 6.5.0-21

linux-tools-6.5.0-21-generic/jammy-security,jammy-updates 6.5.0-21.21~22.04.1 amd64
  Linux kernel version specific tools for version 6.5.0-21

linux-tools-6.5.0-21-lowlatency/jammy-security,jammy-updates 6.5.0-21.21.1~22.04.1 amd64
  Linux kernel version specific tools for version 6.5.0-21

sysop@x2204mini:~$

//

sysop@x2204mini:~$ dpkg -l linux-tools-common
dpkg-query: no packages found matching linux-tools-common
sysop@x2204mini:~$


What release are we working with in your case ?
show us:
```

lsb_release -a

```

So, what do you show instead:
```

apt policy linux-tools-6.5.0-21 libcap2 linux-tools-common

```

We see what it will take to make the package manager happy.

[INDENT]it's all in the process
[/INDENT]

---

### Post by guine on 2024-03-05
I'm on 23.10. For the second one I got this
```
linux-tools-6.5.0-21:
  Installed: 6.5.0-21.21
  Candidate: 6.5.0-21.21
  Version table:
 *** 6.5.0-21.21 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main amd64 Packages
        100 /var/lib/dpkg/status
libcap2:
  Installed: 1:2.66-4ubuntu1
  Candidate: 1:2.66-4ubuntu1
  Version table:
 *** 1:2.66-4ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic/main amd64 Packages
        100 /var/lib/dpkg/status
linux-tools-common:
  Installed: (none)
  Candidate: 6.5.0-21.21
  Version table:
     6.5.0-21.21 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main i386 Packages
     6.5.0-17.17 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main i386 Packages
     6.5.0-15.15 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main i386 Packages
     6.5.0-14.14 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main i386 Packages
     6.5.0-13.13 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main i386 Packages
     6.5.0-10.10 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security/main i386 Packages
     6.5.0-9.9 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic/main i386 Packages
```

---

### Post by Bashing-om on 2024-03-05
guine --

So far so good;
so what results:
```

sudo apt install linux-tools-common
sudo apt update
sudo apt upgrade

```

[INDENT]maybe - as simple as this
[/INDENT]

---

### Post by guine on 2024-03-05
I got this
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  linux-tools-common
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
3 not fully installed or removed.
Need to get 0 B/485 kB of archives.
After this operation, 583 kB of additional disk space will be used.
(Reading database ... 254934 files and directories currently installed.)
Preparing to unpack .../linux-tools-common_6.5.0-21.21_all.deb ...
Unpacking linux-tools-common (6.5.0-21.21) ...
dpkg: error processing archive /var/cache/apt/archives/linux-tools-common_6.5.0-21.21_all.deb (--unpack):
 trying to overwrite '/usr/bin/cpupower', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-tools-common_6.5.0-21.21_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Hit:1 http://security.ubuntu.com/ubuntu mantic-security InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu mantic InRelease                                       
Get:3 http://us.archive.ubuntu.com/ubuntu mantic-updates InRelease [109 kB]   
Hit:4 https://dl.google.com/linux/chrome/deb stable InRelease                            
Hit:5 http://us.archive.ubuntu.com/ubuntu mantic-backports InRelease                     
Get:6 http://us.archive.ubuntu.com/ubuntu mantic-updates/multiverse Translation-en [2,792 B]
Hit:7 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease                                      
Fetched 111 kB in 2s (56.2 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
9 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-tools-6.5.0-21 : Depends: linux-tools-common but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```
so I went ahead and tried apt --fix-broken install and got this
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-tools-common
The following NEW packages will be installed:
  linux-tools-common
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
3 not fully installed or removed.
Need to get 0 B/485 kB of archives.
After this operation, 583 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 254934 files and directories currently installed.)
Preparing to unpack .../linux-tools-common_6.5.0-21.21_all.deb ...
Unpacking linux-tools-common (6.5.0-21.21) ...
dpkg: error processing archive /var/cache/apt/archives/linux-tools-common_6.5.0-21.21_all.deb (--unpack):
 trying to overwrite '/usr/bin/cpupower', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-tools-common_6.5.0-21.21_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2024-03-05
guine; Hummmm ...

Right off hand I would think that what we have here is a conflict in installed packages.
As I do not have a Mantic install handy - check for us:
```

apt show linux-tools-common linux-laptop-tools-common

```

are both needed ?
and let us consider removing the conflict before resorting to opening a bug report for a packaging error.

[INDENT]sometimes I wonder
[INDENT][INDENT]othertimes I just do not know[/INDENT][/INDENT][/INDENT]

---

### Post by guine on 2024-03-06
This is what I got
P```
ackage: linux-tools-common
Version: 6.5.0-25.25
Priority: optional
Section: kernel
Source: linux
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 628 kB
Provides: bpftool
Depends: lsb-release, hwdata
Download-Size: 529 kB
APT-Sources: [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

N: Unable to locate package linus-laptop-tools-common
N: Unable to locate package linus-laptop-tools-common
N: There are 7 additional records. Please use the '-a' switch to see them.
```

---

### Post by Bashing-om on 2024-03-06
guine; Hey hey

> 
N: Unable to locate package linus-laptop-tools-common

typo - should be as linux-laptop-tools-common "ux" instead of "us".

Try again and we

[INDENT]carry on
[/INDENT]

---

### Post by guine on 2024-03-06
Whoops, guess I had peanuts on my mind
```
Package: linux-tools-common
Version: 6.5.0-25.25
Priority: optional
Section: kernel
Source: linux
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 628 kB
Provides: bpftool
Depends: lsb-release, hwdata
Download-Size: 529 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

Package: linux-laptop-tools-common
Version: 6.5.0-1006.9
Priority: optional
Section: kernel
Source: linux-laptop
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 547 kB
Provides: bpftool
Depends: lsb-release
Download-Size: 450 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

N: There are 9 additional records. Please use the '-a' switch to see them.
```

Then with tossing a -a at the end I got all of this as well
```
Package: linux-tools-common
Version: 6.5.0-25.25
Priority: optional
Section: kernel
Source: linux
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 628 kB
Provides: bpftool
Depends: lsb-release, hwdata
Download-Size: 529 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

Package: linux-tools-common
Version: 6.5.0-21.21
Priority: optional
Section: kernel
Source: linux
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 583 kB
Provides: bpftool
Depends: lsb-release, hwdata
Download-Size: 485 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

Package: linux-tools-common
Version: 6.5.0-17.17
Priority: optional
Section: kernel
Source: linux
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 583 kB
Provides: bpftool
Depends: lsb-release, hwdata
Download-Size: 484 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

Package: linux-tools-common
Version: 6.5.0-15.15
Priority: optional
Section: kernel
Source: linux
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 550 kB
Provides: bpftool
Depends: lsb-release, hwdata
Download-Size: 452 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

Package: linux-tools-common
Version: 6.5.0-14.14
Priority: optional
Section: kernel
Source: linux
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 550 kB
Provides: bpftool
Depends: lsb-release, hwdata
Download-Size: 452 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

Package: linux-tools-common
Version: 6.5.0-13.13
Priority: optional
Section: kernel
Source: linux
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 549 kB
Provides: bpftool
Depends: lsb-release
Download-Size: 450 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

Package: linux-tools-common
Version: 6.5.0-10.10
Priority: optional
Section: kernel
Source: linux
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 549 kB
Provides: bpftool
Depends: lsb-release
Download-Size: 450 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

Package: linux-tools-common
Version: 6.5.0-9.9
Priority: optional
Section: kernel
Source: linux
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 548 kB
Provides: bpftool
Depends: lsb-release
Download-Size: 450 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

Package: linux-laptop-tools-common
Version: 6.5.0-1006.9
Priority: optional
Section: kernel
Source: linux-laptop
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 547 kB
Provides: bpftool
Depends: lsb-release
Download-Size: 450 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

Package: linux-laptop-tools-common
Version: 6.5.0-1005.8
Priority: optional
Section: kernel
Source: linux-laptop
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 546 kB
Provides: bpftool
Depends: lsb-release
Download-Size: 449 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

Package: linux-laptop-tools-common
Version: 6.5.0-1004.7
Priority: optional
Section: kernel
Source: linux-laptop
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 546 kB
Provides: bpftool
Depends: lsb-release
Download-Size: 449 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic/main amd64 Packages
Description: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.

```

---

### Post by Bashing-om on 2024-03-06
guine; Uh Huh

Appears that linux-tools-common and linux-laptop-tools-common provide the same functionality.
May I suggest that "linux-laptop-tools-common" be purged as seems the packaging here prevents the completion of inux-tools-common installing.

[INDENT]seems reasonable to me
[/INDENT]

---

### Post by guine on 2024-03-06
for apt-get purge I got this 
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-tools-6.5.0-21 : Depends: linux-tools-common but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```
so I tried the apt --fix-broken install and got this
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-tools-common
The following NEW packages will be installed:
  linux-tools-common
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
3 not fully installed or removed.
Need to get 529 kB of archives.
After this operation, 628 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 linux-tools-common all 6.5.0-25.25 [529 kB]
Fetched 529 kB in 1s (987 kB/s)            
(Reading database ... 254934 files and directories currently installed.)
Preparing to unpack .../linux-tools-common_6.5.0-25.25_all.deb ...
Unpacking linux-tools-common (6.5.0-25.25) ...
dpkg: error processing archive /var/cache/apt/archives/linux-tools-common_6.5.0-
25.25_all.deb (--unpack):
 trying to overwrite '/usr/bin/cpupower', which is also in package linux-laptop-
tools-common 6.5.0-1006.9
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-tools-common_6.5.0-25.25_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2024-03-06
guine -

The above result from:
```

sudo apt --purge remove linux-laptop-tools-common

```
??

[INDENT]look'n for a reason
[/INDENT]

---

### Post by guine on 2024-03-06
I didn't do it with remove the first time, but with that I got this again
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-tools-6.5.0-21 : Depends: linux-tools-common but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

---

### Post by Bashing-om on 2024-03-06
guine; Ouch

I am aware that we can drop down to the dpkg level and  "force" - I would welcome a 2nd opinion here and a more elegant solution.
But - as I expect- do we get the same result:
```

sudo apt update
sudo apt -f install

```

[INDENT]big hammer time ?
[/INDENT]

---

### Post by guine on 2024-03-06
Yeah, get an error with that as well.
```
Hit:1 http://us.archive.ubuntu.com/ubuntu mantic InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu mantic-updates InRelease             
Hit:3 http://us.archive.ubuntu.com/ubuntu mantic-backports InRelease           
Hit:4 http://security.ubuntu.com/ubuntu mantic-security InRelease              
Hit:5 https://dl.google.com/linux/chrome/deb stable InRelease                 
Hit:6 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
18 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-tools-common
The following NEW packages will be installed:
  linux-tools-common
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
3 not fully installed or removed.
Need to get 0 B/529 kB of archives.
After this operation, 628 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 254934 files and directories currently installed.)
Preparing to unpack .../linux-tools-common_6.5.0-25.25_all.deb ...
Unpacking linux-tools-common (6.5.0-25.25) ...
dpkg: error processing archive /var/cache/apt/archives/linux-tools-common_6.5.0-
25.25_all.deb (--unpack):
 trying to overwrite '/usr/bin/cpupower', which is also in package linux-laptop-
tools-common 6.5.0-1006.9
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-tools-common_6.5.0-25.25_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2024-03-06
guine - Uh Huh

As expected.

Let's wait for others to inspect this as I do not feel all that comfortable swinging a big hammer on some one else's system.
Hope for a better way in which to break the round robin.

[INDENT]A know-it-all I am not
[/INDENT]

---

### Post by Bashing-om on 2024-03-07
guine' ---

As to this time no other has chimed in I have taken the liberty to ping one I trust. Presently off-line so may be a while getting onto us.

Cheers

---

### Post by guine on 2024-03-07
Thanks for the help and no worry on a wait.

---

### Post by ian-weisser on 2024-03-08
Hmmm.

The versions are appropriate. It's not an arch conflict. The control files don't have 'breaks' (which they seemingly should when both provide the same file).

I think we need a kernel pro to help us understand this.

---

### Post by #&amp;thj^% on 2024-03-08
I'm not afraid of swinging big hammers, but you should be...before trying my suggestion you should first have good back-ups.

```

sudo dpkg -i --force-overwrite  /var/cache/apt/archives/linux-tools-common_6.5.0-25.25_all.deb
```
Maybe run a simulation first, I trust you know how, if not just ask.

---

### Post by guine on 2024-03-08
I've never done a simulation before, how do I do that?

---

### Post by #&amp;thj^% on 2024-03-08
just add a "-s" flag to the end:
```
sudo dpkg -i --force-overwrite  /var/cache/apt/archives/linux-tools-common_6.5.0-25.25_all.deb -s
```
Or this works as well "--dry-run"
I'm curious to see how this turns out.

---

### Post by guine on 2024-03-08
with the -s I got this
```
dpkg: error: cannot access archive '-s': No such file or directory
```
and with the --dry-run I got this
```
dpkg: error: cannot access archive '--dry-run': No such file or directory
```

---

### Post by Bashing-om on 2024-03-08
guine;

Humm ^^ kinda odd result
How about moving the --dry-run switch ?
```

sudo dpkg -i --force-overwrite --dry-run /var/cache/apt/archives/linux-tools-common_6.5.0-25.25_all.deb

```

[INDENT]nother case of wonderment
[/INDENT]

---

### Post by guine on 2024-03-09
That way I got this 
```
(Reading database ... 254934 files and directories currently installed.)
Preparing to unpack .../linux-tools-common_6.5.0-25.25_all.deb ...
```

---

### Post by #&amp;thj^% on 2024-03-09
Looks good to go now, just remove the "-s flag" and let it rip.
I'll be online for a short time today, so I'll keep my eye on this thread.

---

### Post by guine on 2024-03-09
I got this when running sudo dpkg -i --force-overwrite  /var/cache/apt/archives/linux-tools-common_6.5.0-25.25_all.deb
```
(Reading database ... 254934 files and directories currently installed.)
Preparing to unpack .../linux-tools-common_6.5.0-25.25_all.deb ...
Unpacking linux-tools-common (6.5.0-25.25) ...
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/bin/cpupower', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/bin/perf', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/bin/turbostat', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/bin/usbip', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/bin/usbipd', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/bin/x86_energy_perf_policy', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/sbin/bpftool', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/bash-completion/completions/bpftool', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/cpupower-frequency-info.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/cpupower-frequency-set.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/cpupower-idle-info.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/cpupower-idle-set.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/cpupower-info.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/cpupower-monitor.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/cpupower-powercap-info.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/cpupower-set.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/cpupower.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-annotate.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-archive.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-arm-spe.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-bench.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-buildid-cache.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-buildid-list.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-c2c.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-config.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-daemon.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-data.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-diff.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-dlfilter.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-evlist.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-ftrace.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-help.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-inject.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-intel-pt.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-iostat.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-kallsyms.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-kmem.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-kvm.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-kwork.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-list.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-lock.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-mem.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-probe.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-record.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-report.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-sched.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-script-perl.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-script-python.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-script.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-stat.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-test.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-timechart.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-top.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-trace.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf-version.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/perf.1.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/usbip.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man1/usbipd.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/bpftool-btf.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/bpftool-cgroup.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/bpftool-feature.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/bpftool-gen.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/bpftool-iter.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/bpftool-link.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/bpftool-map.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/bpftool-net.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/bpftool-perf.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/bpftool-prog.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/bpftool-struct_ops.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/bpftool.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/turbostat.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/man/man8/x86_energy_perf_policy.8.gz', which is also in package linux-laptop-tools-common 6.5.0-1006.9
dpkg: dependency problems prevent configuration of linux-tools-common:
 linux-tools-common depends on hwdata; however:
  Package hwdata is not configured yet.

dpkg: error processing package linux-tools-common (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.11.2-3) ...
Errors were encountered while processing:
 linux-tools-common

```

---

### Post by #&amp;thj^% on 2024-03-09
Ok now run and show
EDIT I forgot this:
```
sudo apt clean
```
```
sudo apt install -f 
```
and 
```
sudo dpkg --configure -a
```

---

### Post by guine on 2024-03-09
after sudo -apt install -f I got
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up hwdata (0.374-1) ...
Setting up linux-tools-common (6.5.0-25.25) ...
Setting up linux-tools-6.5.0-21 (6.5.0-21.21) ...
Setting up linux-tools-6.5.0-21-generic (6.5.0-21.21) ...
```
for the other 2 it just nothing popped up, it just went to letting me enter the next command

---

### Post by guine on 2024-03-09
And after running those 3 commands I noticed that the updater error was gone so I tried running software updater and I was able to install updates again and after 2 rounds of updates and a restart I've got all the main updates installed with the exception of darktable, firefox, and snapstore(darktable hasn't wanted to update for a while, the other 2 are more recent with the current update issues, I'm pretty certain the darktable install that wants to update is the .deb version and I switched to the snap version earlier this year to get the new version when it wouldn't update so thats not a huge priority for me).

---

### Post by Bashing-om on 2024-03-09
guine -

"sudo dpkg --configure -a" returns directly to prompt is a good thing - >> dpkg finds nothing to complain about.

so, what shows now:
```

sudo apt update
sudo apt upgrade

```

[INDENT]dpkg did what dpkg does
[/INDENT]

---

### Post by guine on 2024-03-10
for update I got 
```
Hit:1 http://us.archive.ubuntu.com/ubuntu mantic InRelease
Hit:2 http://security.ubuntu.com/ubuntu mantic-security InRelease              
Hit:3 http://us.archive.ubuntu.com/ubuntu mantic-updates InRelease             
Hit:4 http://us.archive.ubuntu.com/ubuntu mantic-backports InRelease           
Hit:5 https://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:6 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease  
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
```
and upgrade I got
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  dpkg dpkg-dev libdpkg-perl
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,814 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 dpkg amd64 1.22.0ubuntu1.1 [1,392 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 dpkg-dev all 1.22.0ubuntu1.1 [1,137 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu mantic-updates/main amd64 libdpkg-perl all 1.22.0ubuntu1.1 [285 kB]
Fetched 2,814 kB in 1s (5,515 kB/s)    
(Reading database ... 254946 files and directories currently installed.)
Preparing to unpack .../dpkg_1.22.0ubuntu1.1_amd64.deb ...
Unpacking dpkg (1.22.0ubuntu1.1) over (1.22.0ubuntu1) ...
Setting up dpkg (1.22.0ubuntu1.1) ...
(Reading database ... 254946 files and directories currently installed.)
Preparing to unpack .../dpkg-dev_1.22.0ubuntu1.1_all.deb ...
Unpacking dpkg-dev (1.22.0ubuntu1.1) over (1.22.0ubuntu1) ...
Preparing to unpack .../libdpkg-perl_1.22.0ubuntu1.1_all.deb ...
Unpacking libdpkg-perl (1.22.0ubuntu1.1) over (1.22.0ubuntu1) ...
Setting up libdpkg-perl (1.22.0ubuntu1.1) ...
Setting up dpkg-dev (1.22.0ubuntu1.1) ...
Processing triggers for man-db (2.11.2-3) ...
```
and now according to software updater everything is up to date, software thinks there are updates for darktable, firefox, and snap store, and ubuntu software for thinks there are updates for darktable and snap store. With software if I try to update it initially starts to try to update with a progress bar popping up for installing that gets all the way across but then it just stops and goes back to the main update screen showing the same 3 updates available, with ubuntu software it gives me this message
```
Unable to install updates:
(null): cannot refresh "snap-store":snap "snap-store" has running apps (ubuntu-software), pids: 2940
```

---

### Post by #&amp;thj^% on 2024-03-10
I'mi not sure if those are held packages, or not but show us this now:
```
snap-store --quit && sudo snap refresh snap-store

```

---

### Post by guine on 2024-03-10
In terminal I got this
```
snap-store 41.3-77-g7dc86c8 from Canonical&#10003; refreshed
```
In software thinks it still shows updates for darktable, firefox, and snap store while ubuntu software only shows an update for darktable now.

---

