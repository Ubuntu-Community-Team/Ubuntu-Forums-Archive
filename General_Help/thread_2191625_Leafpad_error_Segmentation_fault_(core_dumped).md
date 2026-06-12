---
title: "Leafpad error: Segmentation fault (core dumped)"
date: 2013-12-03
forum: General Help
---

### Post by dylan_mulenburg on 2013-12-03
When I try to run Leafpad from the terminal, I get 'Segmentation fault (core dumped)'. If I try to run it from the launch bar nothing happens. I have tried purging/re-installing leafpad, updating/upgrading Lubuntu, and sudo apt-get -f install. I also tried installing an older version of Leafpad. I'm almost positive I've used Leafpad without issue on this computer in the past. I am running Lubuntu 13.04 64-bit with Leafpad version 0.8.18.1-3 . I've done some searching and can't find much other than that someone submitted it as a bug report on launchpad.net. I don't know how else to troubleshoot, especially considering the terminal gives me almost no information, it only returns 'Segmentation fault (core dumped)' when I attempt to run Leafpad. Any suggestions? Thanks.

---

### Post by vasa1 on 2013-12-03
Does all other software run well? Is it only Leafpad that has this problem?

---

### Post by dylan_mulenburg on 2013-12-03
> **vasa1 said:**
> Does all other software run well? Is it only Leafpad that has this problem?  Yes.

---

### Post by Dennis N on 2013-12-04
Here is some information on the segmentation faults:

[http://www.cyberciti.biz/tips/segmentation-fault-on-linux-unix.html](http://www.cyberciti.biz/tips/segmentation-fault-on-linux-unix.html)

A nasty problem and likely hard to resolve. If it is a recurring one, you could use another basic text editor: 

I now prefer **medit** instead of Leafpad (or gedit). It has tabs and colors. It installed on Xubuntu with no additional dependencies not already installed. gedit has a lot of dependencies that come with it on Xubuntu or Lubuntu.

---

### Post by walterorlin on 2013-12-04
Already installed on lubuntu there is the nano text editior but that is terminal based.

---

### Post by dylan_mulenburg on 2013-12-05
Thank you for the replies. One further detail, I tried running leafpad as root (sudo leafpad) and it did not produce the error message, but it still failed to open leafpad, not sure if that means anything.  I just installed medit and it looks great, I'll use that until/unless I get leafpad to work.

---

### Post by childsey01 on 2013-12-05
Following up the bug report is probably the best way to find a solution. As you said segmentation fault really is not that informative. It is a result of the program trying to access memory it shouldn't and the OS stopping it from screwing up the system. If you want to speed up the developers response try gathering more information for them. If you install the debug symbols (on software centre you'll find a lot of packages with -dev, -doc, and -dbg suffixes, iti is the latter that provides the debug information) and then run the software with a debugging program, e.g. (gdb leafpad) it will give you more information. In gdb when you get a seg fault you can then do a backtrace by typing bt. If you attach this information to the bug report it can help identify the exact line of code where the program crashed, helping them to quickly fix it.

---

### Post by dylan_mulenburg on 2013-12-12
> **childsey01 said:**
> Following up the bug report is probably the best way to find a solution. As you said segmentation fault really is not that informative. It is a result of the program trying to access memory it shouldn't and the OS stopping it from screwing up the system. If you want to speed up the developers response try gathering more information for them. If you install the debug symbols (on software centre you'll find a lot of packages with -dev, -doc, and -dbg suffixes, iti is the latter that provides the debug information) and then run the software with a debugging program, e.g. (gdb leafpad) it will give you more information. In gdb when you get a seg fault you can then do a backtrace by typing bt. If you attach this information to the bug report it can help identify the exact line of code where the program crashed, helping them to quickly fix it.

Thank you. Is this correct or do I need to do something more/different?

```
administrator@administrator:~$ gdb leafpad
GNU gdb (GDB) 7.5.91.20130417-cvs-ubuntu
Copyright (C) 2013 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/leafpad...(no debugging symbols found)...done.
(gdb) run
Starting program: /usr/bin/leafpad 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Program received signal SIGSEGV, Segmentation fault.
0x00007ffff629f2e4 in ?? () from /lib/x86_64-linux-gnu/libc.so.6
(gdb) bt
#0  0x00007ffff629f2e4 in ?? () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x000055555555d95e in ?? ()
#2  0x000055555555d3d8 in main ()
(gdb)
```

---

### Post by mörgæs on 2013-12-13
Thanks for considering to report the bug, but first please try the development version (14.04). Might be fixed already.

---

### Post by dylan_mulenburg on 2013-12-13
> **mörgæs said:**
> Thanks for considering to report the bug, but first please try the development version (14.04). Might be fixed already.

Thank you. Where can I find the development version? I checked packages.ubuntu.com and tried installing the latest version, [0.8.18.1-4]("http://packages.ubuntu.com/trusty/leafpad"), I'm not sure if that's what you were referring to, but when I tried to install it, it said that I need two packages that I don't have installed

