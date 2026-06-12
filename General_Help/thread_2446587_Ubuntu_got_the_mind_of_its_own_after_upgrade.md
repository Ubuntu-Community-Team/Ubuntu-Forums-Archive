---
title: "Ubuntu got the mind of its own after upgrade"
date: 2020-07-03
forum: General Help
---

### Post by Freek07 on 2020-07-03
Hey all,

I have an installation on my NAS and after the upgrade (it was due to be upgraded for a looong time) the system doesn't obey RAID and network settings anymore.
Specifically, it does assemble raid array, but not the one it should based on the mdadm.conf (so I cannot use fstab after reboot).

Here's my mdadm.conf
```
# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
DEVICE /dev/disk/by-partuuid/117ca24c-8f92-44df-a202-f5e8d2c70959 /dev/disk/by-partuuid/90cf43a8-25a5-46e6-a64d-8cdcccede0b3

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 devices=/dev/disk/by-partuuid/117ca24c-8f92-44df-a202-f5e8d2c70959,/dev/disk/by-partuuid/90cf43a8-25a5-46e6-a64d-8cdcccede0b3
```

What I get, is /dev/md127.


And the second one is, /etc/network/indefaces does not "work" anymore (interface enp3s0 is not set up automatically, anymore):
```

auto enp3s0
allow-hotplug enp3s0
iface enp3s0 inet static
    address 192.168.1.20
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 193.2.1.66 193.2.1.72
    mtu 1500

```

Any ideas? Thanks :)

---

