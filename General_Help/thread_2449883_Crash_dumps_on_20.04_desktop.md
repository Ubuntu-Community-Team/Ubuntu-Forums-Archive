---
title: "Crash dumps on 20.04 desktop"
date: 2020-09-03
forum: General Help
---

### Post by dashkay on 2020-09-03
I'm trying to enable kernel crash dumps on 20.04 desktop and my system isn't behaving. I followed the guide at [https://ubuntu.com/server/docs/kernel-crash-dump](https://ubuntu.com/server/docs/kernel-crash-dump) and have tried a remote dump with SSH as well as a local dump, as well as setting a panic shell in /etc/default/kdump-tools and kernel.panic=5 in /etc/sysctl.conf.  In all cases the config appears to check out correctly (everything looks good according to the tests in the guide, at least) and yet when I panic the system with echo c > /proc/sysrq-trigger it just locks up hard until I power cycle it.  No shell, no auto-reboot, no crashdump - it mentions the panic on the console and then just sits there.

Any suggestions?

---

### Post by TheFu on 2020-09-03
Anything in the system logs? Always check there first.  If logs aren't being saved between boots, there are settings in the journald.conf file to keep them for X reboots or until Y size is reached.  The config file is commented and the manpage for that file has more details about the settings.

Almost always, crashes are due to failing hardware.  If you boot from a prior kernel and don't see the crashes, then you can be confident it is some issue in the new kernel.

All the stuff around debugging the kernel is a bit premature at this point, unless you are a kernel guru.

---

### Post by edevolde on 2020-12-14
See [https://bugs.launchpad.net/ubuntu/+source/kexec-tools/+bug/1908090](https://bugs.launchpad.net/ubuntu/+source/kexec-tools/+bug/1908090)

---

