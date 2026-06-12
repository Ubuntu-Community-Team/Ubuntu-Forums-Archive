---
title: "poor wifi throughput speeds"
date: 2024-11-13
forum: General Help
---

### Post by brcisna-u on 2024-11-13
Ubuntu 24 Server LTS x 2

have two of these cards in 2 different machines running Ubuntu 24 server fresh installs

```
[04:00.0 Network controller: Intel Corporation Wi-Fi 7(802.11be) AX1775*/AX1790*/BE20*/BE401/BE1750* 2x2 (rev 1a)    Subsystem: Intel Corporation Wi-Fi 7(802.11be) AX1775*/AX1790*/BE20*/BE401/BE1750* 2x2 (BE200 320MHz [Gale Peak])
    Flags: bus master, fast devsel, latency 0, IRQ 19, IOMMU group 8
    Memory at d2000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [b0] MSI-X: Enable+ Count=32 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [148] Secondary PCI Express
    Capabilities: [158] Physical Layer 16.0 GT/s <?>
    Capabilities: [17c] Lane Margining at the Receiver <?>
    Capabilities: [188] Latency Tolerance Reporting
    Capabilities: [190] L1 PM Substates
    Capabilities: [1a0] Vendor Specific Information: ID=0002 Rev=4 Len=100 <?>
    Capabilities: [2a0] Data Link Feature <?>
    Capabilities: [2ac] Precision Time Measurement
    Capabilities: [2b8] Vendor Specific Information: ID=0003 Rev=1 Len=054 <?>
    Capabilities: [500] Vendor Specific Information: ID=0023 Rev=1 Len=010 <?>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi



```

I set SERVER1 as a hotspot through network-manager-gui with 5Ghz selected on chneel 36
On SERVER 2 i make my connection with the same card to the hotspot.

The best i can do with the servers only 20 feet apart in same room is about 145Mbps.

```
Connecting to host 10.42.0.65, port 5201[  5] local 10.42.0.1 port 45456 connected to 10.42.0.65 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  20.0 MBytes   168 Mbits/sec    0    902 KBytes       
[  5]   1.00-2.00   sec  17.5 MBytes   147 Mbits/sec    0   1.04 MBytes       
[  5]   2.00-3.00   sec  17.5 MBytes   147 Mbits/sec    0   1.17 MBytes       
[  5]   3.00-4.00   sec  17.5 MBytes   147 Mbits/sec    0   1.30 MBytes       
[  5]   4.00-5.00   sec  17.5 MBytes   147 Mbits/sec    0   1.46 MBytes       
[  5]   5.00-6.00   sec  17.5 MBytes   147 Mbits/sec    0   1.46 MBytes       
[  5]   6.00-7.00   sec  17.5 MBytes   147 Mbits/sec    0   1.46 MBytes       
[  5]   7.00-8.00   sec  17.5 MBytes   147 Mbits/sec    0   1.64 MBytes       
[  5]   8.00-9.00   sec  17.5 MBytes   147 Mbits/sec    0   1.64 MBytes       
[  5]   9.00-10.00  sec  17.5 MBytes   147 Mbits/sec    0   1.64 MBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec   178 MBytes   149 Mbits/sec    0             sender
[  5]   0.00-10.02  sec   175 MBytes   146 Mbits/sec                  receiver


iperf Done.



```

What puzzles me...the connection rate is only 130 Mbps possible.
If you look at the screen shot my T-MO gateway shows possible 540Mbps connection rate 10 feet away.Opps sorry can not attach a photo/screenshot.

I have tried all channels through both the 2.4 Ghz,and the 5Ghz range and throughput is always fairly simlar the slightly better on 5Ghz channels.

What I am missing that the  connection rate is only 130Mbps.
I did also try setting up a hostapd and it was much worse for throughput.

Have seen were a  gentleman on Youtube,,, was getting over 2Gbps throughput ,,,,going from a client,,,to an soho WiFi7 router. with this same card ! 

TIA

---

