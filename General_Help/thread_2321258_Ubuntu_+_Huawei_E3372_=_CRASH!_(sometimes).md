---
title: "Ubuntu + Huawei E3372 = CRASH! (sometimes)"
date: 2016-04-21
forum: General Help
---

### Post by ubuser4 on 2016-04-21
I bought an **HP Pavilion 17-e057so** laptop and installed **Ubuntu 12.04 LTS** on it in late 2013. In January this year, I upgraded my internet connection to 4G and got a **Huawei E3372** **(E3372h-153)** USB modem. Everything worked fine until about a month ago. That's when my computer started crashing/freezing/hanging.

The first time this happened was when I was watching a YouTube video. I forgot to check the battery charge level, so the computer went into hibernation mode. After waiting a few seconds, I turned the power back on and waited for the connection to come back. It did, but after a couple of minutes, it disconnected and just a moment later, the screen froze and the last sound sample was played endlessly. Neither the keyboard nor the mouse worked, and I had to shut down the computer by holding down the power button. The kernel version was 3.13.0-83.

Here's a part of /var/log/syslog from the crash. The "\00"s at the end are apparently NULL characters:
```
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> wake requested (sleeping: yes  enabled: yes)
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> waking up and re-enabling...
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> WWAN now enabled by management service
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (wlan0): now managed
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (wlan0): bringing up device.
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth0): now managed
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth0): bringing up device.
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth0): preparing device.
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth0): deactivating device (reason 'managed') [2]
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC kernel: [  376.015613] r8169 0000:05:00.0 eth0: link down
Mar 20 19:21:50 u-HP-Pavilion-17-Notebook-PC kernel: [  376.015697] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 20 19:21:52 u-HP-Pavilion-17-Notebook-PC anacron[3707]: Anacron 2.3 started on 2016-03-20
Mar 20 19:21:52 u-HP-Pavilion-17-Notebook-PC anacron[3707]: Normal exit (0 jobs run)
Mar 20 19:21:56 u-HP-Pavilion-17-Notebook-PC kernel: [  381.485075] usb 1-1: new high-speed USB device number 4 using ehci-pci
Mar 20 19:21:56 u-HP-Pavilion-17-Notebook-PC kernel: [  381.618394] usb 1-1: New USB device found, idVendor=12d1, idProduct=1f01
Mar 20 19:21:56 u-HP-Pavilion-17-Notebook-PC kernel: [  381.618407] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Mar 20 19:21:56 u-HP-Pavilion-17-Notebook-PC kernel: [  381.618414] usb 1-1: Product: HUAWEI_MOBILE
Mar 20 19:21:56 u-HP-Pavilion-17-Notebook-PC kernel: [  381.618419] usb 1-1: Manufacturer: HUAWEI_MOBILE
Mar 20 19:21:56 u-HP-Pavilion-17-Notebook-PC kernel: [  381.618425] usb 1-1: SerialNumber: 0123456789ABCDEF
Mar 20 19:21:56 u-HP-Pavilion-17-Notebook-PC kernel: [  381.651145] usb-storage 1-1:1.0: USB Mass Storage device detected
Mar 20 19:21:56 u-HP-Pavilion-17-Notebook-PC kernel: [  381.651328] scsi6 : usb-storage 1-1:1.0
Mar 20 19:21:56 u-HP-Pavilion-17-Notebook-PC mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1"
Mar 20 19:21:56 u-HP-Pavilion-17-Notebook-PC mtp-probe: bus: 1, device: 4 was not an MTP device
Mar 20 19:21:57 u-HP-Pavilion-17-Notebook-PC kernel: [  382.656753] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Mar 20 19:21:57 u-HP-Pavilion-17-Notebook-PC kernel: [  382.657395] scsi 6:0:0:1: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
Mar 20 19:21:57 u-HP-Pavilion-17-Notebook-PC kernel: [  382.661765] sr1: scsi-1 drive
Mar 20 19:21:57 u-HP-Pavilion-17-Notebook-PC kernel: [  382.662031] sr 6:0:0:0: Attached scsi CD-ROM sr1
Mar 20 19:21:57 u-HP-Pavilion-17-Notebook-PC kernel: [  382.662199] sr 6:0:0:0: Attached scsi generic sg2 type 5
Mar 20 19:21:57 u-HP-Pavilion-17-Notebook-PC kernel: [  382.662677] sd 6:0:0:1: Attached scsi generic sg3 type 0
Mar 20 19:21:57 u-HP-Pavilion-17-Notebook-PC kernel: [  382.667273] sd 6:0:0:1: [sdb] Attached SCSI removable disk
Mar 20 19:21:57 u-HP-Pavilion-17-Notebook-PC usb_modeswitch: switching device 12d1:1f01 on 001/004
Mar 20 19:21:57 u-HP-Pavilion-17-Notebook-PC kernel: [  383.079683] usb 1-1: USB disconnect, device number 4
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC kernel: [  383.686191] usb 1-1: new high-speed USB device number 5 using ehci-pci
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC kernel: [  383.819260] usb 1-1: New USB device found, idVendor=12d1, idProduct=14dc
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC kernel: [  383.819270] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC kernel: [  383.819275] usb 1-1: Product: HUAWEI_MOBILE
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC kernel: [  383.819280] usb 1-1: Manufacturer: HUAWEI_MOBILE
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC kernel: [  383.977795] cdc_ether 1-1:1.0 eth1: register 'cdc_ether' at usb-0000:00:12.2-1, CDC Ethernet Device, 0c:5b:8f:27:9a:64
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC kernel: [  383.978318] usb-storage 1-1:1.2: USB Mass Storage device detected
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC kernel: [  383.978587] scsi7 : usb-storage 1-1:1.2
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1"
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC mtp-probe: bus: 1, device: 5 was not an MTP device
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1)
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1): no ifupdown configuration found.
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <warn> failed to allocate link cache: (-12) Object not found
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): carrier is OFF
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): new Ethernet device (driver: 'cdc_ether' ifindex: 5)
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/3
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): now managed
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): bringing up device.
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): carrier now ON (device state 20)
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): preparing device.
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): deactivating device (reason 'managed') [2]
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Added default wired connection 'Kiinteä yhteys 1' for /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): carrier now OFF (device state 30)
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Auto-activating connection 'Kiinteä yhteys 1'.
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) starting connection 'Kiinteä yhteys 1'
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> dhclient started with pid 3859
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Beginning IP6 addrconf.
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC kernel: [  384.032765] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC kernel: [  384.032959] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC dhclient: Copyright 2004-2011 Internet Systems Consortium.
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC dhclient: All rights reserved.
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC dhclient: 
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC dhclient: Listening on LPF/eth1/0c:5b:8f:27:9a:64
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   LPF/eth1/0c:5b:8f:27:9a:64
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   Socket/fallback
Mar 20 19:21:58 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Mar 20 19:21:59 u-HP-Pavilion-17-Notebook-PC kernel: [  384.983998] scsi 7:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
Mar 20 19:21:59 u-HP-Pavilion-17-Notebook-PC kernel: [  384.984335] sd 7:0:0:0: Attached scsi generic sg2 type 0
Mar 20 19:21:59 u-HP-Pavilion-17-Notebook-PC kernel: [  385.005361] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Mar 20 19:22:01 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Mar 20 19:22:04 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): carrier now ON (device state 70)
Mar 20 19:22:04 u-HP-Pavilion-17-Notebook-PC kernel: [  389.727131] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPREQUEST of 192.168.1.100 on eth1 to 255.255.255.255 port 67
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPOFFER of 192.168.1.100 from 192.168.1.1
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC dhclient: bound to 192.168.1.100 -- renewal in 39665 seconds.
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): DHCPv4 state changed preinit -> bound
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info>   address 192.168.1.100
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info>   prefix 24 (255.255.255.0)
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info>   gateway 192.168.1.1
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info>   nameserver '192.168.1.1'
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info>   nameserver '192.168.1.1'
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1224]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1224]: New relevant interface eth1.IPv4 for mDNS.
Mar 20 19:22:05 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1224]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Mar 20 19:22:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1224]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::e5b:8fff:fe27:9a64.
Mar 20 19:22:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1224]: New relevant interface eth1.IPv6 for mDNS.
Mar 20 19:22:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1224]: Registering new address record for fe80::e5b:8fff:fe27:9a64 on eth1.*.
Mar 20 19:22:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): writing resolv.conf to /sbin/resolvconf
Mar 20 19:22:06 u-HP-Pavilion-17-Notebook-PC dnsmasq[1423]: setting upstream servers from DBus
Mar 20 19:22:06 u-HP-Pavilion-17-Notebook-PC dnsmasq[1423]: using nameserver 192.168.1.1#53
Mar 20 19:22:08 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1224]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::e5b:8fff:fe27:9a64.
Mar 20 19:22:08 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1224]: Joining mDNS multicast group on interface eth1.IPv6 with address 2001:14bb:140:5906:e5b:8fff:fe27:9a64.
Mar 20 19:22:08 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1224]: Registering new address record for 2001:14bb:140:5906:e5b:8fff:fe27:9a64 on eth1.*.
Mar 20 19:22:08 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1224]: Withdrawing address record for fe80::e5b:8fff:fe27:9a64 on eth1.
Mar 20 19:22:08 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1224]: Registering new address record for 2001:14bb:140:5906:f5a2:7e1d:7bfe:475d on eth1.*.
Mar 20 19:22:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Mar 20 19:22:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Policy set 'Kiinteä yhteys 1' (eth1) as default for IPv4 routing and DNS.
Mar 20 19:22:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) successful, device activated.
Mar 20 19:22:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Mar 20 19:22:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
Mar 20 19:22:11 u-HP-Pavilion-17-Notebook-PC dbus[1074]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC dbus[1074]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Beginning DHCPv6 transaction (timeout in 45 seconds)
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> dhclient started with pid 3928
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC dhclient: Copyright 2004-2011 Internet Systems Consortium.
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC dhclient: All rights reserved.
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC dhclient: 
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC dhclient: Bound to *:546
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC dhclient: Listening on Socket/eth1
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   Socket/eth1
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): DHCPv6 state changed nbi -> preinit6
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 1020ms.
Mar 20 19:22:12 u-HP-Pavilion-17-Notebook-PC kernel: [  397.967451] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=UDP SPT=48748 DPT=546 LEN=115 
Mar 20 19:22:13 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 2050ms.
Mar 20 19:22:13 u-HP-Pavilion-17-Notebook-PC kernel: [  398.998255] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=48748 DPT=546 LEN=115 
Mar 20 19:22:15 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 4020ms.
Mar 20 19:22:15 u-HP-Pavilion-17-Notebook-PC kernel: [  401.050218] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=48748 DPT=546 LEN=115 
Mar 20 19:22:19 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 7810ms.
Mar 20 19:22:19 u-HP-Pavilion-17-Notebook-PC kernel: [  405.074069] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=48748 DPT=546 LEN=115 
Mar 20 19:22:20 u-HP-Pavilion-17-Notebook-PC ntpdate[3944]: adjust time server 91.189.89.199 offset 0.298457 sec
Mar 20 19:22:27 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 16330ms.
Mar 20 19:22:27 u-HP-Pavilion-17-Notebook-PC kernel: [  412.891643] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=48748 DPT=546 LEN=115 
Mar 20 19:22:43 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 33900ms.
Mar 20 19:22:44 u-HP-Pavilion-17-Notebook-PC kernel: [  429.247190] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=48748 DPT=546 LEN=115 
Mar 20 19:22:57 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <warn> (eth1): DHCPv6 request timed out.
Mar 20 19:22:57 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> (eth1): canceled DHCP transaction, DHCP client pid 3928
Mar 20 19:22:57 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 20 19:22:57 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 20 19:22:57 u-HP-Pavilion-17-Notebook-PC NetworkManager[1271]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar 20 19:23:58 u-HP-Pavilion-17-Notebook-PC AptDaemon: INFO: Quitting due to inactivity
Mar 20 19:23:58 u-HP-Pavilion-17-Notebook-PC AptDaemon: INFO: Quitting was requested
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00
```


The second time was just two days later. I had just finished watching a video when the computer or the modem disconnected itself. I closed Firefox and tried to open Terminal to see kernel messages but it closed (or I accidentally did it). I tried to open it again and that's when the crash happened.

Here's a part of /var/log/syslog:
```
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC dhclient: receive_packet failed on eth1: Network is down
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1209]: Interface eth1.IPv6 no longer relevant for mDNS.
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1209]: Leaving mDNS multicast group on interface eth1.IPv6 with address 2001:14bb:110:133:3dcc:b1be:269c:c266.
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1209]: Interface eth1.IPv4 no longer relevant for mDNS.
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1209]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC kernel: [  350.162130] cdc_ether 1-1:1.0 eth1: unregister 'cdc_ether' usb-0000:00:12.2-1, CDC Ethernet Device
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1209]: IP_DROP_MEMBERSHIP failed: No such device
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1209]: Withdrawing address record for 2001:14bb:110:133:e5b:8fff:fe27:9a64 on eth1.
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1209]: Withdrawing address record for 2001:14bb:110:133:3dcc:b1be:269c:c266 on eth1.
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1209]: Withdrawing address record for 192.168.1.100 on eth1.
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1209]: Withdrawing workstation service for eth1.
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <warn> (4) failed to find interface name for index
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <warn> (4) failed to find interface name for index
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <info> Policy set 'Kiinteä yhteys 1' (eth1) as default for IPv4 routing and DNS.
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <warn> (eth1): failed to update IPv6 config in response to Router Advertisement.
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <info> (eth1): device state change: activated -> failed (reason 'none') [100 120 0]
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <warn> Activation (eth1) failed.
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1)
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <info> (eth1): now unmanaged
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <info> (eth1): device state change: failed -> unmanaged (reason 'removed') [120 10 36]
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <info> (eth1): deactivating device (reason 'removed') [36]
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC dbus[1076]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC dbus[1076]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC kernel: [  350.299653] usb 1-1: reset high-speed USB device number 3 using ehci-pci
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1273
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <warn> (4) failed to find interface name for index
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: nm_system_iface_flush_routes: assertion `iface != NULL' failed
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <warn> (4) failed to find interface name for index
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <warn> DNS: plugin dnsmasq update failed
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <info> (eth1): removing resolv.conf from /sbin/resolvconf
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC dnsmasq[1408]: setting upstream servers from DBus
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <info> (eth1): cleaning up...
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <warn> (4) failed to find interface name for index
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: (nm-system.c:685):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <error> [1458666122.432900] [nm-system.c:687] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar 22 19:02:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1262]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar 22 19:02:17 u-HP-Pavilion-17-Notebook-PC kernel: [  365.418745] usb 1-1: device descriptor read/64, error -110
Mar 22 19:02:22 u-HP-Pavilion-17-Notebook-PC kernel: [  370.657182] usb 1-1: device descriptor read/64, error -71
Mar 22 19:02:22 u-HP-Pavilion-17-Notebook-PC kernel: [  370.873289] usb 1-1: reset high-speed USB device number 3 using ehci-pci
Mar 22 19:02:22 u-HP-Pavilion-17-Notebook-PC kernel: [  371.013330] usb 1-1: device descriptor read/64, error -71
Mar 22 19:02:23 u-HP-Pavilion-17-Notebook-PC kernel: [  371.257456] usb 1-1: device descriptor read/64, error -71
Mar 22 19:02:23 u-HP-Pavilion-17-Notebook-PC kernel: [  371.473566] usb 1-1: reset high-speed USB device number 3 using ehci-pci
Mar 22 19:02:23 u-HP-Pavilion-17-Notebook-PC kernel: [  371.897741] usb 1-1: device not accepting address 3, error -71
Mar 22 19:02:23 u-HP-Pavilion-17-Notebook-PC kernel: [  372.009820] usb 1-1: reset high-speed USB device number 3 using ehci-pci
Mar 22 19:02:24 u-HP-Pavilion-17-Notebook-PC kernel: [  372.434002] usb 1-1: device not accepting address 3, error -71
Mar 22 19:02:24 u-HP-Pavilion-17-Notebook-PC kernel: [  372.434165] usb 1-1: USB disconnect, device number 3
Mar 22 19:02:24 u-HP-Pavilion-17-Notebook-PC kernel: [  372.434293] sd 5:0:0:0: Device offlined - not ready after error recovery
Mar 22 19:02:24 u-HP-Pavilion-17-Notebook-PC kernel: [  372.546033] usb 1-1: new high-speed USB device number 4 using ehci-pci
Mar 22 19:02:24 u-HP-Pavilion-17-Notebook-PC kernel: [  372.686044] usb 1-1: device descriptor read/64, error -71
Mar 22 19:02:24 u-HP-Pavilion-17-Notebook-PC kernel: [  372.930228] usb 1-1: device descriptor read/64, error -71
Mar 22 19:02:25 u-HP-Pavilion-17-Notebook-PC kernel: [  373.146121] usb 1-1: new high-speed USB device number 5 using ehci-pci
Mar 22 19:02:25 u-HP-Pavilion-17-Notebook-PC kernel: [  373.282402] usb 1-1: device descriptor read/64, error -71
Mar 22 19:02:25 u-HP-Pavilion-17-Notebook-PC kernel: [  373.522491] usb 1-1: device descriptor read/64, error -71
Mar 22 19:02:25 u-HP-Pavilion-17-Notebook-PC kernel: [  373.738600] usb 1-1: new high-speed USB device number 6 using ehci-pci
Mar 22 19:02:26 u-HP-Pavilion-17-Notebook-PC kernel: [  374.162617] usb 1-1: device not accepting address 6, error -71
Mar 22 19:02:26 u-HP-Pavilion-17-Notebook-PC kernel: [  374.274841] usb 1-1: new high-speed USB device number 7 using ehci-pci
Mar 22 19:02:26 u-HP-Pavilion-17-Notebook-PC kernel: [  374.699026] usb 1-1: device not accepting address 7, error -71
Mar 22 19:02:26 u-HP-Pavilion-17-Notebook-PC kernel: [  374.699116] hub 1-0:1.0: unable to enumerate USB device on port 1
Mar 22 19:02:26 u-HP-Pavilion-17-Notebook-PC kernel: [  375.015174] usb 3-1: new full-speed USB device number 2 using ohci-pci
Mar 22 19:02:27 u-HP-Pavilion-17-Notebook-PC kernel: [  375.155053] usb 3-1: device descriptor read/64, error -62
Mar 22 19:02:27 u-HP-Pavilion-17-Notebook-PC kernel: [  375.399346] usb 3-1: device descriptor read/64, error -62
Mar 22 19:02:27 u-HP-Pavilion-17-Notebook-PC kernel: [  375.639164] usb 3-1: new full-speed USB device number 3 using ohci-pci
Mar 22 19:02:27 u-HP-Pavilion-17-Notebook-PC kernel: [  375.779425] usb 3-1: device descriptor read/64, error -62
Mar 22 19:02:27 u-HP-Pavilion-17-Notebook-PC kernel: [  376.023648] usb 3-1: device descriptor read/64, error -62
Mar 22 19:02:28 u-HP-Pavilion-17-Notebook-PC kernel: [  376.267427] usb 3-1: new full-speed USB device number 4 using ohci-pci
Mar 22 19:02:28 u-HP-Pavilion-17-Notebook-PC kernel: [  376.675940] usb 3-1: device not accepting address 4, error -62
Mar 22 19:02:28 u-HP-Pavilion-17-Notebook-PC kernel: [  376.811997] usb 3-1: new full-speed USB device number 5 using ohci-pci
Mar 22 19:02:29 u-HP-Pavilion-17-Notebook-PC kernel: [  377.220191] usb 3-1: device not accepting address 5, error -62
Mar 22 19:02:29 u-HP-Pavilion-17-Notebook-PC kernel: [  377.220292] hub 3-0:1.0: unable to enumerate USB device on port 1
Mar 22 19:02:33 u-HP-Pavilion-17-Notebook-PC kernel: [  381.499333] BUG: unable to handle kernel paging request at 0000000000001fc7
Mar 22 19:02:33 u-HP-Pavilion-17-Notebook-PC kernel: [  381.499432] IP: [<ffffffff811afe1c>] kmem_cache_alloc_trace+0x7c/0x1f0
Mar 22 19:02:33 u-HP-Pavilion-17-Notebook-PC kernel: [  381.499483] PGD 2007f4067 PUD 1dd403067 PMD 0 
Mar 22 19:02:33 u-HP-Pavilion-17-Notebook-PC kernel: [  381.499517] Oops: 0000 [#1] SMP 
Mar 22 19:02:33 u-HP-Pavilion-17-Notebook-PC kernel: [  381.499541] Modules linked in: bnep rfcomm bluetooth parport_pc ppdev cdc_ether usbnet xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_state ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables arc4 rt2800pci rt2800mmio rt2800lib uvcvideo crc_ccitt videobuf2_core videodev radeon usb_storage rt2x00mmio videobuf2_vmalloc rt2x00pci videobuf2_memops snd_hda_codec_realtek snd_hda_codec_hdmi snd_hda_intel snd_hda_codec rt2x00lib binfmt_misc snd_hwdep mac80211 kvm snd_pcm ttm crct10dif_pclmul crc32_pclmul snd_seq_midi snd_rawmidi snd_seq_midi_event joydev cfg80211 drm_kms_helper snd_seq aesni_intel ablk_helper snd_timer cryptd snd_seq_device eeprom_93cx6 lrw rtsx_pci_ms gf128mul memstick hp_accel psmouse 
```

The keyboard and the mouse didn't work, so I held the power button down again until the computer shut down. I turned it back on, but the modem light just blinked (the device never moved on to the state where the light was on all the time). I couldn't connect to the internet.

Here's a related part of /var/log/syslog, mostly bizarre error messages. Unlike other log excerpts in this post, this one doesn't cover the computer crash/shutdown messages:
```
Mar 22 19:06:19 u-HP-Pavilion-17-Notebook-PC kernel: [   43.337493] usb 3-1: new full-speed USB device number 7 using ohci-pci
Mar 22 19:06:19 u-HP-Pavilion-17-Notebook-PC kernel: [   43.477420] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:19 u-HP-Pavilion-17-Notebook-PC kernel: [   43.721850] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC kernel: [   43.962095] usb 3-1: new full-speed USB device number 8 using ohci-pci
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[1987]: Successfully made thread 2002 of process 1985 (n/a) owned by '104' RT at priority 5.
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[1987]: Supervising 2 threads of 1 processes of 1 users.
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC kernel: [   44.370288] usb 3-1: device not accepting address 8, error -62
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[1987]: Successfully made thread 2005 of process 1985 (n/a) owned by '104' RT at priority 5.
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[1987]: Supervising 3 threads of 1 processes of 1 users.
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[1987]: Successfully made thread 2007 of process 1985 (n/a) owned by '104' RT at priority 5.
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[1987]: Supervising 4 threads of 1 processes of 1 users.
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC kernel: [   44.506485] usb 3-1: new full-speed USB device number 9 using ohci-pci
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[1987]: Successfully made thread 2010 of process 2010 (n/a) owned by '104' high priority at nice level -11.
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[1987]: Supervising 5 threads of 2 processes of 1 users.
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC pulseaudio[2010]: [pulseaudio] pid.c: Daemon already running.
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC kernel: [   44.915001] usb 3-1: device not accepting address 9, error -62
Mar 22 19:06:20 u-HP-Pavilion-17-Notebook-PC kernel: [   44.915070] hub 3-0:1.0: unable to enumerate USB device on port 1
Mar 22 19:06:21 u-HP-Pavilion-17-Notebook-PC kernel: [   45.131213] usb 3-1: new full-speed USB device number 10 using ohci-pci
Mar 22 19:06:21 u-HP-Pavilion-17-Notebook-PC kernel: [   45.271319] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:21 u-HP-Pavilion-17-Notebook-PC kernel: [   45.515557] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:21 u-HP-Pavilion-17-Notebook-PC kernel: [   45.755782] usb 3-1: new full-speed USB device number 11 using ohci-pci
Mar 22 19:06:21 u-HP-Pavilion-17-Notebook-PC kernel: [   45.895766] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:22 u-HP-Pavilion-17-Notebook-PC kernel: [   46.140045] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:22 u-HP-Pavilion-17-Notebook-PC kernel: [   46.380373] usb 3-1: new full-speed USB device number 12 using ohci-pci
Mar 22 19:06:22 u-HP-Pavilion-17-Notebook-PC kernel: [   46.788779] usb 3-1: device not accepting address 12, error -62
Mar 22 19:06:22 u-HP-Pavilion-17-Notebook-PC kernel: [   46.924906] usb 3-1: new full-speed USB device number 13 using ohci-pci
Mar 22 19:06:23 u-HP-Pavilion-17-Notebook-PC kernel: [   47.333300] usb 3-1: device not accepting address 13, error -62
Mar 22 19:06:23 u-HP-Pavilion-17-Notebook-PC kernel: [   47.333354] hub 3-0:1.0: unable to enumerate USB device on port 1
Mar 22 19:06:23 u-HP-Pavilion-17-Notebook-PC kernel: [   47.833784] usb 3-1: new full-speed USB device number 14 using ohci-pci
Mar 22 19:06:24 u-HP-Pavilion-17-Notebook-PC kernel: [   47.973912] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:24 u-HP-Pavilion-17-Notebook-PC kernel: [   48.218153] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:24 u-HP-Pavilion-17-Notebook-PC kernel: [   48.458372] usb 3-1: new full-speed USB device number 15 using ohci-pci
Mar 22 19:06:24 u-HP-Pavilion-17-Notebook-PC kernel: [   48.598504] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:24 u-HP-Pavilion-17-Notebook-PC kernel: [   48.842734] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:25 u-HP-Pavilion-17-Notebook-PC kernel: [   49.082814] usb 3-1: new full-speed USB device number 16 using ohci-pci
Mar 22 19:06:25 u-HP-Pavilion-17-Notebook-PC kernel: [   49.491376] usb 3-1: device not accepting address 16, error -62
Mar 22 19:06:25 u-HP-Pavilion-17-Notebook-PC kernel: [   49.627535] usb 3-1: new full-speed USB device number 17 using ohci-pci
Mar 22 19:06:26 u-HP-Pavilion-17-Notebook-PC kernel: [   50.035956] usb 3-1: device not accepting address 17, error -62
Mar 22 19:06:26 u-HP-Pavilion-17-Notebook-PC kernel: [   50.035996] hub 3-0:1.0: unable to enumerate USB device on port 1
Mar 22 19:06:26 u-HP-Pavilion-17-Notebook-PC kernel: [   50.248106] usb 3-1: new full-speed USB device number 18 using ohci-pci
Mar 22 19:06:26 u-HP-Pavilion-17-Notebook-PC kernel: [   50.388218] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:26 u-HP-Pavilion-17-Notebook-PC kernel: [   50.632354] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:26 u-HP-Pavilion-17-Notebook-PC kernel: [   50.876726] usb 3-1: new full-speed USB device number 19 using ohci-pci
Mar 22 19:06:27 u-HP-Pavilion-17-Notebook-PC kernel: [   51.016885] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:27 u-HP-Pavilion-17-Notebook-PC kernel: [   51.261063] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:27 u-HP-Pavilion-17-Notebook-PC kernel: [   51.501328] usb 3-1: new full-speed USB device number 20 using ohci-pci
Mar 22 19:06:27 u-HP-Pavilion-17-Notebook-PC kernel: [   51.909540] usb 3-1: device not accepting address 20, error -62
Mar 22 19:06:28 u-HP-Pavilion-17-Notebook-PC kernel: [   52.045853] usb 3-1: new full-speed USB device number 21 using ohci-pci
Mar 22 19:06:28 u-HP-Pavilion-17-Notebook-PC kernel: [   52.454177] usb 3-1: device not accepting address 21, error -62
Mar 22 19:06:28 u-HP-Pavilion-17-Notebook-PC kernel: [   52.454216] hub 3-0:1.0: unable to enumerate USB device on port 1
Mar 22 19:06:29 u-HP-Pavilion-17-Notebook-PC kernel: [   52.962698] usb 3-1: new full-speed USB device number 22 using ohci-pci
Mar 22 19:06:29 u-HP-Pavilion-17-Notebook-PC kernel: [   53.102829] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:29 u-HP-Pavilion-17-Notebook-PC kernel: [   53.347124] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:29 u-HP-Pavilion-17-Notebook-PC kernel: [   53.587334] usb 3-1: new full-speed USB device number 23 using ohci-pci
Mar 22 19:06:29 u-HP-Pavilion-17-Notebook-PC kernel: [   53.727471] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:30 u-HP-Pavilion-17-Notebook-PC kernel: [   53.971701] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:30 u-HP-Pavilion-17-Notebook-PC kernel: [   54.211934] usb 3-1: new full-speed USB device number 24 using ohci-pci
Mar 22 19:06:30 u-HP-Pavilion-17-Notebook-PC kernel: [   54.620320] usb 3-1: device not accepting address 24, error -62
Mar 22 19:06:30 u-HP-Pavilion-17-Notebook-PC kernel: [   54.756332] usb 3-1: new full-speed USB device number 25 using ohci-pci
Mar 22 19:06:31 u-HP-Pavilion-17-Notebook-PC kernel: [   55.164842] usb 3-1: device not accepting address 25, error -62
Mar 22 19:06:31 u-HP-Pavilion-17-Notebook-PC kernel: [   55.164991] hub 3-0:1.0: unable to enumerate USB device on port 1
Mar 22 19:06:31 u-HP-Pavilion-17-Notebook-PC kernel: [   55.376926] usb 3-1: new full-speed USB device number 26 using ohci-pci
Mar 22 19:06:31 u-HP-Pavilion-17-Notebook-PC kernel: [   55.517020] usb 3-1: device descriptor read/64, error -62
Mar 22 19:06:31 u-HP-Pavilion-17-Notebook-PC kernel: [   55.761213] usb 3-1: device descriptor read/64, error -62
```

I turned off the computer and unplugged the modem and waited. Then I replugged the modem and turned the computer on. Everything worked and nothing crashed.


The third crash occurred a few days after the second one. This time, I was only reading some forums when the disconnection happened. I knew the system would crash again soon after seeing the notification. This time, I unplugged the modem to see what would happen. As I was about to clear browsing history and close Firefox, the computer froze.

Here's the /var/log/syslog part about that:
```
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.113975] ------------[ cut here ]------------
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.113993] WARNING: CPU: 3 PID: 0 at /build/linux-lts-trusty-4xknjl/linux-lts-trusty-3.13.0/net/sched/sch_generic.c:264 dev_watchdog+0x267/0x270()
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.113998] NETDEV WATCHDOG: eth1 (cdc_ether): transmit queue 0 timed out
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114001] Modules linked in: bnep rfcomm bluetooth parport_pc ppdev xt_hl ip6t_rt cdc_ether usbnet nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_state ip6table_filter ip6_tables nf_conntrack_netbios_ns arc4 rt2800pci rt2800mmio nf_conntrack_broadcast rt2800lib crc_ccitt nf_nat_ftp nf_nat rt2x00mmio nf_conntrack_ftp rt2x00pci kvm usb_storage nf_conntrack uvcvideo radeon rt2x00lib crct10dif_pclmul crc32_pclmul iptable_filter videobuf2_core snd_hda_codec_realtek snd_hda_codec_hdmi snd_hda_intel videodev snd_hda_codec videobuf2_vmalloc ip_tables videobuf2_memops snd_hwdep mac80211 aesni_intel snd_pcm x_tables snd_seq_midi snd_rawmidi ablk_helper snd_seq_midi_event ttm snd_seq cryptd lrw snd_timer gf128mul snd_seq_device joydev cfg80211 drm_kms_helper drm psmouse snd glue_helper aes_x86_64 hp_accel lis3lv02d rtsx_pci_ms eeprom_93cx6 memstick i2c_piix4 i2c_algo_bit soundcore k10temp hp_wmi sparse_keymap mac_hid 
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: snd_page_alloc serio_raw video input_polldev shpchp wmi hp_wireless binfmt_misc lp parport nls_iso8859_1 hid_generic usbhid hid rtsx_pci_sdmmc rtsx_pci r8169 mii ahci libahci
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114138] CPU: 3 PID: 0 Comm: swapper/3 Not tainted 3.13.0-83-generic #127~precise1-Ubuntu
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114142] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114146]  0000000000000108 ffff88021ed83d28 ffffffff8175ce7d 0000000000000007
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114154]  ffff88021ed83d78 ffff88021ed83d68 ffffffff8106b14c ffff88021ed83dc8
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114160]  ffff8800ad1c4000 ffff8800ad1c4360 ffff8802134c2800 0000000000000001
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114167] Call Trace:
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114171]  <IRQ>  [<ffffffff8175ce7d>] dump_stack+0x46/0x58
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114187]  [<ffffffff8106b14c>] warn_slowpath_common+0x8c/0xc0
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114194]  [<ffffffff8106b236>] warn_slowpath_fmt+0x46/0x50
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114202]  [<ffffffff816752c7>] dev_watchdog+0x267/0x270
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114208]  [<ffffffff81675060>] ? pfifo_fast_dequeue+0xe0/0xe0
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114214]  [<ffffffff810787b5>] call_timer_fn+0x45/0x160
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114220]  [<ffffffff81079b70>] run_timer_softirq+0x280/0x300
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114227]  [<ffffffff81045a3d>] ? lapic_next_event+0x1d/0x30
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114233]  [<ffffffff81675060>] ? pfifo_fast_dequeue+0xe0/0xe0
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114240]  [<ffffffff8107042d>] __do_softirq+0xdd/0x300
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114246]  [<ffffffff810709ee>] irq_exit+0x11e/0x140
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114254]  [<ffffffff81774a3a>] smp_apic_timer_interrupt+0x4a/0x60
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114260]  [<ffffffff8177339d>] apic_timer_interrupt+0x6d/0x80
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114262]  <EOI>  [<ffffffff8101d513>] ? native_sched_clock+0x13/0x80
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114276]  [<ffffffff816007ee>] ? cpuidle_enter_state+0x5e/0xe0
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114282]  [<ffffffff816007e7>] ? cpuidle_enter_state+0x57/0xe0
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114288]  [<ffffffff81600930>] cpuidle_idle_call+0xc0/0x210
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114295]  [<ffffffff8101ea8e>] arch_cpu_idle+0xe/0x30
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114301]  [<ffffffff810c4438>] cpu_idle_loop+0x78/0x270
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114307]  [<ffffffff810c469b>] cpu_startup_entry+0x6b/0x70
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114312]  [<ffffffff810448ad>] start_secondary+0xcd/0xd0
Mar 26 19:31:40 u-HP-Pavilion-17-Notebook-PC kernel: [  227.114317] ---[ end trace 3126ec640daa4598 ]---
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00
```


At this point, I figured out that the random disconnections and crashes would occur if I opened Firefox (or any other program that uses the internet) too soon after logging in (before the first crash, though, I could open it as soon as I liked and there would be no problems), so I took the habit of waiting a couple of minutes before opening the browser, so that AptDaemon would do its job without me distracting it. This worked most of the time. Once it didn't, so I just turned off the computer (from the menu) right after the connection got broken, waited for 15-45 seconds and turned it back on.

Here's the related /var/log/syslog part about that one time:```

Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC kernel: [  288.107138] cdc_ether 1-1:1.0 eth1: unregister 'cdc_ether' usb-0000:00:12.2-1, CDC Ethernet Device
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC dhclient: receive_packet failed on eth1: Network is down
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1314]: Interface eth1.IPv6 no longer relevant for mDNS.
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1314]: Leaving mDNS multicast group on interface eth1.IPv6 with address 2001:14bb:110:185:e5b:8fff:fe27:9a64.
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1314]: Interface eth1.IPv4 no longer relevant for mDNS.
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1314]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1314]: IP_DROP_MEMBERSHIP failed: No such device
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1314]: Withdrawing address record for 2001:14bb:110:185:b889:601f:676c:3e67 on eth1.
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1314]: Withdrawing address record for 2001:14bb:110:185:e5b:8fff:fe27:9a64 on eth1.
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1314]: Withdrawing address record for 192.168.1.100 on eth1.
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1314]: Withdrawing workstation service for eth1.
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <warn> (4) failed to find interface name for index
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <warn> (4) failed to find interface name for index
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <info> Policy set 'Kiinteä yhteys 1' (eth1) as default for IPv4 routing and DNS.
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <warn> (eth1): failed to update IPv6 config in response to Router Advertisement.
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <info> (eth1): device state change: activated -> failed (reason 'none') [100 120 0]
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <warn> Activation (eth1) failed.
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1)
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <info> (eth1): now unmanaged
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <info> (eth1): device state change: failed -> unmanaged (reason 'removed') [120 10 36]
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <info> (eth1): deactivating device (reason 'removed') [36]
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC dbus[1179]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC dbus[1179]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC kernel: [  288.245304] usb 1-1: reset high-speed USB device number 3 using ehci-pci
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1487
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <warn> (4) failed to find interface name for index
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: nm_system_iface_flush_routes: assertion `iface != NULL' failed
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <warn> (4) failed to find interface name for index
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <warn> DNS: plugin dnsmasq update failed
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <info> (eth1): removing resolv.conf from /sbin/resolvconf
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC dnsmasq[1610]: setting upstream servers from DBus
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <info> (eth1): cleaning up...
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <warn> (4) failed to find interface name for index
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: (nm-system.c:685):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <error> [1459364586.411036] [nm-system.c:687] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar 30 22:03:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1394]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Mar 30 22:03:13 u-HP-Pavilion-17-Notebook-PC kernel: Kernel logging (proc) stopped.
Mar 30 22:03:13 u-HP-Pavilion-17-Notebook-PC rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1036" x-info="http://www.rsyslog.com"] exiting on signal 15.
```


