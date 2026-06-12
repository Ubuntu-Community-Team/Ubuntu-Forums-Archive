---
title: "Slow write speed for SAMBA and FTP file transfers"
date: 2018-10-03
forum: General Help
---

### Post by lucanello on 2018-10-03
Hello ubuntu community,

for my private home-NAS I setup a samba server which shares my hard drives to the network.
The setup looks like this:
- SSD over USB 2.0 as system hard drive (will be moved to an internal hard drive ASAP)
- 4 HDDs over SATA connector in 2 (Software-)RAID1 with about 120-170 MB/s read/write speed

The performance when working locally on the server is okay, sharing files via samba from a virtual machine on the same server works perfectly aswell. But the problem is: when I transfer files from different devices in the same network I get slower speeds.

For example:
[LIST]
[*]Macbook via WiFi
[LIST]
[*]file transfer via FTP: about 3-6 MB/s
[*]file transfer via SAMBA: about 1-5 MB/s
[/LIST]

[*]Android via WiFi
[LIST]
[*]file transfer via FTP: about 1 MB/s
[*]file transfer via SAMBA: about 700-1400 KB/s
[/LIST]
[/LIST]

I think these speeds are extremely slow and when I check the in-going speeds it tells me:
[LIST]
[*]Network traffic: Macbook about 30 MB/s and Android about 10 MB/s
[*]Disk write speed: the same as the transfer speed above (not more than 5 MB/s)
[/LIST]

The network speed test over iPerf gave me these connection speeds:

[LIST]
[*]Macbook via WiFi: 30 Mb/s
[*]Android via WiFi: 17 Mb/s
[/LIST]

What is the problem? I get enough incoming network traffic but the write speed is absolutely bad.
There are no firewalls set up and I tried several SAMBA configurations.

My router is a FRITZ!Box 7490

I hope you can help me :)
Thank you!

---

### Post by TheFu on 2018-10-03
wifi sucks.  Always has. Always will. Use wired GigE networking devices whenever possible.

USB2 speeds are usually around 22 Mbps.  Be certain to be 100% consistent in units - MB/s is seldom used for either disk or network performance, so if the tools you are using use that unit, be prepared to convert.  Software weenies think in bytes

You'll need to first determine the theoretical max connection speed possible, then set your expectations for about 50% of that bandwidth for a "best case, real world" throughput.  Do that by looking up each wifi device on the network and the claimed capabilities for it.  Make a table and start testing.

Everything in the chain from the storage to the other storage device can make things slower. Cables, controllers, network adapters,  routers, switches, wifi interference, everything can make things slower.

Most file transfer protocols have a 20-10% overhead for the protocol.

Whatever you do, don't have the NAS connected to the network using wifi.  Don't.  Just don't.

---

