---
title: "udev using 100% of cpu"
date: 2021-11-22
forum: General Help
---

### Post by jontyms on 2021-11-22
```Nov 20 05:59:19.000260 lan. systemd-udevd[3]: ethtool: autonegotiation is unset or enabled, the speed and duplex are not writable.

Nov 20 05:59:19.002444 lan. systemd-udevd[3]: Using default interface naming scheme 'v249'.```
I am on Ubuntu 21.10
Linux 5.13.0-1010-raspi aarch64
Raspberry pi 4 8gb
What should I do to fix this?

---

### Post by peacerat on 2021-12-05
Did you find a solution for this? I see something similar when installing microk8s on a new install of ubuntu server 21.10 on the same hardware.

---

### Post by akrek on 2021-12-10
I habe the same behavior after upgrading from 21.04 to 21.10. I don&#8216;t use microk8s but Docker.
Same hardware.

&#8222;systemd-udevd[1869753]: ethtool: autonegotiation is unset or enabled, the speed and duplex are not writable&#8220;

Linux 5.13.0-1011-raspi #13-Ubuntu SMP PREEMPT Fri Nov 19 18:40:23 UTC 2021 aarch64 aarch64 aarch64 GNU/Linux

---

