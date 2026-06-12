---
title: "kern.log, syslog, debug : growing up, growing up..."
date: 2007-01-15
forum: General Help
---

### Post by Slasher Fun on 2007-01-15
Hi everybody :) 

It seems I have a problem with my log files, stored in /var/log. Kern.log, syslog and debug's sizes are growing up and growing up, making my / partition to be full if I don't empty them...

They all have the same content, it looks like :
```
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.468000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.468000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.468000] SMAC: FromHostIP: could not find IP 82.211.81.186 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.472000] SMAC: FromHostIP: could not find IP 82.211.81.186 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.504000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.508000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.508000] SMAC: FromHostIP: could not find IP 82.211.81.186 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.508000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.512000] SMAC: FromHostIP: could not find IP 82.211.81.186 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.528000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.536000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.536000] SMAC: FromHostIP: could not find IP 82.211.81.186 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.536000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.536000] SMAC: FromHostIP: could not find IP 82.211.81.186 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.536000] SMAC: FromHostIP: could not find IP 82.211.81.186 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.560000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182079.588000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182080.072000] SMAC: FromHostIP: could not find IP 82.243.124.76 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182080.208000] SMAC: FromHostIP: could not find IP 84.105.11.79 in lookup, so drop
Jan 15 22:49:34 mathieu-laptop kernel: [17182080.208000] SMAC: FromHostIP: could not find IP 64.180.180.99 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop kernel: [17182080.424000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop kernel: [17182080.632000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop kernel: [17182080.920000] SMAC: FromHostIP: could not find IP 66.102.1.101 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop kernel: [17182080.920000] SMAC: FromHostIP: could not find IP 66.102.1.101 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop kernel: [17182080.996000] SMAC: FromHostIP: could not find IP 66.102.1.101 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop kernel: [17182081.036000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop kernel: [17182081.112000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop kernel: [17182081.112000] SMAC: FromHostIP: could not find IP 66.102.1.101 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop kernel: [17182081.116000] SMAC: FromHostIP: could not find IP 66.102.1.101 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop kernel: [17182081.176000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop kernel: [17182081.236000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop last message repeated 2 times
Jan 15 22:49:35 mathieu-laptop kernel: [17182081.236000] SMAC: FromHostIP: could not find IP 66.102.1.101 in lookup, so drop
Jan 15 22:49:35 mathieu-laptop kernel: [17182081.236000] SMAC: FromHostIP: could not find IP 66.102.1.101 in lookup, so drop
Jan 15 22:49:36 mathieu-laptop kernel: [17182081.404000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:36 mathieu-laptop kernel: [17182081.404000] SMAC: FromHostIP: could not find IP 66.102.1.101 in lookup, so drop
Jan 15 22:49:36 mathieu-laptop kernel: [17182081.532000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:36 mathieu-laptop kernel: [17182081.616000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 22:49:36 mathieu-laptop kernel: [17182081.656000] SMAC: FromHostIP: could not find IP 66.102.1.101 in lookup, so drop

```

So as you can see, always the sames lines, several times in one second... 192.168.1.2 is the local IP of my computer, and all the other one's belong to... Google ! I don't even have any Google program launched...

Any idea ? Thanks ;)

---

### Post by peabody on 2007-01-15
I believe these entries have something to do with your wireless nic driver (could be wrong).  There may be a way to tweak the /etc/syslog.conf file to spew them somewhere else (preferably /dev/null) but I confess that's not realm of expertise.  Anyone?

---

### Post by Slasher Fun on 2007-01-15
If this can help, I'm using an ipw2200 WiFi chipset (Acer Aspire 1692WLMi) with NetworkManager on an Ubuntu Edgy.

---

### Post by peabody on 2007-01-15
Well, why don't we figure out if it is or isn't your NIC.  Try disabling it for a while and see if the messages go away.

If it is your nic, I hate to say it, but those messages look reminiscent of a network scan.  Could be bad news.

---

### Post by Slasher Fun on 2007-01-15
Ok, so I disabled my WiFi interface at 23:26:37 from NetworkManager's interface, and here is what I got : 

