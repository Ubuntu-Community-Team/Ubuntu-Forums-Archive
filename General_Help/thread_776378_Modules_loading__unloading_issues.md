---
title: "Modules loading / unloading issues"
date: 2008-04-30
forum: General Help
---

### Post by deviant on 2008-04-30
Ok. All started after I upgraded my Ubuntu from 7.10 to 8.04 and reinstalled ndiswrapper. After rebooting the machine, my wired ethernet card (BCM4401-B0 100Base-TX, rev.02) wasn`t working anymore. It seems that the appropriate module (b44) it is not loading at boot time. I added it to /ect/modules, maked sure it isn`t blacklisted in /etc/modprobe.d/blacklist and even tried loading  it via rc.local (added **modpobe b44** to the script). No success so far.

Another problem is making ndiswrapper NOT LOADING at boot time, since I want to try the new fwcutter module. So what I did was to remove it from /etc/modules and blacklisting it in /etc/modprobe.d./blacklist. That ain`t working either. So each time my box boots, ndiswrapper is somehow loaded.
And more, now I get this errors when checking the console output (alt + ctrl + F8 ): **"ERROR: Module ndiswrapper does not exist in /proc/modules"**. Same goes for module **b43** and **b44**.

Any advice on what to do next will be more that appreciated. 
Here is a paste of my syslog file, maybe it will be of any help:
```
Apr 30 01:24:12 Sisif syslogd 1.5.0#1ubuntu1: restart.
Apr 30 01:24:12 Sisif anacron[5930]: Job `cron.daily' terminated
Apr 30 01:24:12 Sisif anacron[5930]: Normal exit (1 job run)
Apr 30 01:26:56 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 30 01:27:00 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 30 01:27:09 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Apr 30 01:27:27 Sisif dhclient: No DHCPOFFERS received.
Apr 30 01:27:27 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 01:27:27 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:27:27 Sisif avahi-autoipd(eth0)[8702]: A routable address has been configured.
Apr 30 01:27:27 Sisif avahi-autoipd(eth0)[8702]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 01:27:27 Sisif avahi-daemon[5428]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 01:27:27 Sisif avahi-daemon[5428]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 01:27:27 Sisif avahi-daemon[5428]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 01:27:30 Sisif avahi-daemon[5428]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 01:27:30 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 01:27:30 Sisif avahi-autoipd(eth0)[8702]: No longer a routable address configured, restarting probe process.
Apr 30 01:27:30 Sisif avahi-daemon[5428]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 01:27:30 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 01:27:35 Sisif avahi-autoipd(eth0)[8702]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 01:27:35 Sisif avahi-daemon[5428]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:27:35 Sisif avahi-daemon[5428]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 01:27:35 Sisif avahi-daemon[5428]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 01:27:39 Sisif avahi-autoipd(eth0)[8702]: Successfully claimed IP address 169.254.9.233
Apr 30 01:32:06 Sisif nmbd[5705]: [2008/04/30 01:32:06, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Apr 30 01:32:06 Sisif nmbd[5705]:   ***** 
Apr 30 01:32:06 Sisif nmbd[5705]:    
Apr 30 01:32:06 Sisif nmbd[5705]:   Samba name server SISIF is now a local master browser for workgroup WORKGROUP on subnet 169.254.9.233 
Apr 30 01:32:06 Sisif nmbd[5705]:    
Apr 30 01:32:06 Sisif nmbd[5705]:   ***** 
Apr 30 01:33:49 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 30 01:33:56 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr 30 01:34:11 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 30 01:34:20 Sisif dhclient: No DHCPOFFERS received.
Apr 30 01:34:20 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 01:34:20 Sisif avahi-autoipd(eth0)[8702]: A routable address has been configured.
Apr 30 01:34:20 Sisif avahi-autoipd(eth0)[8702]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 01:34:20 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:34:20 Sisif avahi-daemon[5428]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 01:34:20 Sisif avahi-daemon[5428]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 01:34:20 Sisif avahi-daemon[5428]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 01:34:23 Sisif avahi-daemon[5428]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 01:34:23 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 01:34:23 Sisif avahi-autoipd(eth0)[8702]: No longer a routable address configured, restarting probe process.
Apr 30 01:34:23 Sisif avahi-daemon[5428]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 01:34:23 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 01:34:28 Sisif avahi-autoipd(eth0)[8702]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 01:34:28 Sisif avahi-daemon[5428]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:34:28 Sisif avahi-daemon[5428]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 01:34:28 Sisif avahi-daemon[5428]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 01:34:32 Sisif avahi-autoipd(eth0)[8702]: Successfully claimed IP address 169.254.9.233
Apr 30 01:41:52 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 30 01:42:00 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Apr 30 01:42:16 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 30 01:42:23 Sisif dhclient: No DHCPOFFERS received.
Apr 30 01:42:23 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 01:42:23 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:42:23 Sisif avahi-autoipd(eth0)[8702]: A routable address has been configured.
Apr 30 01:42:23 Sisif avahi-autoipd(eth0)[8702]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 01:42:23 Sisif avahi-daemon[5428]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 01:42:23 Sisif avahi-daemon[5428]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 01:42:23 Sisif avahi-daemon[5428]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 01:42:26 Sisif avahi-autoipd(eth0)[8702]: No longer a routable address configured, restarting probe process.
Apr 30 01:42:26 Sisif avahi-daemon[5428]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 01:42:26 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 01:42:26 Sisif avahi-daemon[5428]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 01:42:26 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 01:42:32 Sisif avahi-autoipd(eth0)[8702]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 01:42:32 Sisif avahi-daemon[5428]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:42:32 Sisif avahi-daemon[5428]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 01:42:32 Sisif avahi-daemon[5428]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 01:42:36 Sisif avahi-autoipd(eth0)[8702]: Successfully claimed IP address 169.254.9.233
Apr 30 01:47:30 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 30 01:47:36 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 30 01:47:45 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 30 01:47:56 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 30 01:48:01 Sisif dhclient: No DHCPOFFERS received.
Apr 30 01:48:01 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 01:48:01 Sisif avahi-autoipd(eth0)[8702]: A routable address has been configured.
Apr 30 01:48:01 Sisif avahi-autoipd(eth0)[8702]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 01:48:01 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:48:01 Sisif avahi-daemon[5428]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 01:48:01 Sisif avahi-daemon[5428]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 01:48:01 Sisif avahi-daemon[5428]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 01:48:04 Sisif avahi-autoipd(eth0)[8702]: No longer a routable address configured, restarting probe process.
Apr 30 01:48:04 Sisif avahi-daemon[5428]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 01:48:04 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 01:48:04 Sisif avahi-daemon[5428]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 01:48:04 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 01:48:09 Sisif avahi-autoipd(eth0)[8702]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 01:48:09 Sisif avahi-daemon[5428]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:48:09 Sisif avahi-daemon[5428]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 01:48:09 Sisif avahi-daemon[5428]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 01:48:13 Sisif avahi-autoipd(eth0)[8702]: Successfully claimed IP address 169.254.9.233
Apr 30 01:54:33 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 30 01:54:41 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr 30 01:54:56 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 30 01:55:04 Sisif dhclient: No DHCPOFFERS received.
Apr 30 01:55:04 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 01:55:04 Sisif avahi-autoipd(eth0)[8702]: A routable address has been configured.
Apr 30 01:55:04 Sisif avahi-autoipd(eth0)[8702]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 01:55:04 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:55:04 Sisif avahi-daemon[5428]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 01:55:04 Sisif avahi-daemon[5428]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 01:55:04 Sisif avahi-daemon[5428]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 01:55:07 Sisif avahi-autoipd(eth0)[8702]: No longer a routable address configured, restarting probe process.
Apr 30 01:55:07 Sisif avahi-daemon[5428]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 01:55:07 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 01:55:07 Sisif avahi-daemon[5428]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 01:55:07 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 01:55:12 Sisif avahi-autoipd(eth0)[8702]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 01:55:12 Sisif avahi-daemon[5428]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:55:12 Sisif avahi-daemon[5428]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 01:55:12 Sisif avahi-daemon[5428]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 01:55:16 Sisif avahi-autoipd(eth0)[8702]: Successfully claimed IP address 169.254.9.233
Apr 30 01:57:59 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 30 01:58:04 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 30 01:58:17 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 30 01:58:24 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 30 01:58:30 Sisif dhclient: No DHCPOFFERS received.
Apr 30 01:58:30 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 01:58:30 Sisif avahi-autoipd(eth0)[8702]: A routable address has been configured.
Apr 30 01:58:30 Sisif avahi-autoipd(eth0)[8702]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 01:58:30 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:58:30 Sisif avahi-daemon[5428]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 01:58:30 Sisif avahi-daemon[5428]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 01:58:30 Sisif avahi-daemon[5428]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 01:58:33 Sisif avahi-autoipd(eth0)[8702]: No longer a routable address configured, restarting probe process.
Apr 30 01:58:33 Sisif avahi-daemon[5428]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 01:58:33 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 01:58:33 Sisif avahi-daemon[5428]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 01:58:33 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 01:58:38 Sisif avahi-autoipd(eth0)[8702]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 01:58:38 Sisif avahi-daemon[5428]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:58:38 Sisif avahi-daemon[5428]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 01:58:38 Sisif avahi-daemon[5428]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 01:58:42 Sisif avahi-autoipd(eth0)[8702]: Successfully claimed IP address 169.254.9.233
Apr 30 01:59:02 Sisif init: tty4 main process (4825) killed by TERM signal
Apr 30 01:59:02 Sisif init: tty5 main process (4826) killed by TERM signal
Apr 30 01:59:02 Sisif init: tty2 main process (4830) killed by TERM signal
Apr 30 01:59:02 Sisif init: tty3 main process (4831) killed by TERM signal
Apr 30 01:59:02 Sisif init: tty1 main process (6348) killed by TERM signal
Apr 30 01:59:02 Sisif init: tty6 main process (4832) killed by TERM signal
Apr 30 01:59:04 Sisif kernel: [ 4166.708726] gdm[5833]: segfault at 7672657f eip b78477e2 esp bf91eb90 error 6
Apr 30 01:59:04 Sisif avahi-daemon[5428]: Got SIGTERM, quitting.
Apr 30 01:59:04 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 01:59:04 Sisif avahi-daemon[5428]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 01:59:04 Sisif nmbd[5705]: [2008/04/30 01:59:04, 0] nmbd/nmbd.c:terminate(58) 
Apr 30 01:59:04 Sisif nmbd[5705]:   Got SIGTERM: going down... 
Apr 30 01:59:06 Sisif rpc.statd[4551]: Caught signal 15, un-registering and exiting.
Apr 30 01:59:08 Sisif kernel: [ 4171.154503] ip6_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 01:59:10 Sisif kernel: [ 4172.525451] nfsd: last server has exited
Apr 30 01:59:10 Sisif kernel: [ 4172.525456] nfsd: unexporting all filesystems
Apr 30 01:59:10 Sisif mountd[5660]: Caught signal 15, un-registering and exiting.
Apr 30 01:59:10 Sisif exiting on signal 15
Apr 30 01:59:53 Sisif syslogd 1.5.0#1ubuntu1: restart.
Apr 30 01:59:53 Sisif kernel: Inspecting /boot/System.map-2.6.24-16-generic
Apr 30 01:59:53 Sisif kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Apr 30 01:59:53 Sisif kernel: Symbols match kernel version 2.6.24.
Apr 30 01:59:53 Sisif kernel: Loaded 22525 symbols from 99 modules.
Apr 30 01:59:53 Sisif kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Apr 30 01:59:53 Sisif kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 30 01:59:53 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 30 01:59:53 Sisif kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 30 01:59:53 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d3400 (usable)
Apr 30 01:59:53 Sisif kernel: [    0.000000]  BIOS-e820: 000000007f6d3400 - 0000000080000000 (reserved)
Apr 30 01:59:53 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Apr 30 01:59:53 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Apr 30 01:59:53 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 30 01:59:53 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Apr 30 01:59:53 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Apr 30 01:59:53 Sisif kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr 30 01:59:53 Sisif kernel: [    0.000000] 1142MB HIGHMEM available.
Apr 30 01:59:53 Sisif kernel: [    0.000000] 896MB LOWMEM available.
Apr 30 01:59:53 Sisif kernel: [    0.000000] Entering add_active_range(0, 0, 521939) 0 entries of 256 used
Apr 30 01:59:53 Sisif kernel: [    0.000000] Zone PFN ranges:
Apr 30 01:59:53 Sisif kernel: [    0.000000]   DMA             0 ->     4096
Apr 30 01:59:53 Sisif kernel: [    0.000000]   Normal       4096 ->   229376
Apr 30 01:59:53 Sisif kernel: [    0.000000]   HighMem    229376 ->   521939
Apr 30 01:59:53 Sisif kernel: [    0.000000] Movable zone start PFN for each node
Apr 30 01:59:53 Sisif kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 30 01:59:53 Sisif kernel: [    0.000000]     0:        0 ->   521939
Apr 30 01:59:53 Sisif kernel: [    0.000000] On node 0 totalpages: 521939
Apr 30 01:59:53 Sisif kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 30 01:59:53 Sisif kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 30 01:59:53 Sisif kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 30 01:59:53 Sisif kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Apr 30 01:59:53 Sisif kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Apr 30 01:59:53 Sisif kernel: [    0.000000]   HighMem zone: 2285 pages used for memmap
Apr 30 01:59:53 Sisif kernel: [    0.000000]   HighMem zone: 290278 pages, LIFO batch:31
Apr 30 01:59:53 Sisif kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 30 01:59:53 Sisif kernel: [    0.000000] DMI 2.4 present.
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: RSDT 7F6D39CD, 0040 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: FACP 7F6D4800, 0074 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: DSDT 7F6D5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: FACS 7F6E3C00, 0040
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: HPET 7F6D4F00, 0038 (r1 DELL    M07            1 ASL        61)
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: APIC 7F6D5000, 0068 (r1 DELL    M07     27D7060D ASL        47)
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: MCFG 7F6D4FC0, 003E (r16 DELL    M07     27D7060D ASL        61)
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: SLIC 7F6D509C, 0024 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: BOOT 7F6D4BC0, 0028 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: SSDT 7F6D3A0D, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 30 01:59:53 Sisif kernel: [    0.000000] Processor #0 6:14 APIC version 20
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 30 01:59:53 Sisif kernel: [    0.000000] Processor #1 6:14 APIC version 20
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 30 01:59:53 Sisif kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 30 01:59:53 Sisif kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 30 01:59:53 Sisif kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 30 01:59:53 Sisif kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 30 01:59:53 Sisif kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
Apr 30 01:59:53 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 30 01:59:53 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Apr 30 01:59:53 Sisif kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517862
Apr 30 01:59:53 Sisif kernel: [    0.000000] Kernel command line: root=UUID=35a5e031-c7e9-4597-9992-99d1d88d0eac ro quiet splash
Apr 30 01:59:53 Sisif kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Apr 30 01:59:53 Sisif kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Apr 30 01:59:53 Sisif kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 30 01:59:53 Sisif kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 30 01:59:53 Sisif kernel: [    0.000000] Initializing CPU#0
Apr 30 01:59:53 Sisif kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 30 01:59:53 Sisif kernel: [    0.000000] Detected 1729.069 MHz processor.
Apr 30 01:59:53 Sisif kernel: [    7.503056] Console: colour VGA+ 80x25
Apr 30 01:59:53 Sisif kernel: [    7.503059] console [tty0] enabled
Apr 30 01:59:53 Sisif kernel: [    7.503363] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 30 01:59:53 Sisif kernel: [    7.503761] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 30 01:59:53 Sisif kernel: [    7.625959] Memory: 2057924k/2087756k available (2157k kernel code, 28552k reserved, 998k data, 364k init, 1170252k highmem)
Apr 30 01:59:53 Sisif kernel: [    7.625968] virtual kernel memory layout:
Apr 30 01:59:53 Sisif kernel: [    7.625970]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Apr 30 01:59:53 Sisif kernel: [    7.625971]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 30 01:59:53 Sisif kernel: [    7.625972]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Apr 30 01:59:53 Sisif kernel: [    7.625973]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 30 01:59:53 Sisif kernel: [    7.625975]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Apr 30 01:59:53 Sisif kernel: [    7.625976]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Apr 30 01:59:53 Sisif kernel: [    7.625977]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Apr 30 01:59:53 Sisif kernel: [    7.625981] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 30 01:59:53 Sisif kernel: [    7.626024] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 30 01:59:53 Sisif kernel: [    7.626172] hpet clockevent registered
Apr 30 01:59:53 Sisif kernel: [    7.706145] Calibrating delay using timer specific routine.. 3461.90 BogoMIPS (lpj=6923819)
Apr 30 01:59:53 Sisif kernel: [    7.706168] Security Framework initialized
Apr 30 01:59:53 Sisif kernel: [    7.706177] SELinux:  Disabled at boot.
Apr 30 01:59:53 Sisif kernel: [    7.706193] AppArmor: AppArmor initialized
Apr 30 01:59:53 Sisif kernel: [    7.706197] Failure registering capabilities with primary security module.
Apr 30 01:59:53 Sisif kernel: [    7.706206] Mount-cache hash table entries: 512
Apr 30 01:59:53 Sisif kernel: [    7.706343] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 01:59:53 Sisif kernel: [    7.706353] monitor/mwait feature present.
Apr 30 01:59:53 Sisif kernel: [    7.706355] using mwait in idle threads.
Apr 30 01:59:53 Sisif kernel: [    7.706359] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 01:59:53 Sisif kernel: [    7.706361] CPU: L2 cache: 1024K
Apr 30 01:59:53 Sisif kernel: [    7.706364] CPU: Physical Processor ID: 0
Apr 30 01:59:53 Sisif kernel: [    7.706366] CPU: Processor Core ID: 0
Apr 30 01:59:53 Sisif kernel: [    7.706368] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 01:59:53 Sisif kernel: [    7.706378] Compat vDSO mapped to ffffe000.
Apr 30 01:59:53 Sisif kernel: [    7.706391] Checking 'hlt' instruction... OK.
Apr 30 01:59:53 Sisif kernel: [    7.722544] SMP alternatives: switching to UP code
Apr 30 01:59:53 Sisif kernel: [    7.724384] Early unpacking initramfs... done
Apr 30 01:59:53 Sisif kernel: [    8.074447] ACPI: Core revision 20070126
Apr 30 01:59:53 Sisif kernel: [    8.074505] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 30 01:59:53 Sisif kernel: [    8.077182] CPU0: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 01:59:53 Sisif kernel: [    8.077200] SMP alternatives: switching to SMP code
Apr 30 01:59:53 Sisif kernel: [    8.077916] Booting processor 1/1 eip 3000
Apr 30 01:59:53 Sisif kernel: [   10.104689] Initializing CPU#1
Apr 30 01:59:53 Sisif kernel: [   10.184637] Calibrating delay using timer specific routine.. 3458.09 BogoMIPS (lpj=6916196)
Apr 30 01:59:53 Sisif kernel: [   10.184645] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 01:59:53 Sisif kernel: [   10.184651] monitor/mwait feature present.
Apr 30 01:59:53 Sisif kernel: [   10.184654] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 01:59:53 Sisif kernel: [   10.184656] CPU: L2 cache: 1024K
Apr 30 01:59:53 Sisif kernel: [   10.184658] CPU: Physical Processor ID: 0
Apr 30 01:59:53 Sisif kernel: [   10.184660] CPU: Processor Core ID: 1
Apr 30 01:59:53 Sisif kernel: [   10.184661] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 01:59:53 Sisif kernel: [    8.170399] CPU1: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 01:59:53 Sisif kernel: [    8.170423] Total of 2 processors activated (6920.00 BogoMIPS).
Apr 30 01:59:53 Sisif kernel: [    8.170623] ENABLING IO-APIC IRQs
Apr 30 01:59:53 Sisif kernel: [    8.170820] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 30 01:59:53 Sisif kernel: [    8.318000] checking TSC synchronization [CPU#0 -> CPU#1]:
Apr 30 01:59:53 Sisif kernel: [    8.338000] Measured 3484880503 cycles TSC warp between CPUs, turning off TSC clock.
Apr 30 01:59:53 Sisif kernel: [    8.338003] Marking TSC unstable due to: check_tsc_sync_source failed.
Apr 30 01:59:53 Sisif kernel: [    8.338019] Brought up 2 CPUs
Apr 30 01:59:53 Sisif kernel: [    8.338046] CPU0 attaching sched-domain:
Apr 30 01:59:53 Sisif kernel: [    8.338048]  domain 0: span 03
Apr 30 01:59:53 Sisif kernel: [    8.338050]   groups: 01 02
Apr 30 01:59:53 Sisif kernel: [    8.338053] CPU1 attaching sched-domain:
Apr 30 01:59:53 Sisif kernel: [    8.338055]  domain 0: span 03
Apr 30 01:59:53 Sisif kernel: [    8.338057]   groups: 02 01
Apr 30 01:59:53 Sisif kernel: [   10.353017] net_namespace: 64 bytes
Apr 30 01:59:53 Sisif kernel: [   10.353027] Booting paravirtualized kernel on bare hardware
Apr 30 01:59:53 Sisif kernel: [   10.353525] Time: 22:59:30  Date: 04/29/08
Apr 30 01:59:53 Sisif kernel: [   10.353554] NET: Registered protocol family 16
Apr 30 01:59:53 Sisif kernel: [   10.353773] EISA bus registered
Apr 30 01:59:53 Sisif kernel: [   10.353778] ACPI: bus type pci registered
Apr 30 01:59:53 Sisif kernel: [   10.382320] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=13
Apr 30 01:59:53 Sisif kernel: [   10.382322] PCI: Using configuration type 1
Apr 30 01:59:53 Sisif kernel: [   10.382324] Setting up standard PCI resources
Apr 30 01:59:53 Sisif kernel: [    8.373369] ACPI: EC: Look up EC in DSDT
Apr 30 01:59:53 Sisif kernel: [    8.378274] ACPI: Interpreter enabled
Apr 30 01:59:53 Sisif kernel: [    8.378278] ACPI: (supports S0 S3 S4 S5)
Apr 30 01:59:53 Sisif kernel: [    8.378292] ACPI: Using IOAPIC for interrupt routing
Apr 30 01:59:53 Sisif kernel: [    8.392363] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 30 01:59:53 Sisif kernel: [    8.393164] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 30 01:59:53 Sisif kernel: [    8.393169] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Apr 30 01:59:53 Sisif kernel: [   10.409030] PCI: Transparent bridge - 0000:00:1e.0
Apr 30 01:59:53 Sisif kernel: [   10.409069] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 30 01:59:53 Sisif kernel: [   10.409527] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr 30 01:59:53 Sisif kernel: [   10.409660] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 30 01:59:53 Sisif kernel: [   10.409781] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr 30 01:59:53 Sisif kernel: [   10.418182] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr 30 01:59:53 Sisif kernel: [   10.418294] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
Apr 30 01:59:53 Sisif kernel: [   10.418403] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr 30 01:59:53 Sisif kernel: [   10.418511] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Apr 30 01:59:53 Sisif kernel: [   10.418620] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 30 01:59:53 Sisif kernel: [   10.418731] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 30 01:59:53 Sisif kernel: [   10.418842] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Apr 30 01:59:53 Sisif kernel: [   10.418952] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Apr 30 01:59:53 Sisif kernel: [   10.419111] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 30 01:59:53 Sisif kernel: [   10.419145] pnp: PnP ACPI init
Apr 30 01:59:53 Sisif kernel: [   10.419155] ACPI: bus type pnp registered
Apr 30 01:59:53 Sisif kernel: [   10.435431] pnpacpi: exceeded the max number of mem resources: 12
Apr 30 01:59:53 Sisif kernel: [   10.448282] pnp: PnP ACPI: found 12 devices
Apr 30 01:59:53 Sisif kernel: [   10.448285] ACPI: ACPI bus type pnp unregistered
Apr 30 01:59:53 Sisif kernel: [   10.448289] PnPBIOS: Disabled by ACPI PNP
Apr 30 01:59:53 Sisif kernel: [    8.433846] PCI: Using ACPI for IRQ routing
Apr 30 01:59:53 Sisif kernel: [    8.433850] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 30 01:59:53 Sisif kernel: [    8.497828] NET: Registered protocol family 8
Apr 30 01:59:53 Sisif kernel: [    8.497830] NET: Registered protocol family 20
Apr 30 01:59:53 Sisif kernel: [    8.497868] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 30 01:59:53 Sisif kernel: [    8.497873] hpet0: 3 64-bit timers, 14318180 Hz
Apr 30 01:59:53 Sisif kernel: [    8.498915] AppArmor: AppArmor Filesystem Enabled
Apr 30 01:59:53 Sisif kernel: [    8.501804] Time: hpet clocksource has been installed.
Apr 30 01:59:53 Sisif kernel: [    8.501825] Switched to high resolution mode on CPU 0
Apr 30 01:59:53 Sisif kernel: [   10.516638] Switched to high resolution mode on CPU 1
Apr 30 01:59:53 Sisif kernel: [    8.513799] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513803] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513806] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513809] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513812] system 00:00: iomem range 0x100000-0x7f6d33ff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513815] system 00:00: iomem range 0x7f6d3400-0x7f6fffff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513818] system 00:00: iomem range 0x7f700000-0x7f7fffff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513821] system 00:00: iomem range 0x7f700000-0x7fefffff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513825] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513828] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513831] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513835] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513842] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513845] system 00:02: ioport range 0x1000-0x1005 has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513848] system 00:02: ioport range 0x1008-0x100f has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513854] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513857] system 00:03: ioport range 0x1006-0x1007 has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513860] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513864] system 00:03: ioport range 0x1060-0x107f has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513867] system 00:03: ioport range 0x1080-0x10bf has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513870] system 00:03: ioport range 0x10c0-0x10df has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513873] system 00:03: ioport range 0x1010-0x102f has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513876] system 00:03: ioport range 0x809-0x809 has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513884] system 00:08: ioport range 0xc80-0xcff could not be reserved
Apr 30 01:59:53 Sisif kernel: [    8.513887] system 00:08: ioport range 0x910-0x91f has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513890] system 00:08: ioport range 0x920-0x92f has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513893] system 00:08: ioport range 0xcb0-0xcbf has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513896] system 00:08: ioport range 0x930-0x97f has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.513906] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Apr 30 01:59:53 Sisif kernel: [    8.544365] PCI: Bridge: 0000:00:1c.0
Apr 30 01:59:53 Sisif kernel: [    8.544367]   IO window: disabled.
Apr 30 01:59:53 Sisif kernel: [    8.544373]   MEM window: efd00000-efdfffff
Apr 30 01:59:53 Sisif kernel: [    8.544378]   PREFETCH window: disabled.
Apr 30 01:59:53 Sisif kernel: [    8.544384] PCI: Bridge: 0000:00:1c.3
Apr 30 01:59:53 Sisif kernel: [    8.544387]   IO window: d000-dfff
Apr 30 01:59:53 Sisif kernel: [    8.544393]   MEM window: efa00000-efcfffff
Apr 30 01:59:53 Sisif kernel: [    8.544397]   PREFETCH window: e0000000-e01fffff
Apr 30 01:59:53 Sisif kernel: [    8.544404] PCI: Bridge: 0000:00:1e.0
Apr 30 01:59:53 Sisif kernel: [    8.544406]   IO window: disabled.
Apr 30 01:59:53 Sisif kernel: [    8.544412]   MEM window: ef900000-ef9fffff
Apr 30 01:59:53 Sisif kernel: [    8.544416]   PREFETCH window: disabled.
Apr 30 01:59:53 Sisif kernel: [    8.544451] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 01:59:53 Sisif kernel: [    8.544459] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 01:59:53 Sisif kernel: [    8.544484] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Apr 30 01:59:53 Sisif kernel: [    8.544490] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 01:59:53 Sisif kernel: [    8.544504] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 30 01:59:53 Sisif kernel: [    8.544517] NET: Registered protocol family 2
Apr 30 01:59:53 Sisif kernel: [    8.581792] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 30 01:59:53 Sisif kernel: [    8.582031] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 30 01:59:53 Sisif kernel: [    8.582771] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 30 01:59:53 Sisif kernel: [    8.583147] TCP: Hash tables configured (established 131072 bind 65536)
Apr 30 01:59:53 Sisif kernel: [    8.583152] TCP reno registered
Apr 30 01:59:53 Sisif kernel: [    8.593893] checking if image is initramfs... it is
Apr 30 01:59:53 Sisif kernel: [    9.286816] Freeing initrd memory: 7267k freed
Apr 30 01:59:53 Sisif kernel: [    9.286988] Simple Boot Flag at 0x79 set to 0x1
Apr 30 01:59:53 Sisif kernel: [   11.302425] audit: initializing netlink socket (disabled)
Apr 30 01:59:53 Sisif kernel: [   11.302441] audit(1209509970.536:1): initialized
Apr 30 01:59:53 Sisif kernel: [    9.287989] highmem bounce pool size: 64 pages
Apr 30 01:59:53 Sisif kernel: [    9.290145] VFS: Disk quotas dquot_6.5.1
Apr 30 01:59:53 Sisif kernel: [    9.290230] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 30 01:59:53 Sisif kernel: [    9.290376] io scheduler noop registered
Apr 30 01:59:53 Sisif kernel: [    9.290378] io scheduler anticipatory registered
Apr 30 01:59:53 Sisif kernel: [    9.290380] io scheduler deadline registered
Apr 30 01:59:53 Sisif kernel: [    9.290392] io scheduler cfq registered (default)
Apr 30 01:59:53 Sisif kernel: [    9.290405] Boot video device is 0000:00:02.0
Apr 30 01:59:53 Sisif kernel: [    9.290625] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 01:59:53 Sisif kernel: [    9.290684] assign_interrupt_mode Found MSI capability
Apr 30 01:59:53 Sisif kernel: [    9.290735] Allocate Port Service[0000:00:1c.0:pcie00]
Apr 30 01:59:53 Sisif kernel: [    9.290776] Allocate Port Service[0000:00:1c.0:pcie02]
Apr 30 01:59:53 Sisif kernel: [    9.290882] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 01:59:53 Sisif kernel: [    9.290941] assign_interrupt_mode Found MSI capability
Apr 30 01:59:53 Sisif kernel: [    9.290988] Allocate Port Service[0000:00:1c.3:pcie00]
Apr 30 01:59:53 Sisif kernel: [    9.291023] Allocate Port Service[0000:00:1c.3:pcie02]
Apr 30 01:59:53 Sisif kernel: [    9.291310] isapnp: Scanning for PnP cards...
Apr 30 01:59:53 Sisif kernel: [    9.645464] isapnp: No Plug & Play device found
Apr 30 01:59:53 Sisif kernel: [   11.690112] Real Time Clock Driver v1.12ac
Apr 30 01:59:53 Sisif kernel: [   11.690272] hpet_resources: 0xfed00000 is busy
Apr 30 01:59:53 Sisif kernel: [   11.690328] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 30 01:59:53 Sisif kernel: [   11.691612] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 30 01:59:53 Sisif kernel: [   11.691687] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 30 01:59:53 Sisif kernel: [   11.691800] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 30 01:59:53 Sisif kernel: [    9.680058] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 30 01:59:53 Sisif kernel: [    9.680065] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 30 01:59:53 Sisif kernel: [   11.720094] mice: PS/2 mouse device common for all mice
Apr 30 01:59:53 Sisif kernel: [   11.720226] EISA: Probing bus 0 at eisa.0
Apr 30 01:59:53 Sisif kernel: [   11.720294] EISA: Mainboard UO_FFFF detected.
Apr 30 01:59:53 Sisif kernel: [   11.720336] Cannot allocate resource for EISA slot 1
Apr 30 01:59:53 Sisif kernel: [   11.720367] EISA: Detected 0 cards.
Apr 30 01:59:53 Sisif kernel: [   11.720370] cpuidle: using governor ladder
Apr 30 01:59:53 Sisif kernel: [   11.720372] cpuidle: using governor menu
Apr 30 01:59:53 Sisif kernel: [   11.720464] NET: Registered protocol family 1
Apr 30 01:59:53 Sisif kernel: [   11.720495] Using IPI No-Shortcut mode
Apr 30 01:59:53 Sisif kernel: [   11.720528] registered taskstats version 1
Apr 30 01:59:53 Sisif kernel: [   11.720641]   Magic number: 4:943:1008
Apr 30 01:59:53 Sisif kernel: [   11.720647]   hash matches device ttye7
Apr 30 01:59:53 Sisif kernel: [   11.720654]   hash matches device ttyba
Apr 30 01:59:53 Sisif kernel: [   11.720755] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 30 01:59:53 Sisif kernel: [   11.720757] EDD information not available.
Apr 30 01:59:53 Sisif kernel: [   11.720940] Freeing unused kernel memory: 364k freed
Apr 30 01:59:53 Sisif kernel: [   11.723114] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 30 01:59:53 Sisif kernel: [   10.924313] fuse init (API version 7.9)
Apr 30 01:59:53 Sisif kernel: [   12.960389] ACPI: SSDT 7F6D4134, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Apr 30 01:59:53 Sisif kernel: [   12.960582] ACPI: SSDT 7F6D3EE9, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Apr 30 01:59:53 Sisif kernel: [   10.946489] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 01:59:53 Sisif kernel: [   10.946496] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 30 01:59:53 Sisif kernel: [   10.946728] ACPI: SSDT 7F6D4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Apr 30 01:59:53 Sisif kernel: [   10.946902] ACPI: SSDT 7F6D40AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Apr 30 01:59:53 Sisif kernel: [   12.962256] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 01:59:53 Sisif kernel: [   12.962262] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 30 01:59:53 Sisif kernel: [   12.967974] ACPI: Thermal Zone [THM] (41 C)
Apr 30 01:59:53 Sisif kernel: [   11.367779] usbcore: registered new interface driver usbfs
Apr 30 01:59:53 Sisif kernel: [   11.367804] usbcore: registered new interface driver hub
Apr 30 01:59:53 Sisif kernel: [   11.367956] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 01:59:53 Sisif kernel: [   11.367978] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 01:59:53 Sisif kernel: [   11.368583] usbcore: registered new device driver usb
Apr 30 01:59:53 Sisif kernel: [   11.369921] USB Universal Host Controller Interface driver v3.0
Apr 30 01:59:53 Sisif kernel: [   11.424544] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Apr 30 01:59:53 Sisif kernel: [   11.424589] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 01:59:53 Sisif kernel: [   11.424602] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 30 01:59:53 Sisif kernel: [   11.424606] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 30 01:59:53 Sisif kernel: [   11.424887] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr 30 01:59:53 Sisif kernel: [   11.424925] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
Apr 30 01:59:53 Sisif kernel: [   11.425071] usb usb1: configuration #1 chosen from 1 choice
Apr 30 01:59:53 Sisif kernel: [   11.425095] hub 1-0:1.0: USB hub found
Apr 30 01:59:53 Sisif kernel: [   11.425101] hub 1-0:1.0: 2 ports detected
Apr 30 01:59:53 Sisif kernel: [   13.462425] SCSI subsystem initialized
Apr 30 01:59:53 Sisif kernel: [   13.487776] libata version 3.00 loaded.
Apr 30 01:59:53 Sisif kernel: [   11.528467] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
Apr 30 01:59:53 Sisif kernel: [   11.528480] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 30 01:59:53 Sisif kernel: [   11.528485] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 30 01:59:53 Sisif kernel: [   11.528510] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr 30 01:59:53 Sisif kernel: [   11.528544] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bf60
Apr 30 01:59:53 Sisif kernel: [   11.528661] usb usb2: configuration #1 chosen from 1 choice
Apr 30 01:59:53 Sisif kernel: [   11.528685] hub 2-0:1.0: USB hub found
Apr 30 01:59:53 Sisif kernel: [   11.528691] hub 2-0:1.0: 2 ports detected
Apr 30 01:59:53 Sisif kernel: [   11.632445] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
Apr 30 01:59:53 Sisif kernel: [   11.632460] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 30 01:59:53 Sisif kernel: [   11.632465] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 30 01:59:53 Sisif kernel: [   11.632490] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr 30 01:59:53 Sisif kernel: [   11.632528] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000bf40
Apr 30 01:59:53 Sisif kernel: [   11.632656] usb usb3: configuration #1 chosen from 1 choice
Apr 30 01:59:53 Sisif kernel: [   11.632682] hub 3-0:1.0: USB hub found
Apr 30 01:59:53 Sisif kernel: [   11.632688] hub 3-0:1.0: 2 ports detected
Apr 30 01:59:53 Sisif kernel: [   13.751091] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
Apr 30 01:59:53 Sisif kernel: [   13.751105] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Apr 30 01:59:53 Sisif kernel: [   13.751110] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Apr 30 01:59:53 Sisif kernel: [   13.751137] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Apr 30 01:59:53 Sisif kernel: [   13.751172] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000bf20
Apr 30 01:59:53 Sisif kernel: [   13.751303] usb usb4: configuration #1 chosen from 1 choice
Apr 30 01:59:53 Sisif kernel: [   13.751330] hub 4-0:1.0: USB hub found
Apr 30 01:59:53 Sisif kernel: [   13.751335] hub 4-0:1.0: 2 ports detected
Apr 30 01:59:53 Sisif kernel: [   11.841367] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 01:59:53 Sisif kernel: [   11.841384] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 30 01:59:53 Sisif kernel: [   11.841388] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 30 01:59:53 Sisif kernel: [   11.841418] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Apr 30 01:59:53 Sisif kernel: [   11.845343] ehci_hcd 0000:00:1d.7: debug port 1
Apr 30 01:59:53 Sisif kernel: [   11.845351] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr 30 01:59:53 Sisif kernel: [   11.845359] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80000
Apr 30 01:59:53 Sisif kernel: [   11.860216] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 30 01:59:53 Sisif kernel: [   11.860345] usb usb5: configuration #1 chosen from 1 choice
Apr 30 01:59:53 Sisif kernel: [   11.860372] hub 5-0:1.0: USB hub found
Apr 30 01:59:53 Sisif kernel: [   11.860379] hub 5-0:1.0: 8 ports detected
Apr 30 01:59:53 Sisif kernel: [   13.979028] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 01:59:53 Sisif kernel: [   14.042907] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 01:59:53 Sisif kernel: [   14.042944] b44.c:v2.0
Apr 30 01:59:53 Sisif kernel: [   14.063181] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 01:59:53 Sisif kernel: [   14.063456] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Apr 30 01:59:53 Sisif kernel: [   14.116162] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 30 01:59:53 Sisif kernel: [   12.115838] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 01:59:53 Sisif kernel: [   12.115878] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 01:59:53 Sisif kernel: [   12.115892] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Apr 30 01:59:53 Sisif kernel: [   12.119420] ata_piix 0000:00:1f.2: version 2.12
Apr 30 01:59:53 Sisif kernel: [   12.119427] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Apr 30 01:59:53 Sisif kernel: [   12.119447] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 01:59:53 Sisif kernel: [   12.119483] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 01:59:53 Sisif kernel: [   12.119817] scsi0 : ata_piix
Apr 30 01:59:53 Sisif kernel: [   12.119874] scsi1 : ata_piix
Apr 30 01:59:53 Sisif kernel: [   12.120732] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Apr 30 01:59:53 Sisif kernel: [   12.120736] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Apr 30 01:59:53 Sisif kernel: [   12.282353] ata1.00: ATA-7: ST9120822AS, 3.CDD, max UDMA/133
Apr 30 01:59:53 Sisif kernel: [   12.282357] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
Apr 30 01:59:53 Sisif kernel: [   12.297159] ata1.00: configured for UDMA/133
Apr 30 01:59:53 Sisif kernel: [   14.655049] ata2.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1B, max UDMA/33
Apr 30 01:59:53 Sisif kernel: [   14.850894] ata2.00: configured for UDMA/33
Apr 30 01:59:53 Sisif kernel: [   12.836387] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.CD PQ: 0 ANSI: 5
Apr 30 01:59:53 Sisif kernel: [   12.838663] scsi 1:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
Apr 30 01:59:53 Sisif kernel: [   12.846275] Driver 'sd' needs updating - please use bus_type methods
Apr 30 01:59:53 Sisif kernel: [   12.846367] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 01:59:53 Sisif kernel: [   12.846380] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 01:59:53 Sisif kernel: [   12.846383] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 01:59:53 Sisif kernel: [   12.846401] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 01:59:53 Sisif kernel: [   12.846452] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 01:59:53 Sisif kernel: [   12.846462] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 01:59:53 Sisif kernel: [   12.846465] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 01:59:53 Sisif kernel: [   12.846481] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 01:59:53 Sisif kernel: [   12.846486]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Apr 30 01:59:53 Sisif kernel: [   12.941405]  sda1 sda2 sda3
Apr 30 01:59:53 Sisif kernel: [   12.953687] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 30 01:59:53 Sisif kernel: [   12.959297] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 30 01:59:53 Sisif kernel: [   12.959319] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 30 01:59:53 Sisif kernel: [   14.985432] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr 30 01:59:53 Sisif kernel: [   14.985438] Uniform CD-ROM driver Revision: 3.20
Apr 30 01:59:53 Sisif kernel: [   14.985492] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 30 01:59:53 Sisif kernel: [   15.398540] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc00026e60070]
Apr 30 01:59:53 Sisif kernel: [   15.490320] Attempting manual resume
Apr 30 01:59:53 Sisif kernel: [   15.490324] swsusp: Resume From Partition 8:2
Apr 30 01:59:53 Sisif kernel: [   15.490326] PM: Checking swsusp image.
Apr 30 01:59:53 Sisif kernel: [   13.475807] PM: Resume from disk failed.
Apr 30 01:59:53 Sisif kernel: [   15.532872] kjournald starting.  Commit interval 5 seconds
Apr 30 01:59:53 Sisif kernel: [   13.518202] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 01:59:53 Sisif kernel: [   24.395652] input: PC Speaker as /devices/platform/pcspkr/input/input2
Apr 30 01:59:53 Sisif kernel: [   24.623486] Linux agpgart interface v0.102
Apr 30 01:59:53 Sisif kernel: [   22.687676] agpgart: Detected an Intel 945GM Chipset.
Apr 30 01:59:53 Sisif kernel: [   22.688264] agpgart: Detected 7932K stolen memory.
Apr 30 01:59:53 Sisif kernel: [   22.706188] agpgart: AGP aperture is 256M @ 0xd0000000
Apr 30 01:59:53 Sisif kernel: [   22.930945] iTCO_vendor_support: vendor-support=0
Apr 30 01:59:53 Sisif kernel: [   22.963045] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Apr 30 01:59:53 Sisif kernel: [   23.152258] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 30 01:59:53 Sisif kernel: [   23.180169] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
Apr 30 01:59:53 Sisif kernel: [   23.216089] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input3
Apr 30 01:59:53 Sisif kernel: [   23.270815] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Apr 30 01:59:53 Sisif kernel: [   23.270859] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 30 01:59:53 Sisif kernel: [   23.270899] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Apr 30 01:59:53 Sisif kernel: [   23.298008] ACPI: Battery Slot [BAT0] (battery present)
Apr 30 01:59:53 Sisif kernel: [   23.312263] ACPI: AC Adapter [AC] (on-line)
Apr 30 01:59:53 Sisif kernel: [   23.341235] input: Lid Switch as /devices/virtual/input/input4
Apr 30 01:59:53 Sisif kernel: [   23.351153] ACPI: Lid Switch [LID]
Apr 30 01:59:53 Sisif kernel: [   23.351211] input: Power Button (CM) as /devices/virtual/input/input5
Apr 30 01:59:53 Sisif kernel: [   23.382735] ACPI: Power Button (CM) [PBTN]
Apr 30 01:59:53 Sisif kernel: [   23.382801] input: Sleep Button (CM) as /devices/virtual/input/input6
Apr 30 01:59:53 Sisif kernel: [   23.414836] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 30 01:59:53 Sisif kernel: [   23.430709] ACPI: Sleep Button (CM) [SBTN]
Apr 30 01:59:53 Sisif kernel: [   23.430848] ACPI: WMI-Acer: Mapper loaded
Apr 30 01:59:53 Sisif kernel: [   23.534718] sdhci: Secure Digital Host Controller Interface driver
Apr 30 01:59:53 Sisif kernel: [   23.534722] sdhci: Copyright(c) Pierre Ossman
Apr 30 01:59:53 Sisif kernel: [   23.534773] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
Apr 30 01:59:53 Sisif kernel: [   23.534799] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
Apr 30 01:59:53 Sisif kernel: [   23.534870] mmc0: SDHCI at 0xef9fd500 irq 23 DMA
Apr 30 01:59:53 Sisif kernel: [   23.623147] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input7
Apr 30 01:59:53 Sisif kernel: [   23.675069] intel_rng: FWH not detected
Apr 30 01:59:53 Sisif kernel: [   23.678581] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr 30 01:59:53 Sisif kernel: [   23.686719] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input8
Apr 30 01:59:53 Sisif kernel: [   23.742565] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Apr 30 01:59:53 Sisif kernel: [   23.742727] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input9
Apr 30 01:59:53 Sisif kernel: [   23.806538] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Apr 30 01:59:53 Sisif kernel: [   24.478208] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
Apr 30 01:59:53 Sisif kernel: [   24.478238] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 30 01:59:53 Sisif kernel: [   24.502334] b43-phy0: Broadcom 4311 WLAN found
Apr 30 01:59:53 Sisif kernel: [   26.586896] phy0: Selected rate control algorithm 'simple'
Apr 30 01:59:53 Sisif kernel: [   27.279185] udev: renamed network interface wlan0 to eth1
Apr 30 01:59:53 Sisif kernel: [   25.369908] input: b43-phy0 as /devices/virtual/input/input10
Apr 30 01:59:53 Sisif kernel: [   25.421468] lp: driver loaded but no devices found
Apr 30 01:59:53 Sisif kernel: [   25.595345] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 01:59:53 Sisif kernel: [   28.896226] Registered led device: b43-phy0:tx
Apr 30 01:59:53 Sisif kernel: [   28.896254] Registered led device: b43-phy0:rx
Apr 30 01:59:53 Sisif kernel: [   28.896280] Registered led device: b43-phy0:radio
Apr 30 01:59:53 Sisif kernel: [   26.991603] NET: Registered protocol family 17
Apr 30 01:59:53 Sisif kernel: [   27.020143] usbcore: registered new interface driver ndiswrapper
Apr 30 01:59:53 Sisif kernel: [   29.096803] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
Apr 30 01:59:53 Sisif kernel: [   29.721085] EXT3 FS on sda1, internal journal
Apr 30 01:59:53 Sisif kernel: [   30.360194] kjournald starting.  Commit interval 5 seconds
Apr 30 01:59:53 Sisif kernel: [   28.345708] EXT3 FS on sda3, internal journal
Apr 30 01:59:53 Sisif kernel: [   28.345713] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 01:59:53 Sisif kernel: [   28.890944] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 01:59:53 Sisif kernel: [   30.223348] RPC: Registered udp transport module.
Apr 30 01:59:53 Sisif kernel: [   30.223352] RPC: Registered tcp transport module.
Apr 30 01:59:53 Sisif kernel: [   31.046692] No dock devices found.
Apr 30 01:59:54 Sisif avahi-daemon[5445]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Apr 30 01:59:55 Sisif avahi-daemon[5445]: Successfully dropped root privileges.
Apr 30 01:59:55 Sisif avahi-daemon[5445]: avahi-daemon 0.6.22 starting up.
Apr 30 01:59:55 Sisif avahi-daemon[5445]: Successfully called chroot().
Apr 30 01:59:55 Sisif avahi-daemon[5445]: Successfully dropped remaining capabilities.
Apr 30 01:59:55 Sisif avahi-daemon[5445]: No service file found in /etc/avahi/services.
Apr 30 01:59:55 Sisif avahi-daemon[5445]: Network interface enumeration completed.
Apr 30 01:59:55 Sisif avahi-daemon[5445]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 30 01:59:55 Sisif avahi-daemon[5445]: Server startup complete. Host name is Sisif.local. Local service cookie is 614262898.
Apr 30 01:59:55 Sisif dhclient: DHCPREQUEST of 192.168.0.118 on eth0 to 255.255.255.255 port 67
Apr 30 01:59:55 Sisif kernel: [   35.451160] ppdev: user-space parallel port driver
Apr 30 01:59:55 Sisif kernel: [   33.615790] audit(1209509995.311:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5479 profile="/usr/sbin/cupsd" namespace="default"
Apr 30 01:59:55 Sisif kernel: [   33.664219] apm: BIOS not found.
Apr 30 01:59:56 Sisif kernel: [   35.193156] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Apr 30 01:59:56 Sisif exportfs[5652]: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.10.2:/home/itch/Blonda".   Assuming default behaviour ('no_subtree_check').   NOTE: this default has changed since nfs-utils version 1.0.x 
Apr 30 01:59:57 Sisif kernel: [   35.451012] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Apr 30 01:59:57 Sisif kernel: [   35.466827] NFSD: starting 90-second grace period
Apr 30 01:59:58 Sisif nmbd[5722]: [2008/04/30 01:59:58, 0] nmbd/nmbd_subnetdb.c:create_subnets(190) 
Apr 30 01:59:58 Sisif nmbd[5722]:   create_subnets: No local interfaces ! 
Apr 30 01:59:58 Sisif nmbd[5722]: [2008/04/30 01:59:58, 0] nmbd/nmbd_subnetdb.c:create_subnets(191) 
Apr 30 01:59:58 Sisif nmbd[5722]:   create_subnets: Waiting for an interface to appear ... 
Apr 30 01:59:59 Sisif dhcdbd: Started up.
Apr 30 01:59:59 Sisif hcid[5799]: Bluetooth HCI daemon
Apr 30 01:59:59 Sisif kernel: [   38.256177] Bluetooth: Core ver 2.11
Apr 30 01:59:59 Sisif kernel: [   38.257039] NET: Registered protocol family 31
Apr 30 01:59:59 Sisif kernel: [   38.257046] Bluetooth: HCI device and connection manager initialized
Apr 30 01:59:59 Sisif kernel: [   38.257054] Bluetooth: HCI socket layer initialized
Apr 30 01:59:59 Sisif hcid[5799]: Starting SDP server
Apr 30 02:00:00 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr 30 02:00:00 Sisif hcid[5799]: Created local server at unix:abstract=/var/run/dbus-tCrPxaiDLM,guid=32ee0d26267f54b6033243e84817a870
Apr 30 02:00:00 Sisif kernel: [   38.365351] Bluetooth: L2CAP ver 2.9
Apr 30 02:00:00 Sisif kernel: [   38.365360] Bluetooth: L2CAP socket layer initialized
Apr 30 02:00:00 Sisif audio[5818]: Bluetooth Audio daemon
Apr 30 02:00:00 Sisif input[5822]: Bluetooth Input daemon
Apr 30 02:00:00 Sisif input[5822]: Registered input manager path:/org/bluez/input
Apr 30 02:00:00 Sisif audio[5818]: Unix socket created: 5
Apr 30 02:00:00 Sisif audio[5818]: audio.conf: Key file does not have key 'Enable'
Apr 30 02:00:00 Sisif audio[5818]: audio.conf: Key file does not have key 'Disable'
Apr 30 02:00:00 Sisif kernel: [   38.534384] Bluetooth: RFCOMM socket layer initialized
Apr 30 02:00:00 Sisif audio[5818]: add_service_record: got record id 0x10000
Apr 30 02:00:00 Sisif audio[5818]: audio.conf: Key file does not have key 'Disable'
Apr 30 02:00:00 Sisif audio[5818]: audio.conf: Key file does not have group 'A2DP'
Apr 30 02:00:00 Sisif last message repeated 3 times
Apr 30 02:00:00 Sisif audio[5818]: SEP 0x806d578 registered: type:0 codec:0 seid:1
Apr 30 02:00:00 Sisif audio[5818]: add_service_record: got record id 0x10001
Apr 30 02:00:00 Sisif kernel: [   38.534405] Bluetooth: RFCOMM TTY layer initialized
Apr 30 02:00:00 Sisif kernel: [   38.534409] Bluetooth: RFCOMM ver 1.8
Apr 30 02:00:00 Sisif audio[5818]: add_service_record: got record id 0x10002
Apr 30 02:00:00 Sisif audio[5818]: add_service_record: got record id 0x10003
Apr 30 02:00:00 Sisif audio[5818]: Registered manager path:/org/bluez/audio
Apr 30 02:00:01 Sisif ntpd[5875]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 02:00:01 Sisif ntpd[5878]: precision = 1.000 usec
Apr 30 02:00:01 Sisif kernel: [   39.867325] NET: Registered protocol family 10
Apr 30 02:00:01 Sisif kernel: [   39.867896] lo: Disabled Privacy Extensions
Apr 30 02:00:01 Sisif kernel: [   39.871054] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 30 02:00:01 Sisif kernel: [   39.873110] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 02:00:01 Sisif ntpd[5878]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 02:00:01 Sisif ntpd[5878]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 02:00:01 Sisif ntpd[5878]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 02:00:01 Sisif ntpd[5878]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 02:00:01 Sisif ntpd[5878]: kernel time sync status 0040
Apr 30 02:00:01 Sisif ntpd[5878]: frequency initialized -55.757 PPM from /var/lib/ntp/ntp.drift
Apr 30 02:00:03 Sisif ntpd_initres[5899]: host name not found: ntp2a.mcc.ac.uk
Apr 30 02:00:03 Sisif ntpd_initres[5899]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 02:00:03 Sisif ntpd_initres[5899]: host name not found: ntp.landau.ac.ru
Apr 30 02:00:03 Sisif ntpd_initres[5899]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 02:00:04 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 30 02:00:04 Sisif kernel: [   42.345634] [drm] Initialized drm 1.1.0 20060810
Apr 30 02:00:04 Sisif kernel: [   42.433842] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 02:00:04 Sisif kernel: [   42.433859] PCI: Setting latency timer of device 0000:00:02.0 to 64
Apr 30 02:00:04 Sisif kernel: [   44.450345] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr 30 02:00:04 Sisif anacron[5947]: Anacron 2.3 started on 2008-04-30
Apr 30 02:00:04 Sisif anacron[5947]: Normal exit (0 jobs run)
Apr 30 02:00:04 Sisif /usr/sbin/cron[5978]: (CRON) INFO (pidfile fd = 3)
Apr 30 02:00:04 Sisif /usr/sbin/cron[5981]: (CRON) STARTUP (fork ok)
Apr 30 02:00:04 Sisif /usr/sbin/cron[5981]: (CRON) INFO (Running @reboot jobs)
Apr 30 02:00:06 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 02:00:06 Sisif kernel: [   44.659682] input: b43-phy0 as /devices/virtual/input/input11
Apr 30 02:00:07 Sisif kernel: [   46.064630] Registered led device: b43-phy0:tx
Apr 30 02:00:07 Sisif kernel: [   46.065082] Registered led device: b43-phy0:rx
Apr 30 02:00:07 Sisif kernel: [   46.065468] Registered led device: b43-phy0:radio
Apr 30 02:00:07 Sisif kernel: [   48.125428] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 02:00:08 Sisif kernel: [   48.471855] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 02:00:08 Sisif kernel: [   46.475151] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 02:00:08 Sisif kernel: [   46.485029] usbcore: deregistering interface driver ndiswrapper
Apr 30 02:00:08 Sisif kernel: [   48.575752] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 02:00:08 Sisif kernel: [   46.787884] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 02:00:08 Sisif kernel: [   48.802887] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 02:00:08 Sisif kernel: [   48.802952] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 02:00:08 Sisif kernel: [   48.807918] ndiswrapper: using IRQ 16
Apr 30 02:00:08 Sisif kernel: [   49.164087] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 02:00:08 Sisif kernel: [   49.164182] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 02:00:08 Sisif kernel: [   47.153448] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 02:00:08 Sisif kernel: [   47.153535] udev: renamed network interface wlan0 to eth1
Apr 30 02:00:08 Sisif kernel: [   47.162805] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 02:00:08 Sisif kernel: [   49.192282] usbcore: registered new interface driver ndiswrapper
Apr 30 02:00:08 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 02:00:08 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 02:00:08 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 02:00:08 Sisif dhclient: All rights reserved.
Apr 30 02:00:08 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 02:00:08 Sisif dhclient: 
Apr 30 02:00:08 Sisif kernel: [   47.243526] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 02:00:08 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 02:00:08 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 02:00:08 Sisif dhclient: All rights reserved.
Apr 30 02:00:08 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 02:00:08 Sisif dhclient: 
Apr 30 02:00:09 Sisif kernel: [   49.344430] ndiswrapper: device eth1 removed
Apr 30 02:00:09 Sisif kernel: [   49.344461] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 02:00:09 Sisif kernel: [   49.344571] usbcore: deregistering interface driver ndiswrapper
Apr 30 02:00:09 Sisif kernel: [   49.375056] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 02:00:09 Sisif kernel: [   49.399719] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 02:00:09 Sisif kernel: [   47.385357] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 02:00:09 Sisif kernel: [   47.385428] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 02:00:09 Sisif kernel: [   47.390755] ndiswrapper: using IRQ 16
Apr 30 02:00:09 Sisif kernel: [   49.764557] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 02:00:09 Sisif kernel: [   49.765831] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 02:00:09 Sisif kernel: [   49.775894] usbcore: registered new interface driver ndiswrapper
Apr 30 02:00:09 Sisif kernel: [   49.797422] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 02:00:09 Sisif kernel: [   49.797504] udev: renamed network interface wlan0 to eth1
Apr 30 02:00:10 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 02:00:10 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 02:00:10 Sisif dhclient: Sending on   Socket/fallback
Apr 30 02:00:10 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 02:00:10 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 02:00:10 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 02:00:10 Sisif dhclient: Sending on   Socket/fallback
Apr 30 02:00:10 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 02:00:11 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr 30 02:00:11 Sisif dhclient: send_packet: Network is down
Apr 30 02:00:13 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 02:00:13 Sisif dhclient: send_packet: Network is down
Apr 30 02:00:15 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr 30 02:00:15 Sisif dhclient: send_packet: Network is down
Apr 30 02:00:18 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr 30 02:00:18 Sisif dhclient: send_packet: Network is down
Apr 30 02:00:20 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 02:00:20 Sisif dhclient: send_packet: Network is down
Apr 30 02:00:26 Sisif hcid[5799]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Apr 30 02:00:26 Sisif hcid[5799]: Default authorization agent (:1.18, /org/bluez/auth) registered
Apr 30 02:00:26 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr 30 02:00:26 Sisif dhclient: send_packet: Network is down
Apr 30 02:00:39 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 30 02:00:39 Sisif dhclient: send_packet: Network is down
Apr 30 02:00:39 Sisif kernel: [   78.155674] CPU0 attaching NULL sched-domain.
Apr 30 02:00:39 Sisif kernel: [   78.155685] CPU1 attaching NULL sched-domain.
Apr 30 02:00:39 Sisif kernel: [   78.178543] CPU0 attaching sched-domain:
Apr 30 02:00:39 Sisif kernel: [   78.178552]  domain 0: span 03
Apr 30 02:00:39 Sisif kernel: [   78.178554]   groups: 01 02
Apr 30 02:00:39 Sisif kernel: [   78.178560] CPU1 attaching sched-domain:
Apr 30 02:00:39 Sisif kernel: [   78.178562]  domain 0: span 03
Apr 30 02:00:39 Sisif kernel: [   78.178563]   groups: 02 01
Apr 30 02:00:42 Sisif dhclient: No DHCPOFFERS received.
Apr 30 02:00:42 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 02:00:42 Sisif kernel: [   82.321556] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 02:00:42 Sisif avahi-autoipd(eth1)[6892]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 30 02:00:42 Sisif avahi-autoipd(eth1)[6892]: Successfully called chroot().
Apr 30 02:00:42 Sisif avahi-autoipd(eth1)[6892]: Successfully dropped root privileges.
Apr 30 02:00:42 Sisif avahi-autoipd(eth1)[6892]: Starting with address 169.254.4.188
Apr 30 02:00:46 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Apr 30 02:00:46 Sisif avahi-autoipd(eth1)[6892]: Callout BIND, address 169.254.4.188 on interface eth1
Apr 30 02:00:46 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 02:00:46 Sisif avahi-daemon[5445]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 02:00:46 Sisif avahi-daemon[5445]: Registering new address record for 169.254.4.188 on eth1.IPv4.
Apr 30 02:00:50 Sisif avahi-autoipd(eth1)[6892]: Successfully claimed IP address 169.254.4.188
Apr 30 02:00:50 Sisif ntpd[5878]: ntpd exiting on signal 15
Apr 30 02:01:02 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr 30 02:01:10 Sisif dhclient: No DHCPOFFERS received.
Apr 30 02:01:10 Sisif dhclient: Trying recorded lease 192.168.1.102
Apr 30 02:01:10 Sisif avahi-autoipd(eth1)[6892]: A routable address has been configured.
Apr 30 02:01:10 Sisif avahi-autoipd(eth1)[6892]: Callout UNBIND, address 169.254.4.188 on interface eth1
Apr 30 02:01:10 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 02:01:10 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 02:01:10 Sisif avahi-daemon[5445]: Registering new address record for 192.168.1.102 on eth1.IPv4.
Apr 30 02:01:10 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.4.188 on eth1.
Apr 30 02:01:10 Sisif ntpdate[7159]: can't find host ntp2a.mcc.ac.uk 
Apr 30 02:01:13 Sisif avahi-autoipd(eth1)[6892]: No longer a routable address configured, restarting probe process.
Apr 30 02:01:13 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.1.102 on eth1.
Apr 30 02:01:13 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 02:01:13 Sisif avahi-daemon[5445]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 02:01:13 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 02:01:15 Sisif ntpdate[7159]: can't find host ntp.landau.ac.ru 
Apr 30 02:01:15 Sisif ntpdate[7159]: no servers can be used, exiting
Apr 30 02:01:15 Sisif ntpd[7903]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 02:01:15 Sisif ntpd[7904]: precision = 1.000 usec
Apr 30 02:01:15 Sisif ntpd[7904]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 02:01:15 Sisif ntpd[7904]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 02:01:15 Sisif ntpd[7904]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 02:01:15 Sisif ntpd[7904]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 02:01:15 Sisif ntpd[7904]: kernel time sync status 0040
Apr 30 02:01:15 Sisif ntpd[7904]: frequency initialized -55.757 PPM from /var/lib/ntp/ntp.drift
Apr 30 02:01:17 Sisif ntpd_initres[7905]: host name not found: ntp2a.mcc.ac.uk
Apr 30 02:01:17 Sisif ntpd_initres[7905]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 02:01:17 Sisif ntpd_initres[7905]: host name not found: ntp.landau.ac.ru
Apr 30 02:01:17 Sisif ntpd_initres[7905]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 02:01:17 Sisif avahi-autoipd(eth1)[6892]: Callout BIND, address 169.254.4.188 on interface eth1
Apr 30 02:01:17 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 02:01:17 Sisif avahi-daemon[5445]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 02:01:17 Sisif avahi-daemon[5445]: Registering new address record for 169.254.4.188 on eth1.IPv4.
Apr 30 02:01:19 Sisif avahi-daemon[5445]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 02:01:19 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 02:01:19 Sisif avahi-autoipd(eth1)[6892]: SIOCSIFFLAGS failed: Permission denied
Apr 30 02:01:19 Sisif avahi-autoipd(eth1)[6892]: Callout STOP, address 169.254.4.188 on interface eth1
Apr 30 02:01:19 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 02:01:19 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 02:01:19 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.4.188 on eth1.
Apr 30 02:01:19 Sisif avahi-autoipd(eth1)[6893]: client: RTNETLINK answers: No such process
Apr 30 02:01:19 Sisif kernel: [  119.997437] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 02:01:19 Sisif kernel: [  120.198968] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 02:01:20 Sisif dhclient: There is already a pid file /var/run/dhclient.pid with pid 7786
Apr 30 02:01:20 Sisif dhclient: removed stale PID file
Apr 30 02:01:20 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 02:01:20 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 02:01:20 Sisif dhclient: All rights reserved.
Apr 30 02:01:20 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 02:01:20 Sisif dhclient: 
Apr 30 02:01:21 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 02:01:21 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 02:01:21 Sisif dhclient: Sending on   Socket/fallback
Apr 30 02:01:22 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 02:01:23 Sisif kernel: [  123.884147] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 30 02:01:24 Sisif avahi-daemon[5445]: Registering new address record for fe80::219:7eff:fea0:3d2a on eth1.*.
Apr 30 02:01:27 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 02:01:33 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 02:01:33 Sisif kernel: [  133.955445] eth1: no IPv6 routers present
Apr 30 02:01:46 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 30 02:01:47 Sisif dhclient: DHCPOFFER of 192.168.1.102 from 192.168.1.1
Apr 30 02:01:47 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 02:01:47 Sisif dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
Apr 30 02:01:47 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 02:01:47 Sisif avahi-daemon[5445]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 02:01:47 Sisif avahi-daemon[5445]: Registering new address record for 192.168.1.102 on eth1.IPv4.
Apr 30 02:01:47 Sisif dhclient: bound to 192.168.1.102 -- renewal in 42819 seconds.
Apr 30 02:02:02 Sisif nmbd[5722]: [2008/04/30 02:02:02, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 02:02:02 Sisif nmbd[5722]:   Packet send failed to 169.254.255.255(138) ERRNO=Invalid argument 
Apr 30 02:06:16 Sisif ntpd[7904]: Listening on interface #4 eth1, fe80::219:7eff:fea0:3d2a#123 Enabled
Apr 30 02:06:16 Sisif ntpd[7904]: Listening on interface #5 eth1, 192.168.1.102#123 Enabled
Apr 30 02:06:37 Sisif nmbd[5722]: [2008/04/30 02:06:37, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Apr 30 02:06:37 Sisif nmbd[5722]:   ***** 
Apr 30 02:06:37 Sisif nmbd[5722]:    
Apr 30 02:06:37 Sisif nmbd[5722]:   Samba name server SISIF is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.102 
Apr 30 02:06:37 Sisif nmbd[5722]:    
Apr 30 02:06:37 Sisif nmbd[5722]:   ***** 
Apr 30 02:17:02 Sisif /USR/SBIN/CRON[26494]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 02:23:16 Sisif kernel: [ 1433.990440] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 02:23:16 Sisif kernel: [ 1434.048521] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 02:23:16 Sisif kernel: [ 1434.048555] b44.c:v2.0
Apr 30 02:23:16 Sisif kernel: [ 1434.073137] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 02:23:16 Sisif kernel: [ 1434.141220] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 30 02:23:16 Sisif dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Apr 30 02:23:16 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 02:23:16 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 02:23:16 Sisif dhclient: All rights reserved.
Apr 30 02:23:16 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 02:23:16 Sisif dhclient: 
Apr 30 02:23:17 Sisif dhclient: Listening on LPF/eth0/00:19:b9:85:80:f6
Apr 30 02:23:17 Sisif dhclient: Sending on   LPF/eth0/00:19:b9:85:80:f6
Apr 30 02:23:17 Sisif dhclient: Sending on   Socket/fallback
Apr 30 02:23:21 Sisif dhclient: DHCPREQUEST of 192.168.0.118 on eth0 to 255.255.255.255 port 67
Apr 30 02:23:30 Sisif last message repeated 2 times
Apr 30 02:23:45 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 30 02:23:53 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 30 02:24:02 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 30 02:24:11 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 30 02:24:16 Sisif dhclient: No DHCPOFFERS received.
Apr 30 02:24:16 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 02:24:16 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:24:16 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 02:24:16 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 02:24:19 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 02:24:19 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:24:19 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 02:24:19 Sisif avahi-autoipd(eth0)[1868]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 30 02:24:19 Sisif avahi-autoipd(eth0)[1868]: Successfully called chroot().
Apr 30 02:24:19 Sisif avahi-autoipd(eth0)[1868]: Successfully dropped root privileges.
Apr 30 02:24:19 Sisif avahi-autoipd(eth0)[1868]: Starting with address 169.254.9.233
Apr 30 02:24:25 Sisif avahi-autoipd(eth0)[1868]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 02:24:25 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:24:25 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 02:24:25 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 02:24:29 Sisif avahi-autoipd(eth0)[1868]: Successfully claimed IP address 169.254.9.233
Apr 30 02:24:29 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 02:24:29 Sisif ntpd[7904]: ntpd exiting on signal 15
Apr 30 02:24:29 Sisif ntpdate[2070]: can't find host ntp.landau.ac.ru 
Apr 30 02:24:29 Sisif ntpdate[2070]: adjust time server 130.88.202.49 offset 0.457347 sec
Apr 30 02:24:29 Sisif ntpd[2107]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 02:24:29 Sisif ntpd[2108]: precision = 1.000 usec
Apr 30 02:24:29 Sisif ntpd[2108]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 02:24:29 Sisif ntpd[2108]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 02:24:29 Sisif ntpd[2108]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 02:24:29 Sisif ntpd[2108]: Listening on interface #3 eth1, fe80::219:7eff:fea0:3d2a#123 Enabled
Apr 30 02:24:29 Sisif ntpd[2108]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Apr 30 02:24:29 Sisif ntpd[2108]: Listening on interface #5 eth1, 192.168.1.102#123 Enabled
Apr 30 02:24:29 Sisif ntpd[2108]: Listening on interface #6 eth0:avahi, 169.254.9.233#123 Enabled
Apr 30 02:24:29 Sisif ntpd[2108]: kernel time sync status 0040
Apr 30 02:24:29 Sisif ntpd[2108]: frequency initialized -55.757 PPM from /var/lib/ntp/ntp.drift
Apr 30 02:24:31 Sisif ntpd_initres[2109]: host name not found: ntp.landau.ac.ru
Apr 30 02:24:31 Sisif ntpd_initres[2109]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 02:26:42 Sisif nmbd[5722]: [2008/04/30 02:26:42, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Apr 30 02:26:42 Sisif nmbd[5722]:   ***** 
Apr 30 02:26:42 Sisif nmbd[5722]:    
Apr 30 02:26:42 Sisif nmbd[5722]:   Samba name server SISIF is now a local master browser for workgroup WORKGROUP on subnet 169.254.9.233 
Apr 30 02:26:42 Sisif nmbd[5722]:    
Apr 30 02:26:42 Sisif nmbd[5722]:   ***** 
Apr 30 02:28:46 Sisif ntpd[2108]: synchronized to 130.88.202.49, stratum 2
Apr 30 02:28:46 Sisif ntpd[2108]: time reset +0.329420 s
Apr 30 02:28:46 Sisif ntpd[2108]: kernel time sync status change 0001
Apr 30 02:30:02 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 30 02:30:07 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 30 02:30:18 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr 30 02:30:33 Sisif dhclient: No DHCPOFFERS received.
Apr 30 02:30:33 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 02:30:33 Sisif avahi-autoipd(eth0)[1868]: A routable address has been configured.
Apr 30 02:30:33 Sisif avahi-autoipd(eth0)[1868]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 02:30:33 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:30:33 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:30:33 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 02:30:33 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 02:30:36 Sisif avahi-autoipd(eth0)[1868]: No longer a routable address configured, restarting probe process.
Apr 30 02:30:36 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 02:30:36 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:30:36 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 02:30:36 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 02:30:41 Sisif avahi-autoipd(eth0)[1868]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 02:30:41 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:30:41 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 02:30:41 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 02:30:45 Sisif avahi-autoipd(eth0)[1868]: Successfully claimed IP address 169.254.9.233
Apr 30 02:33:17 Sisif ntpd[2108]: synchronized to 130.88.202.49, stratum 2
Apr 30 02:33:46 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 30 02:33:49 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 30 02:33:52 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 30 02:33:58 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 30 02:34:09 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 30 02:34:17 Sisif dhclient: No DHCPOFFERS received.
Apr 30 02:34:17 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 02:34:17 Sisif avahi-autoipd(eth0)[1868]: A routable address has been configured.
Apr 30 02:34:17 Sisif avahi-autoipd(eth0)[1868]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 02:34:17 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:34:17 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:34:17 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 02:34:17 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 02:34:20 Sisif avahi-autoipd(eth0)[1868]: No longer a routable address configured, restarting probe process.
Apr 30 02:34:20 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 02:34:20 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:34:20 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 02:34:20 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 02:34:24 Sisif avahi-autoipd(eth0)[1868]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 02:34:24 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:34:24 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 02:34:24 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 02:34:28 Sisif avahi-autoipd(eth0)[1868]: Successfully claimed IP address 169.254.9.233
Apr 30 02:39:41 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 30 02:39:46 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr 30 02:40:00 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr 30 02:40:12 Sisif dhclient: No DHCPOFFERS received.
Apr 30 02:40:12 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 02:40:12 Sisif avahi-autoipd(eth0)[1868]: A routable address has been configured.
Apr 30 02:40:12 Sisif avahi-autoipd(eth0)[1868]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 02:40:12 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:40:12 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:40:12 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 02:40:12 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 02:40:15 Sisif avahi-autoipd(eth0)[1868]: No longer a routable address configured, restarting probe process.
Apr 30 02:40:15 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 02:40:15 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:40:15 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 02:40:15 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 02:40:21 Sisif avahi-autoipd(eth0)[1868]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 02:40:21 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:40:21 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 02:40:21 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 02:40:25 Sisif avahi-autoipd(eth0)[1868]: Successfully claimed IP address 169.254.9.233
Apr 30 02:44:52 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 02:44:52 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:44:52 Sisif dhclient: receive_packet failed on eth0: Network is down
Apr 30 02:44:52 Sisif avahi-autoipd(eth0)[1868]: if_indextoname() failed: No such device or address
Apr 30 02:44:52 Sisif avahi-autoipd(eth0)[1868]: Callout STOP, address 169.254.9.233 on interface (null)
Apr 30 02:44:52 Sisif avahi-autoipd(eth0)[1869]: if_indextoname() failed: No such device or address
Apr 30 02:44:52 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 02:44:52 Sisif kernel: [ 2729.492676] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 02:44:53 Sisif nmbd[5722]: [2008/04/30 02:44:53, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 02:44:53 Sisif nmbd[5722]:   Packet send failed to 169.254.255.255(138) ERRNO=Invalid argument 
Apr 30 02:44:53 Sisif nmbd[5722]: [2008/04/30 02:44:53, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 02:44:53 Sisif nmbd[5722]:   Packet send failed to 169.254.255.255(138) ERRNO=Invalid argument 
Apr 30 02:45:12 Sisif kernel: [ 2749.425958] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 02:45:12 Sisif kernel: [ 2749.484199] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 02:45:12 Sisif kernel: [ 2749.484818] b44.c:v2.0
Apr 30 02:45:12 Sisif kernel: [ 2751.520446] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 02:45:19 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 30 02:45:19 Sisif dhclient: send_packet: Network is down
Apr 30 02:45:25 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr 30 02:45:25 Sisif dhclient: send_packet: Network is down
Apr 30 02:45:35 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr 30 02:45:35 Sisif dhclient: send_packet: Network is down
Apr 30 02:45:45 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 30 02:45:45 Sisif dhclient: send_packet: Network is down
Apr 30 02:45:50 Sisif dhclient: No DHCPOFFERS received.
Apr 30 02:45:50 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 02:45:50 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:45:50 Sisif kernel: [ 2786.697800] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 30 02:45:50 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 02:45:50 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 02:45:53 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 02:45:53 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:45:53 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 02:45:53 Sisif avahi-autoipd(eth0)[15878]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 30 02:45:53 Sisif avahi-autoipd(eth0)[15878]: Successfully called chroot().
Apr 30 02:45:53 Sisif avahi-autoipd(eth0)[15878]: Successfully dropped root privileges.
Apr 30 02:45:53 Sisif avahi-autoipd(eth0)[15878]: Starting with address 169.254.9.233
Apr 30 02:45:58 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 02:45:58 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:45:58 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 02:45:58 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 02:46:02 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 02:46:02 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 02:50:41 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 30 02:50:46 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr 30 02:50:58 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr 30 02:51:12 Sisif dhclient: No DHCPOFFERS received.
Apr 30 02:51:12 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 02:51:12 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 02:51:12 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:51:12 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 02:51:12 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:51:12 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 02:51:12 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 02:51:15 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 02:51:15 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 02:51:15 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:51:15 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 02:51:15 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 02:51:20 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 02:51:20 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:51:20 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 02:51:20 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 02:51:24 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 02:56:30 Sisif nmbd[5722]: [2008/04/30 02:56:30, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Apr 30 02:56:30 Sisif nmbd[5722]:   ***** 
Apr 30 02:56:30 Sisif nmbd[5722]:    
Apr 30 02:56:30 Sisif nmbd[5722]:   Samba name server SISIF is now a local master browser for workgroup WORKGROUP on subnet 169.254.9.233 
Apr 30 02:56:30 Sisif nmbd[5722]:    
Apr 30 02:56:30 Sisif nmbd[5722]:   ***** 
Apr 30 02:58:13 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 30 02:58:19 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr 30 02:58:29 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr 30 02:58:44 Sisif dhclient: No DHCPOFFERS received.
Apr 30 02:58:44 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 02:58:44 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 02:58:44 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 02:58:44 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:58:44 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:58:44 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 02:58:44 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 02:58:47 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 02:58:47 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 02:58:47 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 02:58:47 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 02:58:47 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 02:58:53 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 02:58:53 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 02:58:53 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 02:58:53 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 02:58:57 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 03:01:44 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 30 03:01:49 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 30 03:02:02 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 30 03:02:15 Sisif dhclient: No DHCPOFFERS received.
Apr 30 03:02:15 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 03:02:15 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 03:02:15 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 03:02:15 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:02:15 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:02:15 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 03:02:15 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 03:02:18 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 03:02:18 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 03:02:18 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:02:18 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 03:02:18 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 03:02:23 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 03:02:23 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:02:23 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 03:02:23 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 03:02:27 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 03:06:31 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 30 03:06:38 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Apr 30 03:06:59 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 30 03:07:02 Sisif dhclient: No DHCPOFFERS received.
Apr 30 03:07:02 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 03:07:02 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 03:07:02 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 03:07:02 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:07:02 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:07:02 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 03:07:02 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 03:07:05 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 03:07:05 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 03:07:05 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:07:05 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 03:07:05 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 03:07:10 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 03:07:10 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:07:10 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 03:07:10 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 03:07:14 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 03:11:30 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 30 03:11:30 Sisif nmbd[5722]: [2008/04/30 03:11:30, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Apr 30 03:11:30 Sisif nmbd[5722]:   ***** 
Apr 30 03:11:30 Sisif nmbd[5722]:    
Apr 30 03:11:30 Sisif nmbd[5722]:   Samba name server SISIF is now a local master browser for workgroup WORKGROUP on subnet 169.254.9.233 
Apr 30 03:11:30 Sisif nmbd[5722]:    
Apr 30 03:11:30 Sisif nmbd[5722]:   ***** 
Apr 30 03:11:38 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 30 03:11:46 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 30 03:11:57 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 30 03:12:01 Sisif dhclient: No DHCPOFFERS received.
Apr 30 03:12:01 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 03:12:01 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 03:12:01 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 03:12:01 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:12:01 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:12:01 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 03:12:01 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 03:12:04 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 03:12:04 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 03:12:04 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:12:04 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 03:12:04 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 03:12:10 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 03:12:10 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:12:10 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 03:12:10 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 03:12:14 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 03:16:55 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 30 03:17:01 Sisif /USR/SBIN/CRON[31408]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 03:17:03 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr 30 03:17:14 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 30 03:17:26 Sisif dhclient: No DHCPOFFERS received.
Apr 30 03:17:26 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 03:17:26 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 03:17:26 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 03:17:26 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:17:26 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:17:26 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 03:17:26 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 03:17:29 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 03:17:29 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:17:29 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 03:17:29 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 03:17:29 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 03:17:34 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 03:17:34 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:17:34 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 03:17:34 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 03:17:38 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 03:22:54 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 30 03:22:58 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr 30 03:23:08 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr 30 03:23:22 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 30 03:23:25 Sisif dhclient: No DHCPOFFERS received.
Apr 30 03:23:25 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 03:23:25 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 03:23:25 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 03:23:25 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:23:25 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:23:25 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 03:23:25 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 03:23:28 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 03:23:28 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 03:23:28 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:23:28 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 03:23:28 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 03:23:31 Sisif nmbd[5722]: [2008/04/30 03:23:31, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 03:23:31 Sisif nmbd[5722]:   Packet send failed to 169.254.255.255(138) ERRNO=Invalid argument 
Apr 30 03:23:31 Sisif nmbd[5722]: [2008/04/30 03:23:31, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 03:23:31 Sisif nmbd[5722]:   Packet send failed to 169.254.255.255(138) ERRNO=Invalid argument 
Apr 30 03:23:33 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 03:23:33 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:23:33 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 03:23:33 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 03:23:37 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 03:30:13 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 30 03:30:18 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 30 03:30:27 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Apr 30 03:30:44 Sisif dhclient: No DHCPOFFERS received.
Apr 30 03:30:44 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 03:30:44 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 03:30:44 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 03:30:44 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:30:44 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:30:44 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 03:30:44 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 03:30:47 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 03:30:47 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 03:30:47 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:30:47 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 03:30:47 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 03:30:53 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 03:30:53 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:30:53 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 03:30:53 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 03:30:57 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 03:34:39 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 30 03:34:45 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 30 03:34:54 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Apr 30 03:35:10 Sisif dhclient: No DHCPOFFERS received.
Apr 30 03:35:10 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 03:35:10 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 03:35:10 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 03:35:10 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:35:10 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:35:10 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 03:35:10 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 03:35:13 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 03:35:13 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 03:35:13 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:35:13 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 03:35:13 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 03:35:17 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 03:35:17 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:35:17 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 03:35:17 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 03:35:21 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 03:38:05 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 30 03:38:13 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 30 03:38:22 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 30 03:38:33 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 30 03:38:36 Sisif dhclient: No DHCPOFFERS received.
Apr 30 03:38:36 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 03:38:36 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 03:38:36 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 03:38:36 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:38:36 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:38:36 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 03:38:36 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 03:38:39 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 03:38:39 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 03:38:39 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:38:39 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 03:38:39 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 03:38:44 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 03:38:44 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:38:44 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 03:38:44 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 03:38:48 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 03:42:11 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 30 03:42:18 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 30 03:42:25 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Apr 30 03:42:42 Sisif dhclient: No DHCPOFFERS received.
Apr 30 03:42:42 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 03:42:42 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 03:42:42 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 03:42:42 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:42:42 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:42:42 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 03:42:42 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 03:42:45 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 03:42:45 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 03:42:45 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:42:45 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 03:42:45 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 03:42:50 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 03:42:50 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:42:50 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 03:42:50 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 03:42:54 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 03:45:30 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 30 03:45:33 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 30 03:45:36 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 30 03:45:41 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 30 03:45:47 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 30 03:46:00 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Apr 30 03:46:01 Sisif dhclient: No DHCPOFFERS received.
Apr 30 03:46:01 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 03:46:01 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:46:01 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 03:46:01 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 03:46:01 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:46:01 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 03:46:01 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 03:46:04 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 03:46:04 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:46:04 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 03:46:04 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 03:46:04 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 03:46:09 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 03:46:09 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:46:09 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 03:46:09 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 03:46:13 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 03:51:19 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 30 03:51:25 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr 30 03:51:39 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 30 03:51:46 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 30 03:51:50 Sisif dhclient: No DHCPOFFERS received.
Apr 30 03:51:50 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 03:51:50 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 03:51:50 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 03:51:50 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:51:50 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:51:50 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 03:51:50 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 03:51:53 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 03:51:53 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 03:51:53 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:51:53 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 03:51:53 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 03:51:59 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 03:51:59 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:51:59 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 03:51:59 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 03:52:03 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 03:55:44 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 30 03:55:51 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 30 03:56:04 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 30 03:56:15 Sisif dhclient: No DHCPOFFERS received.
Apr 30 03:56:15 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 03:56:15 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 03:56:15 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 03:56:15 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:56:15 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:56:15 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 03:56:15 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 03:56:18 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 03:56:18 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 03:56:18 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 03:56:18 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 03:56:18 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 03:56:23 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 03:56:23 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 03:56:23 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 03:56:23 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 03:56:27 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 04:00:17 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 30 04:00:23 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 30 04:00:36 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr 30 04:00:48 Sisif dhclient: No DHCPOFFERS received.
Apr 30 04:00:48 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 04:00:48 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 04:00:48 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 04:00:48 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 04:00:48 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 04:00:48 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 04:00:48 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 04:00:51 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 04:00:51 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 04:00:51 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 04:00:51 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 04:00:51 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 04:00:55 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 04:00:55 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 04:00:55 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 04:00:55 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 04:00:59 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 04:05:56 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 30 04:06:04 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 30 04:06:13 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr 30 04:06:27 Sisif dhclient: No DHCPOFFERS received.
Apr 30 04:06:27 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 04:06:27 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 04:06:27 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 04:06:27 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 04:06:27 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 04:06:27 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 04:06:27 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 04:06:30 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 04:06:30 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 04:06:30 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 04:06:30 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 04:06:30 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 04:06:35 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 04:06:35 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 04:06:35 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 04:06:35 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 04:06:39 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 04:12:39 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 30 04:12:45 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr 30 04:13:00 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr 30 04:13:10 Sisif dhclient: No DHCPOFFERS received.
Apr 30 04:13:10 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 04:13:10 Sisif avahi-autoipd(eth0)[15878]: A routable address has been configured.
Apr 30 04:13:10 Sisif avahi-autoipd(eth0)[15878]: Callout UNBIND, address 169.254.9.233 on interface eth0
Apr 30 04:13:10 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 04:13:10 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 04:13:10 Sisif avahi-daemon[5445]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 04:13:10 Sisif avahi-daemon[5445]: Withdrawing address record for 169.254.9.233 on eth0.
Apr 30 04:13:20 Sisif avahi-autoipd(eth0)[15878]: No longer a routable address configured, restarting probe process.
Apr 30 04:13:20 Sisif avahi-daemon[5445]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 04:13:20 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 04:13:20 Sisif avahi-daemon[5445]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 04:13:20 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 04:13:26 Sisif avahi-autoipd(eth0)[15878]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 04:13:26 Sisif avahi-daemon[5445]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 04:13:26 Sisif avahi-daemon[5445]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 04:13:26 Sisif avahi-daemon[5445]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 04:13:30 Sisif avahi-autoipd(eth0)[15878]: Successfully claimed IP address 169.254.9.233
Apr 30 04:15:04 Sisif gnome-power-manager: (itch) GNOME interactive logout. Reason: The power button has been pressed.
Apr 30 04:15:09 Sisif init: tty4 main process (4840) killed by TERM signal
Apr 30 04:15:09 Sisif init: tty5 main process (4841) killed by TERM signal
Apr 30 04:15:09 Sisif init: tty2 main process (4846) killed by TERM signal
Apr 30 04:15:09 Sisif init: tty3 main process (4849) killed by TERM signal
Apr 30 04:15:09 Sisif init: tty6 main process (4850) killed by TERM signal
Apr 30 04:15:09 Sisif init: tty1 main process (6372) killed by TERM signal
Apr 30 04:15:09 Sisif kernel: [ 8146.131281] gdm[5850]: segfault at 7672657f eip b782b7e2 esp bfb8b520 error 6
Apr 30 04:15:10 Sisif avahi-daemon[5445]: Got SIGTERM, quitting.
Apr 30 04:15:10 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 04:15:10 Sisif avahi-daemon[5445]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 04:15:10 Sisif nmbd[5722]: [2008/04/30 04:15:10, 0] nmbd/nmbd.c:terminate(58) 
Apr 30 04:15:10 Sisif nmbd[5722]:   Got SIGTERM: going down... 
Apr 30 04:15:12 Sisif rpc.statd[4546]: Caught signal 15, un-registering and exiting.
Apr 30 04:15:13 Sisif kernel: [ 8148.147718] ip6_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 04:15:15 Sisif kernel: [ 8151.477914] nfsd: last server has exited
Apr 30 04:15:15 Sisif kernel: [ 8151.477920] nfsd: unexporting all filesystems
Apr 30 04:15:15 Sisif mountd[5677]: Caught signal 15, un-registering and exiting.
Apr 30 04:15:15 Sisif exiting on signal 15
Apr 30 14:44:34 Sisif syslogd 1.5.0#1ubuntu1: restart.
Apr 30 14:44:34 Sisif kernel: Inspecting /boot/System.map-2.6.24-16-generic
Apr 30 14:44:34 Sisif kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Apr 30 14:44:34 Sisif kernel: Symbols match kernel version 2.6.24.
Apr 30 14:44:34 Sisif kernel: Loaded 22549 symbols from 100 modules.
Apr 30 14:44:34 Sisif kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Apr 30 14:44:34 Sisif kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 30 14:44:34 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 30 14:44:34 Sisif kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 30 14:44:34 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d3400 (usable)
Apr 30 14:44:34 Sisif kernel: [    0.000000]  BIOS-e820: 000000007f6d3400 - 0000000080000000 (reserved)
Apr 30 14:44:34 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Apr 30 14:44:34 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Apr 30 14:44:34 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 30 14:44:34 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Apr 30 14:44:34 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Apr 30 14:44:34 Sisif kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr 30 14:44:34 Sisif kernel: [    0.000000] 1142MB HIGHMEM available.
Apr 30 14:44:34 Sisif kernel: [    0.000000] 896MB LOWMEM available.
Apr 30 14:44:34 Sisif kernel: [    0.000000] Entering add_active_range(0, 0, 521939) 0 entries of 256 used
Apr 30 14:44:34 Sisif kernel: [    0.000000] Zone PFN ranges:
Apr 30 14:44:34 Sisif kernel: [    0.000000]   DMA             0 ->     4096
Apr 30 14:44:34 Sisif kernel: [    0.000000]   Normal       4096 ->   229376
Apr 30 14:44:34 Sisif kernel: [    0.000000]   HighMem    229376 ->   521939
Apr 30 14:44:34 Sisif kernel: [    0.000000] Movable zone start PFN for each node
Apr 30 14:44:34 Sisif kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 30 14:44:34 Sisif kernel: [    0.000000]     0:        0 ->   521939
Apr 30 14:44:34 Sisif kernel: [    0.000000] On node 0 totalpages: 521939
Apr 30 14:44:34 Sisif kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 30 14:44:34 Sisif kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 30 14:44:34 Sisif kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 30 14:44:34 Sisif kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Apr 30 14:44:34 Sisif kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Apr 30 14:44:34 Sisif kernel: [    0.000000]   HighMem zone: 2285 pages used for memmap
Apr 30 14:44:34 Sisif kernel: [    0.000000]   HighMem zone: 290278 pages, LIFO batch:31
Apr 30 14:44:34 Sisif kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 30 14:44:34 Sisif kernel: [    0.000000] DMI 2.4 present.
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: RSDT 7F6D39CD, 0040 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: FACP 7F6D4800, 0074 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: DSDT 7F6D5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: FACS 7F6E3C00, 0040
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: HPET 7F6D4F00, 0038 (r1 DELL    M07            1 ASL        61)
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: APIC 7F6D5000, 0068 (r1 DELL    M07     27D7060D ASL        47)
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: MCFG 7F6D4FC0, 003E (r16 DELL    M07     27D7060D ASL        61)
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: SLIC 7F6D509C, 0024 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: BOOT 7F6D4BC0, 0028 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: SSDT 7F6D3A0D, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 30 14:44:34 Sisif kernel: [    0.000000] Processor #0 6:14 APIC version 20
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 30 14:44:34 Sisif kernel: [    0.000000] Processor #1 6:14 APIC version 20
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 30 14:44:34 Sisif kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 30 14:44:34 Sisif kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 30 14:44:34 Sisif kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 30 14:44:34 Sisif kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 30 14:44:34 Sisif kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
Apr 30 14:44:34 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 30 14:44:34 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Apr 30 14:44:34 Sisif kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517862
Apr 30 14:44:34 Sisif kernel: [    0.000000] Kernel command line: root=UUID=35a5e031-c7e9-4597-9992-99d1d88d0eac ro quiet splash
Apr 30 14:44:34 Sisif kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Apr 30 14:44:34 Sisif kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Apr 30 14:44:34 Sisif kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 30 14:44:34 Sisif kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 30 14:44:34 Sisif kernel: [    0.000000] Initializing CPU#0
Apr 30 14:44:34 Sisif kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 30 14:44:34 Sisif kernel: [    0.000000] Detected 1729.065 MHz processor.
Apr 30 14:44:34 Sisif kernel: [    6.564284] Console: colour VGA+ 80x25
Apr 30 14:44:34 Sisif kernel: [    6.564288] console [tty0] enabled
Apr 30 14:44:34 Sisif kernel: [    6.564589] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 30 14:44:34 Sisif kernel: [    6.564989] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 30 14:44:34 Sisif kernel: [    6.686992] Memory: 2057924k/2087756k available (2157k kernel code, 28552k reserved, 998k data, 364k init, 1170252k highmem)
Apr 30 14:44:34 Sisif kernel: [    6.687001] virtual kernel memory layout:
Apr 30 14:44:34 Sisif kernel: [    6.687003]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Apr 30 14:44:34 Sisif kernel: [    6.687004]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 30 14:44:34 Sisif kernel: [    6.687005]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Apr 30 14:44:34 Sisif kernel: [    6.687006]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 30 14:44:34 Sisif kernel: [    6.687008]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Apr 30 14:44:34 Sisif kernel: [    6.687009]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Apr 30 14:44:34 Sisif kernel: [    6.687010]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Apr 30 14:44:34 Sisif kernel: [    6.687014] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 30 14:44:34 Sisif kernel: [    6.687057] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 30 14:44:34 Sisif kernel: [    6.687206] hpet clockevent registered
Apr 30 14:44:34 Sisif kernel: [    6.767177] Calibrating delay using timer specific routine.. 3461.65 BogoMIPS (lpj=6923301)
Apr 30 14:44:34 Sisif kernel: [    6.767201] Security Framework initialized
Apr 30 14:44:34 Sisif kernel: [    6.767210] SELinux:  Disabled at boot.
Apr 30 14:44:34 Sisif kernel: [    6.767226] AppArmor: AppArmor initialized
Apr 30 14:44:34 Sisif kernel: [    6.767231] Failure registering capabilities with primary security module.
Apr 30 14:44:34 Sisif kernel: [    6.767240] Mount-cache hash table entries: 512
Apr 30 14:44:34 Sisif kernel: [    6.767378] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 14:44:34 Sisif kernel: [    6.767388] monitor/mwait feature present.
Apr 30 14:44:34 Sisif kernel: [    6.767389] using mwait in idle threads.
Apr 30 14:44:34 Sisif kernel: [    6.767394] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 14:44:34 Sisif kernel: [    6.767396] CPU: L2 cache: 1024K
Apr 30 14:44:34 Sisif kernel: [    6.767399] CPU: Physical Processor ID: 0
Apr 30 14:44:34 Sisif kernel: [    6.767401] CPU: Processor Core ID: 0
Apr 30 14:44:34 Sisif kernel: [    6.767403] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 14:44:34 Sisif kernel: [    6.767412] Compat vDSO mapped to ffffe000.
Apr 30 14:44:34 Sisif kernel: [    6.767425] Checking 'hlt' instruction... OK.
Apr 30 14:44:34 Sisif kernel: [    6.783578] SMP alternatives: switching to UP code
Apr 30 14:44:34 Sisif kernel: [    6.785416] Early unpacking initramfs... done
Apr 30 14:44:34 Sisif kernel: [    7.135540] ACPI: Core revision 20070126
Apr 30 14:44:34 Sisif kernel: [    7.135600] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 30 14:44:34 Sisif kernel: [    7.138332] CPU0: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 14:44:34 Sisif kernel: [    7.138350] SMP alternatives: switching to SMP code
Apr 30 14:44:34 Sisif kernel: [    7.139078] Booting processor 1/1 eip 3000
Apr 30 14:44:34 Sisif kernel: [    9.226317] Initializing CPU#1
Apr 30 14:44:34 Sisif kernel: [    9.306363] Calibrating delay using timer specific routine.. 3458.04 BogoMIPS (lpj=6916090)
Apr 30 14:44:34 Sisif kernel: [    9.306370] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 14:44:34 Sisif kernel: [    9.306376] monitor/mwait feature present.
Apr 30 14:44:34 Sisif kernel: [    9.306379] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 14:44:34 Sisif kernel: [    9.306381] CPU: L2 cache: 1024K
Apr 30 14:44:34 Sisif kernel: [    9.306384] CPU: Physical Processor ID: 0
Apr 30 14:44:34 Sisif kernel: [    9.306385] CPU: Processor Core ID: 1
Apr 30 14:44:34 Sisif kernel: [    9.306387] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 14:44:34 Sisif kernel: [    7.231441] CPU1: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 14:44:34 Sisif kernel: [    7.231465] Total of 2 processors activated (6919.69 BogoMIPS).
Apr 30 14:44:34 Sisif kernel: [    7.231666] ENABLING IO-APIC IRQs
Apr 30 14:44:34 Sisif kernel: [    7.231862] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 30 14:44:34 Sisif kernel: [    7.379033] checking TSC synchronization [CPU#0 -> CPU#1]:
Apr 30 14:44:34 Sisif kernel: [    7.399034] Measured 3589861496 cycles TSC warp between CPUs, turning off TSC clock.
Apr 30 14:44:34 Sisif kernel: [    7.399037] Marking TSC unstable due to: check_tsc_sync_source failed.
Apr 30 14:44:34 Sisif kernel: [    7.399053] Brought up 2 CPUs
Apr 30 14:44:34 Sisif kernel: [    7.399080] CPU0 attaching sched-domain:
Apr 30 14:44:34 Sisif kernel: [    7.399082]  domain 0: span 03
Apr 30 14:44:34 Sisif kernel: [    7.399084]   groups: 01 02
Apr 30 14:44:34 Sisif kernel: [    7.399087] CPU1 attaching sched-domain:
Apr 30 14:44:34 Sisif kernel: [    7.399089]  domain 0: span 03
Apr 30 14:44:34 Sisif kernel: [    7.399091]   groups: 02 01
Apr 30 14:44:34 Sisif kernel: [    9.474742] net_namespace: 64 bytes
Apr 30 14:44:34 Sisif kernel: [    9.474753] Booting paravirtualized kernel on bare hardware
Apr 30 14:44:34 Sisif kernel: [    9.475249] Time: 11:44:12  Date: 04/30/08
Apr 30 14:44:34 Sisif kernel: [    9.475280] NET: Registered protocol family 16
Apr 30 14:44:34 Sisif kernel: [    9.475496] EISA bus registered
Apr 30 14:44:34 Sisif kernel: [    9.475501] ACPI: bus type pci registered
Apr 30 14:44:34 Sisif kernel: [    9.504238] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=13
Apr 30 14:44:34 Sisif kernel: [    9.504240] PCI: Using configuration type 1
Apr 30 14:44:34 Sisif kernel: [    9.504242] Setting up standard PCI resources
Apr 30 14:44:34 Sisif kernel: [    7.434604] ACPI: EC: Look up EC in DSDT
Apr 30 14:44:34 Sisif kernel: [    7.439469] ACPI: Interpreter enabled
Apr 30 14:44:34 Sisif kernel: [    7.439473] ACPI: (supports S0 S3 S4 S5)
Apr 30 14:44:34 Sisif kernel: [    7.439486] ACPI: Using IOAPIC for interrupt routing
Apr 30 14:44:34 Sisif kernel: [    7.453533] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 30 14:44:34 Sisif kernel: [    7.454337] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 30 14:44:34 Sisif kernel: [    7.454342] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Apr 30 14:44:34 Sisif kernel: [    7.455593] PCI: Transparent bridge - 0000:00:1e.0
Apr 30 14:44:34 Sisif kernel: [    7.455634] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 30 14:44:34 Sisif kernel: [    7.456097] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr 30 14:44:34 Sisif kernel: [    7.456230] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 30 14:44:34 Sisif kernel: [    7.456351] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr 30 14:44:34 Sisif kernel: [    7.464779] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr 30 14:44:34 Sisif kernel: [    7.464890] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
Apr 30 14:44:34 Sisif kernel: [    7.464998] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr 30 14:44:34 Sisif kernel: [    7.465106] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Apr 30 14:44:34 Sisif kernel: [    7.465215] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 30 14:44:34 Sisif kernel: [    7.465326] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 30 14:44:34 Sisif kernel: [    7.465436] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Apr 30 14:44:34 Sisif kernel: [    7.465547] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Apr 30 14:44:34 Sisif kernel: [    7.465704] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 30 14:44:34 Sisif kernel: [    7.465739] pnp: PnP ACPI init
Apr 30 14:44:34 Sisif kernel: [    7.465747] ACPI: bus type pnp registered
Apr 30 14:44:34 Sisif kernel: [    7.482014] pnpacpi: exceeded the max number of mem resources: 12
Apr 30 14:44:34 Sisif kernel: [    7.494863] pnp: PnP ACPI: found 12 devices
Apr 30 14:44:34 Sisif kernel: [    7.494870] ACPI: ACPI bus type pnp unregistered
Apr 30 14:44:34 Sisif kernel: [    7.494873] PnPBIOS: Disabled by ACPI PNP
Apr 30 14:44:34 Sisif kernel: [    9.570555] PCI: Using ACPI for IRQ routing
Apr 30 14:44:34 Sisif kernel: [    9.570558] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 30 14:44:34 Sisif kernel: [    9.630368] NET: Registered protocol family 8
Apr 30 14:44:34 Sisif kernel: [    9.630370] NET: Registered protocol family 20
Apr 30 14:44:34 Sisif kernel: [    9.630409] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 30 14:44:34 Sisif kernel: [    9.630414] hpet0: 3 64-bit timers, 14318180 Hz
Apr 30 14:44:34 Sisif kernel: [    9.631454] AppArmor: AppArmor Filesystem Enabled
Apr 30 14:44:34 Sisif kernel: [    7.558840] Time: hpet clocksource has been installed.
Apr 30 14:44:34 Sisif kernel: [    7.558862] Switched to high resolution mode on CPU 0
Apr 30 14:44:34 Sisif kernel: [    9.634366] Switched to high resolution mode on CPU 1
Apr 30 14:44:34 Sisif kernel: [    9.643222] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643225] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643229] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643232] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643235] system 00:00: iomem range 0x100000-0x7f6d33ff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643238] system 00:00: iomem range 0x7f6d3400-0x7f6fffff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643241] system 00:00: iomem range 0x7f700000-0x7f7fffff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643244] system 00:00: iomem range 0x7f700000-0x7fefffff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643248] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643251] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643254] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643258] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643265] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643268] system 00:02: ioport range 0x1000-0x1005 has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643271] system 00:02: ioport range 0x1008-0x100f has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643277] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643280] system 00:03: ioport range 0x1006-0x1007 has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643284] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643287] system 00:03: ioport range 0x1060-0x107f has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643290] system 00:03: ioport range 0x1080-0x10bf has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643293] system 00:03: ioport range 0x10c0-0x10df has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643296] system 00:03: ioport range 0x1010-0x102f has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643299] system 00:03: ioport range 0x809-0x809 has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643308] system 00:08: ioport range 0xc80-0xcff could not be reserved
Apr 30 14:44:34 Sisif kernel: [    9.643311] system 00:08: ioport range 0x910-0x91f has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643314] system 00:08: ioport range 0x920-0x92f has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643317] system 00:08: ioport range 0xcb0-0xcbf has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643320] system 00:08: ioport range 0x930-0x97f has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.643328] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Apr 30 14:44:34 Sisif kernel: [    9.673791] PCI: Bridge: 0000:00:1c.0
Apr 30 14:44:34 Sisif kernel: [    9.673793]   IO window: disabled.
Apr 30 14:44:34 Sisif kernel: [    9.673799]   MEM window: efd00000-efdfffff
Apr 30 14:44:34 Sisif kernel: [    9.673804]   PREFETCH window: disabled.
Apr 30 14:44:34 Sisif kernel: [    9.673810] PCI: Bridge: 0000:00:1c.3
Apr 30 14:44:34 Sisif kernel: [    9.673813]   IO window: d000-dfff
Apr 30 14:44:34 Sisif kernel: [    9.673819]   MEM window: efa00000-efcfffff
Apr 30 14:44:34 Sisif kernel: [    9.673824]   PREFETCH window: e0000000-e01fffff
Apr 30 14:44:34 Sisif kernel: [    9.673830] PCI: Bridge: 0000:00:1e.0
Apr 30 14:44:34 Sisif kernel: [    9.673832]   IO window: disabled.
Apr 30 14:44:34 Sisif kernel: [    9.673838]   MEM window: ef900000-ef9fffff
Apr 30 14:44:34 Sisif kernel: [    9.673842]   PREFETCH window: disabled.
Apr 30 14:44:34 Sisif kernel: [    9.673877] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 14:44:34 Sisif kernel: [    9.673885] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 14:44:34 Sisif kernel: [    9.673909] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Apr 30 14:44:34 Sisif kernel: [    9.673915] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 14:44:34 Sisif kernel: [    9.673930] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 30 14:44:34 Sisif kernel: [    9.673943] NET: Registered protocol family 2
Apr 30 14:44:34 Sisif kernel: [    9.711218] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 30 14:44:34 Sisif kernel: [    9.711455] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 30 14:44:34 Sisif kernel: [    9.712199] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 30 14:44:34 Sisif kernel: [    9.712577] TCP: Hash tables configured (established 131072 bind 65536)
Apr 30 14:44:34 Sisif kernel: [    9.712580] TCP reno registered
Apr 30 14:44:34 Sisif kernel: [    9.723321] checking if image is initramfs... it is
Apr 30 14:44:34 Sisif kernel: [   10.415907] Freeing initrd memory: 7267k freed
Apr 30 14:44:34 Sisif kernel: [   10.416077] Simple Boot Flag at 0x79 set to 0x1
Apr 30 14:44:34 Sisif kernel: [   10.416821] audit: initializing netlink socket (disabled)
Apr 30 14:44:34 Sisif kernel: [   10.416835] audit(1209555852.528:1): initialized
Apr 30 14:44:34 Sisif kernel: [    8.341694] highmem bounce pool size: 64 pages
Apr 30 14:44:34 Sisif kernel: [   10.419271] VFS: Disk quotas dquot_6.5.1
Apr 30 14:44:34 Sisif kernel: [    8.343969] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 30 14:44:34 Sisif kernel: [    8.344117] io scheduler noop registered
Apr 30 14:44:34 Sisif kernel: [    8.344120] io scheduler anticipatory registered
Apr 30 14:44:34 Sisif kernel: [    8.344122] io scheduler deadline registered
Apr 30 14:44:34 Sisif kernel: [    8.344133] io scheduler cfq registered (default)
Apr 30 14:44:34 Sisif kernel: [    8.344145] Boot video device is 0000:00:02.0
Apr 30 14:44:34 Sisif kernel: [    8.344367] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 14:44:34 Sisif kernel: [    8.344425] assign_interrupt_mode Found MSI capability
Apr 30 14:44:34 Sisif kernel: [    8.344475] Allocate Port Service[0000:00:1c.0:pcie00]
Apr 30 14:44:34 Sisif kernel: [    8.344516] Allocate Port Service[0000:00:1c.0:pcie02]
Apr 30 14:44:34 Sisif kernel: [    8.344625] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 14:44:34 Sisif kernel: [    8.344683] assign_interrupt_mode Found MSI capability
Apr 30 14:44:34 Sisif kernel: [    8.344730] Allocate Port Service[0000:00:1c.3:pcie00]
Apr 30 14:44:34 Sisif kernel: [    8.344768] Allocate Port Service[0000:00:1c.3:pcie02]
Apr 30 14:44:34 Sisif kernel: [    8.345049] isapnp: Scanning for PnP cards...
Apr 30 14:44:34 Sisif kernel: [    8.699243] isapnp: No Plug & Play device found
Apr 30 14:44:34 Sisif kernel: [   10.804488] Real Time Clock Driver v1.12ac
Apr 30 14:44:34 Sisif kernel: [   10.804649] hpet_resources: 0xfed00000 is busy
Apr 30 14:44:34 Sisif kernel: [   10.804703] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 30 14:44:34 Sisif kernel: [   10.805995] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 30 14:44:34 Sisif kernel: [   10.806070] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 30 14:44:34 Sisif kernel: [   10.806176] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 30 14:44:34 Sisif kernel: [   10.809032] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 30 14:44:34 Sisif kernel: [   10.809037] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 30 14:44:34 Sisif kernel: [    8.755355] mice: PS/2 mouse device common for all mice
Apr 30 14:44:34 Sisif kernel: [    8.755497] EISA: Probing bus 0 at eisa.0
Apr 30 14:44:34 Sisif kernel: [    8.755566] EISA: Mainboard UO_FFFF detected.
Apr 30 14:44:34 Sisif kernel: [    8.755608] Cannot allocate resource for EISA slot 1
Apr 30 14:44:34 Sisif kernel: [    8.755641] EISA: Detected 0 cards.
Apr 30 14:44:34 Sisif kernel: [    8.755643] cpuidle: using governor ladder
Apr 30 14:44:34 Sisif kernel: [    8.755646] cpuidle: using governor menu
Apr 30 14:44:34 Sisif kernel: [    8.755747] NET: Registered protocol family 1
Apr 30 14:44:34 Sisif kernel: [    8.755778] Using IPI No-Shortcut mode
Apr 30 14:44:34 Sisif kernel: [    8.755813] registered taskstats version 1
Apr 30 14:44:34 Sisif kernel: [    8.755931]   Magic number: 4:93:733
Apr 30 14:44:34 Sisif kernel: [    8.756040] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 30 14:44:34 Sisif kernel: [    8.756042] EDD information not available.
Apr 30 14:44:34 Sisif kernel: [    8.756212] Freeing unused kernel memory: 364k freed
Apr 30 14:44:34 Sisif kernel: [   10.833767] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 30 14:44:34 Sisif kernel: [    9.973646] fuse init (API version 7.9)
Apr 30 14:44:34 Sisif kernel: [    9.995031] ACPI: SSDT 7F6D4134, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Apr 30 14:44:34 Sisif kernel: [    9.995226] ACPI: SSDT 7F6D3EE9, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Apr 30 14:44:34 Sisif kernel: [    9.995804] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 14:44:34 Sisif kernel: [    9.995809] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 30 14:44:34 Sisif kernel: [    9.996038] ACPI: SSDT 7F6D4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Apr 30 14:44:34 Sisif kernel: [    9.996214] ACPI: SSDT 7F6D40AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Apr 30 14:44:34 Sisif kernel: [   12.072266] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 14:44:34 Sisif kernel: [   12.072271] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 30 14:44:34 Sisif kernel: [   12.077484] ACPI: Thermal Zone [THM] (25 C)
Apr 30 14:44:34 Sisif kernel: [   10.427093] usbcore: registered new interface driver usbfs
Apr 30 14:44:34 Sisif kernel: [   10.427118] usbcore: registered new interface driver hub
Apr 30 14:44:34 Sisif kernel: [   10.437885] usbcore: registered new device driver usb
Apr 30 14:44:34 Sisif kernel: [   10.438048] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 14:44:34 Sisif kernel: [   10.438069] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 14:44:34 Sisif kernel: [   12.538015] USB Universal Host Controller Interface driver v3.0
Apr 30 14:44:34 Sisif kernel: [   12.554126] SCSI subsystem initialized
Apr 30 14:44:34 Sisif kernel: [   12.581959] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Apr 30 14:44:34 Sisif kernel: [   12.582001] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 14:44:34 Sisif kernel: [   12.582014] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 30 14:44:34 Sisif kernel: [   12.582018] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 30 14:44:34 Sisif kernel: [   12.582267] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr 30 14:44:34 Sisif kernel: [   12.582302] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
Apr 30 14:44:34 Sisif kernel: [   12.582451] usb usb1: configuration #1 chosen from 1 choice
Apr 30 14:44:34 Sisif kernel: [   12.582476] hub 1-0:1.0: USB hub found
Apr 30 14:44:34 Sisif kernel: [   12.582482] hub 1-0:1.0: 2 ports detected
Apr 30 14:44:34 Sisif kernel: [   12.599016] libata version 3.00 loaded.
Apr 30 14:44:34 Sisif kernel: [   12.685904] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
Apr 30 14:44:34 Sisif kernel: [   12.685918] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 30 14:44:34 Sisif kernel: [   12.685923] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 30 14:44:34 Sisif kernel: [   12.685950] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr 30 14:44:34 Sisif kernel: [   12.685987] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bf60
Apr 30 14:44:34 Sisif kernel: [   12.686111] usb usb2: configuration #1 chosen from 1 choice
Apr 30 14:44:34 Sisif kernel: [   12.686137] hub 2-0:1.0: USB hub found
Apr 30 14:44:34 Sisif kernel: [   12.686143] hub 2-0:1.0: 2 ports detected
Apr 30 14:44:34 Sisif kernel: [   10.714456] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
Apr 30 14:44:34 Sisif kernel: [   10.714470] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 30 14:44:34 Sisif kernel: [   10.714475] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 30 14:44:34 Sisif kernel: [   10.714501] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr 30 14:44:34 Sisif kernel: [   10.714536] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000bf40
Apr 30 14:44:34 Sisif kernel: [   10.714665] usb usb3: configuration #1 chosen from 1 choice
Apr 30 14:44:34 Sisif kernel: [   10.714690] hub 3-0:1.0: USB hub found
Apr 30 14:44:34 Sisif kernel: [   10.714696] hub 3-0:1.0: 2 ports detected
Apr 30 14:44:34 Sisif kernel: [   10.817419] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
Apr 30 14:44:34 Sisif kernel: [   10.817433] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Apr 30 14:44:34 Sisif kernel: [   10.817438] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Apr 30 14:44:34 Sisif kernel: [   10.817466] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Apr 30 14:44:34 Sisif kernel: [   10.817501] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000bf20
Apr 30 14:44:34 Sisif kernel: [   10.817625] usb usb4: configuration #1 chosen from 1 choice
Apr 30 14:44:34 Sisif kernel: [   10.817651] hub 4-0:1.0: USB hub found
Apr 30 14:44:34 Sisif kernel: [   10.817656] hub 4-0:1.0: 2 ports detected
Apr 30 14:44:34 Sisif kernel: [   10.921502] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Apr 30 14:44:34 Sisif kernel: [   10.974276] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 30 14:44:34 Sisif kernel: [   13.060367] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 14:44:34 Sisif kernel: [   13.060419] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 14:44:34 Sisif kernel: [   13.060431] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 30 14:44:34 Sisif kernel: [   13.060435] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 30 14:44:34 Sisif kernel: [   13.060474] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Apr 30 14:44:34 Sisif kernel: [   13.064375] ehci_hcd 0000:00:1d.7: debug port 1
Apr 30 14:44:34 Sisif kernel: [   13.064381] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr 30 14:44:34 Sisif kernel: [   13.064390] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80000
Apr 30 14:44:34 Sisif kernel: [   13.077582] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 30 14:44:34 Sisif kernel: [   13.077712] usb usb5: configuration #1 chosen from 1 choice
Apr 30 14:44:34 Sisif kernel: [   13.077738] hub 5-0:1.0: USB hub found
Apr 30 14:44:34 Sisif kernel: [   13.077745] hub 5-0:1.0: 8 ports detected
Apr 30 14:44:34 Sisif kernel: [   13.120658] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 14:44:34 Sisif kernel: [   13.120692] b44.c:v2.0
Apr 30 14:44:34 Sisif kernel: [   13.140929] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 14:44:34 Sisif kernel: [   13.185741] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 14:44:34 Sisif kernel: [   13.185783] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 14:44:34 Sisif kernel: [   13.185798] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Apr 30 14:44:34 Sisif kernel: [   13.189834] ata_piix 0000:00:1f.2: version 2.12
Apr 30 14:44:34 Sisif kernel: [   13.189841] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Apr 30 14:44:34 Sisif kernel: [   13.189863] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 14:44:34 Sisif kernel: [   13.189901] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 14:44:34 Sisif kernel: [   13.190388] scsi0 : ata_piix
Apr 30 14:44:34 Sisif kernel: [   13.190627] scsi1 : ata_piix
Apr 30 14:44:34 Sisif kernel: [   13.191419] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Apr 30 14:44:34 Sisif kernel: [   13.191422] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Apr 30 14:44:34 Sisif kernel: [   13.353343] ata1.00: ATA-7: ST9120822AS, 3.CDD, max UDMA/133
Apr 30 14:44:34 Sisif kernel: [   13.353348] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
Apr 30 14:44:34 Sisif kernel: [   11.293565] ata1.00: configured for UDMA/133
Apr 30 14:44:34 Sisif kernel: [   13.713173] ata2.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1B, max UDMA/33
Apr 30 14:44:34 Sisif kernel: [   13.908656] ata2.00: configured for UDMA/33
Apr 30 14:44:34 Sisif kernel: [   11.833440] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.CD PQ: 0 ANSI: 5
Apr 30 14:44:34 Sisif kernel: [   11.835731] scsi 1:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
Apr 30 14:44:34 Sisif kernel: [   13.918698] Driver 'sd' needs updating - please use bus_type methods
Apr 30 14:44:34 Sisif kernel: [   13.918785] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 14:44:34 Sisif kernel: [   13.918799] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 14:44:34 Sisif kernel: [   13.918802] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 14:44:34 Sisif kernel: [   13.918819] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 14:44:34 Sisif kernel: [   13.918874] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 14:44:34 Sisif kernel: [   13.918885] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 14:44:34 Sisif kernel: [   13.918888] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 14:44:34 Sisif kernel: [   13.918905] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 14:44:34 Sisif kernel: [   13.918909]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Apr 30 14:44:34 Sisif kernel: [   11.858036]  sda1 sda2 sda3
Apr 30 14:44:34 Sisif kernel: [   11.870312] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 30 14:44:34 Sisif kernel: [   11.875909] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 30 14:44:34 Sisif kernel: [   11.875929] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 30 14:44:34 Sisif kernel: [   13.962717] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr 30 14:44:34 Sisif kernel: [   13.962723] Uniform CD-ROM driver Revision: 3.20
Apr 30 14:44:34 Sisif kernel: [   13.962780] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 30 14:44:34 Sisif kernel: [   14.329349] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc00026e60070]
Apr 30 14:44:34 Sisif kernel: [   12.392088] Attempting manual resume
Apr 30 14:44:34 Sisif kernel: [   12.392092] swsusp: Resume From Partition 8:2
Apr 30 14:44:34 Sisif kernel: [   12.392094] PM: Checking swsusp image.
Apr 30 14:44:34 Sisif kernel: [   12.392281] PM: Resume from disk failed.
Apr 30 14:44:34 Sisif kernel: [   14.510161] kjournald starting.  Commit interval 5 seconds
Apr 30 14:44:34 Sisif kernel: [   12.434797] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 14:44:34 Sisif kernel: [   20.793042] Linux agpgart interface v0.102
Apr 30 14:44:34 Sisif kernel: [   20.824659] agpgart: Detected an Intel 945GM Chipset.
Apr 30 14:44:34 Sisif kernel: [   20.825226] agpgart: Detected 7932K stolen memory.
Apr 30 14:44:34 Sisif kernel: [   20.842612] agpgart: AGP aperture is 256M @ 0xd0000000
Apr 30 14:44:34 Sisif kernel: [   20.874136] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 30 14:44:34 Sisif kernel: [   20.908594] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 30 14:44:34 Sisif kernel: [   20.990262] ACPI: Battery Slot [BAT0] (battery present)
Apr 30 14:44:34 Sisif kernel: [   21.009408] ACPI: AC Adapter [AC] (on-line)
Apr 30 14:44:34 Sisif kernel: [   21.036981] input: Lid Switch as /devices/virtual/input/input2
Apr 30 14:44:34 Sisif kernel: [   21.037418] ACPI: Lid Switch [LID]
Apr 30 14:44:34 Sisif kernel: [   21.038267] input: Power Button (CM) as /devices/virtual/input/input3
Apr 30 14:44:34 Sisif kernel: [   21.068376] ACPI: Power Button (CM) [PBTN]
Apr 30 14:44:34 Sisif kernel: [   21.068509] input: Sleep Button (CM) as /devices/virtual/input/input4
Apr 30 14:44:34 Sisif kernel: [   21.100372] ACPI: Sleep Button (CM) [SBTN]
Apr 30 14:44:34 Sisif kernel: [   21.265847] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input5
Apr 30 14:44:34 Sisif kernel: [   21.288269] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr 30 14:44:34 Sisif kernel: [   21.296155] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
Apr 30 14:44:34 Sisif kernel: [   21.304266] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Apr 30 14:44:34 Sisif kernel: [   21.304443] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input7
Apr 30 14:44:34 Sisif kernel: [   21.336244] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Apr 30 14:44:34 Sisif kernel: [   21.336316] ACPI: WMI-Acer: Mapper loaded
Apr 30 14:44:34 Sisif kernel: [   21.996760] iTCO_vendor_support: vendor-support=0
Apr 30 14:44:34 Sisif kernel: [   22.015989] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Apr 30 14:44:34 Sisif kernel: [   22.016097] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Apr 30 14:44:34 Sisif kernel: [   22.016136] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 30 14:44:34 Sisif kernel: [   22.133887] intel_rng: FWH not detected
Apr 30 14:44:34 Sisif kernel: [   22.345072] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
Apr 30 14:44:34 Sisif kernel: [   22.345106] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 30 14:44:34 Sisif kernel: [   22.387810] sdhci: Secure Digital Host Controller Interface driver
Apr 30 14:44:34 Sisif kernel: [   22.387815] sdhci: Copyright(c) Pierre Ossman
Apr 30 14:44:34 Sisif kernel: [   22.448389] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
Apr 30 14:44:34 Sisif kernel: [   22.448416] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
Apr 30 14:44:34 Sisif kernel: [   22.448481] mmc0: SDHCI at 0xef9fd400 irq 23 DMA
Apr 30 14:44:34 Sisif kernel: [   24.559177] ricoh-mmc: Ricoh MMC Controller disabling driver
Apr 30 14:44:34 Sisif kernel: [   24.559181] ricoh-mmc: Copyright(c) Philip Langdale
Apr 30 14:44:34 Sisif kernel: [   24.559718] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 1)
Apr 30 14:44:34 Sisif kernel: [   24.559733] ricoh-mmc: Controller is now disabled.
Apr 30 14:44:34 Sisif kernel: [   24.588592] b43-phy0: Broadcom 4311 WLAN found
Apr 30 14:44:34 Sisif kernel: [   24.627085] input: PC Speaker as /devices/platform/pcspkr/input/input8
Apr 30 14:44:34 Sisif kernel: [   24.668207] phy0: Selected rate control algorithm 'simple'
Apr 30 14:44:34 Sisif kernel: [   23.210093] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
Apr 30 14:44:34 Sisif kernel: [   23.246231] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
Apr 30 14:44:34 Sisif kernel: [   25.373553] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Apr 30 14:44:34 Sisif kernel: [   23.937205] udev: renamed network interface wlan0 to eth1
Apr 30 14:44:34 Sisif kernel: [   26.052068] input: b43-phy0 as /devices/virtual/input/input10
Apr 30 14:44:34 Sisif kernel: [   24.346552] lp: driver loaded but no devices found
Apr 30 14:44:34 Sisif kernel: [   24.458807] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 14:44:34 Sisif kernel: [   27.498205] Registered led device: b43-phy0:tx
Apr 30 14:44:34 Sisif kernel: [   27.498233] Registered led device: b43-phy0:rx
Apr 30 14:44:34 Sisif kernel: [   27.498254] Registered led device: b43-phy0:radio
Apr 30 14:44:34 Sisif kernel: [   25.486597] NET: Registered protocol family 17
Apr 30 14:44:34 Sisif kernel: [   27.590431] usbcore: registered new interface driver ndiswrapper
Apr 30 14:44:34 Sisif kernel: [   27.741264] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
Apr 30 14:44:34 Sisif kernel: [   26.311536] EXT3 FS on sda1, internal journal
Apr 30 14:44:34 Sisif kernel: [   29.126605] kjournald starting.  Commit interval 5 seconds
Apr 30 14:44:34 Sisif kernel: [   27.051426] EXT3 FS on sda3, internal journal
Apr 30 14:44:34 Sisif kernel: [   27.051432] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 14:44:34 Sisif kernel: [   27.552267] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 14:44:34 Sisif kernel: [   28.795720] RPC: Registered udp transport module.
Apr 30 14:44:34 Sisif kernel: [   28.795724] RPC: Registered tcp transport module.
Apr 30 14:44:34 Sisif kernel: [   29.452733] No dock devices found.
Apr 30 14:44:34 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr 30 14:44:36 Sisif avahi-daemon[5303]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Apr 30 14:44:36 Sisif avahi-daemon[5303]: Successfully dropped root privileges.
Apr 30 14:44:36 Sisif avahi-daemon[5303]: avahi-daemon 0.6.22 starting up.
Apr 30 14:44:36 Sisif avahi-daemon[5303]: Successfully called chroot().
Apr 30 14:44:36 Sisif avahi-daemon[5303]: Successfully dropped remaining capabilities.
Apr 30 14:44:36 Sisif avahi-daemon[5303]: No service file found in /etc/avahi/services.
Apr 30 14:44:36 Sisif avahi-daemon[5303]: Network interface enumeration completed.
Apr 30 14:44:36 Sisif avahi-daemon[5303]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 30 14:44:36 Sisif avahi-daemon[5303]: Server startup complete. Host name is Sisif.local. Local service cookie is 4047024258.
Apr 30 14:44:36 Sisif kernel: [   33.762455] ppdev: user-space parallel port driver
Apr 30 14:44:36 Sisif kernel: [   31.866458] audit(1209555876.627:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5337 profile="/usr/sbin/cupsd" namespace="default"
Apr 30 14:44:36 Sisif kernel: [   31.914860] apm: BIOS not found.
Apr 30 14:44:38 Sisif kernel: [   33.421578] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Apr 30 14:44:38 Sisif exportfs[5510]: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.10.2:/home/itch/Blonda".   Assuming default behaviour ('no_subtree_check').   NOTE: this default has changed since nfs-utils version 1.0.x 
Apr 30 14:44:38 Sisif kernel: [   35.743764] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Apr 30 14:44:38 Sisif kernel: [   33.684187] NFSD: starting 90-second grace period
Apr 30 14:44:38 Sisif dhclient: DHCPREQUEST of 192.168.0.118 on eth0 to 255.255.255.255 port 67
Apr 30 14:44:40 Sisif nmbd[5580]: [2008/04/30 14:44:40, 0] nmbd/nmbd_subnetdb.c:create_subnets(190) 
Apr 30 14:44:40 Sisif nmbd[5580]:   create_subnets: No local interfaces ! 
Apr 30 14:44:40 Sisif nmbd[5580]: [2008/04/30 14:44:40, 0] nmbd/nmbd_subnetdb.c:create_subnets(191) 
Apr 30 14:44:40 Sisif nmbd[5580]:   create_subnets: Waiting for an interface to appear ... 
Apr 30 14:44:40 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr 30 14:44:41 Sisif dhcdbd: Started up.
Apr 30 14:44:41 Sisif hcid[5657]: Bluetooth HCI daemon
Apr 30 14:44:41 Sisif kernel: [   36.846245] Bluetooth: Core ver 2.11
Apr 30 14:44:41 Sisif kernel: [   36.846412] NET: Registered protocol family 31
Apr 30 14:44:41 Sisif kernel: [   36.846417] Bluetooth: HCI device and connection manager initialized
Apr 30 14:44:41 Sisif kernel: [   36.846424] Bluetooth: HCI socket layer initialized
Apr 30 14:44:41 Sisif hcid[5657]: Starting SDP server
Apr 30 14:44:41 Sisif kernel: [   36.968950] Bluetooth: L2CAP ver 2.9
Apr 30 14:44:41 Sisif kernel: [   36.968961] Bluetooth: L2CAP socket layer initialized
Apr 30 14:44:41 Sisif hcid[5657]: Created local server at unix:abstract=/var/run/dbus-3kAmYT2jsG,guid=b8a0639658516a83001950a048185ba9
Apr 30 14:44:41 Sisif kernel: [   37.052344] Bluetooth: RFCOMM socket layer initialized
Apr 30 14:44:41 Sisif kernel: [   37.052357] Bluetooth: RFCOMM TTY layer initialized
Apr 30 14:44:41 Sisif kernel: [   37.052359] Bluetooth: RFCOMM ver 1.8
Apr 30 14:44:41 Sisif audio[5679]: Bluetooth Audio daemon
Apr 30 14:44:41 Sisif input[5702]: Bluetooth Input daemon
Apr 30 14:44:41 Sisif audio[5679]: Unix socket created: 5
Apr 30 14:44:41 Sisif audio[5679]: audio.conf: Key file does not have key 'Enable'
Apr 30 14:44:41 Sisif audio[5679]: audio.conf: Key file does not have key 'Disable'
Apr 30 14:44:41 Sisif audio[5679]: add_service_record: got record id 0x10000
Apr 30 14:44:41 Sisif audio[5679]: audio.conf: Key file does not have key 'Disable'
Apr 30 14:44:41 Sisif input[5702]: Registered input manager path:/org/bluez/input
Apr 30 14:44:41 Sisif audio[5679]: audio.conf: Key file does not have group 'A2DP'
Apr 30 14:44:41 Sisif last message repeated 3 times
Apr 30 14:44:41 Sisif audio[5679]: SEP 0x806d578 registered: type:0 codec:0 seid:1
Apr 30 14:44:41 Sisif audio[5679]: add_service_record: got record id 0x10001
Apr 30 14:44:41 Sisif audio[5679]: add_service_record: got record id 0x10002
Apr 30 14:44:41 Sisif audio[5679]: add_service_record: got record id 0x10003
Apr 30 14:44:41 Sisif audio[5679]: Registered manager path:/org/bluez/audio
Apr 30 14:44:44 Sisif ntpd[5752]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 14:44:44 Sisif ntpd[5753]: precision = 1.000 usec
Apr 30 14:44:44 Sisif kernel: [   39.680491] NET: Registered protocol family 10
Apr 30 14:44:44 Sisif kernel: [   39.680780] lo: Disabled Privacy Extensions
Apr 30 14:44:44 Sisif kernel: [   39.682156] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 30 14:44:44 Sisif kernel: [   39.682843] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 14:44:44 Sisif ntpd[5753]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 14:44:44 Sisif ntpd[5753]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 14:44:44 Sisif ntpd[5753]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 14:44:44 Sisif ntpd[5753]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 14:44:44 Sisif ntpd[5753]: kernel time sync status 0040
Apr 30 14:44:44 Sisif ntpd[5753]: frequency initialized -57.973 PPM from /var/lib/ntp/ntp.drift
Apr 30 14:44:45 Sisif kernel: [   41.212180] [drm] Initialized drm 1.1.0 20060810
Apr 30 14:44:45 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 30 14:44:46 Sisif kernel: [   43.336584] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 14:44:46 Sisif kernel: [   43.336596] PCI: Setting latency timer of device 0000:00:02.0 to 64
Apr 30 14:44:46 Sisif kernel: [   41.262628] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr 30 14:44:46 Sisif anacron[5821]: Anacron 2.3 started on 2008-04-30
Apr 30 14:44:46 Sisif anacron[5821]: Normal exit (0 jobs run)
Apr 30 14:44:46 Sisif /usr/sbin/cron[5852]: (CRON) INFO (pidfile fd = 3)
Apr 30 14:44:46 Sisif /usr/sbin/cron[5853]: (CRON) STARTUP (fork ok)
Apr 30 14:44:46 Sisif /usr/sbin/cron[5853]: (CRON) INFO (Running @reboot jobs)
Apr 30 14:44:46 Sisif ntpd_initres[5771]: host name not found: ntp2a.mcc.ac.uk
Apr 30 14:44:46 Sisif ntpd_initres[5771]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 14:44:46 Sisif ntpd_initres[5771]: host name not found: ntp.landau.ac.ru
Apr 30 14:44:46 Sisif ntpd_initres[5771]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 14:44:47 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr 30 14:44:47 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 14:44:47 Sisif dhclient: receive_packet failed on eth0: Network is down
Apr 30 14:44:47 Sisif kernel: [   44.630818] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 14:44:47 Sisif kernel: [   42.598426] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 14:44:47 Sisif kernel: [   42.610354] usbcore: deregistering interface driver ndiswrapper
Apr 30 14:44:47 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 14:44:47 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 14:44:47 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 14:44:47 Sisif dhclient: All rights reserved.
Apr 30 14:44:47 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 14:44:47 Sisif dhclient: 
Apr 30 14:44:47 Sisif kernel: [   42.699850] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 14:44:47 Sisif dhclient: Bind socket to interface: No such device
Apr 30 14:44:47 Sisif kernel: [   42.829658] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 14:44:47 Sisif kernel: [   42.829955] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 14:44:47 Sisif kernel: [   42.830019] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 14:44:47 Sisif kernel: [   42.835008] ndiswrapper: using IRQ 16
Apr 30 14:44:47 Sisif kernel: [   43.190662] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 14:44:47 Sisif kernel: [   43.190758] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 14:44:47 Sisif kernel: [   43.193620] usbcore: registered new interface driver ndiswrapper
Apr 30 14:44:47 Sisif kernel: [   45.269818] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 14:44:47 Sisif kernel: [   45.269903] udev: renamed network interface wlan0 to eth1
Apr 30 14:44:47 Sisif kernel: [   45.281257] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 14:44:48 Sisif kernel: [   43.243370] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 14:44:48 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 14:44:48 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 14:44:48 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 14:44:48 Sisif dhclient: All rights reserved.
Apr 30 14:44:48 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 14:44:48 Sisif dhclient: 
Apr 30 14:44:48 Sisif kernel: [   45.501839] ndiswrapper: device eth1 removed
Apr 30 14:44:48 Sisif kernel: [   45.501884] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 14:44:48 Sisif kernel: [   45.502067] usbcore: deregistering interface driver ndiswrapper
Apr 30 14:44:48 Sisif kernel: [   43.481254] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 14:44:48 Sisif kernel: [   43.495146] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 14:44:48 Sisif kernel: [   43.495579] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 14:44:48 Sisif kernel: [   43.495667] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 14:44:48 Sisif kernel: [   43.501243] ndiswrapper: using IRQ 16
Apr 30 14:44:48 Sisif kernel: [   43.862776] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 14:44:48 Sisif kernel: [   43.864975] eth1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 14:44:48 Sisif kernel: [   45.941017] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 14:44:48 Sisif kernel: [   45.941139] udev: renamed network interface wlan0 to eth1
Apr 30 14:44:48 Sisif kernel: [   45.945090] ndiswrapper (wrap_procfs_add_ndis_device:399): eth1 already registered?
Apr 30 14:44:48 Sisif kernel: [   45.949337] usbcore: registered new interface driver ndiswrapper
Apr 30 14:44:48 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 30 14:44:48 Sisif dhclient: send_packet: No such device
Apr 30 14:44:49 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 14:44:49 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 14:44:49 Sisif dhclient: Sending on   Socket/fallback
Apr 30 14:44:49 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr 30 14:44:49 Sisif dhclient: send_packet: Network is down
Apr 30 14:44:49 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 14:44:52 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr 30 14:44:52 Sisif dhclient: send_packet: Network is down
Apr 30 14:44:54 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 30 14:44:54 Sisif dhclient: send_packet: No such device
Apr 30 14:44:58 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr 30 14:44:58 Sisif dhclient: send_packet: Network is down
Apr 30 14:44:59 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr 30 14:44:59 Sisif dhclient: send_packet: Network is down
Apr 30 14:45:05 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr 30 14:45:05 Sisif dhclient: send_packet: No such device
Apr 30 14:45:06 Sisif dhclient: No DHCPOFFERS received.
Apr 30 14:45:06 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 14:45:06 Sisif kernel: [   63.340097] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 14:45:06 Sisif avahi-autoipd(eth1)[6304]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 30 14:45:06 Sisif avahi-autoipd(eth1)[6304]: Successfully called chroot().
Apr 30 14:45:06 Sisif avahi-autoipd(eth1)[6304]: Successfully dropped root privileges.
Apr 30 14:45:06 Sisif avahi-autoipd(eth1)[6304]: Starting with address 169.254.4.188
Apr 30 14:45:08 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr 30 14:45:10 Sisif hcid[5657]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Apr 30 14:45:10 Sisif hcid[5657]: Default authorization agent (:1.18, /org/bluez/auth) registered
Apr 30 14:45:11 Sisif avahi-autoipd(eth1)[6304]: Callout BIND, address 169.254.4.188 on interface eth1
Apr 30 14:45:13 Sisif avahi-daemon[5303]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 14:45:13 Sisif avahi-daemon[5303]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 14:45:13 Sisif avahi-daemon[5303]: Registering new address record for 169.254.4.188 on eth1.IPv4.
Apr 30 14:45:15 Sisif avahi-autoipd(eth1)[6304]: Successfully claimed IP address 169.254.4.188
Apr 30 14:45:16 Sisif dhclient: No DHCPOFFERS received.
Apr 30 14:45:16 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 14:45:17 Sisif ntpd[5753]: ntpd exiting on signal 15
Apr 30 14:45:18 Sisif kernel: [   73.265334] CPU0 attaching NULL sched-domain.
Apr 30 14:45:18 Sisif kernel: [   73.265340] CPU1 attaching NULL sched-domain.
Apr 30 14:45:18 Sisif kernel: [   73.281283] CPU0 attaching sched-domain:
Apr 30 14:45:18 Sisif kernel: [   73.281287]  domain 0: span 03
Apr 30 14:45:18 Sisif kernel: [   73.281289]   groups: 01 02
Apr 30 14:45:18 Sisif kernel: [   73.281292] CPU1 attaching sched-domain:
Apr 30 14:45:18 Sisif kernel: [   73.281294]  domain 0: span 03
Apr 30 14:45:18 Sisif kernel: [   73.281296]   groups: 02 01
Apr 30 14:45:19 Sisif dhclient: No DHCPOFFERS received.
Apr 30 14:45:19 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 14:45:20 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 14:45:23 Sisif avahi-daemon[5303]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 14:45:23 Sisif avahi-daemon[5303]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 14:45:23 Sisif avahi-autoipd(eth1)[6304]: SIOCSIFFLAGS failed: Permission denied
Apr 30 14:45:23 Sisif avahi-autoipd(eth1)[6304]: Callout STOP, address 169.254.4.188 on interface eth1
Apr 30 14:45:23 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 14:45:23 Sisif avahi-daemon[5303]: Withdrawing address record for 169.254.4.188 on eth1.
Apr 30 14:45:23 Sisif avahi-autoipd(eth1)[6305]: client: RTNETLINK answers: No such process
Apr 30 14:45:23 Sisif kernel: [   78.901589] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 14:45:24 Sisif kernel: [   79.331158] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 14:45:24 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 14:45:24 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 14:45:24 Sisif dhclient: All rights reserved.
Apr 30 14:45:24 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 14:45:24 Sisif dhclient: 
Apr 30 14:45:24 Sisif kernel: [   82.104817] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 30 14:45:25 Sisif ntpdate[6672]: can't find host ntp2a.mcc.ac.uk 
Apr 30 14:45:25 Sisif ntpdate[6672]: can't find host ntp.landau.ac.ru 
Apr 30 14:45:25 Sisif ntpdate[6672]: no servers can be used, exiting
Apr 30 14:45:25 Sisif ntpd[6926]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 14:45:25 Sisif ntpd[6927]: precision = 1.000 usec
Apr 30 14:45:25 Sisif ntpd[6927]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 14:45:25 Sisif ntpd[6927]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 14:45:25 Sisif ntpd[6927]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 14:45:25 Sisif ntpd[6927]: bind() fd 19, family 10, port 123, scope 6, addr fe80::219:7eff:fea0:3d2a, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
Apr 30 14:45:25 Sisif ntpd[6927]: unable to create socket on eth1 (3) for fe80::219:7eff:fea0:3d2a#123
Apr 30 14:45:25 Sisif ntpd[6927]: failed to initialize interface for address fe80::219:7eff:fea0:3d2a
Apr 30 14:45:25 Sisif ntpd[6927]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Apr 30 14:45:25 Sisif ntpd[6927]: kernel time sync status 0040
Apr 30 14:45:25 Sisif ntpd[6927]: frequency initialized -57.973 PPM from /var/lib/ntp/ntp.drift
Apr 30 14:45:25 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 14:45:25 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 14:45:25 Sisif dhclient: Sending on   Socket/fallback
Apr 30 14:45:26 Sisif ntpdate[6764]: can't find host ntp2a.mcc.ac.uk 
Apr 30 14:45:26 Sisif ntpdate[6764]: can't find host ntp.landau.ac.ru 
Apr 30 14:45:26 Sisif ntpdate[6764]: no servers can be used, exiting
Apr 30 14:45:26 Sisif ntpd[6927]: bind() fd 20, family 10, port 123, scope 6, addr fe80::219:7eff:fea0:3d2a, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
Apr 30 14:45:26 Sisif ntpd[6927]: unable to create socket on eth1 (5) for fe80::219:7eff:fea0:3d2a#123
Apr 30 14:45:26 Sisif ntpd[6927]: failed to initialize interface for address fe80::219:7eff:fea0:3d2a
Apr 30 14:45:26 Sisif avahi-daemon[5303]: Registering new address record for fe80::219:7eff:fea0:3d2a on eth1.*.
Apr 30 14:45:27 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 14:45:27 Sisif ntpd_initres[6928]: host name not found: ntp2a.mcc.ac.uk
Apr 30 14:45:27 Sisif ntpd_initres[6928]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 14:45:27 Sisif ntpd_initres[6928]: host name not found: ntp.landau.ac.ru
Apr 30 14:45:27 Sisif ntpd_initres[6928]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 14:45:27 Sisif ntpdate[6555]: can't find host ntp2a.mcc.ac.uk 
Apr 30 14:45:27 Sisif ntpdate[6555]: can't find host ntp.landau.ac.ru 
Apr 30 14:45:27 Sisif ntpdate[6555]: no servers can be used, exiting
Apr 30 14:45:32 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 14:45:33 Sisif dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
Apr 30 14:45:33 Sisif avahi-daemon[5303]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 14:45:33 Sisif avahi-daemon[5303]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 14:45:33 Sisif avahi-daemon[5303]: Registering new address record for 192.168.1.102 on eth1.IPv4.
Apr 30 14:45:33 Sisif dhclient: bound to 192.168.1.102 -- renewal in 34811 seconds.
Apr 30 14:45:35 Sisif kernel: [   92.678355] eth1: no IPv6 routers present
Apr 30 14:46:29 Sisif nmbd[5580]: [2008/04/30 14:46:29, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 14:46:29 Sisif nmbd[5580]:   Packet send failed to 169.254.255.255(138) ERRNO=Invalid argument 
Apr 30 14:46:46 Sisif kernel: [  162.084559] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Apr 30 14:47:28 Sisif kernel: [  202.212342] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 14:47:28 Sisif kernel: [  204.347402] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 14:47:28 Sisif kernel: [  204.347436] b44.c:v2.0
Apr 30 14:47:28 Sisif kernel: [  204.368151] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 14:50:26 Sisif ntpd[6927]: Listening on interface #6 eth1, fe80::219:7eff:fea0:3d2a#123 Enabled
Apr 30 14:50:26 Sisif ntpd[6927]: Listening on interface #7 eth1, 192.168.1.102#123 Enabled
Apr 30 14:51:05 Sisif nmbd[5580]: [2008/04/30 14:51:05, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Apr 30 14:51:05 Sisif nmbd[5580]:   ***** 
Apr 30 14:51:05 Sisif nmbd[5580]:    
Apr 30 14:51:05 Sisif nmbd[5580]:   Samba name server SISIF is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.102 
Apr 30 14:51:05 Sisif nmbd[5580]:    
Apr 30 14:51:05 Sisif nmbd[5580]:   ***** 
Apr 30 14:59:36 Sisif kernel: [  931.423837] usb 5-3: new high speed USB device using ehci_hcd and address 2
Apr 30 14:59:36 Sisif kernel: [  931.557807] usb 5-3: configuration #1 chosen from 1 choice
Apr 30 14:59:37 Sisif kernel: [  931.890715] usbcore: registered new interface driver libusual
Apr 30 14:59:37 Sisif kernel: [  933.994433] Initializing USB Mass Storage driver...
Apr 30 14:59:37 Sisif kernel: [  933.996101] scsi2 : SCSI emulation for USB Mass Storage devices
Apr 30 14:59:37 Sisif kernel: [  933.997573] usbcore: registered new interface driver usb-storage
Apr 30 14:59:37 Sisif kernel: [  933.997581] USB Mass Storage support registered.
Apr 30 14:59:37 Sisif kernel: [  933.998040] usb-storage: device found at 2
Apr 30 14:59:37 Sisif kernel: [  933.998044] usb-storage: waiting for device to settle before scanning
Apr 30 14:59:42 Sisif kernel: [  936.918754] usb-storage: device scan complete
Apr 30 14:59:42 Sisif kernel: [  938.994622] scsi 2:0:0:0: Direct-Access     SONY     "PSP" MS         1.00 PQ: 0 ANSI: 0 CCS
Apr 30 14:59:42 Sisif kernel: [  936.924306] sd 2:0:0:0: [sdb] 483328 512-byte hardware sectors (247 MB)
Apr 30 14:59:42 Sisif kernel: [  936.924947] sd 2:0:0:0: [sdb] Write Protect is off
Apr 30 14:59:42 Sisif kernel: [  936.924952] sd 2:0:0:0: [sdb] Mode Sense: 00 6a 20 00
Apr 30 14:59:42 Sisif kernel: [  936.924955] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Apr 30 14:59:42 Sisif kernel: [  936.927915] sd 2:0:0:0: [sdb] 483328 512-byte hardware sectors (247 MB)
Apr 30 14:59:42 Sisif kernel: [  936.928661] sd 2:0:0:0: [sdb] Write Protect is off
Apr 30 14:59:42 Sisif kernel: [  936.928665] sd 2:0:0:0: [sdb] Mode Sense: 00 6a 20 00
Apr 30 14:59:42 Sisif kernel: [  936.928667] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Apr 30 14:59:42 Sisif kernel: [  936.928673]  sdb: sdb1
Apr 30 14:59:42 Sisif kernel: [  936.931165] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Apr 30 14:59:42 Sisif kernel: [  936.931214] sd 2:0:0:0: Attached scsi generic sg2 type 0
Apr 30 14:59:43 Sisif hald: mounted /dev/sdb1 on behalf of uid 1000
Apr 30 15:01:01 Sisif hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 1000
Apr 30 15:01:05 Sisif kernel: [ 1019.833064] usb 5-3: USB disconnect, address 2
Apr 30 15:02:34 Sisif kernel: [ 1109.061476] usb 5-3: new high speed USB device using ehci_hcd and address 3
Apr 30 15:02:34 Sisif kernel: [ 1109.194007] usb 5-3: configuration #1 chosen from 1 choice
Apr 30 15:02:34 Sisif kernel: [ 1109.195143] scsi3 : SCSI emulation for USB Mass Storage devices
Apr 30 15:02:34 Sisif kernel: [ 1109.195368] usb-storage: device found at 3
Apr 30 15:02:34 Sisif kernel: [ 1109.195371] usb-storage: waiting for device to settle before scanning
Apr 30 15:02:39 Sisif kernel: [ 1114.195053] usb-storage: device scan complete
Apr 30 15:02:39 Sisif kernel: [ 1114.196926] scsi 3:0:0:0: Direct-Access     SONY     "PSP" MS         1.00 PQ: 0 ANSI: 0 CCS
Apr 30 15:02:39 Sisif kernel: [ 1114.199647] sd 3:0:0:0: [sdb] 7929856 512-byte hardware sectors (4060 MB)
Apr 30 15:02:39 Sisif kernel: [ 1114.200140] sd 3:0:0:0: [sdb] Write Protect is off
Apr 30 15:02:39 Sisif kernel: [ 1114.200144] sd 3:0:0:0: [sdb] Mode Sense: 00 6a 20 00
Apr 30 15:02:39 Sisif kernel: [ 1114.200147] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Apr 30 15:02:39 Sisif kernel: [ 1114.202901] sd 3:0:0:0: [sdb] 7929856 512-byte hardware sectors (4060 MB)
Apr 30 15:02:39 Sisif kernel: [ 1114.203397] sd 3:0:0:0: [sdb] Write Protect is off
Apr 30 15:02:39 Sisif kernel: [ 1114.203401] sd 3:0:0:0: [sdb] Mode Sense: 00 6a 20 00
Apr 30 15:02:39 Sisif kernel: [ 1114.203404] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Apr 30 15:02:39 Sisif kernel: [ 1114.203411]  sdb: sdb1
Apr 30 15:02:39 Sisif kernel: [ 1114.205119] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Apr 30 15:02:39 Sisif kernel: [ 1114.205170] sd 3:0:0:0: Attached scsi generic sg2 type 0
Apr 30 15:02:40 Sisif hald: mounted /dev/sdb1 on behalf of uid 1000
Apr 30 15:13:57 Sisif hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 1000
Apr 30 15:14:04 Sisif kernel: [ 1798.790246] usb 5-3: USB disconnect, address 3
Apr 30 15:17:01 Sisif /USR/SBIN/CRON[32195]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 15:44:34 Sisif -- MARK --
Apr 30 16:04:34 Sisif -- MARK --
Apr 30 16:17:01 Sisif /USR/SBIN/CRON[12423]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 16:21:49 Sisif kernel: [ 5861.887253] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 16:21:54 Sisif kernel: [ 5869.762904] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 16:21:54 Sisif kernel: [ 5867.748804] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 16:21:54 Sisif kernel: [ 5867.749769] b44.c:v2.0
Apr 30 16:21:54 Sisif kernel: [ 5867.769505] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 16:23:12 Sisif kernel: [ 5945.352228] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 16:23:15 Sisif kernel: [ 5949.917315] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 16:23:15 Sisif kernel: [ 5949.974671] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 16:23:15 Sisif kernel: [ 5949.974704] b44.c:v2.0
Apr 30 16:23:15 Sisif kernel: [ 5949.996847] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 16:24:14 Sisif kernel: [ 6006.966168] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 16:24:18 Sisif kernel: [ 6011.174949] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 16:24:18 Sisif kernel: [ 6011.237734] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 16:24:18 Sisif kernel: [ 6011.237767] b44.c:v2.0
Apr 30 16:24:18 Sisif kernel: [ 6011.261069] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 16:24:33 Sisif kernel: [ 6028.454399] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 16:24:39 Sisif kernel: [ 6032.133963] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 16:24:39 Sisif kernel: [ 6032.192178] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 16:24:39 Sisif kernel: [ 6032.192210] b44.c:v2.0
Apr 30 16:24:39 Sisif kernel: [ 6032.212285] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 16:28:10 Sisif kernel: [ 6242.838960] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 16:28:16 Sisif kernel: [ 6251.411703] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 16:28:16 Sisif kernel: [ 6249.393014] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 16:28:16 Sisif kernel: [ 6249.393049] b44.c:v2.0
Apr 30 16:28:16 Sisif kernel: [ 6249.416601] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 16:44:34 Sisif -- MARK --
Apr 30 17:04:34 Sisif -- MARK --
Apr 30 17:17:01 Sisif /USR/SBIN/CRON[25258]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 17:25:00 Sisif init: tty4 main process (4700) killed by TERM signal
Apr 30 17:25:00 Sisif init: tty5 main process (4701) killed by TERM signal
Apr 30 17:25:00 Sisif init: tty2 main process (4703) killed by TERM signal
Apr 30 17:25:00 Sisif init: tty3 main process (4705) killed by TERM signal
Apr 30 17:25:00 Sisif init: tty6 main process (4707) killed by TERM signal
Apr 30 17:25:00 Sisif init: tty1 main process (6172) killed by TERM signal
Apr 30 17:25:00 Sisif kernel: [ 9652.078657] compiz.real[6429]: segfault at 03100010 eip 08055a80 esp bfbc5ed0 error 4
Apr 30 17:25:02 Sisif kernel: [ 9653.434702] gdm[5721]: segfault at 7672657f eip b77e17e2 esp bfe1ead0 error 6
Apr 30 17:25:02 Sisif avahi-daemon[5303]: Got SIGTERM, quitting.
Apr 30 17:25:02 Sisif avahi-daemon[5303]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 17:25:02 Sisif nmbd[5580]: [2008/04/30 17:25:02, 0] nmbd/nmbd.c:terminate(58) 
Apr 30 17:25:02 Sisif nmbd[5580]:   Got SIGTERM: going down... 
Apr 30 17:25:04 Sisif rpc.statd[4539]: Caught signal 15, un-registering and exiting.
Apr 30 17:25:06 Sisif kernel: [ 9657.905183] ip6_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 17:25:06 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:25:08 Sisif kernel: [ 9659.264896] nfsd: last server has exited
Apr 30 17:25:08 Sisif kernel: [ 9659.264900] nfsd: unexporting all filesystems
Apr 30 17:25:08 Sisif mountd[5535]: Caught signal 15, un-registering and exiting.
Apr 30 17:25:08 Sisif exiting on signal 15
Apr 30 17:25:50 Sisif syslogd 1.5.0#1ubuntu1: restart.
Apr 30 17:25:50 Sisif kernel: Inspecting /boot/System.map-2.6.24-16-generic
Apr 30 17:25:50 Sisif kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Apr 30 17:25:50 Sisif kernel: Symbols match kernel version 2.6.24.
Apr 30 17:25:50 Sisif kernel: Loaded 21378 symbols from 98 modules.
Apr 30 17:25:50 Sisif kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Apr 30 17:25:50 Sisif kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 30 17:25:50 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 30 17:25:50 Sisif kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 30 17:25:50 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d3400 (usable)
Apr 30 17:25:50 Sisif kernel: [    0.000000]  BIOS-e820: 000000007f6d3400 - 0000000080000000 (reserved)
Apr 30 17:25:50 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Apr 30 17:25:50 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Apr 30 17:25:50 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 30 17:25:50 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Apr 30 17:25:50 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Apr 30 17:25:50 Sisif kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr 30 17:25:50 Sisif kernel: [    0.000000] 1142MB HIGHMEM available.
Apr 30 17:25:50 Sisif kernel: [    0.000000] 896MB LOWMEM available.
Apr 30 17:25:50 Sisif kernel: [    0.000000] Entering add_active_range(0, 0, 521939) 0 entries of 256 used
Apr 30 17:25:50 Sisif kernel: [    0.000000] Zone PFN ranges:
Apr 30 17:25:50 Sisif kernel: [    0.000000]   DMA             0 ->     4096
Apr 30 17:25:50 Sisif kernel: [    0.000000]   Normal       4096 ->   229376
Apr 30 17:25:50 Sisif kernel: [    0.000000]   HighMem    229376 ->   521939
Apr 30 17:25:50 Sisif kernel: [    0.000000] Movable zone start PFN for each node
Apr 30 17:25:50 Sisif kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 30 17:25:50 Sisif kernel: [    0.000000]     0:        0 ->   521939
Apr 30 17:25:50 Sisif kernel: [    0.000000] On node 0 totalpages: 521939
Apr 30 17:25:50 Sisif kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 30 17:25:50 Sisif kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 30 17:25:50 Sisif kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 30 17:25:50 Sisif kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Apr 30 17:25:50 Sisif kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Apr 30 17:25:50 Sisif kernel: [    0.000000]   HighMem zone: 2285 pages used for memmap
Apr 30 17:25:50 Sisif kernel: [    0.000000]   HighMem zone: 290278 pages, LIFO batch:31
Apr 30 17:25:50 Sisif kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 30 17:25:50 Sisif kernel: [    0.000000] DMI 2.4 present.
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: RSDT 7F6D39CD, 0040 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: FACP 7F6D4800, 0074 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: DSDT 7F6D5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: FACS 7F6E3C00, 0040
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: HPET 7F6D4F00, 0038 (r1 DELL    M07            1 ASL        61)
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: APIC 7F6D5000, 0068 (r1 DELL    M07     27D7060D ASL        47)
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: MCFG 7F6D4FC0, 003E (r16 DELL    M07     27D7060D ASL        61)
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: SLIC 7F6D509C, 0024 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: BOOT 7F6D4BC0, 0028 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: SSDT 7F6D3A0D, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 30 17:25:50 Sisif kernel: [    0.000000] Processor #0 6:14 APIC version 20
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 30 17:25:50 Sisif kernel: [    0.000000] Processor #1 6:14 APIC version 20
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 30 17:25:50 Sisif kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 30 17:25:50 Sisif kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 30 17:25:50 Sisif kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 30 17:25:50 Sisif kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 30 17:25:50 Sisif kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
Apr 30 17:25:50 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 30 17:25:50 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Apr 30 17:25:50 Sisif kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517862
Apr 30 17:25:50 Sisif kernel: [    0.000000] Kernel command line: root=UUID=35a5e031-c7e9-4597-9992-99d1d88d0eac ro quiet splash
Apr 30 17:25:50 Sisif kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Apr 30 17:25:50 Sisif kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Apr 30 17:25:50 Sisif kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 30 17:25:50 Sisif kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 30 17:25:50 Sisif kernel: [    0.000000] Initializing CPU#0
Apr 30 17:25:50 Sisif kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 30 17:25:50 Sisif kernel: [    0.000000] Detected 1729.099 MHz processor.
Apr 30 17:25:50 Sisif kernel: [    6.720280] Console: colour VGA+ 80x25
Apr 30 17:25:50 Sisif kernel: [    6.720283] console [tty0] enabled
Apr 30 17:25:50 Sisif kernel: [    6.720589] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 30 17:25:50 Sisif kernel: [    6.720987] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 30 17:25:50 Sisif kernel: [    6.842995] Memory: 2057924k/2087756k available (2157k kernel code, 28552k reserved, 998k data, 364k init, 1170252k highmem)
Apr 30 17:25:50 Sisif kernel: [    6.843005] virtual kernel memory layout:
Apr 30 17:25:50 Sisif kernel: [    6.843006]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Apr 30 17:25:50 Sisif kernel: [    6.843008]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 30 17:25:50 Sisif kernel: [    6.843009]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Apr 30 17:25:50 Sisif kernel: [    6.843010]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 30 17:25:50 Sisif kernel: [    6.843011]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Apr 30 17:25:50 Sisif kernel: [    6.843013]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Apr 30 17:25:50 Sisif kernel: [    6.843014]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Apr 30 17:25:50 Sisif kernel: [    6.843017] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 30 17:25:50 Sisif kernel: [    6.843062] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 30 17:25:50 Sisif kernel: [    6.843209] hpet clockevent registered
Apr 30 17:25:50 Sisif kernel: [    6.923180] Calibrating delay using timer specific routine.. 3461.85 BogoMIPS (lpj=6923708)
Apr 30 17:25:50 Sisif kernel: [    6.923204] Security Framework initialized
Apr 30 17:25:50 Sisif kernel: [    6.923213] SELinux:  Disabled at boot.
Apr 30 17:25:50 Sisif kernel: [    6.923229] AppArmor: AppArmor initialized
Apr 30 17:25:50 Sisif kernel: [    6.923234] Failure registering capabilities with primary security module.
Apr 30 17:25:50 Sisif kernel: [    6.923243] Mount-cache hash table entries: 512
Apr 30 17:25:50 Sisif kernel: [    6.923382] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 17:25:50 Sisif kernel: [    6.923392] monitor/mwait feature present.
Apr 30 17:25:50 Sisif kernel: [    6.923393] using mwait in idle threads.
Apr 30 17:25:50 Sisif kernel: [    6.923398] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 17:25:50 Sisif kernel: [    6.923400] CPU: L2 cache: 1024K
Apr 30 17:25:50 Sisif kernel: [    6.923403] CPU: Physical Processor ID: 0
Apr 30 17:25:50 Sisif kernel: [    6.923405] CPU: Processor Core ID: 0
Apr 30 17:25:50 Sisif kernel: [    6.923407] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 17:25:50 Sisif kernel: [    6.923416] Compat vDSO mapped to ffffe000.
Apr 30 17:25:50 Sisif kernel: [    6.923429] Checking 'hlt' instruction... OK.
Apr 30 17:25:50 Sisif kernel: [    6.939582] SMP alternatives: switching to UP code
Apr 30 17:25:50 Sisif kernel: [    6.941419] Early unpacking initramfs... done
Apr 30 17:25:50 Sisif kernel: [    7.291188] ACPI: Core revision 20070126
Apr 30 17:25:50 Sisif kernel: [    7.291248] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 30 17:25:50 Sisif kernel: [    7.293955] CPU0: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 17:25:50 Sisif kernel: [    7.293973] SMP alternatives: switching to SMP code
Apr 30 17:25:50 Sisif kernel: [    7.294690] Booting processor 1/1 eip 3000
Apr 30 17:25:50 Sisif kernel: [    9.320376] Initializing CPU#1
Apr 30 17:25:50 Sisif kernel: [    9.400259] Calibrating delay using timer specific routine.. 3458.04 BogoMIPS (lpj=6916093)
Apr 30 17:25:50 Sisif kernel: [    9.400266] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 17:25:50 Sisif kernel: [    9.400271] monitor/mwait feature present.
Apr 30 17:25:50 Sisif kernel: [    9.400275] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 17:25:50 Sisif kernel: [    9.400277] CPU: L2 cache: 1024K
Apr 30 17:25:50 Sisif kernel: [    9.400279] CPU: Physical Processor ID: 0
Apr 30 17:25:50 Sisif kernel: [    9.400281] CPU: Processor Core ID: 1
Apr 30 17:25:50 Sisif kernel: [    9.400282] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 17:25:50 Sisif kernel: [    7.387412] CPU1: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 17:25:50 Sisif kernel: [    7.387437] Total of 2 processors activated (6919.90 BogoMIPS).
Apr 30 17:25:50 Sisif kernel: [    7.387635] ENABLING IO-APIC IRQs
Apr 30 17:25:50 Sisif kernel: [    7.387830] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 30 17:25:50 Sisif kernel: [    7.535036] checking TSC synchronization [CPU#0 -> CPU#1]:
Apr 30 17:25:50 Sisif kernel: [    7.555039] Measured 3482432538 cycles TSC warp between CPUs, turning off TSC clock.
Apr 30 17:25:50 Sisif kernel: [    7.555042] Marking TSC unstable due to: check_tsc_sync_source failed.
Apr 30 17:25:50 Sisif kernel: [    7.555058] Brought up 2 CPUs
Apr 30 17:25:50 Sisif kernel: [    7.555085] CPU0 attaching sched-domain:
Apr 30 17:25:50 Sisif kernel: [    7.555088]  domain 0: span 03
Apr 30 17:25:50 Sisif kernel: [    7.555090]   groups: 01 02
Apr 30 17:25:50 Sisif kernel: [    7.555093] CPU1 attaching sched-domain:
Apr 30 17:25:50 Sisif kernel: [    7.555095]  domain 0: span 03
Apr 30 17:25:50 Sisif kernel: [    7.555096]   groups: 02 01
Apr 30 17:25:50 Sisif kernel: [    9.568639] net_namespace: 64 bytes
Apr 30 17:25:50 Sisif kernel: [    9.568649] Booting paravirtualized kernel on bare hardware
Apr 30 17:25:50 Sisif kernel: [    9.569147] Time: 14:25:27  Date: 04/30/08
Apr 30 17:25:50 Sisif kernel: [    9.569176] NET: Registered protocol family 16
Apr 30 17:25:50 Sisif kernel: [    9.569396] EISA bus registered
Apr 30 17:25:50 Sisif kernel: [    9.569400] ACPI: bus type pci registered
Apr 30 17:25:50 Sisif kernel: [    9.598131] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=13
Apr 30 17:25:50 Sisif kernel: [    9.598134] PCI: Using configuration type 1
Apr 30 17:25:50 Sisif kernel: [    9.598136] Setting up standard PCI resources
Apr 30 17:25:50 Sisif kernel: [    7.590598] ACPI: EC: Look up EC in DSDT
Apr 30 17:25:50 Sisif kernel: [    7.595556] ACPI: Interpreter enabled
Apr 30 17:25:50 Sisif kernel: [    7.595560] ACPI: (supports S0 S3 S4 S5)
Apr 30 17:25:50 Sisif kernel: [    7.595573] ACPI: Using IOAPIC for interrupt routing
Apr 30 17:25:50 Sisif kernel: [    7.609631] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 30 17:25:50 Sisif kernel: [    7.610436] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 30 17:25:50 Sisif kernel: [    7.610441] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Apr 30 17:25:50 Sisif kernel: [    7.611610] PCI: Transparent bridge - 0000:00:1e.0
Apr 30 17:25:50 Sisif kernel: [    7.611648] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 30 17:25:50 Sisif kernel: [    7.612110] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr 30 17:25:50 Sisif kernel: [    7.612242] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 30 17:25:50 Sisif kernel: [    7.612363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr 30 17:25:50 Sisif kernel: [    7.620733] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr 30 17:25:50 Sisif kernel: [    7.620844] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
Apr 30 17:25:50 Sisif kernel: [    7.620953] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr 30 17:25:50 Sisif kernel: [    7.621061] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Apr 30 17:25:50 Sisif kernel: [    7.621171] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 30 17:25:50 Sisif kernel: [    7.621282] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 30 17:25:50 Sisif kernel: [    7.621392] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Apr 30 17:25:50 Sisif kernel: [    7.621504] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Apr 30 17:25:50 Sisif kernel: [    7.621658] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 30 17:25:50 Sisif kernel: [    7.621693] pnp: PnP ACPI init
Apr 30 17:25:50 Sisif kernel: [    7.621700] ACPI: bus type pnp registered
Apr 30 17:25:50 Sisif kernel: [    7.637999] pnpacpi: exceeded the max number of mem resources: 12
Apr 30 17:25:50 Sisif kernel: [    7.650867] pnp: PnP ACPI: found 12 devices
Apr 30 17:25:50 Sisif kernel: [    7.650874] ACPI: ACPI bus type pnp unregistered
Apr 30 17:25:50 Sisif kernel: [    7.650879] PnPBIOS: Disabled by ACPI PNP
Apr 30 17:25:50 Sisif kernel: [    9.664430] PCI: Using ACPI for IRQ routing
Apr 30 17:25:50 Sisif kernel: [    9.664434] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 30 17:25:50 Sisif kernel: [    9.728265] NET: Registered protocol family 8
Apr 30 17:25:50 Sisif kernel: [    9.728268] NET: Registered protocol family 20
Apr 30 17:25:50 Sisif kernel: [    9.728305] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 30 17:25:50 Sisif kernel: [    9.728310] hpet0: 3 64-bit timers, 14318180 Hz
Apr 30 17:25:50 Sisif kernel: [    9.729350] AppArmor: AppArmor Filesystem Enabled
Apr 30 17:25:50 Sisif kernel: [    7.718841] Time: hpet clocksource has been installed.
Apr 30 17:25:50 Sisif kernel: [    7.718862] Switched to high resolution mode on CPU 0
Apr 30 17:25:50 Sisif kernel: [    9.732262] Switched to high resolution mode on CPU 1
Apr 30 17:25:50 Sisif kernel: [    7.731842] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731845] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731848] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731851] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731855] system 00:00: iomem range 0x100000-0x7f6d33ff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731858] system 00:00: iomem range 0x7f6d3400-0x7f6fffff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731861] system 00:00: iomem range 0x7f700000-0x7f7fffff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731864] system 00:00: iomem range 0x7f700000-0x7fefffff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731868] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731871] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731874] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731878] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731884] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731887] system 00:02: ioport range 0x1000-0x1005 has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731890] system 00:02: ioport range 0x1008-0x100f has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731897] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731900] system 00:03: ioport range 0x1006-0x1007 has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731903] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731906] system 00:03: ioport range 0x1060-0x107f has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731909] system 00:03: ioport range 0x1080-0x10bf has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731912] system 00:03: ioport range 0x10c0-0x10df has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731915] system 00:03: ioport range 0x1010-0x102f has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731918] system 00:03: ioport range 0x809-0x809 has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731927] system 00:08: ioport range 0xc80-0xcff could not be reserved
Apr 30 17:25:50 Sisif kernel: [    7.731930] system 00:08: ioport range 0x910-0x91f has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731933] system 00:08: ioport range 0x920-0x92f has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731936] system 00:08: ioport range 0xcb0-0xcbf has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731939] system 00:08: ioport range 0x930-0x97f has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.731947] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Apr 30 17:25:50 Sisif kernel: [    7.762417] PCI: Bridge: 0000:00:1c.0
Apr 30 17:25:50 Sisif kernel: [    7.762419]   IO window: disabled.
Apr 30 17:25:50 Sisif kernel: [    7.762426]   MEM window: efd00000-efdfffff
Apr 30 17:25:50 Sisif kernel: [    7.762431]   PREFETCH window: disabled.
Apr 30 17:25:50 Sisif kernel: [    7.762437] PCI: Bridge: 0000:00:1c.3
Apr 30 17:25:50 Sisif kernel: [    7.762440]   IO window: d000-dfff
Apr 30 17:25:50 Sisif kernel: [    7.762446]   MEM window: efa00000-efcfffff
Apr 30 17:25:50 Sisif kernel: [    7.762450]   PREFETCH window: e0000000-e01fffff
Apr 30 17:25:50 Sisif kernel: [    7.762457] PCI: Bridge: 0000:00:1e.0
Apr 30 17:25:50 Sisif kernel: [    7.762459]   IO window: disabled.
Apr 30 17:25:50 Sisif kernel: [    7.762465]   MEM window: ef900000-ef9fffff
Apr 30 17:25:50 Sisif kernel: [    7.762470]   PREFETCH window: disabled.
Apr 30 17:25:50 Sisif kernel: [    7.762503] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:25:50 Sisif kernel: [    7.762512] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 17:25:50 Sisif kernel: [    7.762536] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Apr 30 17:25:50 Sisif kernel: [    7.762543] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 17:25:50 Sisif kernel: [    7.762557] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 30 17:25:50 Sisif kernel: [    7.762570] NET: Registered protocol family 2
Apr 30 17:25:50 Sisif kernel: [    7.806828] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 30 17:25:50 Sisif kernel: [    7.807071] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 30 17:25:50 Sisif kernel: [    7.807816] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 30 17:25:50 Sisif kernel: [    7.808194] TCP: Hash tables configured (established 131072 bind 65536)
Apr 30 17:25:50 Sisif kernel: [    7.808197] TCP reno registered
Apr 30 17:25:50 Sisif kernel: [    7.818932] checking if image is initramfs... it is
Apr 30 17:25:50 Sisif kernel: [    8.511851] Freeing initrd memory: 7267k freed
Apr 30 17:25:50 Sisif kernel: [    8.512024] Simple Boot Flag at 0x79 set to 0x1
Apr 30 17:25:50 Sisif kernel: [   10.526041] audit: initializing netlink socket (disabled)
Apr 30 17:25:50 Sisif kernel: [   10.526056] audit(1209565527.544:1): initialized
Apr 30 17:25:50 Sisif kernel: [    8.513019] highmem bounce pool size: 64 pages
Apr 30 17:25:50 Sisif kernel: [    8.515178] VFS: Disk quotas dquot_6.5.1
Apr 30 17:25:50 Sisif kernel: [    8.515264] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 30 17:25:50 Sisif kernel: [    8.515403] io scheduler noop registered
Apr 30 17:25:50 Sisif kernel: [    8.515405] io scheduler anticipatory registered
Apr 30 17:25:50 Sisif kernel: [    8.515407] io scheduler deadline registered
Apr 30 17:25:50 Sisif kernel: [    8.515419] io scheduler cfq registered (default)
Apr 30 17:25:50 Sisif kernel: [    8.515431] Boot video device is 0000:00:02.0
Apr 30 17:25:50 Sisif kernel: [    8.515647] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 17:25:50 Sisif kernel: [    8.515706] assign_interrupt_mode Found MSI capability
Apr 30 17:25:50 Sisif kernel: [    8.515756] Allocate Port Service[0000:00:1c.0:pcie00]
Apr 30 17:25:50 Sisif kernel: [    8.515796] Allocate Port Service[0000:00:1c.0:pcie02]
Apr 30 17:25:50 Sisif kernel: [    8.515903] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 17:25:50 Sisif kernel: [    8.515961] assign_interrupt_mode Found MSI capability
Apr 30 17:25:50 Sisif kernel: [    8.516008] Allocate Port Service[0000:00:1c.3:pcie00]
Apr 30 17:25:50 Sisif kernel: [    8.516044] Allocate Port Service[0000:00:1c.3:pcie02]
Apr 30 17:25:50 Sisif kernel: [    8.516337] isapnp: Scanning for PnP cards...
Apr 30 17:25:50 Sisif kernel: [    8.870499] isapnp: No Plug & Play device found
Apr 30 17:25:50 Sisif kernel: [    8.900535] Real Time Clock Driver v1.12ac
Apr 30 17:25:50 Sisif kernel: [    8.900700] hpet_resources: 0xfed00000 is busy
Apr 30 17:25:50 Sisif kernel: [    8.900758] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 30 17:25:50 Sisif kernel: [    8.902045] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 30 17:25:50 Sisif kernel: [    8.902118] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 30 17:25:50 Sisif kernel: [    8.902220] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 30 17:25:50 Sisif kernel: [    8.905216] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 30 17:25:50 Sisif kernel: [    8.905222] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 30 17:25:50 Sisif kernel: [    8.930333] mice: PS/2 mouse device common for all mice
Apr 30 17:25:50 Sisif kernel: [    8.930465] EISA: Probing bus 0 at eisa.0
Apr 30 17:25:50 Sisif kernel: [    8.930534] EISA: Mainboard UO_FFFF detected.
Apr 30 17:25:50 Sisif kernel: [    8.930579] Cannot allocate resource for EISA slot 1
Apr 30 17:25:50 Sisif kernel: [    8.930610] EISA: Detected 0 cards.
Apr 30 17:25:50 Sisif kernel: [    8.930613] cpuidle: using governor ladder
Apr 30 17:25:50 Sisif kernel: [    8.930615] cpuidle: using governor menu
Apr 30 17:25:50 Sisif kernel: [    8.930720] NET: Registered protocol family 1
Apr 30 17:25:50 Sisif kernel: [    8.930751] Using IPI No-Shortcut mode
Apr 30 17:25:50 Sisif kernel: [    8.930791] registered taskstats version 1
Apr 30 17:25:50 Sisif kernel: [    8.930909]   Magic number: 4:102:436
Apr 30 17:25:50 Sisif kernel: [    8.931021] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 30 17:25:50 Sisif kernel: [    8.931023] EDD information not available.
Apr 30 17:25:50 Sisif kernel: [    8.931193] Freeing unused kernel memory: 364k freed
Apr 30 17:25:50 Sisif kernel: [   10.946791] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 30 17:25:50 Sisif kernel: [   10.148376] fuse init (API version 7.9)
Apr 30 17:25:50 Sisif kernel: [   10.169777] ACPI: SSDT 7F6D4134, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Apr 30 17:25:50 Sisif kernel: [   10.169969] ACPI: SSDT 7F6D3EE9, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Apr 30 17:25:50 Sisif kernel: [   10.170540] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 17:25:50 Sisif kernel: [   10.170545] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 30 17:25:50 Sisif kernel: [   10.170767] ACPI: SSDT 7F6D4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Apr 30 17:25:50 Sisif kernel: [   10.170939] ACPI: SSDT 7F6D40AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Apr 30 17:25:50 Sisif kernel: [   12.184889] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 17:25:50 Sisif kernel: [   12.184895] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 30 17:25:50 Sisif kernel: [   12.191644] ACPI: Thermal Zone [THM] (47 C)
Apr 30 17:25:50 Sisif kernel: [   12.563876] usbcore: registered new interface driver usbfs
Apr 30 17:25:50 Sisif kernel: [   12.563903] usbcore: registered new interface driver hub
Apr 30 17:25:50 Sisif kernel: [   12.568936] usbcore: registered new device driver usb
Apr 30 17:25:50 Sisif kernel: [   12.575874] USB Universal Host Controller Interface driver v3.0
Apr 30 17:25:50 Sisif kernel: [   12.575951] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 17:25:50 Sisif kernel: [   12.575964] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 30 17:25:50 Sisif kernel: [   12.575969] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 30 17:25:50 Sisif kernel: [   12.576221] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr 30 17:25:50 Sisif kernel: [   12.576260] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
Apr 30 17:25:50 Sisif kernel: [   12.576419] usb usb1: configuration #1 chosen from 1 choice
Apr 30 17:25:50 Sisif kernel: [   12.576444] hub 1-0:1.0: USB hub found
Apr 30 17:25:50 Sisif kernel: [   12.576450] hub 1-0:1.0: 2 ports detected
Apr 30 17:25:50 Sisif kernel: [   12.623546] SCSI subsystem initialized
Apr 30 17:25:50 Sisif kernel: [   12.631946] libata version 3.00 loaded.
Apr 30 17:25:50 Sisif kernel: [   12.679831] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
Apr 30 17:25:50 Sisif kernel: [   12.679847] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 30 17:25:50 Sisif kernel: [   12.679852] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 30 17:25:50 Sisif kernel: [   12.679879] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr 30 17:25:50 Sisif kernel: [   12.679915] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bf60
Apr 30 17:25:50 Sisif kernel: [   12.680040] usb usb2: configuration #1 chosen from 1 choice
Apr 30 17:25:50 Sisif kernel: [   12.680065] hub 2-0:1.0: USB hub found
Apr 30 17:25:50 Sisif kernel: [   12.680071] hub 2-0:1.0: 2 ports detected
Apr 30 17:25:50 Sisif kernel: [   12.783798] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
Apr 30 17:25:50 Sisif kernel: [   12.783811] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 30 17:25:50 Sisif kernel: [   12.783816] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 30 17:25:50 Sisif kernel: [   12.783842] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr 30 17:25:50 Sisif kernel: [   12.783878] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000bf40
Apr 30 17:25:50 Sisif kernel: [   12.784004] usb usb3: configuration #1 chosen from 1 choice
Apr 30 17:25:50 Sisif kernel: [   12.784034] hub 3-0:1.0: USB hub found
Apr 30 17:25:50 Sisif kernel: [   12.784040] hub 3-0:1.0: 2 ports detected
Apr 30 17:25:50 Sisif kernel: [   12.887753] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
Apr 30 17:25:50 Sisif kernel: [   12.887766] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Apr 30 17:25:50 Sisif kernel: [   12.887771] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Apr 30 17:25:50 Sisif kernel: [   12.887797] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Apr 30 17:25:50 Sisif kernel: [   12.887833] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000bf20
Apr 30 17:25:50 Sisif kernel: [   12.887957] usb usb4: configuration #1 chosen from 1 choice
Apr 30 17:25:50 Sisif kernel: [   12.887982] hub 4-0:1.0: USB hub found
Apr 30 17:25:50 Sisif kernel: [   12.887988] hub 4-0:1.0: 2 ports detected
Apr 30 17:25:50 Sisif kernel: [   10.978508] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:25:50 Sisif kernel: [   10.978531] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 17:25:50 Sisif kernel: [   13.055679] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Apr 30 17:25:50 Sisif kernel: [   11.042462] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 17:25:50 Sisif kernel: [   11.042478] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 30 17:25:50 Sisif kernel: [   11.042482] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 30 17:25:50 Sisif kernel: [   11.042515] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Apr 30 17:25:50 Sisif kernel: [   11.046419] ehci_hcd 0000:00:1d.7: debug port 1
Apr 30 17:25:50 Sisif kernel: [   11.046427] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr 30 17:25:50 Sisif kernel: [   11.046434] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80000
Apr 30 17:25:50 Sisif kernel: [   11.065240] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 30 17:25:50 Sisif kernel: [   11.065364] usb usb5: configuration #1 chosen from 1 choice
Apr 30 17:25:50 Sisif kernel: [   11.065391] hub 5-0:1.0: USB hub found
Apr 30 17:25:50 Sisif kernel: [   11.065397] hub 5-0:1.0: 8 ports detected
Apr 30 17:25:50 Sisif kernel: [   11.169576] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Apr 30 17:25:50 Sisif kernel: [   11.222977] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 30 17:25:50 Sisif kernel: [   11.227060] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 17:25:50 Sisif kernel: [   11.227103] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 17:25:50 Sisif kernel: [   11.227116] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Apr 30 17:25:50 Sisif kernel: [   11.230629] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 17:25:50 Sisif kernel: [   13.306504] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 17:25:50 Sisif kernel: [   13.306541] b44.c:v2.0
Apr 30 17:25:50 Sisif kernel: [   13.306669] ata_piix 0000:00:1f.2: version 2.12
Apr 30 17:25:50 Sisif kernel: [   13.306676] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Apr 30 17:25:50 Sisif kernel: [   13.306699] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 17:25:50 Sisif kernel: [   13.306740] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 17:25:50 Sisif kernel: [   13.307004] scsi0 : ata_piix
Apr 30 17:25:50 Sisif kernel: [   13.307060] scsi1 : ata_piix
Apr 30 17:25:50 Sisif kernel: [   13.307879] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Apr 30 17:25:50 Sisif kernel: [   13.307883] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Apr 30 17:25:50 Sisif kernel: [   13.327781] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 17:25:50 Sisif kernel: [   11.460222] ata1.00: ATA-7: ST9120822AS, 3.CDD, max UDMA/133
Apr 30 17:25:50 Sisif kernel: [   11.460227] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
Apr 30 17:25:50 Sisif kernel: [   11.475032] ata1.00: configured for UDMA/133
Apr 30 17:25:50 Sisif kernel: [   13.830699] ata2.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1B, max UDMA/33
Apr 30 17:25:50 Sisif kernel: [   14.026531] ata2.00: configured for UDMA/33
Apr 30 17:25:50 Sisif kernel: [   12.013444] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.CD PQ: 0 ANSI: 5
Apr 30 17:25:50 Sisif kernel: [   12.015731] scsi 1:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
Apr 30 17:25:50 Sisif kernel: [   12.023410] Driver 'sd' needs updating - please use bus_type methods
Apr 30 17:25:50 Sisif kernel: [   12.023497] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 17:25:50 Sisif kernel: [   12.023511] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 17:25:50 Sisif kernel: [   12.023514] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 17:25:50 Sisif kernel: [   12.023531] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 17:25:50 Sisif kernel: [   12.023581] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 17:25:50 Sisif kernel: [   12.023592] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 17:25:50 Sisif kernel: [   12.023594] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 17:25:50 Sisif kernel: [   12.023611] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 17:25:50 Sisif kernel: [   12.023615]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Apr 30 17:25:50 Sisif kernel: [   12.113725]  sda1 sda2 sda3
Apr 30 17:25:50 Sisif kernel: [   12.126011] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 30 17:25:50 Sisif kernel: [   12.131612] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 30 17:25:50 Sisif kernel: [   12.131633] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 30 17:25:50 Sisif kernel: [   14.156865] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr 30 17:25:50 Sisif kernel: [   14.156871] Uniform CD-ROM driver Revision: 3.20
Apr 30 17:25:50 Sisif kernel: [   14.156925] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 30 17:25:50 Sisif kernel: [   14.510215] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc00026e60070]
Apr 30 17:25:50 Sisif kernel: [   12.637401] Attempting manual resume
Apr 30 17:25:50 Sisif kernel: [   12.637405] swsusp: Resume From Partition 8:2
Apr 30 17:25:50 Sisif kernel: [   12.637407] PM: Checking swsusp image.
Apr 30 17:25:50 Sisif kernel: [   12.637596] PM: Resume from disk failed.
Apr 30 17:25:50 Sisif kernel: [   14.692687] kjournald starting.  Commit interval 5 seconds
Apr 30 17:25:50 Sisif kernel: [   12.679430] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 17:25:50 Sisif kernel: [   23.523059] input: PC Speaker as /devices/platform/pcspkr/input/input2
Apr 30 17:25:50 Sisif kernel: [   21.682064] iTCO_vendor_support: vendor-support=0
Apr 30 17:25:50 Sisif kernel: [   21.718116] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Apr 30 17:25:50 Sisif kernel: [   21.836153] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 30 17:25:50 Sisif kernel: [   21.880154] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 30 17:25:50 Sisif kernel: [   21.936079] Linux agpgart interface v0.102
Apr 30 17:25:50 Sisif kernel: [   21.976111] agpgart: Detected an Intel 945GM Chipset.
Apr 30 17:25:50 Sisif kernel: [   21.976696] agpgart: Detected 7932K stolen memory.
Apr 30 17:25:50 Sisif kernel: [   21.993953] agpgart: AGP aperture is 256M @ 0xd0000000
Apr 30 17:25:50 Sisif kernel: [   22.114698] ACPI: AC Adapter [AC] (on-line)
Apr 30 17:25:50 Sisif kernel: [   24.150164] input: Lid Switch as /devices/virtual/input/input3
Apr 30 17:25:50 Sisif kernel: [   24.167413] ACPI: Lid Switch [LID]
Apr 30 17:25:50 Sisif kernel: [   24.167477] input: Power Button (CM) as /devices/virtual/input/input4
Apr 30 17:25:50 Sisif kernel: [   24.230225] ACPI: Power Button (CM) [PBTN]
Apr 30 17:25:50 Sisif kernel: [   24.230291] input: Sleep Button (CM) as /devices/virtual/input/input5
Apr 30 17:25:50 Sisif kernel: [   22.267417] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
Apr 30 17:25:50 Sisif kernel: [   24.294192] ACPI: Sleep Button (CM) [SBTN]
Apr 30 17:25:50 Sisif kernel: [   22.318829] ACPI: Battery Slot [BAT0] (battery present)
Apr 30 17:25:50 Sisif kernel: [   22.326499] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
Apr 30 17:25:50 Sisif kernel: [   22.366524] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Apr 30 17:25:50 Sisif kernel: [   22.366565] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 30 17:25:50 Sisif kernel: [   22.366605] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Apr 30 17:25:50 Sisif kernel: [   22.607867] ACPI: WMI-Acer: Mapper loaded
Apr 30 17:25:50 Sisif kernel: [   22.748158] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input7
Apr 30 17:25:50 Sisif kernel: [   22.802610] intel_rng: FWH not detected
Apr 30 17:25:50 Sisif kernel: [   22.806488] sdhci: Secure Digital Host Controller Interface driver
Apr 30 17:25:50 Sisif kernel: [   22.806492] sdhci: Copyright(c) Pierre Ossman
Apr 30 17:25:50 Sisif kernel: [   22.806541] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
Apr 30 17:25:50 Sisif kernel: [   22.806570] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
Apr 30 17:25:50 Sisif kernel: [   22.806646] mmc0: SDHCI at 0xef9fd500 irq 23 DMA
Apr 30 17:25:50 Sisif kernel: [   22.813058] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr 30 17:25:50 Sisif kernel: [   22.821009] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input8
Apr 30 17:25:50 Sisif kernel: [   22.871636] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Apr 30 17:25:50 Sisif kernel: [   22.871793] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input9
Apr 30 17:25:50 Sisif kernel: [   22.935603] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Apr 30 17:25:50 Sisif kernel: [   25.728871] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
Apr 30 17:25:50 Sisif kernel: [   25.728895] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 30 17:25:50 Sisif kernel: [   25.743328] b43-phy0: Broadcom 4311 WLAN found
Apr 30 17:25:50 Sisif kernel: [   25.842341] phy0: Selected rate control algorithm 'simple'
Apr 30 17:25:50 Sisif kernel: [   24.423955] udev: renamed network interface wlan0 to eth1
Apr 30 17:25:50 Sisif kernel: [   26.492335] input: b43-phy0 as /devices/virtual/input/input10
Apr 30 17:25:50 Sisif kernel: [   26.799954] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x00171700
Apr 30 17:25:50 Sisif kernel: [   27.216784] lp: driver loaded but no devices found
Apr 30 17:25:50 Sisif kernel: [   27.379456] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
Apr 30 17:25:50 Sisif kernel: [   25.950706] EXT3 FS on sda1, internal journal
Apr 30 17:25:50 Sisif kernel: [   28.391710] Registered led device: b43-phy0:tx
Apr 30 17:25:50 Sisif kernel: [   28.391738] Registered led device: b43-phy0:rx
Apr 30 17:25:50 Sisif kernel: [   28.391764] Registered led device: b43-phy0:radio
Apr 30 17:25:50 Sisif kernel: [   26.475825] NET: Registered protocol family 17
Apr 30 17:25:50 Sisif kernel: [   28.951613] kjournald starting.  Commit interval 5 seconds
Apr 30 17:25:50 Sisif kernel: [   26.938590] EXT3 FS on sda3, internal journal
Apr 30 17:25:50 Sisif kernel: [   26.938595] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 17:25:50 Sisif kernel: [   27.597072] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 17:25:50 Sisif kernel: [   28.940522] RPC: Registered udp transport module.
Apr 30 17:25:50 Sisif kernel: [   28.940526] RPC: Registered tcp transport module.
Apr 30 17:25:50 Sisif kernel: [   29.697383] No dock devices found.
Apr 30 17:25:51 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr 30 17:25:51 Sisif avahi-daemon[5284]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Apr 30 17:25:51 Sisif avahi-daemon[5284]: Successfully dropped root privileges.
Apr 30 17:25:51 Sisif avahi-daemon[5284]: avahi-daemon 0.6.22 starting up.
Apr 30 17:25:51 Sisif avahi-daemon[5284]: Successfully called chroot().
Apr 30 17:25:51 Sisif avahi-daemon[5284]: Successfully dropped remaining capabilities.
Apr 30 17:25:51 Sisif avahi-daemon[5284]: No service file found in /etc/avahi/services.
Apr 30 17:25:51 Sisif avahi-daemon[5284]: Network interface enumeration completed.
Apr 30 17:25:51 Sisif avahi-daemon[5284]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 30 17:25:51 Sisif avahi-daemon[5284]: Server startup complete. Host name is Sisif.local. Local service cookie is 2248606097.
Apr 30 17:25:52 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:25:52 Sisif kernel: [   32.164810] ppdev: user-space parallel port driver
Apr 30 17:25:52 Sisif kernel: [   32.344147] audit(1209565552.270:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5318 profile="/usr/sbin/cupsd" namespace="default"
Apr 30 17:25:52 Sisif kernel: [   32.392462] apm: BIOS not found.
Apr 30 17:25:53 Sisif kernel: [   33.854863] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Apr 30 17:25:53 Sisif exportfs[5491]: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.10.2:/home/itch/Blonda".   Assuming default behaviour ('no_subtree_check').   NOTE: this default has changed since nfs-utils version 1.0.x 
Apr 30 17:25:54 Sisif dhclient: DHCPREQUEST of 192.168.0.118 on eth0 to 255.255.255.255 port 67
Apr 30 17:25:54 Sisif kernel: [   34.112750] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Apr 30 17:25:54 Sisif kernel: [   34.128580] NFSD: starting 90-second grace period
Apr 30 17:25:55 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr 30 17:25:55 Sisif nmbd[5561]: [2008/04/30 17:25:55, 0] nmbd/nmbd_subnetdb.c:create_subnets(190) 
Apr 30 17:25:55 Sisif nmbd[5561]:   create_subnets: No local interfaces ! 
Apr 30 17:25:55 Sisif nmbd[5561]: [2008/04/30 17:25:55, 0] nmbd/nmbd_subnetdb.c:create_subnets(191) 
Apr 30 17:25:55 Sisif nmbd[5561]:   create_subnets: Waiting for an interface to appear ... 
Apr 30 17:25:56 Sisif dhcdbd: Started up.
Apr 30 17:25:56 Sisif hcid[5638]: Bluetooth HCI daemon
Apr 30 17:25:57 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:25:57 Sisif kernel: [   37.129990] Bluetooth: Core ver 2.11
Apr 30 17:25:57 Sisif kernel: [   39.144008] NET: Registered protocol family 31
Apr 30 17:25:57 Sisif kernel: [   39.144017] Bluetooth: HCI device and connection manager initialized
Apr 30 17:25:57 Sisif kernel: [   39.144025] Bluetooth: HCI socket layer initialized
Apr 30 17:25:57 Sisif hcid[5638]: Starting SDP server
Apr 30 17:25:57 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:25:57 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:25:57 Sisif kernel: [   37.300790] Bluetooth: L2CAP ver 2.9
Apr 30 17:25:57 Sisif kernel: [   37.300798] Bluetooth: L2CAP socket layer initialized
Apr 30 17:25:57 Sisif hcid[5638]: Created local server at unix:abstract=/var/run/dbus-zyacrWOg7a,guid=ab1df83166d1c38c6074f8a348188175
Apr 30 17:25:57 Sisif kernel: [   37.403375] Bluetooth: RFCOMM socket layer initialized
Apr 30 17:25:57 Sisif kernel: [   37.403395] Bluetooth: RFCOMM TTY layer initialized
Apr 30 17:25:57 Sisif kernel: [   37.403399] Bluetooth: RFCOMM ver 1.8
Apr 30 17:25:57 Sisif audio[5660]: Bluetooth Audio daemon
Apr 30 17:25:57 Sisif input[5677]: Bluetooth Input daemon
Apr 30 17:25:57 Sisif audio[5660]: Unix socket created: 5
Apr 30 17:25:57 Sisif audio[5660]: audio.conf: Key file does not have key 'Enable'
Apr 30 17:25:57 Sisif audio[5660]: audio.conf: Key file does not have key 'Disable'
Apr 30 17:25:57 Sisif input[5677]: Registered input manager path:/org/bluez/input
Apr 30 17:25:57 Sisif audio[5660]: add_service_record: got record id 0x10000
Apr 30 17:25:57 Sisif audio[5660]: audio.conf: Key file does not have key 'Disable'
Apr 30 17:25:57 Sisif audio[5660]: audio.conf: Key file does not have group 'A2DP'
Apr 30 17:25:57 Sisif last message repeated 3 times
Apr 30 17:25:57 Sisif audio[5660]: SEP 0x806d578 registered: type:0 codec:0 seid:1
Apr 30 17:25:57 Sisif audio[5660]: add_service_record: got record id 0x10001
Apr 30 17:25:57 Sisif audio[5660]: add_service_record: got record id 0x10002
Apr 30 17:25:57 Sisif audio[5660]: add_service_record: got record id 0x10003
Apr 30 17:25:57 Sisif audio[5660]: Registered manager path:/org/bluez/audio
Apr 30 17:25:59 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 30 17:25:59 Sisif ntpd[5733]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 17:25:59 Sisif ntpd[5734]: precision = 1.000 usec
Apr 30 17:25:59 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:00 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr 30 17:26:00 Sisif kernel: [   40.127339] NET: Registered protocol family 10
Apr 30 17:26:00 Sisif kernel: [   40.127886] lo: Disabled Privacy Extensions
Apr 30 17:26:00 Sisif kernel: [   40.131279] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 30 17:26:00 Sisif kernel: [   40.133243] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:26:00 Sisif ntpd[5734]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 17:26:00 Sisif ntpd[5734]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 17:26:00 Sisif ntpd[5734]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 17:26:00 Sisif ntpd[5734]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 17:26:00 Sisif ntpd[5734]: kernel time sync status 0040
Apr 30 17:26:00 Sisif ntpd[5734]: frequency initialized -57.973 PPM from /var/lib/ntp/ntp.drift
Apr 30 17:26:00 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:00 Sisif last message repeated 7 times
Apr 30 17:26:00 Sisif kernel: [   41.061287] [drm] Initialized drm 1.1.0 20060810
Apr 30 17:26:01 Sisif kernel: [   41.089115] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:26:01 Sisif kernel: [   41.089129] PCI: Setting latency timer of device 0000:00:02.0 to 64
Apr 30 17:26:01 Sisif kernel: [   41.089328] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr 30 17:26:01 Sisif anacron[5806]: Anacron 2.3 started on 2008-04-30
Apr 30 17:26:01 Sisif anacron[5806]: Normal exit (0 jobs run)
Apr 30 17:26:01 Sisif /usr/sbin/cron[5833]: (CRON) INFO (pidfile fd = 3)
Apr 30 17:26:01 Sisif /usr/sbin/cron[5834]: (CRON) STARTUP (fork ok)
Apr 30 17:26:01 Sisif /usr/sbin/cron[5834]: (CRON) INFO (Running @reboot jobs)
Apr 30 17:26:02 Sisif ntpd_initres[5752]: host name not found: ntp2a.mcc.ac.uk
Apr 30 17:26:02 Sisif ntpd_initres[5752]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 17:26:02 Sisif ntpd_initres[5752]: host name not found: ntp.landau.ac.ru
Apr 30 17:26:02 Sisif ntpd_initres[5752]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 17:26:02 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 17:26:03 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 30 17:26:03 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:03 Sisif dhclient: receive_packet failed on eth0: Network is down
Apr 30 17:26:03 Sisif kernel: [   45.168510] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 17:26:03 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:03 Sisif kernel: [   45.176553] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 17:26:03 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:03 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 17:26:03 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:26:03 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:26:03 Sisif dhclient: All rights reserved.
Apr 30 17:26:03 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:26:03 Sisif dhclient: 
Apr 30 17:26:03 Sisif kernel: [   43.267695] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 17:26:03 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:03 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:03 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:26:03 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:03 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:03 Sisif kernel: [   43.420305] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 17:26:03 Sisif kernel: [   43.420598] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:26:03 Sisif kernel: [   43.420665] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 17:26:03 Sisif kernel: [   43.425571] ndiswrapper: using IRQ 16
Apr 30 17:26:03 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:03 Sisif last message repeated 7 times
Apr 30 17:26:03 Sisif kernel: [   43.820337] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 17:26:03 Sisif kernel: [   43.820432] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 17:26:03 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:03 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:03 Sisif kernel: [   43.870051] usbcore: registered new interface driver ndiswrapper
Apr 30 17:26:03 Sisif kernel: [   43.872192] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 17:26:03 Sisif kernel: [   43.872263] udev: renamed network interface wlan0 to eth1
Apr 30 17:26:03 Sisif kernel: [   43.882444] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:26:03 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 17:26:03 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:26:03 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:26:03 Sisif dhclient: All rights reserved.
Apr 30 17:26:03 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:26:03 Sisif dhclient: 
Apr 30 17:26:03 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:03 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:03 Sisif kernel: [   46.059258] ndiswrapper: device eth1 removed
Apr 30 17:26:03 Sisif kernel: [   46.059285] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 17:26:03 Sisif kernel: [   46.059397] usbcore: deregistering interface driver ndiswrapper
Apr 30 17:26:04 Sisif kernel: [   46.089408] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 17:26:04 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:04 Sisif last message repeated 2 times
Apr 30 17:26:04 Sisif kernel: [   44.138158] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 17:26:04 Sisif kernel: [   46.151760] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:26:04 Sisif kernel: [   46.151843] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 17:26:04 Sisif kernel: [   46.156837] ndiswrapper: using IRQ 16
Apr 30 17:26:04 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:26:04 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:26:04 Sisif dhclient: All rights reserved.
Apr 30 17:26:04 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:26:04 Sisif dhclient: 
Apr 30 17:26:04 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:04 Sisif kernel: [   46.512842] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 17:26:04 Sisif kernel: [   46.515033] eth1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 17:26:04 Sisif kernel: [   44.502491] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 17:26:04 Sisif kernel: [   44.502615] udev: renamed network interface wlan0 to eth1
Apr 30 17:26:04 Sisif kernel: [   44.503460] ndiswrapper (wrap_procfs_add_ndis_device:399): eth1 already registered?
Apr 30 17:26:04 Sisif kernel: [   44.507480] usbcore: registered new interface driver ndiswrapper
Apr 30 17:26:04 Sisif kernel: [   46.567360] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:26:04 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:26:04 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:26:04 Sisif dhclient: Sending on   Socket/fallback
Apr 30 17:26:04 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr 30 17:26:05 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:26:05 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:26:05 Sisif dhclient: Sending on   Socket/fallback
Apr 30 17:26:08 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr 30 17:26:08 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 17:26:11 Sisif kernel: [   51.694645] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 30 17:26:13 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr 30 17:26:13 Sisif avahi-daemon[5284]: Registering new address record for fe80::219:7eff:fea0:3d2a on eth1.*.
Apr 30 17:26:15 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 17:26:22 Sisif kernel: [   62.357881] eth1: no IPv6 routers present
Apr 30 17:26:23 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr 30 17:26:23 Sisif hcid[5638]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Apr 30 17:26:23 Sisif hcid[5638]: Default authorization agent (:1.18, /org/bluez/auth) registered
Apr 30 17:26:30 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr 30 17:26:33 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:33 Sisif last message repeated 8 times
Apr 30 17:26:33 Sisif kernel: [   73.805160] CPU0 attaching NULL sched-domain.
Apr 30 17:26:33 Sisif kernel: [   73.805168] CPU1 attaching NULL sched-domain.
Apr 30 17:26:33 Sisif kernel: [   73.837084] CPU0 attaching sched-domain:
Apr 30 17:26:33 Sisif kernel: [   73.837090]  domain 0: span 03
Apr 30 17:26:33 Sisif kernel: [   73.837092]   groups: 01 02
Apr 30 17:26:33 Sisif kernel: [   73.837095] CPU1 attaching sched-domain:
Apr 30 17:26:33 Sisif kernel: [   73.837097]  domain 0: span 03
Apr 30 17:26:33 Sisif kernel: [   73.837099]   groups: 02 01
Apr 30 17:26:35 Sisif dhclient: No DHCPOFFERS received.
Apr 30 17:26:35 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 17:26:35 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr 30 17:26:35 Sisif avahi-autoipd(eth1)[6614]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 30 17:26:35 Sisif avahi-autoipd(eth1)[6614]: Successfully called chroot().
Apr 30 17:26:35 Sisif avahi-autoipd(eth1)[6614]: Successfully dropped root privileges.
Apr 30 17:26:35 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:35 Sisif last message repeated 8 times
Apr 30 17:26:35 Sisif avahi-autoipd(eth1)[6614]: Starting with address 169.254.4.188
Apr 30 17:26:38 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:41 Sisif last message repeated 17 times
Apr 30 17:26:42 Sisif avahi-autoipd(eth1)[6614]: Callout BIND, address 169.254.4.188 on interface eth1
Apr 30 17:26:42 Sisif avahi-daemon[5284]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 17:26:42 Sisif avahi-daemon[5284]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 17:26:42 Sisif avahi-daemon[5284]: Registering new address record for 169.254.4.188 on eth1.IPv4.
Apr 30 17:26:44 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr 30 17:26:44 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:44 Sisif last message repeated 8 times
Apr 30 17:26:46 Sisif avahi-autoipd(eth1)[6614]: Successfully claimed IP address 169.254.4.188
Apr 30 17:26:46 Sisif ntpd[5734]: ntpd exiting on signal 15
Apr 30 17:26:47 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:56 Sisif last message repeated 35 times
Apr 30 17:26:57 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr 30 17:26:59 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:26:59 Sisif last message repeated 8 times
Apr 30 17:27:01 Sisif dhclient: No DHCPOFFERS received.
Apr 30 17:27:01 Sisif dhclient: Trying recorded lease 192.168.1.102
Apr 30 17:27:01 Sisif avahi-autoipd(eth1)[6614]: A routable address has been configured.
Apr 30 17:27:01 Sisif avahi-autoipd(eth1)[6614]: Callout UNBIND, address 169.254.4.188 on interface eth1
Apr 30 17:27:01 Sisif avahi-daemon[5284]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 17:27:01 Sisif avahi-daemon[5284]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 17:27:01 Sisif avahi-daemon[5284]: Registering new address record for 192.168.1.102 on eth1.IPv4.
Apr 30 17:27:01 Sisif avahi-daemon[5284]: Withdrawing address record for 169.254.4.188 on eth1.
Apr 30 17:27:01 Sisif ntpdate[6952]: can't find host ntp2a.mcc.ac.uk 
Apr 30 17:27:02 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:02 Sisif last message repeated 8 times
Apr 30 17:27:04 Sisif avahi-autoipd(eth1)[6614]: No longer a routable address configured, restarting probe process.
Apr 30 17:27:04 Sisif avahi-daemon[5284]: Withdrawing address record for 192.168.1.102 on eth1.
Apr 30 17:27:04 Sisif avahi-daemon[5284]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 17:27:04 Sisif avahi-daemon[5284]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 17:27:04 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 17:27:05 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:05 Sisif last message repeated 8 times
Apr 30 17:27:05 Sisif avahi-daemon[5284]: Withdrawing address record for fe80::219:7eff:fea0:3d2a on eth1.
Apr 30 17:27:05 Sisif avahi-autoipd(eth1)[6614]: SIOCSIFFLAGS failed: Permission denied
Apr 30 17:27:05 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 17:27:05 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 17:27:06 Sisif ntpdate[6952]: can't find host ntp.landau.ac.ru 
Apr 30 17:27:06 Sisif ntpdate[6952]: no servers can be used, exiting
Apr 30 17:27:06 Sisif ntpd[7408]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 17:27:06 Sisif ntpd[7409]: precision = 1.000 usec
Apr 30 17:27:06 Sisif ntpd[7409]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 17:27:06 Sisif ntpd[7409]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 17:27:06 Sisif ntpd[7409]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 17:27:06 Sisif ntpd[7409]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 17:27:06 Sisif ntpd[7409]: kernel time sync status 0040
Apr 30 17:27:06 Sisif ntpd[7409]: frequency initialized -57.973 PPM from /var/lib/ntp/ntp.drift
Apr 30 17:27:08 Sisif ntpd_initres[7410]: host name not found: ntp2a.mcc.ac.uk
Apr 30 17:27:08 Sisif ntpd_initres[7410]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 17:27:08 Sisif ntpd_initres[7410]: host name not found: ntp.landau.ac.ru
Apr 30 17:27:08 Sisif ntpd_initres[7410]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 17:27:08 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:08 Sisif last message repeated 6 times
Apr 30 17:27:08 Sisif dhclient: There is already a pid file /var/run/dhclient.pid with pid 7335
Apr 30 17:27:08 Sisif dhclient: removed stale PID file
Apr 30 17:27:08 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:27:08 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:27:08 Sisif dhclient: All rights reserved.
Apr 30 17:27:08 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:27:08 Sisif dhclient: 
Apr 30 17:27:08 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:08 Sisif last message repeated 4 times
Apr 30 17:27:09 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:27:09 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:27:09 Sisif dhclient: Sending on   Socket/fallback
Apr 30 17:27:09 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 17:27:09 Sisif avahi-daemon[5284]: Registering new address record for fe80::219:7eff:fea0:3d2a on eth1.*.
Apr 30 17:27:11 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:11 Sisif last message repeated 8 times
Apr 30 17:27:14 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 17:27:14 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:18 Sisif last message repeated 25 times
Apr 30 17:27:18 Sisif kernel: [  120.947359] eth1: no IPv6 routers present
Apr 30 17:27:19 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 17:27:20 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:26 Sisif last message repeated 26 times
Apr 30 17:27:29 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 30 17:27:29 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:29 Sisif last message repeated 8 times
Apr 30 17:27:32 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr 30 17:27:32 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:35 Sisif last message repeated 17 times
Apr 30 17:27:37 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr 30 17:27:37 Sisif avahi-daemon[5284]: Withdrawing address record for fe80::219:7eff:fea0:3d2a on eth1.
Apr 30 17:27:37 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:48 Sisif last message repeated 68 times
Apr 30 17:27:48 Sisif kernel: [  148.092496] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:27:48 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:48 Sisif dhclient: There is already a pid file /var/run/dhclient.pid with pid 134519072
Apr 30 17:27:48 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:27:48 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:27:48 Sisif dhclient: All rights reserved.
Apr 30 17:27:48 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:27:48 Sisif dhclient: 
Apr 30 17:27:49 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:27:49 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:27:49 Sisif dhclient: Sending on   Socket/fallback
Apr 30 17:27:50 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:50 Sisif last message repeated 8 times
Apr 30 17:27:51 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 17:27:53 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:53 Sisif last message repeated 8 times
Apr 30 17:27:56 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 17:27:56 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:27:59 Sisif last message repeated 17 times
Apr 30 17:27:59 Sisif nmbd[5561]: [2008/04/30 17:27:59, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:27:59 Sisif nmbd[5561]:   Packet send failed to 169.254.255.255(138) ERRNO=Invalid argument 
Apr 30 17:28:02 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:28:08 Sisif last message repeated 26 times
Apr 30 17:28:10 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr 30 17:28:11 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:28:35 Sisif last message repeated 139 times
Apr 30 17:28:36 Sisif kernel: [  196.063020] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:28:36 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:28:36 Sisif dhclient: There is already a pid file /var/run/dhclient.pid with pid 134519072
Apr 30 17:28:36 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:28:36 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:28:36 Sisif dhclient: All rights reserved.
Apr 30 17:28:36 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:28:36 Sisif dhclient: 
Apr 30 17:28:37 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:28:37 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:28:37 Sisif dhclient: Sending on   Socket/fallback
Apr 30 17:28:38 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 17:28:38 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:28:44 Sisif last message repeated 26 times
Apr 30 17:28:45 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 17:28:47 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:28:53 Sisif last message repeated 26 times
Apr 30 17:28:55 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr 30 17:28:56 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:28:56 Sisif last message repeated 8 times
Apr 30 17:28:59 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr 30 17:28:59 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:28:59 Sisif last message repeated 8 times
Apr 30 17:28:59 Sisif nmbd[5561]: [2008/04/30 17:28:59, 0] nmbd/nmbd.c:reload_interfaces(239) 
Apr 30 17:28:59 Sisif nmbd[5561]:   reload_interfaces: No subnets to listen to. Waiting.. 
Apr 30 17:29:02 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:29:08 Sisif last message repeated 26 times
Apr 30 17:29:09 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 17:29:09 Sisif kernel: [  231.246501] ndiswrapper: device eth1 removed
Apr 30 17:29:09 Sisif kernel: [  231.246534] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 17:29:09 Sisif kernel: [  231.246655] usbcore: deregistering interface driver ndiswrapper
Apr 30 17:29:09 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:29:09 Sisif last message repeated 5 times
Apr 30 17:29:10 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Apr 30 17:29:10 Sisif dhclient: send_packet: No such device
Apr 30 17:29:10 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:29:25 Sisif last message repeated 200 times
Apr 30 17:29:26 Sisif dhclient: No DHCPOFFERS received.
Apr 30 17:29:26 Sisif dhclient: Trying recorded lease 192.168.1.102
Apr 30 17:29:26 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:29:26 Sisif last message repeated 12 times
Apr 30 17:29:26 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 17:29:26 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:29:57 Sisif last message repeated 312 times
Apr 30 17:30:58 Sisif last message repeated 603 times
Apr 30 17:31:48 Sisif last message repeated 531 times
Apr 30 17:31:48 Sisif dhclient: There is already a pid file /var/run/dhclient.pid with pid 12069
Apr 30 17:31:48 Sisif dhclient: removed stale PID file
Apr 30 17:31:48 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:31:48 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:31:48 Sisif dhclient: All rights reserved.
Apr 30 17:31:48 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:31:48 Sisif dhclient: 
Apr 30 17:31:48 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:31:50 Sisif last message repeated 15 times
Apr 30 17:31:50 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:31:50 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:31:59 Sisif last message repeated 120 times
Apr 30 17:31:59 Sisif dhclient: There is already a pid file /var/run/dhclient.pid with pid 134519072
Apr 30 17:31:59 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:31:59 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:31:59 Sisif dhclient: All rights reserved.
Apr 30 17:31:59 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:31:59 Sisif dhclient: 
Apr 30 17:31:59 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:32:01 Sisif last message repeated 18 times
Apr 30 17:32:01 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:32:01 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:32:10 Sisif last message repeated 124 times
Apr 30 17:32:10 Sisif dhclient: There is already a pid file /var/run/dhclient.pid with pid 134519072
Apr 30 17:32:10 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:32:10 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:32:10 Sisif dhclient: All rights reserved.
Apr 30 17:32:10 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:32:10 Sisif dhclient: 
Apr 30 17:32:10 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:32:12 Sisif last message repeated 22 times
Apr 30 17:32:12 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:32:12 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:32:21 Sisif last message repeated 120 times
Apr 30 17:32:21 Sisif dhclient: There is already a pid file /var/run/dhclient.pid with pid 134519072
Apr 30 17:32:21 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:32:21 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:32:21 Sisif dhclient: All rights reserved.
Apr 30 17:32:21 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:32:21 Sisif dhclient: 
Apr 30 17:32:21 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:32:22 Sisif last message repeated 18 times
Apr 30 17:32:22 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:32:22 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:32:31 Sisif last message repeated 97 times
Apr 30 17:32:31 Sisif dhclient: There is already a pid file /var/run/dhclient.pid with pid 134519072
Apr 30 17:32:31 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:32:31 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:32:31 Sisif dhclient: All rights reserved.
Apr 30 17:32:31 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:32:31 Sisif dhclient: 
Apr 30 17:32:31 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:32:32 Sisif last message repeated 18 times
Apr 30 17:32:32 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:32:32 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:33:03 Sisif last message repeated 289 times
Apr 30 17:34:04 Sisif last message repeated 573 times
Apr 30 17:35:05 Sisif last message repeated 377 times
Apr 30 17:35:47 Sisif last message repeated 161 times
Apr 30 17:35:49 Sisif kernel: [  629.547847] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 17:35:49 Sisif kernel: [  629.607065] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 17:35:49 Sisif kernel: [  629.607100] b44.c:v2.0
Apr 30 17:35:49 Sisif kernel: [  629.632638] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 17:35:49 Sisif kernel: [  629.710634] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 30 17:35:49 Sisif dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Apr 30 17:35:49 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:35:49 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:35:49 Sisif dhclient: All rights reserved.
Apr 30 17:35:49 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:35:49 Sisif dhclient: 
Apr 30 17:35:50 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:35:50 Sisif dhclient: Listening on LPF/eth0/00:19:b9:85:80:f6
Apr 30 17:35:50 Sisif dhclient: Sending on   LPF/eth0/00:19:b9:85:80:f6
Apr 30 17:35:50 Sisif dhclient: Sending on   Socket/fallback
Apr 30 17:35:53 Sisif dhclient: DHCPREQUEST of 192.168.0.118 on eth0 to 255.255.255.255 port 67
Apr 30 17:35:53 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:35:59 Sisif last message repeated 6 times
Apr 30 17:36:00 Sisif dhclient: DHCPREQUEST of 192.168.0.118 on eth0 to 255.255.255.255 port 67
Apr 30 17:36:02 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:36:11 Sisif last message repeated 3 times
Apr 30 17:36:12 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 30 17:36:14 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:36:17 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr 30 17:36:17 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:36:20 Sisif modprobe: WARNING: /etc/modprobe.d/blacklist line 28: ignoring bad line starting with 'ndiswrapper' 
Apr 30 17:36:31 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr 30 17:36:43 Sisif dhclient: No DHCPOFFERS received.
Apr 30 17:36:43 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 17:36:43 Sisif avahi-daemon[5284]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 17:36:43 Sisif avahi-daemon[5284]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 17:36:43 Sisif avahi-daemon[5284]: Registering new address record for 192.168.0.118 on eth0.IPv4.
Apr 30 17:36:46 Sisif avahi-daemon[5284]: Withdrawing address record for 192.168.0.118 on eth0.
Apr 30 17:36:46 Sisif avahi-daemon[5284]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.118.
Apr 30 17:36:46 Sisif avahi-daemon[5284]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 30 17:36:46 Sisif avahi-autoipd(eth0)[27837]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 30 17:36:46 Sisif avahi-autoipd(eth0)[27837]: Successfully called chroot().
Apr 30 17:36:46 Sisif avahi-autoipd(eth0)[27837]: Successfully dropped root privileges.
Apr 30 17:36:46 Sisif avahi-autoipd(eth0)[27837]: Starting with address 169.254.9.233
Apr 30 17:36:46 Sisif nmbd[5561]: [2008/04/30 17:36:46, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:46 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:46 Sisif nmbd[5561]: [2008/04/30 17:36:46, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:46 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4636 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:46 Sisif nmbd[5561]: [2008/04/30 17:36:46, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:46 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:46 Sisif nmbd[5561]: [2008/04/30 17:36:46, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:46 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4637 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:46 Sisif nmbd[5561]: [2008/04/30 17:36:46, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:46 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:46 Sisif nmbd[5561]: [2008/04/30 17:36:46, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:46 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4638 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:46 Sisif nmbd[5561]: [2008/04/30 17:36:46, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:46 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:46 Sisif nmbd[5561]: [2008/04/30 17:36:46, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:46 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4639 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:46 Sisif nmbd[5561]: [2008/04/30 17:36:46, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:46 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:46 Sisif nmbd[5561]: [2008/04/30 17:36:46, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:46 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4640 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:46 Sisif nmbd[5561]: [2008/04/30 17:36:46, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:46 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Network is unreachable 
Apr 30 17:36:46 Sisif nmbd[5561]: [2008/04/30 17:36:46, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:46 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4642 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:47 Sisif nmbd[5561]: [2008/04/30 17:36:47, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:47 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:47 Sisif nmbd[5561]: [2008/04/30 17:36:47, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:47 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4636 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:47 Sisif nmbd[5561]: [2008/04/30 17:36:47, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:47 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:47 Sisif nmbd[5561]: [2008/04/30 17:36:47, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:47 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4637 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:47 Sisif nmbd[5561]: [2008/04/30 17:36:47, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:47 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:47 Sisif nmbd[5561]: [2008/04/30 17:36:47, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:47 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4638 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:47 Sisif nmbd[5561]: [2008/04/30 17:36:47, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:47 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:47 Sisif nmbd[5561]: [2008/04/30 17:36:47, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:47 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4639 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:47 Sisif nmbd[5561]: [2008/04/30 17:36:47, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:47 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:47 Sisif nmbd[5561]: [2008/04/30 17:36:47, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:47 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4640 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:47 Sisif nmbd[5561]: [2008/04/30 17:36:47, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:47 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Network is unreachable 
Apr 30 17:36:47 Sisif nmbd[5561]: [2008/04/30 17:36:47, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:47 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4642 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:48 Sisif nmbd[5561]: [2008/04/30 17:36:48, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:48 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:48 Sisif nmbd[5561]: [2008/04/30 17:36:48, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:48 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4636 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:48 Sisif nmbd[5561]: [2008/04/30 17:36:48, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:48 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:48 Sisif nmbd[5561]: [2008/04/30 17:36:48, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:48 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4637 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:48 Sisif nmbd[5561]: [2008/04/30 17:36:48, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:48 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:48 Sisif nmbd[5561]: [2008/04/30 17:36:48, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:48 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4638 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:48 Sisif nmbd[5561]: [2008/04/30 17:36:48, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:48 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:48 Sisif nmbd[5561]: [2008/04/30 17:36:48, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:48 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4639 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:48 Sisif nmbd[5561]: [2008/04/30 17:36:48, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:48 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Invalid argument 
Apr 30 17:36:48 Sisif nmbd[5561]: [2008/04/30 17:36:48, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:48 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4640 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:48 Sisif nmbd[5561]: [2008/04/30 17:36:48, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:48 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(137) ERRNO=Network is unreachable 
Apr 30 17:36:48 Sisif nmbd[5561]: [2008/04/30 17:36:48, 0] nmbd/nmbd_packets.c:retransmit_or_expire_response_records(1619) 
Apr 30 17:36:48 Sisif nmbd[5561]:   retransmit_or_expire_response_records: Failed to resend packet id 4642 to IP 192.168.0.255 on subnet 192.168.0.118 
Apr 30 17:36:52 Sisif avahi-autoipd(eth0)[27837]: Callout BIND, address 169.254.9.233 on interface eth0
Apr 30 17:36:52 Sisif avahi-daemon[5284]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 17:36:52 Sisif avahi-daemon[5284]: New relevant interface eth0.IPv4 for mDNS.
Apr 30 17:36:52 Sisif avahi-daemon[5284]: Registering new address record for 169.254.9.233 on eth0.IPv4.
Apr 30 17:36:55 Sisif init: tty4 main process (4681) killed by TERM signal
Apr 30 17:36:55 Sisif init: tty5 main process (4682) killed by TERM signal
Apr 30 17:36:55 Sisif init: tty2 main process (4684) killed by TERM signal
Apr 30 17:36:55 Sisif init: tty3 main process (4686) killed by TERM signal
Apr 30 17:36:55 Sisif init: tty6 main process (4688) killed by TERM signal
Apr 30 17:36:55 Sisif init: tty1 main process (6203) killed by TERM signal
Apr 30 17:36:55 Sisif kernel: [  695.639365] compiz.real[6469]: segfault at 01e0028b eip 08055a80 esp bfc16c30 error 4
Apr 30 17:36:56 Sisif avahi-autoipd(eth0)[27837]: Successfully claimed IP address 169.254.9.233
Apr 30 17:36:56 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 17:36:56 Sisif ntpd[7409]: ntpd exiting on signal 15
Apr 30 17:36:57 Sisif kernel: [  696.853520] gdm[5702]: segfault at 7672657f eip b785a7e2 esp bfdf9280 error 6
Apr 30 17:36:57 Sisif avahi-daemon[5284]: Got SIGTERM, quitting.
Apr 30 17:36:57 Sisif avahi-daemon[5284]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.9.233.
Apr 30 17:36:57 Sisif nmbd[5561]: [2008/04/30 17:36:57, 0] nmbd/nmbd.c:terminate(58) 
Apr 30 17:36:57 Sisif nmbd[5561]:   Got SIGTERM: going down... 
Apr 30 17:36:57 Sisif nmbd[5561]: [2008/04/30 17:36:57, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:36:57 Sisif nmbd[5561]:   Packet send failed to 192.168.0.255(138) ERRNO=Invalid argument 
Apr 30 17:36:59 Sisif rpc.statd[4516]: Caught signal 15, un-registering and exiting.
Apr 30 17:37:00 Sisif kernel: [  700.414139] ip6_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 17:37:01 Sisif mountd[5516]: Caught signal 15, un-registering and exiting.
Apr 30 17:37:01 Sisif kernel: [  703.660173] nfsd: last server has exited
Apr 30 17:37:01 Sisif kernel: [  703.660177] nfsd: unexporting all filesystems
Apr 30 17:37:01 Sisif exiting on signal 15
Apr 30 17:37:42 Sisif syslogd 1.5.0#1ubuntu1: restart.
Apr 30 17:37:43 Sisif kernel: Inspecting /boot/System.map-2.6.24-16-generic
Apr 30 17:37:43 Sisif kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Apr 30 17:37:43 Sisif kernel: Symbols match kernel version 2.6.24.
Apr 30 17:37:43 Sisif kernel: Loaded 21378 symbols from 98 modules.
Apr 30 17:37:43 Sisif kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Apr 30 17:37:43 Sisif kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 30 17:37:43 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 30 17:37:43 Sisif kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 30 17:37:43 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d3400 (usable)
Apr 30 17:37:43 Sisif kernel: [    0.000000]  BIOS-e820: 000000007f6d3400 - 0000000080000000 (reserved)
Apr 30 17:37:43 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Apr 30 17:37:43 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Apr 30 17:37:43 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 30 17:37:43 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Apr 30 17:37:43 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Apr 30 17:37:43 Sisif kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr 30 17:37:43 Sisif kernel: [    0.000000] 1142MB HIGHMEM available.
Apr 30 17:37:43 Sisif kernel: [    0.000000] 896MB LOWMEM available.
Apr 30 17:37:43 Sisif kernel: [    0.000000] Entering add_active_range(0, 0, 521939) 0 entries of 256 used
Apr 30 17:37:43 Sisif kernel: [    0.000000] Zone PFN ranges:
Apr 30 17:37:43 Sisif kernel: [    0.000000]   DMA             0 ->     4096
Apr 30 17:37:43 Sisif kernel: [    0.000000]   Normal       4096 ->   229376
Apr 30 17:37:43 Sisif kernel: [    0.000000]   HighMem    229376 ->   521939
Apr 30 17:37:43 Sisif kernel: [    0.000000] Movable zone start PFN for each node
Apr 30 17:37:43 Sisif kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 30 17:37:43 Sisif kernel: [    0.000000]     0:        0 ->   521939
Apr 30 17:37:43 Sisif kernel: [    0.000000] On node 0 totalpages: 521939
Apr 30 17:37:43 Sisif kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 30 17:37:43 Sisif kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 30 17:37:43 Sisif kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 30 17:37:43 Sisif kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Apr 30 17:37:43 Sisif kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Apr 30 17:37:43 Sisif kernel: [    0.000000]   HighMem zone: 2285 pages used for memmap
Apr 30 17:37:43 Sisif kernel: [    0.000000]   HighMem zone: 290278 pages, LIFO batch:31
Apr 30 17:37:43 Sisif kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 30 17:37:43 Sisif kernel: [    0.000000] DMI 2.4 present.
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: RSDT 7F6D39CD, 0040 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: FACP 7F6D4800, 0074 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: DSDT 7F6D5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: FACS 7F6E3C00, 0040
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: HPET 7F6D4F00, 0038 (r1 DELL    M07            1 ASL        61)
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: APIC 7F6D5000, 0068 (r1 DELL    M07     27D7060D ASL        47)
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: MCFG 7F6D4FC0, 003E (r16 DELL    M07     27D7060D ASL        61)
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: SLIC 7F6D509C, 0024 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: BOOT 7F6D4BC0, 0028 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: SSDT 7F6D3A0D, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 30 17:37:43 Sisif kernel: [    0.000000] Processor #0 6:14 APIC version 20
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 30 17:37:43 Sisif kernel: [    0.000000] Processor #1 6:14 APIC version 20
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 30 17:37:43 Sisif kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 30 17:37:43 Sisif kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 30 17:37:43 Sisif kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 30 17:37:43 Sisif kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 30 17:37:43 Sisif kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
Apr 30 17:37:43 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 30 17:37:43 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Apr 30 17:37:43 Sisif kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517862
Apr 30 17:37:43 Sisif kernel: [    0.000000] Kernel command line: root=UUID=35a5e031-c7e9-4597-9992-99d1d88d0eac ro quiet splash
Apr 30 17:37:43 Sisif kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Apr 30 17:37:43 Sisif kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Apr 30 17:37:43 Sisif kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 30 17:37:43 Sisif kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 30 17:37:43 Sisif kernel: [    0.000000] Initializing CPU#0
Apr 30 17:37:43 Sisif kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 30 17:37:43 Sisif kernel: [    0.000000] Detected 1729.050 MHz processor.
Apr 30 17:37:43 Sisif kernel: [    7.523213] Console: colour VGA+ 80x25
Apr 30 17:37:43 Sisif kernel: [    7.523217] console [tty0] enabled
Apr 30 17:37:43 Sisif kernel: [    7.523519] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 30 17:37:43 Sisif kernel: [    7.523913] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 30 17:37:43 Sisif kernel: [    7.645883] Memory: 2057924k/2087756k available (2157k kernel code, 28552k reserved, 998k data, 364k init, 1170252k highmem)
Apr 30 17:37:43 Sisif kernel: [    7.645891] virtual kernel memory layout:
Apr 30 17:37:43 Sisif kernel: [    7.645892]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Apr 30 17:37:43 Sisif kernel: [    7.645894]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 30 17:37:43 Sisif kernel: [    7.645895]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Apr 30 17:37:43 Sisif kernel: [    7.645896]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 30 17:37:43 Sisif kernel: [    7.645897]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Apr 30 17:37:43 Sisif kernel: [    7.645899]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Apr 30 17:37:43 Sisif kernel: [    7.645900]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Apr 30 17:37:43 Sisif kernel: [    7.645904] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 30 17:37:43 Sisif kernel: [    7.645947] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 30 17:37:43 Sisif kernel: [    7.646095] hpet clockevent registered
Apr 30 17:37:43 Sisif kernel: [    7.726068] Calibrating delay using timer specific routine.. 3461.82 BogoMIPS (lpj=6923649)
Apr 30 17:37:43 Sisif kernel: [    7.726093] Security Framework initialized
Apr 30 17:37:43 Sisif kernel: [    7.726101] SELinux:  Disabled at boot.
Apr 30 17:37:43 Sisif kernel: [    7.726117] AppArmor: AppArmor initialized
Apr 30 17:37:43 Sisif kernel: [    7.726121] Failure registering capabilities with primary security module.
Apr 30 17:37:43 Sisif kernel: [    7.726131] Mount-cache hash table entries: 512
Apr 30 17:37:43 Sisif kernel: [    7.726268] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 17:37:43 Sisif kernel: [    7.726278] monitor/mwait feature present.
Apr 30 17:37:43 Sisif kernel: [    7.726280] using mwait in idle threads.
Apr 30 17:37:43 Sisif kernel: [    7.726285] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 17:37:43 Sisif kernel: [    7.726287] CPU: L2 cache: 1024K
Apr 30 17:37:43 Sisif kernel: [    7.726290] CPU: Physical Processor ID: 0
Apr 30 17:37:43 Sisif kernel: [    7.726292] CPU: Processor Core ID: 0
Apr 30 17:37:43 Sisif kernel: [    7.726294] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 17:37:43 Sisif kernel: [    7.726303] Compat vDSO mapped to ffffe000.
Apr 30 17:37:43 Sisif kernel: [    7.726316] Checking 'hlt' instruction... OK.
Apr 30 17:37:43 Sisif kernel: [    7.742469] SMP alternatives: switching to UP code
Apr 30 17:37:43 Sisif kernel: [    7.744309] Early unpacking initramfs... done
Apr 30 17:37:43 Sisif kernel: [    8.094182] ACPI: Core revision 20070126
Apr 30 17:37:43 Sisif kernel: [    8.094241] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 30 17:37:43 Sisif kernel: [    8.096916] CPU0: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 17:37:43 Sisif kernel: [    8.096936] SMP alternatives: switching to SMP code
Apr 30 17:37:43 Sisif kernel: [    8.097649] Booting processor 1/1 eip 3000
Apr 30 17:37:43 Sisif kernel: [   10.121289] Initializing CPU#1
Apr 30 17:37:43 Sisif kernel: [   10.201241] Calibrating delay using timer specific routine.. 3458.06 BogoMIPS (lpj=6916136)
Apr 30 17:37:43 Sisif kernel: [   10.201249] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 17:37:43 Sisif kernel: [   10.201255] monitor/mwait feature present.
Apr 30 17:37:43 Sisif kernel: [   10.201259] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 17:37:43 Sisif kernel: [   10.201261] CPU: L2 cache: 1024K
Apr 30 17:37:43 Sisif kernel: [   10.201263] CPU: Physical Processor ID: 0
Apr 30 17:37:43 Sisif kernel: [   10.201264] CPU: Processor Core ID: 1
Apr 30 17:37:43 Sisif kernel: [   10.201266] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 17:37:43 Sisif kernel: [    8.190312] CPU1: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 17:37:43 Sisif kernel: [    8.190336] Total of 2 processors activated (6919.89 BogoMIPS).
Apr 30 17:37:43 Sisif kernel: [    8.190535] ENABLING IO-APIC IRQs
Apr 30 17:37:43 Sisif kernel: [    8.190732] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 30 17:37:43 Sisif kernel: [    8.337924] checking TSC synchronization [CPU#0 -> CPU#1]:
Apr 30 17:37:43 Sisif kernel: [    8.357928] Measured 3479139222 cycles TSC warp between CPUs, turning off TSC clock.
Apr 30 17:37:43 Sisif kernel: [    8.357930] Marking TSC unstable due to: check_tsc_sync_source failed.
Apr 30 17:37:43 Sisif kernel: [    8.357945] Brought up 2 CPUs
Apr 30 17:37:43 Sisif kernel: [    8.357972] CPU0 attaching sched-domain:
Apr 30 17:37:43 Sisif kernel: [    8.357975]  domain 0: span 03
Apr 30 17:37:43 Sisif kernel: [    8.357977]   groups: 01 02
Apr 30 17:37:43 Sisif kernel: [    8.357980] CPU1 attaching sched-domain:
Apr 30 17:37:43 Sisif kernel: [    8.357982]  domain 0: span 03
Apr 30 17:37:43 Sisif kernel: [    8.357983]   groups: 02 01
Apr 30 17:37:43 Sisif kernel: [   10.369622] net_namespace: 64 bytes
Apr 30 17:37:43 Sisif kernel: [   10.369632] Booting paravirtualized kernel on bare hardware
Apr 30 17:37:43 Sisif kernel: [   10.370129] Time: 14:37:21  Date: 04/30/08
Apr 30 17:37:43 Sisif kernel: [   10.370160] NET: Registered protocol family 16
Apr 30 17:37:43 Sisif kernel: [   10.370382] EISA bus registered
Apr 30 17:37:43 Sisif kernel: [   10.370386] ACPI: bus type pci registered
Apr 30 17:37:43 Sisif kernel: [   10.399034] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=13
Apr 30 17:37:43 Sisif kernel: [   10.399037] PCI: Using configuration type 1
Apr 30 17:37:43 Sisif kernel: [   10.399039] Setting up standard PCI resources
Apr 30 17:37:43 Sisif kernel: [    8.393418] ACPI: EC: Look up EC in DSDT
Apr 30 17:37:43 Sisif kernel: [    8.398343] ACPI: Interpreter enabled
Apr 30 17:37:43 Sisif kernel: [    8.398347] ACPI: (supports S0 S3 S4 S5)
Apr 30 17:37:43 Sisif kernel: [    8.398360] ACPI: Using IOAPIC for interrupt routing
Apr 30 17:37:43 Sisif kernel: [    8.412402] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 30 17:37:43 Sisif kernel: [    8.413204] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 30 17:37:43 Sisif kernel: [    8.413209] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Apr 30 17:37:43 Sisif kernel: [    8.414387] PCI: Transparent bridge - 0000:00:1e.0
Apr 30 17:37:43 Sisif kernel: [    8.414428] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 30 17:37:43 Sisif kernel: [    8.414890] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr 30 17:37:43 Sisif kernel: [    8.415023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 30 17:37:43 Sisif kernel: [    8.415143] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr 30 17:37:43 Sisif kernel: [    8.423494] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr 30 17:37:43 Sisif kernel: [    8.423605] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
Apr 30 17:37:43 Sisif kernel: [    8.423713] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr 30 17:37:43 Sisif kernel: [    8.423821] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Apr 30 17:37:43 Sisif kernel: [    8.423931] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 30 17:37:43 Sisif kernel: [    8.424043] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 30 17:37:43 Sisif kernel: [    8.424154] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Apr 30 17:37:43 Sisif kernel: [    8.424264] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Apr 30 17:37:43 Sisif kernel: [    8.424422] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 30 17:37:43 Sisif kernel: [    8.424457] pnp: PnP ACPI init
Apr 30 17:37:43 Sisif kernel: [    8.424464] ACPI: bus type pnp registered
Apr 30 17:37:43 Sisif kernel: [    8.440725] pnpacpi: exceeded the max number of mem resources: 12
Apr 30 17:37:43 Sisif kernel: [    8.453579] pnp: PnP ACPI: found 12 devices
Apr 30 17:37:43 Sisif kernel: [    8.453582] ACPI: ACPI bus type pnp unregistered
Apr 30 17:37:43 Sisif kernel: [    8.453585] PnPBIOS: Disabled by ACPI PNP
Apr 30 17:37:43 Sisif kernel: [   10.465234] PCI: Using ACPI for IRQ routing
Apr 30 17:37:43 Sisif kernel: [   10.465237] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 30 17:37:43 Sisif kernel: [   10.529250] NET: Registered protocol family 8
Apr 30 17:37:43 Sisif kernel: [   10.529253] NET: Registered protocol family 20
Apr 30 17:37:43 Sisif kernel: [   10.529291] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 30 17:37:43 Sisif kernel: [   10.529295] hpet0: 3 64-bit timers, 14318180 Hz
Apr 30 17:37:43 Sisif kernel: [   10.530335] AppArmor: AppArmor Filesystem Enabled
Apr 30 17:37:43 Sisif kernel: [    8.521728] Time: hpet clocksource has been installed.
Apr 30 17:37:43 Sisif kernel: [    8.521750] Switched to high resolution mode on CPU 0
Apr 30 17:37:43 Sisif kernel: [   10.533246] Switched to high resolution mode on CPU 1
Apr 30 17:37:43 Sisif kernel: [    8.534727] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534731] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534734] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534737] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534740] system 00:00: iomem range 0x100000-0x7f6d33ff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534743] system 00:00: iomem range 0x7f6d3400-0x7f6fffff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534747] system 00:00: iomem range 0x7f700000-0x7f7fffff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534750] system 00:00: iomem range 0x7f700000-0x7fefffff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534753] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534757] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534760] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534763] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534770] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534773] system 00:02: ioport range 0x1000-0x1005 has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534776] system 00:02: ioport range 0x1008-0x100f has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534782] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534785] system 00:03: ioport range 0x1006-0x1007 has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534789] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534792] system 00:03: ioport range 0x1060-0x107f has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534795] system 00:03: ioport range 0x1080-0x10bf has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534798] system 00:03: ioport range 0x10c0-0x10df has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534801] system 00:03: ioport range 0x1010-0x102f has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534803] system 00:03: ioport range 0x809-0x809 has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534812] system 00:08: ioport range 0xc80-0xcff could not be reserved
Apr 30 17:37:43 Sisif kernel: [    8.534815] system 00:08: ioport range 0x910-0x91f has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534818] system 00:08: ioport range 0x920-0x92f has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534821] system 00:08: ioport range 0xcb0-0xcbf has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534824] system 00:08: ioport range 0x930-0x97f has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.534832] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Apr 30 17:37:43 Sisif kernel: [    8.565301] PCI: Bridge: 0000:00:1c.0
Apr 30 17:37:43 Sisif kernel: [    8.565303]   IO window: disabled.
Apr 30 17:37:43 Sisif kernel: [    8.565309]   MEM window: efd00000-efdfffff
Apr 30 17:37:43 Sisif kernel: [    8.565314]   PREFETCH window: disabled.
Apr 30 17:37:43 Sisif kernel: [    8.565320] PCI: Bridge: 0000:00:1c.3
Apr 30 17:37:43 Sisif kernel: [    8.565323]   IO window: d000-dfff
Apr 30 17:37:43 Sisif kernel: [    8.565329]   MEM window: efa00000-efcfffff
Apr 30 17:37:43 Sisif kernel: [    8.565334]   PREFETCH window: e0000000-e01fffff
Apr 30 17:37:43 Sisif kernel: [    8.565341] PCI: Bridge: 0000:00:1e.0
Apr 30 17:37:43 Sisif kernel: [    8.565342]   IO window: disabled.
Apr 30 17:37:43 Sisif kernel: [    8.565348]   MEM window: ef900000-ef9fffff
Apr 30 17:37:43 Sisif kernel: [    8.565353]   PREFETCH window: disabled.
Apr 30 17:37:43 Sisif kernel: [    8.565386] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:37:43 Sisif kernel: [    8.565393] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 17:37:43 Sisif kernel: [    8.565418] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Apr 30 17:37:43 Sisif kernel: [    8.565424] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 17:37:43 Sisif kernel: [    8.565438] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 30 17:37:43 Sisif kernel: [    8.565452] NET: Registered protocol family 2
Apr 30 17:37:43 Sisif kernel: [    8.609716] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 30 17:37:43 Sisif kernel: [    8.609960] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 30 17:37:43 Sisif kernel: [    8.610709] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 30 17:37:43 Sisif kernel: [    8.611086] TCP: Hash tables configured (established 131072 bind 65536)
Apr 30 17:37:43 Sisif kernel: [    8.611089] TCP reno registered
Apr 30 17:37:43 Sisif kernel: [    8.621823] checking if image is initramfs... it is
Apr 30 17:37:43 Sisif kernel: [    9.314248] Freeing initrd memory: 7267k freed
Apr 30 17:37:43 Sisif kernel: [    9.314428] Simple Boot Flag at 0x79 set to 0x1
Apr 30 17:37:43 Sisif kernel: [   11.326538] audit: initializing netlink socket (disabled)
Apr 30 17:37:43 Sisif kernel: [   11.326552] audit(1209566241.544:1): initialized
Apr 30 17:37:43 Sisif kernel: [    9.315423] highmem bounce pool size: 64 pages
Apr 30 17:37:43 Sisif kernel: [    9.317568] VFS: Disk quotas dquot_6.5.1
Apr 30 17:37:43 Sisif kernel: [    9.317652] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 30 17:37:43 Sisif kernel: [    9.317796] io scheduler noop registered
Apr 30 17:37:43 Sisif kernel: [    9.317798] io scheduler anticipatory registered
Apr 30 17:37:43 Sisif kernel: [    9.317800] io scheduler deadline registered
Apr 30 17:37:43 Sisif kernel: [    9.317812] io scheduler cfq registered (default)
Apr 30 17:37:43 Sisif kernel: [    9.317823] Boot video device is 0000:00:02.0
Apr 30 17:37:43 Sisif kernel: [    9.318037] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 17:37:43 Sisif kernel: [    9.318095] assign_interrupt_mode Found MSI capability
Apr 30 17:37:43 Sisif kernel: [    9.318146] Allocate Port Service[0000:00:1c.0:pcie00]
Apr 30 17:37:43 Sisif kernel: [    9.318186] Allocate Port Service[0000:00:1c.0:pcie02]
Apr 30 17:37:43 Sisif kernel: [    9.318293] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 17:37:43 Sisif kernel: [    9.318355] assign_interrupt_mode Found MSI capability
Apr 30 17:37:43 Sisif kernel: [    9.318402] Allocate Port Service[0000:00:1c.3:pcie00]
Apr 30 17:37:43 Sisif kernel: [    9.318441] Allocate Port Service[0000:00:1c.3:pcie02]
Apr 30 17:37:43 Sisif kernel: [    9.318729] isapnp: Scanning for PnP cards...
Apr 30 17:37:43 Sisif kernel: [    9.672892] isapnp: No Plug & Play device found
Apr 30 17:37:43 Sisif kernel: [   11.715007] Real Time Clock Driver v1.12ac
Apr 30 17:37:43 Sisif kernel: [   11.715171] hpet_resources: 0xfed00000 is busy
Apr 30 17:37:43 Sisif kernel: [   11.715225] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 30 17:37:43 Sisif kernel: [   11.716491] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 30 17:37:43 Sisif kernel: [   11.716569] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 30 17:37:43 Sisif kernel: [   11.716675] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 30 17:37:43 Sisif kernel: [    9.708268] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 30 17:37:43 Sisif kernel: [    9.708273] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 30 17:37:43 Sisif kernel: [   11.740795] mice: PS/2 mouse device common for all mice
Apr 30 17:37:43 Sisif kernel: [   11.740927] EISA: Probing bus 0 at eisa.0
Apr 30 17:37:43 Sisif kernel: [   11.740994] EISA: Mainboard UO_FFFF detected.
Apr 30 17:37:43 Sisif kernel: [   11.741035] Cannot allocate resource for EISA slot 1
Apr 30 17:37:43 Sisif kernel: [   11.741066] EISA: Detected 0 cards.
Apr 30 17:37:43 Sisif kernel: [   11.741069] cpuidle: using governor ladder
Apr 30 17:37:43 Sisif kernel: [   11.741071] cpuidle: using governor menu
Apr 30 17:37:43 Sisif kernel: [   11.741164] NET: Registered protocol family 1
Apr 30 17:37:43 Sisif kernel: [   11.741195] Using IPI No-Shortcut mode
Apr 30 17:37:43 Sisif kernel: [   11.741230] registered taskstats version 1
Apr 30 17:37:43 Sisif kernel: [   11.741347]   Magic number: 4:308:638
Apr 30 17:37:43 Sisif kernel: [   11.741457] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 30 17:37:43 Sisif kernel: [   11.741460] EDD information not available.
Apr 30 17:37:43 Sisif kernel: [   11.741642] Freeing unused kernel memory: 364k freed
Apr 30 17:37:43 Sisif kernel: [   11.743626] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 30 17:37:43 Sisif kernel: [   12.960116] fuse init (API version 7.9)
Apr 30 17:37:43 Sisif kernel: [   12.981563] ACPI: SSDT 7F6D4134, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Apr 30 17:37:43 Sisif kernel: [   12.981755] ACPI: SSDT 7F6D3EE9, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Apr 30 17:37:43 Sisif kernel: [   10.970978] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 17:37:43 Sisif kernel: [   10.970985] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 30 17:37:43 Sisif kernel: [   10.971216] ACPI: SSDT 7F6D4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Apr 30 17:37:43 Sisif kernel: [   10.971391] ACPI: SSDT 7F6D40AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Apr 30 17:37:43 Sisif kernel: [   12.983852] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 17:37:43 Sisif kernel: [   12.983858] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 30 17:37:43 Sisif kernel: [   12.989139] ACPI: Thermal Zone [THM] (41 C)
Apr 30 17:37:43 Sisif kernel: [   13.171249] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:37:43 Sisif kernel: [   13.171268] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 17:37:43 Sisif kernel: [   13.228998] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Apr 30 17:37:43 Sisif kernel: [   13.394582] usbcore: registered new interface driver usbfs
Apr 30 17:37:43 Sisif kernel: [   13.394609] usbcore: registered new interface driver hub
Apr 30 17:37:43 Sisif kernel: [   13.394849] usbcore: registered new device driver usb
Apr 30 17:37:43 Sisif kernel: [   13.396361] USB Universal Host Controller Interface driver v3.0
Apr 30 17:37:43 Sisif kernel: [   13.396419] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 17:37:43 Sisif kernel: [   13.396431] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 30 17:37:43 Sisif kernel: [   13.396435] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 30 17:37:43 Sisif kernel: [   13.396685] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr 30 17:37:43 Sisif kernel: [   13.396740] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
Apr 30 17:37:43 Sisif kernel: [   13.396885] usb usb1: configuration #1 chosen from 1 choice
Apr 30 17:37:43 Sisif kernel: [   13.396910] hub 1-0:1.0: USB hub found
Apr 30 17:37:43 Sisif kernel: [   13.396915] hub 1-0:1.0: 2 ports detected
Apr 30 17:37:43 Sisif kernel: [   11.486671] SCSI subsystem initialized
Apr 30 17:37:43 Sisif kernel: [   13.500802] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
Apr 30 17:37:43 Sisif kernel: [   13.500815] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 30 17:37:43 Sisif kernel: [   13.500819] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 30 17:37:43 Sisif kernel: [   13.500845] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr 30 17:37:43 Sisif kernel: [   13.500879] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bf60
Apr 30 17:37:43 Sisif kernel: [   13.501003] usb usb2: configuration #1 chosen from 1 choice
Apr 30 17:37:43 Sisif kernel: [   13.501029] hub 2-0:1.0: USB hub found
Apr 30 17:37:43 Sisif kernel: [   13.501035] hub 2-0:1.0: 2 ports detected
Apr 30 17:37:43 Sisif kernel: [   11.519146] libata version 3.00 loaded.
Apr 30 17:37:43 Sisif kernel: [   13.604805] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
Apr 30 17:37:43 Sisif kernel: [   13.604820] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 30 17:37:43 Sisif kernel: [   13.604824] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 30 17:37:43 Sisif kernel: [   13.604851] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr 30 17:37:43 Sisif kernel: [   13.604887] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000bf40
Apr 30 17:37:43 Sisif kernel: [   13.605012] usb usb3: configuration #1 chosen from 1 choice
Apr 30 17:37:43 Sisif kernel: [   13.605039] hub 3-0:1.0: USB hub found
Apr 30 17:37:43 Sisif kernel: [   13.605045] hub 3-0:1.0: 2 ports detected
Apr 30 17:37:43 Sisif kernel: [   13.708726] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
Apr 30 17:37:43 Sisif kernel: [   13.708739] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Apr 30 17:37:43 Sisif kernel: [   13.708744] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Apr 30 17:37:43 Sisif kernel: [   13.708770] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Apr 30 17:37:43 Sisif kernel: [   13.708806] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000bf20
Apr 30 17:37:43 Sisif kernel: [   13.708933] usb usb4: configuration #1 chosen from 1 choice
Apr 30 17:37:43 Sisif kernel: [   13.708958] hub 4-0:1.0: USB hub found
Apr 30 17:37:43 Sisif kernel: [   13.708964] hub 4-0:1.0: 2 ports detected
Apr 30 17:37:43 Sisif kernel: [   13.812844] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 17:37:43 Sisif kernel: [   13.812860] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 30 17:37:43 Sisif kernel: [   13.812865] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 30 17:37:43 Sisif kernel: [   13.812894] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Apr 30 17:37:43 Sisif kernel: [   13.816807] ehci_hcd 0000:00:1d.7: debug port 1
Apr 30 17:37:43 Sisif kernel: [   13.816815] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr 30 17:37:43 Sisif kernel: [   13.816822] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80000
Apr 30 17:37:43 Sisif kernel: [   13.832548] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 30 17:37:43 Sisif kernel: [   13.832674] usb usb5: configuration #1 chosen from 1 choice
Apr 30 17:37:43 Sisif kernel: [   13.832701] hub 5-0:1.0: USB hub found
Apr 30 17:37:43 Sisif kernel: [   13.832708] hub 5-0:1.0: 8 ports detected
Apr 30 17:37:43 Sisif kernel: [   11.925261] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Apr 30 17:37:43 Sisif kernel: [   11.978041] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 30 17:37:43 Sisif kernel: [   11.983108] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 17:37:43 Sisif kernel: [   12.040175] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 17:37:43 Sisif kernel: [   12.040208] b44.c:v2.0
Apr 30 17:37:43 Sisif kernel: [   12.040261] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 17:37:43 Sisif kernel: [   12.040298] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 17:37:43 Sisif kernel: [   12.040312] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Apr 30 17:37:43 Sisif kernel: [   12.060405] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 17:37:43 Sisif kernel: [   14.075332] ata_piix 0000:00:1f.2: version 2.12
Apr 30 17:37:43 Sisif kernel: [   14.075340] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Apr 30 17:37:43 Sisif kernel: [   14.075361] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 17:37:43 Sisif kernel: [   14.075405] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 17:37:43 Sisif kernel: [   14.075506] scsi0 : ata_piix
Apr 30 17:37:43 Sisif kernel: [   14.075576] scsi1 : ata_piix
Apr 30 17:37:43 Sisif kernel: [   14.076358] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Apr 30 17:37:43 Sisif kernel: [   14.076361] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Apr 30 17:37:43 Sisif kernel: [   12.233962] ata1.00: ATA-7: ST9120822AS, 3.CDD, max UDMA/133
Apr 30 17:37:43 Sisif kernel: [   12.233967] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
Apr 30 17:37:43 Sisif kernel: [   12.250620] ata1.00: configured for UDMA/133
Apr 30 17:37:43 Sisif kernel: [   14.603694] ata2.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1B, max UDMA/33
Apr 30 17:37:43 Sisif kernel: [   14.799543] ata2.00: configured for UDMA/33
Apr 30 17:37:43 Sisif kernel: [   12.788359] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.CD PQ: 0 ANSI: 5
Apr 30 17:37:43 Sisif kernel: [   12.790650] scsi 1:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
Apr 30 17:37:43 Sisif kernel: [   12.798223] Driver 'sd' needs updating - please use bus_type methods
Apr 30 17:37:43 Sisif kernel: [   12.798313] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 17:37:43 Sisif kernel: [   12.798326] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 17:37:43 Sisif kernel: [   12.798329] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 17:37:43 Sisif kernel: [   12.798346] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 17:37:43 Sisif kernel: [   12.798397] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 17:37:43 Sisif kernel: [   12.798407] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 17:37:43 Sisif kernel: [   12.798410] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 17:37:43 Sisif kernel: [   12.798426] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 17:37:43 Sisif kernel: [   12.798430]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Apr 30 17:37:43 Sisif kernel: [   12.894864]  sda1 sda2 sda3
Apr 30 17:37:43 Sisif kernel: [   12.907150] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 30 17:37:43 Sisif kernel: [   12.912730] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 30 17:37:43 Sisif kernel: [   12.912753] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 30 17:37:43 Sisif kernel: [   14.936100] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr 30 17:37:43 Sisif kernel: [   14.936106] Uniform CD-ROM driver Revision: 3.20
Apr 30 17:37:43 Sisif kernel: [   14.936163] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 30 17:37:43 Sisif kernel: [   15.264339] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc00026e60070]
Apr 30 17:37:43 Sisif kernel: [   13.429655] Attempting manual resume
Apr 30 17:37:43 Sisif kernel: [   13.429659] swsusp: Resume From Partition 8:2
Apr 30 17:37:43 Sisif kernel: [   13.429660] PM: Checking swsusp image.
Apr 30 17:37:43 Sisif kernel: [   13.429840] PM: Resume from disk failed.
Apr 30 17:37:43 Sisif kernel: [   15.483019] kjournald starting.  Commit interval 5 seconds
Apr 30 17:37:43 Sisif kernel: [   13.471666] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 17:37:43 Sisif kernel: [   21.589079] Linux agpgart interface v0.102
Apr 30 17:37:43 Sisif kernel: [   23.643941] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 30 17:37:43 Sisif kernel: [   23.683990] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 30 17:37:43 Sisif kernel: [   21.724484] agpgart: Detected an Intel 945GM Chipset.
Apr 30 17:37:43 Sisif kernel: [   21.725054] agpgart: Detected 7932K stolen memory.
Apr 30 17:37:43 Sisif kernel: [   21.742128] agpgart: AGP aperture is 256M @ 0xd0000000
Apr 30 17:37:43 Sisif kernel: [   23.822685] ACPI: AC Adapter [AC] (on-line)
Apr 30 17:37:43 Sisif kernel: [   21.838539] input: Lid Switch as /devices/virtual/input/input2
Apr 30 17:37:43 Sisif kernel: [   21.838963] ACPI: Lid Switch [LID]
Apr 30 17:37:43 Sisif kernel: [   21.839016] input: Power Button (CM) as /devices/virtual/input/input3
Apr 30 17:37:43 Sisif kernel: [   21.861177] ACPI: Power Button (CM) [PBTN]
Apr 30 17:37:43 Sisif kernel: [   21.861267] input: Sleep Button (CM) as /devices/virtual/input/input4
Apr 30 17:37:43 Sisif kernel: [   21.891373] ACPI: Sleep Button (CM) [SBTN]
Apr 30 17:37:43 Sisif kernel: [   24.065177] ACPI: Battery Slot [BAT0] (battery present)
Apr 30 17:37:43 Sisif kernel: [   22.167541] ACPI: WMI-Acer: Mapper loaded
Apr 30 17:37:43 Sisif kernel: [   24.358164] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input5
Apr 30 17:37:43 Sisif kernel: [   24.379472] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr 30 17:37:43 Sisif kernel: [   24.387502] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
Apr 30 17:37:43 Sisif kernel: [   24.403457] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Apr 30 17:37:43 Sisif kernel: [   24.403646] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input7
Apr 30 17:37:43 Sisif kernel: [   24.419862] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Apr 30 17:37:43 Sisif kernel: [   23.020959] iTCO_vendor_support: vendor-support=0
Apr 30 17:37:43 Sisif kernel: [   23.214780] b43-phy0: Broadcom 4311 WLAN found
Apr 30 17:37:43 Sisif kernel: [   23.234800] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Apr 30 17:37:43 Sisif kernel: [   23.234904] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Apr 30 17:37:43 Sisif kernel: [   23.234946] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 30 17:37:43 Sisif kernel: [   23.277007] input: PC Speaker as /devices/platform/pcspkr/input/input8
Apr 30 17:37:43 Sisif kernel: [   23.292980] phy0: Selected rate control algorithm 'simple'
Apr 30 17:37:43 Sisif kernel: [   23.298516] intel_rng: FWH not detected
Apr 30 17:37:43 Sisif kernel: [   23.354446] sdhci: Secure Digital Host Controller Interface driver
Apr 30 17:37:43 Sisif kernel: [   23.354451] sdhci: Copyright(c) Pierre Ossman
Apr 30 17:37:43 Sisif kernel: [   23.378754] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
Apr 30 17:37:43 Sisif kernel: [   23.378781] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 30 17:37:43 Sisif kernel: [   23.595437] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
Apr 30 17:37:43 Sisif kernel: [   23.595464] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
Apr 30 17:37:43 Sisif kernel: [   23.595526] mmc0: SDHCI at 0xef9fd500 irq 23 DMA
Apr 30 17:37:43 Sisif kernel: [   26.155132] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
Apr 30 17:37:43 Sisif kernel: [   24.179758] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
Apr 30 17:37:43 Sisif kernel: [   24.225400] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Apr 30 17:37:43 Sisif kernel: [   24.953700] udev: renamed network interface wlan0 to eth1
Apr 30 17:37:43 Sisif kernel: [   27.069276] input: b43-phy0 as /devices/virtual/input/input10
Apr 30 17:37:43 Sisif kernel: [   25.284192] lp: driver loaded but no devices found
Apr 30 17:37:43 Sisif kernel: [   27.459564] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
Apr 30 17:37:43 Sisif kernel: [   28.005122] EXT3 FS on sda1, internal journal
Apr 30 17:37:43 Sisif kernel: [   26.525608] Registered led device: b43-phy0:tx
Apr 30 17:37:43 Sisif kernel: [   26.525638] Registered led device: b43-phy0:rx
Apr 30 17:37:43 Sisif kernel: [   26.525663] Registered led device: b43-phy0:radio
Apr 30 17:37:43 Sisif kernel: [   26.601072] NET: Registered protocol family 17
Apr 30 17:37:43 Sisif kernel: [   28.834120] kjournald starting.  Commit interval 5 seconds
Apr 30 17:37:43 Sisif kernel: [   26.822996] EXT3 FS on sda3, internal journal
Apr 30 17:37:43 Sisif kernel: [   26.823001] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 17:37:43 Sisif kernel: [   27.634561] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 17:37:43 Sisif kernel: [   28.978084] RPC: Registered udp transport module.
Apr 30 17:37:43 Sisif kernel: [   28.978088] RPC: Registered tcp transport module.
Apr 30 17:37:43 Sisif kernel: [   29.690416] No dock devices found.
Apr 30 17:37:44 Sisif avahi-daemon[5274]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Apr 30 17:37:44 Sisif avahi-daemon[5274]: Successfully dropped root privileges.
Apr 30 17:37:44 Sisif avahi-daemon[5274]: avahi-daemon 0.6.22 starting up.
Apr 30 17:37:44 Sisif avahi-daemon[5274]: Successfully called chroot().
Apr 30 17:37:44 Sisif avahi-daemon[5274]: Successfully dropped remaining capabilities.
Apr 30 17:37:44 Sisif avahi-daemon[5274]: No service file found in /etc/avahi/services.
Apr 30 17:37:44 Sisif avahi-daemon[5274]: Network interface enumeration completed.
Apr 30 17:37:44 Sisif avahi-daemon[5274]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 30 17:37:44 Sisif avahi-daemon[5274]: Server startup complete. Host name is Sisif.local. Local service cookie is 146550374.
Apr 30 17:37:45 Sisif kernel: [   34.191561] ppdev: user-space parallel port driver
Apr 30 17:37:45 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr 30 17:37:45 Sisif kernel: [   32.359436] audit(1209566265.179:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5308 profile="/usr/sbin/cupsd" namespace="default"
Apr 30 17:37:45 Sisif kernel: [   32.407738] apm: BIOS not found.
Apr 30 17:37:46 Sisif kernel: [   33.914537] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Apr 30 17:37:46 Sisif exportfs[5481]: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.10.2:/home/itch/Blonda".   Assuming default behaviour ('no_subtree_check').   NOTE: this default has changed since nfs-utils version 1.0.x 
Apr 30 17:37:46 Sisif kernel: [   34.161309] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Apr 30 17:37:46 Sisif kernel: [   34.177159] NFSD: starting 90-second grace period
Apr 30 17:37:48 Sisif nmbd[5551]: [2008/04/30 17:37:48, 0] nmbd/nmbd_subnetdb.c:create_subnets(190) 
Apr 30 17:37:48 Sisif nmbd[5551]:   create_subnets: No local interfaces ! 
Apr 30 17:37:48 Sisif nmbd[5551]: [2008/04/30 17:37:48, 0] nmbd/nmbd_subnetdb.c:create_subnets(191) 
Apr 30 17:37:48 Sisif nmbd[5551]:   create_subnets: Waiting for an interface to appear ... 
Apr 30 17:37:49 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 30 17:37:49 Sisif dhcdbd: Started up.
Apr 30 17:37:49 Sisif hcid[5628]: Bluetooth HCI daemon
Apr 30 17:37:49 Sisif kernel: [   37.011665] Bluetooth: Core ver 2.11
Apr 30 17:37:49 Sisif kernel: [   37.012538] NET: Registered protocol family 31
Apr 30 17:37:49 Sisif kernel: [   37.012546] Bluetooth: HCI device and connection manager initialized
Apr 30 17:37:49 Sisif kernel: [   37.012555] Bluetooth: HCI socket layer initialized
Apr 30 17:37:49 Sisif hcid[5628]: Starting SDP server
Apr 30 17:37:49 Sisif kernel: [   37.111518] Bluetooth: L2CAP ver 2.9
Apr 30 17:37:49 Sisif kernel: [   37.111526] Bluetooth: L2CAP socket layer initialized
Apr 30 17:37:49 Sisif hcid[5628]: Created local server at unix:abstract=/var/run/dbus-kbi34YR2zp,guid=9efcea9adea587212da5c5b24818843d
Apr 30 17:37:49 Sisif kernel: [   39.135110] Bluetooth: RFCOMM socket layer initialized
Apr 30 17:37:49 Sisif kernel: [   39.135133] Bluetooth: RFCOMM TTY layer initialized
Apr 30 17:37:49 Sisif kernel: [   39.135137] Bluetooth: RFCOMM ver 1.8
Apr 30 17:37:50 Sisif audio[5654]: Bluetooth Audio daemon
Apr 30 17:37:50 Sisif input[5659]: Bluetooth Input daemon
Apr 30 17:37:50 Sisif input[5659]: Registered input manager path:/org/bluez/input
Apr 30 17:37:50 Sisif audio[5654]: Unix socket created: 5
Apr 30 17:37:50 Sisif audio[5654]: audio.conf: Key file does not have key 'Enable'
Apr 30 17:37:50 Sisif audio[5654]: audio.conf: Key file does not have key 'Disable'
Apr 30 17:37:50 Sisif audio[5654]: add_service_record: got record id 0x10000
Apr 30 17:37:50 Sisif audio[5654]: audio.conf: Key file does not have key 'Disable'
Apr 30 17:37:50 Sisif audio[5654]: audio.conf: Key file does not have group 'A2DP'
Apr 30 17:37:50 Sisif last message repeated 3 times
Apr 30 17:37:50 Sisif audio[5654]: SEP 0x806d578 registered: type:0 codec:0 seid:1
Apr 30 17:37:50 Sisif audio[5654]: add_service_record: got record id 0x10001
Apr 30 17:37:50 Sisif audio[5654]: add_service_record: got record id 0x10002
Apr 30 17:37:50 Sisif audio[5654]: add_service_record: got record id 0x10003
Apr 30 17:37:50 Sisif audio[5654]: Registered manager path:/org/bluez/audio
Apr 30 17:37:51 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 30 17:37:52 Sisif ntpd[5723]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 17:37:52 Sisif ntpd[5724]: precision = 1.000 usec
Apr 30 17:37:52 Sisif kernel: [   39.954020] NET: Registered protocol family 10
Apr 30 17:37:52 Sisif kernel: [   39.954561] lo: Disabled Privacy Extensions
Apr 30 17:37:52 Sisif kernel: [   39.956525] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 30 17:37:52 Sisif kernel: [   39.957597] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:37:52 Sisif ntpd[5724]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 17:37:52 Sisif ntpd[5724]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 17:37:52 Sisif ntpd[5724]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 17:37:52 Sisif ntpd[5724]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 17:37:52 Sisif ntpd[5724]: kernel time sync status 0040
Apr 30 17:37:52 Sisif ntpd[5724]: frequency initialized -57.973 PPM from /var/lib/ntp/ntp.drift
Apr 30 17:37:54 Sisif kernel: [   43.399788] [drm] Initialized drm 1.1.0 20060810
Apr 30 17:37:54 Sisif kernel: [   43.414262] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:37:54 Sisif kernel: [   43.414283] PCI: Setting latency timer of device 0000:00:02.0 to 64
Apr 30 17:37:54 Sisif kernel: [   43.414447] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr 30 17:37:54 Sisif anacron[5791]: Anacron 2.3 started on 2008-04-30
Apr 30 17:37:54 Sisif anacron[5791]: Normal exit (0 jobs run)
Apr 30 17:37:54 Sisif /usr/sbin/cron[5823]: (CRON) INFO (pidfile fd = 3)
Apr 30 17:37:54 Sisif /usr/sbin/cron[5824]: (CRON) STARTUP (fork ok)
Apr 30 17:37:54 Sisif /usr/sbin/cron[5824]: (CRON) INFO (Running @reboot jobs)
Apr 30 17:37:54 Sisif ntpd_initres[5742]: host name not found: ntp2a.mcc.ac.uk
Apr 30 17:37:54 Sisif ntpd_initres[5742]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 17:37:54 Sisif ntpd_initres[5742]: host name not found: ntp.landau.ac.ru
Apr 30 17:37:54 Sisif ntpd_initres[5742]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 17:37:55 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 17:37:55 Sisif dhclient: receive_packet failed on eth0: Network is down
Apr 30 17:37:55 Sisif kernel: [   44.826046] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 17:37:55 Sisif kernel: [   44.828940] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 17:37:55 Sisif kernel: [   42.922916] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 17:37:55 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 17:37:55 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:37:55 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:37:55 Sisif dhclient: All rights reserved.
Apr 30 17:37:55 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:37:55 Sisif dhclient: 
Apr 30 17:37:55 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:37:55 Sisif kernel: [   43.156172] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 17:37:55 Sisif kernel: [   45.167874] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:37:55 Sisif kernel: [   45.167936] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 17:37:56 Sisif kernel: [   45.172924] ndiswrapper: using IRQ 16
Apr 30 17:37:56 Sisif kernel: [   45.530239] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 17:37:56 Sisif kernel: [   45.530332] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 17:37:56 Sisif kernel: [   45.532839] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 17:37:56 Sisif kernel: [   45.532924] udev: renamed network interface wlan0 to eth1
Apr 30 17:37:56 Sisif kernel: [   43.528803] usbcore: registered new interface driver ndiswrapper
Apr 30 17:37:56 Sisif kernel: [   45.543681] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:37:56 Sisif kernel: [   43.576643] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:37:56 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 17:37:56 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:37:56 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:37:56 Sisif dhclient: All rights reserved.
Apr 30 17:37:56 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:37:56 Sisif dhclient: 
Apr 30 17:37:56 Sisif kernel: [   45.725040] ndiswrapper: device eth1 removed
Apr 30 17:37:56 Sisif kernel: [   45.725714] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 17:37:56 Sisif kernel: [   45.726653] usbcore: deregistering interface driver ndiswrapper
Apr 30 17:37:56 Sisif kernel: [   45.786813] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 17:37:56 Sisif kernel: [   45.802749] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 17:37:56 Sisif kernel: [   45.804172] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:37:56 Sisif kernel: [   45.804261] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 17:37:56 Sisif kernel: [   45.809736] ndiswrapper: using IRQ 16
Apr 30 17:37:56 Sisif kernel: [   46.172779] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 17:37:56 Sisif kernel: [   46.172893] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 17:37:56 Sisif modprobe: WARNING: Not loading blacklisted module ndiswrapper 
Apr 30 17:37:56 Sisif kernel: [   46.178160] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 17:37:56 Sisif kernel: [   46.178284] udev: renamed network interface wlan0 to eth1
Apr 30 17:37:57 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 30 17:37:57 Sisif dhclient: send_packet: No such device
Apr 30 17:37:57 Sisif kernel: [   46.188122] usbcore: registered new interface driver ndiswrapper
Apr 30 17:37:57 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:37:57 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:37:57 Sisif dhclient: Sending on   Socket/fallback
Apr 30 17:37:57 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 30 17:37:57 Sisif dhclient: send_packet: Network is down
Apr 30 17:37:57 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 17:37:58 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr 30 17:37:58 Sisif dhclient: send_packet: Network is down
Apr 30 17:38:00 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr 30 17:38:00 Sisif dhclient: send_packet: Network is down
Apr 30 17:38:06 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 30 17:38:06 Sisif dhclient: send_packet: No such device
Apr 30 17:38:08 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr 30 17:38:08 Sisif dhclient: send_packet: Network is down
Apr 30 17:38:12 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr 30 17:38:12 Sisif dhclient: send_packet: Network is down
Apr 30 17:38:16 Sisif dhclient: No DHCPOFFERS received.
Apr 30 17:38:16 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 17:38:16 Sisif kernel: [   63.192029] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:38:16 Sisif avahi-autoipd(eth1)[6291]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 30 17:38:16 Sisif avahi-autoipd(eth1)[6291]: Successfully called chroot().
Apr 30 17:38:16 Sisif avahi-autoipd(eth1)[6291]: Successfully dropped root privileges.
Apr 30 17:38:16 Sisif avahi-autoipd(eth1)[6291]: Starting with address 169.254.4.188
Apr 30 17:38:17 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 30 17:38:17 Sisif dhclient: send_packet: No such device
Apr 30 17:38:17 Sisif hcid[5628]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Apr 30 17:38:17 Sisif hcid[5628]: Default authorization agent (:1.18, /org/bluez/auth) registered
Apr 30 17:38:20 Sisif dhclient: No DHCPOFFERS received.
Apr 30 17:38:20 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 17:38:20 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 17:38:21 Sisif ntpd[5724]: ntpd exiting on signal 15
Apr 30 17:38:21 Sisif ntpdate[6482]: can't find host ntp2a.mcc.ac.uk 
Apr 30 17:38:21 Sisif ntpdate[6482]: can't find host ntp.landau.ac.ru 
Apr 30 17:38:21 Sisif ntpdate[6482]: no servers can be used, exiting
Apr 30 17:38:21 Sisif ntpd[6512]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 17:38:21 Sisif ntpd[6513]: precision = 1.000 usec
Apr 30 17:38:21 Sisif ntpd[6513]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 17:38:21 Sisif ntpd[6513]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 17:38:21 Sisif ntpd[6513]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 17:38:21 Sisif ntpd[6513]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 17:38:21 Sisif ntpd[6513]: kernel time sync status 0040
Apr 30 17:38:21 Sisif ntpd[6513]: frequency initialized -57.973 PPM from /var/lib/ntp/ntp.drift
Apr 30 17:38:21 Sisif avahi-autoipd(eth1)[6291]: Callout BIND, address 169.254.4.188 on interface eth1
Apr 30 17:38:21 Sisif avahi-daemon[5274]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 17:38:21 Sisif avahi-daemon[5274]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 17:38:21 Sisif avahi-daemon[5274]: Registering new address record for 169.254.4.188 on eth1.IPv4.
Apr 30 17:38:22 Sisif ntpd[6513]: Listening on interface #4 eth1:avahi, 169.254.4.188#123 Enabled
Apr 30 17:38:23 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr 30 17:38:25 Sisif avahi-autoipd(eth1)[6291]: Successfully claimed IP address 169.254.4.188
Apr 30 17:38:28 Sisif dhclient: No DHCPOFFERS received.
Apr 30 17:38:28 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 17:38:28 Sisif ntpd[6513]: ntpd exiting on signal 15
Apr 30 17:38:29 Sisif kernel: [   76.766198] CPU0 attaching NULL sched-domain.
Apr 30 17:38:29 Sisif kernel: [   76.766210] CPU1 attaching NULL sched-domain.
Apr 30 17:38:29 Sisif kernel: [   76.775162] CPU0 attaching sched-domain:
Apr 30 17:38:29 Sisif kernel: [   76.775171]  domain 0: span 03
Apr 30 17:38:29 Sisif kernel: [   76.775173]   groups: 01 02
Apr 30 17:38:29 Sisif kernel: [   76.775178] CPU1 attaching sched-domain:
Apr 30 17:38:29 Sisif kernel: [   76.775180]  domain 0: span 03
Apr 30 17:38:29 Sisif kernel: [   76.775182]   groups: 02 01
Apr 30 17:38:32 Sisif avahi-daemon[5274]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 17:38:32 Sisif avahi-daemon[5274]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 17:38:32 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 17:38:32 Sisif avahi-autoipd(eth1)[6291]: SIOCSIFFLAGS failed: Permission denied
Apr 30 17:38:32 Sisif avahi-autoipd(eth1)[6291]: Callout STOP, address 169.254.4.188 on interface eth1
Apr 30 17:38:32 Sisif avahi-daemon[5274]: Withdrawing address record for 169.254.4.188 on eth1.
Apr 30 17:38:32 Sisif avahi-autoipd(eth1)[6292]: client: RTNETLINK answers: No such process
Apr 30 17:38:32 Sisif kernel: [   81.670922] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:38:32 Sisif kernel: [   82.141196] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:38:32 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:38:32 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:38:32 Sisif dhclient: All rights reserved.
Apr 30 17:38:32 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:38:32 Sisif dhclient: 
Apr 30 17:38:33 Sisif ntpdate[6720]: can't find host ntp2a.mcc.ac.uk 
Apr 30 17:38:33 Sisif ntpdate[6720]: can't find host ntp.landau.ac.ru 
Apr 30 17:38:33 Sisif ntpdate[6720]: no servers can be used, exiting
Apr 30 17:38:33 Sisif ntpd[6936]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 17:38:33 Sisif ntpd[6937]: precision = 1.000 usec
Apr 30 17:38:33 Sisif ntpd[6937]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 17:38:33 Sisif ntpd[6937]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 17:38:33 Sisif ntpd[6937]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 17:38:33 Sisif ntpd[6937]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 17:38:33 Sisif ntpd[6937]: kernel time sync status 0040
Apr 30 17:38:33 Sisif ntpd[6937]: frequency initialized -57.973 PPM from /var/lib/ntp/ntp.drift
Apr 30 17:38:33 Sisif ntpd_initres[6514]: host name not found: ntp2a.mcc.ac.uk
Apr 30 17:38:33 Sisif ntpd_initres[6514]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 17:38:33 Sisif ntpd_initres[6514]: parent died before we finished, exiting
Apr 30 17:38:33 Sisif ntpdate[6779]: can't find host ntp2a.mcc.ac.uk 
Apr 30 17:38:33 Sisif ntpdate[6779]: can't find host ntp.landau.ac.ru 
Apr 30 17:38:33 Sisif ntpdate[6779]: no servers can be used, exiting
Apr 30 17:38:34 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:38:34 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:38:34 Sisif dhclient: Sending on   Socket/fallback
Apr 30 17:38:35 Sisif ntpd_initres[6938]: host name not found: ntp2a.mcc.ac.uk
Apr 30 17:38:35 Sisif ntpd_initres[6938]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 17:38:35 Sisif ntpd_initres[6938]: host name not found: ntp.landau.ac.ru
Apr 30 17:38:35 Sisif ntpd_initres[6938]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 17:38:36 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 17:38:38 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 17:38:47 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 30 17:38:52 Sisif last message repeated 2 times
Apr 30 17:38:56 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 30 17:39:03 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr 30 17:39:18 Sisif dhclient: No DHCPOFFERS received.
Apr 30 17:39:18 Sisif dhclient: Trying recorded lease 192.168.1.102
Apr 30 17:39:18 Sisif avahi-daemon[5274]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 17:39:18 Sisif avahi-daemon[5274]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 17:39:18 Sisif avahi-daemon[5274]: Registering new address record for 192.168.1.102 on eth1.IPv4.
Apr 30 17:39:21 Sisif avahi-daemon[5274]: Withdrawing address record for 192.168.1.102 on eth1.
Apr 30 17:39:21 Sisif avahi-daemon[5274]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 17:39:21 Sisif avahi-daemon[5274]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 17:39:21 Sisif avahi-autoipd(eth1)[7854]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 30 17:39:21 Sisif avahi-autoipd(eth1)[7854]: Successfully called chroot().
Apr 30 17:39:21 Sisif avahi-autoipd(eth1)[7854]: Successfully dropped root privileges.
Apr 30 17:39:21 Sisif avahi-autoipd(eth1)[7854]: Starting with address 169.254.4.188
Apr 30 17:39:26 Sisif avahi-autoipd(eth1)[7854]: Callout BIND, address 169.254.4.188 on interface eth1
Apr 30 17:39:26 Sisif avahi-daemon[5274]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 17:39:26 Sisif avahi-daemon[5274]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 17:39:26 Sisif avahi-daemon[5274]: Registering new address record for 169.254.4.188 on eth1.IPv4.
Apr 30 17:39:27 Sisif avahi-daemon[5274]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 17:39:27 Sisif avahi-daemon[5274]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 17:39:27 Sisif avahi-autoipd(eth1)[7854]: if_indextoname() failed: No such device or address
Apr 30 17:39:27 Sisif avahi-autoipd(eth1)[7854]: Callout STOP, address 169.254.4.188 on interface (null)
Apr 30 17:39:27 Sisif avahi-autoipd(eth1)[7855]: if_indextoname() failed: No such device or address
Apr 30 17:39:27 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 17:39:27 Sisif avahi-daemon[5274]: Withdrawing address record for 169.254.4.188 on eth1.
Apr 30 17:39:27 Sisif kernel: [  136.371973] ndiswrapper: device eth1 removed
Apr 30 17:39:27 Sisif kernel: [  136.372005] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 17:39:27 Sisif kernel: [  136.372109] usbcore: deregistering interface driver ndiswrapper
Apr 30 17:39:27 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 17:39:37 Sisif nmbd[5551]: [2008/04/30 17:39:37, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:39:37 Sisif nmbd[5551]:   Packet send failed to 169.254.255.255(138) ERRNO=Invalid argument 
Apr 30 17:40:37 Sisif nmbd[5551]: [2008/04/30 17:40:37, 0] nmbd/nmbd.c:reload_interfaces(239) 
Apr 30 17:40:37 Sisif nmbd[5551]:   reload_interfaces: No subnets to listen to. Waiting.. 
Apr 30 17:43:55 Sisif dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6427
Apr 30 17:43:55 Sisif dhclient: removed stale PID file
Apr 30 17:43:55 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:43:55 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:43:55 Sisif dhclient: All rights reserved.
Apr 30 17:43:55 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:43:55 Sisif dhclient: 
Apr 30 17:43:55 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:43:55 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6665
Apr 30 17:43:55 Sisif dhclient: removed stale PID file
Apr 30 17:43:55 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:43:55 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:43:55 Sisif dhclient: All rights reserved.
Apr 30 17:43:55 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:43:55 Sisif dhclient: 
Apr 30 17:43:55 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:43:55 Sisif dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Apr 30 17:43:55 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:43:55 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:43:55 Sisif dhclient: All rights reserved.
Apr 30 17:43:55 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:43:55 Sisif dhclient: 
Apr 30 17:43:56 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:43:57 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 17:43:57 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:43:57 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:43:57 Sisif dhclient: All rights reserved.
Apr 30 17:43:57 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:43:57 Sisif dhclient: 
Apr 30 17:43:58 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:44:31 Sisif dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Apr 30 17:44:31 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:44:31 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:44:31 Sisif dhclient: All rights reserved.
Apr 30 17:44:31 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:44:31 Sisif dhclient: 
Apr 30 17:44:33 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:44:34 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 17:44:34 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:44:34 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:44:34 Sisif dhclient: All rights reserved.
Apr 30 17:44:34 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:44:34 Sisif dhclient: 
Apr 30 17:44:35 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:44:38 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 30 17:44:38 Sisif dhclient: send_packet: No such device
Apr 30 17:44:41 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 30 17:44:41 Sisif dhclient: send_packet: No such device
Apr 30 17:44:44 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 30 17:44:44 Sisif dhclient: send_packet: No such device
Apr 30 17:44:50 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
Apr 30 17:44:50 Sisif dhclient: send_packet: No such device
Apr 30 17:45:03 Sisif init: tty4 main process (4671) killed by TERM signal
Apr 30 17:45:03 Sisif init: tty5 main process (4672) killed by TERM signal
Apr 30 17:45:03 Sisif init: tty2 main process (4674) killed by TERM signal
Apr 30 17:45:03 Sisif init: tty3 main process (4676) killed by TERM signal
Apr 30 17:45:03 Sisif init: tty6 main process (4678) killed by TERM signal
Apr 30 17:45:03 Sisif init: tty1 main process (6142) killed by TERM signal
Apr 30 17:45:03 Sisif kernel: [  470.344609] compiz.real[6389]: segfault at 00000078 eip 08055a6d esp bfc167d0 error 4
Apr 30 17:45:04 Sisif kernel: [  471.585564] gdm[5692]: segfault at 7672657f eip b78ae7e2 esp bfb265a0 error 6
Apr 30 17:45:04 Sisif avahi-daemon[5274]: Got SIGTERM, quitting.
Apr 30 17:45:06 Sisif rpc.statd[4510]: Caught signal 15, un-registering and exiting.
Apr 30 17:45:07 Sisif kernel: [  474.624760] ip6_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 17:45:08 Sisif mountd[5506]: Caught signal 15, un-registering and exiting.
Apr 30 17:45:08 Sisif kernel: [  477.848280] nfsd: last server has exited
Apr 30 17:45:08 Sisif kernel: [  477.848285] nfsd: unexporting all filesystems
Apr 30 17:45:08 Sisif exiting on signal 15
Apr 30 17:45:50 Sisif syslogd 1.5.0#1ubuntu1: restart.
Apr 30 17:45:50 Sisif kernel: Inspecting /boot/System.map-2.6.24-16-generic
Apr 30 17:45:50 Sisif kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Apr 30 17:45:50 Sisif kernel: Symbols match kernel version 2.6.24.
Apr 30 17:45:50 Sisif kernel: Loaded 21378 symbols from 98 modules.
Apr 30 17:45:50 Sisif kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Apr 30 17:45:50 Sisif kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 30 17:45:50 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 30 17:45:50 Sisif kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 30 17:45:50 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d3400 (usable)
Apr 30 17:45:50 Sisif kernel: [    0.000000]  BIOS-e820: 000000007f6d3400 - 0000000080000000 (reserved)
Apr 30 17:45:50 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Apr 30 17:45:50 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Apr 30 17:45:50 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 30 17:45:50 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Apr 30 17:45:50 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Apr 30 17:45:50 Sisif kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr 30 17:45:50 Sisif kernel: [    0.000000] 1142MB HIGHMEM available.
Apr 30 17:45:50 Sisif kernel: [    0.000000] 896MB LOWMEM available.
Apr 30 17:45:50 Sisif kernel: [    0.000000] Entering add_active_range(0, 0, 521939) 0 entries of 256 used
Apr 30 17:45:50 Sisif kernel: [    0.000000] Zone PFN ranges:
Apr 30 17:45:50 Sisif kernel: [    0.000000]   DMA             0 ->     4096
Apr 30 17:45:50 Sisif kernel: [    0.000000]   Normal       4096 ->   229376
Apr 30 17:45:50 Sisif kernel: [    0.000000]   HighMem    229376 ->   521939
Apr 30 17:45:50 Sisif kernel: [    0.000000] Movable zone start PFN for each node
Apr 30 17:45:50 Sisif kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 30 17:45:50 Sisif kernel: [    0.000000]     0:        0 ->   521939
Apr 30 17:45:50 Sisif kernel: [    0.000000] On node 0 totalpages: 521939
Apr 30 17:45:50 Sisif kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 30 17:45:50 Sisif kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 30 17:45:50 Sisif kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 30 17:45:50 Sisif kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Apr 30 17:45:50 Sisif kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Apr 30 17:45:50 Sisif kernel: [    0.000000]   HighMem zone: 2285 pages used for memmap
Apr 30 17:45:50 Sisif kernel: [    0.000000]   HighMem zone: 290278 pages, LIFO batch:31
Apr 30 17:45:50 Sisif kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 30 17:45:50 Sisif kernel: [    0.000000] DMI 2.4 present.
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: RSDT 7F6D39CD, 0040 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: FACP 7F6D4800, 0074 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: DSDT 7F6D5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: FACS 7F6E3C00, 0040
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: HPET 7F6D4F00, 0038 (r1 DELL    M07            1 ASL        61)
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: APIC 7F6D5000, 0068 (r1 DELL    M07     27D7060D ASL        47)
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: MCFG 7F6D4FC0, 003E (r16 DELL    M07     27D7060D ASL        61)
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: SLIC 7F6D509C, 0024 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: BOOT 7F6D4BC0, 0028 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: SSDT 7F6D3A0D, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 30 17:45:50 Sisif kernel: [    0.000000] Processor #0 6:14 APIC version 20
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 30 17:45:50 Sisif kernel: [    0.000000] Processor #1 6:14 APIC version 20
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 30 17:45:50 Sisif kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 30 17:45:50 Sisif kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 30 17:45:50 Sisif kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 30 17:45:50 Sisif kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 30 17:45:50 Sisif kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
Apr 30 17:45:50 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 30 17:45:50 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Apr 30 17:45:50 Sisif kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517862
Apr 30 17:45:50 Sisif kernel: [    0.000000] Kernel command line: root=UUID=35a5e031-c7e9-4597-9992-99d1d88d0eac ro quiet splash
Apr 30 17:45:50 Sisif kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Apr 30 17:45:50 Sisif kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Apr 30 17:45:50 Sisif kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 30 17:45:50 Sisif kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 30 17:45:50 Sisif kernel: [    0.000000] Initializing CPU#0
Apr 30 17:45:50 Sisif kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 30 17:45:50 Sisif kernel: [    0.000000] Detected 1729.044 MHz processor.
Apr 30 17:45:50 Sisif kernel: [    7.416694] Console: colour VGA+ 80x25
Apr 30 17:45:50 Sisif kernel: [    7.416697] console [tty0] enabled
Apr 30 17:45:50 Sisif kernel: [    7.417000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 30 17:45:50 Sisif kernel: [    7.417398] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 30 17:45:50 Sisif kernel: [    7.539502] Memory: 2057924k/2087756k available (2157k kernel code, 28552k reserved, 998k data, 364k init, 1170252k highmem)
Apr 30 17:45:50 Sisif kernel: [    7.539511] virtual kernel memory layout:
Apr 30 17:45:50 Sisif kernel: [    7.539512]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Apr 30 17:45:50 Sisif kernel: [    7.539513]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 30 17:45:50 Sisif kernel: [    7.539515]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Apr 30 17:45:50 Sisif kernel: [    7.539516]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 30 17:45:50 Sisif kernel: [    7.539517]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Apr 30 17:45:50 Sisif kernel: [    7.539519]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Apr 30 17:45:50 Sisif kernel: [    7.539520]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Apr 30 17:45:50 Sisif kernel: [    7.539523] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 30 17:45:50 Sisif kernel: [    7.539567] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 30 17:45:50 Sisif kernel: [    7.539717] hpet clockevent registered
Apr 30 17:45:50 Sisif kernel: [    7.619690] Calibrating delay using timer specific routine.. 3461.93 BogoMIPS (lpj=6923863)
Apr 30 17:45:50 Sisif kernel: [    7.619713] Security Framework initialized
Apr 30 17:45:50 Sisif kernel: [    7.619721] SELinux:  Disabled at boot.
Apr 30 17:45:50 Sisif kernel: [    7.619738] AppArmor: AppArmor initialized
Apr 30 17:45:50 Sisif kernel: [    7.619742] Failure registering capabilities with primary security module.
Apr 30 17:45:50 Sisif kernel: [    7.619751] Mount-cache hash table entries: 512
Apr 30 17:45:50 Sisif kernel: [    7.619891] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 17:45:50 Sisif kernel: [    7.619901] monitor/mwait feature present.
Apr 30 17:45:50 Sisif kernel: [    7.619902] using mwait in idle threads.
Apr 30 17:45:50 Sisif kernel: [    7.619907] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 17:45:50 Sisif kernel: [    7.619909] CPU: L2 cache: 1024K
Apr 30 17:45:50 Sisif kernel: [    7.619912] CPU: Physical Processor ID: 0
Apr 30 17:45:50 Sisif kernel: [    7.619914] CPU: Processor Core ID: 0
Apr 30 17:45:50 Sisif kernel: [    7.619916] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 17:45:50 Sisif kernel: [    7.619927] Compat vDSO mapped to ffffe000.
Apr 30 17:45:50 Sisif kernel: [    7.619940] Checking 'hlt' instruction... OK.
Apr 30 17:45:50 Sisif kernel: [    7.636089] SMP alternatives: switching to UP code
Apr 30 17:45:50 Sisif kernel: [    7.637929] Early unpacking initramfs... done
Apr 30 17:45:50 Sisif kernel: [    7.988116] ACPI: Core revision 20070126
Apr 30 17:45:50 Sisif kernel: [    7.988175] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 30 17:45:50 Sisif kernel: [    7.990889] CPU0: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 17:45:50 Sisif kernel: [    7.990907] SMP alternatives: switching to SMP code
Apr 30 17:45:50 Sisif kernel: [    7.991631] Booting processor 1/1 eip 3000
Apr 30 17:45:50 Sisif kernel: [   10.018064] Initializing CPU#1
Apr 30 17:45:50 Sisif kernel: [   10.097529] Calibrating delay using timer specific routine.. 3458.05 BogoMIPS (lpj=6916119)
Apr 30 17:45:50 Sisif kernel: [   10.097537] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 17:45:50 Sisif kernel: [   10.097542] monitor/mwait feature present.
Apr 30 17:45:50 Sisif kernel: [   10.097546] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 17:45:50 Sisif kernel: [   10.097548] CPU: L2 cache: 1024K
Apr 30 17:45:50 Sisif kernel: [   10.097550] CPU: Physical Processor ID: 0
Apr 30 17:45:50 Sisif kernel: [   10.097551] CPU: Processor Core ID: 1
Apr 30 17:45:50 Sisif kernel: [   10.097553] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 17:45:50 Sisif kernel: [    8.083932] CPU1: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 17:45:50 Sisif kernel: [    8.083956] Total of 2 processors activated (6919.99 BogoMIPS).
Apr 30 17:45:50 Sisif kernel: [    8.084154] ENABLING IO-APIC IRQs
Apr 30 17:45:50 Sisif kernel: [    8.084351] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 30 17:45:50 Sisif kernel: [    8.231544] checking TSC synchronization [CPU#0 -> CPU#1]:
Apr 30 17:45:50 Sisif kernel: [    8.251545] Measured 3483750686 cycles TSC warp between CPUs, turning off TSC clock.
Apr 30 17:45:50 Sisif kernel: [    8.251547] Marking TSC unstable due to: check_tsc_sync_source failed.
Apr 30 17:45:50 Sisif kernel: [    8.251562] Brought up 2 CPUs
Apr 30 17:45:50 Sisif kernel: [    8.251591] CPU0 attaching sched-domain:
Apr 30 17:45:50 Sisif kernel: [    8.251593]  domain 0: span 03
Apr 30 17:45:50 Sisif kernel: [    8.251595]   groups: 01 02
Apr 30 17:45:50 Sisif kernel: [    8.251598] CPU1 attaching sched-domain:
Apr 30 17:45:50 Sisif kernel: [    8.251600]  domain 0: span 03
Apr 30 17:45:50 Sisif kernel: [    8.251602]   groups: 02 01
Apr 30 17:45:50 Sisif kernel: [   10.265907] net_namespace: 64 bytes
Apr 30 17:45:50 Sisif kernel: [   10.265918] Booting paravirtualized kernel on bare hardware
Apr 30 17:45:50 Sisif kernel: [   10.266414] Time: 14:45:28  Date: 04/30/08
Apr 30 17:45:50 Sisif kernel: [   10.266444] NET: Registered protocol family 16
Apr 30 17:45:50 Sisif kernel: [   10.266662] EISA bus registered
Apr 30 17:45:50 Sisif kernel: [   10.266667] ACPI: bus type pci registered
Apr 30 17:45:50 Sisif kernel: [   10.295412] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=13
Apr 30 17:45:50 Sisif kernel: [   10.295414] PCI: Using configuration type 1
Apr 30 17:45:50 Sisif kernel: [   10.295416] Setting up standard PCI resources
Apr 30 17:45:50 Sisif kernel: [    8.287117] ACPI: EC: Look up EC in DSDT
Apr 30 17:45:50 Sisif kernel: [    8.291985] ACPI: Interpreter enabled
Apr 30 17:45:50 Sisif kernel: [    8.291989] ACPI: (supports S0 S3 S4 S5)
Apr 30 17:45:50 Sisif kernel: [    8.292003] ACPI: Using IOAPIC for interrupt routing
Apr 30 17:45:50 Sisif kernel: [    8.306052] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 30 17:45:50 Sisif kernel: [    8.306854] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 30 17:45:50 Sisif kernel: [    8.306859] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Apr 30 17:45:50 Sisif kernel: [    8.308037] PCI: Transparent bridge - 0000:00:1e.0
Apr 30 17:45:50 Sisif kernel: [    8.308077] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 30 17:45:50 Sisif kernel: [    8.308540] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr 30 17:45:50 Sisif kernel: [    8.308672] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 30 17:45:50 Sisif kernel: [    8.308795] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr 30 17:45:50 Sisif kernel: [    8.317143] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr 30 17:45:50 Sisif kernel: [    8.317254] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
Apr 30 17:45:50 Sisif kernel: [    8.317363] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr 30 17:45:50 Sisif kernel: [    8.317471] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Apr 30 17:45:50 Sisif kernel: [    8.317580] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 30 17:45:50 Sisif kernel: [    8.317691] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 30 17:45:50 Sisif kernel: [    8.317802] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Apr 30 17:45:50 Sisif kernel: [    8.317913] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Apr 30 17:45:50 Sisif kernel: [    8.318069] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 30 17:45:50 Sisif kernel: [    8.318104] pnp: PnP ACPI init
Apr 30 17:45:50 Sisif kernel: [    8.318112] ACPI: bus type pnp registered
Apr 30 17:45:50 Sisif kernel: [    8.334395] pnpacpi: exceeded the max number of mem resources: 12
Apr 30 17:45:50 Sisif kernel: [    8.347252] pnp: PnP ACPI: found 12 devices
Apr 30 17:45:50 Sisif kernel: [    8.347254] ACPI: ACPI bus type pnp unregistered
Apr 30 17:45:50 Sisif kernel: [    8.347258] PnPBIOS: Disabled by ACPI PNP
Apr 30 17:45:50 Sisif kernel: [    8.347555] PCI: Using ACPI for IRQ routing
Apr 30 17:45:50 Sisif kernel: [    8.347559] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 30 17:45:50 Sisif kernel: [    8.403360] NET: Registered protocol family 8
Apr 30 17:45:50 Sisif kernel: [    8.403362] NET: Registered protocol family 20
Apr 30 17:45:50 Sisif kernel: [    8.403401] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 30 17:45:50 Sisif kernel: [    8.403406] hpet0: 3 64-bit timers, 14318180 Hz
Apr 30 17:45:50 Sisif kernel: [    8.404449] AppArmor: AppArmor Filesystem Enabled
Apr 30 17:45:50 Sisif kernel: [    8.407352] Time: hpet clocksource has been installed.
Apr 30 17:45:50 Sisif kernel: [    8.407373] Switched to high resolution mode on CPU 0
Apr 30 17:45:50 Sisif kernel: [   10.421532] Switched to high resolution mode on CPU 1
Apr 30 17:45:50 Sisif kernel: [    8.419348] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419352] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419355] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419358] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419361] system 00:00: iomem range 0x100000-0x7f6d33ff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419364] system 00:00: iomem range 0x7f6d3400-0x7f6fffff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419367] system 00:00: iomem range 0x7f700000-0x7f7fffff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419371] system 00:00: iomem range 0x7f700000-0x7fefffff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419374] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419377] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419381] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419384] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419391] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419394] system 00:02: ioport range 0x1000-0x1005 has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419397] system 00:02: ioport range 0x1008-0x100f has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419404] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419407] system 00:03: ioport range 0x1006-0x1007 has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419410] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419413] system 00:03: ioport range 0x1060-0x107f has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419416] system 00:03: ioport range 0x1080-0x10bf has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419419] system 00:03: ioport range 0x10c0-0x10df has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419422] system 00:03: ioport range 0x1010-0x102f has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419424] system 00:03: ioport range 0x809-0x809 has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419433] system 00:08: ioport range 0xc80-0xcff could not be reserved
Apr 30 17:45:50 Sisif kernel: [    8.419436] system 00:08: ioport range 0x910-0x91f has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419438] system 00:08: ioport range 0x920-0x92f has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419441] system 00:08: ioport range 0xcb0-0xcbf has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419444] system 00:08: ioport range 0x930-0x97f has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.419452] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Apr 30 17:45:50 Sisif kernel: [    8.449915] PCI: Bridge: 0000:00:1c.0
Apr 30 17:45:50 Sisif kernel: [    8.449917]   IO window: disabled.
Apr 30 17:45:50 Sisif kernel: [    8.449924]   MEM window: efd00000-efdfffff
Apr 30 17:45:50 Sisif kernel: [    8.449928]   PREFETCH window: disabled.
Apr 30 17:45:50 Sisif kernel: [    8.449934] PCI: Bridge: 0000:00:1c.3
Apr 30 17:45:50 Sisif kernel: [    8.449937]   IO window: d000-dfff
Apr 30 17:45:50 Sisif kernel: [    8.449943]   MEM window: efa00000-efcfffff
Apr 30 17:45:50 Sisif kernel: [    8.449948]   PREFETCH window: e0000000-e01fffff
Apr 30 17:45:50 Sisif kernel: [    8.449955] PCI: Bridge: 0000:00:1e.0
Apr 30 17:45:50 Sisif kernel: [    8.449956]   IO window: disabled.
Apr 30 17:45:50 Sisif kernel: [    8.449962]   MEM window: ef900000-ef9fffff
Apr 30 17:45:50 Sisif kernel: [    8.449966]   PREFETCH window: disabled.
Apr 30 17:45:50 Sisif kernel: [    8.450000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:45:50 Sisif kernel: [    8.450008] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 17:45:50 Sisif kernel: [    8.450032] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Apr 30 17:45:50 Sisif kernel: [    8.450039] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 17:45:50 Sisif kernel: [    8.450053] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 30 17:45:50 Sisif kernel: [    8.450066] NET: Registered protocol family 2
Apr 30 17:45:50 Sisif kernel: [    8.487343] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 30 17:45:50 Sisif kernel: [    8.487585] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 30 17:45:50 Sisif kernel: [    8.488328] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 30 17:45:50 Sisif kernel: [    8.488704] TCP: Hash tables configured (established 131072 bind 65536)
Apr 30 17:45:50 Sisif kernel: [    8.488709] TCP reno registered
Apr 30 17:45:50 Sisif kernel: [    8.499453] checking if image is initramfs... it is
Apr 30 17:45:50 Sisif kernel: [    9.192386] Freeing initrd memory: 7267k freed
Apr 30 17:45:50 Sisif kernel: [    9.192558] Simple Boot Flag at 0x79 set to 0x1
Apr 30 17:45:50 Sisif kernel: [   11.207345] audit: initializing netlink socket (disabled)
Apr 30 17:45:50 Sisif kernel: [   11.207359] audit(1209566728.528:1): initialized
Apr 30 17:45:50 Sisif kernel: [    9.193557] highmem bounce pool size: 64 pages
Apr 30 17:45:50 Sisif kernel: [   11.209764] VFS: Disk quotas dquot_6.5.1
Apr 30 17:45:50 Sisif kernel: [    9.195812] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 30 17:45:50 Sisif kernel: [    9.195958] io scheduler noop registered
Apr 30 17:45:50 Sisif kernel: [    9.195961] io scheduler anticipatory registered
Apr 30 17:45:50 Sisif kernel: [    9.195964] io scheduler deadline registered
Apr 30 17:45:50 Sisif kernel: [    9.195976] io scheduler cfq registered (default)
Apr 30 17:45:50 Sisif kernel: [    9.195988] Boot video device is 0000:00:02.0
Apr 30 17:45:50 Sisif kernel: [    9.196206] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 17:45:50 Sisif kernel: [    9.196266] assign_interrupt_mode Found MSI capability
Apr 30 17:45:50 Sisif kernel: [    9.196317] Allocate Port Service[0000:00:1c.0:pcie00]
Apr 30 17:45:50 Sisif kernel: [    9.196357] Allocate Port Service[0000:00:1c.0:pcie02]
Apr 30 17:45:50 Sisif kernel: [    9.196467] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 17:45:50 Sisif kernel: [    9.196525] assign_interrupt_mode Found MSI capability
Apr 30 17:45:50 Sisif kernel: [    9.196572] Allocate Port Service[0000:00:1c.3:pcie00]
Apr 30 17:45:50 Sisif kernel: [    9.196609] Allocate Port Service[0000:00:1c.3:pcie02]
Apr 30 17:45:50 Sisif kernel: [    9.196901] isapnp: Scanning for PnP cards...
Apr 30 17:45:50 Sisif kernel: [    9.551012] isapnp: No Plug & Play device found
Apr 30 17:45:50 Sisif kernel: [   11.595410] Real Time Clock Driver v1.12ac
Apr 30 17:45:50 Sisif kernel: [   11.595572] hpet_resources: 0xfed00000 is busy
Apr 30 17:45:50 Sisif kernel: [   11.595629] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 30 17:45:50 Sisif kernel: [   11.596925] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 30 17:45:50 Sisif kernel: [   11.596998] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 30 17:45:50 Sisif kernel: [   11.597107] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 30 17:45:50 Sisif kernel: [    9.586034] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 30 17:45:50 Sisif kernel: [    9.586041] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 30 17:45:50 Sisif kernel: [   11.617010] mice: PS/2 mouse device common for all mice
Apr 30 17:45:50 Sisif kernel: [   11.617152] EISA: Probing bus 0 at eisa.0
Apr 30 17:45:50 Sisif kernel: [   11.617221] EISA: Mainboard UO_FFFF detected.
Apr 30 17:45:50 Sisif kernel: [   11.617264] Cannot allocate resource for EISA slot 1
Apr 30 17:45:50 Sisif kernel: [   11.617295] EISA: Detected 0 cards.
Apr 30 17:45:50 Sisif kernel: [   11.617298] cpuidle: using governor ladder
Apr 30 17:45:50 Sisif kernel: [   11.617300] cpuidle: using governor menu
Apr 30 17:45:50 Sisif kernel: [   11.617393] NET: Registered protocol family 1
Apr 30 17:45:50 Sisif kernel: [   11.617426] Using IPI No-Shortcut mode
Apr 30 17:45:50 Sisif kernel: [   11.617459] registered taskstats version 1
Apr 30 17:45:50 Sisif kernel: [   11.617576]   Magic number: 4:961:789
Apr 30 17:45:50 Sisif kernel: [   11.617684] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 30 17:45:50 Sisif kernel: [   11.617687] EDD information not available.
Apr 30 17:45:50 Sisif kernel: [   11.617870] Freeing unused kernel memory: 364k freed
Apr 30 17:45:50 Sisif kernel: [   11.620239] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 30 17:45:50 Sisif kernel: [   10.821696] fuse init (API version 7.9)
Apr 30 17:45:50 Sisif kernel: [   10.843104] ACPI: SSDT 7F6D4134, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Apr 30 17:45:50 Sisif kernel: [   10.843297] ACPI: SSDT 7F6D3EE9, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Apr 30 17:45:50 Sisif kernel: [   10.843868] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 17:45:50 Sisif kernel: [   10.843873] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 30 17:45:50 Sisif kernel: [   10.844110] ACPI: SSDT 7F6D4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Apr 30 17:45:50 Sisif kernel: [   10.844284] ACPI: SSDT 7F6D40AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Apr 30 17:45:50 Sisif kernel: [   12.858997] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 17:45:50 Sisif kernel: [   12.859003] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 30 17:45:50 Sisif kernel: [   12.864321] ACPI: Thermal Zone [THM] (42 C)
Apr 30 17:45:50 Sisif kernel: [   11.226360] usbcore: registered new interface driver usbfs
Apr 30 17:45:50 Sisif kernel: [   11.226388] usbcore: registered new interface driver hub
Apr 30 17:45:50 Sisif kernel: [   11.226528] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:45:50 Sisif kernel: [   11.226548] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 17:45:50 Sisif kernel: [   11.226614] usbcore: registered new device driver usb
Apr 30 17:45:50 Sisif kernel: [   11.228549] USB Universal Host Controller Interface driver v3.0
Apr 30 17:45:50 Sisif kernel: [   11.286127] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Apr 30 17:45:50 Sisif kernel: [   11.286177] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 17:45:50 Sisif kernel: [   11.286189] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 30 17:45:50 Sisif kernel: [   11.286194] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 30 17:45:50 Sisif kernel: [   11.286467] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr 30 17:45:50 Sisif kernel: [   11.286506] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
Apr 30 17:45:50 Sisif kernel: [   11.286650] usb usb1: configuration #1 chosen from 1 choice
Apr 30 17:45:50 Sisif kernel: [   11.286674] hub 1-0:1.0: USB hub found
Apr 30 17:45:50 Sisif kernel: [   11.286680] hub 1-0:1.0: 2 ports detected
Apr 30 17:45:50 Sisif kernel: [   13.306965] SCSI subsystem initialized
Apr 30 17:45:50 Sisif kernel: [   13.353605] libata version 3.00 loaded.
Apr 30 17:45:50 Sisif kernel: [   11.390072] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
Apr 30 17:45:50 Sisif kernel: [   11.390087] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 30 17:45:50 Sisif kernel: [   11.390092] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 30 17:45:50 Sisif kernel: [   11.390115] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr 30 17:45:50 Sisif kernel: [   11.390150] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bf60
Apr 30 17:45:50 Sisif kernel: [   11.390271] usb usb2: configuration #1 chosen from 1 choice
Apr 30 17:45:50 Sisif kernel: [   11.390296] hub 2-0:1.0: USB hub found
Apr 30 17:45:50 Sisif kernel: [   11.390301] hub 2-0:1.0: 2 ports detected
Apr 30 17:45:50 Sisif kernel: [   11.494018] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
Apr 30 17:45:50 Sisif kernel: [   11.494037] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 30 17:45:50 Sisif kernel: [   11.494044] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 30 17:45:50 Sisif kernel: [   11.494069] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr 30 17:45:50 Sisif kernel: [   11.494103] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000bf40
Apr 30 17:45:50 Sisif kernel: [   11.494220] usb usb3: configuration #1 chosen from 1 choice
Apr 30 17:45:50 Sisif kernel: [   11.494246] hub 3-0:1.0: USB hub found
Apr 30 17:45:50 Sisif kernel: [   11.494251] hub 3-0:1.0: 2 ports detected
Apr 30 17:45:50 Sisif kernel: [   13.612003] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
Apr 30 17:45:50 Sisif kernel: [   13.612016] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Apr 30 17:45:50 Sisif kernel: [   13.612021] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Apr 30 17:45:50 Sisif kernel: [   13.612048] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Apr 30 17:45:50 Sisif kernel: [   13.612085] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000bf20
Apr 30 17:45:50 Sisif kernel: [   13.612214] usb usb4: configuration #1 chosen from 1 choice
Apr 30 17:45:50 Sisif kernel: [   13.612240] hub 4-0:1.0: USB hub found
Apr 30 17:45:50 Sisif kernel: [   13.612246] hub 4-0:1.0: 2 ports detected
Apr 30 17:45:50 Sisif kernel: [   13.717102] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 17:45:50 Sisif kernel: [   13.717120] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 30 17:45:50 Sisif kernel: [   13.717125] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 30 17:45:50 Sisif kernel: [   13.717153] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Apr 30 17:45:50 Sisif kernel: [   13.721076] ehci_hcd 0000:00:1d.7: debug port 1
Apr 30 17:45:50 Sisif kernel: [   13.721084] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr 30 17:45:50 Sisif kernel: [   13.721091] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80000
Apr 30 17:45:50 Sisif kernel: [   13.736832] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 30 17:45:50 Sisif kernel: [   13.736962] usb usb5: configuration #1 chosen from 1 choice
Apr 30 17:45:50 Sisif kernel: [   13.736988] hub 5-0:1.0: USB hub found
Apr 30 17:45:50 Sisif kernel: [   13.736996] hub 5-0:1.0: 8 ports detected
Apr 30 17:45:50 Sisif kernel: [   11.826984] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 17:45:50 Sisif kernel: [   13.903831] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 17:45:50 Sisif kernel: [   13.903864] b44.c:v2.0
Apr 30 17:45:50 Sisif kernel: [   13.924096] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 17:45:50 Sisif kernel: [   13.924372] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Apr 30 17:45:50 Sisif kernel: [   13.977081] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 30 17:45:50 Sisif kernel: [   11.971878] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 17:45:50 Sisif kernel: [   11.971918] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 17:45:50 Sisif kernel: [   11.971932] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Apr 30 17:45:50 Sisif kernel: [   11.976170] ata_piix 0000:00:1f.2: version 2.12
Apr 30 17:45:50 Sisif kernel: [   11.976177] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Apr 30 17:45:50 Sisif kernel: [   11.976199] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 17:45:50 Sisif kernel: [   11.976237] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 17:45:50 Sisif kernel: [   11.976702] scsi0 : ata_piix
Apr 30 17:45:50 Sisif kernel: [   11.977337] scsi1 : ata_piix
Apr 30 17:45:50 Sisif kernel: [   11.978149] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Apr 30 17:45:50 Sisif kernel: [   11.978152] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Apr 30 17:45:50 Sisif kernel: [   12.138416] ata1.00: ATA-7: ST9120822AS, 3.CDD, max UDMA/133
Apr 30 17:45:50 Sisif kernel: [   12.138421] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
Apr 30 17:45:50 Sisif kernel: [   12.155071] ata1.00: configured for UDMA/133
Apr 30 17:45:50 Sisif kernel: [   14.511974] ata2.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1B, max UDMA/33
Apr 30 17:45:50 Sisif kernel: [   14.703820] ata2.00: configured for UDMA/33
Apr 30 17:45:50 Sisif kernel: [   12.689948] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.CD PQ: 0 ANSI: 5
Apr 30 17:45:50 Sisif kernel: [   12.692408] scsi 1:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
Apr 30 17:45:50 Sisif kernel: [   12.700083] Driver 'sd' needs updating - please use bus_type methods
Apr 30 17:45:50 Sisif kernel: [   12.700171] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 17:45:50 Sisif kernel: [   12.700186] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 17:45:50 Sisif kernel: [   12.700189] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 17:45:50 Sisif kernel: [   12.700206] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 17:45:50 Sisif kernel: [   12.700257] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 17:45:50 Sisif kernel: [   12.700268] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 17:45:50 Sisif kernel: [   12.700270] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 17:45:50 Sisif kernel: [   12.700287] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 17:45:50 Sisif kernel: [   12.700291]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Apr 30 17:45:50 Sisif kernel: [   12.788209]  sda1 sda2 sda3
Apr 30 17:45:50 Sisif kernel: [   12.800494] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 30 17:45:50 Sisif kernel: [   12.806126] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 30 17:45:50 Sisif kernel: [   12.806147] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 30 17:45:50 Sisif kernel: [   14.832659] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr 30 17:45:50 Sisif kernel: [   14.832664] Uniform CD-ROM driver Revision: 3.20
Apr 30 17:45:50 Sisif kernel: [   14.832720] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 30 17:45:50 Sisif kernel: [   15.255475] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc00026e60070]
Apr 30 17:45:50 Sisif kernel: [   15.337029] Attempting manual resume
Apr 30 17:45:50 Sisif kernel: [   15.337033] swsusp: Resume From Partition 8:2
Apr 30 17:45:50 Sisif kernel: [   15.337034] PM: Checking swsusp image.
Apr 30 17:45:50 Sisif kernel: [   15.337714] PM: Resume from disk failed.
Apr 30 17:45:50 Sisif kernel: [   15.379041] kjournald starting.  Commit interval 5 seconds
Apr 30 17:45:50 Sisif kernel: [   13.365018] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 17:45:50 Sisif kernel: [   21.328799] Linux agpgart interface v0.102
Apr 30 17:45:50 Sisif kernel: [   21.474271] agpgart: Detected an Intel 945GM Chipset.
Apr 30 17:45:50 Sisif kernel: [   21.474850] agpgart: Detected 7932K stolen memory.
Apr 30 17:45:50 Sisif kernel: [   21.492100] agpgart: AGP aperture is 256M @ 0xd0000000
Apr 30 17:45:50 Sisif kernel: [   21.565176] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 30 17:45:50 Sisif kernel: [   21.603496] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 30 17:45:50 Sisif kernel: [   23.772586] ACPI: Battery Slot [BAT0] (battery present)
Apr 30 17:45:50 Sisif kernel: [   21.817540] ACPI: AC Adapter [AC] (on-line)
Apr 30 17:45:50 Sisif kernel: [   21.849079] input: Lid Switch as /devices/virtual/input/input2
Apr 30 17:45:50 Sisif kernel: [   21.849496] ACPI: Lid Switch [LID]
Apr 30 17:45:50 Sisif kernel: [   21.849567] input: Power Button (CM) as /devices/virtual/input/input3
Apr 30 17:45:50 Sisif kernel: [   21.868914] ACPI: Power Button (CM) [PBTN]
Apr 30 17:45:50 Sisif kernel: [   21.869030] input: Sleep Button (CM) as /devices/virtual/input/input4
Apr 30 17:45:50 Sisif kernel: [   21.900886] ACPI: Sleep Button (CM) [SBTN]
Apr 30 17:45:50 Sisif kernel: [   21.900997] ACPI: WMI-Acer: Mapper loaded
Apr 30 17:45:50 Sisif kernel: [   22.011167] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input5
Apr 30 17:45:50 Sisif kernel: [   22.032837] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr 30 17:45:50 Sisif kernel: [   22.040841] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
Apr 30 17:45:50 Sisif kernel: [   22.052833] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Apr 30 17:45:50 Sisif kernel: [   22.053053] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input7
Apr 30 17:45:50 Sisif kernel: [   22.088806] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Apr 30 17:45:50 Sisif kernel: [   22.945732] iTCO_vendor_support: vendor-support=0
Apr 30 17:45:50 Sisif kernel: [   22.984891] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Apr 30 17:45:50 Sisif kernel: [   22.984996] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Apr 30 17:45:50 Sisif kernel: [   22.985036] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 30 17:45:50 Sisif kernel: [   23.053438] intel_rng: FWH not detected
Apr 30 17:45:50 Sisif kernel: [   23.292402] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
Apr 30 17:45:50 Sisif kernel: [   23.292433] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 30 17:45:50 Sisif kernel: [   23.408194] sdhci: Secure Digital Host Controller Interface driver
Apr 30 17:45:50 Sisif kernel: [   23.408198] sdhci: Copyright(c) Pierre Ossman
Apr 30 17:45:50 Sisif kernel: [   23.408240] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
Apr 30 17:45:50 Sisif kernel: [   23.408266] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
Apr 30 17:45:50 Sisif kernel: [   23.408345] mmc0: SDHCI at 0xef9fd500 irq 23 DMA
Apr 30 17:45:50 Sisif kernel: [   23.468325] input: PC Speaker as /devices/platform/pcspkr/input/input8
Apr 30 17:45:50 Sisif kernel: [   23.643849] b43-phy0: Broadcom 4311 WLAN found
Apr 30 17:45:50 Sisif kernel: [   23.710742] phy0: Selected rate control algorithm 'simple'
Apr 30 17:45:50 Sisif kernel: [   24.176234] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
Apr 30 17:45:50 Sisif kernel: [   26.226178] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
Apr 30 17:45:50 Sisif kernel: [   24.259663] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Apr 30 17:45:50 Sisif kernel: [   24.783050] udev: renamed network interface wlan0 to eth1
Apr 30 17:45:50 Sisif kernel: [   24.883755] input: b43-phy0 as /devices/virtual/input/input10
Apr 30 17:45:50 Sisif kernel: [   25.179982] lp: driver loaded but no devices found
Apr 30 17:45:50 Sisif kernel: [   25.302503] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
Apr 30 17:45:50 Sisif kernel: [   25.883387] EXT3 FS on sda1, internal journal
Apr 30 17:45:50 Sisif kernel: [   26.303299] Registered led device: b43-phy0:tx
Apr 30 17:45:50 Sisif kernel: [   26.303323] Registered led device: b43-phy0:rx
Apr 30 17:45:50 Sisif kernel: [   26.303348] Registered led device: b43-phy0:radio
Apr 30 17:45:50 Sisif kernel: [   26.416754] NET: Registered protocol family 17
Apr 30 17:45:50 Sisif kernel: [   29.151908] kjournald starting.  Commit interval 5 seconds
Apr 30 17:45:50 Sisif kernel: [   27.138059] EXT3 FS on sda3, internal journal
Apr 30 17:45:50 Sisif kernel: [   27.138065] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 17:45:50 Sisif kernel: [   27.727675] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 17:45:50 Sisif kernel: [   29.115610] RPC: Registered udp transport module.
Apr 30 17:45:50 Sisif kernel: [   29.115615] RPC: Registered tcp transport module.
Apr 30 17:45:50 Sisif kernel: [   29.761368] No dock devices found.
Apr 30 17:45:51 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 30 17:45:51 Sisif avahi-daemon[5291]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Apr 30 17:45:51 Sisif avahi-daemon[5291]: Successfully dropped root privileges.
Apr 30 17:45:51 Sisif avahi-daemon[5291]: avahi-daemon 0.6.22 starting up.
Apr 30 17:45:51 Sisif avahi-daemon[5291]: Successfully called chroot().
Apr 30 17:45:51 Sisif avahi-daemon[5291]: Successfully dropped remaining capabilities.
Apr 30 17:45:51 Sisif avahi-daemon[5291]: No service file found in /etc/avahi/services.
Apr 30 17:45:51 Sisif avahi-daemon[5291]: Network interface enumeration completed.
Apr 30 17:45:51 Sisif avahi-daemon[5291]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 30 17:45:51 Sisif avahi-daemon[5291]: Server startup complete. Host name is Sisif.local. Local service cookie is 3779655278.
Apr 30 17:45:51 Sisif kernel: [   34.020682] ppdev: user-space parallel port driver
Apr 30 17:45:51 Sisif dhclient: DHCPREQUEST of 192.168.0.118 on eth0 to 255.255.255.255 port 67
Apr 30 17:45:52 Sisif kernel: [   32.186180] audit(1209566752.171:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5325 profile="/usr/sbin/cupsd" namespace="default"
Apr 30 17:45:52 Sisif kernel: [   32.234513] apm: BIOS not found.
Apr 30 17:45:53 Sisif kernel: [   33.652509] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Apr 30 17:45:53 Sisif exportfs[5498]: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.10.2:/home/itch/Blonda".   Assuming default behaviour ('no_subtree_check').   NOTE: this default has changed since nfs-utils version 1.0.x 
Apr 30 17:45:53 Sisif kernel: [   33.899330] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Apr 30 17:45:53 Sisif kernel: [   33.915132] NFSD: starting 90-second grace period
Apr 30 17:45:55 Sisif nmbd[5568]: [2008/04/30 17:45:55, 0] nmbd/nmbd_subnetdb.c:create_subnets(190) 
Apr 30 17:45:55 Sisif nmbd[5568]:   create_subnets: No local interfaces ! 
Apr 30 17:45:55 Sisif nmbd[5568]: [2008/04/30 17:45:55, 0] nmbd/nmbd_subnetdb.c:create_subnets(191) 
Apr 30 17:45:55 Sisif nmbd[5568]:   create_subnets: Waiting for an interface to appear ... 
Apr 30 17:45:56 Sisif dhcdbd: Started up.
Apr 30 17:45:56 Sisif hcid[5645]: Bluetooth HCI daemon
Apr 30 17:45:56 Sisif kernel: [   36.848730] Bluetooth: Core ver 2.11
Apr 30 17:45:56 Sisif kernel: [   36.849585] NET: Registered protocol family 31
Apr 30 17:45:56 Sisif kernel: [   36.849593] Bluetooth: HCI device and connection manager initialized
Apr 30 17:45:56 Sisif kernel: [   36.849600] Bluetooth: HCI socket layer initialized
Apr 30 17:45:56 Sisif hcid[5645]: Starting SDP server
Apr 30 17:45:57 Sisif kernel: [   37.023917] Bluetooth: L2CAP ver 2.9
Apr 30 17:45:57 Sisif kernel: [   37.023922] Bluetooth: L2CAP socket layer initialized
Apr 30 17:45:57 Sisif hcid[5645]: Created local server at unix:abstract=/var/run/dbus-inCwYM11Ji,guid=0238482b24ef56437954814948188625
Apr 30 17:45:57 Sisif kernel: [   37.124433] Bluetooth: RFCOMM socket layer initialized
Apr 30 17:45:57 Sisif kernel: [   37.124453] Bluetooth: RFCOMM TTY layer initialized
Apr 30 17:45:57 Sisif kernel: [   37.124458] Bluetooth: RFCOMM ver 1.8
Apr 30 17:45:57 Sisif audio[5667]: Bluetooth Audio daemon
Apr 30 17:45:57 Sisif input[5689]: Bluetooth Input daemon
Apr 30 17:45:57 Sisif audio[5667]: Unix socket created: 5
Apr 30 17:45:57 Sisif audio[5667]: audio.conf: Key file does not have key 'Enable'
Apr 30 17:45:57 Sisif audio[5667]: audio.conf: Key file does not have key 'Disable'
Apr 30 17:45:57 Sisif audio[5667]: add_service_record: got record id 0x10000
Apr 30 17:45:57 Sisif audio[5667]: audio.conf: Key file does not have key 'Disable'
Apr 30 17:45:57 Sisif audio[5667]: audio.conf: Key file does not have group 'A2DP'
Apr 30 17:45:57 Sisif last message repeated 3 times
Apr 30 17:45:57 Sisif audio[5667]: SEP 0x806d578 registered: type:0 codec:0 seid:1
Apr 30 17:45:57 Sisif audio[5667]: add_service_record: got record id 0x10001
Apr 30 17:45:57 Sisif audio[5667]: add_service_record: got record id 0x10002
Apr 30 17:45:57 Sisif audio[5667]: add_service_record: got record id 0x10003
Apr 30 17:45:57 Sisif audio[5667]: Registered manager path:/org/bluez/audio
Apr 30 17:45:57 Sisif input[5689]: Registered input manager path:/org/bluez/input
Apr 30 17:45:58 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr 30 17:45:59 Sisif ntpd[5740]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 17:45:59 Sisif ntpd[5741]: precision = 1.000 usec
Apr 30 17:45:59 Sisif kernel: [   39.902649] NET: Registered protocol family 10
Apr 30 17:45:59 Sisif kernel: [   39.903975] lo: Disabled Privacy Extensions
Apr 30 17:45:59 Sisif kernel: [   39.906516] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 30 17:45:59 Sisif kernel: [   39.908660] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:45:59 Sisif ntpd[5741]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 17:45:59 Sisif ntpd[5741]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 17:45:59 Sisif ntpd[5741]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 17:45:59 Sisif ntpd[5741]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 17:45:59 Sisif ntpd[5741]: kernel time sync status 0040
Apr 30 17:46:00 Sisif ntpd[5741]: frequency initialized -57.973 PPM from /var/lib/ntp/ntp.drift
Apr 30 17:46:00 Sisif kernel: [   40.844969] [drm] Initialized drm 1.1.0 20060810
Apr 30 17:46:00 Sisif kernel: [   40.903579] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:46:00 Sisif kernel: [   40.903597] PCI: Setting latency timer of device 0000:00:02.0 to 64
Apr 30 17:46:00 Sisif kernel: [   42.919813] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr 30 17:46:01 Sisif anacron[5809]: Anacron 2.3 started on 2008-04-30
Apr 30 17:46:01 Sisif anacron[5809]: Normal exit (0 jobs run)
Apr 30 17:46:01 Sisif /usr/sbin/cron[5840]: (CRON) INFO (pidfile fd = 3)
Apr 30 17:46:01 Sisif /usr/sbin/cron[5841]: (CRON) STARTUP (fork ok)
Apr 30 17:46:01 Sisif /usr/sbin/cron[5841]: (CRON) INFO (Running @reboot jobs)
Apr 30 17:46:02 Sisif ntpd_initres[5759]: host name not found: ntp2a.mcc.ac.uk
Apr 30 17:46:02 Sisif ntpd_initres[5759]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 17:46:02 Sisif ntpd_initres[5759]: host name not found: ntp.landau.ac.ru
Apr 30 17:46:02 Sisif ntpd_initres[5759]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 17:46:02 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 17:46:02 Sisif dhclient: receive_packet failed on eth0: Network is down
Apr 30 17:46:02 Sisif kernel: [   44.810682] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 17:46:02 Sisif kernel: [   44.828033] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 17:46:02 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 17:46:02 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:46:02 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:46:02 Sisif dhclient: All rights reserved.
Apr 30 17:46:02 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:46:02 Sisif dhclient: 
Apr 30 17:46:02 Sisif kernel: [   42.960000] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 17:46:02 Sisif dhclient: Bind socket to interface: No such device
Apr 30 17:46:03 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 30 17:46:03 Sisif dhclient: send_packet: No such device
Apr 30 17:46:03 Sisif kernel: [   43.027318] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 17:46:03 Sisif kernel: [   43.028110] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:46:03 Sisif kernel: [   43.028177] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 17:46:03 Sisif kernel: [   43.033090] ndiswrapper: using IRQ 16
Apr 30 17:46:03 Sisif kernel: [   43.391497] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 17:46:03 Sisif kernel: [   43.392898] eth1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 17:46:03 Sisif kernel: [   45.407552] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 17:46:03 Sisif kernel: [   45.407642] udev: renamed network interface wlan0 to eth1
Apr 30 17:46:03 Sisif kernel: [   43.399593] ndiswrapper (wrap_procfs_add_ndis_device:399): eth1 already registered?
Apr 30 17:46:03 Sisif kernel: [   43.403405] usbcore: registered new interface driver ndiswrapper
Apr 30 17:46:03 Sisif kernel: [   45.421044] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:46:03 Sisif kernel: [   43.441320] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:46:03 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 17:46:03 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:46:03 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:46:03 Sisif dhclient: All rights reserved.
Apr 30 17:46:03 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:46:03 Sisif dhclient: 
Apr 30 17:46:03 Sisif kernel: [   43.546096] ndiswrapper: device eth1 removed
Apr 30 17:46:03 Sisif kernel: [   43.546708] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 17:46:03 Sisif kernel: [   43.547490] usbcore: deregistering interface driver ndiswrapper
Apr 30 17:46:03 Sisif kernel: [   43.587579] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 17:46:03 Sisif kernel: [   43.597327] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 17:46:03 Sisif kernel: [   43.598558] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 17:46:03 Sisif kernel: [   43.598637] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 17:46:03 Sisif kernel: [   43.603979] ndiswrapper: using IRQ 16
Apr 30 17:46:03 Sisif kernel: [   43.963410] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 17:46:03 Sisif kernel: [   43.963517] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 17:46:03 Sisif kernel: [   45.979824] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 17:46:03 Sisif kernel: [   45.979914] udev: renamed network interface wlan0 to eth1
Apr 30 17:46:03 Sisif kernel: [   43.969661] usbcore: registered new interface driver ndiswrapper
Apr 30 17:46:04 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:46:04 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:46:04 Sisif dhclient: Sending on   Socket/fallback
Apr 30 17:46:04 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 30 17:46:04 Sisif dhclient: send_packet: Network is down
Apr 30 17:46:04 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 17:46:07 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr 30 17:46:07 Sisif dhclient: send_packet: No such device
Apr 30 17:46:09 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr 30 17:46:09 Sisif dhclient: send_packet: Network is down
Apr 30 17:46:11 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr 30 17:46:11 Sisif dhclient: send_packet: Network is down
Apr 30 17:46:17 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr 30 17:46:17 Sisif dhclient: send_packet: No such device
Apr 30 17:46:21 Sisif hcid[5645]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Apr 30 17:46:21 Sisif hcid[5645]: Default authorization agent (:1.18, /org/bluez/auth) registered
Apr 30 17:46:22 Sisif dhclient: No DHCPOFFERS received.
Apr 30 17:46:22 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 17:46:22 Sisif kernel: [   64.058901] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:46:22 Sisif avahi-autoipd(eth1)[6372]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 30 17:46:22 Sisif avahi-autoipd(eth1)[6372]: Successfully called chroot().
Apr 30 17:46:22 Sisif avahi-autoipd(eth1)[6372]: Successfully dropped root privileges.
Apr 30 17:46:22 Sisif avahi-autoipd(eth1)[6372]: Starting with address 169.254.4.188
Apr 30 17:46:25 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr 30 17:46:28 Sisif kernel: [   68.214755] CPU0 attaching NULL sched-domain.
Apr 30 17:46:28 Sisif kernel: [   68.214764] CPU1 attaching NULL sched-domain.
Apr 30 17:46:28 Sisif kernel: [   68.232307] CPU0 attaching sched-domain:
Apr 30 17:46:28 Sisif kernel: [   68.232311]  domain 0: span 03
Apr 30 17:46:28 Sisif kernel: [   68.232313]   groups: 01 02
Apr 30 17:46:28 Sisif kernel: [   68.232317] CPU1 attaching sched-domain:
Apr 30 17:46:28 Sisif kernel: [   68.232319]  domain 0: span 03
Apr 30 17:46:28 Sisif kernel: [   68.232320]   groups: 02 01
Apr 30 17:46:28 Sisif avahi-autoipd(eth1)[6372]: Callout BIND, address 169.254.4.188 on interface eth1
Apr 30 17:46:28 Sisif avahi-daemon[5291]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 17:46:28 Sisif avahi-daemon[5291]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 17:46:28 Sisif avahi-daemon[5291]: Registering new address record for 169.254.4.188 on eth1.IPv4.
Apr 30 17:46:32 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Apr 30 17:46:32 Sisif dhclient: send_packet: No such device
Apr 30 17:46:32 Sisif avahi-autoipd(eth1)[6372]: Successfully claimed IP address 169.254.4.188
Apr 30 17:46:32 Sisif ntpd[5741]: ntpd exiting on signal 15
Apr 30 17:46:34 Sisif dhclient: No DHCPOFFERS received.
Apr 30 17:46:34 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 17:46:34 Sisif dhclient: No DHCPOFFERS received.
Apr 30 17:46:34 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 17:46:35 Sisif avahi-daemon[5291]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 17:46:35 Sisif avahi-daemon[5291]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 17:46:35 Sisif avahi-autoipd(eth1)[6372]: SIOCSIFFLAGS failed: Permission denied
Apr 30 17:46:35 Sisif avahi-autoipd(eth1)[6372]: Callout STOP, address 169.254.4.188 on interface eth1
Apr 30 17:46:35 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 17:46:35 Sisif avahi-daemon[5291]: Withdrawing address record for 169.254.4.188 on eth1.
Apr 30 17:46:35 Sisif avahi-autoipd(eth1)[6373]: client: RTNETLINK answers: No such process
Apr 30 17:46:35 Sisif kernel: [   75.624180] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:46:36 Sisif kernel: [   76.022413] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 17:46:36 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 17:46:36 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 17:46:36 Sisif dhclient: All rights reserved.
Apr 30 17:46:36 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 17:46:36 Sisif dhclient: 
Apr 30 17:46:36 Sisif kernel: [   78.720829] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 30 17:46:37 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:46:37 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 17:46:37 Sisif dhclient: Sending on   Socket/fallback
Apr 30 17:46:37 Sisif avahi-daemon[5291]: Registering new address record for fe80::219:7eff:fea0:3d2a on eth1.*.
Apr 30 17:46:37 Sisif ntpdate[6622]: can't find host ntp2a.mcc.ac.uk 
Apr 30 17:46:37 Sisif ntpdate[6622]: can't find host ntp.landau.ac.ru 
Apr 30 17:46:37 Sisif ntpdate[6622]: no servers can be used, exiting
Apr 30 17:46:37 Sisif ntpd[6864]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 17:46:37 Sisif ntpd[6865]: precision = 1.000 usec
Apr 30 17:46:37 Sisif ntpd[6865]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 17:46:37 Sisif ntpd[6865]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 17:46:37 Sisif ntpd[6865]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 17:46:37 Sisif ntpd[6865]: Listening on interface #3 eth1, fe80::219:7eff:fea0:3d2a#123 Enabled
Apr 30 17:46:37 Sisif ntpd[6865]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Apr 30 17:46:37 Sisif ntpd[6865]: kernel time sync status 0040
Apr 30 17:46:37 Sisif ntpd[6865]: frequency initialized -57.973 PPM from /var/lib/ntp/ntp.drift
Apr 30 17:46:39 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 17:46:39 Sisif dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
Apr 30 17:46:39 Sisif avahi-daemon[5291]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 17:46:39 Sisif avahi-daemon[5291]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 17:46:39 Sisif avahi-daemon[5291]: Registering new address record for 192.168.1.102 on eth1.IPv4.
Apr 30 17:46:39 Sisif ntpd[6865]: Cannot find existing interface for address 130.88.202.49
Apr 30 17:46:39 Sisif ntpd_initres[6866]: ntpd indicates no data available!
Apr 30 17:46:40 Sisif dhclient: bound to 192.168.1.102 -- renewal in 40484 seconds.
Apr 30 17:46:40 Sisif ntpd_initres[6866]: host name not found: ntp.landau.ac.ru
Apr 30 17:46:40 Sisif ntpd_initres[6866]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 17:46:40 Sisif ntpdate[6769]: can't find host ntp2a.mcc.ac.uk 
Apr 30 17:46:40 Sisif ntpdate[6769]: can't find host ntp.landau.ac.ru 
Apr 30 17:46:40 Sisif ntpdate[6769]: no servers can be used, exiting
Apr 30 17:46:46 Sisif kernel: [   88.747559] eth1: no IPv6 routers present
Apr 30 17:47:40 Sisif ntpd[6865]: Cannot find existing interface for address 130.88.202.49
Apr 30 17:47:40 Sisif ntpd_initres[6866]: ntpd indicates no data available!
Apr 30 17:47:44 Sisif nmbd[5568]: [2008/04/30 17:47:44, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 17:47:44 Sisif nmbd[5568]:   Packet send failed to 169.254.255.255(138) ERRNO=Invalid argument 
Apr 30 17:48:40 Sisif ntpd[6865]: Cannot find existing interface for address 130.88.202.49
Apr 30 17:48:40 Sisif ntpd_initres[6866]: ntpd indicates no data available!
Apr 30 17:49:40 Sisif ntpd[6865]: Cannot find existing interface for address 130.88.202.49
Apr 30 17:49:40 Sisif ntpd_initres[6866]: ntpd indicates no data available!
Apr 30 17:50:40 Sisif ntpd[6865]: Cannot find existing interface for address 130.88.202.49
Apr 30 17:50:40 Sisif ntpd_initres[6866]: ntpd indicates no data available!
Apr 30 17:51:38 Sisif ntpd[6865]: Listening on interface #5 eth1, 192.168.1.102#123 Enabled
Apr 30 17:52:19 Sisif nmbd[5568]: [2008/04/30 17:52:19, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Apr 30 17:52:19 Sisif nmbd[5568]:   ***** 
Apr 30 17:52:19 Sisif nmbd[5568]:    
Apr 30 17:52:19 Sisif nmbd[5568]:   Samba name server SISIF is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.102 
Apr 30 17:52:19 Sisif nmbd[5568]:    
Apr 30 17:52:19 Sisif nmbd[5568]:   ***** 
Apr 30 17:56:10 Sisif ntpd[6865]: synchronized to 130.88.202.49, stratum 2
Apr 30 17:56:10 Sisif ntpd[6865]: time reset +0.265383 s
Apr 30 17:56:10 Sisif ntpd[6865]: kernel time sync status change 0001
Apr 30 18:01:22 Sisif ntpd[6865]: synchronized to 130.88.202.49, stratum 2
Apr 30 18:07:41 Sisif gnome-power-manager: (itch) GNOME interactive logout. Reason: The power button has been pressed.
Apr 30 18:07:48 Sisif init: tty4 main process (4688) killed by TERM signal
Apr 30 18:07:48 Sisif init: tty5 main process (4689) killed by TERM signal
Apr 30 18:07:48 Sisif init: tty2 main process (4691) killed by TERM signal
Apr 30 18:07:48 Sisif init: tty3 main process (4693) killed by TERM signal
Apr 30 18:07:48 Sisif init: tty1 main process (6160) killed by TERM signal
Apr 30 18:07:48 Sisif init: tty6 main process (4695) killed by TERM signal
Apr 30 18:07:48 Sisif kernel: [ 1349.995395] gdm[5709]: segfault at 7672657f eip b78297e2 esp bfaa8f90 error 6
Apr 30 18:07:48 Sisif avahi-daemon[5291]: Got SIGTERM, quitting.
Apr 30 18:07:48 Sisif avahi-daemon[5291]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 18:07:49 Sisif nmbd[5568]: [2008/04/30 18:07:49, 0] nmbd/nmbd.c:terminate(58) 
Apr 30 18:07:49 Sisif nmbd[5568]:   Got SIGTERM: going down... 
Apr 30 18:07:51 Sisif rpc.statd[4527]: Caught signal 15, un-registering and exiting.
Apr 30 18:07:52 Sisif kernel: [ 1351.820001] ip6_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 18:07:53 Sisif mountd[5523]: Caught signal 15, un-registering and exiting.
Apr 30 18:07:53 Sisif kernel: [ 1353.066288] nfsd: last server has exited
Apr 30 18:07:53 Sisif kernel: [ 1353.066293] nfsd: unexporting all filesystems
Apr 30 18:07:53 Sisif exiting on signal 15
Apr 30 23:14:23 Sisif syslogd 1.5.0#1ubuntu1: restart.
Apr 30 23:14:23 Sisif kernel: Inspecting /boot/System.map-2.6.24-16-generic
Apr 30 23:14:23 Sisif kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Apr 30 23:14:23 Sisif kernel: Symbols match kernel version 2.6.24.
Apr 30 23:14:24 Sisif kernel: Loaded 21402 symbols from 99 modules.
Apr 30 23:14:24 Sisif kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Apr 30 23:14:24 Sisif kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 30 23:14:24 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 30 23:14:24 Sisif kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 30 23:14:24 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d3400 (usable)
Apr 30 23:14:24 Sisif kernel: [    0.000000]  BIOS-e820: 000000007f6d3400 - 0000000080000000 (reserved)
Apr 30 23:14:24 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Apr 30 23:14:24 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Apr 30 23:14:24 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 30 23:14:24 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Apr 30 23:14:24 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Apr 30 23:14:24 Sisif kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr 30 23:14:24 Sisif kernel: [    0.000000] 1142MB HIGHMEM available.
Apr 30 23:14:24 Sisif kernel: [    0.000000] 896MB LOWMEM available.
Apr 30 23:14:24 Sisif kernel: [    0.000000] Entering add_active_range(0, 0, 521939) 0 entries of 256 used
Apr 30 23:14:24 Sisif kernel: [    0.000000] Zone PFN ranges:
Apr 30 23:14:24 Sisif kernel: [    0.000000]   DMA             0 ->     4096
Apr 30 23:14:24 Sisif kernel: [    0.000000]   Normal       4096 ->   229376
Apr 30 23:14:24 Sisif kernel: [    0.000000]   HighMem    229376 ->   521939
Apr 30 23:14:24 Sisif kernel: [    0.000000] Movable zone start PFN for each node
Apr 30 23:14:24 Sisif kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 30 23:14:24 Sisif kernel: [    0.000000]     0:        0 ->   521939
Apr 30 23:14:24 Sisif kernel: [    0.000000] On node 0 totalpages: 521939
Apr 30 23:14:24 Sisif kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 30 23:14:24 Sisif kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 30 23:14:24 Sisif kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 30 23:14:24 Sisif kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Apr 30 23:14:24 Sisif kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Apr 30 23:14:24 Sisif kernel: [    0.000000]   HighMem zone: 2285 pages used for memmap
Apr 30 23:14:24 Sisif kernel: [    0.000000]   HighMem zone: 290278 pages, LIFO batch:31
Apr 30 23:14:24 Sisif kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 30 23:14:24 Sisif kernel: [    0.000000] DMI 2.4 present.
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: RSDT 7F6D39CD, 0040 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: FACP 7F6D4800, 0074 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: DSDT 7F6D5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: FACS 7F6E3C00, 0040
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: HPET 7F6D4F00, 0038 (r1 DELL    M07            1 ASL        61)
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: APIC 7F6D5000, 0068 (r1 DELL    M07     27D7060D ASL        47)
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: MCFG 7F6D4FC0, 003E (r16 DELL    M07     27D7060D ASL        61)
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: SLIC 7F6D509C, 0024 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: BOOT 7F6D4BC0, 0028 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: SSDT 7F6D3A0D, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 30 23:14:24 Sisif kernel: [    0.000000] Processor #0 6:14 APIC version 20
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 30 23:14:24 Sisif kernel: [    0.000000] Processor #1 6:14 APIC version 20
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 30 23:14:24 Sisif kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 30 23:14:24 Sisif kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 30 23:14:24 Sisif kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 30 23:14:24 Sisif kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 30 23:14:24 Sisif kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
Apr 30 23:14:24 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 30 23:14:24 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Apr 30 23:14:24 Sisif kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517862
Apr 30 23:14:24 Sisif kernel: [    0.000000] Kernel command line: root=UUID=35a5e031-c7e9-4597-9992-99d1d88d0eac ro quiet splash
Apr 30 23:14:24 Sisif kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Apr 30 23:14:24 Sisif kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Apr 30 23:14:24 Sisif kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 30 23:14:24 Sisif kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 30 23:14:24 Sisif kernel: [    0.000000] Initializing CPU#0
Apr 30 23:14:24 Sisif kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 30 23:14:24 Sisif kernel: [    0.000000] Detected 1729.062 MHz processor.
Apr 30 23:14:24 Sisif kernel: [    6.735036] Console: colour VGA+ 80x25
Apr 30 23:14:24 Sisif kernel: [    6.735040] console [tty0] enabled
Apr 30 23:14:24 Sisif kernel: [    6.735342] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 30 23:14:24 Sisif kernel: [    6.735740] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 30 23:14:24 Sisif kernel: [    6.857742] Memory: 2057924k/2087756k available (2157k kernel code, 28552k reserved, 998k data, 364k init, 1170252k highmem)
Apr 30 23:14:24 Sisif kernel: [    6.857751] virtual kernel memory layout:
Apr 30 23:14:24 Sisif kernel: [    6.857752]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Apr 30 23:14:24 Sisif kernel: [    6.857753]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 30 23:14:24 Sisif kernel: [    6.857754]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Apr 30 23:14:24 Sisif kernel: [    6.857756]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 30 23:14:24 Sisif kernel: [    6.857757]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Apr 30 23:14:24 Sisif kernel: [    6.857758]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Apr 30 23:14:24 Sisif kernel: [    6.857760]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Apr 30 23:14:24 Sisif kernel: [    6.857763] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 30 23:14:24 Sisif kernel: [    6.857809] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 30 23:14:24 Sisif kernel: [    6.857957] hpet clockevent registered
Apr 30 23:14:24 Sisif kernel: [    6.937929] Calibrating delay using timer specific routine.. 3461.92 BogoMIPS (lpj=6923854)
Apr 30 23:14:24 Sisif kernel: [    6.937954] Security Framework initialized
Apr 30 23:14:24 Sisif kernel: [    6.937963] SELinux:  Disabled at boot.
Apr 30 23:14:24 Sisif kernel: [    6.937979] AppArmor: AppArmor initialized
Apr 30 23:14:24 Sisif kernel: [    6.937985] Failure registering capabilities with primary security module.
Apr 30 23:14:24 Sisif kernel: [    6.937993] Mount-cache hash table entries: 512
Apr 30 23:14:24 Sisif kernel: [    6.938130] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 23:14:24 Sisif kernel: [    6.938141] monitor/mwait feature present.
Apr 30 23:14:24 Sisif kernel: [    6.938143] using mwait in idle threads.
Apr 30 23:14:24 Sisif kernel: [    6.938147] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 23:14:24 Sisif kernel: [    6.938150] CPU: L2 cache: 1024K
Apr 30 23:14:24 Sisif kernel: [    6.938153] CPU: Physical Processor ID: 0
Apr 30 23:14:24 Sisif kernel: [    6.938155] CPU: Processor Core ID: 0
Apr 30 23:14:24 Sisif kernel: [    6.938157] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 23:14:24 Sisif kernel: [    6.938166] Compat vDSO mapped to ffffe000.
Apr 30 23:14:24 Sisif kernel: [    6.938180] Checking 'hlt' instruction... OK.
Apr 30 23:14:24 Sisif kernel: [    6.954332] SMP alternatives: switching to UP code
Apr 30 23:14:24 Sisif kernel: [    6.956174] Early unpacking initramfs... done
Apr 30 23:14:24 Sisif kernel: [    7.306386] ACPI: Core revision 20070126
Apr 30 23:14:24 Sisif kernel: [    7.306445] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 30 23:14:24 Sisif kernel: [    7.309128] CPU0: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 23:14:24 Sisif kernel: [    7.309148] SMP alternatives: switching to SMP code
Apr 30 23:14:24 Sisif kernel: [    7.309876] Booting processor 1/1 eip 3000
Apr 30 23:14:24 Sisif kernel: [    9.394676] Initializing CPU#1
Apr 30 23:14:24 Sisif kernel: [    9.474552] Calibrating delay using timer specific routine.. 3458.03 BogoMIPS (lpj=6916073)
Apr 30 23:14:24 Sisif kernel: [    9.474561] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 23:14:24 Sisif kernel: [    9.474566] monitor/mwait feature present.
Apr 30 23:14:24 Sisif kernel: [    9.474570] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 23:14:24 Sisif kernel: [    9.474572] CPU: L2 cache: 1024K
Apr 30 23:14:24 Sisif kernel: [    9.474574] CPU: Physical Processor ID: 0
Apr 30 23:14:24 Sisif kernel: [    9.474576] CPU: Processor Core ID: 1
Apr 30 23:14:24 Sisif kernel: [    9.474577] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 23:14:24 Sisif kernel: [    7.402250] CPU1: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 23:14:24 Sisif kernel: [    7.402274] Total of 2 processors activated (6919.96 BogoMIPS).
Apr 30 23:14:24 Sisif kernel: [    7.402474] ENABLING IO-APIC IRQs
Apr 30 23:14:24 Sisif kernel: [    7.402671] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 30 23:14:24 Sisif kernel: [    7.549785] checking TSC synchronization [CPU#0 -> CPU#1]:
Apr 30 23:14:24 Sisif kernel: [    7.569784] Measured 3585429575 cycles TSC warp between CPUs, turning off TSC clock.
Apr 30 23:14:24 Sisif kernel: [    7.569787] Marking TSC unstable due to: check_tsc_sync_source failed.
Apr 30 23:14:24 Sisif kernel: [    7.569804] Brought up 2 CPUs
Apr 30 23:14:24 Sisif kernel: [    7.569831] CPU0 attaching sched-domain:
Apr 30 23:14:24 Sisif kernel: [    7.569833]  domain 0: span 03
Apr 30 23:14:24 Sisif kernel: [    7.569835]   groups: 01 02
Apr 30 23:14:24 Sisif kernel: [    7.569838] CPU1 attaching sched-domain:
Apr 30 23:14:24 Sisif kernel: [    7.569840]  domain 0: span 03
Apr 30 23:14:24 Sisif kernel: [    7.569842]   groups: 02 01
Apr 30 23:14:24 Sisif kernel: [    9.642930] net_namespace: 64 bytes
Apr 30 23:14:24 Sisif kernel: [    9.642940] Booting paravirtualized kernel on bare hardware
Apr 30 23:14:24 Sisif kernel: [    9.643440] Time: 20:14:02  Date: 04/30/08
Apr 30 23:14:24 Sisif kernel: [    9.643471] NET: Registered protocol family 16
Apr 30 23:14:24 Sisif kernel: [    9.643695] EISA bus registered
Apr 30 23:14:24 Sisif kernel: [    9.643700] ACPI: bus type pci registered
Apr 30 23:14:24 Sisif kernel: [    9.672431] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=13
Apr 30 23:14:24 Sisif kernel: [    9.672433] PCI: Using configuration type 1
Apr 30 23:14:24 Sisif kernel: [    9.672436] Setting up standard PCI resources
Apr 30 23:14:24 Sisif kernel: [    7.605356] ACPI: EC: Look up EC in DSDT
Apr 30 23:14:24 Sisif kernel: [    7.610271] ACPI: Interpreter enabled
Apr 30 23:14:24 Sisif kernel: [    7.610274] ACPI: (supports S0 S3 S4 S5)
Apr 30 23:14:24 Sisif kernel: [    7.610288] ACPI: Using IOAPIC for interrupt routing
Apr 30 23:14:24 Sisif kernel: [    7.624342] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 30 23:14:24 Sisif kernel: [    7.625144] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 30 23:14:24 Sisif kernel: [    7.625149] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Apr 30 23:14:24 Sisif kernel: [    7.626397] PCI: Transparent bridge - 0000:00:1e.0
Apr 30 23:14:24 Sisif kernel: [    7.626437] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 30 23:14:24 Sisif kernel: [    7.626897] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr 30 23:14:24 Sisif kernel: [    7.627032] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 30 23:14:24 Sisif kernel: [    7.627153] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr 30 23:14:24 Sisif kernel: [    7.635559] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr 30 23:14:24 Sisif kernel: [    7.635672] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
Apr 30 23:14:24 Sisif kernel: [    7.635780] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr 30 23:14:24 Sisif kernel: [    7.635888] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Apr 30 23:14:24 Sisif kernel: [    7.635998] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 30 23:14:24 Sisif kernel: [    7.636108] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 30 23:14:24 Sisif kernel: [    7.636219] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Apr 30 23:14:24 Sisif kernel: [    7.636329] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Apr 30 23:14:24 Sisif kernel: [    7.636488] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 30 23:14:24 Sisif kernel: [    7.636524] pnp: PnP ACPI init
Apr 30 23:14:24 Sisif kernel: [    7.636532] ACPI: bus type pnp registered
Apr 30 23:14:24 Sisif kernel: [    7.652795] pnpacpi: exceeded the max number of mem resources: 12
Apr 30 23:14:24 Sisif kernel: [    7.665651] pnp: PnP ACPI: found 12 devices
Apr 30 23:14:24 Sisif kernel: [    7.665653] ACPI: ACPI bus type pnp unregistered
Apr 30 23:14:24 Sisif kernel: [    7.665657] PnPBIOS: Disabled by ACPI PNP
Apr 30 23:14:24 Sisif kernel: [    9.738752] PCI: Using ACPI for IRQ routing
Apr 30 23:14:24 Sisif kernel: [    9.738756] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 30 23:14:24 Sisif kernel: [    9.814549] NET: Registered protocol family 8
Apr 30 23:14:24 Sisif kernel: [    9.814551] NET: Registered protocol family 20
Apr 30 23:14:24 Sisif kernel: [    9.814588] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 30 23:14:24 Sisif kernel: [    9.814593] hpet0: 3 64-bit timers, 14318180 Hz
Apr 30 23:14:24 Sisif kernel: [    9.815632] AppArmor: AppArmor Filesystem Enabled
Apr 30 23:14:24 Sisif kernel: [    7.745585] Time: hpet clocksource has been installed.
Apr 30 23:14:24 Sisif kernel: [    7.745607] Switched to high resolution mode on CPU 0
Apr 30 23:14:24 Sisif kernel: [    9.818546] Switched to high resolution mode on CPU 1
Apr 30 23:14:24 Sisif kernel: [    7.758585] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758588] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758591] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758594] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758597] system 00:00: iomem range 0x100000-0x7f6d33ff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758601] system 00:00: iomem range 0x7f6d3400-0x7f6fffff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758604] system 00:00: iomem range 0x7f700000-0x7f7fffff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758607] system 00:00: iomem range 0x7f700000-0x7fefffff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758611] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758614] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758617] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758620] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758627] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758630] system 00:02: ioport range 0x1000-0x1005 has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758633] system 00:02: ioport range 0x1008-0x100f has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758640] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758643] system 00:03: ioport range 0x1006-0x1007 has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758646] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758649] system 00:03: ioport range 0x1060-0x107f has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758652] system 00:03: ioport range 0x1080-0x10bf has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758655] system 00:03: ioport range 0x10c0-0x10df has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758658] system 00:03: ioport range 0x1010-0x102f has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758661] system 00:03: ioport range 0x809-0x809 has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758671] system 00:08: ioport range 0xc80-0xcff could not be reserved
Apr 30 23:14:24 Sisif kernel: [    7.758674] system 00:08: ioport range 0x910-0x91f has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758677] system 00:08: ioport range 0x920-0x92f has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758680] system 00:08: ioport range 0xcb0-0xcbf has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758683] system 00:08: ioport range 0x930-0x97f has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.758692] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Apr 30 23:14:24 Sisif kernel: [    7.789164] PCI: Bridge: 0000:00:1c.0
Apr 30 23:14:24 Sisif kernel: [    7.789166]   IO window: disabled.
Apr 30 23:14:24 Sisif kernel: [    7.789172]   MEM window: efd00000-efdfffff
Apr 30 23:14:24 Sisif kernel: [    7.789177]   PREFETCH window: disabled.
Apr 30 23:14:24 Sisif kernel: [    7.789183] PCI: Bridge: 0000:00:1c.3
Apr 30 23:14:24 Sisif kernel: [    7.789186]   IO window: d000-dfff
Apr 30 23:14:24 Sisif kernel: [    7.789192]   MEM window: efa00000-efcfffff
Apr 30 23:14:24 Sisif kernel: [    7.789197]   PREFETCH window: e0000000-e01fffff
Apr 30 23:14:24 Sisif kernel: [    7.789204] PCI: Bridge: 0000:00:1e.0
Apr 30 23:14:24 Sisif kernel: [    7.789205]   IO window: disabled.
Apr 30 23:14:24 Sisif kernel: [    7.789211]   MEM window: ef900000-ef9fffff
Apr 30 23:14:24 Sisif kernel: [    7.789215]   PREFETCH window: disabled.
Apr 30 23:14:24 Sisif kernel: [    7.789250] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 23:14:24 Sisif kernel: [    7.789257] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 23:14:24 Sisif kernel: [    7.789282] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Apr 30 23:14:24 Sisif kernel: [    7.789288] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 23:14:24 Sisif kernel: [    7.789302] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 30 23:14:24 Sisif kernel: [    7.789315] NET: Registered protocol family 2
Apr 30 23:14:24 Sisif kernel: [    7.833572] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 30 23:14:24 Sisif kernel: [    7.833816] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 30 23:14:24 Sisif kernel: [    7.834563] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 30 23:14:24 Sisif kernel: [    7.834941] TCP: Hash tables configured (established 131072 bind 65536)
Apr 30 23:14:24 Sisif kernel: [    7.834945] TCP reno registered
Apr 30 23:14:24 Sisif kernel: [    7.845679] checking if image is initramfs... it is
Apr 30 23:14:24 Sisif kernel: [    8.538381] Freeing initrd memory: 7267k freed
Apr 30 23:14:24 Sisif kernel: [    8.538552] Simple Boot Flag at 0x79 set to 0x1
Apr 30 23:14:24 Sisif kernel: [   10.612108] audit: initializing netlink socket (disabled)
Apr 30 23:14:24 Sisif kernel: [   10.612124] audit(1209586442.556:1): initialized
Apr 30 23:14:24 Sisif kernel: [    8.539541] highmem bounce pool size: 64 pages
Apr 30 23:14:24 Sisif kernel: [    8.541691] VFS: Disk quotas dquot_6.5.1
Apr 30 23:14:24 Sisif kernel: [    8.541776] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 30 23:14:24 Sisif kernel: [    8.541921] io scheduler noop registered
Apr 30 23:14:24 Sisif kernel: [    8.541923] io scheduler anticipatory registered
Apr 30 23:14:24 Sisif kernel: [    8.541925] io scheduler deadline registered
Apr 30 23:14:24 Sisif kernel: [    8.541937] io scheduler cfq registered (default)
Apr 30 23:14:24 Sisif kernel: [    8.541948] Boot video device is 0000:00:02.0
Apr 30 23:14:24 Sisif kernel: [    8.542163] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 23:14:24 Sisif kernel: [    8.542226] assign_interrupt_mode Found MSI capability
Apr 30 23:14:24 Sisif kernel: [    8.542277] Allocate Port Service[0000:00:1c.0:pcie00]
Apr 30 23:14:24 Sisif kernel: [    8.542319] Allocate Port Service[0000:00:1c.0:pcie02]
Apr 30 23:14:24 Sisif kernel: [    8.542427] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 23:14:24 Sisif kernel: [    8.542486] assign_interrupt_mode Found MSI capability
Apr 30 23:14:24 Sisif kernel: [    8.542532] Allocate Port Service[0000:00:1c.3:pcie00]
Apr 30 23:14:24 Sisif kernel: [    8.542571] Allocate Port Service[0000:00:1c.3:pcie02]
Apr 30 23:14:24 Sisif kernel: [    8.542855] isapnp: Scanning for PnP cards...
Apr 30 23:14:24 Sisif kernel: [    8.896991] isapnp: No Plug & Play device found
Apr 30 23:14:24 Sisif kernel: [    8.926893] Real Time Clock Driver v1.12ac
Apr 30 23:14:24 Sisif kernel: [    8.927058] hpet_resources: 0xfed00000 is busy
Apr 30 23:14:24 Sisif kernel: [    8.927114] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 30 23:14:24 Sisif kernel: [    8.928405] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 30 23:14:24 Sisif kernel: [    8.928479] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 30 23:14:24 Sisif kernel: [    8.928585] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 30 23:14:24 Sisif kernel: [    8.931598] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 30 23:14:24 Sisif kernel: [    8.931603] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 30 23:14:24 Sisif kernel: [    8.953089] mice: PS/2 mouse device common for all mice
Apr 30 23:14:24 Sisif kernel: [    8.953219] EISA: Probing bus 0 at eisa.0
Apr 30 23:14:24 Sisif kernel: [    8.953287] EISA: Mainboard UO_FFFF detected.
Apr 30 23:14:24 Sisif kernel: [    8.953332] Cannot allocate resource for EISA slot 1
Apr 30 23:14:24 Sisif kernel: [    8.953363] EISA: Detected 0 cards.
Apr 30 23:14:24 Sisif kernel: [    8.953366] cpuidle: using governor ladder
Apr 30 23:14:24 Sisif kernel: [    8.953368] cpuidle: using governor menu
Apr 30 23:14:24 Sisif kernel: [    8.953461] NET: Registered protocol family 1
Apr 30 23:14:24 Sisif kernel: [    8.953503] Using IPI No-Shortcut mode
Apr 30 23:14:24 Sisif kernel: [    8.953537] registered taskstats version 1
Apr 30 23:14:24 Sisif kernel: [    8.953660]   Magic number: 4:532:246
Apr 30 23:14:24 Sisif kernel: [    8.953685]   hash matches device ttyw2
Apr 30 23:14:24 Sisif kernel: [    8.953780] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 30 23:14:24 Sisif kernel: [    8.953783] EDD information not available.
Apr 30 23:14:24 Sisif kernel: [    8.953951] Freeing unused kernel memory: 364k freed
Apr 30 23:14:24 Sisif kernel: [   11.028681] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 30 23:14:24 Sisif kernel: [   10.172524] fuse init (API version 7.9)
Apr 30 23:14:24 Sisif kernel: [   10.194019] ACPI: SSDT 7F6D4134, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Apr 30 23:14:24 Sisif kernel: [   10.194210] ACPI: SSDT 7F6D3EE9, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Apr 30 23:14:24 Sisif kernel: [   10.194786] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 23:14:24 Sisif kernel: [   10.194791] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 30 23:14:24 Sisif kernel: [   10.195013] ACPI: SSDT 7F6D4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Apr 30 23:14:24 Sisif kernel: [   10.195185] ACPI: SSDT 7F6D40AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Apr 30 23:14:24 Sisif kernel: [   12.268674] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 23:14:24 Sisif kernel: [   12.268679] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 30 23:14:24 Sisif kernel: [   12.273925] ACPI: Thermal Zone [THM] (25 C)
Apr 30 23:14:24 Sisif kernel: [   12.629986] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 23:14:24 Sisif kernel: [   12.630008] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 23:14:24 Sisif kernel: [   12.648529] usbcore: registered new interface driver usbfs
Apr 30 23:14:24 Sisif kernel: [   12.648552] usbcore: registered new interface driver hub
Apr 30 23:14:24 Sisif kernel: [   12.648579] usbcore: registered new device driver usb
Apr 30 23:14:24 Sisif kernel: [   12.649771] USB Universal Host Controller Interface driver v3.0
Apr 30 23:14:24 Sisif kernel: [   12.698160] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Apr 30 23:14:24 Sisif kernel: [   12.698207] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 23:14:24 Sisif kernel: [   12.698219] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 30 23:14:24 Sisif kernel: [   12.698224] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 30 23:14:24 Sisif kernel: [   12.698493] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr 30 23:14:24 Sisif kernel: [   12.698530] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
Apr 30 23:14:24 Sisif kernel: [   12.698671] usb usb1: configuration #1 chosen from 1 choice
Apr 30 23:14:24 Sisif kernel: [   12.698696] hub 1-0:1.0: USB hub found
Apr 30 23:14:24 Sisif kernel: [   12.698702] hub 1-0:1.0: 2 ports detected
Apr 30 23:14:24 Sisif kernel: [   12.700989] SCSI subsystem initialized
Apr 30 23:14:24 Sisif kernel: [   12.743476] libata version 3.00 loaded.
Apr 30 23:14:24 Sisif kernel: [   12.802087] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
Apr 30 23:14:24 Sisif kernel: [   12.802101] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 30 23:14:24 Sisif kernel: [   12.802106] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 30 23:14:24 Sisif kernel: [   12.802130] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr 30 23:14:24 Sisif kernel: [   12.802165] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bf60
Apr 30 23:14:24 Sisif kernel: [   12.802284] usb usb2: configuration #1 chosen from 1 choice
Apr 30 23:14:24 Sisif kernel: [   12.802308] hub 2-0:1.0: USB hub found
Apr 30 23:14:24 Sisif kernel: [   12.802314] hub 2-0:1.0: 2 ports detected
Apr 30 23:14:24 Sisif kernel: [   12.906068] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
Apr 30 23:14:24 Sisif kernel: [   12.906082] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 30 23:14:24 Sisif kernel: [   12.906086] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 30 23:14:24 Sisif kernel: [   12.906112] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr 30 23:14:24 Sisif kernel: [   12.906146] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000bf40
Apr 30 23:14:24 Sisif kernel: [   12.906268] usb usb3: configuration #1 chosen from 1 choice
Apr 30 23:14:24 Sisif kernel: [   12.906292] hub 3-0:1.0: USB hub found
Apr 30 23:14:24 Sisif kernel: [   12.906299] hub 3-0:1.0: 2 ports detected
Apr 30 23:14:24 Sisif kernel: [   10.937186] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
Apr 30 23:14:24 Sisif kernel: [   10.937199] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Apr 30 23:14:24 Sisif kernel: [   10.937204] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Apr 30 23:14:24 Sisif kernel: [   10.937230] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Apr 30 23:14:24 Sisif kernel: [   10.937265] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000bf20
Apr 30 23:14:24 Sisif kernel: [   10.937390] usb usb4: configuration #1 chosen from 1 choice
Apr 30 23:14:24 Sisif kernel: [   10.937419] hub 4-0:1.0: USB hub found
Apr 30 23:14:24 Sisif kernel: [   10.937424] hub 4-0:1.0: 2 ports detected
Apr 30 23:14:24 Sisif kernel: [   13.112997] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 23:14:24 Sisif kernel: [   11.105060] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 23:14:24 Sisif kernel: [   11.105095] b44.c:v2.0
Apr 30 23:14:24 Sisif kernel: [   11.105150] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 23:14:24 Sisif kernel: [   11.105166] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 30 23:14:24 Sisif kernel: [   11.105171] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 30 23:14:24 Sisif kernel: [   11.105200] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Apr 30 23:14:24 Sisif kernel: [   11.109109] ehci_hcd 0000:00:1d.7: debug port 1
Apr 30 23:14:24 Sisif kernel: [   11.109117] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr 30 23:14:24 Sisif kernel: [   11.109126] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80000
Apr 30 23:14:24 Sisif kernel: [   11.124346] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 23:14:24 Sisif kernel: [   11.124376] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 30 23:14:24 Sisif kernel: [   11.124500] usb usb5: configuration #1 chosen from 1 choice
Apr 30 23:14:24 Sisif kernel: [   11.124535] hub 5-0:1.0: USB hub found
Apr 30 23:14:24 Sisif kernel: [   11.124542] hub 5-0:1.0: 8 ports detected
Apr 30 23:14:24 Sisif kernel: [   13.300930] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 23:14:24 Sisif kernel: [   13.300971] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 23:14:24 Sisif kernel: [   13.300984] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Apr 30 23:14:24 Sisif kernel: [   11.228308] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Apr 30 23:14:24 Sisif kernel: [   11.281073] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 30 23:14:24 Sisif kernel: [   13.359116] ata_piix 0000:00:1f.2: version 2.12
Apr 30 23:14:24 Sisif kernel: [   13.359126] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Apr 30 23:14:24 Sisif kernel: [   13.359152] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 23:14:24 Sisif kernel: [   13.359196] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 23:14:24 Sisif kernel: [   13.359934] scsi0 : ata_piix
Apr 30 23:14:24 Sisif kernel: [   13.360591] scsi1 : ata_piix
Apr 30 23:14:24 Sisif kernel: [   13.361399] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Apr 30 23:14:24 Sisif kernel: [   13.361403] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Apr 30 23:14:24 Sisif kernel: [   11.452337] ata1.00: ATA-7: ST9120822AS, 3.CDD, max UDMA/133
Apr 30 23:14:24 Sisif kernel: [   11.452341] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
Apr 30 23:14:24 Sisif kernel: [   11.468332] ata1.00: configured for UDMA/133
Apr 30 23:14:24 Sisif kernel: [   13.885001] ata2.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1B, max UDMA/33
Apr 30 23:14:24 Sisif kernel: [   14.076842] ata2.00: configured for UDMA/33
Apr 30 23:14:24 Sisif kernel: [   12.004772] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.CD PQ: 0 ANSI: 5
Apr 30 23:14:24 Sisif kernel: [   12.007067] scsi 1:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
Apr 30 23:14:24 Sisif kernel: [   12.014781] Driver 'sd' needs updating - please use bus_type methods
Apr 30 23:14:24 Sisif kernel: [   12.014870] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 23:14:24 Sisif kernel: [   12.014884] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 23:14:24 Sisif kernel: [   12.014886] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 23:14:24 Sisif kernel: [   12.014904] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 23:14:24 Sisif kernel: [   12.014955] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 23:14:24 Sisif kernel: [   12.014966] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 23:14:24 Sisif kernel: [   12.014968] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 23:14:24 Sisif kernel: [   12.014985] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 23:14:24 Sisif kernel: [   12.014989]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Apr 30 23:14:24 Sisif kernel: [   12.028866]  sda1 sda2 sda3
Apr 30 23:14:24 Sisif kernel: [   12.041139] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 30 23:14:24 Sisif kernel: [   12.046705] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 30 23:14:24 Sisif kernel: [   12.046725] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 30 23:14:24 Sisif kernel: [   14.134135] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr 30 23:14:24 Sisif kernel: [   14.134141] Uniform CD-ROM driver Revision: 3.20
Apr 30 23:14:24 Sisif kernel: [   14.134193] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 30 23:14:24 Sisif kernel: [   12.552166] Attempting manual resume
Apr 30 23:14:24 Sisif kernel: [   12.552170] swsusp: Resume From Partition 8:2
Apr 30 23:14:24 Sisif kernel: [   12.552171] PM: Checking swsusp image.
Apr 30 23:14:24 Sisif kernel: [   12.552358] PM: Resume from disk failed.
Apr 30 23:14:24 Sisif kernel: [   12.556405] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc00026e60070]
Apr 30 23:14:24 Sisif kernel: [   14.667334] kjournald starting.  Commit interval 5 seconds
Apr 30 23:14:24 Sisif kernel: [   12.594533] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 23:14:24 Sisif kernel: [   23.119049] iTCO_vendor_support: vendor-support=0
Apr 30 23:14:24 Sisif kernel: [   23.137572] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 30 23:14:24 Sisif kernel: [   23.142820] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 30 23:14:24 Sisif kernel: [   21.089997] Linux agpgart interface v0.102
Apr 30 23:14:24 Sisif kernel: [   21.107652] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Apr 30 23:14:24 Sisif kernel: [   21.107758] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Apr 30 23:14:24 Sisif kernel: [   21.107796] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 30 23:14:24 Sisif kernel: [   23.201885] ACPI: AC Adapter [AC] (on-line)
Apr 30 23:14:24 Sisif kernel: [   23.287447] ACPI: Battery Slot [BAT0] (battery present)
Apr 30 23:14:24 Sisif kernel: [   21.248221] agpgart: Detected an Intel 945GM Chipset.
Apr 30 23:14:24 Sisif kernel: [   21.248801] agpgart: Detected 7932K stolen memory.
Apr 30 23:14:24 Sisif kernel: [   21.266269] agpgart: AGP aperture is 256M @ 0xd0000000
Apr 30 23:14:24 Sisif kernel: [   21.336138] intel_rng: FWH not detected
Apr 30 23:14:24 Sisif kernel: [   21.411244] input: Lid Switch as /devices/virtual/input/input2
Apr 30 23:14:24 Sisif kernel: [   21.411682] ACPI: Lid Switch [LID]
Apr 30 23:14:24 Sisif kernel: [   21.411749] input: Power Button (CM) as /devices/virtual/input/input3
Apr 30 23:14:24 Sisif kernel: [   21.435033] ACPI: Power Button (CM) [PBTN]
Apr 30 23:14:24 Sisif kernel: [   21.435130] input: Sleep Button (CM) as /devices/virtual/input/input4
Apr 30 23:14:24 Sisif kernel: [   21.451018] ACPI: Sleep Button (CM) [SBTN]
Apr 30 23:14:24 Sisif kernel: [   21.583877] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input5
Apr 30 23:14:24 Sisif kernel: [   21.610983] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr 30 23:14:24 Sisif kernel: [   21.619017] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
Apr 30 23:14:24 Sisif kernel: [   21.635506] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Apr 30 23:14:24 Sisif kernel: [   21.635695] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input7
Apr 30 23:14:24 Sisif kernel: [   21.662918] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Apr 30 23:14:24 Sisif kernel: [   21.675843] ACPI: WMI-Acer: Mapper loaded
Apr 30 23:14:24 Sisif kernel: [   22.597406] ricoh-mmc: Ricoh MMC Controller disabling driver
Apr 30 23:14:24 Sisif kernel: [   22.597410] ricoh-mmc: Copyright(c) Philip Langdale
Apr 30 23:14:24 Sisif kernel: [   22.597467] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 1)
Apr 30 23:14:24 Sisif kernel: [   22.597481] ricoh-mmc: Controller is now disabled.
Apr 30 23:14:24 Sisif kernel: [   22.678480] sdhci: Secure Digital Host Controller Interface driver
Apr 30 23:14:24 Sisif kernel: [   22.678484] sdhci: Copyright(c) Pierre Ossman
Apr 30 23:14:24 Sisif kernel: [   22.678541] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
Apr 30 23:14:24 Sisif kernel: [   22.678568] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
Apr 30 23:14:24 Sisif kernel: [   22.678640] mmc0: SDHCI at 0xef9fd400 irq 23 DMA
Apr 30 23:14:24 Sisif kernel: [   22.778538] input: PC Speaker as /devices/platform/pcspkr/input/input8
Apr 30 23:14:24 Sisif kernel: [   22.863661] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
Apr 30 23:14:24 Sisif kernel: [   22.863690] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 30 23:14:24 Sisif kernel: [   25.146255] b43-phy0: Broadcom 4311 WLAN found
Apr 30 23:14:24 Sisif kernel: [   25.212595] phy0: Selected rate control algorithm 'simple'
Apr 30 23:14:24 Sisif kernel: [   25.496250] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
Apr 30 23:14:24 Sisif kernel: [   25.532262] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
Apr 30 23:14:24 Sisif kernel: [   23.510074] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Apr 30 23:14:24 Sisif kernel: [   26.244173] udev: renamed network interface wlan0 to eth1
Apr 30 23:14:24 Sisif kernel: [   24.218657] input: b43-phy0 as /devices/virtual/input/input10
Apr 30 23:14:24 Sisif kernel: [   24.473528] lp: driver loaded but no devices found
Apr 30 23:14:24 Sisif kernel: [   24.637658] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
Apr 30 23:14:24 Sisif kernel: [   25.226043] EXT3 FS on sda1, internal journal
Apr 30 23:14:24 Sisif kernel: [   27.710374] Registered led device: b43-phy0:tx
Apr 30 23:14:24 Sisif kernel: [   27.710403] Registered led device: b43-phy0:rx
Apr 30 23:14:24 Sisif kernel: [   27.710428] Registered led device: b43-phy0:radio
Apr 30 23:14:24 Sisif kernel: [   25.735077] NET: Registered protocol family 17
Apr 30 23:14:24 Sisif kernel: [   28.071642] kjournald starting.  Commit interval 5 seconds
Apr 30 23:14:24 Sisif kernel: [   25.999081] EXT3 FS on sda3, internal journal
Apr 30 23:14:24 Sisif kernel: [   25.999086] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 23:14:24 Sisif kernel: [   26.668684] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 23:14:24 Sisif kernel: [   27.945414] RPC: Registered udp transport module.
Apr 30 23:14:24 Sisif kernel: [   27.945418] RPC: Registered tcp transport module.
Apr 30 23:14:24 Sisif kernel: [   28.624682] No dock devices found.
Apr 30 23:14:25 Sisif avahi-daemon[5286]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Apr 30 23:14:25 Sisif avahi-daemon[5286]: Successfully dropped root privileges.
Apr 30 23:14:25 Sisif avahi-daemon[5286]: avahi-daemon 0.6.22 starting up.
Apr 30 23:14:25 Sisif avahi-daemon[5286]: Successfully called chroot().
Apr 30 23:14:25 Sisif avahi-daemon[5286]: Successfully dropped remaining capabilities.
Apr 30 23:14:25 Sisif avahi-daemon[5286]: No service file found in /etc/avahi/services.
Apr 30 23:14:25 Sisif avahi-daemon[5286]: Network interface enumeration completed.
Apr 30 23:14:25 Sisif avahi-daemon[5286]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 30 23:14:25 Sisif avahi-daemon[5286]: Server startup complete. Host name is Sisif.local. Local service cookie is 1442479072.
Apr 30 23:14:25 Sisif kernel: [   30.881859] ppdev: user-space parallel port driver
Apr 30 23:14:25 Sisif kernel: [   31.060548] audit(1209586465.712:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5320 profile="/usr/sbin/cupsd" namespace="default"
Apr 30 23:14:25 Sisif kernel: [   31.108949] apm: BIOS not found.
Apr 30 23:14:27 Sisif kernel: [   32.626847] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Apr 30 23:14:27 Sisif exportfs[5493]: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.10.2:/home/itch/Blonda".   Assuming default behaviour ('no_subtree_check').   NOTE: this default has changed since nfs-utils version 1.0.x 
Apr 30 23:14:27 Sisif kernel: [   32.873524] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Apr 30 23:14:27 Sisif kernel: [   32.889376] NFSD: starting 90-second grace period
Apr 30 23:14:28 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 30 23:14:29 Sisif nmbd[5563]: [2008/04/30 23:14:29, 0] nmbd/nmbd_subnetdb.c:create_subnets(190) 
Apr 30 23:14:29 Sisif nmbd[5563]:   create_subnets: No local interfaces ! 
Apr 30 23:14:29 Sisif nmbd[5563]: [2008/04/30 23:14:29, 0] nmbd/nmbd_subnetdb.c:create_subnets(191) 
Apr 30 23:14:29 Sisif nmbd[5563]:   create_subnets: Waiting for an interface to appear ... 
Apr 30 23:14:30 Sisif dhclient: DHCPREQUEST of 192.168.0.118 on eth0 to 255.255.255.255 port 67
Apr 30 23:14:30 Sisif dhcdbd: Started up.
Apr 30 23:14:30 Sisif hcid[5640]: Bluetooth HCI daemon
Apr 30 23:14:30 Sisif kernel: [   38.129993] Bluetooth: Core ver 2.11
Apr 30 23:14:30 Sisif kernel: [   38.130159] NET: Registered protocol family 31
Apr 30 23:14:30 Sisif kernel: [   38.130165] Bluetooth: HCI device and connection manager initialized
Apr 30 23:14:30 Sisif kernel: [   38.130173] Bluetooth: HCI socket layer initialized
Apr 30 23:14:30 Sisif hcid[5640]: Starting SDP server
Apr 30 23:14:30 Sisif kernel: [   36.250186] Bluetooth: L2CAP ver 2.9
Apr 30 23:14:30 Sisif kernel: [   36.250191] Bluetooth: L2CAP socket layer initialized
Apr 30 23:14:30 Sisif hcid[5640]: Created local server at unix:abstract=/var/run/dbus-IPz5D2yqaj,guid=06e63f8255dbceba9bd717464818d326
Apr 30 23:14:31 Sisif kernel: [   36.354516] Bluetooth: RFCOMM socket layer initialized
Apr 30 23:14:31 Sisif kernel: [   36.355402] Bluetooth: RFCOMM TTY layer initialized
Apr 30 23:14:31 Sisif kernel: [   36.355411] Bluetooth: RFCOMM ver 1.8
Apr 30 23:14:31 Sisif audio[5662]: Bluetooth Audio daemon
Apr 30 23:14:31 Sisif input[5685]: Bluetooth Input daemon
Apr 30 23:14:31 Sisif audio[5662]: Unix socket created: 5
Apr 30 23:14:31 Sisif input[5685]: Registered input manager path:/org/bluez/input
Apr 30 23:14:31 Sisif audio[5662]: audio.conf: Key file does not have key 'Enable'
Apr 30 23:14:31 Sisif audio[5662]: audio.conf: Key file does not have key 'Disable'
Apr 30 23:14:31 Sisif audio[5662]: add_service_record: got record id 0x10000
Apr 30 23:14:31 Sisif audio[5662]: audio.conf: Key file does not have key 'Disable'
Apr 30 23:14:31 Sisif audio[5662]: audio.conf: Key file does not have group 'A2DP'
Apr 30 23:14:31 Sisif last message repeated 3 times
Apr 30 23:14:31 Sisif audio[5662]: SEP 0x806d578 registered: type:0 codec:0 seid:1
Apr 30 23:14:31 Sisif audio[5662]: add_service_record: got record id 0x10001
Apr 30 23:14:31 Sisif audio[5662]: add_service_record: got record id 0x10002
Apr 30 23:14:31 Sisif audio[5662]: add_service_record: got record id 0x10003
Apr 30 23:14:31 Sisif audio[5662]: Registered manager path:/org/bluez/audio
Apr 30 23:14:33 Sisif ntpd[5735]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 23:14:33 Sisif ntpd[5736]: precision = 1.000 usec
Apr 30 23:14:33 Sisif kernel: [   41.073477] NET: Registered protocol family 10
Apr 30 23:14:33 Sisif kernel: [   41.073758] lo: Disabled Privacy Extensions
Apr 30 23:14:33 Sisif kernel: [   41.075321] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 30 23:14:33 Sisif kernel: [   41.075811] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:14:33 Sisif ntpd[5736]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 23:14:33 Sisif ntpd[5736]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 23:14:33 Sisif ntpd[5736]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 23:14:33 Sisif ntpd[5736]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 23:14:33 Sisif ntpd[5736]: kernel time sync status 0040
Apr 30 23:14:33 Sisif ntpd[5736]: frequency initialized -57.977 PPM from /var/lib/ntp/ntp.drift
Apr 30 23:14:35 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr 30 23:14:35 Sisif kernel: [   40.611251] [drm] Initialized drm 1.1.0 20060810
Apr 30 23:14:35 Sisif kernel: [   40.634033] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 23:14:35 Sisif kernel: [   40.634051] PCI: Setting latency timer of device 0000:00:02.0 to 64
Apr 30 23:14:35 Sisif kernel: [   42.708801] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr 30 23:14:35 Sisif anacron[5802]: Anacron 2.3 started on 2008-04-30
Apr 30 23:14:35 Sisif anacron[5802]: Normal exit (0 jobs run)
Apr 30 23:14:35 Sisif /usr/sbin/cron[5833]: (CRON) INFO (pidfile fd = 3)
Apr 30 23:14:35 Sisif /usr/sbin/cron[5836]: (CRON) STARTUP (fork ok)
Apr 30 23:14:35 Sisif /usr/sbin/cron[5836]: (CRON) INFO (Running @reboot jobs)
Apr 30 23:14:35 Sisif ntpd_initres[5754]: host name not found: ntp2a.mcc.ac.uk
Apr 30 23:14:35 Sisif ntpd_initres[5754]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 23:14:35 Sisif ntpd_initres[5754]: host name not found: ntp.landau.ac.ru
Apr 30 23:14:35 Sisif ntpd_initres[5754]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 23:14:36 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 23:14:36 Sisif dhclient: receive_packet failed on eth0: Network is down
Apr 30 23:14:36 Sisif kernel: [   41.937573] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 23:14:36 Sisif kernel: [   41.951512] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 23:14:36 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 23:14:36 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 23:14:36 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 23:14:36 Sisif dhclient: All rights reserved.
Apr 30 23:14:36 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 23:14:36 Sisif dhclient: 
Apr 30 23:14:36 Sisif kernel: [   44.156243] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 23:14:36 Sisif dhclient: Bind socket to interface: No such device
Apr 30 23:14:36 Sisif kernel: [   42.223693] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 23:14:36 Sisif kernel: [   44.297570] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 23:14:36 Sisif kernel: [   44.297643] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 23:14:36 Sisif kernel: [   44.302730] ndiswrapper: using IRQ 16
Apr 30 23:14:37 Sisif kernel: [   44.659750] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 23:14:37 Sisif kernel: [   44.659850] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 23:14:37 Sisif kernel: [   44.663233] usbcore: registered new interface driver ndiswrapper
Apr 30 23:14:37 Sisif kernel: [   42.590436] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 23:14:37 Sisif kernel: [   42.590526] udev: renamed network interface wlan0 to eth1
Apr 30 23:14:37 Sisif kernel: [   42.611385] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:14:37 Sisif kernel: [   42.643069] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:14:37 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 23:14:37 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 23:14:37 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 23:14:37 Sisif dhclient: All rights reserved.
Apr 30 23:14:37 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 23:14:37 Sisif dhclient: 
Apr 30 23:14:37 Sisif kernel: [   42.824561] ndiswrapper: device eth1 removed
Apr 30 23:14:37 Sisif kernel: [   42.824602] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 23:14:37 Sisif kernel: [   42.824795] usbcore: deregistering interface driver ndiswrapper
Apr 30 23:14:37 Sisif kernel: [   42.881821] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 23:14:37 Sisif kernel: [   42.895856] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 23:14:37 Sisif kernel: [   42.896299] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 23:14:37 Sisif kernel: [   42.896388] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 23:14:37 Sisif kernel: [   42.901930] ndiswrapper: using IRQ 16
Apr 30 23:14:37 Sisif kernel: [   43.257904] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 23:14:37 Sisif kernel: [   43.260101] eth1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 23:14:37 Sisif kernel: [   45.333651] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 23:14:37 Sisif kernel: [   45.333776] udev: renamed network interface wlan0 to eth1
Apr 30 23:14:37 Sisif kernel: [   45.334569] ndiswrapper (wrap_procfs_add_ndis_device:399): eth1 already registered?
Apr 30 23:14:37 Sisif kernel: [   45.339752] usbcore: registered new interface driver ndiswrapper
Apr 30 23:14:38 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 23:14:38 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 23:14:38 Sisif dhclient: Sending on   Socket/fallback
Apr 30 23:14:38 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 23:14:40 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 30 23:14:40 Sisif dhclient: send_packet: No such device
Apr 30 23:14:41 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr 30 23:14:41 Sisif dhclient: send_packet: Network is down
Apr 30 23:14:44 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr 30 23:14:44 Sisif dhclient: send_packet: Network is down
Apr 30 23:14:46 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr 30 23:14:46 Sisif dhclient: send_packet: Network is down
Apr 30 23:14:48 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr 30 23:14:48 Sisif dhclient: send_packet: No such device
Apr 30 23:14:54 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
Apr 30 23:14:54 Sisif dhclient: No DHCPOFFERS received.
Apr 30 23:14:54 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 23:14:54 Sisif dhclient: send_packet: Network is down
Apr 30 23:14:54 Sisif kernel: [   61.445261] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:14:54 Sisif avahi-autoipd(eth1)[6170]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 30 23:14:54 Sisif avahi-autoipd(eth1)[6170]: Successfully called chroot().
Apr 30 23:14:54 Sisif avahi-autoipd(eth1)[6170]: Successfully dropped root privileges.
Apr 30 23:14:54 Sisif avahi-autoipd(eth1)[6170]: Starting with address 169.254.4.188
Apr 30 23:14:58 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 30 23:14:58 Sisif dhclient: send_packet: No such device
Apr 30 23:14:59 Sisif avahi-autoipd(eth1)[6170]: Callout BIND, address 169.254.4.188 on interface eth1
Apr 30 23:14:59 Sisif avahi-daemon[5286]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 23:14:59 Sisif avahi-daemon[5286]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 23:14:59 Sisif avahi-daemon[5286]: Registering new address record for 169.254.4.188 on eth1.IPv4.
Apr 30 23:15:03 Sisif avahi-autoipd(eth1)[6170]: Successfully claimed IP address 169.254.4.188
Apr 30 23:15:03 Sisif ntpd[5736]: ntpd exiting on signal 15
Apr 30 23:15:09 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Apr 30 23:15:09 Sisif dhclient: send_packet: No such device
Apr 30 23:15:11 Sisif dhclient: No DHCPOFFERS received.
Apr 30 23:15:11 Sisif dhclient: Trying recorded lease 192.168.0.118
Apr 30 23:15:12 Sisif dhclient: No DHCPOFFERS received.
Apr 30 23:15:12 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 23:15:14 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 23:15:23 Sisif ntpdate[6232]: can't find host ntp2a.mcc.ac.uk 
Apr 30 23:15:32 Sisif ntpdate[6316]: can't find host ntp2a.mcc.ac.uk 
Apr 30 23:15:34 Sisif ntpdate[6396]: can't find host ntp2a.mcc.ac.uk 
Apr 30 23:15:43 Sisif ntpdate[6232]: can't find host ntp.landau.ac.ru 
Apr 30 23:15:43 Sisif ntpdate[6232]: no servers can be used, exiting
Apr 30 23:15:43 Sisif ntpd[6424]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 23:15:43 Sisif ntpd[6425]: precision = 1.000 usec
Apr 30 23:15:43 Sisif ntpd[6425]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 23:15:43 Sisif ntpd[6425]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 23:15:43 Sisif ntpd[6425]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 23:15:43 Sisif ntpd[6425]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 23:15:43 Sisif ntpd[6425]: Listening on interface #4 eth1:avahi, 169.254.4.188#123 Enabled
Apr 30 23:15:43 Sisif ntpd[6425]: kernel time sync status 0040
Apr 30 23:15:43 Sisif ntpd[6425]: frequency initialized -57.977 PPM from /var/lib/ntp/ntp.drift
Apr 30 23:15:52 Sisif ntpdate[6316]: can't find host ntp.landau.ac.ru 
Apr 30 23:15:52 Sisif ntpdate[6316]: no servers can be used, exiting
Apr 30 23:15:54 Sisif ntpdate[6396]: can't find host ntp.landau.ac.ru 
Apr 30 23:15:54 Sisif ntpdate[6396]: no servers can be used, exiting
Apr 30 23:16:08 Sisif hcid[5640]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Apr 30 23:16:08 Sisif hcid[5640]: Default authorization agent (:1.18, /org/bluez/auth) registered
Apr 30 23:16:18 Sisif kernel: [  144.183196] CPU0 attaching NULL sched-domain.
Apr 30 23:16:18 Sisif kernel: [  144.183204] CPU1 attaching NULL sched-domain.
Apr 30 23:16:18 Sisif kernel: [  144.198290] CPU0 attaching sched-domain:
Apr 30 23:16:18 Sisif kernel: [  144.198295]  domain 0: span 03
Apr 30 23:16:18 Sisif kernel: [  144.198297]   groups: 01 02
Apr 30 23:16:18 Sisif kernel: [  144.198301] CPU1 attaching sched-domain:
Apr 30 23:16:18 Sisif kernel: [  144.198302]  domain 0: span 03
Apr 30 23:16:18 Sisif kernel: [  144.198304]   groups: 02 01
Apr 30 23:16:21 Sisif avahi-daemon[5286]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 23:16:21 Sisif avahi-daemon[5286]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 23:16:21 Sisif avahi-autoipd(eth1)[6170]: SIOCSIFFLAGS failed: Permission denied
Apr 30 23:16:21 Sisif avahi-autoipd(eth1)[6170]: Callout STOP, address 169.254.4.188 on interface eth1
Apr 30 23:16:21 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 23:16:21 Sisif avahi-daemon[5286]: Withdrawing address record for 169.254.4.188 on eth1.
Apr 30 23:16:21 Sisif avahi-autoipd(eth1)[6171]: client: RTNETLINK answers: No such process
Apr 30 23:16:21 Sisif kernel: [  146.781404] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:16:21 Sisif kernel: [  147.163919] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:16:21 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 23:16:21 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 23:16:21 Sisif dhclient: All rights reserved.
Apr 30 23:16:21 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 23:16:21 Sisif dhclient: 
Apr 30 23:16:22 Sisif kernel: [  149.898914] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 30 23:16:23 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 23:16:23 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 23:16:23 Sisif dhclient: Sending on   Socket/fallback
Apr 30 23:16:23 Sisif avahi-daemon[5286]: Registering new address record for fe80::219:7eff:fea0:3d2a on eth1.*.
Apr 30 23:16:24 Sisif ntpd[6425]: Listening on interface #5 eth1, fe80::219:7eff:fea0:3d2a#123 Enabled
Apr 30 23:16:24 Sisif ntpd[6425]: Deleting interface #4 eth1:avahi, 169.254.4.188#123, interface stats: received=0, sent=0, dropped=0, active_time=1 secs
Apr 30 23:16:25 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 23:16:25 Sisif ntpd_initres[7030]: host name not found: ntp2a.mcc.ac.uk
Apr 30 23:16:25 Sisif ntpd_initres[7030]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 23:16:25 Sisif ntpd_initres[7030]: host name not found: ntp.landau.ac.ru
Apr 30 23:16:25 Sisif ntpd_initres[7030]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 23:16:31 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 23:16:32 Sisif kernel: [  159.898357] eth1: no IPv6 routers present
Apr 30 23:16:38 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr 30 23:16:44 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr 30 23:16:57 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr 30 23:17:01 Sisif /USR/SBIN/CRON[7993]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 30 23:17:09 Sisif dhclient: No DHCPOFFERS received.
Apr 30 23:17:09 Sisif dhclient: Trying recorded lease 192.168.1.102
Apr 30 23:17:09 Sisif avahi-daemon[5286]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 23:17:09 Sisif avahi-daemon[5286]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 23:17:09 Sisif avahi-daemon[5286]: Registering new address record for 192.168.1.102 on eth1.IPv4.
Apr 30 23:17:12 Sisif avahi-daemon[5286]: Withdrawing address record for 192.168.1.102 on eth1.
Apr 30 23:17:12 Sisif avahi-daemon[5286]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 23:17:12 Sisif avahi-daemon[5286]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 23:17:12 Sisif avahi-autoipd(eth1)[8330]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 30 23:17:12 Sisif avahi-autoipd(eth1)[8330]: Successfully called chroot().
Apr 30 23:17:12 Sisif avahi-autoipd(eth1)[8330]: Successfully dropped root privileges.
Apr 30 23:17:12 Sisif avahi-autoipd(eth1)[8330]: Starting with address 169.254.4.188
Apr 30 23:17:17 Sisif avahi-autoipd(eth1)[8330]: Callout BIND, address 169.254.4.188 on interface eth1
Apr 30 23:17:17 Sisif avahi-daemon[5286]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 23:17:17 Sisif avahi-daemon[5286]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 23:17:17 Sisif avahi-daemon[5286]: Registering new address record for 169.254.4.188 on eth1.IPv4.
Apr 30 23:17:21 Sisif avahi-autoipd(eth1)[8330]: Successfully claimed IP address 169.254.4.188
Apr 30 23:17:21 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 23:17:29 Sisif avahi-daemon[5286]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 23:17:29 Sisif avahi-daemon[5286]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 23:17:29 Sisif avahi-autoipd(eth1)[8330]: SIOCSIFFLAGS failed: Permission denied
Apr 30 23:17:29 Sisif avahi-autoipd(eth1)[8330]: Callout STOP, address 169.254.4.188 on interface eth1
Apr 30 23:17:29 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 23:17:29 Sisif avahi-daemon[5286]: Withdrawing address record for fe80::219:7eff:fea0:3d2a on eth1.
Apr 30 23:17:29 Sisif avahi-daemon[5286]: Withdrawing address record for 169.254.4.188 on eth1.
Apr 30 23:17:29 Sisif avahi-autoipd(eth1)[8331]: client: RTNETLINK answers: No such process
Apr 30 23:17:30 Sisif kernel: [  217.711425] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:17:30 Sisif dhclient: There is already a pid file /var/run/dhclient.pid with pid 8643
Apr 30 23:17:30 Sisif dhclient: removed stale PID file
Apr 30 23:17:30 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 23:17:30 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 23:17:30 Sisif dhclient: All rights reserved.
Apr 30 23:17:30 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 23:17:30 Sisif dhclient: 
Apr 30 23:17:30 Sisif kernel: [  216.193952] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 30 23:17:31 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 23:17:31 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 23:17:31 Sisif dhclient: Sending on   Socket/fallback
Apr 30 23:17:31 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 23:17:31 Sisif dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
Apr 30 23:17:31 Sisif avahi-daemon[5286]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 23:17:31 Sisif avahi-daemon[5286]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 23:17:31 Sisif avahi-daemon[5286]: Registering new address record for 192.168.1.102 on eth1.IPv4.
Apr 30 23:17:31 Sisif dhclient: bound to 192.168.1.102 -- renewal in 33331 seconds.
Apr 30 23:17:32 Sisif avahi-daemon[5286]: Registering new address record for fe80::219:7eff:fea0:3d2a on eth1.*.
Apr 30 23:17:41 Sisif kernel: [  226.923403] eth1: no IPv6 routers present
Apr 30 23:18:18 Sisif nmbd[5563]: [2008/04/30 23:18:18, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 23:18:18 Sisif nmbd[5563]:   Packet send failed to 169.254.255.255(138) ERRNO=Invalid argument 
Apr 30 23:20:53 Sisif nmbd[5563]: [2008/04/30 23:20:53, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Apr 30 23:20:53 Sisif nmbd[5563]:   ***** 
Apr 30 23:20:53 Sisif nmbd[5563]:    
Apr 30 23:20:53 Sisif nmbd[5563]:   Samba name server SISIF is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.102 
Apr 30 23:20:53 Sisif nmbd[5563]:    
Apr 30 23:20:53 Sisif nmbd[5563]:   ***** 
Apr 30 23:21:24 Sisif ntpd[6425]: Listening on interface #6 eth1, 192.168.1.102#123 Enabled
Apr 30 23:34:23 Sisif -- MARK --
Apr 30 23:53:32 Sisif init: tty4 main process (4682) killed by TERM signal
Apr 30 23:53:32 Sisif init: tty5 main process (4683) killed by TERM signal
Apr 30 23:53:32 Sisif init: tty2 main process (4685) killed by TERM signal
Apr 30 23:53:32 Sisif init: tty3 main process (4687) killed by TERM signal
Apr 30 23:53:32 Sisif init: tty6 main process (4689) killed by TERM signal
Apr 30 23:53:32 Sisif init: tty1 main process (6147) killed by TERM signal
Apr 30 23:53:32 Sisif kernel: [ 2378.630568] compiz.real[6732]: segfault at 00085bf9 eip 08055a6d esp bfd08b40 error 4
Apr 30 23:53:33 Sisif kernel: [ 2379.761407] gdm[5704]: segfault at 7672657f eip b78527e2 esp bfc333c0 error 6
Apr 30 23:53:33 Sisif avahi-daemon[5286]: Got SIGTERM, quitting.
Apr 30 23:53:33 Sisif avahi-daemon[5286]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 23:53:33 Sisif nmbd[5563]: [2008/04/30 23:53:33, 0] nmbd/nmbd.c:terminate(58) 
Apr 30 23:53:33 Sisif nmbd[5563]:   Got SIGTERM: going down... 
Apr 30 23:53:35 Sisif rpc.statd[4521]: Caught signal 15, un-registering and exiting.
Apr 30 23:53:36 Sisif kernel: [ 2380.989270] ip6_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 23:53:37 Sisif mountd[5518]: Caught signal 15, un-registering and exiting.
Apr 30 23:53:37 Sisif kernel: [ 2384.272521] nfsd: last server has exited
Apr 30 23:53:37 Sisif kernel: [ 2384.272525] nfsd: unexporting all filesystems
Apr 30 23:53:37 Sisif exiting on signal 15
Apr 30 23:54:19 Sisif syslogd 1.5.0#1ubuntu1: restart.
Apr 30 23:54:19 Sisif kernel: Inspecting /boot/System.map-2.6.24-16-generic
Apr 30 23:54:19 Sisif kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Apr 30 23:54:19 Sisif kernel: Symbols match kernel version 2.6.24.
Apr 30 23:54:19 Sisif kernel: Loaded 21378 symbols from 98 modules.
Apr 30 23:54:19 Sisif kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Apr 30 23:54:19 Sisif kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 30 23:54:19 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 30 23:54:19 Sisif kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 30 23:54:19 Sisif kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d3400 (usable)
Apr 30 23:54:19 Sisif kernel: [    0.000000]  BIOS-e820: 000000007f6d3400 - 0000000080000000 (reserved)
Apr 30 23:54:19 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Apr 30 23:54:19 Sisif kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Apr 30 23:54:19 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 30 23:54:19 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Apr 30 23:54:19 Sisif kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Apr 30 23:54:19 Sisif kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Apr 30 23:54:19 Sisif kernel: [    0.000000] 1142MB HIGHMEM available.
Apr 30 23:54:19 Sisif kernel: [    0.000000] 896MB LOWMEM available.
Apr 30 23:54:19 Sisif kernel: [    0.000000] Entering add_active_range(0, 0, 521939) 0 entries of 256 used
Apr 30 23:54:19 Sisif kernel: [    0.000000] Zone PFN ranges:
Apr 30 23:54:19 Sisif kernel: [    0.000000]   DMA             0 ->     4096
Apr 30 23:54:19 Sisif kernel: [    0.000000]   Normal       4096 ->   229376
Apr 30 23:54:19 Sisif kernel: [    0.000000]   HighMem    229376 ->   521939
Apr 30 23:54:19 Sisif kernel: [    0.000000] Movable zone start PFN for each node
Apr 30 23:54:19 Sisif kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 30 23:54:19 Sisif kernel: [    0.000000]     0:        0 ->   521939
Apr 30 23:54:19 Sisif kernel: [    0.000000] On node 0 totalpages: 521939
Apr 30 23:54:19 Sisif kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 30 23:54:19 Sisif kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 30 23:54:19 Sisif kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 30 23:54:19 Sisif kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Apr 30 23:54:19 Sisif kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Apr 30 23:54:19 Sisif kernel: [    0.000000]   HighMem zone: 2285 pages used for memmap
Apr 30 23:54:19 Sisif kernel: [    0.000000]   HighMem zone: 290278 pages, LIFO batch:31
Apr 30 23:54:19 Sisif kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 30 23:54:19 Sisif kernel: [    0.000000] DMI 2.4 present.
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: RSDT 7F6D39CD, 0040 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: FACP 7F6D4800, 0074 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: DSDT 7F6D5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: FACS 7F6E3C00, 0040
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: HPET 7F6D4F00, 0038 (r1 DELL    M07            1 ASL        61)
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: APIC 7F6D5000, 0068 (r1 DELL    M07     27D7060D ASL        47)
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: MCFG 7F6D4FC0, 003E (r16 DELL    M07     27D7060D ASL        61)
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: SLIC 7F6D509C, 0024 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: BOOT 7F6D4BC0, 0028 (r1 DELL    M07     27D7060D ASL        61)
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: SSDT 7F6D3A0D, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 30 23:54:19 Sisif kernel: [    0.000000] Processor #0 6:14 APIC version 20
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 30 23:54:19 Sisif kernel: [    0.000000] Processor #1 6:14 APIC version 20
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 30 23:54:19 Sisif kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 30 23:54:19 Sisif kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 30 23:54:19 Sisif kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 30 23:54:19 Sisif kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 30 23:54:19 Sisif kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
Apr 30 23:54:19 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 30 23:54:19 Sisif kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Apr 30 23:54:19 Sisif kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517862
Apr 30 23:54:19 Sisif kernel: [    0.000000] Kernel command line: root=UUID=35a5e031-c7e9-4597-9992-99d1d88d0eac ro quiet splash
Apr 30 23:54:19 Sisif kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Apr 30 23:54:19 Sisif kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Apr 30 23:54:19 Sisif kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 30 23:54:19 Sisif kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 30 23:54:19 Sisif kernel: [    0.000000] Initializing CPU#0
Apr 30 23:54:19 Sisif kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 30 23:54:19 Sisif kernel: [    0.000000] Detected 1729.007 MHz processor.
Apr 30 23:54:19 Sisif kernel: [    7.460452] Console: colour VGA+ 80x25
Apr 30 23:54:19 Sisif kernel: [    7.460458] console [tty0] enabled
Apr 30 23:54:19 Sisif kernel: [    7.460761] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 30 23:54:19 Sisif kernel: [    7.461156] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 30 23:54:19 Sisif kernel: [    7.583153] Memory: 2057924k/2087756k available (2157k kernel code, 28552k reserved, 998k data, 364k init, 1170252k highmem)
Apr 30 23:54:19 Sisif kernel: [    7.583162] virtual kernel memory layout:
Apr 30 23:54:19 Sisif kernel: [    7.583163]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Apr 30 23:54:19 Sisif kernel: [    7.583164]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 30 23:54:19 Sisif kernel: [    7.583166]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Apr 30 23:54:19 Sisif kernel: [    7.583167]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 30 23:54:19 Sisif kernel: [    7.583168]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Apr 30 23:54:19 Sisif kernel: [    7.583169]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Apr 30 23:54:19 Sisif kernel: [    7.583171]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Apr 30 23:54:19 Sisif kernel: [    7.583174] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 30 23:54:19 Sisif kernel: [    7.583218] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 30 23:54:19 Sisif kernel: [    7.583367] hpet clockevent registered
Apr 30 23:54:19 Sisif kernel: [    7.663340] Calibrating delay using timer specific routine.. 3461.86 BogoMIPS (lpj=6923736)
Apr 30 23:54:19 Sisif kernel: [    7.663365] Security Framework initialized
Apr 30 23:54:19 Sisif kernel: [    7.663374] SELinux:  Disabled at boot.
Apr 30 23:54:19 Sisif kernel: [    7.663390] AppArmor: AppArmor initialized
Apr 30 23:54:19 Sisif kernel: [    7.663395] Failure registering capabilities with primary security module.
Apr 30 23:54:19 Sisif kernel: [    7.663403] Mount-cache hash table entries: 512
Apr 30 23:54:19 Sisif kernel: [    7.663539] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 23:54:19 Sisif kernel: [    7.663550] monitor/mwait feature present.
Apr 30 23:54:19 Sisif kernel: [    7.663552] using mwait in idle threads.
Apr 30 23:54:19 Sisif kernel: [    7.663556] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 23:54:19 Sisif kernel: [    7.663558] CPU: L2 cache: 1024K
Apr 30 23:54:19 Sisif kernel: [    7.663561] CPU: Physical Processor ID: 0
Apr 30 23:54:19 Sisif kernel: [    7.663563] CPU: Processor Core ID: 0
Apr 30 23:54:19 Sisif kernel: [    7.663565] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 23:54:19 Sisif kernel: [    7.663575] Compat vDSO mapped to ffffe000.
Apr 30 23:54:19 Sisif kernel: [    7.663589] Checking 'hlt' instruction... OK.
Apr 30 23:54:19 Sisif kernel: [    7.679739] SMP alternatives: switching to UP code
Apr 30 23:54:19 Sisif kernel: [    7.681581] Early unpacking initramfs... done
Apr 30 23:54:19 Sisif kernel: [    8.031713] ACPI: Core revision 20070126
Apr 30 23:54:19 Sisif kernel: [    8.031774] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 30 23:54:19 Sisif kernel: [    8.034451] CPU0: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 23:54:19 Sisif kernel: [    8.034471] SMP alternatives: switching to SMP code
Apr 30 23:54:19 Sisif kernel: [    8.035199] Booting processor 1/1 eip 3000
Apr 30 23:54:19 Sisif kernel: [   10.064113] Initializing CPU#1
Apr 30 23:54:19 Sisif kernel: [   10.144034] Calibrating delay using timer specific routine.. 3458.04 BogoMIPS (lpj=6916096)
Apr 30 23:54:19 Sisif kernel: [   10.144041] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Apr 30 23:54:19 Sisif kernel: [   10.144047] monitor/mwait feature present.
Apr 30 23:54:19 Sisif kernel: [   10.144050] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 30 23:54:19 Sisif kernel: [   10.144052] CPU: L2 cache: 1024K
Apr 30 23:54:19 Sisif kernel: [   10.144054] CPU: Physical Processor ID: 0
Apr 30 23:54:19 Sisif kernel: [   10.144056] CPU: Processor Core ID: 1
Apr 30 23:54:19 Sisif kernel: [   10.144057] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Apr 30 23:54:19 Sisif kernel: [    8.127627] CPU1: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
Apr 30 23:54:19 Sisif kernel: [    8.127651] Total of 2 processors activated (6919.91 BogoMIPS).
Apr 30 23:54:19 Sisif kernel: [    8.127849] ENABLING IO-APIC IRQs
Apr 30 23:54:19 Sisif kernel: [    8.128045] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 30 23:54:19 Sisif kernel: [    8.275195] checking TSC synchronization [CPU#0 -> CPU#1]:
Apr 30 23:54:19 Sisif kernel: [    8.295195] Measured 3488687072 cycles TSC warp between CPUs, turning off TSC clock.
Apr 30 23:54:19 Sisif kernel: [    8.295198] Marking TSC unstable due to: check_tsc_sync_source failed.
Apr 30 23:54:19 Sisif kernel: [    8.295215] Brought up 2 CPUs
Apr 30 23:54:19 Sisif kernel: [    8.295242] CPU0 attaching sched-domain:
Apr 30 23:54:19 Sisif kernel: [    8.295245]  domain 0: span 03
Apr 30 23:54:19 Sisif kernel: [    8.295247]   groups: 01 02
Apr 30 23:54:19 Sisif kernel: [    8.295250] CPU1 attaching sched-domain:
Apr 30 23:54:19 Sisif kernel: [    8.295252]  domain 0: span 03
Apr 30 23:54:19 Sisif kernel: [    8.295254]   groups: 02 01
Apr 30 23:54:19 Sisif kernel: [   10.312410] net_namespace: 64 bytes
Apr 30 23:54:19 Sisif kernel: [   10.312421] Booting paravirtualized kernel on bare hardware
Apr 30 23:54:19 Sisif kernel: [   10.312919] Time: 20:53:57  Date: 04/30/08
Apr 30 23:54:19 Sisif kernel: [   10.312950] NET: Registered protocol family 16
Apr 30 23:54:19 Sisif kernel: [   10.313172] EISA bus registered
Apr 30 23:54:19 Sisif kernel: [   10.313177] ACPI: bus type pci registered
Apr 30 23:54:19 Sisif kernel: [   10.341910] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=13
Apr 30 23:54:19 Sisif kernel: [   10.341913] PCI: Using configuration type 1
Apr 30 23:54:19 Sisif kernel: [   10.341914] Setting up standard PCI resources
Apr 30 23:54:19 Sisif kernel: [    8.330768] ACPI: EC: Look up EC in DSDT
Apr 30 23:54:19 Sisif kernel: [    8.335680] ACPI: Interpreter enabled
Apr 30 23:54:19 Sisif kernel: [    8.335684] ACPI: (supports S0 S3 S4 S5)
Apr 30 23:54:19 Sisif kernel: [    8.335698] ACPI: Using IOAPIC for interrupt routing
Apr 30 23:54:19 Sisif kernel: [    8.349742] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 30 23:54:19 Sisif kernel: [    8.350547] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 30 23:54:19 Sisif kernel: [    8.350552] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Apr 30 23:54:19 Sisif kernel: [    8.351731] PCI: Transparent bridge - 0000:00:1e.0
Apr 30 23:54:19 Sisif kernel: [    8.351770] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 30 23:54:19 Sisif kernel: [    8.352233] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr 30 23:54:19 Sisif kernel: [    8.352365] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 30 23:54:19 Sisif kernel: [    8.352486] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr 30 23:54:19 Sisif kernel: [    8.360871] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr 30 23:54:19 Sisif kernel: [    8.360982] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
Apr 30 23:54:19 Sisif kernel: [    8.361090] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Apr 30 23:54:19 Sisif kernel: [    8.361198] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Apr 30 23:54:19 Sisif kernel: [    8.361308] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 30 23:54:19 Sisif kernel: [    8.361420] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 30 23:54:19 Sisif kernel: [    8.361530] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Apr 30 23:54:19 Sisif kernel: [    8.361641] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Apr 30 23:54:19 Sisif kernel: [    8.361796] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 30 23:54:19 Sisif kernel: [    8.361830] pnp: PnP ACPI init
Apr 30 23:54:19 Sisif kernel: [    8.361838] ACPI: bus type pnp registered
Apr 30 23:54:19 Sisif kernel: [    8.378109] pnpacpi: exceeded the max number of mem resources: 12
Apr 30 23:54:19 Sisif kernel: [    8.390953] pnp: PnP ACPI: found 12 devices
Apr 30 23:54:19 Sisif kernel: [    8.390956] ACPI: ACPI bus type pnp unregistered
Apr 30 23:54:19 Sisif kernel: [    8.390959] PnPBIOS: Disabled by ACPI PNP
Apr 30 23:54:19 Sisif kernel: [    8.391255] PCI: Using ACPI for IRQ routing
Apr 30 23:54:19 Sisif kernel: [    8.391258] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 30 23:54:19 Sisif kernel: [    8.463003] NET: Registered protocol family 8
Apr 30 23:54:19 Sisif kernel: [    8.463006] NET: Registered protocol family 20
Apr 30 23:54:19 Sisif kernel: [   10.479947] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 30 23:54:19 Sisif kernel: [   10.479952] hpet0: 3 64-bit timers, 14318180 Hz
Apr 30 23:54:19 Sisif kernel: [   10.480995] AppArmor: AppArmor Filesystem Enabled
Apr 30 23:54:19 Sisif kernel: [    8.466996] Time: hpet clocksource has been installed.
Apr 30 23:54:19 Sisif kernel: [    8.467016] Switched to high resolution mode on CPU 0
Apr 30 23:54:19 Sisif kernel: [   10.484032] Switched to high resolution mode on CPU 1
Apr 30 23:54:19 Sisif kernel: [    8.479999] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480003] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480006] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480009] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480012] system 00:00: iomem range 0x100000-0x7f6d33ff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480015] system 00:00: iomem range 0x7f6d3400-0x7f6fffff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480019] system 00:00: iomem range 0x7f700000-0x7f7fffff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480022] system 00:00: iomem range 0x7f700000-0x7fefffff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480025] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480029] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480032] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480035] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480042] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480045] system 00:02: ioport range 0x1000-0x1005 has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480048] system 00:02: ioport range 0x1008-0x100f has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480055] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480058] system 00:03: ioport range 0x1006-0x1007 has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480061] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480064] system 00:03: ioport range 0x1060-0x107f has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480067] system 00:03: ioport range 0x1080-0x10bf has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480070] system 00:03: ioport range 0x10c0-0x10df has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480073] system 00:03: ioport range 0x1010-0x102f has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480076] system 00:03: ioport range 0x809-0x809 has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480085] system 00:08: ioport range 0xc80-0xcff could not be reserved
Apr 30 23:54:19 Sisif kernel: [    8.480088] system 00:08: ioport range 0x910-0x91f has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480091] system 00:08: ioport range 0x920-0x92f has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480094] system 00:08: ioport range 0xcb0-0xcbf has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480097] system 00:08: ioport range 0x930-0x97f has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.480105] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Apr 30 23:54:19 Sisif kernel: [    8.510574] PCI: Bridge: 0000:00:1c.0
Apr 30 23:54:19 Sisif kernel: [    8.510576]   IO window: disabled.
Apr 30 23:54:19 Sisif kernel: [    8.510583]   MEM window: efd00000-efdfffff
Apr 30 23:54:19 Sisif kernel: [    8.510587]   PREFETCH window: disabled.
Apr 30 23:54:19 Sisif kernel: [    8.510593] PCI: Bridge: 0000:00:1c.3
Apr 30 23:54:19 Sisif kernel: [    8.510596]   IO window: d000-dfff
Apr 30 23:54:19 Sisif kernel: [    8.510602]   MEM window: efa00000-efcfffff
Apr 30 23:54:19 Sisif kernel: [    8.510607]   PREFETCH window: e0000000-e01fffff
Apr 30 23:54:19 Sisif kernel: [    8.510614] PCI: Bridge: 0000:00:1e.0
Apr 30 23:54:19 Sisif kernel: [    8.510615]   IO window: disabled.
Apr 30 23:54:19 Sisif kernel: [    8.510621]   MEM window: ef900000-ef9fffff
Apr 30 23:54:19 Sisif kernel: [    8.510626]   PREFETCH window: disabled.
Apr 30 23:54:19 Sisif kernel: [    8.510660] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 23:54:19 Sisif kernel: [    8.510669] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 23:54:19 Sisif kernel: [    8.510694] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Apr 30 23:54:19 Sisif kernel: [    8.510700] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 23:54:19 Sisif kernel: [    8.510714] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 30 23:54:19 Sisif kernel: [    8.510727] NET: Registered protocol family 2
Apr 30 23:54:19 Sisif kernel: [    8.554980] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 30 23:54:19 Sisif kernel: [    8.555220] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 30 23:54:19 Sisif kernel: [    8.555966] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 30 23:54:19 Sisif kernel: [    8.556344] TCP: Hash tables configured (established 131072 bind 65536)
Apr 30 23:54:19 Sisif kernel: [    8.556348] TCP reno registered
Apr 30 23:54:19 Sisif kernel: [    8.567087] checking if image is initramfs... it is
Apr 30 23:54:19 Sisif kernel: [    9.259744] Freeing initrd memory: 7267k freed
Apr 30 23:54:19 Sisif kernel: [    9.259916] Simple Boot Flag at 0x79 set to 0x1
Apr 30 23:54:19 Sisif kernel: [   11.277546] audit: initializing netlink socket (disabled)
Apr 30 23:54:19 Sisif kernel: [   11.277561] audit(1209588837.552:1): initialized
Apr 30 23:54:19 Sisif kernel: [    9.260907] highmem bounce pool size: 64 pages
Apr 30 23:54:19 Sisif kernel: [   11.279975] VFS: Disk quotas dquot_6.5.1
Apr 30 23:54:19 Sisif kernel: [    9.263163] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 30 23:54:19 Sisif kernel: [    9.263311] io scheduler noop registered
Apr 30 23:54:19 Sisif kernel: [    9.263314] io scheduler anticipatory registered
Apr 30 23:54:19 Sisif kernel: [    9.263316] io scheduler deadline registered
Apr 30 23:54:19 Sisif kernel: [    9.263328] io scheduler cfq registered (default)
Apr 30 23:54:19 Sisif kernel: [    9.263339] Boot video device is 0000:00:02.0
Apr 30 23:54:19 Sisif kernel: [    9.263553] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 30 23:54:19 Sisif kernel: [    9.263616] assign_interrupt_mode Found MSI capability
Apr 30 23:54:19 Sisif kernel: [    9.263667] Allocate Port Service[0000:00:1c.0:pcie00]
Apr 30 23:54:19 Sisif kernel: [    9.263709] Allocate Port Service[0000:00:1c.0:pcie02]
Apr 30 23:54:19 Sisif kernel: [    9.263820] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 30 23:54:19 Sisif kernel: [    9.263878] assign_interrupt_mode Found MSI capability
Apr 30 23:54:19 Sisif kernel: [    9.263925] Allocate Port Service[0000:00:1c.3:pcie00]
Apr 30 23:54:19 Sisif kernel: [    9.263962] Allocate Port Service[0000:00:1c.3:pcie02]
Apr 30 23:54:19 Sisif kernel: [    9.264245] isapnp: Scanning for PnP cards...
Apr 30 23:54:19 Sisif kernel: [    9.618401] isapnp: No Plug & Play device found
Apr 30 23:54:19 Sisif kernel: [    9.648459] Real Time Clock Driver v1.12ac
Apr 30 23:54:19 Sisif kernel: [   11.665539] hpet_resources: 0xfed00000 is busy
Apr 30 23:54:19 Sisif kernel: [   11.665595] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 30 23:54:19 Sisif kernel: [   11.666890] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 30 23:54:19 Sisif kernel: [   11.666967] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 30 23:54:19 Sisif kernel: [   11.667078] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 30 23:54:19 Sisif kernel: [    9.653178] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 30 23:54:19 Sisif kernel: [    9.653185] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 30 23:54:19 Sisif kernel: [   11.691439] mice: PS/2 mouse device common for all mice
Apr 30 23:54:19 Sisif kernel: [   11.691568] EISA: Probing bus 0 at eisa.0
Apr 30 23:54:19 Sisif kernel: [   11.691637] EISA: Mainboard UO_FFFF detected.
Apr 30 23:54:19 Sisif kernel: [   11.691677] Cannot allocate resource for EISA slot 1
Apr 30 23:54:19 Sisif kernel: [   11.691707] EISA: Detected 0 cards.
Apr 30 23:54:19 Sisif kernel: [   11.691712] cpuidle: using governor ladder
Apr 30 23:54:19 Sisif kernel: [   11.691714] cpuidle: using governor menu
Apr 30 23:54:19 Sisif kernel: [   11.691806] NET: Registered protocol family 1
Apr 30 23:54:19 Sisif kernel: [   11.691836] Using IPI No-Shortcut mode
Apr 30 23:54:19 Sisif kernel: [   11.691869] registered taskstats version 1
Apr 30 23:54:19 Sisif kernel: [   11.691987]   Magic number: 4:703:903
Apr 30 23:54:19 Sisif kernel: [   11.692097] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 30 23:54:19 Sisif kernel: [   11.692099] EDD information not available.
Apr 30 23:54:19 Sisif kernel: [   11.692271] Freeing unused kernel memory: 364k freed
Apr 30 23:54:19 Sisif kernel: [   11.694682] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 30 23:54:19 Sisif kernel: [   10.893272] fuse init (API version 7.9)
Apr 30 23:54:19 Sisif kernel: [   10.914729] ACPI: SSDT 7F6D4134, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Apr 30 23:54:19 Sisif kernel: [   10.914921] ACPI: SSDT 7F6D3EE9, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Apr 30 23:54:19 Sisif kernel: [   10.915497] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 23:54:19 Sisif kernel: [   10.915502] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 30 23:54:19 Sisif kernel: [   10.915726] ACPI: SSDT 7F6D4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Apr 30 23:54:19 Sisif kernel: [   10.915899] ACPI: SSDT 7F6D40AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Apr 30 23:54:19 Sisif kernel: [   12.933464] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 30 23:54:19 Sisif kernel: [   12.933469] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 30 23:54:19 Sisif kernel: [   12.940067] ACPI: Thermal Zone [THM] (48 C)
Apr 30 23:54:19 Sisif kernel: [   11.311213] usbcore: registered new interface driver usbfs
Apr 30 23:54:19 Sisif kernel: [   11.311238] usbcore: registered new interface driver hub
Apr 30 23:54:19 Sisif kernel: [   11.311561] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 23:54:19 Sisif kernel: [   11.311581] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 23:54:19 Sisif kernel: [   11.311650] usbcore: registered new device driver usb
Apr 30 23:54:19 Sisif kernel: [   11.312900] USB Universal Host Controller Interface driver v3.0
Apr 30 23:54:19 Sisif kernel: [   13.360515] SCSI subsystem initialized
Apr 30 23:54:19 Sisif kernel: [   13.381833] libata version 3.00 loaded.
Apr 30 23:54:19 Sisif kernel: [   11.369737] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Apr 30 23:54:19 Sisif kernel: [   11.369786] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 23:54:19 Sisif kernel: [   11.369799] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 30 23:54:19 Sisif kernel: [   11.369804] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 30 23:54:19 Sisif kernel: [   11.370320] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Apr 30 23:54:19 Sisif kernel: [   11.370359] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
Apr 30 23:54:19 Sisif kernel: [   11.370505] usb usb1: configuration #1 chosen from 1 choice
Apr 30 23:54:19 Sisif kernel: [   11.370531] hub 1-0:1.0: USB hub found
Apr 30 23:54:19 Sisif kernel: [   11.370536] hub 1-0:1.0: 2 ports detected
Apr 30 23:54:19 Sisif kernel: [   11.473678] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
Apr 30 23:54:19 Sisif kernel: [   11.473691] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 30 23:54:19 Sisif kernel: [   11.473696] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 30 23:54:19 Sisif kernel: [   11.473721] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Apr 30 23:54:19 Sisif kernel: [   11.473756] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bf60
Apr 30 23:54:19 Sisif kernel: [   11.473873] usb usb2: configuration #1 chosen from 1 choice
Apr 30 23:54:19 Sisif kernel: [   11.473898] hub 2-0:1.0: USB hub found
Apr 30 23:54:19 Sisif kernel: [   11.473904] hub 2-0:1.0: 2 ports detected
Apr 30 23:54:19 Sisif kernel: [   13.594551] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
Apr 30 23:54:19 Sisif kernel: [   13.594564] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 30 23:54:19 Sisif kernel: [   13.594569] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 30 23:54:19 Sisif kernel: [   13.594595] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Apr 30 23:54:19 Sisif kernel: [   13.594631] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000bf40
Apr 30 23:54:19 Sisif kernel: [   13.594752] usb usb3: configuration #1 chosen from 1 choice
Apr 30 23:54:19 Sisif kernel: [   13.594782] hub 3-0:1.0: USB hub found
Apr 30 23:54:19 Sisif kernel: [   13.594787] hub 3-0:1.0: 2 ports detected
Apr 30 23:54:19 Sisif kernel: [   13.699491] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
Apr 30 23:54:19 Sisif kernel: [   13.699504] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Apr 30 23:54:19 Sisif kernel: [   13.699509] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Apr 30 23:54:19 Sisif kernel: [   13.699538] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Apr 30 23:54:19 Sisif kernel: [   13.699573] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000bf20
Apr 30 23:54:19 Sisif kernel: [   13.699702] usb usb4: configuration #1 chosen from 1 choice
Apr 30 23:54:19 Sisif kernel: [   13.699728] hub 4-0:1.0: USB hub found
Apr 30 23:54:19 Sisif kernel: [   13.699733] hub 4-0:1.0: 2 ports detected
Apr 30 23:54:19 Sisif kernel: [   11.786567] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Apr 30 23:54:19 Sisif kernel: [   11.786584] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 30 23:54:19 Sisif kernel: [   11.786589] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 30 23:54:19 Sisif kernel: [   11.786618] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Apr 30 23:54:19 Sisif kernel: [   11.790534] ehci_hcd 0000:00:1d.7: debug port 1
Apr 30 23:54:19 Sisif kernel: [   11.790542] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr 30 23:54:19 Sisif kernel: [   11.790551] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80000
Apr 30 23:54:19 Sisif kernel: [   11.805417] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 30 23:54:19 Sisif kernel: [   11.805547] usb usb5: configuration #1 chosen from 1 choice
Apr 30 23:54:19 Sisif kernel: [   11.805575] hub 5-0:1.0: USB hub found
Apr 30 23:54:19 Sisif kernel: [   11.805584] hub 5-0:1.0: 8 ports detected
Apr 30 23:54:19 Sisif kernel: [   13.927291] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Apr 30 23:54:19 Sisif kernel: [   11.969407] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Apr 30 23:54:19 Sisif kernel: [   11.969443] b44.c:v2.0
Apr 30 23:54:19 Sisif kernel: [   13.986365] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Apr 30 23:54:19 Sisif kernel: [   11.989671] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:85:80:f6
Apr 30 23:54:19 Sisif kernel: [   14.039063] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 30 23:54:19 Sisif kernel: [   12.036777] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 23:54:19 Sisif kernel: [   12.036824] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 23:54:19 Sisif kernel: [   12.036838] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Apr 30 23:54:19 Sisif kernel: [   12.040489] ata_piix 0000:00:1f.2: version 2.12
Apr 30 23:54:19 Sisif kernel: [   12.040497] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Apr 30 23:54:19 Sisif kernel: [   12.040519] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Apr 30 23:54:19 Sisif kernel: [   12.040558] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 30 23:54:19 Sisif kernel: [   12.040651] scsi0 : ata_piix
Apr 30 23:54:19 Sisif kernel: [   12.040704] scsi1 : ata_piix
Apr 30 23:54:19 Sisif kernel: [   12.041531] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Apr 30 23:54:19 Sisif kernel: [   12.041535] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Apr 30 23:54:19 Sisif kernel: [   12.206323] ata1.00: ATA-7: ST9120822AS, 3.CDD, max UDMA/133
Apr 30 23:54:19 Sisif kernel: [   12.206328] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
Apr 30 23:54:19 Sisif kernel: [   12.222980] ata1.00: configured for UDMA/133
Apr 30 23:54:19 Sisif kernel: [   14.582470] ata2.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1B, max UDMA/33
Apr 30 23:54:19 Sisif kernel: [   14.778309] ata2.00: configured for UDMA/33
Apr 30 23:54:19 Sisif kernel: [   12.761595] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.CD PQ: 0 ANSI: 5
Apr 30 23:54:19 Sisif kernel: [   12.763942] scsi 1:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
Apr 30 23:54:19 Sisif kernel: [   12.771581] Driver 'sd' needs updating - please use bus_type methods
Apr 30 23:54:19 Sisif kernel: [   12.771669] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 23:54:19 Sisif kernel: [   12.771683] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 23:54:19 Sisif kernel: [   12.771686] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 23:54:19 Sisif kernel: [   12.771703] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 23:54:19 Sisif kernel: [   12.771754] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Apr 30 23:54:19 Sisif kernel: [   12.771764] sd 0:0:0:0: [sda] Write Protect is off
Apr 30 23:54:19 Sisif kernel: [   12.771767] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 30 23:54:19 Sisif kernel: [   12.771784] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 30 23:54:19 Sisif kernel: [   12.771788]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Apr 30 23:54:19 Sisif kernel: [   12.865370]  sda1 sda2 sda3
Apr 30 23:54:19 Sisif kernel: [   12.877656] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 30 23:54:19 Sisif kernel: [   14.901095] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 30 23:54:19 Sisif kernel: [   14.901117] sr 1:0:0:0: Attached scsi generic sg1 type 5
Apr 30 23:54:19 Sisif kernel: [   12.896942] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr 30 23:54:19 Sisif kernel: [   12.896947] Uniform CD-ROM driver Revision: 3.20
Apr 30 23:54:19 Sisif kernel: [   12.897008] sr 1:0:0:0: Attached scsi CD-ROM sr0
Apr 30 23:54:19 Sisif kernel: [   13.305033] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc00026e60070]
Apr 30 23:54:19 Sisif kernel: [   13.366927] Attempting manual resume
Apr 30 23:54:19 Sisif kernel: [   13.366931] swsusp: Resume From Partition 8:2
Apr 30 23:54:19 Sisif kernel: [   13.366933] PM: Checking swsusp image.
Apr 30 23:54:19 Sisif kernel: [   13.367111] PM: Resume from disk failed.
Apr 30 23:54:19 Sisif kernel: [   15.425752] kjournald starting.  Commit interval 5 seconds
Apr 30 23:54:19 Sisif kernel: [   13.408881] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 23:54:19 Sisif kernel: [   21.420915] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 30 23:54:19 Sisif kernel: [   23.609762] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 30 23:54:19 Sisif kernel: [   23.691588] Linux agpgart interface v0.102
Apr 30 23:54:19 Sisif kernel: [   23.714650] agpgart: Detected an Intel 945GM Chipset.
Apr 30 23:54:19 Sisif kernel: [   23.715220] agpgart: Detected 7932K stolen memory.
Apr 30 23:54:19 Sisif kernel: [   23.733445] agpgart: AGP aperture is 256M @ 0xd0000000
Apr 30 23:54:19 Sisif kernel: [   23.784468] ACPI: AC Adapter [AC] (on-line)
Apr 30 23:54:19 Sisif kernel: [   23.908334] ACPI: Battery Slot [BAT0] (battery present)
Apr 30 23:54:19 Sisif kernel: [   23.926671] input: Lid Switch as /devices/virtual/input/input2
Apr 30 23:54:19 Sisif kernel: [   23.927090] ACPI: Lid Switch [LID]
Apr 30 23:54:19 Sisif kernel: [   23.927158] input: Power Button (CM) as /devices/virtual/input/input3
Apr 30 23:54:19 Sisif kernel: [   23.950469] ACPI: Power Button (CM) [PBTN]
Apr 30 23:54:19 Sisif kernel: [   23.950594] input: Sleep Button (CM) as /devices/virtual/input/input4
Apr 30 23:54:19 Sisif kernel: [   23.982422] ACPI: Sleep Button (CM) [SBTN]
Apr 30 23:54:19 Sisif kernel: [   24.343802] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input5
Apr 30 23:54:19 Sisif kernel: [   24.374236] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr 30 23:54:19 Sisif kernel: [   24.382051] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
Apr 30 23:54:19 Sisif kernel: [   24.406239] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Apr 30 23:54:19 Sisif kernel: [   24.406418] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input7
Apr 30 23:54:19 Sisif kernel: [   24.438212] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Apr 30 23:54:19 Sisif kernel: [   24.438379] ACPI: WMI-Acer: Mapper loaded
Apr 30 23:54:19 Sisif kernel: [   25.120609] iTCO_vendor_support: vendor-support=0
Apr 30 23:54:19 Sisif kernel: [   25.157910] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Apr 30 23:54:19 Sisif kernel: [   25.158018] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Apr 30 23:54:19 Sisif kernel: [   25.158060] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 30 23:54:19 Sisif kernel: [   23.324923] intel_rng: FWH not detected
Apr 30 23:54:19 Sisif kernel: [   23.425146] input: PC Speaker as /devices/platform/pcspkr/input/input8
Apr 30 23:54:19 Sisif kernel: [   23.603857] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
Apr 30 23:54:19 Sisif kernel: [   23.603887] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 30 23:54:19 Sisif kernel: [   25.653694] sdhci: Secure Digital Host Controller Interface driver
Apr 30 23:54:19 Sisif kernel: [   25.653697] sdhci: Copyright(c) Pierre Ossman
Apr 30 23:54:19 Sisif kernel: [   25.725170] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
Apr 30 23:54:19 Sisif kernel: [   25.725198] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
Apr 30 23:54:19 Sisif kernel: [   25.725269] mmc0: SDHCI at 0xef9fd500 irq 23 DMA
Apr 30 23:54:19 Sisif kernel: [   23.744791] b43-phy0: Broadcom 4311 WLAN found
Apr 30 23:54:19 Sisif kernel: [   23.812179] phy0: Selected rate control algorithm 'simple'
Apr 30 23:54:19 Sisif kernel: [   24.190706] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
Apr 30 23:54:19 Sisif kernel: [   26.243734] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
Apr 30 23:54:19 Sisif kernel: [   24.271384] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Apr 30 23:54:19 Sisif kernel: [   26.915095] udev: renamed network interface wlan0 to eth1
Apr 30 23:54:19 Sisif kernel: [   24.983215] input: b43-phy0 as /devices/virtual/input/input10
Apr 30 23:54:19 Sisif kernel: [   25.254355] lp: driver loaded but no devices found
Apr 30 23:54:19 Sisif kernel: [   25.562719] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
Apr 30 23:54:19 Sisif kernel: [   28.119894] EXT3 FS on sda1, internal journal
Apr 30 23:54:19 Sisif kernel: [   26.478872] Registered led device: b43-phy0:tx
Apr 30 23:54:19 Sisif kernel: [   26.478900] Registered led device: b43-phy0:rx
Apr 30 23:54:19 Sisif kernel: [   26.478925] Registered led device: b43-phy0:radio
Apr 30 23:54:19 Sisif kernel: [   26.527243] NET: Registered protocol family 17
Apr 30 23:54:19 Sisif kernel: [   29.174117] kjournald starting.  Commit interval 5 seconds
Apr 30 23:54:19 Sisif kernel: [   27.157483] EXT3 FS on sda3, internal journal
Apr 30 23:54:19 Sisif kernel: [   27.157488] EXT3-fs: mounted filesystem with ordered data mode.
Apr 30 23:54:19 Sisif kernel: [   27.793702] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 30 23:54:19 Sisif kernel: [   29.126164] RPC: Registered udp transport module.
Apr 30 23:54:19 Sisif kernel: [   29.126167] RPC: Registered tcp transport module.
Apr 30 23:54:19 Sisif kernel: [   29.760835] No dock devices found.
Apr 30 23:54:20 Sisif avahi-daemon[5291]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Apr 30 23:54:20 Sisif avahi-daemon[5291]: Successfully dropped root privileges.
Apr 30 23:54:20 Sisif avahi-daemon[5291]: avahi-daemon 0.6.22 starting up.
Apr 30 23:54:20 Sisif avahi-daemon[5291]: Successfully called chroot().
Apr 30 23:54:20 Sisif avahi-daemon[5291]: Successfully dropped remaining capabilities.
Apr 30 23:54:20 Sisif avahi-daemon[5291]: No service file found in /etc/avahi/services.
Apr 30 23:54:20 Sisif avahi-daemon[5291]: Network interface enumeration completed.
Apr 30 23:54:20 Sisif avahi-daemon[5291]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 30 23:54:20 Sisif avahi-daemon[5291]: Server startup complete. Host name is Sisif.local. Local service cookie is 2866837722.
Apr 30 23:54:20 Sisif kernel: [   32.084098] ppdev: user-space parallel port driver
Apr 30 23:54:21 Sisif dhclient: DHCPREQUEST of 192.168.0.118 on eth0 to 255.255.255.255 port 67
Apr 30 23:54:21 Sisif kernel: [   32.263325] audit(1209588861.138:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5325 profile="/usr/sbin/cupsd" namespace="default"
Apr 30 23:54:21 Sisif kernel: [   32.311766] apm: BIOS not found.
Apr 30 23:54:22 Sisif kernel: [   33.862863] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Apr 30 23:54:22 Sisif exportfs[5498]: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.10.2:/home/itch/Blonda".   Assuming default behaviour ('no_subtree_check').   NOTE: this default has changed since nfs-utils version 1.0.x 
Apr 30 23:54:22 Sisif kernel: [   34.109681] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Apr 30 23:54:23 Sisif kernel: [   34.125466] NFSD: starting 90-second grace period
Apr 30 23:54:24 Sisif nmbd[5571]: [2008/04/30 23:54:24, 0] nmbd/nmbd_subnetdb.c:create_subnets(190) 
Apr 30 23:54:24 Sisif nmbd[5571]:   create_subnets: No local interfaces ! 
Apr 30 23:54:24 Sisif nmbd[5571]: [2008/04/30 23:54:24, 0] nmbd/nmbd_subnetdb.c:create_subnets(191) 
Apr 30 23:54:24 Sisif nmbd[5571]:   create_subnets: Waiting for an interface to appear ... 
Apr 30 23:54:25 Sisif dhcdbd: Started up.
Apr 30 23:54:25 Sisif hcid[5648]: Bluetooth HCI daemon
Apr 30 23:54:25 Sisif kernel: [   36.936902] Bluetooth: Core ver 2.11
Apr 30 23:54:25 Sisif kernel: [   36.937779] NET: Registered protocol family 31
Apr 30 23:54:25 Sisif kernel: [   36.937786] Bluetooth: HCI device and connection manager initialized
Apr 30 23:54:25 Sisif kernel: [   36.937794] Bluetooth: HCI socket layer initialized
Apr 30 23:54:25 Sisif hcid[5648]: Starting SDP server
Apr 30 23:54:26 Sisif kernel: [   37.145273] Bluetooth: L2CAP ver 2.9
Apr 30 23:54:26 Sisif kernel: [   37.145282] Bluetooth: L2CAP socket layer initialized
Apr 30 23:54:26 Sisif hcid[5648]: Created local server at unix:abstract=/var/run/dbus-sqZGmgsgKQ,guid=f7e60284ecf0562644eba3454818dc82
Apr 30 23:54:26 Sisif audio[5670]: Bluetooth Audio daemon
Apr 30 23:54:26 Sisif input[5671]: Bluetooth Input daemon
Apr 30 23:54:26 Sisif audio[5670]: Unix socket created: 5
Apr 30 23:54:26 Sisif audio[5670]: audio.conf: Key file does not have key 'Enable'
Apr 30 23:54:26 Sisif audio[5670]: audio.conf: Key file does not have key 'Disable'
Apr 30 23:54:26 Sisif input[5671]: Registered input manager path:/org/bluez/input
Apr 30 23:54:26 Sisif kernel: [   37.314614] Bluetooth: RFCOMM socket layer initialized
Apr 30 23:54:26 Sisif kernel: [   37.314637] Bluetooth: RFCOMM TTY layer initialized
Apr 30 23:54:26 Sisif kernel: [   37.314642] Bluetooth: RFCOMM ver 1.8
Apr 30 23:54:26 Sisif audio[5670]: add_service_record: got record id 0x10000
Apr 30 23:54:26 Sisif audio[5670]: audio.conf: Key file does not have key 'Disable'
Apr 30 23:54:26 Sisif audio[5670]: audio.conf: Key file does not have group 'A2DP'
Apr 30 23:54:26 Sisif last message repeated 3 times
Apr 30 23:54:26 Sisif audio[5670]: SEP 0x806d578 registered: type:0 codec:0 seid:1
Apr 30 23:54:26 Sisif audio[5670]: add_service_record: got record id 0x10001
Apr 30 23:54:26 Sisif audio[5670]: add_service_record: got record id 0x10002
Apr 30 23:54:26 Sisif audio[5670]: add_service_record: got record id 0x10003
Apr 30 23:54:26 Sisif audio[5670]: Registered manager path:/org/bluez/audio
Apr 30 23:54:27 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr 30 23:54:27 Sisif ntpd[5728]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 23:54:27 Sisif ntpd[5731]: precision = 1.000 usec
Apr 30 23:54:27 Sisif kernel: [   38.781106] NET: Registered protocol family 10
Apr 30 23:54:27 Sisif kernel: [   38.781665] lo: Disabled Privacy Extensions
Apr 30 23:54:27 Sisif kernel: [   38.784828] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 30 23:54:27 Sisif kernel: [   38.786780] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:54:27 Sisif ntpd[5731]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 23:54:27 Sisif ntpd[5731]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 23:54:27 Sisif ntpd[5731]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 23:54:27 Sisif ntpd[5731]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 23:54:27 Sisif ntpd[5731]: kernel time sync status 0040
Apr 30 23:54:27 Sisif ntpd[5731]: frequency initialized -57.977 PPM from /var/lib/ntp/ntp.drift
Apr 30 23:54:29 Sisif kernel: [   43.106059] [drm] Initialized drm 1.1.0 20060810
Apr 30 23:54:30 Sisif ntpd_initres[5752]: host name not found: ntp2a.mcc.ac.uk
Apr 30 23:54:30 Sisif ntpd_initres[5752]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 23:54:30 Sisif ntpd_initres[5752]: host name not found: ntp.landau.ac.ru
Apr 30 23:54:30 Sisif ntpd_initres[5752]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 23:54:30 Sisif kernel: [   41.194364] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 23:54:30 Sisif kernel: [   41.194382] PCI: Setting latency timer of device 0000:00:02.0 to 64
Apr 30 23:54:30 Sisif kernel: [   43.213166] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr 30 23:54:30 Sisif anacron[5800]: Anacron 2.3 started on 2008-04-30
Apr 30 23:54:30 Sisif anacron[5800]: Normal exit (0 jobs run)
Apr 30 23:54:31 Sisif dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 30 23:54:31 Sisif /usr/sbin/cron[5833]: (CRON) INFO (pidfile fd = 3)
Apr 30 23:54:31 Sisif /usr/sbin/cron[5834]: (CRON) STARTUP (fork ok)
Apr 30 23:54:31 Sisif /usr/sbin/cron[5834]: (CRON) INFO (Running @reboot jobs)
Apr 30 23:54:32 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 23:54:32 Sisif kernel: [   43.397174] input: b43-phy0 as /devices/virtual/input/input11
Apr 30 23:54:33 Sisif kernel: [   46.716350] Registered led device: b43-phy0:tx
Apr 30 23:54:33 Sisif kernel: [   46.716381] Registered led device: b43-phy0:rx
Apr 30 23:54:33 Sisif kernel: [   46.716406] Registered led device: b43-phy0:radio
Apr 30 23:54:33 Sisif kernel: [   46.760057] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:54:34 Sisif kernel: [   45.133932] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Apr 30 23:54:34 Sisif kernel: [   47.166910] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 23:54:34 Sisif kernel: [   47.367645] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 23:54:34 Sisif kernel: [   47.463328] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 23:54:34 Sisif kernel: [   45.446762] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 23:54:34 Sisif kernel: [   45.446822] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 23:54:34 Sisif kernel: [   45.452071] ndiswrapper: using IRQ 16
Apr 30 23:54:34 Sisif kernel: [   45.810197] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 23:54:34 Sisif kernel: [   45.810291] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 23:54:34 Sisif kernel: [   47.831039] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 23:54:34 Sisif kernel: [   47.831118] udev: renamed network interface wlan0 to eth1
Apr 30 23:54:34 Sisif kernel: [   47.834463] usbcore: registered new interface driver ndiswrapper
Apr 30 23:54:34 Sisif kernel: [   45.823490] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:54:34 Sisif dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Apr 30 23:54:34 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 23:54:34 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 23:54:34 Sisif dhclient: All rights reserved.
Apr 30 23:54:34 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 23:54:34 Sisif dhclient: 
Apr 30 23:54:34 Sisif kernel: [   45.935135] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:54:34 Sisif kernel: [   48.022623] ndiswrapper: device eth1 removed
Apr 30 23:54:34 Sisif kernel: [   48.022658] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Apr 30 23:54:34 Sisif kernel: [   48.022775] usbcore: deregistering interface driver ndiswrapper
Apr 30 23:54:34 Sisif kernel: [   48.055783] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Apr 30 23:54:34 Sisif kernel: [   48.069441] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Apr 30 23:54:34 Sisif kernel: [   48.070603] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 30 23:54:34 Sisif kernel: [   48.070680] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Apr 30 23:54:34 Sisif kernel: [   48.076168] ndiswrapper: using IRQ 16
Apr 30 23:54:35 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 23:54:35 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 23:54:35 Sisif dhclient: All rights reserved.
Apr 30 23:54:35 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 23:54:35 Sisif dhclient: 
Apr 30 23:54:35 Sisif kernel: [   48.437405] wlan0: ethernet device 00:19:7e:a0:3d:2a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
Apr 30 23:54:35 Sisif kernel: [   48.437504] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Apr 30 23:54:35 Sisif modprobe: WARNING: Not loading blacklisted module ndiswrapper 
Apr 30 23:54:35 Sisif kernel: [   48.441323] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Apr 30 23:54:35 Sisif kernel: [   48.441418] udev: renamed network interface wlan0 to eth1
Apr 30 23:54:35 Sisif kernel: [   48.451611] usbcore: registered new interface driver ndiswrapper
Apr 30 23:54:35 Sisif kernel: [   48.463801] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:54:35 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 23:54:35 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 23:54:35 Sisif dhclient: Sending on   Socket/fallback
Apr 30 23:54:36 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 23:54:36 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 23:54:36 Sisif dhclient: Sending on   Socket/fallback
Apr 30 23:54:38 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 30 23:54:40 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 23:54:44 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 23:54:45 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr 30 23:54:48 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 23:54:56 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Apr 30 23:54:58 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr 30 23:54:59 Sisif hcid[5648]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Apr 30 23:54:59 Sisif hcid[5648]: Default authorization agent (:1.18, /org/bluez/auth) registered
Apr 30 23:55:03 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Apr 30 23:55:06 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 30 23:55:09 Sisif dhclient: No DHCPOFFERS received.
Apr 30 23:55:09 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 23:55:09 Sisif avahi-autoipd(eth1)[6551]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Apr 30 23:55:09 Sisif kernel: [   80.177321] CPU0 attaching NULL sched-domain.
Apr 30 23:55:09 Sisif kernel: [   80.177329] CPU1 attaching NULL sched-domain.
Apr 30 23:55:09 Sisif kernel: [   80.191015] CPU0 attaching sched-domain:
Apr 30 23:55:09 Sisif kernel: [   80.191021]  domain 0: span 03
Apr 30 23:55:09 Sisif kernel: [   80.191023]   groups: 01 02
Apr 30 23:55:09 Sisif kernel: [   80.191027] CPU1 attaching sched-domain:
Apr 30 23:55:09 Sisif kernel: [   80.191029]  domain 0: span 03
Apr 30 23:55:09 Sisif kernel: [   80.191030]   groups: 02 01
Apr 30 23:55:09 Sisif avahi-autoipd(eth1)[6551]: Successfully called chroot().
Apr 30 23:55:09 Sisif avahi-autoipd(eth1)[6551]: Successfully dropped root privileges.
Apr 30 23:55:09 Sisif avahi-autoipd(eth1)[6551]: Starting with address 169.254.4.188
Apr 30 23:55:10 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Apr 30 23:55:14 Sisif avahi-autoipd(eth1)[6551]: Callout BIND, address 169.254.4.188 on interface eth1
Apr 30 23:55:15 Sisif avahi-daemon[5291]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 23:55:15 Sisif avahi-daemon[5291]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 23:55:15 Sisif avahi-daemon[5291]: Registering new address record for 169.254.4.188 on eth1.IPv4.
Apr 30 23:55:18 Sisif avahi-autoipd(eth1)[6551]: Successfully claimed IP address 169.254.4.188
Apr 30 23:55:19 Sisif ntpd[5731]: ntpd exiting on signal 15
Apr 30 23:55:29 Sisif dhclient: No DHCPOFFERS received.
Apr 30 23:55:29 Sisif dhclient: Trying recorded lease 192.168.1.102
Apr 30 23:55:29 Sisif avahi-autoipd(eth1)[6551]: A routable address has been configured.
Apr 30 23:55:29 Sisif avahi-autoipd(eth1)[6551]: Callout UNBIND, address 169.254.4.188 on interface eth1
Apr 30 23:55:29 Sisif avahi-daemon[5291]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 23:55:29 Sisif avahi-daemon[5291]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 23:55:29 Sisif avahi-daemon[5291]: Registering new address record for 192.168.1.102 on eth1.IPv4.
Apr 30 23:55:29 Sisif avahi-daemon[5291]: Withdrawing address record for 169.254.4.188 on eth1.
Apr 30 23:55:39 Sisif avahi-autoipd(eth1)[6551]: No longer a routable address configured, restarting probe process.
Apr 30 23:55:39 Sisif avahi-daemon[5291]: Withdrawing address record for 192.168.1.102 on eth1.
Apr 30 23:55:39 Sisif avahi-daemon[5291]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 23:55:39 Sisif avahi-daemon[5291]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 23:55:39 Sisif dhclient: No working leases in persistent database - sleeping.
Apr 30 23:55:39 Sisif ntpdate[6839]: can't find host ntp2a.mcc.ac.uk 
Apr 30 23:55:39 Sisif ntpdate[6839]: can't find host ntp.landau.ac.ru 
Apr 30 23:55:39 Sisif ntpdate[6839]: no servers can be used, exiting
Apr 30 23:55:39 Sisif ntpd[7307]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Apr 30 23:55:39 Sisif ntpd[7308]: precision = 1.000 usec
Apr 30 23:55:39 Sisif ntpd[7308]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 30 23:55:39 Sisif ntpd[7308]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 30 23:55:39 Sisif ntpd[7308]: Listening on interface #2 lo, ::1#123 Enabled
Apr 30 23:55:39 Sisif ntpd[7308]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 30 23:55:39 Sisif ntpd[7308]: kernel time sync status 0040
Apr 30 23:55:39 Sisif ntpd[7308]: frequency initialized -57.977 PPM from /var/lib/ntp/ntp.drift
Apr 30 23:55:41 Sisif ntpd_initres[7309]: host name not found: ntp2a.mcc.ac.uk
Apr 30 23:55:41 Sisif ntpd_initres[7309]: couldn't resolve `ntp2a.mcc.ac.uk', giving up on it
Apr 30 23:55:41 Sisif ntpd_initres[7309]: host name not found: ntp.landau.ac.ru
Apr 30 23:55:41 Sisif ntpd_initres[7309]: couldn't resolve `ntp.landau.ac.ru', giving up on it
Apr 30 23:55:44 Sisif avahi-autoipd(eth1)[6551]: Callout BIND, address 169.254.4.188 on interface eth1
Apr 30 23:55:44 Sisif avahi-daemon[5291]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 23:55:44 Sisif avahi-daemon[5291]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 23:55:44 Sisif avahi-daemon[5291]: Registering new address record for 169.254.4.188 on eth1.IPv4.
Apr 30 23:55:48 Sisif avahi-autoipd(eth1)[6551]: Successfully claimed IP address 169.254.4.188
Apr 30 23:56:00 Sisif avahi-daemon[5291]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 30 23:56:00 Sisif avahi-daemon[5291]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.188.
Apr 30 23:56:00 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 23:56:00 Sisif avahi-autoipd(eth1)[6551]: SIOCSIFFLAGS failed: Permission denied
Apr 30 23:56:00 Sisif avahi-autoipd(eth1)[6551]: Callout STOP, address 169.254.4.188 on interface eth1
Apr 30 23:56:00 Sisif dhclient: receive_packet failed on eth1: Network is down
Apr 30 23:56:00 Sisif avahi-daemon[5291]: Withdrawing address record for 169.254.4.188 on eth1.
Apr 30 23:56:00 Sisif avahi-autoipd(eth1)[6552]: client: RTNETLINK answers: No such process
Apr 30 23:56:00 Sisif kernel: [  131.774305] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:56:00 Sisif kernel: [  131.823381] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 30 23:56:00 Sisif dhclient: There is already a pid file /var/run/dhclient.pid with pid 7278
Apr 30 23:56:00 Sisif dhclient: removed stale PID file
Apr 30 23:56:00 Sisif dhclient: Internet Systems Consortium DHCP Client V3.0.6
Apr 30 23:56:00 Sisif dhclient: Copyright 2004-2007 Internet Systems Consortium.
Apr 30 23:56:00 Sisif dhclient: All rights reserved.
Apr 30 23:56:00 Sisif dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 23:56:00 Sisif dhclient: 
Apr 30 23:56:01 Sisif dhclient: Listening on LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 23:56:01 Sisif dhclient: Sending on   LPF/eth1/00:19:7e:a0:3d:2a
Apr 30 23:56:01 Sisif dhclient: Sending on   Socket/fallback
Apr 30 23:56:01 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 23:56:04 Sisif kernel: [  135.525762] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 30 23:56:05 Sisif avahi-daemon[5291]: Registering new address record for fe80::219:7eff:fea0:3d2a on eth1.*.
Apr 30 23:56:07 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 23:56:13 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr 30 23:56:14 Sisif kernel: [  146.071232] eth1: no IPv6 routers present
Apr 30 23:56:18 Sisif dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr 30 23:56:18 Sisif dhclient: DHCPOFFER of 192.168.1.102 from 192.168.1.1
Apr 30 23:56:18 Sisif dhclient: DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
Apr 30 23:56:18 Sisif dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
Apr 30 23:56:18 Sisif avahi-daemon[5291]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.102.
Apr 30 23:56:18 Sisif avahi-daemon[5291]: New relevant interface eth1.IPv4 for mDNS.
Apr 30 23:56:18 Sisif avahi-daemon[5291]: Registering new address record for 192.168.1.102 on eth1.IPv4.
Apr 30 23:56:18 Sisif dhclient: bound to 192.168.1.102 -- renewal in 41137 seconds.
Apr 30 23:56:33 Sisif nmbd[5571]: [2008/04/30 23:56:33, 0] libsmb/nmblib.c:send_udp(793) 
Apr 30 23:56:33 Sisif nmbd[5571]:   Packet send failed to 169.254.255.255(138) ERRNO=Invalid argument 
May  1 00:00:40 Sisif ntpd[7308]: Listening on interface #4 eth1, fe80::219:7eff:fea0:3d2a#123 Enabled
May  1 00:00:40 Sisif ntpd[7308]: Listening on interface #5 eth1, 192.168.1.102#123 Enabled
May  1 00:01:08 Sisif nmbd[5571]: [2008/05/01 00:01:08, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
May  1 00:01:08 Sisif nmbd[5571]:   ***** 
May  1 00:01:08 Sisif nmbd[5571]:    
May  1 00:01:08 Sisif nmbd[5571]:   Samba name server SISIF is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.102 
May  1 00:01:08 Sisif nmbd[5571]:    
May  1 00:01:08 Sisif nmbd[5571]:   ***** 
May  1 00:14:19 Sisif -- MARK --
May  1 00:17:01 Sisif /USR/SBIN/CRON[28734]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

Thank you.

---

### Post by deviant on 2008-05-01
Anyone ?

---