As I wrote above, the method (where I waited) worked – until today, that is. When I had logged in and waited, I opened Firefox – and the connection was broken almost instantly. I turned off the computer before it would crash. I turned it on again and it worked fine then. Later, however, when I started the computer, logged in and waited, it (or the modem) disconnected itself again – and I hadn't even started using the internet. I believe this disconnection was caused by the popup window (or the application/service handling it) that offered a new version of Ubuntu. This was the second disconnection during the same day, which had never happened before! Now, I tried to solve the problem by quickly unplugging and replugging the modem. For a moment, it seemed the connection was formed again, but eventually, it wasn't, so I tried to shut the computer down (from the menu). Then, the screen froze for a second, and was then replaced with kernel messages (I used the Gnome Classic in this session instead of Unity). I had no choice but shut down by holding the power button. I updated the kernel to version 3.13.0-85 about two weeks before that, and as of now, I'm still using it.

Here's the /var/log/syslog part from when I managed to avoid the crash by turning off the computer:
```
Supervising 5 threads of 2 processes of 2 users.
Apr 21 11:33:06 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2154]: Successfully made thread 2314 of process 2313 (n/a) owned by '1001' RT at priority 5.
Apr 21 11:33:06 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2154]: Supervising 6 threads of 2 processes of 2 users.
Apr 21 11:33:06 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2154]: Successfully made thread 2317 of process 2313 (n/a) owned by '1001' RT at priority 5.
Apr 21 11:33:06 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2154]: Supervising 7 threads of 2 processes of 2 users.
Apr 21 11:33:06 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2154]: Successfully made thread 2318 of process 2313 (n/a) owned by '1001' RT at priority 5.
Apr 21 11:33:06 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2154]: Supervising 8 threads of 2 processes of 2 users.
Apr 21 11:33:06 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 34470ms.
Apr 21 11:33:06 u-HP-Pavilion-17-Notebook-PC kernel: [   65.631462] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=50963 DPT=546 LEN=115 
Apr 21 11:33:07 u-HP-Pavilion-17-Notebook-PC dbus[1137]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Apr 21 11:33:07 u-HP-Pavilion-17-Notebook-PC dbus[1137]: [system] Successfully activated service 'org.freedesktop.UDisks'
Apr 21 11:33:17 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <warn> (eth1): DHCPv6 request timed out.
Apr 21 11:33:17 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1691
Apr 21 11:33:17 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 21 11:33:17 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 21 11:33:17 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 21 11:33:23 u-HP-Pavilion-17-Notebook-PC goa[2496]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Apr 21 11:34:19 u-HP-Pavilion-17-Notebook-PC dbus[1137]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Apr 21 11:34:23 u-HP-Pavilion-17-Notebook-PC AptDaemon: INFO: Initializing daemon
Apr 21 11:34:24 u-HP-Pavilion-17-Notebook-PC AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Apr 21 11:34:24 u-HP-Pavilion-17-Notebook-PC dbus[1137]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Apr 21 11:34:24 u-HP-Pavilion-17-Notebook-PC AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Apr 21 11:34:24 u-HP-Pavilion-17-Notebook-PC AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/13d1717b658e42e7b275bdf184e727e9
Apr 21 11:34:24 u-HP-Pavilion-17-Notebook-PC AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/13d1717b658e42e7b275bdf184e727e9
Apr 21 11:34:29 u-HP-Pavilion-17-Notebook-PC AptDaemon.PackageKit: INFO: Get updates()
Apr 21 11:34:31 u-HP-Pavilion-17-Notebook-PC AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/13d1717b658e42e7b275bdf184e727e9
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1236]: Interface eth1.IPv6 no longer relevant for mDNS.
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1236]: Leaving mDNS multicast group on interface eth1.IPv6 with address 2001:14bb:110:1a40:dd50:1761:eb3a:ee48.
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1236]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1236]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC dhclient: receive_packet failed on eth1: Network is down
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC kernel: [  273.075383] cdc_ether 1-1:1.0 eth1: unregister 'cdc_ether' usb-0000:00:12.2-1, CDC Ethernet Device
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1236]: IP_DROP_MEMBERSHIP failed: No such device
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1236]: Withdrawing address record for 2001:14bb:110:1a40:e5b:8fff:fe27:9a64 on eth1.
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1236]: Withdrawing address record for 2001:14bb:110:1a40:dd50:1761:eb3a:ee48 on eth1.
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1236]: Withdrawing address record for 192.168.1.100 on eth1.
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1236]: Withdrawing workstation service for eth1.
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <warn> (4) failed to find interface name for index
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <warn> (4) failed to find interface name for index
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> Policy set 'Kiinteä yhteys 1' (eth1) as default for IPv4 routing and DNS.
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <warn> (eth1): failed to update IPv6 config in response to Router Advertisement.
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> (eth1): device state change: activated -> failed (reason 'none') [100 120 0]
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <warn> Activation (eth1) failed.
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC dbus[1137]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1)
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> (eth1): now unmanaged
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> (eth1): device state change: failed -> unmanaged (reason 'removed') [120 10 36]
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> (eth1): deactivating device (reason 'removed') [36]
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC dbus[1137]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC kernel: [  273.208626] usb 1-1: reset high-speed USB device number 3 using ehci-pci
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1344
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <warn> (4) failed to find interface name for index
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: nm_system_iface_flush_routes: assertion `iface != NULL' failed
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <warn> (4) failed to find interface name for index
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <warn> DNS: plugin dnsmasq update failed
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> (eth1): removing resolv.conf from /sbin/resolvconf
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC dnsmasq[1445]: setting upstream servers from DBus
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> (eth1): cleaning up...
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <warn> (4) failed to find interface name for index
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: (nm-system.c:685):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <error> [1461227794.407458] [nm-system.c:687] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Apr 21 11:36:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1302]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Apr 21 11:36:44 u-HP-Pavilion-17-Notebook-PC kernel: Kernel logging (proc) stopped.
Apr 21 11:36:44 u-HP-Pavilion-17-Notebook-PC rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1024" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

