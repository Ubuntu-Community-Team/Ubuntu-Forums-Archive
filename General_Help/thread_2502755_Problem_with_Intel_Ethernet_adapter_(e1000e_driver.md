---
title: "Problem with Intel Ethernet adapter (e1000e driver) on Ubuntu 24.04"
date: 2024-11-27
forum: General Help
---

### Post by bomberb17 on 2024-11-27
When I connect a LAN cable to my laptop, it doesn't negotiate an IP and I see the following after running `sudo dmesg -w`:

```
[ 7555.219803] e1000e 0000:00:1f.6 eno2: NETDEV WATCHDOG: CPU: 5: transmit queue 0 timed out 10430 ms
[ 7555.219823] e1000e 0000:00:1f.6 eno2: Reset adapter unexpectedly
[ 7560.601747] e1000e 0000:00:1f.6 eno2: NIC Link is Up 10 Mbps Full Duplex, Flow Control: Rx/Tx
[ 7576.851432] e1000e 0000:00:1f.6 eno2: Detected Hardware Unit Hang:
                 TDH                  <1>
                 TDT                  <3>
                 next_to_use          <3>
                 next_to_clean        <1>
               buffer_info[next_to_clean]:
                 time_stamp           <100694b15>
                 next_to_watch        <1>
                 jiffies              <100698a80>
                 next_to_watch.status <0>
               MAC Status             <40080003>
               PHY Status             <796d>
               PHY 1000BASE-T Status  <3800>
               PHY Extended Status    <3000>
               PCI Status             <10>
[ 7577.234697] e1000e 0000:00:1f.6 eno2: NETDEV WATCHDOG: CPU: 5: transmit queue 0 timed out 7624 ms
[ 7577.234798] e1000e 0000:00:1f.6 eno2: Reset adapter unexpectedly

```

Any idea on how to solve this?

---

