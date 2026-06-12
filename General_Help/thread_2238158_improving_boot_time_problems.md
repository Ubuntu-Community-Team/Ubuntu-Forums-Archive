---
title: "improving boot time problems"
date: 2014-08-06
forum: General Help
---

### Post by jwe.van.dijk on 2014-08-06
I would like to improve boot time. I have ubuntu 14.04 on hp pavilion dual amd64.
It takes 45 secs until I can enter the password and after that it takes an other 40 secs before the unity taskbar appears.
As a start I have filtered all dmesg lines that took more than 1 sec to appear (immediately after start: dmesg > dmesg.txt and a python script to filter the slow lines):

( 209 d= 1.04) [    1.062855] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
( 518 d= 1.23) [    3.729141] PCI: CLS 64 bytes, default 64
( 777 d=12.14) [   19.733798] Adding 4401148k swap on /dev/sda7.  Priority:-1 extents:1 across:4401148k FS
( 778 d= 1.12) [   20.854499] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
( 853 d= 3.08) [   29.290557] FS-Cache: Loaded
( 864 d= 1.45) [   32.125674] init: avahi-cups-reload main process (983) terminated with status 1
( 882 d= 2.17) [   35.246848] r8169 0000:07:00.0 eth0: link down
( 892 d= 1.09) [   37.353954] cfg80211: Calling CRDA for country: DE
( 904 d= 1.27) [   39.004832] type=1400 audit(1407323103.534:84): apparmor="DENIED" operation="open" profile="/usr/bin/freshclam" name="/etc/ld.so.preload" pid=1415 comm="freshclam" requested_mask="r" denied_mask="r" fsuid=117 ouid=0
( 905 d= 2.96) [   41.965475] fglrx_pci 0000:00:01.0: irq 43 for MSI/MSI-X
( 923 d=28.80) [   73.263292] type=1400 audit(1407323137.799:87): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/etc/ld.so.preload" pid=2609 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

The dmesg lines are prefixed by (linenr d=secs since prev. line)
In particular the lines concerning the swap and the last one worry me.
Any explanation and suggestions for improvement welcome
Cheers, Janwillem

---