```
dpkg: dependency problems prevent configuration of leafpad:
 leafpad depends on libpango-1.0-0 (>= 1.14.0); however:
  Package libpango-1.0-0 is not installed.
 leafpad depends on libpangocairo-1.0-0 (>= 1.14.0); however:
  Package libpangocairo-1.0-0 is not installed.
```

And when I tried installing them it said that doing so would break other packages I already have installed. Should I try to find a way around this, and if so do you have any suggestions, or is 0.8.18.1-4 not even the version of Leafpad you were referring to?

Here is all the code (after I purged the existing installation of leafpad) in case I didn't give enough information

Installing the newest version of Leafpad:

```
administrator@administrator:~$ sudo dpkg -i ~/Desktop/leafpad_0.8.18.1-4_amd64.deb
Selecting previously unselected package leafpad.
(Reading database ... 111997 files and directories currently installed.)
Unpacking leafpad (from .../leafpad_0.8.18.1-4_amd64.deb) ...
dpkg: dependency problems prevent configuration of leafpad:
 leafpad depends on libpango-1.0-0 (>= 1.14.0); however:
  Package libpango-1.0-0 is not installed.
 leafpad depends on libpangocairo-1.0-0 (>= 1.14.0); however:
  Package libpangocairo-1.0-0 is not installed.

dpkg: error processing leafpad (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Errors were encountered while processing:
 leafpad
```

Attempting to install the two missing dependencies from the repositories:
```
administrator@administrator:~$ sudo apt-get install --no-install-recommends libpango-1.0-0 libpangocairo-1.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libpango-1.0-0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package libpangocairo-1.0-0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libpango-1.0-0' has no installation candidate
E: Package 'libpangocairo-1.0-0' has no installation candidate
```

Attempting to install the two missing dependencies with dpkg (after downloading files from packages.ubuntu.com)
```
administrator@administrator:~$ cd Desktop
administrator@administrator:~/Desktop$ sudo dpkg -i libpango-1.0-0_1.36.0-1ubuntu2_amd64.deb
Selecting previously unselected package libpango-1.0-0:amd64.
dpkg: regarding libpango-1.0-0_1.36.0-1ubuntu2_amd64.deb containing libpango-1.0-0:amd64:
 libpango-1.0-0 conflicts with plymouth (<< 0.8.8-0ubuntu7)
  plymouth (version 0.8.8-0ubuntu6.2) is present and installed.

dpkg: error processing libpango-1.0-0_1.36.0-1ubuntu2_amd64.deb (--install):
 conflicting packages - not installing libpango-1.0-0:amd64
Errors were encountered while processing:
 libpango-1.0-0_1.36.0-1ubuntu2_amd64.deb
administrator@administrator:~/Desktop$ sudo dpkg -i libpangocairo-1.0-0_1.36.0-1ubuntu2_amd64.deb
Selecting previously unselected package libpangocairo-1.0-0:amd64.
dpkg: regarding libpangocairo-1.0-0_1.36.0-1ubuntu2_amd64.deb containing libpangocairo-1.0-0:amd64:
 libpangocairo-1.0-0 breaks libpango1.0-0 (<< 1.32.5-2)
  libpango1.0-0:amd64 (version 1.32.5-0ubuntu1) is present and installed.

dpkg: error processing libpangocairo-1.0-0_1.36.0-1ubuntu2_amd64.deb (--install):
 installing libpangocairo-1.0-0:amd64 would break libpango1.0-0:amd64, and
 deconfiguration is not permitted (--auto-deconfigure might help)
Errors were encountered while processing:
 libpangocairo-1.0-0_1.36.0-1ubuntu2_amd64.deb
```


Also, if it turns out that this does not work, is the information in my last post the correct information to include in a bug report, and who should I send it to?

---

### Post by mörgæs on 2013-12-13
[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

---

### Post by dylan_mulenburg on 2013-12-19
> **mörgæs said:**
> [http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

Thanks. I tried that and Leafpad works fine. Leafpad even works when I boot Lubuntu 13.04 from CD (the same distro and release that I have installed on my HDD), it's only when I boot from my HDD that I have the issue. I'm going to reinstall my OS soon, I'll see if that fixes it. Is this something I should still submit a bug report for? If so, who should I submit it to, and is the information I posted on page 1 of this thread everything they would need to know?

---

### Post by mörgæs on 2013-12-20
Are you saying that Leafpad works in 14.04 both in a live boot and when installed to the hard disk?

---

### Post by dylan_mulenburg on 2013-12-20
> **mörgæs said:**
> Are you saying that Leafpad works in 14.04 both in a live boot and when installed to the hard disk?

>Lubuntu 13.04 installed to hard disk
Does not work
>Lubuntu 13.04 boot from CD
Works
>Lubuntu 13.10 boot from CD
Works
>Xubuntu 14.04 boot from CD
Works

All are 64-bit.

I haven't tried installing 14.04 or anything else to my hard disk yet.

---