Syslog :
```
Jan 15 23:26:30 mathieu-laptop kernel: [17184295.664000] SMAC: FromHostIP: could not find IP 66.102.1.102 in lookup, so drop
Jan 15 23:26:37 mathieu-laptop NetworkManager: <information>^IGoing to sleep. 
Jan 15 23:26:37 mathieu-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 10302
Jan 15 23:26:37 mathieu-laptop dhclient: killed old client process, removed PID file
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.568000] bridge-eth1: disabling the bridge
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.568000] SMAC: Calling    : SMAC_SetMac
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.568000] SMAC: SMAC_SetMac: state d46f2800 mac 00000000
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.568000] SMAC: Returned   : SMAC_SetMac
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.636000] bridge-eth1: down
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset b (was 3ed173b, writing 661025)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset 3 (was 0, writing 2008)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset 2 (was 2000000, writing 2000003)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset 1 (was 2b00000, writing 2b00006)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset 0 (was 3ed173b, writing 169c14e4)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.912000] bridge-eth0: disabling the bridge
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.924000] bridge-eth0: down
Jan 15 23:26:37 mathieu-laptop dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Jan 15 23:26:37 mathieu-laptop dhclient: send_packet: Network is unreachable
Jan 15 23:26:37 mathieu-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] bridge-eth1: enabling the bridge
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] bridge-eth1: is a Wireless Adapter
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: Calling    : SMAC_InitState
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: SMAC_InitState: state e20b9800
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: Returned   : SMAC_InitState
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: Calling    : SMAC_SetMac
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: SMAC_SetMac: state e20b9800 mac f7d7c118
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: mac 0x00:0x12:0xf0:0x86:0x12:0x8f
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: Returned   : SMAC_SetMac
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] bridge-eth1: up
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.088000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:16 IPv6
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.088000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:38 mathieu-laptop kernel: [17184303.400000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:ff:86:12:8f IPv6
Jan 15 23:26:38 mathieu-laptop kernel: [17184303.400000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:39 mathieu-laptop kernel: [17184304.400000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:02 IPv6
Jan 15 23:26:39 mathieu-laptop kernel: [17184304.400000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:41 mathieu-laptop kernel: [17184307.188000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:42 mathieu-laptop kernel: [17184307.744000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:43 mathieu-laptop kernel: [17184308.400000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:02 IPv6
Jan 15 23:26:43 mathieu-laptop kernel: [17184308.400000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:43 mathieu-laptop kernel: [17184308.792000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:44 mathieu-laptop kernel: [17184310.248000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:16 IPv6
Jan 15 23:26:44 mathieu-laptop kernel: [17184310.248000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:45 mathieu-laptop kernel: [17184310.340000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:46 mathieu-laptop kernel: [17184311.460000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:46 mathieu-laptop kernel: [17184312.292000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:47 mathieu-laptop kernel: [17184312.392000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:47 mathieu-laptop kernel: [17184312.400000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:02 IPv6
Jan 15 23:26:47 mathieu-laptop kernel: [17184312.400000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:48 mathieu-laptop kernel: [17184313.400000] eth1: no IPv6 routers present
Jan 15 23:26:48 mathieu-laptop kernel: [17184314.128000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:51 mathieu-laptop kernel: [17184316.492000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:59 mathieu-laptop kernel: [17184324.692000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:59 mathieu-laptop kernel: [17184324.956000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:27:11 mathieu-laptop kernel: [17184336.900000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop

```

Debug :
```
Jan 15 23:26:30 mathieu-laptop kernel: [17184295.664000] SMAC: FromHostIP: could not find IP 66.102.1.102 in lookup, so drop
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.568000] bridge-eth1: disabling the bridge
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.568000] SMAC: Calling    : SMAC_SetMac
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.568000] SMAC: SMAC_SetMac: state d46f2800 mac 00000000
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.568000] SMAC: Returned   : SMAC_SetMac
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.636000] bridge-eth1: down
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset b (was 3ed173b, writing 661025)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset 3 (was 0, writing 2008)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset 2 (was 2000000, writing 2000003)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset 1 (was 2b00000, writing 2b00006)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset 0 (was 3ed173b, writing 169c14e4)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.912000] bridge-eth0: disabling the bridge
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.924000] bridge-eth0: down
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] bridge-eth1: enabling the bridge
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: Calling    : SMAC_InitState
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: SMAC_InitState: state e20b9800
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: Returned   : SMAC_InitState
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: Calling    : SMAC_SetMac
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: SMAC_SetMac: state e20b9800 mac f7d7c118
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: mac 0x00:0x12:0xf0:0x86:0x12:0x8f
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: Returned   : SMAC_SetMac
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] bridge-eth1: up
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.088000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:16 IPv6
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.088000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:38 mathieu-laptop kernel: [17184303.400000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:ff:86:12:8f IPv6
Jan 15 23:26:38 mathieu-laptop kernel: [17184303.400000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:39 mathieu-laptop kernel: [17184304.400000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:02 IPv6
Jan 15 23:26:39 mathieu-laptop kernel: [17184304.400000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:41 mathieu-laptop kernel: [17184307.188000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:42 mathieu-laptop kernel: [17184307.744000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:43 mathieu-laptop kernel: [17184308.400000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:02 IPv6
Jan 15 23:26:43 mathieu-laptop kernel: [17184308.400000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:43 mathieu-laptop kernel: [17184308.792000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:44 mathieu-laptop kernel: [17184310.248000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:16 IPv6
Jan 15 23:26:44 mathieu-laptop kernel: [17184310.248000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:45 mathieu-laptop kernel: [17184310.340000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:46 mathieu-laptop kernel: [17184311.460000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:46 mathieu-laptop kernel: [17184312.292000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:47 mathieu-laptop kernel: [17184312.392000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:47 mathieu-laptop kernel: [17184312.400000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:02 IPv6
Jan 15 23:26:47 mathieu-laptop kernel: [17184312.400000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:48 mathieu-laptop kernel: [17184313.400000] eth1: no IPv6 routers present
Jan 15 23:26:48 mathieu-laptop kernel: [17184314.128000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:51 mathieu-laptop kernel: [17184316.492000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:59 mathieu-laptop kernel: [17184324.692000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:59 mathieu-laptop kernel: [17184324.956000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop

```

