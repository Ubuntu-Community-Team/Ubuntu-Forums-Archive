---
title: "Totally in stuck"
date: 2006-09-29
forum: General Help
---

### Post by User-007 on 2006-09-29
Hi! 

I tried to install some hazy software from deb-packages. Unfortunately, now I am totally in stuck. 

When trying to run update manager, i will get:

--------------------------
[COLOR="Red"]Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/COLOR]
--------------------------

When trying Synaptic, 4 broken packages are found, but I am not able to fix the issue. Cannot remove them, cannot reinstall, cannot automatically "fix broken packages", either. Moreover, when trying the last alternative, the result is:

--------------------------
[COLOR="Red"]$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-4 is installed
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-4 is installed  xmoto: Depends: libc6 (>= 2.4-1) but 2.3.6.ds1-4 is installed
         Depends: libcurl3 (>= 7.15.4-1) but 7.15.1-1ubuntu2 is installed
         Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is installed
         Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.9-0.0ubuntu2 is installed
         Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies[/COLOR]
----------------------------

How to fix the issue? Please, help.

User JB

---

### Post by wieman01 on 2006-09-29
You can try a tool called "gtkorphaned" to removed broken/orphaned packages. This is all I can offer.

Perhaps you can find something useful here: [http://www.ubuntuforums.org/showthread.php?t=186672]("http://www.ubuntuforums.org/showthread.php?t=186672")

---

### Post by User-007 on 2006-09-30
THANK YOU!

"sudo aptitude -f remove" helped. After running...

[COLOR="Red"]$ sudo aptitude -f remove
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libc6 libc6-dev libc6-i686 xmoto
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-4 is installed.
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-4 is installed.
  libc6: Depends: tzdata which is a virtual package.
  xmoto: Depends: libc6 (>= 2.4-1) but 2.3.6.ds1-4 is installed.
         Depends: libcurl3 (>= 7.15.4-1) but 7.15.1-1ubuntu2 is installed.
         Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is installed.
         Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.9-0.0ubuntu2 is installed.
         Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libc6 [2.3.6.ds1-4 (now) -> 2.3.6-0ubuntu20 (dapper)]
xmoto [0.2.1-1 (now) -> 0.1.10-1ubuntu2 (dapper)]
xmoto-data [0.2.1-1 (now) -> 0.1.10-1ubuntu2 (dapper)]

Score is -220

Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  libc6 xmoto xmoto-data
0 packages upgraded, 0 newly installed, 3 downgraded, 0 to remove and 0 not upgraded.
Need to get 7423kB of archives. After unpacking 4780kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe xmoto 0.1.10-1ubuntu2 [355kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe xmoto-data 0.1.10-1ubuntu2 [2480kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libc6 2.3.6-0ubuntu20 [4588kB]
Fetched 7423kB in 1m7s (110kB/s)
(Reading database ... 151924 files and directories currently installed.)
Preparing to replace xmoto 0.2.1-1 (using .../xmoto_0.1.10-1ubuntu2_i386.deb) ...
Unpacking replacement xmoto ...
dpkg - warning: downgrading xmoto-data from 0.2.1-1 to 0.1.10-1ubuntu2.
Preparing to replace xmoto-data 0.2.1-1 (using .../xmoto-data_0.1.10-1ubuntu2_all.deb) ...
Unpacking replacement xmoto-data ...
Preparing to replace libc6 2.3.6.ds1-4 (using .../libc6_2.3.6-0ubuntu20_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: warning - unable to delete old directory `/etc/ld.so.conf.d': Directory not empty
Setting up libc6 (2.3.6-0ubuntu20) ...

Setting up xmoto-data (0.1.10-1ubuntu2) ...
Setting up xmoto (0.1.10-1ubuntu2) ...
[/COLOR]

...everything works like a charm again.

User JB

---

