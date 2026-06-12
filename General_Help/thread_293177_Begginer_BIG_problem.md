---
title: "Begginer BIG problem"
date: 2006-11-04
forum: General Help
---

### Post by stevand on 2006-11-04
I am getting this message that I do not know how to fix ....

"
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
"


thanks a LOOT

---

### Post by taurus on 2006-11-04
Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo apt-get install -f
```

---

### Post by stevand on 2006-11-04
I got this message

stevand@stevand-desktop:~/Desktop/blitz-0.9$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  cpp-4.0: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is installed
  gcc-4.0: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is installed
  libgcc1: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is installed
  libgfortran0: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is installed
  libstdc++6: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
stevand@stevand-desktop:~/Desktop/blitz-0.9$

I tried several time but always this message pops up

---

### Post by taurus on 2006-11-04
Did you install gcc or build-essential at all?

---

### Post by PriceChild on 2006-11-04
Could you post your sources list please....

---

### Post by stevand on 2006-11-04
I do not know how to get source list

and I tried essential-build ... it gives me the same


sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
  cpp-4.0: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is to be installed
  gcc-4.0: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is to be installed
  libgcc1: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is to be installed
  libgfortran0: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is to be installed
  libstdc++6: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.3-4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by taurus on 2006-11-04
```
more /etc/apt/sources.list
```

---

### Post by stevand on 2006-11-04
here it is 

"
stevand@stevand-desktop:~$ more /etc/apt/sources.list

deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by taurus on 2006-11-04
Okay, try something like these from a terminal!!!

```

sudo aptitude update
sudo aptitude remove build-essential
sudo aptitude install build-essential

```

---

### Post by stevand on 2006-11-04
Great it work I got g++ to work ....

this is what I got .....
still there is some warning that says perl hope that this does not do any harm 





stevand@stevand-desktop:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libc6-dev
The following NEW packages will be automatically installed:
  g++ g++-4.0 libstdc++6-4.0-dev
The following NEW packages will be installed:
  build-essential g++ g++-4.0 libstdc++6-4.0-dev
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6572kB of archives. After unpacking 25.5MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.4-1ubuntu12 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libc6 [2.4-1ubuntu12 (now) -> 2.3.6-0ubuntu20 (dapper)]

Score is -40

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  g++ g++-4.0 libc6-dev libstdc++6-4.0-dev
The following packages will be DOWNGRADED:
  libc6
The following NEW packages will be installed:
  build-essential g++ g++-4.0 libc6-dev libstdc++6-4.0-dev
0 packages upgraded, 5 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 4588kB/11.2MB of archives. After unpacking 25.4MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libc6 2.3.6-0ubuntu20 [4588kB]
Fetched 4588kB in 15s (293kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg - warning: downgrading libc6 from 2.4-1ubuntu12 to 2.3.6-0ubuntu20.
(Reading database ... 138278 files and directories currently installed.)
Preparing to replace libc6 2.4-1ubuntu12 (using .../libc6_2.3.6-0ubuntu20_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: warning - unable to delete old directory `/etc/ld.so.conf.d': Directory not empty
Setting up libc6 (2.3.6-0ubuntu20) ...
Installing new version of config file /etc/init.d/glibc.sh ...

Selecting previously deselected package libc6-dev.
(Reading database ... 138273 files and directories currently installed.)
Unpacking libc6-dev (from .../libc6-dev_2.3.6-0ubuntu20_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up libc6-dev (2.3.6-0ubuntu20) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
stevand@stevand-desktop:~$ g++
g++: no input files
stevand@stevand-desktop:~$



THANKS A LOT THIS IS THE BEST FORUM IN SOLAR SYSTEM

---

### Post by taurus on 2006-11-04
You can remove perl and reinstall it again if you wish...

```
sudo aptitude remove perl
sudo aptitude install perl
```
Otherwise, don't worry about it if it doesn't give you any problem!  ;)

---

### Post by az on 2006-11-04
> **stevand said:**
> 
libc6 [2.4-1ubuntu12 (now) -> 2.3.6-0ubuntu20 (dapper)]


Your whole problem is that you mixed Dapper and Edgy repositories.  That is libc6 from Edgy.

You should not do that.  Make it all-or-nothing.  Either change all your sources to Edgy and keep it that way or don't change at all.

---