And here's /var/log/syslog snippet from the actual crash that happened later. It ends abruptly and the next line (not seen here) is from the next time I turned on the computer:
```
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1223]: Interface eth1.IPv6 no longer relevant for mDNS.
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1223]: Leaving mDNS multicast group on interface eth1.IPv6 with address 2001:14bb:150:1bbb:1520:6bad:1349:3c30.
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1223]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1223]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC dhclient: receive_packet failed on eth1: Network is down
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC kernel: [  170.007311] cdc_ether 1-1:1.0 eth1: unregister 'cdc_ether' usb-0000:00:12.2-1, CDC Ethernet Device
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1223]: IP_DROP_MEMBERSHIP failed: No such device
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1223]: Withdrawing address record for 2001:14bb:150:1bbb:e5b:8fff:fe27:9a64 on eth1.
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1223]: Withdrawing address record for 2001:14bb:150:1bbb:1520:6bad:1349:3c30 on eth1.
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1223]: Withdrawing address record for 192.168.1.100 on eth1.
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1223]: Withdrawing workstation service for eth1.
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <warn> (4) failed to find interface name for index
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <warn> (4) failed to find interface name for index
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Policy set 'Kiinteä yhteys 1' (eth1) as default for IPv4 routing and DNS.
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <warn> (eth1): failed to update IPv6 config in response to Router Advertisement.
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): device state change: activated -> failed (reason 'none') [100 120 0]
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <warn> Activation (eth1) failed.
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1)
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC dbus[1078]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): now unmanaged
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): device state change: failed -> unmanaged (reason 'removed') [120 10 36]
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): deactivating device (reason 'removed') [36]
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC dbus[1078]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC kernel: [  170.140781] usb 1-1: reset high-speed USB device number 3 using ehci-pci
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1440
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <warn> (4) failed to find interface name for index
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: nm_system_iface_flush_routes: assertion `iface != NULL' failed
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <warn> (4) failed to find interface name for index
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <warn> DNS: plugin dnsmasq update failed
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): removing resolv.conf from /sbin/resolvconf
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC dnsmasq[1551]: setting upstream servers from DBus
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): cleaning up...
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <warn> (4) failed to find interface name for index
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: (nm-system.c:685):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <error> [1461228973.372982] [nm-system.c:687] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Apr 21 11:56:13 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Apr 21 11:56:19 u-HP-Pavilion-17-Notebook-PC kernel: [  176.151989] usb 1-1: USB disconnect, device number 3
Apr 21 11:56:19 u-HP-Pavilion-17-Notebook-PC kernel: [  176.152079] sd 5:0:0:0: Device offlined - not ready after error recovery
Apr 21 11:56:33 u-HP-Pavilion-17-Notebook-PC kernel: [  190.354172] usb 1-1: new high-speed USB device number 4 using ehci-pci
Apr 21 11:56:33 u-HP-Pavilion-17-Notebook-PC kernel: [  190.487716] usb 1-1: New USB device found, idVendor=12d1, idProduct=1f01
Apr 21 11:56:33 u-HP-Pavilion-17-Notebook-PC kernel: [  190.487725] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Apr 21 11:56:33 u-HP-Pavilion-17-Notebook-PC kernel: [  190.487731] usb 1-1: Product: HUAWEI_MOBILE
Apr 21 11:56:33 u-HP-Pavilion-17-Notebook-PC kernel: [  190.487735] usb 1-1: Manufacturer: HUAWEI_MOBILE
Apr 21 11:56:33 u-HP-Pavilion-17-Notebook-PC kernel: [  190.487739] usb 1-1: SerialNumber: 0123456789ABCDEF
Apr 21 11:56:33 u-HP-Pavilion-17-Notebook-PC kernel: [  190.527731] usb-storage 1-1:1.0: USB Mass Storage device detected
Apr 21 11:56:33 u-HP-Pavilion-17-Notebook-PC kernel: [  190.527901] scsi6 : usb-storage 1-1:1.0
Apr 21 11:56:33 u-HP-Pavilion-17-Notebook-PC mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1"
Apr 21 11:56:33 u-HP-Pavilion-17-Notebook-PC mtp-probe: bus: 1, device: 4 was not an MTP device
Apr 21 11:56:34 u-HP-Pavilion-17-Notebook-PC kernel: [  191.533718] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Apr 21 11:56:34 u-HP-Pavilion-17-Notebook-PC kernel: [  191.534323] scsi 6:0:0:1: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
Apr 21 11:56:34 u-HP-Pavilion-17-Notebook-PC kernel: [  191.537730] sr1: scsi-1 drive
Apr 21 11:56:34 u-HP-Pavilion-17-Notebook-PC kernel: [  191.538018] sr 6:0:0:0: Attached scsi CD-ROM sr1
Apr 21 11:56:34 u-HP-Pavilion-17-Notebook-PC kernel: [  191.538182] sr 6:0:0:0: Attached scsi generic sg2 type 5
Apr 21 11:56:34 u-HP-Pavilion-17-Notebook-PC kernel: [  191.538614] sd 6:0:0:1: Attached scsi generic sg3 type 0
Apr 21 11:56:34 u-HP-Pavilion-17-Notebook-PC kernel: [  191.541499] sd 6:0:0:1: [sdb] Attached SCSI removable disk
Apr 21 11:56:34 u-HP-Pavilion-17-Notebook-PC usb_modeswitch: switching device 12d1:1f01 on 001/004
Apr 21 11:56:34 u-HP-Pavilion-17-Notebook-PC kernel: [  191.945237] usb 1-1: USB disconnect, device number 4
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC kernel: [  192.551181] usb 1-1: new high-speed USB device number 5 using ehci-pci
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC kernel: [  192.684576] usb 1-1: New USB device found, idVendor=12d1, idProduct=14dc
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC kernel: [  192.684586] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC kernel: [  192.684591] usb 1-1: Product: HUAWEI_MOBILE
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC kernel: [  192.684596] usb 1-1: Manufacturer: HUAWEI_MOBILE
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC kernel: [  192.843437] cdc_ether 1-1:1.0 eth1: register 'cdc_ether' at usb-0000:00:12.2-1, CDC Ethernet Device, 0c:5b:8f:27:9a:64
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC kernel: [  192.845892] usb-storage 1-1:1.2: USB Mass Storage device detected
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC kernel: [  192.846056] scsi7 : usb-storage 1-1:1.2
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1"
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC mtp-probe: bus: 1, device: 5 was not an MTP device
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1)
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1): no ifupdown configuration found.
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <warn> failed to allocate link cache: (-12) Object not found
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): carrier is OFF
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): new Ethernet device (driver: 'cdc_ether' ifindex: 5)
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/3
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): now managed
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): bringing up device.
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): carrier now ON (device state 20)
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): preparing device.
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): deactivating device (reason 'managed') [2]
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Added default wired connection 'Kiinteä yhteys 1' for /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Auto-activating connection 'Kiinteä yhteys 1'.
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) starting connection 'Kiinteä yhteys 1'
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> dhclient started with pid 2630
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) Beginning IP6 addrconf.
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC dhclient: Copyright 2004-2011 Internet Systems Consortium.
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC dhclient: All rights reserved.
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC dhclient: 
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC kernel: [  192.890257] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC kernel: [  192.890461] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1333]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC dhclient: Listening on LPF/eth1/0c:5b:8f:27:9a:64
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   LPF/eth1/0c:5b:8f:27:9a:64
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   Socket/fallback
Apr 21 11:56:35 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 21 11:56:36 u-HP-Pavilion-17-Notebook-PC kernel: [  193.849452] scsi 7:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
Apr 21 11:56:36 u-HP-Pavilion-17-Notebook-PC kernel: [  193.850086] sd 7:0:0:0: Attached scsi generic sg2 type 0
Apr 21 11:56:36 u-HP-Pavilion-17-Notebook-PC kernel: [  193.852683] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902139] ------------[ cut here ]------------
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902154] WARNING: CPU: 2 PID: 2642 at /build/linux-lts-trusty-q6GBfl/linux-lts-trusty-3.13.0/include/linux/kref.h:47 aa_get_label.part.4+0x1e/0x27()
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902158] Modules linked in: bnep rfcomm bluetooth parport_pc ppdev snd_hda_codec_realtek snd_hda_codec_hdmi xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT xt_LOG xt_limit xt_tcpudp xt_addrtype cdc_ether usbnet nf_conntrack_ipv4 nf_defrag_ipv4 xt_state ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp kvm nf_conntrack uvcvideo iptable_filter ip_tables arc4 x_tables rt2800pci crct10dif_pclmul videobuf2_core rt2800mmio snd_hda_intel snd_hda_codec radeon usb_storage videodev rt2800lib crc32_pclmul crc_ccitt rt2x00mmio snd_hwdep rt2x00pci videobuf2_vmalloc snd_pcm rt2x00lib aesni_intel videobuf2_memops ablk_helper snd_seq_midi cryptd snd_rawmidi snd_seq_midi_event snd_seq mac80211 lrw snd_seq_device gf128mul snd_timer ttm glue_helper aes_x86_64 binfmt_misc drm_kms_helper joydev cfg80211 drm psmouse snd hp_wmi rtsx_pci_ms soundcore memstick eeprom_93cx6 snd_page_alloc hp_accel shpchp sparse_keymap wmi hp_wireless
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: mac_hid lis3lv02d i2c_algo_bit serio_raw video i2c_piix4 input_polldev k10temp lp parport nls_iso8859_1 hid_generic usbhid hid rtsx_pci_sdmmc rtsx_pci r8169 mii ahci libahci
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902290] CPU: 2 PID: 2642 Comm: udisks-part-id Not tainted 3.13.0-85-generic #129~precise1-Ubuntu
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902295] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902299]  0000000000000000 ffff88021199dc78 ffffffff81761a0e 0000000000000000
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902307]  000000000000002f ffff88021199dcb8 ffffffff8106c23c ffffffff8132e2ea
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902313]  ffff880216c0c430 ffff88021360ff00 ffff880216c0c430 ffff88021199df24
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902320] Call Trace:
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902329]  [<ffffffff81761a0e>] dump_stack+0x64/0x82
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902338]  [<ffffffff8106c23c>] warn_slowpath_common+0x8c/0xc0
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902345]  [<ffffffff8132e2ea>] ? apparmor_file_alloc_security+0x5a/0x150
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902352]  [<ffffffff8106c28a>] warn_slowpath_null+0x1a/0x20
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902357]  [<ffffffff81760c4d>] aa_get_label.part.4+0x1e/0x27
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902363]  [<ffffffff8132e3d2>] apparmor_file_alloc_security+0x142/0x150
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902370]  [<ffffffff812eeea6>] security_file_alloc+0x16/0x20
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902377]  [<ffffffff811cf850>] get_empty_filp+0x90/0x1a0
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902383]  [<ffffffff811dd498>] path_openat+0x48/0x4c0
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902388]  [<ffffffff811dd990>] ? getname_flags.part.25+0x30/0x140
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902395]  [<ffffffff811de7a3>] do_filp_open+0x43/0xa0
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902401]  [<ffffffff811eb8de>] ? __alloc_fd+0xce/0x120
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902409]  [<ffffffff811ccde6>] do_sys_open+0x136/0x2c0
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902416]  [<ffffffff81096a5d>] ? __put_cred+0x3d/0x50
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902422]  [<ffffffff811cc3a8>] ? SyS_faccessat+0x1d8/0x220
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902429]  [<ffffffff811ccf8e>] SyS_open+0x1e/0x20
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902436]  [<ffffffff8177721d>] system_call_fastpath+0x1a/0x1f
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.902440] ---[ end trace 986071c59d1bf884 ]---
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.903328] ------------[ cut here ]------------
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.903371] kernel BUG at /build/linux-lts-trusty-q6GBfl/linux-lts-trusty-3.13.0/security/apparmor/context.c:98!
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.903438] invalid opcode: 0000 [#1] SMP 
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.903687] ------------[ cut here ]------------
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.903701] WARNING: CPU: 1 PID: 2318 at /build/linux-lts-trusty-q6GBfl/linux-lts-trusty-3.13.0/security/apparmor/file.c:552 aa_file_perm+0x16a/0x180()
Apr 21 11:56:37 u-HP-Pavilion-17-Notebook-PC kernel: [  193.903471] Modules linked in: bnep rfcomm bluetooth parport_pc ppdev snd_hda_codec_realtek snd_hda_codec_hdmi xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT xt_LOG xt_limit xt_tcpudp xt_addrtype cdc_ether usbnet nf_conntrack_ipv4 nf_defrag_ipv4 xt_state ip6table_filter
Apr 21 11:56:42 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 21 11:56:42 u-HP-Pavilion-17-Notebook-PC udevd[421]: worker [2569] terminated by signal 9 (Killed)
Apr 21 11:56:42 u-HP-Pavilion-17-Notebook-PC udevd[421]: worker [2569] failed while handling '/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.2/host7/target7:0:0/7:0:0:0/block/sdb'
Apr 21 11:56:44 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 21 11:56:44 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2125]: The canary thread is apparently starving. Taking action.
Apr 21 11:56:44 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2125]: Demoting known real-time threads.
Apr 21 11:56:44 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2125]: Successfully demoted thread 2300 of process 2296 (n/a).
Apr 21 11:56:44 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2125]: Successfully demoted thread 2299 of process 2296 (n/a).
Apr 21 11:56:44 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2125]: Successfully demoted thread 2297 of process 2296 (n/a).
Apr 21 11:56:44 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2125]: Successfully demoted thread 2296 of process 2296 (n/a).
Apr 21 11:56:44 u-HP-Pavilion-17-Notebook-PC rtkit-daemon[2125]: Demoted 4 threads.
Apr 21 11:56:45 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPREQUEST of 192.168.1.100 on eth1 to 255.255.255.255 port 67
Apr 21 11:56:45 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPOFFER of 192.168.1.100 from 192.168.1.1
Apr 21 11:56:45 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Apr 21 11:56:45 u-HP-Pavilion-17-Notebook-PC dhclient: bound to 192.168.1.100 -- renewal in 34667 seconds.
Apr 21 11:56:46 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1223]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::e5b:8fff:fe27:9a64.
Apr 21 11:56:46 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1223]: New relevant interface eth1.IPv6 for mDNS.
Apr 21 11:56:46 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1223]: Registering new address record for fe80::e5b:8fff:fe27:9a64 on eth1.*.
```


Even during and after these incidents, **the LED on the device stays constantly ON and cyan**, which means it should be connected to a 4G (LTE) network.


After the April 21 crashes, I have adopted yet another method: keep the modem unplugged and plug it only when I have logged in and waited a couple of minutes. This has worked so far. (Until today, I had mostly kept the modem plugged in, even when I wasn't using the computer.) However, this method has an obvious drawback: it will wear the USB connection and there's the risk of the port getting damaged. I also fear that sooner or later the disconnections and crashes start happening again (regardless of whether or not the port is damaged). They did.

The disconnection/crash incidents have always occurred within about the first 5-8 minutes after logging in, so if I got past that, there would be no issues for that session, touch wood.

For what it's worth, I also have a four-year-old Asus laptop with Windows 7. Before April, there had never been any problems with that, even though I plug the modem in before turning the computer on and unplug it after turning the computer off. However, since April, there have been some issues, but they're uncommon and different so I think they might be unrelated (and possibly caused by old age).


[B]In short, my computer crashes if the internet is used, but only shortly after startup. Keeping the USB modem physically unplugged until a few minutes after logging in has worked so far, but I don't think that's a good solution.


UPDATE (June 29th, 2016): [/B]The workaround I mentioned above stopped working. I have also tried the following methods but *none* of them have worked:
- Did a clean install of 14.04 LTS
- Used an extension cable
- Used a different port
- Did a clean install of 16.04 LTS
- Bought a new dongle (similar to the old one)
- Changed the SIM card

Now I'm asking you if there are other solutions or at least workarounds to these disconnections and crashes.

---

### Post by ubuser4 on 2016-04-23
I've been thinking about my situation and now mostly believe the disconnections/crashes might be caused by 1) whatever software or service is responsible for updates OR 2) network manager OR 3) some kind of broken compatibility between the two. I'm pretty sure something in them broke right before or when the problem came up for the first time.

On another note, messages in /var/log/syslog mention this bug several times:  [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889). It's said on Launchpad that it's a  Firefox bug, but I've got the message even when I haven't used the  application during the session.

The questions that come into my mind are:
1. Why have these incidents happened only shortly after start-up?
2. How can I fix possible broken software?
3. Am I wrong here and my problems are caused by something else?
4. Could some event related to the hibernation I talked about have done physical damage to my laptop?
5. Is keeping using the workaround I explained in the end of my previous post and hoping it will still work in the future the only thing that can be done?

**UPDATE:** For reference, here are example logs (/var/log/syslog again):
Connecting the modem (after logging in and waiting):
```
Apr 22 18:55:31 u-HP-Pavilion-17-Notebook-PC kernel: [  220.793443] usb 1-1: new high-speed USB device number 2 using ehci-pci
Apr 22 18:55:31 u-HP-Pavilion-17-Notebook-PC kernel: [  220.926532] usb 1-1: New USB device found, idVendor=12d1, idProduct=1f01
Apr 22 18:55:31 u-HP-Pavilion-17-Notebook-PC kernel: [  220.926542] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Apr 22 18:55:31 u-HP-Pavilion-17-Notebook-PC kernel: [  220.926547] usb 1-1: Product: HUAWEI_MOBILE
Apr 22 18:55:31 u-HP-Pavilion-17-Notebook-PC kernel: [  220.926552] usb 1-1: Manufacturer: HUAWEI_MOBILE
Apr 22 18:55:31 u-HP-Pavilion-17-Notebook-PC kernel: [  220.926556] usb 1-1: SerialNumber: 0123456789ABCDEF
Apr 22 18:55:31 u-HP-Pavilion-17-Notebook-PC mtp-probe: checking bus 1, device 2: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1"
Apr 22 18:55:31 u-HP-Pavilion-17-Notebook-PC mtp-probe: bus: 1, device: 2 was not an MTP device
Apr 22 18:55:31 u-HP-Pavilion-17-Notebook-PC kernel: [  221.446068] usb-storage 1-1:1.0: USB Mass Storage device detected
Apr 22 18:55:31 u-HP-Pavilion-17-Notebook-PC kernel: [  221.446514] scsi4 : usb-storage 1-1:1.0
Apr 22 18:55:31 u-HP-Pavilion-17-Notebook-PC kernel: [  221.446684] usbcore: registered new interface driver usb-storage
Apr 22 18:55:32 u-HP-Pavilion-17-Notebook-PC kernel: [  222.450563] scsi 4:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Apr 22 18:55:32 u-HP-Pavilion-17-Notebook-PC kernel: [  222.451164] scsi 4:0:0:1: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
Apr 22 18:55:32 u-HP-Pavilion-17-Notebook-PC kernel: [  222.454687] sr1: scsi-1 drive
Apr 22 18:55:32 u-HP-Pavilion-17-Notebook-PC kernel: [  222.454988] sr 4:0:0:0: Attached scsi CD-ROM sr1
Apr 22 18:55:32 u-HP-Pavilion-17-Notebook-PC kernel: [  222.455434] sr 4:0:0:0: Attached scsi generic sg2 type 5
Apr 22 18:55:32 u-HP-Pavilion-17-Notebook-PC kernel: [  222.456160] sd 4:0:0:1: Attached scsi generic sg3 type 0
Apr 22 18:55:32 u-HP-Pavilion-17-Notebook-PC kernel: [  222.472865] sd 4:0:0:1: [sdb] Attached SCSI removable disk
Apr 22 18:55:33 u-HP-Pavilion-17-Notebook-PC usb_modeswitch: switching device 12d1:1f01 on 001/002
Apr 22 18:55:33 u-HP-Pavilion-17-Notebook-PC kernel: [  222.823529] usb 1-1: USB disconnect, device number 2
Apr 22 18:55:33 u-HP-Pavilion-17-Notebook-PC kernel: [  223.482521] usb 1-1: new high-speed USB device number 3 using ehci-pci
Apr 22 18:55:33 u-HP-Pavilion-17-Notebook-PC kernel: [  223.615472] usb 1-1: New USB device found, idVendor=12d1, idProduct=14dc
Apr 22 18:55:33 u-HP-Pavilion-17-Notebook-PC kernel: [  223.615483] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Apr 22 18:55:33 u-HP-Pavilion-17-Notebook-PC kernel: [  223.615490] usb 1-1: Product: HUAWEI_MOBILE
Apr 22 18:55:33 u-HP-Pavilion-17-Notebook-PC kernel: [  223.615495] usb 1-1: Manufacturer: HUAWEI_MOBILE
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC kernel: [  223.755962] usb-storage 1-1:1.2: USB Mass Storage device detected
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC kernel: [  223.756127] scsi5 : usb-storage 1-1:1.2
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC mtp-probe: checking bus 1, device 3: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1"
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC mtp-probe: bus: 1, device: 3 was not an MTP device
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC kernel: [  223.910621] cdc_ether 1-1:1.0 eth1: register 'cdc_ether' at usb-0000:00:12.2-1, CDC Ethernet Device, 0c:5b:8f:27:9a:64
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC kernel: [  223.910690] usbcore: registered new interface driver cdc_ether
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1)
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1): no ifupdown configuration found.
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <warn> failed to allocate link cache: (-12) Object not found
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): carrier is OFF
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): new Ethernet device (driver: 'cdc_ether' ifindex: 4)
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): now managed
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): bringing up device.
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): carrier now ON (device state 20)
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): preparing device.
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): deactivating device (reason 'managed') [2]
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Added default wired connection 'Kiinteä yhteys 2' for /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Auto-activating connection 'Kiinteä yhteys 2'.
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) starting connection 'Kiinteä yhteys 2'
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> dhclient started with pid 2542
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Beginning IP6 addrconf.
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): carrier now OFF (device state 70, deferring action for 4 seconds)
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC kernel: [  224.123910] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC kernel: [  224.124134] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC dhclient: Copyright 2004-2011 Internet Systems Consortium.
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC dhclient: All rights reserved.
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC dhclient: 
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC dhclient: Listening on LPF/eth1/0c:5b:8f:27:9a:64
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   LPF/eth1/0c:5b:8f:27:9a:64
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   Socket/fallback
Apr 22 18:55:34 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 22 18:55:35 u-HP-Pavilion-17-Notebook-PC kernel: [  224.758856] scsi 5:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
Apr 22 18:55:35 u-HP-Pavilion-17-Notebook-PC kernel: [  224.759325] sd 5:0:0:0: Attached scsi generic sg2 type 0
Apr 22 18:55:35 u-HP-Pavilion-17-Notebook-PC kernel: [  224.766748] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Apr 22 18:55:37 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr 22 18:55:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): carrier now ON (device state 70)
Apr 22 18:55:39 u-HP-Pavilion-17-Notebook-PC kernel: [  228.766601] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 22 18:55:40 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::e5b:8fff:fe27:9a64.
Apr 22 18:55:40 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: New relevant interface eth1.IPv6 for mDNS.
Apr 22 18:55:40 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Registering new address record for fe80::e5b:8fff:fe27:9a64 on eth1.*.
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Beginning DHCPv6 transaction (timeout in 45 seconds)
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> dhclient started with pid 2558
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC dhclient: Copyright 2004-2011 Internet Systems Consortium.
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC dhclient: All rights reserved.
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC dhclient: 
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC dhclient: Bound to *:546
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): DHCPv6 state changed nbi -> preinit6
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC dhclient: Listening on Socket/eth1
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   Socket/eth1
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::e5b:8fff:fe27:9a64.
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Joining mDNS multicast group on interface eth1.IPv6 with address 2001:14bb:170:888b:e5b:8fff:fe27:9a64.
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Registering new address record for 2001:14bb:170:888b:e5b:8fff:fe27:9a64 on eth1.*.
Apr 22 18:55:43 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Withdrawing address record for fe80::e5b:8fff:fe27:9a64 on eth1.
Apr 22 18:55:44 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 1080ms.
Apr 22 18:55:44 u-HP-Pavilion-17-Notebook-PC kernel: [  233.685009] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=UDP SPT=48987 DPT=546 LEN=115 
Apr 22 18:55:44 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Registering new address record for 2001:14bb:170:888b:bcdb:41cf:e8c0:350e on eth1.*.
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 2090ms.
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC kernel: [  234.763855] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=UDP SPT=48987 DPT=546 LEN=115 
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPREQUEST of 192.168.1.100 on eth1 to 255.255.255.255 port 67
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPOFFER of 192.168.1.100 from 192.168.1.1
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC dhclient: bound to 192.168.1.100 -- renewal in 33484 seconds.
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): DHCPv4 state changed preinit -> bound
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info>   address 192.168.1.100
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info>   prefix 24 (255.255.255.0)
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info>   gateway 192.168.1.1
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info>   nameserver '192.168.1.1'
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info>   nameserver '192.168.1.1'
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: New relevant interface eth1.IPv4 for mDNS.
Apr 22 18:55:45 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> DNS: starting dnsmasq...
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <error> [1461340546.480399] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <error> [1461340546.480452] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <warn> DNS: plugin dnsmasq update failed
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): writing resolv.conf to /sbin/resolvconf
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC dnsmasq[2561]: started, version 2.59 cache disabled
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC dnsmasq[2561]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC dnsmasq[2561]: DBus support enabled: connected to system bus
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC dnsmasq[2561]: warning: no upstream servers configured
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Policy set 'Kiinteä yhteys 2' (eth1) as default for IPv4 routing and DNS.
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) successful, device activated.
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC dbus[1089]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <warn> dnsmasq appeared on DBus: :1.75
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): writing resolv.conf to /sbin/resolvconf
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC dnsmasq[2561]: setting upstream servers from DBus
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC dnsmasq[2561]: using nameserver 192.168.1.1#53
Apr 22 18:55:46 u-HP-Pavilion-17-Notebook-PC dbus[1089]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 22 18:55:47 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 4050ms.
Apr 22 18:55:47 u-HP-Pavilion-17-Notebook-PC kernel: [  236.861544] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=UDP SPT=48987 DPT=546 LEN=115 
Apr 22 18:55:51 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 8240ms.
Apr 22 18:55:51 u-HP-Pavilion-17-Notebook-PC kernel: [  240.897244] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=48987 DPT=546 LEN=115 
Apr 22 18:55:56 u-HP-Pavilion-17-Notebook-PC ntpdate[2661]: step time server 2001:67c:1560:8003::c7 offset 0.618327 sec
Apr 22 18:56:00 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 16860ms.
Apr 22 18:56:00 u-HP-Pavilion-17-Notebook-PC kernel: [  249.148180] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=48987 DPT=546 LEN=115 
Apr 22 18:56:16 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 33110ms.
Apr 22 18:56:17 u-HP-Pavilion-17-Notebook-PC kernel: [  265.999874] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=48987 DPT=546 LEN=115 
Apr 22 18:56:28 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <warn> (eth1): DHCPv6 request timed out.
Apr 22 18:56:29 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2558
Apr 22 18:56:29 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 22 18:56:29 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 22 18:56:29 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```
Disconnecting the modem (I clicked Disconnect in the network manager applet before unplugging the device):
```
Apr 22 22:20:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Apr 22 22:20:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): deactivating device (reason 'user-requested') [39]
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2542
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Withdrawing address record for 2001:14bb:170:888b:bcdb:41cf:e8c0:350e on eth1.
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Withdrawing address record for 2001:14bb:170:888b:e5b:8fff:fe27:9a64 on eth1.
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Leaving mDNS multicast group on interface eth1.IPv6 with address 2001:14bb:170:888b:e5b:8fff:fe27:9a64.
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::e5b:8fff:fe27:9a64.
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Registering new address record for fe80::e5b:8fff:fe27:9a64 on eth1.*.
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Withdrawing address record for fe80::e5b:8fff:fe27:9a64 on eth1.
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::e5b:8fff:fe27:9a64.
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Interface eth1.IPv6 no longer relevant for mDNS.
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Withdrawing address record for 192.168.1.100 on eth1.
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <warn> DNS: plugin dnsmasq update failed
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): removing resolv.conf from /sbin/resolvconf
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC dnsmasq[2561]: setting upstream servers from DBus
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC dbus[1089]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 22 22:20:07 u-HP-Pavilion-17-Notebook-PC dbus[1089]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 22 22:20:08 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::e5b:8fff:fe27:9a64.
Apr 22 22:20:08 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: New relevant interface eth1.IPv6 for mDNS.
Apr 22 22:20:08 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Registering new address record for fe80::e5b:8fff:fe27:9a64 on eth1.*.
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC kernel: [12487.111903] usb 1-1: USB disconnect, device number 3
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Interface eth1.IPv6 no longer relevant for mDNS.
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::e5b:8fff:fe27:9a64.
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): carrier now OFF (device state 30)
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Withdrawing address record for fe80::e5b:8fff:fe27:9a64 on eth1.
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): device state change: disconnected -> unavailable (reason 'carrier-changed') [30 20 40]
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): deactivating device (reason 'carrier-changed') [40]
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1200]: Withdrawing workstation service for eth1.
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <warn> (4) failed to find interface name for index
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: nm_system_iface_flush_routes: assertion `iface != NULL' failed
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <warn> (4) failed to find interface name for index
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC kernel: [12487.114145] cdc_ether 1-1:1.0 eth1: unregister 'cdc_ether' usb-0000:00:12.2-1, CDC Ethernet Device
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1)
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): now unmanaged
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> (eth1): cleaning up...
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <warn> (4) failed to find interface name for index
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: (nm-system.c:685):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <error> [1461352811.418897] [nm-system.c:687] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Apr 22 22:20:11 u-HP-Pavilion-17-Notebook-PC NetworkManager[1232]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
```
I just noticed that the Launchpad URL appears here as well. Perhaps I should unplug the modem when the computer is off to prevent any further damage? I also noticed that the messages here in general are very similar to the ones that were printed during the disconnection/crash incidents. Now I'm scared.

---

### Post by ubuser4 on 2016-04-24
I added a short summary of my problem to the end of the first post. Here it is again: **My computer crashes if the internet is used, but only shortly after  startup. Keeping the USB modem physically unplugged until a few minutes  after logging in has worked so far, but I don't think that's a good  solution. I'd like to be able to use the internet 1) without having to wait and physically plug the modem in every time and also 2) without being scared of the next possible freeze.**

I came up with some more thoughts (none of which, except maybe 4, are that good in my opinion):
1. If only there was some easy way to delay the start-up of the modem or at least disable the automatic connection. However, this would only be a workaround and not a real solution, as it would only "hide" the underlying problem, maybe even unsuccessfully sometimes (e.g. if the delay happens to be too small). I'd also still have to wait.
2. Purge and reinstall network-manager or packagekit and aptdaemon. This would be very tricky, especially the network-manager part.
3. Turn off checks for updates. This would obviously be a workaround and I've read it can be difficult to disable automatic update checks completely.
4. Upgrade to 14.04 and hope the problem goes away.
5. Reinstall everything and hope that solves the problem. I'd rather not do this.

Any thoughts, suggestions, or other ideas?

---

### Post by ubuser4 on 2016-04-25
Has no one else experienced anything similar?
Should I have asked on the Networking & Wireless sub-forum instead?

---

### Post by ubuser4 on 2016-04-27
bump

---