Kern.log :
```
Jan 15 23:26:30 mathieu-laptop kernel: [17184295.664000] SMAC: FromHostIP: could not find IP 66.102.1.102 in lookup, so drop
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.568000] bridge-eth1: disabling the bridge
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.568000] SMAC: Calling    : SMAC_SetMac
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.568000] SMAC: SMAC_SetMac: state d46f2800 mac 00000000
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.568000] SMAC: Returned   : SMAC_SetMac
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.636000] bridge-eth1: down
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset b (was 3ed173b, writing 661025)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset 3 (was 0, writing 2008)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset 2 (was 2000000, writing 2000003)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset 1 (was 2b00000, writing 2b00006)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.652000] PM: Writing back config space on device 0000:06:08.0 at offset 0 (was 3ed173b, writing 169c14e4)
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.912000] bridge-eth0: disabling the bridge
Jan 15 23:26:37 mathieu-laptop kernel: [17184302.924000] bridge-eth0: down
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] bridge-eth1: enabling the bridge
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] bridge-eth1: is a Wireless Adapter
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: Calling    : SMAC_InitState
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: SMAC_InitState: state e20b9800
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: Returned   : SMAC_InitState
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: Calling    : SMAC_SetMac
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: SMAC_SetMac: state e20b9800 mac f7d7c118
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: mac 0x00:0x12:0xf0:0x86:0x12:0x8f
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] SMAC: Returned   : SMAC_SetMac
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.080000] bridge-eth1: up
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.088000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:16 IPv6
Jan 15 23:26:37 mathieu-laptop kernel: [17184303.088000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:38 mathieu-laptop kernel: [17184303.400000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:ff:86:12:8f IPv6
Jan 15 23:26:38 mathieu-laptop kernel: [17184303.400000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:39 mathieu-laptop kernel: [17184304.400000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:02 IPv6
Jan 15 23:26:39 mathieu-laptop kernel: [17184304.400000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:41 mathieu-laptop kernel: [17184307.188000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:42 mathieu-laptop kernel: [17184307.744000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:43 mathieu-laptop kernel: [17184308.400000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:02 IPv6
Jan 15 23:26:43 mathieu-laptop kernel: [17184308.400000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:43 mathieu-laptop kernel: [17184308.792000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:44 mathieu-laptop kernel: [17184310.248000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:16 IPv6
Jan 15 23:26:44 mathieu-laptop kernel: [17184310.248000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:45 mathieu-laptop kernel: [17184310.340000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:46 mathieu-laptop kernel: [17184311.460000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:46 mathieu-laptop kernel: [17184312.292000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:47 mathieu-laptop kernel: [17184312.392000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:47 mathieu-laptop kernel: [17184312.400000] SMAC: FromHost: non-IP & non-ARP (b|m)cast 00:12:f0:86:12:8f -> 33:33:00:00:00:02 IPv6
Jan 15 23:26:47 mathieu-laptop kernel: [17184312.400000] SMAC: FromHost: Forward unrecognized non-arp/ip b/mcast
Jan 15 23:26:48 mathieu-laptop kernel: [17184313.400000] eth1: no IPv6 routers present
Jan 15 23:26:48 mathieu-laptop kernel: [17184314.128000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:51 mathieu-laptop kernel: [17184316.492000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:59 mathieu-laptop kernel: [17184324.692000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop
Jan 15 23:26:59 mathieu-laptop kernel: [17184324.956000] SMAC: FromHostIP: could not find IP 192.168.1.2 in lookup, so drop

```

After the reactivation of the WiFi interface, the "could not find IP ... so drop" continues to appears as it did before, still with my local IP, some of my ISP IPs (like 194.117.200.11), and all the Google IPs. Note that the message only talks about my IP address when the WiFi is off.

---

### Post by peabody on 2007-01-15
Hmm, what kind of apps are running, Google Earth by any chance?

