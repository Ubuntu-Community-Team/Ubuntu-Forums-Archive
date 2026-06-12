---
title: "hald (HAL daemon) behavior analysis"
date: 2014-01-24
forum: General Help
---

### Post by qzy8882 on 2014-01-24
We were looking at the behavior of hald on a Linux host (Ubuntu 12.04.2 LTS 64-bit). We looked at both its syslog and system calls (using strace). According to the documentation, hald receives notifications whenever a new hardware device is plugged in. On our host, however, even though we never plug in any new hardware devices, the hald process keeps receiving messages from a datagram unix domain socket (which was bound at @/org/freedesktop/hal/udev_event). From syslog, we can see the repeated messages such as this:

[FONT=arial black]hald[19608]: 22:26:33.665 [I] osspec.c:256: SEQNUM=541371, ACTION=add, SUBSYSTEM=queues, DEVPATH=/sys/devices/virtual/net/lo/queues/rx-0, DEVNAME=, IFINDEX=0

hald[19608]: 22:26:33.665 [D] hotplug.c:476: checking ADD event /sys/devices/virtual/net/lo/queues/rx-0

hald[19608]: 22:26:33.665 [D] hotplug.c:397: event /sys/devices/virtual/net/lo/queues/rx-0: skip ourselves and all later events

hald[19608]: 22:26:33.665 [I] osspec.c:1022: hal_util_find_known_parent: '/sys/devices/virtual/net/lo/queues/rx-0'->'/sys/devices/virtual/net/lo'

hald[19608]: 22:26:33.665 [I] device.c:4997: add_dev: subsys=queues sysfs_path=/sys/devices/virtual/net/lo/queues/rx-0 dev= parent_dev=0x01d66980

hald[19608]: 22:26:33.665 [D] hotplug.c:500: events queued = 0, events in progress = 0

hald[19608]: 22:26:33.665 [D] hotplug.c:505: Hotplug-queue empty now ... no hotplug events in progress
[/FONT]

I wonder what is this really happeneing. It seems that some one has requested the device "/sys/devices/virtual/net/lo/queues/rx-0" to be added to the system. However, this path already existed (thus I assume added already) and I do not understand why someone keeps asking to add it. We are suspecting that something is wrong in the system and such requests should not be generated in the first place (but couldn't confirm). If anyone could shed any light on such behavior, it will be very appreciated!

---

### Post by cariboo on 2014-01-24
Moved to General Help, as this is a support question.

---

### Post by tgalati4 on 2014-01-24
I presume that you are using 12.04 as a host for several virtual machines.  It's possible that this is normal behavior to provide the "lo" or loopback network device for each virtual machine.  I presume you are using KVM to support your virtual machines, and that may be the way KVM works.

---

### Post by millerthegorilla on 2014-03-18
I'm getting this along with nfconntrack messages in udevadm monitor when I start chromium.

It reports:

KERNEL[1800.213828] add      /kernel/slab/nf_conntrack_ffff88010ee51b00 (slab)
UDEV  [1800.214833] add      /kernel/slab/nf_conntrack_ffff88010ee51b00 (slab)
KERNEL[1800.214854] add      /devices/virtual/net/lo/queues/rx-0 (queues)
UDEV  [1800.214868] add      /devices/virtual/net/lo/queues/rx-0 (queues)
KERNEL[1800.214879] add      /devices/virtual/net/lo/queues/tx-0 (queues)
UDEV  [1800.214891] add      /devices/virtual/net/lo/queues/tx-0 (queues)
KERNEL[1800.493361] remove   /devices/virtual/net/lo/queues/rx-0 (queues)
KERNEL[1800.493385] remove   /devices/virtual/net/lo/queues/tx-0 (queues)
UDEV  [1800.493761] remove   /devices/virtual/net/lo/queues/rx-0 (queues)
UDEV  [1800.493776] remove   /devices/virtual/net/lo/queues/tx-0 (queues)
KERNEL[1800.509463] remove   /kernel/slab/nf_conntrack_ffff88010ee51b00 (slab)
UDEV  [1800.509972] remove   /kernel/slab/nf_conntrack_ffff88010ee51b00 (slab)

in udevadm monitor.  I ought to point out that I have no virtual machines installed.

Linux super-R720 3.8.0-32-lowlatency #24-Ubuntu SMP PREEMPT Tue Oct 15 21:20:09 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

running ubuntu studio 12.04

---

