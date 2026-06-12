---
title: "Segmentation fault , No RAM errors , Ubuntu 18 something updated last week"
date: 2018-06-07
forum: General Help
---

### Post by MasterCATZ on 2018-06-07
LSB Version:    security-9.20170808ubuntu1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic


Linux aio 4.16.7-041607-generic #201805021131 SMP Wed May 2 15:34:55 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux




an update some time this month has broken the OS and programs will not run without Segmentation fault 
I don't know if it was yesterday's updates or not but after reboot all programs dead 
RAM tested fine , tried all combinations of memory also 

 tried with IGPU disabled with Dedicated Card same issue 

 google-chrome
Segmentation fault
aio@aio:~/Downloads$ [13598:13598:0608/135630.922986:ERROR:sandbox_linux.cc(378)] InitializeSandbox() called with multiple threads in process gpu-process.


MEGAprivate ERROR DUMP
Application: MEGAsync
Version code: 3001.0
Module name: megasync
Operating system: Linux
System release:  4.16.7-041607-generic
System arch: x86_64
Error info:
Segmentation fault (11) at address 0x7ff36ed72018
Stacktrace:
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0x25ca6) [0x7ff36ebe5ca6]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0x25ca6) [0x7ff36ebe5ca6]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0x22a2d) [0x7ff36ebe2a2d]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0x22ab9) [0x7ff36ebe2ab9]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0x17754) [0x7ff36ebd7754]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0x13674) [0x7ff36ebd3674]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0x13b0e) [0x7ff36ebd3b0e]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0x12cb6) [0x7ff36ebd2cb6]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0xc421) [0x7ff36ebcc421]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0xc799) [0x7ff36ebcc799]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0xdcef) [0x7ff36ebcdcef]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0xbe6b) [0x7ff36ebcbe6b]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0xc07c) [0x7ff36ebcc07c]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(+0x9a30) [0x7ff36ebc9a30]
/usr/lib/x86_64-linux-gnu/libesets_pac.so(fclose+0x1db) [0x7ff36ebca0bc]
/usr/lib/x86_64-linux-gnu/libcares.so.2(ares_init_options+0x8d1) [0x7ff36dbf6861]
megasync() [0x5d0719]
megasync() [0x5bbafb]
megasync() [0x5c201b]
megasync() [0x5c20b8]
/usr/lib/x86_64-linux-gnu/libQtCore.so.4(+0x7ae3c) [0x7ff36bdeae3c]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x76db) [0x7ff36bb576db]
/lib/x86_64-linux-gnu/libc.so.6(clone+0x3f) [0x7ff36af3188f]
------------------------------



works fine booting from live USB

reinstalled everything that had been upgraded to rule out corrupt file 
still failing
tried old kernal 4.15.0-23-generic 
Segmentation fault

what can I do to work this out ? 

dmesg

[58.196008] TaskSchedulerBa[5026]: segfault at 7fbc53a05000 ip 00007fbc53862a0b sp 00007fbc3ae590c0 error 4
 [  359.414492] TaskSchedulerFo[8561]: segfault at 7f2bfc784000 ip 00007f2bfc7aaa0b sp 00007f2bc410aa00 error 4 in libesets_pac.so[7f2bfc7a0000+44000]
[  273.482956] pool[5801]: segfault at 99fffffff8 ip 00007fa54c57798d sp 00007fa5097fd450 error 4 in libc-2.27.so[7fa54c4e0000+1e7000]

---

### Post by MasterCATZ on 2018-06-08
Solved 

Removed Nod32 / Eset Antivirus ... 


[LIST=1]
[*]Open a Terminal window by clicking Applications &#8594; Accessories  &#8594; Terminal.
[*]Type the following command and press Enter:

cd /opt/eset/esets/bin
[*]Type the following command to run the uninstaller script:

sudo ./esets_gil
[/LIST]

---

