---
title: "boost libraries not found"
date: 2022-10-19
forum: General Help
---

### Post by bitrat2 on 2022-10-19
boost libraries not found 	
 	 	[INDENT] 		I installed aptitude on LTS 18.04, but got this error ...

```
user@host:~$ aptitude
aptitude: error while loading shared libraries: libboost_iostreams.so.1.65.1: cannot open shared object file: No such file or directory 


```

```
user@host:~$ ldconfig -p | grep iostream
user@host:~$ 

 	
```

```
user@host:~$ ll /usr/lib/x86_64-linux-gnu | grep iostream
-rw-r--r--   1 root root   317546 Mar  6  2018 libboost_iostreams.a 
lrwxrwxrwx   1 root root       28 Mar  6  2018 libboost_iostreams.so -> libboost_iostreams.so.1.65.1
```

 

Tried removing and reinstalling the library...

```
user@host:~$ sudo apt-get remove libboost-iostreams-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-atomic-dev libboost-chrono-dev libboost-container-dev libboost-context-dev libboost-coroutine-dev libboost-date-time-dev libboost-exception-dev libboost-fiber-dev libboost-filesystem-dev
  libboost-graph-dev libboost-graph-parallel-dev libboost-locale-dev libboost-log-dev libboost-math-dev libboost-mpi-dev libboost-mpi-python-dev libboost-numpy-dev libboost-program-options-dev
  libboost-python-dev libboost-random-dev libboost-regex-dev libboost-serialization-dev libboost-signals-dev libboost-stacktrace-dev libboost-system-dev libboost-test-dev libboost-thread-de
  libboost-timer-dev libboost-tools-dev libboost-type-erasure-dev libboost-wave-dev
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  libboost-all-dev libboost-iostreams-dev
0 upgraded, 0 newly installed, 2 to remove and 4 not upgraded.
After this operation, 20.5 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 297160 files and directories currently installed.)
Removing libboost-all-dev (1.65.1.0ubuntu1) ...
Removing libboost-iostreams-dev:amd64 (1.65.1.0ubuntu1) ....
.
.
.
user@host:~$ sudo apt-get install libboost-iostreams-devReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-atomic-dev libboost-chrono-dev libboost-container-dev libboost-context-dev libboost-coroutine-dev libboost-date-time-dev libboost-exception-dev libboost-fiber-dev libboost-filesystem-dev
  libboost-graph-dev libboost-graph-parallel-dev libboost-locale-dev libboost-log-dev libboost-math-dev libboost-mpi-dev libboost-mpi-python-dev libboost-numpy-dev libboost-program-options-dev
  libboost-python-dev libboost-random-dev libboost-regex-dev libboost-serialization-dev libboost-signals-dev libboost-stacktrace-dev libboost-system-dev libboost-test-dev libboost-thread-dev
  libboost-timer-dev libboost-tools-dev libboost-type-erasure-dev libboost-wave-dev
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libboost-iostreams-dev
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 2,916 B of archives.
After this operation, 10.2 kB of additional disk space will be used.
Get:1 http://nz.archive.ubuntu.com/ubuntu bionic/universe amd64 libboost-iostreams-dev amd64 1.65.1.0ubuntu1 [2,916 B]
Fetched 2,916 B in 1s (4,905 B/s)
Selecting previously unselected package libboost-iostreams-dev:amd64.
(Reading database ... 297156 files and directories currently installed.)
Preparing to unpack .../libboost-iostreams-dev_1.65.1.0ubuntu1_amd64.deb ...
Unpacking libboost-iostreams-dev:amd64 (1.65.1.0ubuntu1) ...
Setting up libboost-iostreams-dev:amd64 (1.65.1.0ubuntu1) ... 

```

Still not there...


  ```
user@host:~$ ll /usr/lib/x86_64-linux-gnu | grep iostream
-rw-r--r--   1 root root   317546 Mar  6  2018 libboost_iostreams.a
lrwxrwxrwx   1 root root       28 Mar  6  2018 libboost_iostreams.so -> libboost_iostreams.so.1.65.1 
```

