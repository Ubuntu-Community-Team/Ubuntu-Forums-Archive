---
title: "Desktop refuses to hibernate"
date: 2006-12-05
forum: General Help
---

### Post by reech on 2006-12-05
My desktop refuses to hibernate - it seems to make it ...and then gets woken up again immediately (see syslog below).

Has anyone experiences anything similar/have any ideas how to resolve this?

```
Dec  5 22:49:34 reech-desktop dhclient: 
Dec  5 22:49:59 reech-desktop kernel: [17189808.868000]  Freezing cpus ...
Dec  5 22:49:59 reech-desktop kernel: [17189813.200000] Stopping tasks: ========================================================================================================
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]  stopping tasks timed out after 20 seconds (11 tasks remaining):
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]   kseriod
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]   pdflush
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]   pdflush
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]   kswapd0
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]   knodemgrd_0
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]   khubd
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]   kjournald
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]   kgameportd
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]   w1_control
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]   w1_bus_master1
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]   dhclient3
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000] Restarting tasks...<6> Strange, kseriod not stopped
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]  Strange, pdflush not stopped
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]  Strange, pdflush not stopped
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]  Strange, kswapd0 not stopped
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]  Strange, knodemgrd_0 not stopped
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]  Strange, khubd not stopped
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]  Strange, kjournald not stopped
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]  Strange, kgameportd not stopped
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]  Strange, w1_control not stopped
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]  Strange, w1_bus_master1 not stopped
Dec  5 22:49:59 reech-desktop kernel: [17189833.204000]  Strange, dhclient3 not stopped
Dec  5 22:49:59 reech-desktop kernel: [17189833.740000]  done
Dec  5 22:49:59 reech-desktop kernel: [17189833.740000] Thawing cpus ...
Dec  5 22:50:01 reech-desktop kernel: [17189835.244000] Linux Tulip driver version 1.1.14 (May 6, 2006)
Dec  5 22:50:01 reech-desktop kernel: [17189835.248000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKF] -> GSI 9 (level, low) -> IRQ 9
Dec  5 22:50:01 reech-desktop kernel: [17189835.320000] tulip0:  EEPROM default media type Autosense.
Dec  5 22:50:01 reech-desktop kernel: [17189835.320000] tulip0:  Index #0 - Media MII (#11) described by a 21140 MII PHY (1) block.
Dec  5 22:50:01 reech-desktop kernel: [17189835.340000] tulip0:  MII transceiver #0 config 1200 status 7809 advertising 01e1.
Dec  5 22:50:09 reech-desktop gnome-power-manager: (reech) Resuming computer 
```

Thanks for looking folks.

---

### Post by Azakus on 2006-12-07
How big is your RAM relative to your Swap partition? You need a Swap partition at least 1.5 times larger than your RAM size.

---

### Post by psypher on 2007-01-11
I have a similar problem, same symptoms but different logs, here is my syslog when trying to hibernate:

```
Jan 11 10:11:14 localhost last message repeated 3 times
Jan 11 10:11:29 localhost kernel: [17186846.384000] ohci1394: fw-host0: Unrecoverable error!
Jan 11 10:11:29 localhost kernel: [17186846.384000] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
Jan 11 10:11:29 localhost kernel: [17186846.384000] ohci1394: fw-host0: Error in reception of SelfID packets [0xa3a3a3a3/0x00011f2c] (count: 3)
Jan 11 10:11:29 localhost kernel: [17186846.384000] ohci1394: fw-host0: Unhandled interrupt(s) 0xa220a300
Jan 11 10:11:29 localhost kernel: [17186846.384000] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
Jan 11 10:11:33 localhost gnome-power-manager: Hibernating computer because the DBUS method Hibernate() was invoked
Jan 11 10:11:33 localhost NetworkManager: <information>^IGoing to sleep.
Jan 11 10:11:33 localhost kernel: [17186850.524000] bridge-eth1: disabling the bridge
Jan 11 10:11:33 localhost kernel: [17186850.536000] bridge-eth1: down
Jan 11 10:11:33 localhost kernel: [17186850.548000] bridge-eth0: disabling the bridge
Jan 11 10:11:33 localhost NetworkManager: <information>^Imatch
Jan 11 10:11:33 localhost last message repeated 3 times
Jan 11 10:11:33 localhost kernel: [17186850.560000] bridge-eth0: down
Jan 11 10:11:33 localhost NetworkManager: <information>^Imatch
Jan 11 10:11:33 localhost dhclient: DHCPRELEASE on eth0 to 192.168.100.10 port 67
Jan 11 10:11:33 localhost dhclient: send_packet: Network is unreachable
Jan 11 10:11:33 localhost dhclient: send_packet: please consult README file regarding broadcast address.
Jan 11 10:11:33 localhost kernel: [17186850.824000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jan 11 10:11:33 localhost NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link.
Jan 11 10:11:33 localhost NetworkManager: <information>^Imatch
Jan 11 10:11:33 localhost kernel: [17186850.828000] bridge-eth0: enabling the bridge
Jan 11 10:11:33 localhost NetworkManager: <information>^Imatch
Jan 11 10:11:33 localhost kernel: [17186850.828000] bridge-eth0: up
Jan 11 10:11:33 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.3
Jan 11 10:11:33 localhost dhclient: Copyright 2004-2005 Internet Systems Consortium.
Jan 11 10:11:33 localhost dhclient: All rights reserved.
Jan 11 10:11:33 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
Jan 11 10:11:33 localhost dhclient:
Jan 11 10:11:33 localhost dhclient: Listening on LPF/eth0/00:03:0d:1b:65:32
Jan 11 10:11:33 localhost dhclient: Sending on   LPF/eth0/00:03:0d:1b:65:32
Jan 11 10:11:33 localhost dhclient: Sending on   Socket/fallback
Jan 11 10:11:33 localhost dhclient: DHCPRELEASE on eth0 to 192.168.100.10 port 67
Jan 11 10:11:33 localhost dhclient: send_packet: Network is unreachable
Jan 11 10:11:33 localhost dhclient: send_packet: please consult README file regarding broadcast address.
Jan 11 10:11:34 localhost NetworkManager: <information>^Imatch
Jan 11 10:11:34 localhost kernel: [17186850.972000] bridge-eth0: disabling the bridge
Jan 11 10:11:34 localhost kernel: [17186850.984000] bridge-eth0: down
Jan 11 10:11:34 localhost NetworkManager: <information>^Imatch
Jan 11 10:11:34 localhost mysqld[17762]: 070111 10:11:34 [Note] /usr/sbin/mysqld: Normal shutdown
Jan 11 10:11:34 localhost mysqld[17762]:
Jan 11 10:11:36 localhost mysqld[17762]: 070111 10:11:36  InnoDB: Starting shutdown...
Jan 11 10:11:39 localhost mysqld[17762]: 070111 10:11:39  InnoDB: Shutdown completed; log sequence number 0 43655
Jan 11 10:11:39 localhost mysqld[17762]: 070111 10:11:39 [Note] /usr/sbin/mysqld: Shutdown complete
Jan 11 10:11:39 localhost mysqld[17762]:
Jan 11 10:11:39 localhost mysqld_safe[18805]: ended
Jan 11 10:11:39 localhost kernel: [17186856.524000] ACPI: PCI interrupt for device 0000:01:0c.0 disabled
Jan 11 10:11:39 localhost kernel: [17186856.580000] ACPI: PCI interrupt for device 0000:01:07.0 disabled
Jan 11 10:11:39 localhost kernel: [17186856.584000] ieee80211_crypt: unregistered algorithm 'NULL'
Jan 11 10:11:39 localhost kernel: [17186856.596000] ieee80211_1_1_13_crypt: unregistered algorithm 'NULL'
Jan 11 10:11:48 localhost kernel: [17186859.288000] Freezing cpus ...
Jan 11 10:11:48 localhost kernel: [17186859.288000] Stopping tasks: ================================================================================================================================================================
Jan 11 10:11:48 localhost kernel: [17186865.292000]  stopping tasks failed (1 tasks remaining)
Jan 11 10:11:48 localhost kernel: [17186865.292000] Restarting tasks...<6> Strange, knodemgrd_0 not stopped
Jan 11 10:11:48 localhost kernel: [17186865.296000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:48 localhost kernel: [17186865.300000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:48 localhost last message repeated 5 times
Jan 11 10:11:48 localhost kernel: [17186865.300000]  done
Jan 11 10:11:48 localhost kernel: [17186865.304000] Thawing cpus ...
Jan 11 10:11:48 localhost kernel: [17186865.304000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:48 localhost last message repeated 3 times
Jan 11 10:11:48 localhost kernel: [17186865.308000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:48 localhost last message repeated 3 times
Jan 11 10:11:48 localhost kernel: [17186865.312000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:48 localhost last message repeated 7 times
Jan 11 10:11:48 localhost kernel: [17186865.316000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:48 localhost last message repeated 3 times
Jan 11 10:11:48 localhost kernel: [17186865.356000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:48 localhost kernel: [17186865.356000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:48 localhost kernel: [17186865.360000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:48 localhost kernel: [17186865.360000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:48 localhost kernel: [17186865.376000] 8139too Fast Ethernet driver 0.9.27
Jan 11 10:11:48 localhost kernel: [17186865.380000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
Jan 11 10:11:48 localhost kernel: [17186865.380000] eth0: RealTek RTL8139 at 0xdf87a400, 00:03:0d:1b:65:32, IRQ 5
Jan 11 10:11:48 localhost kernel: [17186865.380000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Jan 11 10:11:48 localhost kernel: [17186865.388000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
Jan 11 10:11:48 localhost kernel: [17186865.392000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
Jan 11 10:11:48 localhost kernel: [17186865.392000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jan 11 10:11:48 localhost kernel: [17186865.392000] ieee80211_crypt: registered algorithm 'NULL'
Jan 11 10:11:48 localhost kernel: [17186865.396000] ieee80211: 802.11 data/management/control stack, git-1.1.7
Jan 11 10:11:48 localhost kernel: [17186865.396000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jan 11 10:11:48 localhost kernel: [17186865.396000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
Jan 11 10:11:48 localhost kernel: [17186865.400000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jan 11 10:11:48 localhost kernel: [17186865.400000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
Jan 11 10:11:48 localhost kernel: [17186865.400000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
Jan 11 10:11:48 localhost kernel: [17186865.400000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jan 11 10:11:48 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.3
Jan 11 10:11:48 localhost dhclient: Copyright 2004-2005 Internet Systems Consortium.
Jan 11 10:11:48 localhost dhclient: All rights reserved.
Jan 11 10:11:48 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
Jan 11 10:11:48 localhost dhclient:
Jan 11 10:11:48 localhost kernel: [17186865.560000] ipw2200: Radio Frequency Kill Switch is On:
Jan 11 10:11:48 localhost kernel: [17186865.560000] Kill switch must be turned off for wireless networking to work.
Jan 11 10:11:48 localhost kernel: [17186865.572000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jan 11 10:11:48 localhost NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link.
Jan 11 10:11:48 localhost NetworkManager: <information>^Imatch
Jan 11 10:11:48 localhost kernel: [17186865.572000] bridge-eth0: enabling the bridge
Jan 11 10:11:48 localhost kernel: [17186865.572000] bridge-eth0: up
Jan 11 10:11:48 localhost NetworkManager: <information>^Imatch
Jan 11 10:11:48 localhost kernel: [17186865.596000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
Jan 11 10:11:51 localhost mysqld_safe[19114]: started
Jan 11 10:11:51 localhost mysqld[19118]: 070111 10:11:51  InnoDB: Started; log sequence number 0 43655
Jan 11 10:11:51 localhost mysqld[19118]: 070111 10:11:51 [Note] /usr/sbin/mysqld: ready for connections.
Jan 11 10:11:51 localhost mysqld[19118]: Version: '5.0.22-Debian_0ubuntu6.06.2-log'  socket: '/var/run/mysqld/mysqld.sock' port: 3306  Debian Etch distribution
Jan 11 10:11:51 localhost dhclient: Listening on LPF/eth0/00:03:0d:1b:65:32
Jan 11 10:11:51 localhost dhclient: Sending on   LPF/eth0/00:03:0d:1b:65:32
Jan 11 10:11:51 localhost dhclient: Sending on   Socket/fallback
Jan 11 10:11:52 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan 11 10:11:52 localhost dhclient: DHCPOFFER from 192.168.100.10
Jan 11 10:11:52 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan 11 10:11:52 localhost dhclient: DHCPACK from 192.168.100.10
Jan 11 10:11:52 localhost dhclient: bound to 192.168.100.66 -- renewal in 325726 seconds.
Jan 11 10:11:52 localhost kernel: [17186867.080000] ACPI: Power Button (FF) [PWRF]
Jan 11 10:11:52 localhost kernel: [17186867.080000] ACPI: Lid Switch [LID]
Jan 11 10:11:52 localhost kernel: [17186867.080000] ACPI: Sleep Button (CM) [SLPB]
Jan 11 10:11:52 localhost kernel: [17186867.080000] ACPI: Power Button (CM) [PWRB]
Jan 11 10:11:52 localhost kernel: [17186867.128000] ACPI: Thermal Zone [THRM] (11 C)
Jan 11 10:11:52 localhost /etc/mysql/debian-start[19172]: Running MySQL upgrade script in the background...
Jan 11 10:11:52 localhost kernel: [17186867.188000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.188000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.192000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.192000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.208000] ACPI: AC Adapter [AC0] (on-line)
Jan 11 10:11:52 localhost /etc/mysql/debian-start[19222]: This script updates all the mysql privilege tables to be usable byJan 11 10:11:52 localhost /etc/mysql/debian-start[19222]: MySQL 4.0 and above.
Jan 11 10:11:52 localhost /etc/mysql/debian-start[19222]:
Jan 11 10:11:52 localhost /etc/mysql/debian-start[19222]: This is needed if you want to use the new GRANT functions,
Jan 11 10:11:52 localhost /etc/mysql/debian-start[19222]: CREATE AGGREGATE FUNCTION, stored procedures, or
Jan 11 10:11:52 localhost /etc/mysql/debian-start[19222]: more secure passwords in 4.1
Jan 11 10:11:52 localhost /etc/mysql/debian-start[19222]:
Jan 11 10:11:52 localhost kernel: [17186867.296000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 3 times
Jan 11 10:11:52 localhost NetworkManager: <information>^Imatch
Jan 11 10:11:52 localhost NetworkManager: <information>^Imatch
Jan 11 10:11:52 localhost kernel: [17186867.300000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.300000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.308000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 3 times
Jan 11 10:11:52 localhost kernel: [17186867.312000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 3 times
Jan 11 10:11:52 localhost kernel: [17186867.316000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.316000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.320000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.320000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.324000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.324000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.328000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.328000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.332000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 3 times
Jan 11 10:11:52 localhost kernel: [17186867.336000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.336000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.344000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.344000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.348000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.348000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.352000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 3 times
Jan 11 10:11:52 localhost kernel: [17186867.356000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.356000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.404000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.404000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.408000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 5 times
Jan 11 10:11:52 localhost kernel: [17186867.412000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 3 times
Jan 11 10:11:52 localhost kernel: [17186867.420000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.420000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.424000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.424000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.432000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 3 times
Jan 11 10:11:52 localhost kernel: [17186867.436000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.436000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.440000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.440000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.440000] ACPI: Battery Slot [BAT0] (battery present)
Jan 11 10:11:52 localhost kernel: [17186867.444000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.444000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.536000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 3 times
Jan 11 10:11:52 localhost kernel: [17186867.580000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 11 times
Jan 11 10:11:52 localhost kernel: [17186867.584000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 3 times
Jan 11 10:11:52 localhost kernel: [17186867.588000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 7 times
Jan 11 10:11:52 localhost kernel: [17186867.592000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 3 times
Jan 11 10:11:52 localhost kernel: [17186867.600000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.600000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.604000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.604000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.608000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 3 times
Jan 11 10:11:52 localhost kernel: [17186867.612000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.612000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.620000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost last message repeated 3 times
Jan 11 10:11:52 localhost kernel: [17186867.624000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:52 localhost kernel: [17186867.624000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.628000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost last message repeated 3 times
Jan 11 10:11:50 localhost kernel: [17186867.632000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.632000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.640000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost last message repeated 3 times
Jan 11 10:11:50 localhost kernel: [17186867.644000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.644000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost ntpdate[19146]: step time server 82.211.81.145 offset -2.215740 sec
Jan 11 10:11:50 localhost kernel: [17186867.648000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost last message repeated 3 times
Jan 11 10:11:50 localhost kernel: [17186867.652000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.652000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.660000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost last message repeated 3 times
Jan 11 10:11:50 localhost kernel: [17186867.664000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.664000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.668000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost last message repeated 3 times
Jan 11 10:11:50 localhost kernel: [17186867.676000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.676000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.680000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost last message repeated 3 times
Jan 11 10:11:50 localhost kernel: [17186867.684000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.684000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.688000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.688000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.692000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.692000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.696000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.696000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.700000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.700000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.704000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.704000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.712000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost last message repeated 2 times
Jan 11 10:11:50 localhost kernel: [17186867.716000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.716000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.720000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost last message repeated 3 times
Jan 11 10:11:50 localhost kernel: [17186867.724000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.724000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.732000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost kernel: [17186867.732000] ohci1394: fw-host0: Unhandled interrupt(s) 0xf0000000
Jan 11 10:11:50 localhost /etc/mysql/debian-start[19222]: done

```

As far as I can tell my swap is 1.5 times the size of mem, 512mb ram 1.5GB swap. Any ideas. Hibernate will be OH SO usefull!!!!! I am running and INtel chipset on a generic laptop, here is my lspci:

```
0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:01:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Any ideas anybody, my suspend works great, from what I can tell.

---