There's two things you could try, one is to divert the kernel type message via /etc/syslog.conf to another file.  You'd have to then manually check in on this file as it wouldn't get rotated via logrotate.

The other thing you could try is researching your nic driver to see if there's an option you could place in /etc/modprobe.conf to turn off its verbose messaging.

Only advice I've got to offer unfortunately.

---

### Post by Slasher Fun on 2007-01-15
I've checked with which launched application those messages appear, and the winner is... Mozilla Firefox ! (the one from the repositories). But suprises, even with all the firefox's extensions disabled, and what ever the webpage I'm showing can be, those messages continue to appear...

I'll try to erase my profile and to reinstall firefox, I'll see what I can get...

---

### Post by Slasher Fun on 2007-01-15
Oops... Actually the messages appear with firefox but also with aMSN, GAIM, Skype... So with every single program that would need an internet access...

If you don't have any idea of where the messages could come from, could you just explain me how to get them out of the three log files ?
Thanks for your help :-)

---

### Post by peabody on 2007-01-15
Here's a random thought, I remember there being, historically, issues with firefox and IPv6.  Not sure if that could be the problem here, just something to chew on I guess.

---

### Post by Slasher Fun on 2007-01-15
Forget about the firefox idea since I realized after that it happens with some other programs that I mentionned :-)

---

### Post by Slasher Fun on 2007-01-15
If you don't have any idea of where the messages could come from, could you just explain me how to get them out of the three log files ?

---

### Post by peabody on 2007-01-15
gotta finish an essay, try asking around, I'll check back later.

---

### Post by Slasher Fun on 2007-01-16
I've been looking at man syslog.conf, but I didn't really understand how to get my messages out of the 3 logs.. Any (last ?) help would be welcomed :-)

---

### Post by peabody on 2007-01-16
> **Slasher Fun said:**
> I've been looking at man syslog.conf, but I didn't really understand how to get my messages out of the 3 logs.. Any (last ?) help would be welcomed :-)

I believe the type of these messages are "kernel".  The syslog facility deals with types of messages and programs designed to use it decide what types messages should be and then send them to that type.  The /etc/syslog.conf file controls where each type of message goes.  I believe if you redirect kernel messages this will remove them from your logs, but I must warn that this would remove all kernel message which you may or may not want.  There may be a way to just remove this network card's messages but I can't be sure.  Any syslog experts out there wanna help?

---

### Post by dcstar on 2007-01-16
> **Slasher Fun said:**
> I've been looking at man syslog.conf, but I didn't really understand how to get my messages out of the 3 logs.. Any (last ?) help would be welcomed :-)

If "out" means delete, then install the **logrotate** package.

---

### Post by emersonrj on 2007-01-29
Hey, all. I've started seeing the same behaviour on my system, and it seems to have started only yesterday. For example:

```

rjemerson@smithwicks:/var/log$ ls -lh syslog*
-rw-r----- 1 root adm 648K 2007-01-29 09:14 syslog
-rw-r----- 1 root adm 133K 2007-01-29 07:37 syslog.0
-rw-r----- 1 root adm 1.6M 2007-01-28 07:36 syslog.1.gz
-rw-r----- 1 root adm  30K 2007-01-27 07:36 syslog.2.gz
-rw-r----- 1 root adm  13K 2007-01-26 07:37 syslog.3.gz
-rw-r----- 1 root adm  31K 2007-01-25 07:36 syslog.4.gz
-rw-r----- 1 root adm  25K 2007-01-24 07:35 syslog.5.gz
-rw-r----- 1 root adm  23K 2007-01-23 07:35 syslog.6.gz

```

It also seems to be related to my wireless NIC. I'd prefer to not disable all kernel messages, and I'd rather know the root of the problem than patch it by changing my logrotate config (unless, of course, this is the only option).

My NIC is a Broadcom BCM4318 [AirForce One 54g] (rev. 02) using the bcm43xx kernel module. Kernel version is 2.6.17-10-generic from the Ubuntu repositories.

Any help that's available would be greatly appreciated.

**UPDATE**
A little messing about makes me think this is a fault with either the kernel module or the firmware extracted using bcm43xx-fwcutter. Replacing the bcm43xx module with ndiswrapper makes 'tail -f /var/log/syslog' nice and boring again.

---

### Post by kreedtek21 on 2007-02-07
Do either of you have VMware installed?

---

### Post by kalou@kalou.net on 2007-03-03
Hi there,

   this error message is related to VMware, I can confirm .. my logs were filling with tons of:


(...)
 kernel[0]: SMAC: FromHostIP: could not find IP 192.168.1.168 in lookup, so drop
(...)


Stopped VMware, did nothing.
Issued the following command, and just stopped straight..

/Library/Application\ Support/VMware\ Fusion/vmnet-apps.sh stop


So report this to VMWare :)

Best Regards,


Kalou

---

