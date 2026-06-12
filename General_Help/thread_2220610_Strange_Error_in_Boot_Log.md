---
title: "Strange Error in Boot Log"
date: 2014-04-28
forum: General Help
---

### Post by adec2 on 2014-04-28
Hi,
I am getting an error that repeats itself over 100 times with the boot sequence log

"Apr 28 23:24:05 ade-G41D3C kernel: [ 4337.842855] multiqueue0:src[9199]: segfault at 200000000 ip 00007f6afe34edd2 sp 00007f6afcbf9860 error 6 in libgstlibav.so[7f6afe335000+35000]"

Also here is part of my boot log and I am convinced this is why part of the boot process is getting slow

Apr 28 22:18:40 ade-G41D3C rtkit-daemon[2997]: Successfully made thread 3508 of process 3508 (n/a) owned by '1000' high priority at nice level -11.
Apr 28 22:18:40 ade-G41D3C rtkit-daemon[2997]: Supervising 5 threads of 2 processes of 1 users.
Apr 28 22:18:40 ade-G41D3C rtkit-daemon[2997]: Successfully made thread 3509 of process 3508 (n/a) owned by '1000' RT at priority 5.
Apr 28 22:18:40 ade-G41D3C rtkit-daemon[2997]: Supervising 6 threads of 2 processes of 1 users.
Apr 28 22:18:40 ade-G41D3C rtkit-daemon[2997]: Successfully made thread 3510 of process 3508 (n/a) owned by '1000' RT at priority 5.
Apr 28 22:18:40 ade-G41D3C rtkit-daemon[2997]: Supervising 7 threads of 2 processes of 1 users.
Apr 28 22:18:40 ade-G41D3C rtkit-daemon[2997]: Successfully made thread 3511 of process 3508 (n/a) owned by '1000' RT at priority 5.
Apr 28 22:18:40 ade-G41D3C rtkit-daemon[2997]: Supervising 8 threads of 2 processes of 1 users.
Apr 28 22:18:40 ade-G41D3C pulseaudio[3508]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
Apr 28 22:18:40 ade-G41D3C pulseaudio[3508]: [pulseaudio] main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NotSupported: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11

The system does boot eventually

Has anybody any idea what it is or how to fix it even?

Thank You

---

### Post by kurt miller on 2014-06-06
Getting the same.

---

