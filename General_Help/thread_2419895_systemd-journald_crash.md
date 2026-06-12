---
title: "systemd-journald crash"
date: 2019-05-26
forum: General Help
---

### Post by gvando on 2019-05-26
Hi I am new to linux,

I recently installed ubuntu 18.04 on my Lenovo thinkpad X1 carbon 6th ed. I am getting a crash report upon startup every time. I tried clearing my crash folder, but that did not solve the issue.
Here is the apport log:

```
ERROR: apport (pid 2822) Sat May 25 14:37:02 2019: called for pid 275, signal 6, core limit 0, dump mode 1
ERROR: apport (pid 2822) Sat May 25 14:37:02 2019: executable: /lib/systemd/systemd-journald (command line "/lib/systemd/systemd-journald")
ERROR: apport (pid 2822) Sat May 25 14:37:02 2019: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 2822) Sat May 25 14:37:02 2019: wrote report /var/crash/_lib_systemd_systemd-journald.0.crash
ERROR: apport (pid 9448) Sat May 25 20:34:52 2019: called for pid 267, signal 6, core limit 0, dump mode 1
ERROR: apport (pid 9448) Sat May 25 20:34:52 2019: executable: /lib/systemd/systemd-journald (command line "/lib/systemd/systemd-journald")
ERROR: apport (pid 9448) Sat May 25 20:34:52 2019: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 9448) Sat May 25 20:34:52 2019: apport: report /var/crash/_lib_systemd_systemd-journald.0.crash already exists and unseen, doing nothing to avoid disk usage DoS

Crash Report:

ProblemType: Crash
Architecture: amd64
Date: Sat May 25 14:37:02 2019
DistroRelease: Ubuntu 18.04
ExecutablePath: /lib/systemd/systemd-journald
ExecutableTimestamp: 1555331390
ProcCmdline: /lib/systemd/systemd-journald
ProcCwd: /
ProcEnviron:
 LANG=en_US.UTF-8
 PATH=(custom, no user)
...
ProcStatus:
 Name:  systemd-journal
 Umask: 0022
 State: S (sleeping)
 Tgid:  275
 Ngid:  0
 Pid:   275
 PPid:  1
 TracerPid:     0
 Uid:   0       0       0       0
 Gid:   0       0       0       0
 FDSize:        128
 Groups:
 NStgid:        275
 NSpid: 275
 NSpgid:        275
 NSsid: 275
 VmPeak:           95056 kB
 VmSize:           95056 kB
 VmLck:        0 kB
 VmPin:        0 kB
 VmHWM:    17736 kB
 VmRSS:    17736 kB
```
What is the purpose of journald? How can I fix this error? I'd rather not ignore it by simply turning off crash reports.

Thanks!

---

### Post by wildmanne39 on 2019-05-26
Hello and welcome to the forum!

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Thanks!

---

