---
title: "Slow boot in Ubuntu 14.04 xen domU"
date: 2015-10-17
forum: General Help
---

### Post by bruce40 on 2015-10-17
I was wondering if anyone had suggestions on how to fix a slow boot on Ubuntu 14.04 running under XEN domU (this was previously a Ubunto 10.xx system updated to 12 -> 14 ), I've narrowed down the slowdown to this part of the bootup process:

```
[    1.492052] Sending DHCP requests ...... timed out!
[   87.564412] IP-Config: Reopening network devices...
[   87.580098] Sending DHCP requests ...... timed out!
[  177.452182] IP-Config: Auto-configuration of network failed

```
It takes 4-5 mins for the DHCP autoconfig to timeout, it seems this is part of the kernel boot and not part of the system boot

My grub boot config is as follows:

```
title           Ubuntu 14.04.3 LTS, kernel 3.13.0-65-generic
uuid            299bd4f1-9ffd-4b89-aad9-0187681a793b
kernel          /boot/vmlinuz-3.13.0-65-generic root=UUID=299bd4f1-9ffd-4b89-aad9-0187681a793b ro splash console=xvc0 ip=off 
initrd          /boot/initrd.img-3.13.0-65-generic
```

I've tried different combinations of the 'ip' flag with no success, 'off', 'none', 'eth0', and ommiting it

Any suggestions would be appreciated.

Thanks.

---

### Post by bruce40 on 2015-10-17
Additionally this only happens on the 3.13 kernel and not on the 2.6.32 kernel on the same domU.

---

### Post by bruce40 on 2015-10-22
finally figured out the problem, XEN was adding boot options to the kernel on boot due to the 'dchp' directive in the configuration for the domU, removed that and resolved the slow boot problem.  I suspect the kernel driver for the virtual ethernet card had some regressions between releases and had trouble requesting an IP address during boot.

---

