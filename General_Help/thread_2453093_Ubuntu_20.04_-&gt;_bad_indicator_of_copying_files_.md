---
title: "Ubuntu 20.04 -&gt; bad indicator of copying files to USB flash"
date: 2020-11-03
forum: General Help
---

### Post by eDrak on 2020-11-03
Hi. 
Please help.
I have a problem in the Linux distribution ubuntu 20.04.
When copying data to a usb flash drive -> the copy indicator shows an incredible copy speed (140mb/s). 
After that, copying remains 99%. However, the copy time corresponds to the speed of the USB flash drive.
I found that the problem is in the system cache.

To fix it, I need to edit the** /etc/sysctl.conf** file. I need to add a value: **vm.dirty_ratio = 3 **I did this, but the value does not load after the system restarts:
```
sysctl -a | grep dirtysysctl: permission denied on key 'fs.protected_fifos'
sysctl: permission denied on key 'fs.protected_hardlinks'
sysctl: permission denied on key 'fs.protected_regular'
sysctl: permission denied on key 'fs.protected_symlinks'
sysctl: permission denied on key 'kernel.cad_pid'
sysctl: permission denied on key 'kernel.unprivileged_userns_apparmor_policy'
sysctl: permission denied on key 'kernel.usermodehelper.bset'
sysctl: permission denied on key 'kernel.usermodehelper.inheritable'
sysctl: permission denied on key 'net.core.bpf_jit_harden'
sysctl: permission denied on key 'net.core.bpf_jit_kallsyms'
sysctl: permission denied on key 'net.core.bpf_jit_limit'
sysctl: permission denied on key 'net.ipv4.tcp_fastopen_key'
sysctl: permission denied on key 'net.ipv6.conf.all.stable_secret'
sysctl: permission denied on key 'net.ipv6.conf.default.stable_secret'
sysctl: permission denied on key 'net.ipv6.conf.enp4s0.stable_secret'
sysctl: permission denied on key 'net.ipv6.conf.lo.stable_secret'
sysctl: permission denied on key 'net.ipv6.conf.wlp5s0.stable_secret'
sysctl: permission denied on key 'vm.mmap_rnd_bits'
sysctl: permission denied on key 'vm.mmap_rnd_compat_bits'
vm.dirty_background_bytes = 0
vm.dirty_background_ratio = 10
vm.dirty_bytes = 0
vm.dirty_expire_centisecs = 3000
vm.dirty_ratio = 40
vm.dirty_writeback_centisecs = 500
vm.dirtytime_expire_seconds = 43200
sysctl: permission denied on key 'vm.stat_refresh'
```

Something in the system is preventing the written values from being read.
I can't find the cause.


edit.:
I found on the internet that the file: /usr/lib/pm-utils/power.d/**laptop-mode** can do these problems. 
_I do not have_ this file in the directory. My directory is: /usr/lib/pm-utils/**95hdparm-apm**

---

