---
title: "Sudden kernel restart and time jump"
date: 2017-02-09
forum: General Help
---

### Post by jayaraj2 on 2017-02-09
I have the following setup and am noticing that on some occasions when I am upgrading my in-house application (where I stop the service and start it again), the kernel abruptly restarts and I also notice there is a time jump in the kernel logs. 

I am using an ATCA chassis with a 7311 and 7470 blades.
Linux 7311-9 3.2.0-29-generic #46 SMP Fri Jul 15 10:04:18 IST 2016 x86_64 x86_64 x86_64 GNU/Linux

[U][B]Excerpts from the kernel.log
[/B][/U]Feb  7 00:24:24 7475-14 kernel: [19053539.090473] TIPC: Lost link <1.1.14:base-1.1.9:base> on network plane A
Feb  7 00:24:24 7475-14 kernel: [19053539.090475] TIPC: Lost contact with <1.1.9>
Feb  7 00:24:25 7475-14 kernel: [19053539.290591] TIPC: Left network mode
Feb  7 00:24:25 7475-14 kernel: [19053539.302601] NET: Unregistered protocol family 30
Feb  7 00:24:25 7475-14 kernel: [19053539.302608] TIPC: Deactivated
Feb  7 00:24:27 7311-6 kernel: Kernel logging (proc) stopped.
[COLOR=#008000]Feb  7 **00:24:27 **[/COLOR]7311-6 kernel: imklog 5.8.6, log source = /proc/kmsg started.                                        [Please note the time jump]
[COLOR=#FF0000]Feb  7 **01:25:24 **731[/COLOR]1-6 kernel: imklog 5.8.6, log source = /proc/kmsg started.
Feb  7 01:25:24 7311-6 kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  7 01:25:24 7311-6 kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  7 01:25:24 7311-6 kernel: [    0.000000] Linux version 3.2.0-29-generic ([EMAIL="root@7311-9"]root@7311-9[/EMAIL]) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46 SMP Thu Feb 5 07:51:40 EST 2015 (Ubuntu 3.2.0-29.46-generic 3.2.24)
Feb  7 01:25:24 7311-6 kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.2.0-29-generic root=UUID=a3c9eb86-6471-434e-a4a8-2fa5be0e3bce ro console=ttyS0,115200n8
Feb  7 01:25:24 7311-6 kernel: [    0.000000] KERNEL supported cpus:
Feb  7 01:25:24 7311-6 kernel: [    0.000000]   Intel GenuineIntel
Feb  7 01:25:24 7311-6 kernel: [    0.000000]   AMD AuthenticAMD
Feb  7 01:25:24 7311-6 kernel: [    0.000000]   Centaur CentaurHauls
Unfortunately I do not have a kdump or trace for the reason of the reboot.

Is there anyway that someone can shed light on 
1) Why the kernel may have restarted
2) Why there seems to be an hour time jump in kernel logs
3) Is there any way the two are related?

In addition syslog also show several instances of the following log for over an hour and then it stabilizes
ntpd exiting on signal 15

---

