---
title: "Pls help Ubuntu Often Hangs...."
date: 2008-06-05
forum: General Help
---

### Post by MATHEWJOHN on 2008-06-05
Please help I am new to Ubuntu. I have installed ubuntu 8.04 (dual boot XP)

My system configuration is P4 3 GHZ HT, Pentium orginal mother board, 768 MB DDR, 80 GB HDD (IDE), Shared Video memory.... also have another 20 GB hard drive. Both ubuntu & Xp installed on 80 GB disk


My issue is that Ubuntu Hangs most of time.... I have extracted log from my syslog
************************************************** ***************

Jun 1 20:19:19 Thekkadathu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun 1 20:19:19 Thekkadathu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun 1 20:19:19 Thekkadathu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 1 20:19:19 Thekkadathu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun 1 20:19:19 Thekkadathu NetworkManager: <info> Retrieved the following IP4 configuration from the DHCP daemon: 
Jun 1 20:19:19 Thekkadathu NetworkManager: <info> address 192.168.1.5 
Jun 1 20:19:19 Thekkadathu NetworkManager: <info> netmask 255.255.255.0 
Jun 1 20:19:19 Thekkadathu NetworkManager: <info> broadcast 192.168.1.255 
Jun 1 20:19:19 Thekkadathu NetworkManager: <info> gateway 192.168.1.1 
Jun 1 20:19:19 Thekkadathu NetworkManager: <info> nameserver 192.168.1.1 
Jun 1 20:19:19 Thekkadathu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jun 1 20:19:19 Thekkadathu NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jun 1 20:19:19 Thekkadathu NetworkManager: <info> Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jun 1 20:19:19 Thekkadathu NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jun 1 20:19:19 Thekkadathu avahi-daemon[4924]: Withdrawing address record for 192.168.1.5 on eth0.
Jun 1 20:19:19 Thekkadathu avahi-daemon[4924]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.5.
Jun 1 20:19:19 Thekkadathu avahi-daemon[4924]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun 1 20:19:19 Thekkadathu avahi-daemon[4924]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.5.
Jun 1 20:19:19 Thekkadathu avahi-daemon[4924]: New relevant interface eth0.IPv4 for mDNS.
Jun 1 20:19:19 Thekkadathu avahi-daemon[4924]: Registering new address record for 192.168.1.5 on eth0.IPv4.
Jun 1 20:19:20 Thekkadathu NetworkManager: <info> Clearing nscd hosts cache. 
Jun 1 20:19:20 Thekkadathu NetworkManager: <WARN> nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory)) 
Jun 1 20:19:20 Thekkadathu NetworkManager: <info> Activation (eth0) successful, device activated. 
Jun 1 20:19:20 Thekkadathu NetworkManager: <info> Activation (eth0) Finish handler scheduled. 
Jun 1 20:19:20 Thekkadathu NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun 1 20:19:20 Thekkadathu kernel: [ 39.951287] NET: Registered protocol family 10
Jun 1 20:19:20 Thekkadathu kernel: [ 39.951824] lo: Disabled Privacy Extensions
Jun 1 20:19:21 Thekkadathu ntpdate[5492]: adjust time server 91.189.94.4 offset -0.190255 sec
Jun 1 20:19:22 Thekkadathu avahi-daemon[4924]: Registering new address record for fe80::219:d1ff:fe3f:69e on eth0.*.
Jun 1 20:19:23 Thekkadathu kernel: [ 42.762485] hda-intel: Invalid position buffer, using LPIB read method instead.
Jun 1 20:19:31 Thekkadathu kernel: [ 50.862628] eth0: no IPv6 routers present
Jun 1 20:19:36 Thekkadathu NetworkManager: <info> Updating allowed wireless network lists. 
Jun 1 20:19:36 Thekkadathu NetworkManager: <WARN> nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun 1 20:39:13 Thekkadathu -- MARK --
Jun 1 20:59:13 Thekkadathu -- MARK --
*****************************************

pls help

---

### Post by danwood76 on 2008-06-05
Could you describe the error please?
Like when it happens, what you actually mean by a hang, etc.

---

### Post by MATHEWJOHN on 2008-06-05
Complete freeze not responding keyboards, mouse,,, only reset switch to reboot the machine...

any way to check any reports ?

---

### Post by danwood76 on 2008-06-05
Yes.

If you go System (at the top) -> Administration -> System log

scroll back to around the time the system hung and post the output or any obvious errors you see.

Also it would be nice to see a detailed spec of your system, running this in the terminal will show us what you have connected:
```

lspci -v

```

enclode the output in code tags to make it easier to read.

---

### Post by MATHEWJOHN on 2008-06-05
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
	Subsystem: Intel Corporation Unknown device d600
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at <ignored> (64-bit, non-prefetchable)

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: d0000000-dfffffff
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Intel Corporation Unknown device d600
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Intel Corporation Unknown device d600
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Unknown device d600
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
	Subsystem: Intel Corporation Unknown device d600
	Flags: 66MHz, medium devsel
	I/O ports at 0b00 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Unknown device d600
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at fe00 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Intel Corporation Unknown device d600
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Intel Corporation Unknown device d600
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdf00000-fdffffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200] (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation Unknown device d600
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at ee00 [size=256]
	Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at fde00000 [disabled] [size=128K]
	Capabilities: <access denied>

02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Intel Corporation Unknown device d600
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at de00 [size=256]
	Memory at fddff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

---