### Post by ubuser4 on 2016-04-28
I tried a live session with Ubuntu 14.04.4 and everything worked **perfectly** even though the modem/dongle was plugged in all the time. (Except the startup was slow, but then again, this is often the case in live sessions. There were also some problems with the GPU during the startup, but I didn't experience anything negative after that.)

This is how I did it:
1. Turned the computer on normally and logged in.
2. Waited a couple of minutes.
3. Plugged in the modem and waited until the connection was established and a couple of minutes for good measure.
4. Inserted the Ubuntu 14.04.4 DVD that I had made earlier (from the standard amd64 desktop image found on ubuntu.com) and waited until it started running. Selected "Cancel" when a dialog asking what to do appeared.
5. Rebooted the computer with the DVD inside.
6. Entered the live session: selected "Try Ubuntu", waited until it started, did all kinds of things (used Firefox, browsed files and settings, read logs).
7. Exited the live session: selected "Shut Down" (or whatever it's called, I already forgot) in the menu and confirmed I wanted to shutdown, waited, removed the DVD, closed tray and shut down the computer by pressing Enter. After that, unplugged the USB modem.

Judging from the successful live-session test, it seems doing a clean install would indeed be one solution (assuming, of course, that the slowness of the startup didn't prevent the error from occurring). However, I think I'm going to try a thing or two before resorting to that.

---

### Post by ubuser4 on 2016-05-03
I looked into purging and reinstalling packagekit, aptdaemon, avahi, etc. (software whose configurations I think broke when the crashes/freezes started to occur), but completely removing even one of them would remove so many other packages that I might as well do a clean install.

I might do it in a few days if I have time, unless other solutions turn up.

---

### Post by ryu3 on 2016-05-07
I am having problem with mint 17.3 XFCE crashing whenever I use the menu in the bottom right. It doesn't happen on first menu use but it consistently occurs in under 30 seconds of using the menu.

---

### Post by mörgæs on 2016-05-07
> **ubuser4 said:**
> I might as well do a clean install.


Please post the results when you do it. It will help others with a similar problem.

---

### Post by ubuser4 on 2016-05-08
Today, **the "wait and plug" method failed**. After a few minutes of browsing, the connection disappeared and knowing what was coming, I shut down the computer as fast as I could, averting the crash. Perhaps I plugged the modem in too soon, or perhaps the updater was doing something special.

Here's a snippet from /var/log/syslog. It starts shortly before the AptDaemon runs and ends when the shutdown procedure is complete:
```
May  8 15:48:44 u-HP-Pavilion-17-Notebook-PC dbus[1054]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
May  8 15:48:44 u-HP-Pavilion-17-Notebook-PC dbus[1054]: [system] Successfully activated service 'org.freedesktop.UDisks'
May  8 15:48:59 u-HP-Pavilion-17-Notebook-PC goa[2327]: goa-daemon version 3.4.0 starting [main.c:112, main()]
May  8 15:49:57 u-HP-Pavilion-17-Notebook-PC dbus[1054]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
May  8 15:50:01 u-HP-Pavilion-17-Notebook-PC AptDaemon: INFO: Initializing daemon
May  8 15:50:01 u-HP-Pavilion-17-Notebook-PC AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
May  8 15:50:01 u-HP-Pavilion-17-Notebook-PC dbus[1054]: [system] Successfully activated service 'org.freedesktop.PackageKit'
May  8 15:50:01 u-HP-Pavilion-17-Notebook-PC AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
May  8 15:50:01 u-HP-Pavilion-17-Notebook-PC AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/13a45de6a654429c92461d8869ac81cf
May  8 15:50:01 u-HP-Pavilion-17-Notebook-PC AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/13a45de6a654429c92461d8869ac81cf
May  8 15:50:07 u-HP-Pavilion-17-Notebook-PC AptDaemon.PackageKit: INFO: Get updates()
May  8 15:50:08 u-HP-Pavilion-17-Notebook-PC AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/13a45de6a654429c92461d8869ac81cf
May  8 15:50:31 u-HP-Pavilion-17-Notebook-PC kernel: [  163.984374] usb 1-1: new high-speed USB device number 2 using ehci-pci
May  8 15:50:32 u-HP-Pavilion-17-Notebook-PC kernel: [  164.117797] usb 1-1: New USB device found, idVendor=12d1, idProduct=1f01
May  8 15:50:32 u-HP-Pavilion-17-Notebook-PC kernel: [  164.117806] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May  8 15:50:32 u-HP-Pavilion-17-Notebook-PC kernel: [  164.117812] usb 1-1: Product: HUAWEI_MOBILE
May  8 15:50:32 u-HP-Pavilion-17-Notebook-PC kernel: [  164.117816] usb 1-1: Manufacturer: HUAWEI_MOBILE
May  8 15:50:32 u-HP-Pavilion-17-Notebook-PC kernel: [  164.117820] usb 1-1: SerialNumber: 0123456789ABCDEF
May  8 15:50:32 u-HP-Pavilion-17-Notebook-PC mtp-probe: checking bus 1, device 2: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1"
May  8 15:50:32 u-HP-Pavilion-17-Notebook-PC mtp-probe: bus: 1, device: 2 was not an MTP device
May  8 15:50:32 u-HP-Pavilion-17-Notebook-PC kernel: [  164.372055] usb-storage 1-1:1.0: USB Mass Storage device detected
May  8 15:50:32 u-HP-Pavilion-17-Notebook-PC kernel: [  164.372204] scsi4 : usb-storage 1-1:1.0
May  8 15:50:32 u-HP-Pavilion-17-Notebook-PC kernel: [  164.372383] usbcore: registered new interface driver usb-storage
May  8 15:50:33 u-HP-Pavilion-17-Notebook-PC kernel: [  165.378656] scsi 4:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
May  8 15:50:33 u-HP-Pavilion-17-Notebook-PC kernel: [  165.379961] scsi 4:0:0:1: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
May  8 15:50:33 u-HP-Pavilion-17-Notebook-PC kernel: [  165.384354] sr1: scsi-1 drive
May  8 15:50:33 u-HP-Pavilion-17-Notebook-PC kernel: [  165.384647] sr 4:0:0:0: Attached scsi CD-ROM sr1
May  8 15:50:33 u-HP-Pavilion-17-Notebook-PC kernel: [  165.384825] sr 4:0:0:0: Attached scsi generic sg2 type 5
May  8 15:50:33 u-HP-Pavilion-17-Notebook-PC kernel: [  165.385988] sd 4:0:0:1: Attached scsi generic sg3 type 0
May  8 15:50:33 u-HP-Pavilion-17-Notebook-PC kernel: [  165.392504] sd 4:0:0:1: [sdb] Attached SCSI removable disk
May  8 15:50:33 u-HP-Pavilion-17-Notebook-PC usb_modeswitch: switching device 12d1:1f01 on 001/002
May  8 15:50:33 u-HP-Pavilion-17-Notebook-PC kernel: [  165.677488] usb 1-1: USB disconnect, device number 2
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC kernel: [  166.282578] usb 1-1: new high-speed USB device number 3 using ehci-pci
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC kernel: [  166.415905] usb 1-1: New USB device found, idVendor=12d1, idProduct=14dc
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC kernel: [  166.415914] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC kernel: [  166.415919] usb 1-1: Product: HUAWEI_MOBILE
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC kernel: [  166.415924] usb 1-1: Manufacturer: HUAWEI_MOBILE
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC kernel: [  166.542500] usb-storage 1-1:1.2: USB Mass Storage device detected
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC kernel: [  166.542655] scsi5 : usb-storage 1-1:1.2
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC mtp-probe: checking bus 1, device 3: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1"
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC mtp-probe: bus: 1, device: 3 was not an MTP device
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC kernel: [  166.699412] cdc_ether 1-1:1.0 eth1: register 'cdc_ether' at usb-0000:00:12.2-1, CDC Ethernet Device, 0c:5b:8f:27:9a:64
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC kernel: [  166.699483] usbcore: registered new interface driver cdc_ether
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1)
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1): no ifupdown configuration found.
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <warn> failed to allocate link cache: (-12) Object not found
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): carrier is OFF
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): new Ethernet device (driver: 'cdc_ether' ifindex: 4)
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): now managed
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): bringing up device.
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): carrier now ON (device state 20)
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): preparing device.
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): deactivating device (reason 'managed') [2]
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Added default wired connection 'Kiinteä yhteys 2' for /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Auto-activating connection 'Kiinteä yhteys 2'.
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) starting connection 'Kiinteä yhteys 2'
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
May  8 15:50:34 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> dhclient started with pid 2516
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Beginning IP6 addrconf.
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC kernel: [  167.211083] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): carrier now OFF (device state 70, deferring action for 4 seconds)
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC kernel: [  167.211342] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC dhclient: Copyright 2004-2011 Internet Systems Consortium.
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC dhclient: All rights reserved.
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC dhclient: 
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): DHCPv4 state changed nbi -> preinit
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC dhclient: Listening on LPF/eth1/0c:5b:8f:27:9a:64
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   LPF/eth1/0c:5b:8f:27:9a:64
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   Socket/fallback
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC kernel: [  167.549712] scsi 5:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC kernel: [  167.550175] sd 5:0:0:0: Attached scsi generic sg2 type 0
May  8 15:50:35 u-HP-Pavilion-17-Notebook-PC kernel: [  167.552618] sd 5:0:0:0: [sdb] Attached SCSI removable disk
May  8 15:50:38 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: ip-config -> unavailable (reason 'carrier-changed') [70 20 40]
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): deactivating device (reason 'carrier-changed') [40]
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2516
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC kernel: [  171.486145] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): carrier now ON (device state 20)
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC kernel: [  171.837487] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Auto-activating connection 'Kiinteä yhteys 2'.
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) starting connection 'Kiinteä yhteys 2'
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> dhclient started with pid 2532
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Beginning IP6 addrconf.
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: Copyright 2004-2011 Internet Systems Consortium.
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: All rights reserved.
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: 
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC kernel: [  171.848891] audit_printk_skb: 126 callbacks suppressed
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC kernel: [  171.848899] type=1400 audit(1462711839.813:75): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" name="/var/lib/dhcp/dhclient-bea0d3ec-bc0c-4d95-9e93-67e625d24ac6-eth1.lease" pid=2533 comm="nm-dhcp-client." requested_mask="r" denied_mask="r" fsuid=0 ouid=0
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): DHCPv4 state changed nbi -> preinit
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: Listening on LPF/eth1/0c:5b:8f:27:9a:64
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   LPF/eth1/0c:5b:8f:27:9a:64
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   Socket/fallback
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPREQUEST of 192.168.1.100 on eth1 to 255.255.255.255 port 67
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPOFFER of 192.168.1.100 from 192.168.1.1
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC kernel: [  171.917473] type=1400 audit(1462711839.881:76): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" name="/var/lib/dhcp/dhclient-bea0d3ec-bc0c-4d95-9e93-67e625d24ac6-eth1.lease" pid=2534 comm="nm-dhcp-client." requested_mask="r" denied_mask="r" fsuid=0 ouid=0
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC dhclient: bound to 192.168.1.100 -- renewal in 36817 seconds.
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): DHCPv4 state changed preinit -> bound
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info>   address 192.168.1.100
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info>   prefix 24 (255.255.255.0)
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info>   gateway 192.168.1.1
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info>   nameserver '192.168.1.1'
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info>   nameserver '192.168.1.1'
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: New relevant interface eth1.IPv4 for mDNS.
May  8 15:50:39 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Registering new address record for 192.168.1.100 on eth1.IPv4.
May  8 15:50:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> DNS: starting dnsmasq...
May  8 15:50:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <error> [1462711840.922698] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
May  8 15:50:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <error> [1462711840.922745] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
May  8 15:50:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <warn> DNS: plugin dnsmasq update failed
May  8 15:50:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): writing resolv.conf to /sbin/resolvconf
May  8 15:50:40 u-HP-Pavilion-17-Notebook-PC dnsmasq[2535]: started, version 2.59 cache disabled
May  8 15:50:40 u-HP-Pavilion-17-Notebook-PC dnsmasq[2535]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May  8 15:50:40 u-HP-Pavilion-17-Notebook-PC dnsmasq[2535]: DBus support enabled: connected to system bus
May  8 15:50:40 u-HP-Pavilion-17-Notebook-PC dnsmasq[2535]: warning: no upstream servers configured
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: ip-config -> activated (reason 'none') [70 100 0]
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Policy set 'Kiinteä yhteys 2' (eth1) as default for IPv4 routing and DNS.
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) successful, device activated.
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC dbus[1054]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <warn> dnsmasq appeared on DBus: :1.73
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): writing resolv.conf to /sbin/resolvconf
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC dnsmasq[2535]: setting upstream servers from DBus
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC dnsmasq[2535]: using nameserver 192.168.1.1#53
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC dbus[1054]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::e5b:8fff:fe27:9a64.
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: New relevant interface eth1.IPv6 for mDNS.
May  8 15:50:41 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Registering new address record for fe80::e5b:8fff:fe27:9a64 on eth1.*.
May  8 15:50:44 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::e5b:8fff:fe27:9a64.
May  8 15:50:44 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Joining mDNS multicast group on interface eth1.IPv6 with address 2001:14bb:140:8749:e5b:8fff:fe27:9a64.
May  8 15:50:44 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Registering new address record for 2001:14bb:140:8749:e5b:8fff:fe27:9a64 on eth1.*.
May  8 15:50:44 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Withdrawing address record for fe80::e5b:8fff:fe27:9a64 on eth1.
May  8 15:50:45 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Registering new address record for 2001:14bb:140:8749:618c:573b:523a:f616 on eth1.*.
May  8 15:50:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
May  8 15:50:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Beginning DHCPv6 transaction (timeout in 45 seconds)
May  8 15:50:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> dhclient started with pid 2646
May  8 15:50:46 u-HP-Pavilion-17-Notebook-PC dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May  8 15:50:46 u-HP-Pavilion-17-Notebook-PC dhclient: Copyright 2004-2011 Internet Systems Consortium.
May  8 15:50:46 u-HP-Pavilion-17-Notebook-PC dhclient: All rights reserved.
May  8 15:50:46 u-HP-Pavilion-17-Notebook-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  8 15:50:46 u-HP-Pavilion-17-Notebook-PC dhclient: 
May  8 15:50:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): DHCPv6 state changed nbi -> preinit6
May  8 15:50:46 u-HP-Pavilion-17-Notebook-PC dhclient: Bound to *:546
May  8 15:50:46 u-HP-Pavilion-17-Notebook-PC dhclient: Listening on Socket/eth1
May  8 15:50:46 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   Socket/eth1
May  8 15:50:47 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 1040ms.
May  8 15:50:47 u-HP-Pavilion-17-Notebook-PC kernel: [  179.724152] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=UDP SPT=54620 DPT=546 LEN=115 
May  8 15:50:48 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 2020ms.
May  8 15:50:48 u-HP-Pavilion-17-Notebook-PC kernel: [  180.755130] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=UDP SPT=54620 DPT=546 LEN=115 
May  8 15:50:50 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 4240ms.
May  8 15:50:50 u-HP-Pavilion-17-Notebook-PC kernel: [  182.807158] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=64 FLOWLBL=0 PROTO=UDP SPT=54620 DPT=546 LEN=115 
May  8 15:50:54 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 8330ms.
May  8 15:50:54 u-HP-Pavilion-17-Notebook-PC kernel: [  187.041019] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=54620 DPT=546 LEN=115 
May  8 15:50:55 u-HP-Pavilion-17-Notebook-PC ntpdate[2638]: adjust time server 2001:67c:1560:8003::c7 offset -0.176791 sec
May  8 15:51:03 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 17200ms.
May  8 15:51:03 u-HP-Pavilion-17-Notebook-PC kernel: [  195.378998] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=54620 DPT=546 LEN=115 
May  8 15:51:20 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 34870ms.
May  8 15:51:20 u-HP-Pavilion-17-Notebook-PC kernel: [  212.625416] [UFW BLOCK] IN=eth1 OUT= MAC=0c:5b:8f:27:9a:64:ba:ab:be:34:00:00:86:dd SRC=fe80:0000:0000:0000:b8ab:beff:fe34:0000 DST=fe80:0000:0000:0000:0e5b:8fff:fe27:9a64 LEN=155 TC=0 HOPLIMIT=255 FLOWLBL=0 PROTO=UDP SPT=54620 DPT=546 LEN=115 
May  8 15:51:32 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <warn> (eth1): DHCPv6 request timed out.
May  8 15:51:32 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2646
May  8 15:51:32 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  8 15:51:32 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  8 15:51:32 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Interface eth1.IPv6 no longer relevant for mDNS.
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Leaving mDNS multicast group on interface eth1.IPv6 with address 2001:14bb:140:8749:e5b:8fff:fe27:9a64.
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Interface eth1.IPv4 no longer relevant for mDNS.
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC dhclient: receive_packet failed on eth1: Network is down
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC kernel: [  485.568266] cdc_ether 1-1:1.0 eth1: unregister 'cdc_ether' usb-0000:00:12.2-1, CDC Ethernet Device
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: IP_DROP_MEMBERSHIP failed: No such device
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Withdrawing address record for 2001:14bb:140:8749:618c:573b:523a:f616 on eth1.
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Withdrawing address record for 2001:14bb:140:8749:e5b:8fff:fe27:9a64 on eth1.
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Withdrawing address record for 192.168.1.100 on eth1.
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC avahi-daemon[1175]: Withdrawing workstation service for eth1.
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <warn> (4) failed to find interface name for index
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <warn> (4) failed to find interface name for index
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Policy set 'Kiinteä yhteys 2' (eth1) as default for IPv4 routing and DNS.
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <warn> (eth1): failed to update IPv6 config in response to Router Advertisement.
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: activated -> failed (reason 'none') [100 120 0]
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <warn> Activation (eth1) failed.
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/eth1, iface: eth1)
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): now unmanaged
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): device state change: failed -> unmanaged (reason 'removed') [120 10 36]
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): deactivating device (reason 'removed') [36]
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC dbus[1054]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC dbus[1054]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC kernel: [  485.705895] usb 1-1: reset high-speed USB device number 3 using ehci-pci
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2532
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <warn> (4) failed to find interface name for index
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: nm_system_iface_flush_routes: assertion `iface != NULL' failed
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <warn> (4) failed to find interface name for index
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <warn> DNS: plugin dnsmasq update failed
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): removing resolv.conf from /sbin/resolvconf
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC dnsmasq[2535]: setting upstream servers from DBus
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> (eth1): cleaning up...
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <warn> (4) failed to find interface name for index
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: (nm-system.c:685):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <error> [1462712153.387331] [nm-system.c:687] nm_system_iface_get_flags(): (unknown): failed to get interface link object
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May  8 15:55:53 u-HP-Pavilion-17-Notebook-PC NetworkManager[1282]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May  8 15:56:01 u-HP-Pavilion-17-Notebook-PC kernel: Kernel logging (proc) stopped.
```

I now believe the disconnections have something to do with AptDaemon quitting incorrectly. These lines don't appear in the log above or any other disconnection/crash logs except in the first one, but they do appear in the log now (and whenever the disconnections don't happen):
```
May  8 16:05:00 u-HP-Pavilion-17-Notebook-PC AptDaemon: INFO: Quitting due to inactivity
May  8 16:05:00 u-HP-Pavilion-17-Notebook-PC AptDaemon: INFO: Quitting was requested
```
These two messages appear in the log about 6 minutes after the daemon has checked for updates. The latest disconnection happened around the time when similar messages should have appeared.

By the way, I tried to disable automatic updates a couple of days ago, but the daemon was run anyway, so I don't think that would be a workaround and thus I re-enabled the updates on the same day.

Judging by these experiences, looks like the safest bet would be to wait 10 minutes instead of 2 after logging in and plug the modem in after that. However, I don't always have that much time to wait!


I haven't done the clean install yet. I'll do it tomorrow or the day after that if
1. I have time
AND
2. no other ideas come up before that.

I'm planning on installing version 14.04.4 LTS.

---

### Post by ubuser4 on 2016-05-19
**I did a clean install** 10 days ago (and again 4 days ago because I ran into another problem which I tried to solve in a wrong way and made my system unusable) and replaced Ubuntu 12.04.5 with 14.04.4 (I used the same DVD that I used for the live-session test). After that, **everything was fine** and I was able to start using the internet with little waiting and without freezes, even though I've kept the modem plugged in at all times! There have been no hibernate or suspend events after the clean install (I even disabled suspend, hibernation was already off) and it seems AptDaemon won't run on startup.

However, **a disconnection suddenly happened tonight**, only a couple of minutes after logging in. I didn't wait for a freeze but shut down the computer as soon as I realized what was going on.

Here's /var/log/syslog from the incident. I started using the internet at 23:05, shortly after the 6th message was printed. The last 5 messages are from a normal shutdown event. "Tiedostoa tai hakemistoa ei ole" means that file or directory was not found:
```
May 19 23:04:50 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 34220ms.
May 19 23:05:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <warn> (eth1): DHCPv6 request timed out.
May 19 23:05:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1491
May 19 23:05:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 19 23:05:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 19 23:05:02 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 19 23:05:04 u-HP-Pavilion-17-Notebook-PC gnome-session[2028]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC avahi-daemon[985]: Interface eth1.IPv6 no longer relevant for mDNS.
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC avahi-daemon[985]: Leaving mDNS multicast group on interface eth1.IPv6 with address 2001:14bb:180:1d37:b83a:12b6:805d:7c59.
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC kernel: [  156.144698] cdc_ether 3-1:1.0 eth1: unregister 'cdc_ether' usb-0000:00:12.2-1, CDC Ethernet Device
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC dhclient: receive_packet failed on eth1: Network is down
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC avahi-daemon[985]: Interface eth1.IPv4 no longer relevant for mDNS.
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC avahi-daemon[985]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC avahi-daemon[985]: Withdrawing address record for 2001:14bb:180:1d37:e5b:8fff:fe27:9a64 on eth1.
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC avahi-daemon[985]: Withdrawing address record for 2001:14bb:180:1d37:b83a:12b6:805d:7c59 on eth1.
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC avahi-daemon[985]: Withdrawing address record for 192.168.1.100 on eth1.
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC avahi-daemon[985]: Withdrawing workstation service for eth1.
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <warn> (4) failed to find interface name for index
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <warn> (eth1): failed to update IPv6 config in response to Router Advertisement.
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> (eth1): device state change: activated -> failed (reason 'config-failed') [100 120 4]
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC whoopsie[1223]: offline
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> NetworkManager state is now DISCONNECTED
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <warn> Activation (eth1) failed for connection 'Kiinteä yhteys 1'
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC dbus[870]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:12.2/usb3/3-1/3-1:1.0/net/eth1, iface: eth1)
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> (eth1): device state change: failed -> unmanaged (reason 'removed') [120 10 36]
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> (eth1): deactivating device (reason 'removed') [36]
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC dbus[870]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC kernel: [  156.286312] usb 3-1: reset high-speed USB device number 3 using ehci-pci
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1292
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/disable_ipv6': (2) Tiedostoa tai hakemistoa ei ole
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/accept_ra': (2) Tiedostoa tai hakemistoa ei ole
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/use_tempaddr': (2) Tiedostoa tai hakemistoa ei ole
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <warn> (4) failed to find interface name for index
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <warn> (4) failed to find interface name for index
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> Writing DNS information to /sbin/resolvconf
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC dnsmasq[1330]: setting upstream servers from DBus
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> (eth1): cleaning up...
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <warn> (4) failed to find interface name for index
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <error> [1463688381.286791] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> NetworkManager state is now CONNECTED_GLOBAL
May 19 23:06:21 u-HP-Pavilion-17-Notebook-PC NetworkManager[1079]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 19 23:06:26 u-HP-Pavilion-17-Notebook-PC kernel: [  161.403206] usb 3-1: device descriptor read/64, error -110
May 19 23:06:41 u-HP-Pavilion-17-Notebook-PC kernel: [  176.634772] usb 3-1: device descriptor read/64, error -110
May 19 23:06:41 u-HP-Pavilion-17-Notebook-PC kernel: [  176.850902] usb 3-1: reset high-speed USB device number 3 using ehci-pci
May 19 23:06:41 u-HP-Pavilion-17-Notebook-PC kernel: [  176.991080] usb 3-1: device descriptor read/64, error -71
May 19 23:06:42 u-HP-Pavilion-17-Notebook-PC kernel: [  177.231375] usb 3-1: device descriptor read/64, error -71
May 19 23:06:42 u-HP-Pavilion-17-Notebook-PC kernel: [  177.451596] usb 3-1: reset high-speed USB device number 3 using ehci-pci
May 19 23:06:42 u-HP-Pavilion-17-Notebook-PC kernel: [  177.875843] usb 3-1: device not accepting address 3, error -71
May 19 23:06:42 u-HP-Pavilion-17-Notebook-PC kernel: [  177.992066] usb 3-1: reset high-speed USB device number 3 using ehci-pci
May 19 23:06:43 u-HP-Pavilion-17-Notebook-PC kernel: [  178.416392] usb 3-1: device not accepting address 3, error -71
May 19 23:06:43 u-HP-Pavilion-17-Notebook-PC kernel: [  178.416602] usb 3-1: USB disconnect, device number 3
May 19 23:06:43 u-HP-Pavilion-17-Notebook-PC kernel: [  178.560423] usb 3-1: new high-speed USB device number 4 using ehci-pci
May 19 23:06:43 u-HP-Pavilion-17-Notebook-PC kernel: [  178.696787] usb 3-1: device descriptor read/64, error -71
May 19 23:06:43 u-HP-Pavilion-17-Notebook-PC kernel: [  178.937010] usb 3-1: device descriptor read/64, error -71
May 19 23:06:44 u-HP-Pavilion-17-Notebook-PC kernel: [  179.153236] usb 3-1: new high-speed USB device number 5 using ehci-pci
May 19 23:06:44 u-HP-Pavilion-17-Notebook-PC kernel: [  179.289357] usb 3-1: device descriptor read/64, error -71
May 19 23:06:44 u-HP-Pavilion-17-Notebook-PC kernel: [  179.529601] usb 3-1: device descriptor read/64, error -71
May 19 23:06:44 u-HP-Pavilion-17-Notebook-PC kernel: [  179.745825] usb 3-1: new high-speed USB device number 6 using ehci-pci
May 19 23:06:45 u-HP-Pavilion-17-Notebook-PC kernel: [  180.170240] usb 3-1: device not accepting address 6, error -71
May 19 23:06:45 u-HP-Pavilion-17-Notebook-PC kernel: [  180.282356] usb 3-1: new high-speed USB device number 7 using ehci-pci
May 19 23:06:45 u-HP-Pavilion-17-Notebook-PC kernel: [  180.706779] usb 3-1: device not accepting address 7, error -71
May 19 23:06:45 u-HP-Pavilion-17-Notebook-PC kernel: [  180.706838] usb usb3-port1: unable to enumerate USB device
May 19 23:06:45 u-HP-Pavilion-17-Notebook-PC kernel: [  181.023101] usb 5-1: new full-speed USB device number 2 using ohci-pci
May 19 23:06:46 u-HP-Pavilion-17-Notebook-PC kernel: [  181.163239] usb 5-1: device descriptor read/64, error -62
May 19 23:06:46 u-HP-Pavilion-17-Notebook-PC kernel: [  181.407489] usb 5-1: device descriptor read/64, error -62
May 19 23:06:46 u-HP-Pavilion-17-Notebook-PC kernel: [  181.647739] usb 5-1: new full-speed USB device number 3 using ohci-pci
May 19 23:06:46 u-HP-Pavilion-17-Notebook-PC kernel: [  181.787874] usb 5-1: device descriptor read/64, error -62
May 19 23:06:46 u-HP-Pavilion-17-Notebook-PC kernel: [  182.032079] usb 5-1: device descriptor read/64, error -62
May 19 23:06:47 u-HP-Pavilion-17-Notebook-PC kernel: [  182.272331] usb 5-1: new full-speed USB device number 4 using ohci-pci
May 19 23:06:47 u-HP-Pavilion-17-Notebook-PC kernel: [  182.680725] usb 5-1: device not accepting address 4, error -62
May 19 23:06:47 u-HP-Pavilion-17-Notebook-PC kernel: [  182.816871] usb 5-1: new full-speed USB device number 5 using ohci-pci
May 19 23:06:48 u-HP-Pavilion-17-Notebook-PC kernel: [  183.225271] usb 5-1: device not accepting address 5, error -62
May 19 23:06:48 u-HP-Pavilion-17-Notebook-PC kernel: [  183.225332] usb usb5-port1: unable to enumerate USB device
May 19 23:06:50 u-HP-Pavilion-17-Notebook-PC dbus[870]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
May 19 23:06:50 u-HP-Pavilion-17-Notebook-PC dbus[870]: [system] Successfully activated service 'org.freedesktop.systemd1'
May 19 23:06:50 u-HP-Pavilion-17-Notebook-PC colord: device removed: xrandr-AU Optronics
May 19 23:06:50 u-HP-Pavilion-17-Notebook-PC colord: Profile removed: icc-908d7de98361a20192b7d115e8f79beb
May 19 23:06:50 u-HP-Pavilion-17-Notebook-PC rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="875" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

Can my modem be broken even though it works on my other computer, or is this a bug?

**Should I also start a new thread, since I no longer use Ubuntu 12.04?**

---

### Post by mörgæs on 2016-05-20
If you suspect that 14.04 has a bug then a fresh install of 16.04 is your best option. 

If you edit the first post you can delete the '12.04' from the title.

---

### Post by ubuser4 on 2016-05-23
The problems don't stop. Today, yet another disconnection happened. It was again a few minutes after logging in.
Here's the related part of the /var/log/syslog. The last message before the first one here appeared almost 3.5 minutes before these:
```
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC dhclient: receive_packet failed on eth1: Network is down
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC kernel: [  281.085320] cdc_ether 3-1:1.0 eth1: unregister 'cdc_ether' usb-0000:00:12.2-1, CDC Ethernet Device
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <warn> (4) failed to find interface name for index
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <warn> (eth1): failed to update IPv6 config in response to Router Advertisement.
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: activated -> failed (reason 'config-failed') [100 120 4]
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC kernel: [  281.222769] usb 3-1: reset high-speed USB device number 3 using ehci-pci
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> NetworkManager state is now DISCONNECTED
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <warn> Activation (eth1) failed for connection 'Kiinteä yhteys 1'
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC dbus[892]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:12.2/usb3/3-1/3-1:1.0/net/eth1, iface: eth1)
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: failed -> unmanaged (reason 'removed') [120 10 36]
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): deactivating device (reason 'removed') [36]
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC dbus[892]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1290
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/disable_ipv6': (2) Tiedostoa tai hakemistoa ei ole
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/accept_ra': (2) Tiedostoa tai hakemistoa ei ole
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/use_tempaddr': (2) Tiedostoa tai hakemistoa ei ole
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <warn> (4) failed to find interface name for index
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <warn> (4) failed to find interface name for index
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Writing DNS information to /sbin/resolvconf
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC dnsmasq[1327]: setting upstream servers from DBus
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): cleaning up...
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <warn> (4) failed to find interface name for index
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <error> [1463986636.738316] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> NetworkManager state is now CONNECTED_GLOBAL
May 23 09:57:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 23 09:57:21 u-HP-Pavilion-17-Notebook-PC kernel: [  286.337438] usb 3-1: device descriptor read/64, error -110
May 23 09:57:36 u-HP-Pavilion-17-Notebook-PC kernel: [  301.561061] usb 3-1: device descriptor read/64, error -110
May 23 09:57:36 u-HP-Pavilion-17-Notebook-PC kernel: [  301.777045] usb 3-1: reset high-speed USB device number 3 using ehci-pci
May 23 09:57:37 u-HP-Pavilion-17-Notebook-PC kernel: [  301.913263] usb 3-1: device descriptor read/64, error -71
May 23 09:57:37 u-HP-Pavilion-17-Notebook-PC kernel: [  302.153336] usb 3-1: device descriptor read/64, error -71
May 23 09:57:37 u-HP-Pavilion-17-Notebook-PC kernel: [  302.369518] usb 3-1: reset high-speed USB device number 3 using ehci-pci
May 23 09:57:37 u-HP-Pavilion-17-Notebook-PC kernel: [  302.793724] usb 3-1: device not accepting address 3, error -71
May 23 09:57:37 u-HP-Pavilion-17-Notebook-PC kernel: [  302.905793] usb 3-1: reset high-speed USB device number 3 using ehci-pci
May 23 09:57:38 u-HP-Pavilion-17-Notebook-PC kernel: [  303.330026] usb 3-1: device not accepting address 3, error -71
May 23 09:57:38 u-HP-Pavilion-17-Notebook-PC kernel: [  303.330267] usb 3-1: USB disconnect, device number 3
May 23 09:57:38 u-HP-Pavilion-17-Notebook-PC kernel: [  303.461997] usb 3-1: new high-speed USB device number 4 using ehci-pci
May 23 09:57:38 u-HP-Pavilion-17-Notebook-PC kernel: [  303.598082] usb 3-1: device descriptor read/64, error -71
May 23 09:57:38 u-HP-Pavilion-17-Notebook-PC kernel: [  303.838194] usb 3-1: device descriptor read/64, error -71
May 23 09:57:39 u-HP-Pavilion-17-Notebook-PC kernel: [  304.054291] usb 3-1: new high-speed USB device number 5 using ehci-pci
May 23 09:57:39 u-HP-Pavilion-17-Notebook-PC kernel: [  304.190369] usb 3-1: device descriptor read/64, error -71
May 23 09:57:39 u-HP-Pavilion-17-Notebook-PC kernel: [  304.434495] usb 3-1: device descriptor read/64, error -71
May 23 09:57:39 u-HP-Pavilion-17-Notebook-PC kernel: [  304.650611] usb 3-1: new high-speed USB device number 6 using ehci-pci
May 23 09:57:40 u-HP-Pavilion-17-Notebook-PC kernel: [  305.074886] usb 3-1: device not accepting address 6, error -71
May 23 09:57:40 u-HP-Pavilion-17-Notebook-PC kernel: [  305.186860] usb 3-1: new high-speed USB device number 7 using ehci-pci
May 23 09:57:40 u-HP-Pavilion-17-Notebook-PC kernel: [  305.610996] usb 3-1: device not accepting address 7, error -71
May 23 09:57:40 u-HP-Pavilion-17-Notebook-PC kernel: [  305.611054] usb usb3-port1: unable to enumerate USB device
May 23 09:57:41 u-HP-Pavilion-17-Notebook-PC kernel: [  305.927258] usb 5-1: new full-speed USB device number 2 using ohci-pci
May 23 09:57:41 u-HP-Pavilion-17-Notebook-PC kernel: [  306.067324] usb 5-1: device descriptor read/64, error -62
May 23 09:57:41 u-HP-Pavilion-17-Notebook-PC kernel: [  306.311438] usb 5-1: device descriptor read/64, error -62
May 23 09:57:41 u-HP-Pavilion-17-Notebook-PC kernel: [  306.551576] usb 5-1: new full-speed USB device number 3 using ohci-pci
May 23 09:57:41 u-HP-Pavilion-17-Notebook-PC kernel: [  306.691628] usb 5-1: device descriptor read/64, error -62
May 23 09:57:42 u-HP-Pavilion-17-Notebook-PC kernel: [  306.935766] usb 5-1: device descriptor read/64, error -62
May 23 09:57:42 u-HP-Pavilion-17-Notebook-PC kernel: [  307.175870] usb 5-1: new full-speed USB device number 4 using ohci-pci
May 23 09:57:42 u-HP-Pavilion-17-Notebook-PC kernel: [  307.584035] usb 5-1: device not accepting address 4, error -62
May 23 09:57:42 u-HP-Pavilion-17-Notebook-PC kernel: [  307.720145] usb 5-1: new full-speed USB device number 5 using ohci-pci
May 23 09:57:43 u-HP-Pavilion-17-Notebook-PC kernel: [  308.128383] usb 5-1: device not accepting address 5, error -62
May 23 09:57:43 u-HP-Pavilion-17-Notebook-PC kernel: [  308.128421] usb usb5-port1: unable to enumerate USB device
```

I was away from the computer when that happened and returned at 10:00. The computer hadn't frozen, so I unplugged and replugged the modem. Here's the log for that (same file as above):
```
May 23 10:00:38 u-HP-Pavilion-17-Notebook-PC kernel: [  483.577035] usb 3-1: new high-speed USB device number 8 using ehci-pci
May 23 10:00:38 u-HP-Pavilion-17-Notebook-PC kernel: [  483.710100] usb 3-1: New USB device found, idVendor=12d1, idProduct=1f01
May 23 10:00:38 u-HP-Pavilion-17-Notebook-PC kernel: [  483.710108] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May 23 10:00:38 u-HP-Pavilion-17-Notebook-PC kernel: [  483.710114] usb 3-1: Product: HUAWEI_MOBILE
May 23 10:00:38 u-HP-Pavilion-17-Notebook-PC kernel: [  483.710118] usb 3-1: Manufacturer: HUAWEI_MOBILE
May 23 10:00:38 u-HP-Pavilion-17-Notebook-PC kernel: [  483.710121] usb 3-1: SerialNumber: 0123456789ABCDEF
May 23 10:00:38 u-HP-Pavilion-17-Notebook-PC kernel: [  483.751972] usb-storage 3-1:1.0: USB Mass Storage device detected
May 23 10:00:38 u-HP-Pavilion-17-Notebook-PC kernel: [  483.752181] scsi host6: usb-storage 3-1:1.0
May 23 10:00:38 u-HP-Pavilion-17-Notebook-PC mtp-probe: checking bus 3, device 8: "/sys/devices/pci0000:00/0000:00:12.2/usb3/3-1"
May 23 10:00:38 u-HP-Pavilion-17-Notebook-PC mtp-probe: bus: 3, device: 8 was not an MTP device
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC kernel: [  484.756397] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC kernel: [  484.756953] scsi 6:0:0:1: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC kernel: [  484.760985] sr 6:0:0:0: [sr1] scsi-1 drive
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC kernel: [  484.761327] sr 6:0:0:0: Attached scsi CD-ROM sr1
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC kernel: [  484.761752] sr 6:0:0:0: Attached scsi generic sg2 type 5
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC kernel: [  484.762786] sd 6:0:0:1: Attached scsi generic sg3 type 0
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC kernel: [  484.777620] sd 6:0:0:1: [sdb] Attached SCSI removable disk
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC usb_modeswitch: switch device 12d1:1f01 on 003/008
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC kernel: [  484.867143] systemd-udevd[2657]: Failed to apply ACL on /dev/sr1: No such file or directory
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC kernel: [  484.867156] systemd-udevd[2657]: Failed to apply ACL on /dev/sr1: No such file or directory
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC kernel: [  484.888885] usb 3-1: USB disconnect, device number 8
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC kernel: [  484.914308] systemd-udevd[2657]: Failed to apply ACL on /dev/sr1: No such file or directory
May 23 10:00:39 u-HP-Pavilion-17-Notebook-PC kernel: [  484.914326] systemd-udevd[2657]: Failed to apply ACL on /dev/sr1: No such file or directory
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC kernel: [  485.518003] usb 3-1: new high-speed USB device number 9 using ehci-pci
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC kernel: [  485.650928] usb 3-1: New USB device found, idVendor=12d1, idProduct=14dc
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC kernel: [  485.650934] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC kernel: [  485.650939] usb 3-1: Product: HUAWEI_MOBILE
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC kernel: [  485.650942] usb 3-1: Manufacturer: HUAWEI_MOBILE
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC kernel: [  485.819269] cdc_ether 3-1:1.0 eth1: register 'cdc_ether' at usb-0000:00:12.2-1, CDC Ethernet Device, 0c:5b:8f:27:9a:64
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC kernel: [  485.821487] usb-storage 3-1:1.2: USB Mass Storage device detected
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC kernel: [  485.821674] scsi host7: usb-storage 3-1:1.2
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC mtp-probe: checking bus 3, device 9: "/sys/devices/pci0000:00/0000:00:12.2/usb3/3-1"
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC mtp-probe: bus: 3, device: 9 was not an MTP device
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <warn> failed to allocate link cache: (-12) Object not found
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): carrier is OFF
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): new Ethernet device (driver: 'cdc_ether' ifindex: 5)
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/3
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): bringing up device.
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): carrier now ON (device state 20)
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): preparing device.
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): deactivating device (reason 'managed') [2]
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> NetworkManager state is now DISCONNECTED
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Added default wired connection 'Kiinteä yhteys 1' for /sys/devices/pci0000:00/0000:00:12.2/usb3/3-1/3-1:1.0/net/eth1
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.2/usb3/3-1/3-1:1.0/net/eth1, iface: eth1)
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.2/usb3/3-1/3-1:1.0/net/eth1, iface: eth1): no ifupdown configuration found.
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC kernel: [  485.839217] cdc_ether 3-1:1.0 eth1: kevent 12 may have been dropped
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Auto-activating connection 'Kiinteä yhteys 1'.
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) starting connection 'Kiinteä yhteys 1'
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> NetworkManager state is now CONNECTING
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): carrier now OFF (device state 40, deferring action for 4 seconds)
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> dhclient started with pid 2691
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Beginning IP6 addrconf.
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC dhclient: Internet Systems Consortium DHCP Client 4.2.4
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC dhclient: Copyright 2004-2012 Internet Systems Consortium.
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC dhclient: All rights reserved.
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC dhclient: 
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC kernel: [  485.863765] cdc_ether 3-1:1.0 eth1: kevent 12 may have been dropped
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC kernel: [  485.863888] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): DHCPv4 state changed nbi -> preinit
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC dhclient: Listening on LPF/eth1/0c:5b:8f:27:9a:64
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   LPF/eth1/0c:5b:8f:27:9a:64
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   Socket/fallback
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0xe6a93204)
May 23 10:00:40 u-HP-Pavilion-17-Notebook-PC usb_modeswitch: switched to 12d1:ffffffff on 003/008
May 23 10:00:41 u-HP-Pavilion-17-Notebook-PC kernel: [  486.825528] scsi 7:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
May 23 10:00:41 u-HP-Pavilion-17-Notebook-PC kernel: [  486.826078] sd 7:0:0:0: Attached scsi generic sg2 type 0
May 23 10:00:41 u-HP-Pavilion-17-Notebook-PC kernel: [  486.832316] sd 7:0:0:0: [sdb] Attached SCSI removable disk
May 23 10:00:43 u-HP-Pavilion-17-Notebook-PC ModemManager[936]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:12.2/usb3/3-1': not supported by any plugin
May 23 10:00:45 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: ip-config -> unavailable (reason 'carrier-changed') [70 20 40]
May 23 10:00:45 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): deactivating device (reason 'carrier-changed') [40]
May 23 10:00:45 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2691
May 23 10:00:45 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> NetworkManager state is now DISCONNECTED
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC kernel: [  491.620463] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC kernel: [  491.620481] cdc_ether 3-1:1.0 eth1: kevent 12 may have been dropped
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): carrier now ON (device state 20)
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Auto-activating connection 'Kiinteä yhteys 1'.
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) starting connection 'Kiinteä yhteys 1'
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> NetworkManager state is now CONNECTING
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> dhclient started with pid 2703
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Beginning IP6 addrconf.
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC kernel: [  491.630800] cdc_ether 3-1:1.0 eth1: kevent 12 may have been dropped
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: Internet Systems Consortium DHCP Client 4.2.4
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: Copyright 2004-2012 Internet Systems Consortium.
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: All rights reserved.
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: 
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): DHCPv4 state changed nbi -> preinit
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: Listening on LPF/eth1/0c:5b:8f:27:9a:64
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   LPF/eth1/0c:5b:8f:27:9a:64
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   Socket/fallback
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x2d3f57d)
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPREQUEST of 192.168.1.100 on eth1 to 255.255.255.255 port 67 (xid=0x7df5d302)
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPOFFER of 192.168.1.100 from 192.168.1.1
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC dhclient: bound to 192.168.1.100 -- renewal in 38223 seconds.
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): DHCPv4 state changed preinit -> bound
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info>   address 192.168.1.100
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info>   prefix 24 (255.255.255.0)
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info>   gateway 192.168.1.1
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info>   nameserver '192.168.1.1'
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info>   nameserver '192.168.1.1'
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 23 10:00:46 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
May 23 10:00:47 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
May 23 10:00:47 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
May 23 10:00:47 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
May 23 10:00:47 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> NetworkManager state is now CONNECTED_GLOBAL
May 23 10:00:47 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Policy set 'Kiinteä yhteys 1' (eth1) as default for IPv4 routing and DNS.
May 23 10:00:47 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Writing DNS information to /sbin/resolvconf
May 23 10:00:47 u-HP-Pavilion-17-Notebook-PC dnsmasq[1327]: setting upstream servers from DBus
May 23 10:00:47 u-HP-Pavilion-17-Notebook-PC dnsmasq[1327]: using nameserver 192.168.1.1#53
May 23 10:00:47 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) successful, device activated.
May 23 10:00:47 u-HP-Pavilion-17-Notebook-PC dbus[892]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 23 10:00:47 u-HP-Pavilion-17-Notebook-PC dbus[892]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 23 10:00:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
May 23 10:00:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Beginning DHCPv6 transaction (timeout in 45 seconds)
May 23 10:00:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> dhclient started with pid 2759
May 23 10:00:50 u-HP-Pavilion-17-Notebook-PC dhclient: Internet Systems Consortium DHCP Client 4.2.4
May 23 10:00:50 u-HP-Pavilion-17-Notebook-PC dhclient: Copyright 2004-2012 Internet Systems Consortium.
May 23 10:00:50 u-HP-Pavilion-17-Notebook-PC dhclient: All rights reserved.
May 23 10:00:50 u-HP-Pavilion-17-Notebook-PC dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 23 10:00:50 u-HP-Pavilion-17-Notebook-PC dhclient: 
May 23 10:00:50 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): DHCPv6 state changed nbi -> preinit6
May 23 10:00:50 u-HP-Pavilion-17-Notebook-PC dhclient: Bound to *:546
May 23 10:00:50 u-HP-Pavilion-17-Notebook-PC dhclient: Listening on Socket/eth1
May 23 10:00:50 u-HP-Pavilion-17-Notebook-PC dhclient: Sending on   Socket/eth1
May 23 10:00:51 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 1030ms.
May 23 10:00:52 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 2030ms.
May 23 10:00:52 u-HP-Pavilion-17-Notebook-PC whoopsie[1192]: online
May 23 10:00:54 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 4010ms.
May 23 10:00:58 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 7920ms.
May 23 10:00:59 u-HP-Pavilion-17-Notebook-PC ntpdate[2746]: adjust time server 91.189.89.199 offset 0.208913 sec
May 23 10:01:06 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 16630ms.
May 23 10:01:22 u-HP-Pavilion-17-Notebook-PC dhclient: XMT: Solicit on eth1, interval 33570ms.
May 23 10:01:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <warn> (eth1): DHCPv6 request timed out.
May 23 10:01:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2759
May 23 10:01:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 23 10:01:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 23 10:01:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1077]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```

Everything worked normally (or seemed that way), until the GUI froze. After that, the keyboard didn't work, so I shut down the computer by holding down the power button and then started it normally. I noticed that this error was saved in the log:
```
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.569177] BUG: unable to handle kernel paging request at 0000000000001ef3
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.569239] IP: [<ffffffff811d0cca>] kmem_cache_alloc_trace+0x7a/0x240
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.569290] PGD ad46b067 PUD 9ad2f067 PMD 0 
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.569326] Oops: 0000 [#1] SMP 
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.569351] Modules linked in: cdc_ether usbnet bnep rfcomm bluetooth binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat hp_wmi nf_conntrack_ftp nf_conntrack iptable_filter sparse_keymap ip_tables x_tables rtsx_pci_ms memstick kvm crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_hda_codec_realtek cryptd snd_hda_codec_generic snd_hda_codec_hdmi arc4 snd_hda_intel joydev snd_hda_codec rt2800pci rt2800mmio snd_hda_core rt2800lib snd_hwdep rt2x00pci snd_seq_midi rt2x00mmio input_leds snd_seq_midi_event rt2x00lib serio_raw k10temp snd_rawmidi snd_pcm mac80211 i2c_piix4 snd_seq cfg80211 snd_seq_device snd_timer eeprom_93cx6 crc_ccitt snd shpchp soundcore hp_accel mac_hid lis3lv02d input_polldev parport_pc ppdev lp hp_wireless parport uas hid_generic usb_storage usbhid hid rtsx_pci_sdmmc amdkfd amd_iommu_v2 radeon psmouse ahci i2c_algo_bit r8169 ttm mii rtsx_pci drm_kms_helper libahci drm wmi video
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570301] CPU: 1 PID: 2866 Comm: nautilus Not tainted 4.2.0-36-generic #42~14.04.1-Ubuntu
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570359] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570419] task: ffff88009ae53700 ti: ffff8801fcd20000 task.ti: ffff8801fcd20000
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570470] RIP: 0010:[<ffffffff811d0cca>]  [<ffffffff811d0cca>] kmem_cache_alloc_trace+0x7a/0x240
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570536] RSP: 0018:ffff8801fcd23c18  EFLAGS: 00010282
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570573] RAX: 0000000000000000 RBX: 00000000000080d0 RCX: 00000000000173ec
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570619] RDX: 00000000000173eb RSI: 00000000000080d0 RDI: ffff880216c01c00
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570668] RBP: ffff8801fcd23c68 R08: 0000000000019a60 R09: ffff880216c01c00
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570714] R10: ffffffff8135091b R11: 0000000000000000 R12: 00000000000080d0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570762] R13: ffff8801fcd23ef4 R14: 0000000000001ef3 R15: ffff880216c01c00
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570808] FS:  00007f12fc4967c0(0000) GS:ffff88021ec80000(0000) knlGS:0000000000000000
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570857] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570895] CR2: 0000000000001ef3 CR3: 000000009acf0000 CR4: 00000000000406e0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570942] Stack:
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.570957]  0000000000000000 ffff880216c01c00 ffffffff8135091b 0000000000000018
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571012]  ffff8801fcd23c98 ffff880216c8d030 ffff8801ff7a9400 ffff8801fcd23ef4
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571065]  ffff8801fcd23dc8 00000000000039f8 ffff8801fcd23c98 ffffffff8135091b
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571117] Call Trace:
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571142]  [<ffffffff8135091b>] ? apparmor_file_alloc_security+0x5b/0x160
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571190]  [<ffffffff8135091b>] apparmor_file_alloc_security+0x5b/0x160
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571235]  [<ffffffff811f004c>] ? get_empty_filp+0x5c/0x1a0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571276]  [<ffffffff81311ff3>] security_file_alloc+0x33/0x50
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571321]  [<ffffffff811f0083>] get_empty_filp+0x93/0x1a0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571366]  [<ffffffff811fc06e>] path_openat+0x2e/0x1360
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571408]  [<ffffffff811fabca>] ? walk_component+0x3a/0x230
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571453]  [<ffffffff811fd51f>] ? putname+0x5f/0x70
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571490]  [<ffffffff811fe46a>] do_filp_open+0x7a/0xd0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571528]  [<ffffffff811fd57f>] ? getname_flags+0x4f/0x1f0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571570]  [<ffffffff8120b606>] ? __alloc_fd+0x46/0x110
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571608]  [<ffffffff811ed919>] do_sys_open+0x129/0x270
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.571648]  [<ffffffff810996bd>] ? __put_cred+0x3d/0x50
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.573862]  [<ffffffff811ecda3>] ? SyS_access+0x193/0x1e0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.575851]  [<ffffffff811eda7e>] SyS_open+0x1e/0x20
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.577807]  [<ffffffff817c35b2>] entry_SYSCALL_64_fastpath+0x16/0x75
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.579743] Code: 4c 03 05 c2 94 e3 7e 4d 8b 30 49 8b 40 10 4d 85 f6 0f 84 5b 01 00 00 48 85 c0 0f 84 52 01 00 00 49 63 47 20 48 8d 4a 01 4d 8b 07 <49> 8b 1c 06 4c 89 f0 65 49 0f c7 08 0f 94 c0 84 c0 74 b9 49 63 
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.584024] RIP  [<ffffffff811d0cca>] kmem_cache_alloc_trace+0x7a/0x240
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.586123]  RSP <ffff8801fcd23c18>
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.588200] CR2: 0000000000001ef3
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.600855] ---[ end trace 38af98d968a0ffec ]---
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.616175] BUG: unable to handle kernel paging request at 0000000000001ef3
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.619069] IP: [<ffffffff811d0cca>] kmem_cache_alloc_trace+0x7a/0x240
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.621959] PGD 0 
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.624818] Oops: 0000 [#2] SMP 
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.627676] Modules linked in: cdc_ether usbnet bnep rfcomm bluetooth binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat hp_wmi nf_conntrack_ftp nf_conntrack iptable_filter sparse_keymap ip_tables x_tables rtsx_pci_ms memstick kvm crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_hda_codec_realtek cryptd snd_hda_codec_generic snd_hda_codec_hdmi arc4 snd_hda_intel joydev snd_hda_codec rt2800pci rt2800mmio snd_hda_core rt2800lib snd_hwdep rt2x00pci snd_seq_midi rt2x00mmio input_leds snd_seq_midi_event rt2x00lib serio_raw k10temp snd_rawmidi snd_pcm mac80211 i2c_piix4 snd_seq cfg80211 snd_seq_device snd_timer eeprom_93cx6 crc_ccitt snd shpchp soundcore hp_accel mac_hid lis3lv02d input_polldev parport_pc ppdev lp hp_wireless parport uas hid_generic usb_storage usbhid hid rtsx_pci_sdmmc amdkfd amd_iommu_v2 radeon psmouse ahci i2c_algo_bit r8169 ttm mii rtsx_pci drm_kms_helper libahci drm wmi video
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.650927] CPU: 1 PID: 1311 Comm: Xorg Tainted: G      D         4.2.0-36-generic #42~14.04.1-Ubuntu
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.654228] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.657468] task: ffff8800359e5280 ti: ffff880214380000 task.ti: ffff880214380000
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.660624] RIP: 0010:[<ffffffff811d0cca>]  [<ffffffff811d0cca>] kmem_cache_alloc_trace+0x7a/0x240
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.663743] RSP: 0018:ffff880214383a38  EFLAGS: 00010282
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.666749] RAX: 0000000000000000 RBX: 00000000000080d0 RCX: 00000000000173ee
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.669720] RDX: 00000000000173ed RSI: 00000000000080d0 RDI: ffff880216c01c00
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.672660] RBP: ffff880214383a88 R08: 0000000000019a60 R09: ffff880216c01c00
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.675565] R10: ffffffff8135091b R11: 00000000c020645d R12: 00000000000080d0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.678444] R13: ffffffff81823800 R14: 0000000000001ef3 R15: ffff880216c01c00
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.681292] FS:  00007f72c48218c0(0000) GS:ffff88021ec80000(0000) knlGS:0000000000000000
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.684175] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.687053] CR2: 0000000000001ef3 CR3: 0000000035f96000 CR4: 00000000000406e0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.689973] Stack:
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.692864]  ffffffff8120785d ffff880216c01c00 ffffffff8135091b 0000000000000018
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.695821]  ffff880216c15000 ffff880216c8d030 ffff8801ff7a9200 ffffffff81823800
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.698762]  ffff880216c15000 0000000000200000 ffff880214383ab8 ffffffff8135091b
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.701677] Call Trace:
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.704558]  [<ffffffff8120785d>] ? inode_init_always+0x11d/0x1d0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.707468]  [<ffffffff8135091b>] ? apparmor_file_alloc_security+0x5b/0x160
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.710374]  [<ffffffff8135091b>] apparmor_file_alloc_security+0x5b/0x160
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.713274]  [<ffffffff811f004c>] ? get_empty_filp+0x5c/0x1a0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.716181]  [<ffffffff81311ff3>] security_file_alloc+0x33/0x50
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.719056]  [<ffffffff811f0083>] get_empty_filp+0x93/0x1a0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.721917]  [<ffffffff811f01af>] alloc_file+0x1f/0xc0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.724764]  [<ffffffff811922b0>] __shmem_file_setup+0x100/0x1b0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.727614]  [<ffffffff81192370>] shmem_file_setup+0x10/0x20
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.730499]  [<ffffffffc002e20b>] drm_gem_object_init+0x2b/0x40 [drm]
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.733417]  [<ffffffffc0190818>] radeon_bo_create+0xb8/0x260 [radeon]
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.736287]  [<ffffffff8119470a>] ? shmem_undo_range+0x35a/0x690
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.739176]  [<ffffffffc00f25aa>] ? ttm_bo_release+0x11a/0x280 [ttm]
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.742101]  [<ffffffffc01a3a80>] radeon_gem_object_create+0xc0/0x1a0 [radeon]
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.745045]  [<ffffffffc01a3f0e>] radeon_gem_create_ioctl+0x5e/0x150 [radeon]
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.747992]  [<ffffffffc002f723>] drm_ioctl+0x363/0x680 [drm]
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.750958]  [<ffffffffc01a3eb0>] ? radeon_gem_pwrite_ioctl+0x30/0x30 [radeon]
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.753911]  [<ffffffff81208d9c>] ? destroy_inode+0x3c/0x60
May 2 repeatedly3 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.756877]  [<ffffffffc017204b>] radeon_drm_ioctl+0x4b/0x80 [radeon]
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.759837]  [<ffffffff8120155d>] do_vfs_ioctl+0x2cd/0x4b0
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.762801]  [<ffffffff8120de54>] ? mntput+0x24/0x40
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.765751]  [<ffffffff811f0510>] ? __fput+0x190/0x210
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.768608]  [<ffffffff812017b9>] SyS_ioctl+0x79/0x90
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.771380]  [<ffffffff817c35b2>] entry_SYSCALL_64_fastpath+0x16/0x75
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.774146] Code: 4c 03 05 c2 94 e3 7e 4d 8b 30 49 8b 40 10 4d 85 f6 0f 84 5b 01 00 00 48 85 c0 0f 84 52 01 00 00 49 63 47 20 48 8d 4a 01 4d 8b 07 <49> 8b 1c 06 4c 89 f0 65 49 0f c7 08 0f 94 c0 84 c0 74 b9 49 63 
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.780022] RIP  [<ffffffff811d0cca>] kmem_cache_alloc_trace+0x7a/0x240
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.782946]  RSP <ffff880214383a38>
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.785834] CR2: 0000000000001ef3
May 23 10:03:38 u-HP-Pavilion-17-Notebook-PC kernel: [  663.788762] ---[ end trace 38af98d968a0ffed ]---
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.560823] ------------[ cut here ]------------
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.560840] WARNING: CPU: 0 PID: 2451 at /build/linux-lts-wily-JUyKGw/linux-lts-wily-4.2.0/security/apparmor/file.c:317 aa_path_perm+0x120/0x130()
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.560844] AppArmor WARN aa_path_perm: ((!((label)->flags & FLAG_PROFILE))): 
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.560847] Modules linked in: cdc_ether usbnet bnep rfcomm bluetooth binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat hp_wmi nf_conntrack_ftp nf_conntrack iptable_filter sparse_keymap ip_tables x_tables rtsx_pci_ms memstick kvm crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_hda_codec_realtek cryptd snd_hda_codec_generic snd_hda_codec_hdmi arc4 snd_hda_intel joydev snd_hda_codec rt2800pci rt2800mmio snd_hda_core rt2800lib snd_hwdep rt2x00pci snd_seq_midi rt2x00mmio input_leds snd_seq_midi_event rt2x00lib serio_raw k10temp snd_rawmidi snd_pcm mac80211 i2c_piix4 snd_seq cfg80211 snd_seq_device snd_timer eeprom_93cx6 crc_ccitt snd shpchp soundcore hp_accel mac_hid lis3lv02d input_polldev parport_pc ppdev lp hp_wireless parport uas hid_generic usb_storage usbhid hid rtsx_pci_sdmmc amdkfd amd_iommu_v2 radeon psmouse ahci i2c_algo_bit r8169 ttm mii rtsx_pci drm_kms_helper libahci drm wmi video
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.560983] CPU: 0 PID: 2451 Comm: psensor Tainted: G      D         4.2.0-36-generic #42~14.04.1-Ubuntu
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.560986] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.560990]  0000000000000000 ffff8801ff7cbc88 ffffffff817bc0e7 ffff8801ff7cbcd8
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.560995]  ffffffff81ad6060 ffff8801ff7cbcc8 ffffffff81079b3a ffff8801ff7cbd28
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561000]  ffff880216c8d030 ffff8801ff7cbe08 00000000ffffff9c ffff8801ff7cbdf0
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561005] Call Trace:
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561015]  [<ffffffff817bc0e7>] dump_stack+0x63/0x81
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561022]  [<ffffffff81079b3a>] warn_slowpath_common+0x8a/0xc0
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561027]  [<ffffffff81079bb6>] warn_slowpath_fmt+0x46/0x50
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561033]  [<ffffffff811fd51f>] ? putname+0x5f/0x70
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561038]  [<ffffffff813524c0>] aa_path_perm+0x120/0x130
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561042]  [<ffffffff8134f89f>] common_perm+0x5f/0x100
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561046]  [<ffffffff8134f96b>] common_perm_cond+0x2b/0x30
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561050]  [<ffffffff8134f9b0>] apparmor_inode_getattr+0x40/0x50
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561055]  [<ffffffff81311ae1>] security_inode_getattr+0x41/0x60
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561061]  [<ffffffff811f3217>] vfs_getattr+0x17/0x30
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561066]  [<ffffffff811f32f5>] vfs_fstatat+0x65/0xa0
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561071]  [<ffffffff811f375f>] SYSC_newstat+0x1f/0x40
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561077]  [<ffffffff81203705>] ? SyS_poll+0x65/0xf0
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561081]  [<ffffffff811f39ce>] SyS_newstat+0xe/0x10
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561086]  [<ffffffff817c35b2>] entry_SYSCALL_64_fastpath+0x16/0x75
May 23 10:03:39 u-HP-Pavilion-17-Notebook-PC kernel: [  664.561089] ---[ end trace 38af98d968a0ffee ]---

```
The part after the "cut here" appeared repeatedly, presumably until the computer shut down.

The first error I can see here and in the previous disconnection is USB read/64 error -110 which apparently means the port can't supply enough power for the device and the solution in this case is to turn off the computer, wait, and turn it back on. Is there any way to prevent this error from occurring?

---

### Post by ubuser4 on 2016-05-23
> **mörgæs said:**
> If you suspect that 14.04 has a bug then a fresh install of 16.04 is your best option.

After reading about the USB read/64 errors, I now suspect the problem is somewhere in the hardware although I can't be sure because it happens randomly and without warning.

Thank you anyway for the suggestion.

---

### Post by mörgæs on 2016-05-23
Is the output shown in post #13 from 14.04 or 16.04?

---

### Post by ubuser4 on 2016-05-24
> **mörgæs said:**
> Is the output shown in post #13 from 14.04 or 16.04?

It's from 14.04.

---

### Post by mörgæs on 2016-05-24
The thread has now lasted a month. I think it's about time to try a clean install of 16.04.

Huawei E3372 is a new dongle and one can't expect old software to work with it.

---

### Post by ubuser4 on 2016-05-24
Does 16.04 support my GPU? According to HP ([http://support.hp.com/us-en/document/c03809123](http://support.hp.com/us-en/document/c03809123)), the microprocessor in my computer is "AMD Dual-Core A8-5550M APU with Radeon HD 8550G Graphics" (it's actually quad-core, not dual-core) and the video graphics system is "AMD Radeon HD 8550M/8670M Dual GPU". However, lspci -nn | grep VGA says "00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8550G] [1002:990d]". The command lspci | grep -E "VGA|3D" prints the same thing but with less details, and according to sudo lspci -v -s 00:01.0, I'm using radeon driver. It's part of X.Org X server &#8211; AMD/ATI display driver wrapper from xserver-xorg-video-ati, so I'm not using fglrx. I could *not* find either Richland, 8550G or 8550M/8670M listed here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).

---

### Post by mörgæs on 2016-05-26
> **ubuser4 said:**
> Does 16.04 support my GPU?

Most likely yes but you tell me. Try a live boot.

---

### Post by ubuser4 on 2016-05-27
The disconnection happened again. Here's the log about it. I excluded a few messages about the shutdown:
```
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC kernel: [  150.125769] cdc_ether 3-1:1.0 eth1: unregister 'cdc_ether' usb-0000:00:12.2-1, CDC Ethernet Device
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC dhclient: receive_packet failed on eth1: Network is down
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <warn> (4) failed to find interface name for index
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <warn> (eth1): failed to update IPv6 config in response to Router Advertisement.
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <info> (eth1): device state change: activated -> failed (reason 'config-failed') [100 120 4]
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC whoopsie[1186]: offline
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <info> NetworkManager state is now DISCONNECTED
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <warn> Activation (eth1) failed for connection 'Kiinteä yhteys 2'
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:12.2/usb3/3-1/3-1:1.0/net/eth1, iface: eth1)
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <info> (eth1): device state change: failed -> unmanaged (reason 'removed') [120 10 36]
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <info> (eth1): deactivating device (reason 'removed') [36]
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC dbus[865]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC dbus[865]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC kernel: [  150.263527] usb 3-1: reset high-speed USB device number 3 using ehci-pci
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1181
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/disable_ipv6': (2) Tiedostoa tai hakemistoa ei ole
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/accept_ra': (2) Tiedostoa tai hakemistoa ei ole
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/use_tempaddr': (2) Tiedostoa tai hakemistoa ei ole
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <warn> (4) failed to find interface name for index
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <warn> (4) failed to find interface name for index
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <info> Writing DNS information to /sbin/resolvconf
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC dnsmasq[1398]: setting upstream servers from DBus
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <info> (eth1): cleaning up...
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <warn> (4) failed to find interface name for index
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <error> [1464350855.677122] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <info> NetworkManager state is now CONNECTED_GLOBAL
May 27 15:07:35 u-HP-Pavilion-17-Notebook-PC NetworkManager[1031]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 27 15:07:40 u-HP-Pavilion-17-Notebook-PC kernel: [  155.380553] usb 3-1: device descriptor read/64, error -110
```

I'm still using 14.04.

I'll try a live boot of 16.04 next week if I can and maybe also do a fresh install of it. I'll post results here when I'm done.

---

### Post by ubuser4 on 2016-06-04
The week is almost over, but I haven't had time to even test 16.04 and I don't know when I will.

However, I got an extension cable for the dongle and have been using it for a few days. I did that because I thought the problem could also be related with there not being enough free space around the device. The internet connection is now slightly faster than before (of course), but moving the dongle farther from the computer didn't solve anything, because another disconnection happened this morning. Unless asked, I'm not posting log messages about that because I don't think they help anyone at this point and they're similar to previous ones.

For now, I'm using the dongle in a different USB port until either the problem occurs again or I get to try 16.04, whichever comes first. I do this as an attempt to see if the port I normally use could be damaged (or otherwise have become incompatible with the dongle?).

---

### Post by ubuser4 on 2016-06-06
I'm still using 14.04, but I thought I could post an update here, because things seem to get more and more bizarre.

Yesterday, when I was downloading a huge file, the download suddenly stopped progressing and I couldn't access any websites. The computer had been on for almost two hours, which is unusual, because connection problems have always happened within the first few minutes. However, I was still connected, according to the network icon and no messages appeared in the logs. There was no crash/freeze. In hindsight, though, I realized that maybe I should have tried to restart Firefox.

Today, a more usual disconnection happened, and this time the computer crashed/froze, which has happened only once before this time after installing 14.04, and that was when I unplugged and replugged the modem. This time I didn't do it. Here's the var/log/syslog about the disconnection and the crash:
```
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093713] ------------[ cut here ]------------
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093751] WARNING: CPU: 0 PID: 0 at /build/linux-lts-wily-JUyKGw/linux-lts-wily-4.2.0/net/sched/sch_generic.c:303 dev_watchdog+0x23b/0x250()
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093755] NETDEV WATCHDOG: eth1 (cdc_ether): transmit queue 0 timed out
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093758] Modules linked in: cdc_ether usbnet bnep rfcomm bluetooth binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter hp_wmi ip_tables x_tables sparse_keymap rtsx_pci_ms memstick kvm crct10dif_pclmul crc32_pclmul snd_hda_codec_realtek snd_hda_codec_generic aesni_intel aes_x86_64 snd_hda_codec_hdmi lrw gf128mul glue_helper snd_hda_intel ablk_helper cryptd snd_hda_codec snd_hda_core snd_hwdep joydev snd_seq_midi snd_seq_midi_event arc4 input_leds serio_raw rt2800pci snd_pcm rt2800mmio k10temp rt2800lib rt2x00pci rt2x00mmio snd_rawmidi i2c_piix4 rt2x00lib mac80211 snd_seq snd_seq_device cfg80211 snd_timer snd eeprom_93cx6 crc_ccitt shpchp parport_pc soundcore ppdev lp parport hp_accel lis3lv02d input_polldev hp_wireless mac_hid hid_generic usbhid hid uas usb_storage amdkfd rtsx_pci_sdmmc amd_iommu_v2 radeon i2c_algo_bit ttm psmouse drm_kms_helper r8169 rtsx_pci mii ahci drm libahci wmi video
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093899] CPU: 0 PID: 0 Comm: swapper/0 Not tainted 4.2.0-36-generic #42~14.04.1-Ubuntu
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093913] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093924]  0000000000000000 ffff88021ec03d68 ffffffff817bc0e7 ffff88021ec03db8
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093929]  ffffffff81b4abf0 ffff88021ec03da8 ffffffff81079b3a ffff88021ec1a900
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093934]  0000000000000000 ffff880212d90000 0000000000000001 ffff8800aceed080
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093946] Call Trace:
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093949]  <IRQ>  [<ffffffff817bc0e7>] dump_stack+0x63/0x81
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093972]  [<ffffffff81079b3a>] warn_slowpath_common+0x8a/0xc0
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093981]  [<ffffffff81079bb6>] warn_slowpath_fmt+0x46/0x50
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.093988]  [<ffffffff816dbcfb>] dev_watchdog+0x23b/0x250
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094000]  [<ffffffff816dbac0>] ? dev_deactivate_queue.constprop.34+0x70/0x70
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094008]  [<ffffffff810e18d9>] call_timer_fn+0x39/0x130
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094013]  [<ffffffff816dbac0>] ? dev_deactivate_queue.constprop.34+0x70/0x70
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094024]  [<ffffffff810e31be>] run_timer_softirq+0x20e/0x2c0
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094029]  [<ffffffff8107dced>] __do_softirq+0xdd/0x290
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094039]  [<ffffffff8107e0d5>] irq_exit+0x95/0xa0
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094043]  [<ffffffff817c6286>] smp_apic_timer_interrupt+0x46/0x60
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094056]  [<ffffffff817c441b>] apic_timer_interrupt+0x6b/0x70
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094058]  <EOI>  [<ffffffff8165ba68>] ? cpuidle_enter_state+0xd8/0x250
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094077]  [<ffffffff8165ba44>] ? cpuidle_enter_state+0xb4/0x250
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094085]  [<ffffffff8165bc17>] cpuidle_enter+0x17/0x20
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094092]  [<ffffffff810ba5eb>] call_cpuidle+0x3b/0x70
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094097]  [<ffffffff8165bbf3>] ? cpuidle_select+0x13/0x20
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094107]  [<ffffffff810ba8c7>] cpu_startup_entry+0x2a7/0x370
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094113]  [<ffffffff817abfbc>] rest_init+0x7c/0x80
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094124]  [<ffffffff81d5211f>] start_kernel+0x4b0/0x4bd
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094128]  [<ffffffff81d51a54>] ? set_init_arg+0x57/0x57
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094132]  [<ffffffff81d51120>] ? early_idt_handler_array+0x120/0x120
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094136]  [<ffffffff81d515ee>] x86_64_start_reservations+0x2a/0x2c
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094139]  [<ffffffff81d5172d>] x86_64_start_kernel+0x13d/0x14c
Jun  6 10:31:48 u-HP-Pavilion-17-Notebook-PC kernel: [  280.094142] ---[ end trace 2a098d262f03fc1e ]---
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC dhclient: receive_packet failed on eth1: Network is down
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <warn> (4) failed to find interface name for index
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <warn> (eth1): failed to update IPv6 config in response to Router Advertisement.
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <info> (eth1): device state change: activated -> failed (reason 'config-failed') [100 120 4]
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC kernel: [  296.190358] cdc_ether 1-2:1.0 eth1: unregister 'cdc_ether' usb-0000:00:10.0-2, CDC Ethernet Device
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <info> NetworkManager state is now DISCONNECTED
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <warn> Activation (eth1) failed for connection 'Kiinteä yhteys 1'
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/net/eth1, iface: eth1)
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <info> (eth1): device state change: failed -> unmanaged (reason 'removed') [120 10 36]
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <info> (eth1): deactivating device (reason 'removed') [36]
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC dbus[919]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC dbus[919]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun  6 10:32:04 u-HP-Pavilion-17-Notebook-PC kernel: [  296.327120] usb 1-2: reset high-speed USB device number 3 using xhci_hcd
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1286
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/disable_ipv6': (2) Tiedostoa tai hakemistoa ei ole
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/accept_ra': (2) Tiedostoa tai hakemistoa ei ole
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/use_tempaddr': (2) Tiedostoa tai hakemistoa ei ole
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <warn> (4) failed to find interface name for index
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <warn> (4) failed to find interface name for index
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <info> Writing DNS information to /sbin/resolvconf
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC dnsmasq[1324]: setting upstream servers from DBus
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <info> (eth1): cleaning up...
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <warn> (4) failed to find interface name for index
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <error> [1465198325.136750] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jun  6 10:32:05 u-HP-Pavilion-17-Notebook-PC NetworkManager[1087]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  6 10:32:10 u-HP-Pavilion-17-Notebook-PC kernel: [  301.440804] usb 1-2: device descriptor read/64, error -110
Jun  6 10:32:25 u-HP-Pavilion-17-Notebook-PC kernel: [  316.664502] usb 1-2: device descriptor read/64, error -110
Jun  6 10:32:25 u-HP-Pavilion-17-Notebook-PC kernel: [  316.880548] usb 1-2: reset high-speed USB device number 3 using xhci_hcd
Jun  6 10:32:25 u-HP-Pavilion-17-Notebook-PC kernel: [  316.992665] usb 1-2: device descriptor read/64, error -71
Jun  6 10:32:25 u-HP-Pavilion-17-Notebook-PC kernel: [  317.208620] usb 1-2: device descriptor read/64, error -71
Jun  6 10:32:26 u-HP-Pavilion-17-Notebook-PC kernel: [  317.424923] usb 1-2: reset high-speed USB device number 3 using xhci_hcd
Jun  6 10:32:26 u-HP-Pavilion-17-Notebook-PC kernel: [  317.425578] usb 1-2: Device not responding to setup address.
Jun  6 10:32:26 u-HP-Pavilion-17-Notebook-PC kernel: [  317.629199] usb 1-2: Device not responding to setup address.
Jun  6 10:32:26 u-HP-Pavilion-17-Notebook-PC kernel: [  317.832985] usb 1-2: device not accepting address 3, error -71
Jun  6 10:32:26 u-HP-Pavilion-17-Notebook-PC kernel: [  317.945191] usb 1-2: reset high-speed USB device number 3 using xhci_hcd
Jun  6 10:32:26 u-HP-Pavilion-17-Notebook-PC kernel: [  317.945828] usb 1-2: Device not responding to setup address.
Jun  6 10:32:26 u-HP-Pavilion-17-Notebook-PC kernel: [  318.149746] usb 1-2: Device not responding to setup address.
Jun  6 10:32:27 u-HP-Pavilion-17-Notebook-PC kernel: [  318.353211] usb 1-2: device not accepting address 3, error -71
Jun  6 10:32:27 u-HP-Pavilion-17-Notebook-PC kernel: [  318.353548] usb 1-2: USB disconnect, device number 3
Jun  6 10:32:27 u-HP-Pavilion-17-Notebook-PC kernel: [  318.353586] xhci_hcd 0000:00:10.0: ERROR: unexpected command completion code 0x13.
Jun  6 10:32:27 u-HP-Pavilion-17-Notebook-PC kernel: [  318.353595] usb 1-2: Not enough bandwidth for altsetting 0
Jun  6 10:32:27 u-HP-Pavilion-17-Notebook-PC kernel: [  318.353621] cdc_ether: probe of 1-2:1.0 failed with error -22
Jun  6 10:32:27 u-HP-Pavilion-17-Notebook-PC kernel: [  318.485195] usb 1-2: new high-speed USB device number 4 using xhci_hcd
Jun  6 10:32:27 u-HP-Pavilion-17-Notebook-PC kernel: [  318.597336] usb 1-2: device descriptor read/64, error -71
Jun  6 10:32:27 u-HP-Pavilion-17-Notebook-PC kernel: [  318.813486] usb 1-2: device descriptor read/64, error -71
Jun  6 10:32:27 u-HP-Pavilion-17-Notebook-PC kernel: [  319.029457] usb 1-2: new high-speed USB device number 5 using xhci_hcd
Jun  6 10:32:27 u-HP-Pavilion-17-Notebook-PC kernel: [  319.141578] usb 1-2: device descriptor read/64, error -71
Jun  6 10:32:28 u-HP-Pavilion-17-Notebook-PC kernel: [  319.357720] usb 1-2: device descriptor read/64, error -71
Jun  6 10:32:28 u-HP-Pavilion-17-Notebook-PC kernel: [  319.573762] usb 1-2: new high-speed USB device number 6 using xhci_hcd
Jun  6 10:32:28 u-HP-Pavilion-17-Notebook-PC kernel: [  319.574158] usb 1-2: Device not responding to setup address.
Jun  6 10:32:28 u-HP-Pavilion-17-Notebook-PC kernel: [  319.778013] usb 1-2: Device not responding to setup address.
Jun  6 10:32:28 u-HP-Pavilion-17-Notebook-PC kernel: [  319.981951] usb 1-2: device not accepting address 6, error -71
Jun  6 10:32:28 u-HP-Pavilion-17-Notebook-PC kernel: [  320.094027] usb 1-2: new high-speed USB device number 7 using xhci_hcd
Jun  6 10:32:28 u-HP-Pavilion-17-Notebook-PC kernel: [  320.094222] usb 1-2: Device not responding to setup address.
Jun  6 10:32:28 u-HP-Pavilion-17-Notebook-PC kernel: [  320.298288] usb 1-2: Device not responding to setup address.
Jun  6 10:32:29 u-HP-Pavilion-17-Notebook-PC kernel: [  320.502253] usb 1-2: device not accepting address 7, error -71
Jun  6 10:32:29 u-HP-Pavilion-17-Notebook-PC kernel: [  320.502322] usb usb1-port2: unable to enumerate USB device
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.247334] BUG: unable to handle kernel paging request at ffffeb88001fb080
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.247394] IP: [<ffffffff811cfeea>] kfree+0x5a/0x150
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.247435] PGD 0 
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.247452] Oops: 0000 [#1] SMP 
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.247477] Modules linked in: cdc_ether usbnet bnep rfcomm bluetooth binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter hp_wmi ip_tables x_tables sparse_keymap rtsx_pci_ms memstick kvm crct10dif_pclmul crc32_pclmul snd_hda_codec_realtek snd_hda_codec_generic aesni_intel aes_x86_64 snd_hda_codec_hdmi lrw gf128mul glue_helper snd_hda_intel ablk_helper cryptd snd_hda_codec snd_hda_core snd_hwdep joydev snd_seq_midi snd_seq_midi_event arc4 input_leds serio_raw rt2800pci snd_pcm rt2800mmio k10temp rt2800lib rt2x00pci rt2x00mmio snd_rawmidi i2c_piix4 rt2x00lib mac80211 snd_seq snd_seq_device cfg80211 snd_timer snd eeprom_93cx6 crc_ccitt shpchp parport_pc soundcore ppdev lp parport hp_accel lis3lv02d input_polldev hp_wireless mac_hid hid_generic usbhid hid uas usb_storage amdkfd rtsx_pci_sdmmc amd_iommu_v2 radeon i2c_algo_bit ttm psmouse drm_kms_helper r8169 rtsx_pci mii ahci drm libahci wmi video
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248364] CPU: 1 PID: 1307 Comm: Xorg Tainted: G        W       4.2.0-36-generic #42~14.04.1-Ubuntu
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248424] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248481] task: ffff880214b52940 ti: ffff880214a88000 task.ti: ffff880214a88000
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248529] RIP: 0010:[<ffffffff811cfeea>]  [<ffffffff811cfeea>] kfree+0x5a/0x150
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248625] RSP: 0018:ffff880214a8b8b8  EFLAGS: 00010282
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248663] RAX: 00000188001fb080 RBX: ffffea0007ec2a40 RCX: 0000000000000000
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248709] RDX: 000077ff80000000 RSI: ffffea0007ec2a40 RDI: ffffea0007ec2a40
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248755] RBP: ffff880214a8b8d8 R08: 0000000000000000 R09: ffff8801fde72000
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248800] R10: ffffeb88001fb080 R11: ffffffff81ab1bc0 R12: 0000000000000003
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248845] R13: ffffffffc0152108 R14: ffffea0007ec2a40 R15: ffff880211ce5b40
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248891] FS:  00007fa4c27e78c0(0000) GS:ffff88021ec80000(0000) knlGS:0000000000000000
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248943] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.248980] CR2: ffffeb88001fb080 CR3: 0000000211fb8000 CR4: 00000000000406e0
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249026] Stack:
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249040]  0000000000000003 0000000000000004 0000000000000003 ffff8802128c98c0
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249091]  ffff880214a8b9b8 ffffffffc0152108 ffff880214b52940 ffff880211ce5ba4
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249143]  ffff880215ffe098 ffff880211ce5b68 ffff88009b9ca4e0 ffff880211c3ac00
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249194] Call Trace:
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249226]  [<ffffffffc0152108>] ttm_dma_populate+0x618/0x900 [ttm]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249270]  [<ffffffff811d17cc>] ? __kmalloc+0x22c/0x280
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249311]  [<ffffffffc01492b0>] ? ttm_dma_tt_init+0xb0/0xd0 [ttm]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249358]  [<ffffffffc01492b0>] ? ttm_dma_tt_init+0xb0/0xd0 [ttm]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249439]  [<ffffffffc018f6a9>] radeon_ttm_tt_populate+0x199/0x290 [radeon]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249490]  [<ffffffffc0148ca4>] ttm_tt_bind+0x34/0x60 [ttm]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249534]  [<ffffffffc014b038>] ttm_bo_handle_move_mem+0x538/0x590 [ttm]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249585]  [<ffffffffc014b726>] ? ttm_bo_mem_space+0x166/0x320 [ttm]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249633]  [<ffffffffc014bd52>] ttm_bo_validate+0x1c2/0x1d0 [ttm]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249705]  [<ffffffffc00487bb>] ? drm_vma_offset_add+0xab/0xc0 [drm]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249753]  [<ffffffffc014bf8d>] ttm_bo_init+0x22d/0x440 [ttm]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249819]  [<ffffffffc01908ff>] radeon_bo_create+0x19f/0x260 [radeon]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.249888]  [<ffffffffc0190450>] ? radeon_update_memory_usage.isra.3+0x60/0x60 [radeon]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.252161]  [<ffffffffc01a3a80>] radeon_gem_object_create+0xc0/0x1a0 [radeon]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.254891]  [<ffffffffc01a3f0e>] radeon_gem_create_ioctl+0x5e/0x150 [radeon]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.257674]  [<ffffffffc002f723>] drm_ioctl+0x363/0x680 [drm]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.260414]  [<ffffffffc01a3eb0>] ? radeon_gem_pwrite_ioctl+0x30/0x30 [radeon]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.263217]  [<ffffffffc017204b>] radeon_drm_ioctl+0x4b/0x80 [radeon]
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.265994]  [<ffffffff8120155d>] do_vfs_ioctl+0x2cd/0x4b0
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.268773]  [<ffffffff81066296>] ? __do_page_fault+0x1b6/0x430
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.271561]  [<ffffffff811ade7b>] ? SyS_mmap_pgoff+0xeb/0x260
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.274350]  [<ffffffff812017b9>] SyS_ioctl+0x79/0x90
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.277108]  [<ffffffff817c35b2>] entry_SYSCALL_64_fastpath+0x16/0x75
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.279854] Code: 00 00 00 80 ff 77 00 00 49 ba 00 00 00 00 00 ea ff ff 48 01 d8 48 0f 42 15 34 41 a4 00 48 01 d0 48 c1 e8 0c 48 c1 e0 06 49 01 c2 <49> 8b 02 f6 c4 80 0f 85 d6 00 00 00 49 8b 02 a8 80 0f 84 a7 00 
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.285830] RIP  [<ffffffff811cfeea>] kfree+0x5a/0x150
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.288806]  RSP <ffff880214a8b8b8>
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.291697] CR2: ffffeb88001fb080
Jun  6 10:33:13 u-HP-Pavilion-17-Notebook-PC kernel: [  365.308885] ---[ end trace 2a098d262f03fc1f ]---
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.720611] general protection fault: 0000 [#2] SMP 
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.723510] Modules linked in: cdc_ether usbnet bnep rfcomm bluetooth binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter hp_wmi ip_tables x_tables sparse_keymap rtsx_pci_ms memstick kvm crct10dif_pclmul crc32_pclmul snd_hda_codec_realtek snd_hda_codec_generic aesni_intel aes_x86_64 snd_hda_codec_hdmi lrw gf128mul glue_helper snd_hda_intel ablk_helper cryptd snd_hda_codec snd_hda_core snd_hwdep joydev snd_seq_midi snd_seq_midi_event arc4 input_leds serio_raw rt2800pci snd_pcm rt2800mmio k10temp rt2800lib rt2x00pci rt2x00mmio snd_rawmidi i2c_piix4 rt2x00lib mac80211 snd_seq snd_seq_device cfg80211 snd_timer snd eeprom_93cx6 crc_ccitt shpchp parport_pc soundcore ppdev lp parport hp_accel lis3lv02d input_polldev hp_wireless mac_hid hid_generic usbhid hid uas usb_storage amdkfd rtsx_pci_sdmmc amd_iommu_v2 radeon i2c_algo_bit ttm psmouse drm_kms_helper r8169 rtsx_pci mii ahci drm libahci wmi video
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.745231] CPU: 1 PID: 2455 Comm: psensor Tainted: G      D W       4.2.0-36-generic #42~14.04.1-Ubuntu
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.748195] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.751134] task: ffff8802158b2940 ti: ffff88009b87c000 task.ti: ffff88009b87c000
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.754064] RIP: 0010:[<ffffffff811d0cca>]  [<ffffffff811d0cca>] kmem_cache_alloc_trace+0x7a/0x240
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.757018] RSP: 0018:ffff88009b87fc18  EFLAGS: 00010282
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.759946] RAX: 0000000000000000 RBX: 00000000000080d0 RCX: 00000000000119ab
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.762883] RDX: 00000000000119aa RSI: 00000000000080d0 RDI: ffff880216c01c00
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.765802] RBP: ffff88009b87fc68 R08: 0000000000019a60 R09: ffff880216c01c00
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.768717] R10: ffffffff8135091b R11: ffff880216c01700 R12: 00000000000080d0
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.771635] R13: ffff88009b87fef4 R14: 02ffff0000000000 R15: ffff880216c01c00
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.774556] FS:  00007f988899e700(0000) GS:ffff88021ec80000(0000) knlGS:0000000000000000
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.777501] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.780422] CR2: ffffeb88001fb080 CR3: 000000009b8cb000 CR4: 00000000000406e0
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.783353] Stack:
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.786248]  ffff88009b87fc38 ffff880216c01c00 ffffffff8135091b 0000000000000018
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.789190]  ffff88009b87fc88 ffff880216c8d030 ffff880210e22600 ffff88009b87fef4
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.792113]  ffff88009b87fdc8 00000000000001b6 ffff88009b87fc98 ffffffff8135091b
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.795032] Call Trace:
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.797937]  [<ffffffff8135091b>] ? apparmor_file_alloc_security+0x5b/0x160
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.800864]  [<ffffffff8135091b>] apparmor_file_alloc_security+0x5b/0x160
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.803787]  [<ffffffff811f004c>] ? get_empty_filp+0x5c/0x1a0
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.806704]  [<ffffffff81311ff3>] security_file_alloc+0x33/0x50
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.809621]  [<ffffffff811f0083>] get_empty_filp+0x93/0x1a0
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.812560]  [<ffffffff811fc06e>] path_openat+0x2e/0x1360
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.815491]  [<ffffffff810af16f>] ? put_prev_entity+0x2f/0x4a0
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.818415]  [<ffffffff8101eec9>] ? sched_clock+0x9/0x10
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.821331]  [<ffffffff811fe46a>] do_filp_open+0x7a/0xd0
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.824242]  [<ffffffff810e4b5a>] ? hrtimer_try_to_cancel+0x1a/0x110
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.827155]  [<ffffffff811fd57f>] ? getname_flags+0x4f/0x1f0
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.830062]  [<ffffffff8120b606>] ? __alloc_fd+0x46/0x110
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.832959]  [<ffffffff811ed919>] do_sys_open+0x129/0x270
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.835848]  [<ffffffff817c2874>] ? do_nanosleep+0x64/0x100
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.838724]  [<ffffffff811eda7e>] SyS_open+0x1e/0x20
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.841578]  [<ffffffff817c35b2>] entry_SYSCALL_64_fastpath+0x16/0x75
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.844441] Code: 4c 03 05 c2 94 e3 7e 4d 8b 30 49 8b 40 10 4d 85 f6 0f 84 5b 01 00 00 48 85 c0 0f 84 52 01 00 00 49 63 47 20 48 8d 4a 01 4d 8b 07 <49> 8b 1c 06 4c 89 f0 65 49 0f c7 08 0f 94 c0 84 c0 74 b9 49 63 
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.850579] RIP  [<ffffffff811d0cca>] kmem_cache_alloc_trace+0x7a/0x240
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.853612]  RSP <ffff88009b87fc18>
Jun  6 10:33:14 u-HP-Pavilion-17-Notebook-PC kernel: [  365.856653] ---[ end trace 2a098d262f03fc20 ]---
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.172254] general protection fault: 0000 [#3] SMP 
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.175304] Modules linked in: cdc_ether usbnet bnep rfcomm bluetooth binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter hp_wmi ip_tables x_tables sparse_keymap rtsx_pci_ms memstick kvm crct10dif_pclmul crc32_pclmul snd_hda_codec_realtek snd_hda_codec_generic aesni_intel aes_x86_64 snd_hda_codec_hdmi lrw gf128mul glue_helper snd_hda_intel ablk_helper cryptd snd_hda_codec snd_hda_core snd_hwdep joydev snd_seq_midi snd_seq_midi_event arc4 input_leds serio_raw rt2800pci snd_pcm rt2800mmio k10temp rt2800lib rt2x00pci rt2x00mmio snd_rawmidi i2c_piix4 rt2x00lib mac80211 snd_seq snd_seq_device cfg80211 snd_timer snd eeprom_93cx6 crc_ccitt shpchp parport_pc soundcore ppdev lp parport hp_accel lis3lv02d input_polldev hp_wireless mac_hid hid_generic usbhid hid uas usb_storage amdkfd rtsx_pci_sdmmc amd_iommu_v2 radeon i2c_algo_bit ttm psmouse drm_kms_helper r8169 rtsx_pci mii ahci drm libahci wmi video
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.199327] CPU: 1 PID: 2633 Comm: pool Tainted: G      D W       4.2.0-36-generic #42~14.04.1-Ubuntu
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.202946] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.206590] task: ffff8800adb18000 ti: ffff8801fc470000 task.ti: ffff8801fc470000
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.210164] RIP: 0010:[<ffffffff811d0cca>]  [<ffffffff811d0cca>] kmem_cache_alloc_trace+0x7a/0x240
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.213691] RSP: 0018:ffff8801fc473c18  EFLAGS: 00010282
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.217115] RAX: 0000000000000000 RBX: 00000000000080d0 RCX: 00000000000119ab
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.220466] RDX: 00000000000119aa RSI: 00000000000080d0 RDI: ffff880216c01c00
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.223709] RBP: ffff8801fc473c68 R08: 0000000000019a60 R09: ffff880216c01c00
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.226855] R10: ffffffff8135091b R11: 0000000000000000 R12: 00000000000080d0
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.229906] R13: ffff8801fc473ef4 R14: 02ffff0000000000 R15: ffff880216c01c00
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.232906] FS:  00007f21bd3ed700(0000) GS:ffff88021ec80000(0000) knlGS:0000000000000000
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.235902] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.238867] CR2: 00007f21b00010b8 CR3: 0000000212d01000 CR4: 00000000000406e0
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.241825] Stack:
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.244736]  ffff880215e72940 ffff880216c01c00 ffffffff8135091b 0000000000000018
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.247704]  ffff8801fc473d80 ffff880216c8d030 ffff880210e22000 ffff8801fc473ef4
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.250680]  ffff8801fc473dc8 000000000000f800 ffff8801fc473c98 ffffffff8135091b
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.253661] Call Trace:
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.256622]  [<ffffffff8135091b>] ? apparmor_file_alloc_security+0x5b/0x160
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.259615]  [<ffffffff8135091b>] apparmor_file_alloc_security+0x5b/0x160
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.262591]  [<ffffffff811f004c>] ? get_empty_filp+0x5c/0x1a0
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.265549]  [<ffffffff81311ff3>] security_file_alloc+0x33/0x50
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.268491]  [<ffffffff811f0083>] get_empty_filp+0x93/0x1a0
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.271412]  [<ffffffff810f4d5d>] ? futex_wait+0x1ad/0x280
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.274311]  [<ffffffff811fc06e>] path_openat+0x2e/0x1360
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.277206]  [<ffffffff811a6d8c>] ? do_wp_page+0x1dc/0x540
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.280081]  [<ffffffff811fe46a>] do_filp_open+0x7a/0xd0
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.282938]  [<ffffffff811a94f7>] ? handle_mm_fault+0xb77/0x11f0
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.285841]  [<ffffffff811fd57f>] ? getname_flags+0x4f/0x1f0
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.288681]  [<ffffffff8120b606>] ? __alloc_fd+0x46/0x110
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.291504]  [<ffffffff811ed919>] do_sys_open+0x129/0x270
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.294322]  [<ffffffff810f7441>] ? SyS_futex+0x71/0x150
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.297135]  [<ffffffff811eda7e>] SyS_open+0x1e/0x20
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.299950]  [<ffffffff817c35b2>] entry_SYSCALL_64_fastpath+0x16/0x75
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.302774] Code: 4c 03 05 c2 94 e3 7e 4d 8b 30 49 8b 40 10 4d 85 f6 0f 84 5b 01 00 00 48 85 c0 0f 84 52 01 00 00 49 63 47 20 48 8d 4a 01 4d 8b 07 <49> 8b 1c 06 4c 89 f0 65 49 0f c7 08 0f 94 c0 84 c0 74 b9 49 63 
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.308796] RIP  [<ffffffff811d0cca>] kmem_cache_alloc_trace+0x7a/0x240
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.311810]  RSP <ffff8801fc473c18>
Jun  6 10:33:17 u-HP-Pavilion-17-Notebook-PC kernel: [  369.314918] ---[ end trace 2a098d262f03fc21 ]---
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.344044] general protection fault: 0000 [#4] SMP 
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.347104] Modules linked in: cdc_ether usbnet bnep rfcomm bluetooth binfmt_misc nls_iso8859_1 uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter hp_wmi ip_tables x_tables sparse_keymap rtsx_pci_ms memstick kvm crct10dif_pclmul crc32_pclmul snd_hda_codec_realtek snd_hda_codec_generic aesni_intel aes_x86_64 snd_hda_codec_hdmi lrw gf128mul glue_helper snd_hda_intel ablk_helper cryptd snd_hda_codec snd_hda_core snd_hwdep joydev snd_seq_midi snd_seq_midi_event arc4 input_leds serio_raw rt2800pci snd_pcm rt2800mmio k10temp rt2800lib rt2x00pci rt2x00mmio snd_rawmidi i2c_piix4 rt2x00lib mac80211 snd_seq snd_seq_device cfg80211 snd_timer snd eeprom_93cx6 crc_ccitt shpchp parport_pc soundcore ppdev lp parport hp_accel lis3lv02d input_polldev hp_wireless mac_hid hid_generic usbhid hid uas usb_storage amdkfd rtsx_pci_sdmmc amd_iommu_v2 radeon i2c_algo_bit ttm psmouse drm_kms_helper r8169 rtsx_pci mii ahci drm libahci wmi video
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.371393] CPU: 1 PID: 1621 Comm: upowerd Tainted: G      D W       4.2.0-36-generic #42~14.04.1-Ubuntu
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.374993] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.378738] task: ffff880214383700 ti: ffff8800acb20000 task.ti: ffff8800acb20000
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.382285] RIP: 0010:[<ffffffff811d1636>]  [<ffffffff811d1636>] __kmalloc+0x96/0x280
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.385768] RSP: 0018:ffff8800acb23968  EFLAGS: 00010282
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.389152] RAX: 0000000000000000 RBX: 00000000000000d0 RCX: 00000000000119ab
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.392464] RDX: 00000000000119aa RSI: 0000000000000000 RDI: 0000000000000002
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.395665] RBP: ffff8800acb239a8 R08: 0000000000019a60 R09: ffff880216c01c00
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.398772] R10: ffffffff8145144f R11: ffffffff81448042 R12: 00000000000000d0
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.401795] R13: 0000000000000015 R14: 02ffff0000000000 R15: ffff880216c01c00
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.404771] FS:  00007f9789a18840(0000) GS:ffff88021ec80000(0000) knlGS:0000000000000000
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.407740] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.410683] CR2: 00007f21b00010b8 CR3: 00000002139b3000 CR4: 00000000000406e0
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.413621] Stack:
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.416508]  ffffffff8145144f ffff880216c01c00 ffff8800acb23998 0000000000000002
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.419452]  0000000000000004 0000000000000015 ffff8800acb23a64 ffff8800acb23a68
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.422407]  ffff8800acb239d8 ffffffff8145144f ffff8800acb23a64 ffff8801fc748801
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.425371] Call Trace:
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.428315]  [<ffffffff8145144f>] ? acpi_ex_allocate_name_string+0x4b/0xb9
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.431312]  [<ffffffff8145144f>] acpi_ex_allocate_name_string+0x4b/0xb9
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.434288]  [<ffffffff814516c7>] acpi_ex_get_name_string+0x10b/0x1c7
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.437245]  [<ffffffff81449604>] acpi_ds_create_operand+0x54/0x239
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.440185]  [<ffffffff814569a5>] ? acpi_ns_lookup+0x229/0x349
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.443098]  [<ffffffff811d0c25>] ? kmem_cache_alloc+0x1e5/0x210
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.445992]  [<ffffffff814498f4>] acpi_ds_evaluate_name_path+0x4e/0xfa
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.448891]  [<ffffffff81449cd9>] acpi_ds_exec_end_op+0x9b/0x3ee
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.451778]  [<ffffffff8145bc4f>] acpi_ps_parse_loop+0x51d/0x576
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.454644]  [<ffffffff81448042>] ? acpi_ds_call_control_method+0x109/0x190
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.457505]  [<ffffffff8145c707>] acpi_ps_parse_aml+0x99/0x28b
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.460363]  [<ffffffff8145cf5d>] acpi_ps_execute_method+0x1c4/0x272
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.463214]  [<ffffffff814577db>] acpi_ns_evaluate+0x1c4/0x25c
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.466055]  [<ffffffff8145a127>] acpi_evaluate_object+0x126/0x22f
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.468900]  [<ffffffff811ec4eb>] ? do_dentry_open+0x28b/0x320
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.471756]  [<ffffffff8146b9e5>] acpi_battery_get_state+0x6a/0x1a0
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.474613]  [<ffffffff8146bbed>] acpi_battery_get_property+0x36/0x307
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.477468]  [<ffffffff81621239>] power_supply_get_property+0x19/0x30
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.480321]  [<ffffffff81621fd9>] power_supply_show_property+0x49/0x1c0
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.483173]  [<ffffffff814f6c00>] dev_attr_show+0x20/0x50
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.486020]  [<ffffffff817c1886>] ? mutex_lock+0x16/0x37
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.488933]  [<ffffffff81267d22>] sysfs_kf_seq_show+0xc2/0x1a0
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.491786]  [<ffffffff81266573>] kernfs_seq_show+0x23/0x30
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.494640]  [<ffffffff812114a5>] seq_read+0xe5/0x350
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.497490]  [<ffffffff81266d2d>] kernfs_fop_read+0x10d/0x170
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.500345]  [<ffffffff811ee158>] __vfs_read+0x18/0x40
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.503111]  [<ffffffff811ee736>] vfs_read+0x86/0x130
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.505790]  [<ffffffff811ef556>] SyS_read+0x46/0xa0
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.508431]  [<ffffffff817c35b2>] entry_SYSCALL_64_fastpath+0x16/0x75
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.511071] Code: 4c 03 05 56 8b e3 7e 4d 8b 30 49 8b 40 10 4d 85 f6 0f 84 64 01 00 00 48 85 c0 0f 84 5b 01 00 00 49 63 47 20 48 8d 4a 01 4d 8b 07 <49> 8b 1c 06 4c 89 f0 65 49 0f c7 08 0f 94 c0 84 c0 74 b9 49 63 
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.516614] RIP  [<ffffffff811d1636>] __kmalloc+0x96/0x280
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.519223]  RSP <ffff8800acb23968>
Jun  6 10:33:19 u-HP-Pavilion-17-Notebook-PC kernel: [  370.521812] ---[ end trace 2a098d262f03fc22 ]---
Jun  6 10:35:12 u-HP-Pavilion-17-Notebook-PC rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="824" x-info="http://www.rsyslog.com"] start
Jun  6 10:35:12 u-HP-Pavilion-17-Notebook-PC rsyslogd: rsyslogd's groupid changed to 104
Jun  6 10:35:12 u-HP-Pavilion-17-Notebook-PC rsyslogd: rsyslogd's userid changed to 101
```

At least I learned that the problem isn't caused by a faulty USB port (unless they all are somehow damaged).

---

### Post by ubuser4 on 2016-06-08
I finally got around to trying a live boot of 16.04. In fact, this post was sent during a live session. As for the GPU, the "radeon" driver is in use and I haven't had any GPU problems. However, the uptime is only about 40 minutes right now.

I still have a couple of questions.
1. The syslog of this live session has many variants of this message related to ureadahead:
```
Error retrieving chunk extents: Operation not supported
```
Is this normal during a live boot or is there something wrong with my computer?
2. Maybe I should have asked this earlier because this message already appeared in 14.04 and maybe 12.04. What does the following message mean? It's obviously related to networking, but I don't know more.
```
cdc_ether 1-1:1.0 enx0c5b8f279a64: kevent 12 may have been dropped
```

I might try to install 16.04 later but maybe not today.

---

### Post by ubuser4 on 2016-06-08
Is the web interface of the dongle supposed to open automatically on Ubuntu? It happened to me only once when I still used 12.04. That was after my problems started and shortly before I moved on to 14.04.

---

### Post by ubuser4 on 2016-06-09
I updated the first post a little, and by the way, the problem occurred again earlier today.

---

### Post by ubuser4 on 2016-06-16
**I finally made a fresh install of 16.04.** On June 11, when I still used 14.04, there were two disconnections. One of them happened about 30 minutes after using the internet, which had probably happened only once before (see post #22), except now log messages appeared. This made me lean more towards the idea of hardware issues. Therefore, I also did the following:
**- got a new dongle, similar to the other one** (Huawei E3372h-153)
[B]- replaced the SIM card
[/B]I plugged the dongle in after logging in and waiting for 10-15 minutes. I used the same extension cable and port as with the previous device.
Here are related /var/log/syslog messages from when I plugged in the new dongle:
```
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC kernel: [ 1694.097868] usb 1-1: new high-speed USB device number 2 using ehci-pci
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC kernel: [ 1694.231138] usb 1-1: New USB device found, idVendor=12d1, idProduct=1f01
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC kernel: [ 1694.231147] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC kernel: [ 1694.231152] usb 1-1: Product: HUAWEI_MOBILE
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC kernel: [ 1694.231155] usb 1-1: Manufacturer: HUAWEI_MOBILE
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC kernel: [ 1694.231159] usb 1-1: SerialNumber: 0123456789ABCDEF
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC mtp-probe: checking bus 1, device 2: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1"
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC mtp-probe: bus: 1, device: 2 was not an MTP device
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC systemd[1]: Created slice system-usb_modeswitch.slice.
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC systemd[1]: Starting USB_ModeSwitch_1-1:1.0...
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC kernel: [ 1694.762068] usb-storage 1-1:1.0: USB Mass Storage device detected
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC kernel: [ 1694.763899] scsi host4: usb-storage 1-1:1.0
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC kernel: [ 1694.764115] usbcore: registered new interface driver usb-storage
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC usb_modeswitch_dispatcher[2023]: Could not read attribute: No such file or directory
Jun 16 15:52:59 u-HP-Pavilion-17-Notebook-PC kernel: [ 1694.797959] usbcore: registered new interface driver uas
Jun 16 15:52:59 u-HP-Pavilion-17-Notebook-PC kernel: [ 1695.768711] scsi 4:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Jun 16 15:52:59 u-HP-Pavilion-17-Notebook-PC kernel: [ 1695.769393] scsi 4:0:0:1: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
Jun 16 15:52:59 u-HP-Pavilion-17-Notebook-PC kernel: [ 1695.773717] sr 4:0:0:0: [sr1] scsi-1 drive
Jun 16 15:52:59 u-HP-Pavilion-17-Notebook-PC kernel: [ 1695.774221] sr 4:0:0:0: Attached scsi CD-ROM sr1
Jun 16 15:52:59 u-HP-Pavilion-17-Notebook-PC kernel: [ 1695.774412] sr 4:0:0:0: Attached scsi generic sg2 type 5
Jun 16 15:52:59 u-HP-Pavilion-17-Notebook-PC kernel: [ 1695.774914] sd 4:0:0:1: Attached scsi generic sg3 type 0
Jun 16 15:53:00 u-HP-Pavilion-17-Notebook-PC kernel: [ 1695.785645] sd 4:0:0:1: [sdb] Attached SCSI removable disk
Jun 16 15:52:58 u-HP-Pavilion-17-Notebook-PC usb_modeswitch_dispatcher[2023]: message repeated 2 times: [ Could not read attribute: No such file or directory]
Jun 16 15:53:00 u-HP-Pavilion-17-Notebook-PC usb_modeswitch: switch device 12d1:1f01 on 001/002
Jun 16 15:53:00 u-HP-Pavilion-17-Notebook-PC kernel: [ 1696.056011] usb 1-1: USB disconnect, device number 2
Jun 16 15:53:00 u-HP-Pavilion-17-Notebook-PC org.freedesktop.fwupd[737]: (fwupd:1636): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Jun 16 15:53:00 u-HP-Pavilion-17-Notebook-PC kernel: [ 1696.633825] usb 1-1: new high-speed USB device number 3 using ehci-pci
Jun 16 15:53:00 u-HP-Pavilion-17-Notebook-PC kernel: [ 1696.767000] usb 1-1: New USB device found, idVendor=12d1, idProduct=14dc
Jun 16 15:53:00 u-HP-Pavilion-17-Notebook-PC kernel: [ 1696.767008] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jun 16 15:53:00 u-HP-Pavilion-17-Notebook-PC kernel: [ 1696.767013] usb 1-1: Product: HUAWEI_MOBILE
Jun 16 15:53:00 u-HP-Pavilion-17-Notebook-PC kernel: [ 1696.767017] usb 1-1: Manufacturer: HUAWEI_MOBILE
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC kernel: [ 1696.894782] usb-storage 1-1:1.2: USB Mass Storage device detected
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC kernel: [ 1696.895049] scsi host5: usb-storage 1-1:1.2
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC mtp-probe: checking bus 1, device 3: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1"
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC mtp-probe: bus: 1, device: 3 was not an MTP device
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <warn>  [1466081581.2947] device (eth0): failed to find device 4 'eth0' with udev
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC kernel: [ 1697.073668] cdc_ether 1-1:1.0 eth0: register 'cdc_ether' at usb-0000:00:12.2-1, CDC Ethernet Device, 0c:5b:8f:27:9a:64
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC kernel: [ 1697.073801] usbcore: registered new interface driver cdc_ether
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081581.2976] manager: (eth0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/3)
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC usb_modeswitch_dispatcher[2023]: Could not read attribute: No such file or directory
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC usb_modeswitch[2023]: usb_modeswitch: switched to 12d1:14dc on 1/3
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC systemd[1]: Started USB_ModeSwitch_1-1:1.0.
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC kernel: [ 1697.096608] cdc_ether 1-1:1.0 enx0c5b8f279a64: renamed from eth0
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081581.3306] device (eth0): interface index 4 renamed iface from 'eth0' to 'enx0c5b8f279a64'
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC kernel: [ 1697.119138] IPv6: ADDRCONF(NETDEV_UP): enx0c5b8f279a64: link is not ready
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC kernel: [ 1697.119429] cdc_ether 1-1:1.0 enx0c5b8f279a64: kevent 12 may have been dropped
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC kernel: [ 1697.119439] cdc_ether 1-1:1.0 enx0c5b8f279a64: kevent 12 may have been dropped
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081581.3389] devices added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/enx0c5b8f279a64, iface: enx0c5b8f279a64)
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081581.3390] device added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/net/enx0c5b8f279a64, iface: enx0c5b8f279a64): no ifupdown configuration found.
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081581.3393] device (enx0c5b8f279a64): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081581.3401] device (enx0c5b8f279a64): link connected
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081581.3427] keyfile: add connection in-memory (a42e38f8-cc26-4085-b970-e0ae5093f685,"Kiinteä yhteys 2")
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081581.3436] settings: (enx0c5b8f279a64): created default wired connection 'Kiinteä yhteys 2'
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081581.3488] device (enx0c5b8f279a64): state change: unavailable -> disconnected (reason 'none') [20 30 0]
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC kernel: [ 1697.129077] cdc_ether 1-1:1.0 enx0c5b8f279a64: kevent 11 may have been dropped
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081581.3512] policy: auto-activating connection 'Kiinteä yhteys 2'
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081581.3531] device (enx0c5b8f279a64): link disconnected
Jun 16 15:53:01 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081581.3539] device (enx0c5b8f279a64): state change: disconnected -> unavailable (reason 'carrier-changed') [30 20 40]
Jun 16 15:53:02 u-HP-Pavilion-17-Notebook-PC kernel: [ 1697.900834] scsi 5:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
Jun 16 15:53:02 u-HP-Pavilion-17-Notebook-PC kernel: [ 1697.901585] sd 5:0:0:0: Attached scsi generic sg2 type 0
Jun 16 15:53:02 u-HP-Pavilion-17-Notebook-PC kernel: [ 1697.916692] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Jun 16 15:53:03 u-HP-Pavilion-17-Notebook-PC ModemManager[727]: <info>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1': not supported by any plugin
Jun 16 15:53:03 u-HP-Pavilion-17-Notebook-PC gnome-session[1377]: (gnome-software:1549): Gs-WARNING **: failed to get updates: no results to show
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.0536] device (enx0c5b8f279a64): link connected
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.0544] device (enx0c5b8f279a64): state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.0561] policy: auto-activating connection 'Kiinteä yhteys 2'
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC kernel: [ 1701.834224] cdc_ether 1-1:1.0 enx0c5b8f279a64: kevent 12 may have been dropped
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.0582] device (enx0c5b8f279a64): Activation: starting connection 'Kiinteä yhteys 2' (a42e38f8-cc26-4085-b970-e0ae5093f685)
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.0585] device (enx0c5b8f279a64): state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.0588] manager: NetworkManager state is now CONNECTING
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.0604] device (enx0c5b8f279a64): state change: prepare -> config (reason 'none') [40 50 0]
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.0622] device (enx0c5b8f279a64): state change: config -> ip-config (reason 'none') [50 70 0]
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC whoopsie[782]: [15:53:06] offline
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.1185] dhcp4 (enx0c5b8f279a64): activation: beginning transaction (timeout in 45 seconds)
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.1649] dhcp4 (enx0c5b8f279a64): dhclient started with pid 2111
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC dhclient[2111]: DHCPDISCOVER on enx0c5b8f279a64 to 255.255.255.255 port 67 interval 3 (xid=0xa639e310)
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC dhclient[2111]: DHCPREQUEST of 192.168.1.100 on enx0c5b8f279a64 to 255.255.255.255 port 67 (xid=0x10e339a6)
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC dhclient[2111]: DHCPOFFER of 192.168.1.100 from 192.168.1.1
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC dhclient[2111]: DHCPACK of 192.168.1.100 from 192.168.1.1
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.4573]   address 192.168.1.100
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.4574]   plen 24 (255.255.255.0)
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.4574]   gateway 192.168.1.1
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.4575]   server identifier 192.168.1.1
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.4575]   lease time 86400
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: Joining mDNS multicast group on interface enx0c5b8f279a64.IPv4 with address 192.168.1.100.
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.4576]   nameserver '192.168.1.1'
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: New relevant interface enx0c5b8f279a64.IPv4 for mDNS.
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.4576]   nameserver '192.168.1.1'
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: Registering new address record for 192.168.1.100 on enx0c5b8f279a64.IPv4.
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.4576] dhcp4 (enx0c5b8f279a64): state changed unknown -> bound
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.4610] device (enx0c5b8f279a64): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.4621] device (enx0c5b8f279a64): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.4627] device (enx0c5b8f279a64): state change: secondaries -> activated (reason 'none') [90 100 0]
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.4634] manager: NetworkManager state is now CONNECTED_LOCAL
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC dhclient[2111]: bound to 192.168.1.100 -- renewal in 33144 seconds.
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC whoopsie[782]: [15:53:06] Cannot reach: https://daisy.ubuntu.com
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.6326] manager: NetworkManager state is now CONNECTED_GLOBAL
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.6330] policy: set 'Kiinteä yhteys 2' (enx0c5b8f279a64) as default for IPv4 routing and DNS
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.6332] DNS: starting dnsmasq...
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <warn>  [1466081586.6778] dnsmasq[0x1c302e0]: dnsmasq not found on the bus. The nameserver update will be sent when dnsmasq appears
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081586.6779] dns-mgr: Writing DNS information to /sbin/resolvconf
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC dnsmasq[2123]: started, version 2.75 cache disabled
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC dnsmasq[2123]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC dnsmasq[2123]: DBus support enabled: connected to system bus
Jun 16 15:53:06 u-HP-Pavilion-17-Notebook-PC dnsmasq[2123]: warning: no upstream servers configured
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081587.0267] device (enx0c5b8f279a64): Activation: successful, device activated.
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC dbus[737]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC whoopsie[782]: [15:53:07] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081587.0349] dnsmasq[0x1c302e0]: dnsmasq appeared as :1.111
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC dnsmasq[2123]: setting upstream servers from DBus
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081587.0352] dns-mgr: Writing DNS information to /sbin/resolvconf
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC dnsmasq[2123]: using nameserver 192.168.1.1#53
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC systemd[1]: Starting Network Manager Script Dispatcher Service...
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC whoopsie[782]: [15:53:07] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC whoopsie[782]: [15:53:07] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC dbus[737]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC systemd[1]: Started Network Manager Script Dispatcher Service.
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC nm-dispatcher: req:1 'up' [enx0c5b8f279a64]: new request (1 scripts)
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC nm-dispatcher: req:1 'up' [enx0c5b8f279a64]: start running ordered scripts...
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: Joining mDNS multicast group on interface enx0c5b8f279a64.IPv6 with address fe80::753b:582f:2cc6:9649.
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: New relevant interface enx0c5b8f279a64.IPv6 for mDNS.
Jun 16 15:53:07 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: Registering new address record for fe80::753b:582f:2cc6:9649 on enx0c5b8f279a64.*.
Jun 16 15:53:09 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081589.5711] policy: set 'Kiinteä yhteys 2' (enx0c5b8f279a64) as default for IPv6 routing and DNS
Jun 16 15:53:09 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081589.6010] dhcp6 (enx0c5b8f279a64): activation: beginning transaction (timeout in 45 seconds)
Jun 16 15:53:09 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081589.6039] dhcp6 (enx0c5b8f279a64): dhclient started with pid 2207
Jun 16 15:53:09 u-HP-Pavilion-17-Notebook-PC dhclient[2207]: XMT: Info-Request on enx0c5b8f279a64, interval 960ms.
Jun 16 15:53:10 u-HP-Pavilion-17-Notebook-PC dhclient[2207]: XMT: Info-Request on enx0c5b8f279a64, interval 1980ms.
Jun 16 15:53:12 u-HP-Pavilion-17-Notebook-PC dhclient[2207]: XMT: Info-Request on enx0c5b8f279a64, interval 3950ms.
Jun 16 15:53:16 u-HP-Pavilion-17-Notebook-PC dhclient[2207]: XMT: Info-Request on enx0c5b8f279a64, interval 8260ms.
Jun 16 15:53:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081596.8342] dhcp6 (enx0c5b8f279a64): dhclient started with pid 2208
Jun 16 15:53:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081596.8351] dhcp6 (enx0c5b8f279a64): canceled DHCP transaction, DHCP client pid 2207
Jun 16 15:53:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081596.8352] dhcp6 (enx0c5b8f279a64): state changed unknown -> done
Jun 16 15:53:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081596.8365] dhcp6 (enx0c5b8f279a64): activation: beginning transaction (timeout in 45 seconds)
Jun 16 15:53:16 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081596.8395] dhcp6 (enx0c5b8f279a64): dhclient started with pid 2209
Jun 16 15:53:17 u-HP-Pavilion-17-Notebook-PC dhclient[2209]: XMT: Solicit on enx0c5b8f279a64, interval 1080ms.
Jun 16 15:53:18 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: Leaving mDNS multicast group on interface enx0c5b8f279a64.IPv6 with address fe80::753b:582f:2cc6:9649.
Jun 16 15:53:18 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: Joining mDNS multicast group on interface enx0c5b8f279a64.IPv6 with address 2001:14bb:150:6a26:ac59:d77f:eddc:ff82.
Jun 16 15:53:18 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: Registering new address record for 2001:14bb:150:6a26:ac59:d77f:eddc:ff82 on enx0c5b8f279a64.*.
Jun 16 15:53:18 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: Withdrawing address record for fe80::753b:582f:2cc6:9649 on enx0c5b8f279a64.
Jun 16 15:53:18 u-HP-Pavilion-17-Notebook-PC kernel: [ 1713.977781] cdc_ether 1-1:1.0 enx0c5b8f279a64: kevent 12 may have been dropped
Jun 16 15:53:18 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: Registering new address record for 2001:14bb:150:6a26:ba19:8355:7757:bc3b on enx0c5b8f279a64.*.
Jun 16 15:53:18 u-HP-Pavilion-17-Notebook-PC dhclient[2209]: XMT: Solicit on enx0c5b8f279a64, interval 2250ms.
Jun 16 15:53:21 u-HP-Pavilion-17-Notebook-PC dhclient[2209]: XMT: Solicit on enx0c5b8f279a64, interval 4650ms.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC whoopsie[782]: [15:53:22] online
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC systemd[1]: Stopping Avahi mDNS/DNS-SD Stack...
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: Got SIGTERM, quitting.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: Leaving mDNS multicast group on interface enx0c5b8f279a64.IPv6 with address 2001:14bb:150:6a26:ac59:d77f:eddc:ff82.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: Leaving mDNS multicast group on interface enx0c5b8f279a64.IPv4 with address 192.168.1.100.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[754]: avahi-daemon 0.6.32-rc exiting.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC systemd[1]: Stopped Avahi mDNS/DNS-SD Stack.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC kernel: [ 1718.202742] cdc_ether 1-1:1.0 enx0c5b8f279a64: kevent 12 may have been dropped
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC nm-dispatcher[2162]: Warning: Stopping avahi-daemon.service, but it can still be activated by:
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC nm-dispatcher[2162]:   avahi-daemon.socket
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC dbus[737]: [system] Activating via systemd: service name='org.freedesktop.Avahi' unit='dbus-org.freedesktop.Avahi.service'
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi: Avahi detected that your currently configured local DNS server serves
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi: a domain .local. This is inherently incompatible with Avahi and thus
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi: contact your administrator and convince him to use a different DNS domain,
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi: since .local should be used exclusively for Zeroconf technology.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi: For more information, see http://avahi.org/wiki/AvahiAndUnicastDotLocal
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: Process 754 died: No such process; trying to remove PID file. (/var/run/avahi-daemon//pid)
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: Found user 'avahi' (UID 111) and group 'avahi' (GID 120).
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: Successfully dropped root privileges.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: avahi-daemon 0.6.32-rc starting up.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC dbus[737]: [system] Successfully activated service 'org.freedesktop.Avahi'
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: Successfully called chroot().
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: Successfully dropped remaining capabilities.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: No service file found in /etc/avahi/services.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: Joining mDNS multicast group on interface enx0c5b8f279a64.IPv6 with address 2001:14bb:150:6a26:ba19:8355:7757:bc3b.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: New relevant interface enx0c5b8f279a64.IPv6 for mDNS.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: Joining mDNS multicast group on interface enx0c5b8f279a64.IPv4 with address 192.168.1.100.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: New relevant interface enx0c5b8f279a64.IPv4 for mDNS.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: Network interface enumeration completed.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: Registering new address record for 2001:14bb:150:6a26:ba19:8355:7757:bc3b on enx0c5b8f279a64.*.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: Registering new address record for 2001:14bb:150:6a26:ac59:d77f:eddc:ff82 on enx0c5b8f279a64.*.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: Registering new address record for 192.168.1.100 on enx0c5b8f279a64.IPv4.
Jun 16 15:53:22 u-HP-Pavilion-17-Notebook-PC kernel: [ 1718.242308] cdc_ether 1-1:1.0 enx0c5b8f279a64: kevent 12 may have been dropped
Jun 16 15:53:23 u-HP-Pavilion-17-Notebook-PC avahi-daemon[2289]: Server startup complete. Host name is u-HP-Pavilion-17-Notebook-PC.local. Local service cookie is 2920346692.
Jun 16 15:53:23 u-HP-Pavilion-17-Notebook-PC systemd[1]: Time has been changed
Jun 16 15:53:23 u-HP-Pavilion-17-Notebook-PC systemd[1152]: Time has been changed
Jun 16 15:53:23 u-HP-Pavilion-17-Notebook-PC systemd-timesyncd[634]: Synchronized to time server [2001:67c:1560:8003::c7]:123 (ntp.ubuntu.com).
Jun 16 15:53:23 u-HP-Pavilion-17-Notebook-PC systemd[1]: snapd.refresh.timer: Adding 5h 14min 42.022486s random time.
Jun 16 15:53:23 u-HP-Pavilion-17-Notebook-PC systemd[1]: apt-daily.timer: Adding 4h 12min 55.452624s random time.
Jun 16 15:53:24 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081604.9177] dhcp6 (enx0c5b8f279a64): dhclient started with pid 2318
Jun 16 15:53:24 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081604.9186] dhcp6 (enx0c5b8f279a64): canceled DHCP transaction, DHCP client pid 2209
Jun 16 15:53:24 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081604.9186] dhcp6 (enx0c5b8f279a64): state changed unknown -> done
Jun 16 15:53:32 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081612.1732] dhcp6 (enx0c5b8f279a64): activation: beginning transaction (timeout in 45 seconds)
Jun 16 15:53:32 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081612.1762] dhcp6 (enx0c5b8f279a64): dhclient started with pid 2323
Jun 16 15:53:32 u-HP-Pavilion-17-Notebook-PC dhclient[2323]: XMT: Solicit on enx0c5b8f279a64, interval 1090ms.
Jun 16 15:53:33 u-HP-Pavilion-17-Notebook-PC dhclient[2323]: XMT: Solicit on enx0c5b8f279a64, interval 2180ms.
Jun 16 15:53:36 u-HP-Pavilion-17-Notebook-PC dhclient[2323]: XMT: Solicit on enx0c5b8f279a64, interval 4330ms.
Jun 16 15:53:40 u-HP-Pavilion-17-Notebook-PC dhclient[2323]: XMT: Solicit on enx0c5b8f279a64, interval 8700ms.
Jun 16 15:53:43 u-HP-Pavilion-17-Notebook-PC gnome-session[1377]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Jun 16 15:53:49 u-HP-Pavilion-17-Notebook-PC dhclient[2323]: XMT: Solicit on enx0c5b8f279a64, interval 17080ms.
Jun 16 15:54:06 u-HP-Pavilion-17-Notebook-PC dhclient[2323]: XMT: Solicit on enx0c5b8f279a64, interval 34770ms.
Jun 16 15:54:17 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <warn>  [1466081657.6624] dhcp6 (enx0c5b8f279a64): request timed out
Jun 16 15:54:17 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081657.6625] dhcp6 (enx0c5b8f279a64): state changed unknown -> timeout
Jun 16 15:54:17 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081657.6634] dhcp6 (enx0c5b8f279a64): canceled DHCP transaction, DHCP client pid 2323
Jun 16 15:54:17 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466081657.6635] dhcp6 (enx0c5b8f279a64): state changed timeout -> done
```

By the way, the web management page of the dongle didn't open automatically. I still don't know if it's supposed to on Ubuntu.

I just noticed that I also got these messages in the syslog:
```

Jun 16 16:03:54 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466082234.0177] dhcp6 (enx0c5b8f279a64): activation: beginning transaction (timeout in 45 seconds)
Jun 16 16:03:54 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466082234.0204] dhcp6 (enx0c5b8f279a64): dhclient started with pid 2558
Jun 16 16:03:54 u-HP-Pavilion-17-Notebook-PC dhclient[2558]: XMT: Solicit on enx0c5b8f279a64, interval 1090ms.
Jun 16 16:03:55 u-HP-Pavilion-17-Notebook-PC dhclient[2558]: XMT: Solicit on enx0c5b8f279a64, interval 2140ms.
Jun 16 16:03:57 u-HP-Pavilion-17-Notebook-PC dhclient[2558]: XMT: Solicit on enx0c5b8f279a64, interval 4200ms.
Jun 16 16:04:02 u-HP-Pavilion-17-Notebook-PC dhclient[2558]: XMT: Solicit on enx0c5b8f279a64, interval 8680ms.
Jun 16 16:04:10 u-HP-Pavilion-17-Notebook-PC dhclient[2558]: XMT: Solicit on enx0c5b8f279a64, interval 17700ms.
Jun 16 16:04:28 u-HP-Pavilion-17-Notebook-PC dhclient[2558]: XMT: Solicit on enx0c5b8f279a64, interval 33870ms.
Jun 16 16:04:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <warn>  [1466082279.6451] dhcp6 (enx0c5b8f279a64): request timed out
Jun 16 16:04:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466082279.6452] dhcp6 (enx0c5b8f279a64): state changed unknown -> timeout
Jun 16 16:04:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466082279.6460] dhcp6 (enx0c5b8f279a64): canceled DHCP transaction, DHCP client pid 2558
Jun 16 16:04:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466082279.6461] dhcp6 (enx0c5b8f279a64): state changed timeout -> done
Jun 16 16:07:54 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466082474.2868] dhcp6 (enx0c5b8f279a64): activation: beginning transaction (timeout in 45 seconds)
Jun 16 16:07:54 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466082474.2898] dhcp6 (enx0c5b8f279a64): dhclient started with pid 2575
Jun 16 16:07:54 u-HP-Pavilion-17-Notebook-PC dhclient[2575]: XMT: Solicit on enx0c5b8f279a64, interval 1040ms.
Jun 16 16:07:55 u-HP-Pavilion-17-Notebook-PC dhclient[2575]: XMT: Solicit on enx0c5b8f279a64, interval 2170ms.
Jun 16 16:07:58 u-HP-Pavilion-17-Notebook-PC dhclient[2575]: XMT: Solicit on enx0c5b8f279a64, interval 4490ms.
Jun 16 16:08:02 u-HP-Pavilion-17-Notebook-PC dhclient[2575]: XMT: Solicit on enx0c5b8f279a64, interval 8880ms.
Jun 16 16:08:11 u-HP-Pavilion-17-Notebook-PC dhclient[2575]: XMT: Solicit on enx0c5b8f279a64, interval 17500ms.
Jun 16 16:08:29 u-HP-Pavilion-17-Notebook-PC dhclient[2575]: XMT: Solicit on enx0c5b8f279a64, interval 35180ms.
Jun 16 16:08:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <warn>  [1466082519.6514] dhcp6 (enx0c5b8f279a64): request timed out
Jun 16 16:08:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466082519.6515] dhcp6 (enx0c5b8f279a64): state changed unknown -> timeout
Jun 16 16:08:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466082519.6524] dhcp6 (enx0c5b8f279a64): canceled DHCP transaction, DHCP client pid 2575
Jun 16 16:08:39 u-HP-Pavilion-17-Notebook-PC NetworkManager[769]: <info>  [1466082519.6525] dhcp6 (enx0c5b8f279a64): state changed timeout -> done

```
**Is this normal behavior? I'm also worried about the "kevent dropped" messages that appear in the upper log part of this post.**

I also noticed that AptDaemon has returned also for non-admin users, and with an even longer inactivity period. This is not good if the disconnection problem also returns because it might now more likely happen within the first 15-20 minutes instead of the previous 5-10.

---

### Post by ubuser4 on 2016-06-16
I started my computer again, this time with the dongle already plugged in. Now it wasn't detected as a modem, but a CD named HILINK. I used the Eject function of Files (Nautilus), physically unplugged the dongle, and replugged it back. It was detected as a modem again and there has been an internet connection since, at least for now. Is this (eject, unplug, replug) the correct procedure, or should I have run the installation script on the "CD"?

---

### Post by ubuser4 on 2016-06-16
Now I started my computer without the dongle plugged in. I had to plug it in three times before I could get on the internet. (I used the eject-unplug-replug method I described in my previous post.)
Here's dmesg from the first two attempts:
```

[  155.876350] usb 1-1: new high-speed USB device number 2 using ehci-pci
[  156.009551] usb 1-1: New USB device found, idVendor=12d1, idProduct=1f01
[  156.009559] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  156.009564] usb 1-1: Product: HUAWEI_MOBILE
[  156.009568] usb 1-1: Manufacturer: HUAWEI_MOBILE
[  156.009572] usb 1-1: SerialNumber: 0123456789ABCDEF
[  156.299401] usb-storage 1-1:1.0: USB Mass Storage device detected
[  156.299689] scsi host4: usb-storage 1-1:1.0
[  156.299869] usbcore: registered new interface driver usb-storage
[  156.337078] usbcore: registered new interface driver uas
[  157.303261] scsi 4:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  157.303889] scsi 4:0:0:1: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[  157.308629] sr 4:0:0:0: [sr1] scsi-1 drive
[  157.308919] sr 4:0:0:0: Attached scsi CD-ROM sr1
[  157.309072] sr 4:0:0:0: Attached scsi generic sg2 type 5
[  157.313431] sd 4:0:0:1: Attached scsi generic sg3 type 0
[  157.323877] sd 4:0:0:1: [sdb] Attached SCSI removable disk
[  159.884410] sr 4:0:0:0: [sr1] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  159.884421] sr 4:0:0:0: [sr1] tag#0 Sense Key : Medium Error [current] 
[  159.884427] sr 4:0:0:0: [sr1] tag#0 Add. Sense: Unrecovered read error
[  159.884435] sr 4:0:0:0: [sr1] tag#0 CDB: Read(10) 28 00 00 00 0f fe 00 00 02 00
[  159.884440] blk_update_request: critical medium error, dev sr1, sector 16376
[  159.891282] sr 4:0:0:0: [sr1] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  159.891293] sr 4:0:0:0: [sr1] tag#0 Sense Key : Medium Error [current] 
[  159.891299] sr 4:0:0:0: [sr1] tag#0 Add. Sense: Unrecovered read error
[  159.891306] sr 4:0:0:0: [sr1] tag#0 CDB: Read(10) 28 00 00 00 0f fe 00 00 02 00
[  159.891311] blk_update_request: critical medium error, dev sr1, sector 16376
[  159.891318] Buffer I/O error on dev sr1, logical block 2047, async page read
[  160.151940] ISO 9660 Extensions: Microsoft Joliet Level 1
[  160.175872] ISOFS: changing to secondary root
[  250.826020] usb 1-1: USB disconnect, device number 2
[  272.067906] usb 1-1: new high-speed USB device number 3 using ehci-pci
[  272.201425] usb 1-1: New USB device found, idVendor=12d1, idProduct=1f01
[  272.201433] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  272.201438] usb 1-1: Product: HUAWEI_MOBILE
[  272.201442] usb 1-1: Manufacturer: HUAWEI_MOBILE
[  272.201446] usb 1-1: SerialNumber: 0123456789ABCDEF
[  272.263387] usb-storage 1-1:1.0: USB Mass Storage device detected
[  272.264111] scsi host5: usb-storage 1-1:1.0
[  273.270901] scsi 5:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  273.271693] scsi 5:0:0:1: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[  273.276775] sr 5:0:0:0: [sr1] scsi-1 drive
[  273.277987] sr 5:0:0:0: Attached scsi CD-ROM sr1
[  273.278213] sr 5:0:0:0: Attached scsi generic sg2 type 5
[  273.278626] sd 5:0:0:1: Attached scsi generic sg3 type 0
[  273.292783] sd 5:0:0:1: [sdb] Attached SCSI removable disk
[  275.603351] sr 5:0:0:0: [sr1] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  275.603361] sr 5:0:0:0: [sr1] tag#0 Sense Key : Medium Error [current] 
[  275.603368] sr 5:0:0:0: [sr1] tag#0 Add. Sense: Unrecovered read error
[  275.603375] sr 5:0:0:0: [sr1] tag#0 CDB: Read(10) 28 00 00 00 0f fe 00 00 02 00
[  275.603380] blk_update_request: critical medium error, dev sr1, sector 16376
[  275.610225] sr 5:0:0:0: [sr1] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  275.610235] sr 5:0:0:0: [sr1] tag#0 Sense Key : Medium Error [current] 
[  275.610242] sr 5:0:0:0: [sr1] tag#0 Add. Sense: Unrecovered read error
[  275.610248] sr 5:0:0:0: [sr1] tag#0 CDB: Read(10) 28 00 00 00 0f fe 00 00 02 00
[  275.610253] blk_update_request: critical medium error, dev sr1, sector 16376
[  275.610260] Buffer I/O error on dev sr1, logical block 2047, async page read
[  275.739947] ISO 9660 Extensions: Microsoft Joliet Level 1
[  275.740450] ISOFS: changing to secondary root

```
During those attempts, I got a dialog asking if I would like to run software on the CD. I chose to run it, only to get a dialog which stated that software wasn't found.

I think this might be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1424181](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1424181). When I look at the Huawei web UI page, it says the signal is weak (alternates between 1 and 2 bars out of 5). Could this be why Ubuntu sometimes interprets the device as a CD?

---

### Post by ubuser4 on 2016-06-17
The problem where the dongle is interpreted as a CD is probably not related to signal strength. I had it again today and when I finally got online, the web UI said that signal strength is 5/5, sometimes 4/5.

I also noticed that whenever the dongle is detected as a CD, its LED blinks as green twice every two seconds, which means the power is on, but the device is not registering or connected to any network.

When the connection does happen, the connection doesn't always have a name. When it does, it's named "HUAWEI MOBILE".

---

### Post by ubuser4 on 2016-06-17
I did some more searching and found this: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1507957/comments/17](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1507957/comments/17). My current situation is similar to that in the comment I linked but I'm using Ubuntu 16.04 and the kernel is from the 4.4 series.

---

### Post by ubuser4 on 2016-06-19
A disconnection happened today, and **with the new dongle!** The Network Manager still said I was connected. Here's /var/log/syslog:
```
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932462] ------------[ cut here ]------------
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932477] WARNING: CPU: 2 PID: 941 at /build/linux-oXTOqc/linux-4.4.0/net/sched/sch_generic.c:303 dev_watchdog+0x237/0x240()
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932481] NETDEV WATCHDOG: enx0c5b8f279a64 (cdc_ether): transmit queue 0 timed out
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932484] Modules linked in: cdc_ether usbnet nls_utf8 isofs uas usb_storage nls_iso8859_1 kvm snd_hda_codec_realtek uvcvideo snd_hda_codec_generic snd_hda_codec_hdmi irqbypass videobuf2_vmalloc videobuf2_memops hp_wmi arc4 videobuf2_v4l2 videobuf2_core rt2800pci sparse_keymap rt2800mmio v4l2_common snd_hda_intel videodev snd_hda_codec snd_hda_core crct10dif_pclmul rt2800lib media snd_hwdep crc32_pclmul rt2x00pci rt2x00mmio aesni_intel aes_x86_64 rt2x00lib snd_pcm lrw snd_seq_midi snd_seq_midi_event gf128mul snd_rawmidi mac80211 cfg80211 glue_helper snd_seq eeprom_93cx6 crc_ccitt ablk_helper rtsx_pci_ms memstick cryptd k10temp input_leds joydev snd_seq_device snd_timer serio_raw snd soundcore shpchp i2c_piix4 hp_accel lis3lv02d input_polldev hp_wireless mac_hid ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables parport_pc ppdev lp parport autofs4 hid_generic usbhid hid rtsx_pci_sdmmc amdkfd amd_iommu_v2 radeon i2c_algo_bit psmouse ttm drm_kms_helper r8169 syscopyarea sysfillrect rtsx_pci mii sysimgblt fb_sys_fops ahci drm libahci wmi fjes video
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932613] CPU: 2 PID: 941 Comm: Xorg Not tainted 4.4.0-24-generic #43-Ubuntu
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932617] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932621]  0000000000003286 000000008196a60b ffff88021ed03d98 ffffffff813eab23
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932627]  ffff88021ed03de0 ffffffff81d62b48 ffff88021ed03dd0 ffffffff810810d2
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932631]  0000000000000000 ffff8800ad1c3480 0000000000000002 ffff8800ad9e3000
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932636] Call Trace:
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932639]  <IRQ>  [<ffffffff813eab23>] dump_stack+0x63/0x90
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932652]  [<ffffffff810810d2>] warn_slowpath_common+0x82/0xc0
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932657]  [<ffffffff8108116c>] warn_slowpath_fmt+0x5c/0x80
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932664]  [<ffffffff817426e7>] dev_watchdog+0x237/0x240
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932668]  [<ffffffff817424b0>] ? qdisc_rcu_free+0x40/0x40
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932675]  [<ffffffff810ec4c5>] call_timer_fn+0x35/0x120
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932678]  [<ffffffff817424b0>] ? qdisc_rcu_free+0x40/0x40
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932684]  [<ffffffff810ece7a>] run_timer_softirq+0x23a/0x2f0
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932690]  [<ffffffff81085b11>] __do_softirq+0x101/0x290
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932695]  [<ffffffff81085e13>] irq_exit+0xa3/0xb0
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932701]  [<ffffffff818286a2>] smp_apic_timer_interrupt+0x42/0x50
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932705]  [<ffffffff81826962>] apic_timer_interrupt+0x82/0x90
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932707]  <EOI> 
Jun 19 11:00:06 u-HP-Pavilion-17-Notebook-PC kernel: [  296.932710] ---[ end trace 81189c743739e0d3 ]---
```

Maybe I didn't wait long enough before using the internet, but then again, waiting didn't help when I used Ubuntu 14.04 and the old dongle.

At least no freeze happened this time, so I could shut down normally.

---

### Post by ubuser4 on 2016-07-05
I've managed to avoid the problem for over a week now. The last time a disconnection happened was 8 days ago. The connection lasted almost 12 minutes before that. Here's the related part of /var/log/syslog:
```
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732418] ------------[ cut here ]------------
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732433] WARNING: CPU: 2 PID: 0 at /build/linux-oXTOqc/linux-4.4.0/net/sched/sch_generic.c:303 dev_watchdog+0x237/0x240()
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732437] NETDEV WATCHDOG: enx0c5b8f279a64 (cdc_ether): transmit queue 0 timed out
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732440] Modules linked in: cdc_ether usbnet uas usb_storage nls_iso8859_1 arc4 rt2800pci uvcvideo rt2800mmio rt2800lib videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core hp_wmi v4l2_common rt2x00pci sparse_keymap rt2x00mmio snd_hda_codec_realtek snd_hda_codec_generic kvm snd_hda_codec_hdmi snd_hda_intel snd_hda_codec rt2x00lib snd_hda_core irqbypass videodev media snd_hwdep mac80211 crct10dif_pclmul snd_pcm crc32_pclmul snd_seq_midi aesni_intel cfg80211 aes_x86_64 snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer lrw gf128mul eeprom_93cx6 crc_ccitt glue_helper snd rtsx_pci_ms ablk_helper memstick cryptd k10temp input_leds joydev serio_raw soundcore shpchp i2c_piix4 hp_accel lis3lv02d hp_wireless input_polldev mac_hid ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables parport_pc ppdev lp parport autofs4 hid_generic usbhid hid rtsx_pci_sdmmc amdkfd amd_iommu_v2 radeon i2c_algo_bit ttm psmouse drm_kms_helper r8169 syscopyarea rtsx_pci sysfillrect mii sysimgblt fb_sys_fops ahci drm libahci wmi fjes video
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732567] CPU: 2 PID: 0 Comm: swapper/2 Not tainted 4.4.0-24-generic #43-Ubuntu
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732571] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732574]  0000000000000286 75ee5de698e118ca ffff88021ed03d98 ffffffff813eab23
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732580]  ffff88021ed03de0 ffffffff81d62b48 ffff88021ed03dd0 ffffffff810810d2
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732585]  0000000000000000 ffff8800a7d25a80 0000000000000002 ffff880213133000
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732589] Call Trace:
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732592]  <IRQ>  [<ffffffff813eab23>] dump_stack+0x63/0x90
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732606]  [<ffffffff810810d2>] warn_slowpath_common+0x82/0xc0
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732611]  [<ffffffff8108116c>] warn_slowpath_fmt+0x5c/0x80
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732617]  [<ffffffff817426e7>] dev_watchdog+0x237/0x240
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732622]  [<ffffffff817424b0>] ? qdisc_rcu_free+0x40/0x40
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732628]  [<ffffffff810ec4c5>] call_timer_fn+0x35/0x120
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732632]  [<ffffffff817424b0>] ? qdisc_rcu_free+0x40/0x40
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732638]  [<ffffffff810ece7a>] run_timer_softirq+0x23a/0x2f0
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732644]  [<ffffffff81085b11>] __do_softirq+0x101/0x290
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732649]  [<ffffffff81085e13>] irq_exit+0xa3/0xb0
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732655]  [<ffffffff818286a2>] smp_apic_timer_interrupt+0x42/0x50
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732658]  [<ffffffff81826962>] apic_timer_interrupt+0x82/0x90
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732660]  <EOI>  [<ffffffff816bcd21>] ? cpuidle_enter_state+0x111/0x2b0
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732669]  [<ffffffff816bcef7>] cpuidle_enter+0x17/0x20
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732675]  [<ffffffff810c3ec2>] call_cpuidle+0x32/0x60
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732679]  [<ffffffff816bced3>] ? cpuidle_select+0x13/0x20
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732683]  [<ffffffff810c4180>] cpu_startup_entry+0x290/0x350
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732689]  [<ffffffff81051714>] start_secondary+0x154/0x190
Jun 27 17:12:00 u-HP-Pavilion-17-Notebook-PC kernel: [  912.732693] ---[ end trace 344effa8f6af5034 ]---
```
The last logged things before the disconnection were startup of a hostname service and cleanup of temporary directories. These happened within the last minute before the messages above. There was no freeze and I didn't wait for one (I shut down the computer almost immediately).

I've also noticed that the longer I wait before plugging in the dongle, the less probably the device is detected as a CD. It also seems waiting a few minutes after the connection is established makes the disconnections/crashes happen less frequently. Perhaps the dongle needs some time to "warm up"?

---

### Post by ubuser4 on 2016-07-06
This post is about the "dongle is detected as a CD" bug. (Should I have started another thread for this because it can be unrelated to the disconnection and crash issue?)

On some forums, the command "usb_modeswitch -J -v 0x12d1 -p 0x1f01" has been posted as a workaround. However, that doesn't work for me. This is what I get if I try it:
```
Look for default devices ...
   product ID matched
 Found devices in default mode (1)
Access device 003 on bus 001
Error opening the device. Abort
```
It doesn't matter if the device is mounted or not. The result is always the same. So far, the eject-unplug-replug method has been the only one that works to some extent, but sometimes I've had to repeat it for almost 10 times before I got the dongle detected correctly.

---

### Post by ubuser4 on 2016-07-15
I just updated the software on the dongle (I think).

When I opened Firefox, the web interface of Huawei E3372 opened instead of the default home page. There was a message there stating that an update was available, so I chose to install it. At 99%, the installation process got stuck and the device appeared as a CD. I followed the instructions at [https://sites.google.com/site/tomihasa/mobile-sticks](https://sites.google.com/site/tomihasa/mobile-sticks), but got nothing. The next thing I did was try the usb_modeswitch trick (usb_modeswitch -J -v 0x12d1 -p 0x1f01). I did it as sudo and the dongle started up correctly, or at least that's what it looks like to me. However, the web UI page didn't change, so I refreshed it. After that, I told the software to check for updates and it found none. (In hindsight, I perhaps should have written down the old and new version numbers and compared them to see if any software was updated.)

The dongle has worked for now. According to the web page, the current connection has lasted 22 minutes. I haven't closed the browser or restarted the computer so I don't know if it lasts.

All in all, I'm not sure if the update was successful and I don't know yet if it solved anything.

---

### Post by ubuser4 on 2016-08-01
A crash happened again (but no freeze).

As always, here's the part of /var/log/syslog that I think might be related to the problem:
```

Aug  1 17:58:02 u-HP-Pavilion-17-Notebook-PC systemd-timesyncd[618]: Timed out waiting for reply from [2001:67c:1560:8003::c7]:123 (ntp.ubuntu.com).
Aug  1 17:58:12 u-HP-Pavilion-17-Notebook-PC systemd-timesyncd[618]: Timed out waiting for reply from [2001:67c:1560:8003::c8]:123 (ntp.ubuntu.com).
Aug  1 17:58:23 u-HP-Pavilion-17-Notebook-PC systemd-timesyncd[618]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
Aug  1 17:58:33 u-HP-Pavilion-17-Notebook-PC systemd-timesyncd[618]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
Aug  1 17:58:43 u-HP-Pavilion-17-Notebook-PC systemd-timesyncd[618]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
Aug  1 17:58:53 u-HP-Pavilion-17-Notebook-PC systemd-timesyncd[618]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.672692] ------------[ cut here ]------------
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.672740] WARNING: CPU: 3 PID: 0 at /build/linux-dcxD3m/linux-4.4.0/net/sched/sch_generic.c:306 dev_watchdog+0x237/0x240()
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.672748] NETDEV WATCHDOG: enx0c5b8f279a64 (cdc_ether): transmit queue 0 timed out
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.672753] Modules linked in: cdc_ether usbnet uas usb_storage nls_iso8859_1 arc4 rt2800pci rt2800mmio rt2800lib rt2x00pci kvm snd_hda_codec_realtek snd_hda_codec_hdmi snd_hda_codec_generic rt2x00mmio snd_hda_intel uvcvideo rt2x00lib snd_hda_codec irqbypass mac80211 snd_hda_core videobuf2_vmalloc videobuf2_memops crct10dif_pclmul videobuf2_v4l2 snd_hwdep videobuf2_core v4l2_common snd_pcm videodev hp_wmi snd_seq_midi snd_seq_midi_event media sparse_keymap crc32_pclmul snd_rawmidi aesni_intel snd_seq aes_x86_64 lrw gf128mul glue_helper snd_seq_device cfg80211 snd_timer snd ablk_helper joydev eeprom_93cx6 soundcore crc_ccitt rtsx_pci_ms memstick cryptd input_leds k10temp serio_raw shpchp i2c_piix4 hp_accel lis3lv02d input_polldev hp_wireless mac_hid ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables parport_pc ppdev x_tables lp parport autofs4 hid_generic usbhid hid rtsx_pci_sdmmc amdkfd amd_iommu_v2 radeon i2c_algo_bit ttm r8169 drm_kms_helper mii syscopyarea psmouse sysfillrect sysimgblt fb_sys_fops rtsx_pci drm ahci libahci wmi fjes video
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.672953] CPU: 3 PID: 0 Comm: swapper/3 Not tainted 4.4.0-31-generic #50-Ubuntu
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.672971] Hardware name: Hewlett-Packard HP Pavilion 17 Notebook PC/1984, BIOS F.22 09/26/2013
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.672980]  0000000000000286 827e61ce46f644c3 ffff88021ed83d98 ffffffff813f1143
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.672987]  ffff88021ed83de0 ffffffff81d66c78 ffff88021ed83dd0 ffffffff81081102
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673000]  0000000000000000 ffff8800ad4dda80 0000000000000003 ffff8800ae33a000
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673007] Call Trace:
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673015]  <IRQ>  [<ffffffff813f1143>] dump_stack+0x63/0x90
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673032]  [<ffffffff81081102>] warn_slowpath_common+0x82/0xc0
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673039]  [<ffffffff8108119c>] warn_slowpath_fmt+0x5c/0x80
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673081]  [<ffffffffc004dbf0>] ? vblank_disable_and_save+0x70/0x80 [drm]
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673105]  [<ffffffff817495f7>] dev_watchdog+0x237/0x240
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673113]  [<ffffffff817493c0>] ? qdisc_rcu_free+0x40/0x40
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673129]  [<ffffffff810ec5e5>] call_timer_fn+0x35/0x120
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673139]  [<ffffffff817493c0>] ? qdisc_rcu_free+0x40/0x40
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673150]  [<ffffffff810ecf9a>] run_timer_softirq+0x23a/0x2f0
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673161]  [<ffffffff81085b51>] __do_softirq+0x101/0x290
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673170]  [<ffffffff81085e53>] irq_exit+0xa3/0xb0
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673197]  [<ffffffff818305e2>] smp_apic_timer_interrupt+0x42/0x50
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673222]  [<ffffffff8182e8a2>] apic_timer_interrupt+0x82/0x90
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673239]  <EOI>  [<ffffffff816c3c11>] ? cpuidle_enter_state+0x111/0x2b0
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673285]  [<ffffffff816c3de7>] cpuidle_enter+0x17/0x20
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673311]  [<ffffffff810c3fe2>] call_cpuidle+0x32/0x60
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673338]  [<ffffffff816c3dc3>] ? cpuidle_select+0x13/0x20
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673367]  [<ffffffff810c42a0>] cpu_startup_entry+0x290/0x350
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673395]  [<ffffffff81051714>] start_secondary+0x154/0x190
Aug  1 18:00:05 u-HP-Pavilion-17-Notebook-PC kernel: [  685.673447] ---[ end trace 5dfaf9b12279a480 ]---

```


I have absolutely no idea what to do. Perhaps I should just give up, get a dongle of a different type (or use my phone) and hope it will work better.

---

