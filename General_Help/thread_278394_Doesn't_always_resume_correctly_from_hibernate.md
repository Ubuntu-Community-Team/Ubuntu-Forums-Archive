---
title: "Doesn't always resume correctly from hibernate"
date: 2006-10-16
forum: General Help
---

### Post by W. Irving on 2006-10-16
I have Dapper on my IBM T23, and it works really well. Having used DOS and Windows for over half of my life, I am amazed how stable, flexible and easy Ubuntu is in comparison.

I need help sorting out hibernation though. Hibernating in Dapper has always worked like a - eh - Breeze. Resuming is another matter, it works nine times out of ten. The tenth time Ubuntu ignores the fact that it's supposed to resume, and instead boots like it normally would! Which means I lose my work (although I'm always clever enough to save before hibernating). Gnome even remembers what windows were open last time it booted (not from the time I hibernated, but from when it started before that).

I am familiar with how ntldr works, by checking if there's a hibernation file, but the theory behind hibernation in Ubuntu is new to me so I don't know what to look for or where to start. It always appears to behave the same when hibernating, so there's no way to tell if it's going to resume or boot next time.

I'm attaching two syslog excerpts - the first is from a successful hibernate/restore, and the second from a failed such.

> Oct 16 11:58:03 localhost gnome-power-manager: Hibernating computer because the DBUS method Hibernate() was invoked
Oct 16 11:58:04 localhost postfix/master[5098]: reload configuration /etc/postfix
Oct 16 11:58:04 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.3
Oct 16 11:58:04 localhost dhclient: Copyright 2004-2005 Internet Systems Consortium.
Oct 16 11:58:04 localhost dhclient: All rights reserved.
Oct 16 11:58:04 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Oct 16 11:58:04 localhost dhclient: 
Oct 16 11:58:04 localhost dhclient: Listening on LPF/eth0/00:d0:59:bf:a6:f5
Oct 16 11:58:04 localhost dhclient: Sending on   LPF/eth0/00:d0:59:bf:a6:f5
Oct 16 11:58:04 localhost dhclient: Sending on   Socket/fallback
Oct 16 11:58:04 localhost dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Oct 16 11:58:04 localhost postfix/master[5098]: reload configuration /etc/postfix
Oct 16 11:58:05 localhost mysqld[5673]: 061016 11:58:05 [Note] /usr/sbin/mysqld: Normal shutdown
Oct 16 11:58:05 localhost mysqld[5673]: 
Oct 16 11:58:07 localhost mysqld[5673]: 061016 11:58:07  InnoDB: Starting shutdown...
Oct 16 11:58:10 localhost mysqld[5673]: 061016 11:58:10  InnoDB: Shutdown completed; log sequence number 0 7829236
Oct 16 11:58:10 localhost mysqld[5673]: 061016 11:58:10 [Note] /usr/sbin/mysqld: Shutdown complete
Oct 16 11:58:10 localhost mysqld[5673]: 
Oct 16 11:58:10 localhost mysqld_safe[10400]: ended
Oct 16 11:58:10 localhost kernel: [17444146.596000] ACPI: PCI interrupt for device 0000:02:08.0 disabled
Oct 16 13:26:42 localhost kernel: [17444149.444000] Stopping tasks: ============================================================================================================|
Oct 16 13:26:42 localhost kernel: [17444149.444000] Shrinking memory...  ^H-^H\^Hdone (17432 pages freed)
Oct 16 13:26:42 localhost kernel: [17444152.616000] ACPI: PCI interrupt for device 0000:02:00.1 disabled
Oct 16 13:26:42 localhost kernel: [17444152.616000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Oct 16 13:26:42 localhost kernel: [17444152.616000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
Oct 16 13:26:42 localhost kernel: [17444152.616000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Oct 16 13:26:42 localhost kernel: [17444152.616000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Oct 16 13:26:42 localhost kernel: [17444152.616000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Oct 16 13:26:42 localhost kernel: [17444152.616000] swsusp: Need to copy 54371 pages
Oct 16 13:26:42 localhost kernel: [17444152.616000] swsusp: Restoring Highmem
Oct 16 13:26:42 localhost kernel: [17449458.616000] **** SET: Misaligned resource pointer: cc3abde2 Type 07 Len 0
Oct 16 13:26:42 localhost last message repeated 4 times
Oct 16 13:26:42 localhost kernel: [17449458.680000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Oct 16 13:26:42 localhost kernel: [17449458.680000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Oct 16 13:26:42 localhost kernel: [17449458.680000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 16 13:26:42 localhost kernel: [17449458.680000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Oct 16 13:26:42 localhost kernel: [17449458.680000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Oct 16 13:26:42 localhost kernel: [17449458.680000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Oct 16 13:26:42 localhost kernel: [17449458.680000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Oct 16 13:26:42 localhost kernel: [17449458.680000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Oct 16 13:26:42 localhost kernel: [17449458.680000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 16 13:26:42 localhost kernel: [17449458.680000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Oct 16 13:26:42 localhost kernel: [17449459.040000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Oct 16 13:26:42 localhost kernel: [17449459.040000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Oct 16 13:26:42 localhost kernel: [17449459.040000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Oct 16 13:26:42 localhost kernel: [17449459.040000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Oct 16 13:26:42 localhost kernel: [17449459.436000] Restarting tasks... done

The failed one, shortened since it included several hundred more lines added 14:13:08

> Oct 16 13:48:46 localhost gnome-power-manager: Hibernating computer because the DBUS method Hibernate() was invoked
Oct 16 13:48:47 localhost postfix/master[5098]: reload configuration /etc/postfix
Oct 16 13:48:47 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.3
Oct 16 13:48:47 localhost dhclient: Copyright 2004-2005 Internet Systems Consortium.
Oct 16 13:48:47 localhost dhclient: All rights reserved.
Oct 16 13:48:47 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Oct 16 13:48:47 localhost dhclient: 
Oct 16 13:48:47 localhost dhclient: Listening on LPF/eth0/00:d0:59:bf:a6:f5
Oct 16 13:48:47 localhost dhclient: Sending on   LPF/eth0/00:d0:59:bf:a6:f5
Oct 16 13:48:47 localhost dhclient: Sending on   Socket/fallback
Oct 16 13:48:47 localhost dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Oct 16 13:48:47 localhost dhclient: send_packet: Network is unreachable
Oct 16 13:48:47 localhost dhclient: send_packet: please consult README file regarding broadcast address.
Oct 16 13:48:47 localhost postfix/master[5098]: reload configuration /etc/postfix
Oct 16 13:48:48 localhost mysqld[10880]: 061016 13:48:48 [Note] /usr/sbin/mysqld: Normal shutdown
Oct 16 13:48:48 localhost mysqld[10880]: 
Oct 16 13:48:50 localhost mysqld[10880]: 061016 13:48:50  InnoDB: Starting shutdown...
Oct 16 13:48:53 localhost mysqld[10880]: 061016 13:48:53  InnoDB: Shutdown completed; log sequence number 0 7829246
Oct 16 13:48:53 localhost mysqld[10880]: 061016 13:48:53 [Note] /usr/sbin/mysqld: Shutdown complete
Oct 16 13:48:53 localhost mysqld[10880]: 
Oct 16 13:48:53 localhost mysqld_safe[12232]: ended
Oct 16 13:48:54 localhost kernel: [17450791.776000] ACPI: PCI interrupt for device 0000:02:08.0 disabled
Oct 16 14:13:07 localhost syslogd 1.4.1#17ubuntu7: restart.
Oct 16 14:13:07 localhost kernel: Inspecting /boot/System.map-2.6.15-27-386
Oct 16 14:13:08 localhost kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Oct 16 14:13:08 localhost kernel: Symbols match kernel version 2.6.15.
Oct 16 14:13:08 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Oct 16 14:13:08 localhost kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
Oct 16 14:13:08 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
Oct 16 14:13:08 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Oct 16 14:13:08 localhost kernel: [17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Oct 16 14:13:08 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Oct 16 14:13:08 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
Oct 16 14:13:08 localhost kernel: [17179569.184000]  BIOS-e820: 000000001ff70000 - 000000001ff7e000 (ACPI data)
Oct 16 14:13:08 localhost kernel: [17179569.184000]  BIOS-e820: 000000001ff7e000 - 000000001ff80000 (ACPI NVS)
Oct 16 14:13:08 localhost kernel: [17179569.184000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
Oct 16 14:13:08 localhost kernel: [17179569.184000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Oct 16 14:13:08 localhost kernel: [17179569.184000] 0MB HIGHMEM available.
Oct 16 14:13:08 localhost kernel: [17179569.184000] 511MB LOWMEM available.

Help? :)

---

