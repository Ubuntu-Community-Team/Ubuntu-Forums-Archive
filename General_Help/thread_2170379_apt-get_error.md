---
title: "apt-get error"
date: 2013-08-26
forum: General Help
---

### Post by joewbarber on 2013-08-26
I tried to install the NCurses64 library for my GCC compiler through Gnome Terminal on Ubuntu 13.04.
There was an error message and then it removed a load of programs, including GCC & G++.
Now every time I try to run the 'apt-get install' command in Terminal I get this message

joe@Ubuntu-Lenovo:~$ sudo apt-get install gcc
[sudo] password for joe:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
gcc : Depends: gcc-4.7 (>= 4.7.3-1~) but it is not going to be installed
lib64ncurses5-dev:i386 : Depends: lib64c-dev:i386
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
joe@Ubuntu-Lenovo:~$

When I run the command 'sudo apt-get -f install' Terminal lists a load of packages and then asks me whether I want to install them or not,
now instead of installing them it says this:

After this operation, 9,552 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 315277 files and directories currently installed.)
Unpacking libc6-dev-amd64 (from .../libc6-dev-amd64_2.17-0ubuntu5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libc6-dev-amd64_2.17-0ubuntu5_i386.deb (--unpack):
trying to overwrite '/usr/include/gnu', which is also in package libc6-dev-i386 2.17-0ubuntu5
No apport report written because MaxReports has already been reached
Errors were encountered while processing:
/var/cache/apt/archives/libc6-dev-amd64_2.17-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe@Ubuntu-Lenovo:~$

I've rebooted twice and tried various things, if I don't get a solution soon I'm going to reinstall Ubuntu as I'm getting really pissed off
with not being able to use my system properly. I'm also getting a lot more program and system failures than I normally do.

I'm in the middle of a big programming project and I can't compile my code because I don't have a compiler, I'm not installing a
different one; GCC is the best one. Does anyone have a solution on how to fix these issues? Thanks

---

### Post by ian-weisser on 2013-08-26
> **joewbarber said:**
> 
After this operation, 9,552 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 315277 files and directories currently installed.)
[COLOR=#ff0000]Unpacking libc6-dev-amd64[/COLOR] (from .../libc6-dev-amd64_2.17-0ubuntu5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libc6-dev-amd64_2.17-0ubuntu5_i386.deb (--unpack):
trying to overwrite '/usr/include/gnu', which is also in package[COLOR=#ff0000] libc6-dev-i386 2.17-0ubuntu5[/COLOR]
No apport report written because MaxReports has already been reached
Errors were encountered while processing:
/var/cache/apt/archives/libc6-dev-amd64_2.17-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Seems like you have an architecture mismatch.
You are trying to install an amd64-specific package over an existing i386-specific package.
If you have an x86 system, then purge the amd64 library(ies).

---

