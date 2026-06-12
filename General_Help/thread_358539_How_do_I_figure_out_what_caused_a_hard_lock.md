---
title: "How do I figure out what caused a hard lock?"
date: 2007-02-10
forum: General Help
---

### Post by SnowPunk98 on 2007-02-10
For some reason my system seems to lock up for no real reason sometimes, it has only happened a few times, mainly when opening Firefox but is there any way to figure out what did it and fix it?

---

### Post by gradedcheese on 2007-02-11
You can look at the logs after rebooting:

/var/log/syslog.0

is one, and the numbers go up but they get compressed.  So:

sudo gunzip /var/log/syslog.1.gz
less /var/log/syslog.1

(scroll down, 'q' gets you out of 'less').  For kernel messages, it's nearly the same thing:

sudo gunzip /var/log/dmesg.1.gz
less /var/log/dmesg.1

---

### Post by teaker1s on 2007-02-11
look at system messages under desktop system tab/administation/system log

or terminal

 sudo gedit /var/log/messages
sudo gedit /var/log/syslog.0

---

### Post by SnowPunk98 on 2007-02-11
What exactly am I looking for in these logs, is there anything I can search for?

---

### Post by teaker1s on 2007-02-11
looking for errors and complaining, otherwise it should just show standard processes

---

### Post by SnowPunk98 on 2007-02-11
So my system just hard locked in Firefox again for no reason it seems. Here is part of the syslog from right before and after the system locked. I had to hold down the power button to get it to turn off. Can anyone see what caused it or how I can figure it out because it is getting kind of annoying.

```
Feb 11 17:48:47 JANEWAY NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Feb 11 17:48:47 JANEWAY NetworkManager: <information>^I  address 192.168.0.142 
Feb 11 17:48:47 JANEWAY NetworkManager: <information>^I  netmask 255.255.255.0 
Feb 11 17:48:47 JANEWAY NetworkManager: <information>^I  broadcast 192.168.0.255 
Feb 11 17:48:47 JANEWAY NetworkManager: <information>^I  gateway 192.168.0.1 
Feb 11 17:48:47 JANEWAY NetworkManager: <information>^I  nameserver 192.168.0.1 
Feb 11 17:48:47 JANEWAY NetworkManager: <information>^I  domain name 'removed by SnowPunk98' 
Feb 11 17:48:47 JANEWAY NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb 11 17:48:47 JANEWAY NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Feb 11 17:48:47 JANEWAY NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Feb 11 17:48:48 JANEWAY NetworkManager: <information>^IDHCP returned name servers but system has disabled dynamic modification! 
Feb 11 17:48:48 JANEWAY NetworkManager: <information>^IActivation (eth1) successful, device activated. 
Feb 11 17:48:48 JANEWAY NetworkManager: <information>^IActivation (eth1) Finish handler scheduled. 
Feb 11 17:48:48 JANEWAY NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Feb 11 17:48:48 JANEWAY ntpdate[11964]: step time server 82.211.81.145 offset -0.001402 sec
Feb 11 17:48:49 JANEWAY dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Feb 11 17:48:59 JANEWAY kernel: [17189258.232000] eth1: no IPv6 routers present
Feb 11 17:49:00 JANEWAY dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Feb 11 17:49:12 JANEWAY dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Feb 11 17:49:28 JANEWAY dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Feb 11 17:49:41 JANEWAY dhclient: No DHCPOFFERS received.
Feb 11 17:49:41 JANEWAY dhclient: No working leases in persistent database - sleeping.
Feb 11 17:49:41 JANEWAY ntpdate[12005]: step time server 82.211.81.145 offset -0.004769 sec
Feb 11 17:54:39 JANEWAY dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 11 17:54:46 JANEWAY dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb 11 17:54:54 JANEWAY dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Feb 11 17:55:03 JANEWAY dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Feb 11 17:56:11 JANEWAY syslogd 1.4.1#18ubuntu6: restart.
Feb 11 17:56:11 JANEWAY kernel: Inspecting /boot/System.map-2.6.17-11-generic
Feb 11 17:56:11 JANEWAY kernel: Loaded 22866 symbols from /boot/System.map-2.6.17-11-generic.
Feb 11 17:56:11 JANEWAY kernel: Symbols match kernel version 2.6.17.
Feb 11 17:56:11 JANEWAY kernel: No module symbols loaded - kernel modules not enabled. 
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] BIOS-provided physical RAM map:
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fed3400 (usable)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]  BIOS-e820: 000000003fed3400 - 0000000040000000 (reserved)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] 126MB HIGHMEM available.
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] 896MB LOWMEM available.
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] On node 0 totalpages: 261843
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000]   HighMem zone: 32467 pages, LIFO batch:7
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] DMI 2.4 present.
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc1b0
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: RSDT (v001 DELL    M07     0x27d60b11 ASL  0x00000061) @ 0x3fed39cd
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: FADT (v001 DELL    M07     0x27d60b11 ASL  0x00000061) @ 0x3fed4800
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: HPET (v001 DELL    M07     0x00000001 ASL  0x00000061) @ 0x3fed4f00
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: MADT (v001 DELL    M07     0x27d60b11 ASL  0x00000047) @ 0x3fed5000
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: MCFG (v016 DELL    M07     0x27d60b11 ASL  0x00000061) @ 0x3fed4fc0
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: SLIC (v001 DELL    M07     0x27d60b11 ASL  0x00000061) @ 0x3fed509c
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: BOOT (v001 DELL    M07     0x27d60b11 ASL  0x00000061) @ 0x3fed4bc0
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x3fed3a0d
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 INTL 0x20050624) @ 0x00000000
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x1008
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: Local APIC address 0xfee00000
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] Processor #0 6:15 APIC version 20
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] Processor #1 6:15 APIC version 20
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: IRQ0 used by override.
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: IRQ2 used by override.
Feb 11 17:56:11 JANEWAY kernel: [17179569.184000] ACPI: IRQ9 used by override.
```

---

### Post by SnowPunk98 on 2007-02-12
Anyone happen to know?

---

### Post by SnowPunk98 on 2007-02-13
Last bump on this thread

---

### Post by teaker1s on 2007-02-14
It could be firefox using all memory and causing a crash, have you tried another browser

---

### Post by SnowPunk98 on 2007-02-14
Nope, it has only happened 2 times and it hasn't happened for a while. If it does again and is in Firefox I will try another browser.

---

### Post by graigsmith on 2007-02-14
could be something simple like bios settings i noticed it was calling apic mode.  do you have apic disabled in the bios?  i was having problems with my apic mode.  it was messing with my system clock.  when i disabled it all was well.

---