There are a few other boost libraries with similar dead links, after full reinstall of boost and boost-dev using apt-get.

 
Anyone have any idea why these libraries are missing and won't install? 	
[/INDENT]

---

### Post by TheFu on 2022-10-19
Did you run "sudo apt update" today?

```

$ dpkg -l libboost*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-===========================================================
un  libboost-date-time1.55.0    <none>             <none>             (no description available)
ii  libboost-filesystem1.65.1:a 1.65.1+dfsg-0ubunt amd64              filesystem operations (portable paths, iteration over direc
ii  libboost-iostreams1.58.0:am 1.58.0+dfsg-5ubunt amd64              Boost.Iostreams Library
ii  libboost-iostreams1.65.1:am 1.65.1+dfsg-0ubunt amd64              Boost.Iostreams Library
ii  libboost-random1.58.0:amd64 1.58.0+dfsg-5ubunt amd64              Boost Random Number Library
ii  libboost-regex1.65.1:amd64  1.65.1+dfsg-0ubunt amd64              regular expression library for C++
ii  libboost-system1.58.0:amd64 1.58.0+dfsg-5ubunt amd64              Operating system (e.g. diagnostics support) library
ii  libboost-system1.65.1:amd64 1.65.1+dfsg-0ubunt amd64              Operating system (e.g. diagnostics support) library
ii  libboost-thread1.58.0:amd64 1.58.0+dfsg-5ubunt amd64              portable C++ multi-threading
ii  libboost-thread1.65.1:amd64 1.65.1+dfsg-0ubunt amd64              portable C++ multi-threading

```
are installed on my 18.04 workstation.

```
$ apt search libboost-iostreams1.65.1
Sorting... Done
Full Text Search... Done
libboost-iostreams1.65.1/bionic,now 1.65.1+dfsg-0ubuntu5 amd64 [installed,automatic]
  Boost.Iostreams Library

```
This command shows over 100 Boost libraries available to be installed.
```
$ apt search libboost-* |wc -l
```
There are 3 lines per library, so the 494 count of returned lines means about &#8531;rd are available libraries - as a quick guessimate.

BTW, you can reinstall packages without removing them. Use
```
$ sudo apt install --reinstall {packagename}
```
This won't remove system settings, for that, a 'purge' is needed. But it won't touch any per user account settings in $HOME for any user.

---

### Post by bitrat2 on 2022-10-19
> Did you run "sudo apt update" today?
Yes.

```
sudo apt install --reinstall libboost-iostreams1.65.1
sudo apt install --reinstall libboost-filesystem1.65.1
sudo apt install --reinstall libboost-system1.65.1
aptitude  **WORKS!**
```

Thanks! ***[FONT=courier new]--reinstall[/FONT]*** did the trick for some reason.

Also, fyi, I renamed the soft link before reinstalling the iostream library..
```
mv /usr/lib/x86_64-linux-gnu/libboost_iostreams.so /usr/lib/x86_64-linux-gnu/libboost_iostreams.so.XXXX
```
..and was interested to see it wasn't recreated when I reinstalled.

```
user@host:~$ ll /usr/lib/x86_64-linux-gnu/ | grep libboost_iostreams.so
-rw-r--r--   1 root root   105032 Mar  6  2018 libboost_iostreams.so.1.65.1
lrwxrwxrwx   1 root root       28 Mar  6  2018 libboost_iostreams.so.XXXX -> libboost_iostreams.so.1.65.1
```


After I renamed the link to the original name and reinstalled the other files, it worked. 

 Maybe renaming one link triggered something by not being there, but I was surprised the installer didn't recreate it.

Anyway, thanks again.  :-)

---

### Post by TheFu on 2022-10-20
I suspect the remove didn't do anything because of dependencies.

---

