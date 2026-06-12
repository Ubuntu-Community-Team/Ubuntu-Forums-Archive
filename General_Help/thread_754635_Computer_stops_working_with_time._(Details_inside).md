---
title: "Computer stops working with time. (Details inside)"
date: 2008-04-14
forum: General Help
---

### Post by Mamsaac on 2008-04-14
Ok, I've looked everywhere (or at least I think so). This is what happens:

My laptop is a Dell Inspiron 1520, with Intel Graphics (which I seriously doubt is the problem) and intel wireless 3945 (which I believe is closely related to the issue). I'm using "Intel PRO/Wireless 3945 Network Connection driver for Linux" driver.

Anyway, here is how this goes:

I'm all perfect enjoying of Ubuntu Gutsy, when my Internet disconnects. Then, when I try to reconnect it can't do so and the animation of network manager freezes. After that happens, I cannot open any application or even restart/shut down my laptop. I have to do a hard reset (turn off by pressing the power button until it shuts down).

Ok, so, if I have System Monitor opened, it stops working after this problem happens. I don't know where I can grab error logs, so, if they matter or might be helpful, I will provide them.

Any other detail I can provide, I will do so. Thanks in advance for all the help.

---

### Post by Agent Graves on 2008-04-14
This sounds like a classic RAM problem to me. I would start troubleshooting that first. How much RAM should be in your laptop?

---

### Post by sekinto on 2008-04-14
As much as I would love to support the native Linux driver, some network drivers for Linux are just glitchy. I had a laptop that was glitchy when using a Linux network driver. I used ndiswrapper and the XP driver and everything worked fine. Although if there is another way to fix your issue I'd suggest doing that instead, I'd wait for more replies.

---

### Post by ayoli on 2008-04-14
Main logs to watch are /var/syslog and .xsesion-errors.
Is your system up to date ? I had a 100% cpu issue with network manager and a PRO/Wireless 3945 using linux module, but after some upgrade the issue was solved.

---

### Post by Mamsaac on 2008-04-14
> Re: Computer stops working with time. (Details inside)
This sounds like a classic RAM problem to me. I would start troubleshooting that first. How much RAM should be in your laptop?

I have 2GB of RAM. The system detects all RAM perfectly. I already tested the RAM memory using programs I got installed and it came out clear.

> Re: Computer stops working with time. (Details inside)
As much as I would love to support the native Linux driver, some network drivers for Linux are just glitchy. I had a laptop that was glitchy when using a Linux network driver. I used ndiswrapper and the XP driver and everything worked fine. Although if there is another way to fix your issue I'd suggest doing that instead, I'd wait for more replies.

Using ndiswrapper sounds as a very possible idea. I got Vista's drivers, I don't know if they will work with ndiswrapper, but I'm sure I can find XP drivers... I will consider :) thanks

> Re: Computer stops working with time. (Details inside)
Main logs to watch are /var/syslog and .xsesion-errors.
Is your system up to date ? I had a 100% cpu issue with network manager and a PRO/Wireless 3945 using linux module, but after some upgrade the issue was solved.

Yes, it is up to date. Here are my logs:

```
Apr 13 17:41:24 mamsaac-laptop syslogd 1.4.1#21ubuntu3: restart.
Apr 13 17:41:24 mamsaac-laptop anacron[8055]: Job `cron.daily' terminated (mailing output)
Apr 13 17:41:24 mamsaac-laptop anacron[8055]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Apr 13 17:45:05 mamsaac-laptop anacron[8055]: Job `cron.weekly' started
Apr 13 17:45:05 mamsaac-laptop anacron[8519]: Updated timestamp for job `cron.weekly' to 2008-04-13
Apr 13 17:45:07 mamsaac-laptop syslogd 1.4.1#21ubuntu3: restart.
Apr 13 17:45:07 mamsaac-laptop anacron[8055]: Job `cron.weekly' terminated
Apr 13 17:45:07 mamsaac-laptop anacron[8055]: Normal exit (2 jobs run)
Apr 13 17:46:42 mamsaac-laptop kernel: [ 8529.292000] ipw3945: Error sending cmd #07 to daemon: time out after 500ms.
Apr 13 17:46:44 mamsaac-laptop kernel: [ 8530.892000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
Apr 13 17:46:44 mamsaac-laptop kernel: [ 8531.392000] ipw3945: Error sending cmd #08 to daemon: time out after 500ms.
Apr 13 17:46:45 mamsaac-laptop kernel: [ 8531.892000] ipw3945: Error sending ADD_STA: time out after 500ms.
Apr 13 17:46:45 mamsaac-laptop kernel: [ 8532.392000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
Apr 13 17:46:49 mamsaac-laptop kernel: [ 8535.928000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Apr 13 17:47:05 mamsaac-laptop NetworkManager: <info>  eth1: link timed out. 
Apr 13 17:47:05 mamsaac-laptop NetworkManager: <info>  SWITCH: found better connection 'eth1/Veracruz' than current connection 'eth1/Veracruz'.  same_ssid=1, have_link=0 
Apr 13 17:47:05 mamsaac-laptop NetworkManager: <info>  Will activate connection 'eth1/Veracruz'. 
Apr 13 17:47:05 mamsaac-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Apr 13 17:47:05 mamsaac-laptop NetworkManager: <info>  Deactivating device eth1. 
Apr 13 17:47:05 mamsaac-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6572
Apr 13 17:47:05 mamsaac-laptop dhclient: killed old client process, removed PID file
Apr 13 17:47:06 mamsaac-laptop dhclient: DHCPRELEASE on eth1 to 192.168.0.1 port 67
Apr 13 17:47:06 mamsaac-laptop avahi-daemon[5933]: Withdrawing address record for 192.168.0.4 on eth1.
Apr 13 17:47:06 mamsaac-laptop avahi-daemon[5933]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.4.
Apr 13 17:47:06 mamsaac-laptop avahi-daemon[5933]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 13 17:47:06 mamsaac-laptop NetworkManager: <info>  Activation (eth1) started... 
Apr 13 17:47:06 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 13 17:47:06 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Apr 13 17:47:06 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Apr 13 17:47:06 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Apr 13 17:47:06 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Apr 13 17:47:06 mamsaac-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Veracruz' is encrypted, and a key exists.  No new key needed. 
Apr 13 17:47:06 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Apr 13 17:47:06 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface eth1 
Apr 13 17:47:06 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Apr 13 17:47:07 mamsaac-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Apr 13 17:47:07 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant7^I' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: response was '0' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 566572616372757a' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 17:47:08 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Apr 13 17:47:44 mamsaac-laptop kernel: [ 8591.392000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Apr 13 17:47:45 mamsaac-laptop kernel: [ 8591.892000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Apr 13 17:47:46 mamsaac-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Apr 13 17:48:18 mamsaac-laptop last message repeated 16 times
Apr 13 17:49:06 mamsaac-laptop last message repeated 24 times
Apr 13 17:49:08 mamsaac-laptop NetworkManager: <info>  Activation (eth1/wireless): association took too long (>120s), asking for new key. 
Apr 13 17:49:08 mamsaac-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Veracruz'. 
Apr 13 17:49:08 mamsaac-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_get_essid(): error getting ESSID for device eth1: Resource temporarily unavailable 
Apr 13 17:49:22 mamsaac-laptop last message repeated 7 times
Apr 13 17:49:22 mamsaac-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Veracruz' received. 
Apr 13 17:49:22 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 13 17:49:22 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Apr 13 17:49:22 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Apr 13 17:49:22 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Apr 13 17:49:22 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Apr 13 17:49:22 mamsaac-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Veracruz' is encrypted, and a key exists.  No new key needed. 
Apr 13 17:49:23 mamsaac-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Apr 13 17:49:23 mamsaac-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Apr 13 17:49:23 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant8^I' 
Apr 13 17:49:35 mamsaac-laptop NetworkManager: <info>  SUP: response was 'TIMEOUT[CLI]' 
Apr 13 17:49:35 mamsaac-laptop NetworkManager: <WARN>  nm_utils_supplicant_request_with_check(): supplicant_interface_init: supplicant error for 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant8^I'.  Response: 'TIMEOUT[CLI]' 
Apr 13 17:49:35 mamsaac-laptop NetworkManager: <WARN>  real_act_stage2_config(): Activation (eth1/wireless): couldn't connect to the supplicant. 
Apr 13 17:49:35 mamsaac-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Apr 13 17:49:35 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Apr 13 17:49:35 mamsaac-laptop NetworkManager: <info>  Activation (eth1) failed for access point (Veracruz) 
Apr 13 17:49:35 mamsaac-laptop NetworkManager: <info>  Activation (eth1) failed. 
Apr 13 17:49:35 mamsaac-laptop NetworkManager: <info>  Deactivating device eth1. 
Apr 13 17:50:00 mamsaac-laptop gnome-power-manager: (mamsaac) Salida interactiva de GNOME porque se ha pulsado el botón de encendido
Apr 13 19:18:23 mamsaac-laptop syslogd 1.4.1#21ubuntu3: restart.
Apr 13 19:18:23 mamsaac-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Apr 13 19:18:24 mamsaac-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Apr 13 19:18:24 mamsaac-laptop kernel: Symbols match kernel version 2.6.22.
Apr 13 19:18:24 mamsaac-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f692400 (usable)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]  BIOS-e820: 000000007f692400 - 0000000080000000 (reserved)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] 1142MB HIGHMEM available.
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] 896MB LOWMEM available.
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 521874) 0 entries of 256 used
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Zone PFN ranges:
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]   DMA             0 ->     4096
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]   HighMem    229376 ->   521874
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]     0:        0 ->   521874
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] On node 0 totalpages: 521874
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]   HighMem zone: 2285 pages used for memmap
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000]   HighMem zone: 290213 pages, LIFO batch:31
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] DMI 2.4 present.
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FBBF0 checksum 0
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: RSDP 000FBBF0, 0024 (r2 DELL  )
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: XSDT 7F693E00, 005C (r1 DELL    M08     27D70510 ASL        61)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: FACP 7F693C9C, 00F4 (r4 DELL    M08     27D70510 ASL        61)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: DSDT 7F694400, 560B (r2 INT430 SYSFexxx     1001 INTL 20050624)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: FACS 7F6A2C00, 0040
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: HPET 7F693F00, 0038 (r1 DELL    M08            1 ASL        61)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: APIC 7F694000, 0068 (r1 DELL    M08     27D70510 ASL        47)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: MCFG 7F693FC0, 003E (r16 DELL    M08     27D70510 ASL        61)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: SLIC 7F69409C, 0176 (r1 DELL    M08     27D70510 ASL        61)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: BOOT 7F693BC0, 0028 (r1 DELL    M08     27D70510 ASL        61)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: SSDT 7F6926EB, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:78000000)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Built 1 zonelists.  Total pages: 517797
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Kernel command line: root=UUID=129c410f-4e08-4ec5-a341-8d996b8221bf ro quiet splash
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Initializing CPU#0
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 13 19:18:24 mamsaac-laptop kernel: [    0.000000] Detected 1994.607 MHz processor.
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.048398] Console: colour VGA+ 80x25
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.048701] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.048986] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117675] Memory: 2058164k/2087496k available (2015k kernel code, 28116k reserved, 915k data, 364k init, 1169992k highmem)
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117682] virtual kernel memory layout:
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117683]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117684]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117685]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117686]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117687]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117688]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117689]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117692] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117724] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117850] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.117855] hpet0: 3 64-bit timers, 14318180 Hz
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198806] Calibrating delay using timer specific routine.. 3993.35 BogoMIPS (lpj=7986712)
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198826] Security Framework v1.0.0 initialized
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198831] SELinux:  Disabled at boot.
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198842] Mount-cache hash table entries: 512
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198953] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198960] monitor/mwait feature present.
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198961] using mwait in idle threads.
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198965] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198968] CPU: L2 cache: 4096K
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198970] CPU: Physical Processor ID: 0
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198971] CPU: Processor Core ID: 0
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198973] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198981] Compat vDSO mapped to ffffe000.
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.198992] Checking 'hlt' instruction... OK.
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.214885] SMP alternatives: switching to UP code
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.215249] Early unpacking initramfs... done
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.489971] ACPI: Core revision 20070126
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.490008] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.493369] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.493383] SMP alternatives: switching to SMP code
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.493443] Booting processor 1/1 eip 3000
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.503844] Initializing CPU#1
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.582477] Calibrating delay using timer specific routine.. 3988.89 BogoMIPS (lpj=7977781)
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.582482] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.582486] monitor/mwait feature present.
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.582489] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.582491] CPU: L2 cache: 4096K
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.582492] CPU: Physical Processor ID: 0
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.582494] CPU: Processor Core ID: 1
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.582495] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.583227] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.583249] Total of 2 processors activated (7982.24 BogoMIPS).
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.583446] ENABLING IO-APIC IRQs
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.583644] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.730430] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.750427] Brought up 2 CPUs
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.991342] migration_cost=21
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.991448] Booting paravirtualized kernel on bare hardware
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.991532] Time: 19:17:58  Date: 03/13/108
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.991548] NET: Registered protocol family 16
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.991615] EISA bus registered
Apr 13 19:18:24 mamsaac-laptop kernel: [    8.991619] ACPI: bus type pci registered
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.002184] PCI: PCI BIOS revision 2.10 entry at 0xfad46, last bus=14
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.002185] PCI: Using configuration type 1
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.002187] Setting up standard PCI resources
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.009345] ACPI: EC: Look up EC in DSDT
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.044661] ACPI: Interpreter enabled
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.044664] ACPI: (supports S0 S3 S4 S5)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.044677] ACPI: Using IOAPIC for interrupt routing
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.064714] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.064727] PCI: Probing PCI hardware (bus 00)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.066868] PCI: Transparent bridge - 0000:00:1e.0
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.066944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.067338] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.067475] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.067581] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.067685] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.077815] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.077917] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.078017] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.078140] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.078241] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.078343] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.078444] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.078537] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.078649] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.078657] pnp: PnP ACPI init
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.078664] ACPI: bus type pnp registered
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.114745] pnp: PnP ACPI: found 12 devices
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.114747] ACPI: ACPI bus type pnp unregistered
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.114750] PnPBIOS: Disabled by ACPI PNP
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.114785] PCI: Using ACPI for IRQ routing
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.114787] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174219] NET: Registered protocol family 8
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174221] NET: Registered protocol family 20
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174271] pnp: 00:05: ioport range 0xc80-0xcff could not be reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174278] pnp: 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174282] pnp: 00:09: ioport range 0x900-0x97f has been reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174284] pnp: 00:09: ioport range 0x4d0-0x4d1 has been reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174286] pnp: 00:09: ioport range 0x1000-0x1005 has been reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174289] pnp: 00:09: ioport range 0x1008-0x100f has been reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174293] pnp: 00:0a: ioport range 0xf400-0xf4fe has been reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174295] pnp: 00:0a: ioport range 0x1006-0x1007 has been reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174298] pnp: 00:0a: ioport range 0x100a-0x1059 could not be reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174300] pnp: 00:0a: ioport range 0x1060-0x107f has been reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174302] pnp: 00:0a: ioport range 0x1080-0x10bf has been reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174304] pnp: 00:0a: ioport range 0x10c0-0x10df has been reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174307] pnp: 00:0a: ioport range 0x1010-0x102f has been reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174311] pnp: 00:0b: iomem range 0x0-0x9efff could not be reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174313] pnp: 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174316] pnp: 00:0b: iomem range 0xc0000-0xcffff could not be reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.174318] pnp: 00:0b: iomem range 0xe0000-0xfffff could not be reserved
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.177978] Time: tsc clocksource has been installed.
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.177990] Switched to high resolution mode on CPU 0
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.178060] Switched to high resolution mode on CPU 1
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204546] PCI: Bridge: 0000:00:1c.0
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204547]   IO window: disabled.
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204553]   MEM window: disabled.
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204557]   PREFETCH window: disabled.
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204563] PCI: Bridge: 0000:00:1c.1
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204564]   IO window: disabled.
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204570]   MEM window: fe800000-fe8fffff
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204574]   PREFETCH window: disabled.
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204580] PCI: Bridge: 0000:00:1c.3
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204583]   IO window: d000-dfff
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204589]   MEM window: fe600000-fe7fffff
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204593]   PREFETCH window: f0000000-f01fffff
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204600] PCI: Bridge: 0000:00:1e.0
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204601]   IO window: disabled.
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204607]   MEM window: fe500000-fe5fffff
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204611]   PREFETCH window: disabled.
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204640] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204646] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204670] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204676] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204700] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204706] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204720] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.204729] NET: Registered protocol family 2
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.249889] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.249936] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.250456] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.250635] TCP: Hash tables configured (established 131072 bind 65536)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.250638] TCP reno registered
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.265964] checking if image is initramfs... it is
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.807555] Freeing initrd memory: 7059k freed
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.807654] Simple Boot Flag at 0x79 set to 0x1
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.808044] audit: initializing netlink socket (disabled)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.808057] audit(1208114278.436:1): initialized
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.808138] highmem bounce pool size: 64 pages
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.809667] VFS: Disk quotas dquot_6.5.1
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.809705] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.809781] io scheduler noop registered
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.809783] io scheduler anticipatory registered
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.809785] io scheduler deadline registered
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.809795] io scheduler cfq registered (default)
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.809809] Boot video device is 0000:00:02.0
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810006] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810065] assign_interrupt_mode Found MSI capability
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810068] Allocate Port Service[0000:00:1c.0:pcie00]
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810097] Allocate Port Service[0000:00:1c.0:pcie02]
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810192] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810251] assign_interrupt_mode Found MSI capability
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810253] Allocate Port Service[0000:00:1c.1:pcie00]
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810276] Allocate Port Service[0000:00:1c.1:pcie02]
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810373] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810431] assign_interrupt_mode Found MSI capability
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810433] Allocate Port Service[0000:00:1c.3:pcie00]
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810457] Allocate Port Service[0000:00:1c.3:pcie02]
Apr 13 19:18:24 mamsaac-laptop kernel: [    9.810602] isapnp: Scanning for PnP cards...
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.164289] isapnp: No Plug & Play device found
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.180406] Real Time Clock Driver v1.12ac
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.180526] hpet_resources: 0xfed00000 is busy
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.180582] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.181426] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.181529] input: Macintosh mouse button emulation as /class/input/input0
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.181591] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.184763] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.184767] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.184887] mice: PS/2 mouse device common for all mice
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.184975] EISA: Probing bus 0 at eisa.0
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.184984] Cannot allocate resource for EISA slot 1
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.185015] EISA: Detected 0 cards.
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.185078] TCP cubic registered
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.185088] NET: Registered protocol family 1
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.185105] Using IPI No-Shortcut mode
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.185254]   Magic number: 4:698:293
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.185261]   hash matches device ttyz7
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.185265]   hash matches device ttywa
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.185298]   hash matches device tty26
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.185491] Freeing unused kernel memory: 364k freed
Apr 13 19:18:24 mamsaac-laptop kernel: [   10.188606] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.358099] AppArmor: AppArmor initialized<5>audit(1208114279.936:2):  type=1505 info="AppArmor initialized" pid=1268
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.364413] fuse init (API version 7.8)
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.367928] Failure registering capabilities with primary security module.
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.394866] ACPI: SSDT 7F6930F2, 0286 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.395039] ACPI: SSDT 7F692BB7, 04B6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.395273] Monitor-Mwait will be used to enter C-1 state
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.395276] Monitor-Mwait will be used to enter C-2 state
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.395278] Monitor-Mwait will be used to enter C-3 state
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.395282] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.395285] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.395458] ACPI: SSDT 7F693378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.395615] ACPI: SSDT 7F69306D, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.395880] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 13 19:18:24 mamsaac-laptop kernel: [   11.395885] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.156000] Marking TSC unstable due to: possible TSC halt in C2.
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.160000] Time: hpet clocksource has been installed.
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.160000] ACPI: Thermal Zone [THM] (51 C)
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.532000] usbcore: registered new interface driver usbfs
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.532000] usbcore: registered new interface driver hub
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.532000] usbcore: registered new device driver usb
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.536000] USB Universal Host Controller Interface driver v3.0
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.536000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 19
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.536000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.536000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.536000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.536000] uhci_hcd 0000:00:1a.0: irq 19, io base 0x00006f20
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.536000] usb usb1: configuration #1 chosen from 1 choice
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.536000] hub 1-0:1.0: USB hub found
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.536000] hub 1-0:1.0: 2 ports detected
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.612000] SCSI subsystem initialized
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.616000] libata version 2.21 loaded.
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.640000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.640000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.640000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.640000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.640000] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00006f00
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.640000] usb usb2: configuration #1 chosen from 1 choice
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.640000] hub 2-0:1.0: USB hub found
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.640000] hub 2-0:1.0: 2 ports detected
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.744000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.744000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.744000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.744000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.744000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00006f80
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.744000] usb usb3: configuration #1 chosen from 1 choice
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.744000] hub 3-0:1.0: USB hub found
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.744000] hub 3-0:1.0: 2 ports detected
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.860000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.860000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.860000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.860000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.860000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00006f60
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.860000] usb usb4: configuration #1 chosen from 1 choice
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.860000] hub 4-0:1.0: USB hub found
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.860000] hub 4-0:1.0: 2 ports detected
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.916000] usb 1-2: new full speed USB device using uhci_hcd and address 2
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.980000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.980000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.980000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.980000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.980000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00006f40
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.980000] usb usb5: configuration #1 chosen from 1 choice
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.980000] hub 5-0:1.0: USB hub found
Apr 13 19:18:24 mamsaac-laptop kernel: [    3.980000] hub 5-0:1.0: 2 ports detected
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.000000] Clocksource tsc unstable (delta = -282427289 ns)
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.084000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 21
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.084000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.084000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.084000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.084000] ehci_hcd 0000:00:1a.7: debug port 1
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.084000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.084000] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xfed1c400
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.088000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.088000] usb usb6: configuration #1 chosen from 1 choice
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.088000] hub 6-0:1.0: USB hub found
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.088000] hub 6-0:1.0: 4 ports detected
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.096000] usb 1-2: unable to read config index 0 descriptor/start
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.096000] usb 1-2: chopping to 0 config(s)
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.104000] usb 1-2: string descriptor 0 read error: -71
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.112000] usb 1-2: string descriptor 0 read error: -71
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.112000] usb 1-2: no configuration chosen from 0 choices
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.192000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.192000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.192000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.192000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.192000] ehci_hcd 0000:00:1d.7: debug port 1
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.192000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.192000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfed1c000
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.196000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.196000] usb usb7: configuration #1 chosen from 1 choice
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.196000] hub 7-0:1.0: USB hub found
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.196000] hub 7-0:1.0: 6 ports detected
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.300000] ahci 0000:00:1f.2: version 2.2
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.300000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.300000] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.336000] usb 1-2: USB disconnect, address 2
Apr 13 19:18:24 mamsaac-laptop kernel: [    4.944000] usb 7-6: new high speed USB device using ehci_hcd and address 2
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.080000] usb 7-6: configuration #1 chosen from 1 choice
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.304000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.304000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.304000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.304000] scsi0 : ahci
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.304000] scsi1 : ahci
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.304000] scsi2 : ahci
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.304000] ata1: SATA max UDMA/133 cmd 0xf8862900 ctl 0x00000000 bmdma 0x00000000 irq 17
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.304000] ata2: DUMMY
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.304000] ata3: SATA max UDMA/133 cmd 0xf8862a00 ctl 0x00000000 bmdma 0x00000000 irq 17
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.332000] usb 1-2: new full speed USB device using uhci_hcd and address 3
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.560000] usb 1-2: configuration #1 chosen from 1 choice
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.564000] hub 1-2:1.0: USB hub found
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.564000] hub 1-2:1.0: 3 ports detected
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.788000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.788000] ata1.00: ATA-7: ST9160821AS, 3.CDD, max UDMA/133
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.788000] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.796000] ata1.00: configured for UDMA/133
Apr 13 19:18:24 mamsaac-laptop kernel: [    5.876000] usb 1-2.1: new full speed USB device using uhci_hcd and address 4
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.000000] usb 1-2.1: configuration #1 chosen from 1 choice
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.112000] ata3: SATA link down (SStatus 0 SControl 300)
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.112000] scsi 0:0:0:0: Direct-Access     ATA      ST9160821AS      3.CD PQ: 0 ANSI: 5
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.112000] b44.c:v1.01 (Jun 16, 2006)
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.112000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.116000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:19:b9:85:ab:e9
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.116000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.168000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fe5fd800-fe5fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.172000] ata_piix 0000:00:1f.1: version 2.11
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.172000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.172000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.172000] scsi3 : ata_piix
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.172000] scsi4 : ata_piix
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.172000] ata4: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00016fa0 irq 14
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.172000] ata5: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00016fa8 irq 15
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.176000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.176000] sd 0:0:0:0: [sda] Write Protect is off
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.176000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.176000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.176000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.176000] sd 0:0:0:0: [sda] Write Protect is off
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.176000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.176000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.176000]  sda: sda1 sda2 sda3 <<6>usb 1-2.2: new full speed USB device using uhci_hcd and address 5
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.244000]  sda5 sda6 sda7 sda8 >
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.284000] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.288000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.364000] usb 1-2.2: configuration #1 chosen from 1 choice
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.492000] ata4.00: ATAPI: SONY CD-RW/DVD-ROM CRX880A, KD09, max UDMA/33
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.572000] usb 1-2.3: new full speed USB device using uhci_hcd and address 6
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.664000] ata4.00: configured for UDMA/33
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.664000] ata5: port disabled. ignoring.
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.664000] scsi 3:0:0:0: CD-ROM            SONY     CDRWDVD CRX880A  KD09 PQ: 0 ANSI: 5
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.664000] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.668000] Attempting manual resume
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.668000] swsusp: Resume From Partition 8:7
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.668000] PM: Checking swsusp image.
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.668000] PM: Resume from disk failed.
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.680000] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.680000] EXT3-fs: write access will be enabled during recovery.
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.680000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.680000] Uniform CD-ROM driver Revision: 3.20
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.680000] sr 3:0:0:0: Attached scsi CD-ROM sr0
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.700000] usb 1-2.3: configuration #1 chosen from 1 choice
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.708000] usbcore: registered new interface driver hiddev
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.708000] input: Broadcom Corp as /class/input/input2
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.708000] input: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.716000] input: Broadcom Corp as /class/input/input3
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.716000] input: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.716000] usbcore: registered new interface driver usbhid
Apr 13 19:18:24 mamsaac-laptop kernel: [    6.716000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Apr 13 19:18:24 mamsaac-laptop kernel: [    7.272000] kjournald starting.  Commit interval 5 seconds
Apr 13 19:18:24 mamsaac-laptop kernel: [    7.272000] EXT3-fs: sda6: orphan cleanup on readonly fs
Apr 13 19:18:24 mamsaac-laptop kernel: [    7.444000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[374fc00015a53181]
Apr 13 19:18:24 mamsaac-laptop kernel: [    7.456000] ext3_orphan_cleanup: deleting unreferenced inode 669474
Apr 13 19:18:24 mamsaac-laptop kernel: [    7.456000] ext3_orphan_cleanup: deleting unreferenced inode 406408
Apr 13 19:18:24 mamsaac-laptop kernel: [    7.456000] ext3_orphan_cleanup: deleting unreferenced inode 406407
Apr 13 19:18:24 mamsaac-laptop kernel: [    7.456000] ext3_orphan_cleanup: deleting unreferenced inode 406406
Apr 13 19:18:24 mamsaac-laptop kernel: [    7.456000] ext3_orphan_cleanup: deleting unreferenced inode 406405
Apr 13 19:18:24 mamsaac-laptop kernel: [    7.456000] ext3_orphan_cleanup: deleting unreferenced inode 406402
Apr 13 19:18:24 mamsaac-laptop kernel: [    7.456000] EXT3-fs: sda6: 6 orphan inodes deleted
Apr 13 19:18:24 mamsaac-laptop kernel: [    7.456000] EXT3-fs: recovery complete.
Apr 13 19:18:24 mamsaac-laptop kernel: [    7.456000] EXT3-fs: mounted filesystem with ordered data mode.
Apr 13 19:18:24 mamsaac-laptop kernel: [   15.912000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 13 19:18:24 mamsaac-laptop kernel: [   15.936000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 13 19:18:24 mamsaac-laptop kernel: [   15.984000] Linux agpgart interface v0.102 (c) Dave Jones
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.044000] agpgart: Detected an Intel 965GM Chipset.
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.044000] agpgart: Detected 7676K stolen memory.
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.056000] agpgart: AGP aperture is 256M @ 0xe0000000
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.352000] input: PC Speaker as /class/input/input4
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.396000] Bluetooth: Core ver 2.11
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.396000] NET: Registered protocol family 31
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.396000] Bluetooth: HCI device and connection manager initialized
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.396000] Bluetooth: HCI socket layer initialized
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.416000] Linux video capture interface: v2.00
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.460000] ieee80211_crypt: registered algorithm 'NULL'
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.460000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.460000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.476000] sdhci: Secure Digital Host Controller Interface driver
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.476000] sdhci: Copyright(c) Pierre Ossman
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.476000] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 22)
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.476000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.476000] mmc0: SDHCI at 0xfe5fd400 irq 22 DMA
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.560000] Bluetooth: HCI USB driver ver 2.9
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.568000] usbcore: registered new interface driver hci_usb
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.592000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.592000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.592000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.592000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.592000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.628000] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.628000] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.684000] usbcore: registered new interface driver uvcvideo
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.684000] USB Video Class driver (v0.1.0)
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.724000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04793/0x300000
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.724000] serio: Synaptics pass-through port at isa0060/serio1/input0
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.760000] input: SynPS/2 Synaptics TouchPad as /class/input/input5
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.844000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
Apr 13 19:18:24 mamsaac-laptop kernel: [   16.844000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 13 19:18:24 mamsaac-laptop kernel: [   17.476000] lp: driver loaded but no devices found
Apr 13 19:18:24 mamsaac-laptop kernel: [   17.600000] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.1.0
Apr 13 19:18:24 mamsaac-laptop kernel: [   17.600000] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Apr 13 19:18:24 mamsaac-laptop kernel: [   17.636000] Adding 530104k swap on /dev/sda7.  Priority:-1 extents:1 across:530104k
Apr 13 19:18:24 mamsaac-laptop kernel: [   18.096000] EXT3 FS on sda6, internal journal
Apr 13 19:18:24 mamsaac-laptop kernel: [   18.576000] ata1.00: exception Emask 0x2 SAct 0x4 SErr 0x0 action 0x2 frozen
Apr 13 19:18:24 mamsaac-laptop kernel: [   18.576000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x4 FIS=004040a1:00000001)
Apr 13 19:18:24 mamsaac-laptop kernel: [   18.576000] ata1.00: cmd 60/fe:10:29:b1:da/00:00:03:00:00/40 tag 2 cdb 0x0 data 130048 in
Apr 13 19:18:24 mamsaac-laptop kernel: [   18.576000]          res 40/00:10:29:b1:da/00:00:03:00:00/40 Emask 0x2 (HSM violation)
Apr 13 19:18:24 mamsaac-laptop kernel: [   18.588000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Apr 13 19:18:24 mamsaac-laptop kernel: [   18.892000] ata1: soft resetting port
Apr 13 19:18:24 mamsaac-laptop kernel: [   19.064000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 13 19:18:24 mamsaac-laptop kernel: [   19.068000] ata1.00: configured for UDMA/133
Apr 13 19:18:24 mamsaac-laptop kernel: [   19.068000] ata1: EH complete
Apr 13 19:18:24 mamsaac-laptop kernel: [   19.068000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Apr 13 19:18:24 mamsaac-laptop kernel: [   19.068000] sd 0:0:0:0: [sda] Write Protect is off
Apr 13 19:18:24 mamsaac-laptop kernel: [   19.068000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 13 19:18:24 mamsaac-laptop kernel: [   19.068000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 13 19:18:24 mamsaac-laptop kernel: [   26.624000] input: Lid Switch as /class/input/input6
Apr 13 19:18:24 mamsaac-laptop kernel: [   26.624000] ACPI: Lid Switch [LID]
Apr 13 19:18:24 mamsaac-laptop kernel: [   26.624000] input: Power Button (CM) as /class/input/input7
Apr 13 19:18:24 mamsaac-laptop kernel: [   26.624000] ACPI: Power Button (CM) [PBTN]
Apr 13 19:18:24 mamsaac-laptop kernel: [   26.624000] input: Sleep Button (CM) as /class/input/input8
Apr 13 19:18:24 mamsaac-laptop kernel: [   26.624000] ACPI: Sleep Button (CM) [SBTN]
Apr 13 19:18:24 mamsaac-laptop kernel: [   26.664000] No dock devices found.
Apr 13 19:18:24 mamsaac-laptop kernel: [   26.780000] ACPI: Battery Slot [BAT0] (battery present)
Apr 13 19:18:24 mamsaac-laptop kernel: [   26.832000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Apr 13 19:18:24 mamsaac-laptop kernel: [   26.840000] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Apr 13 19:18:24 mamsaac-laptop kernel: [   26.840000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Apr 13 19:18:24 mamsaac-laptop kernel: [   26.852000] ACPI: AC Adapter [AC] (off-line)
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <info>  starting... 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.505679] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.684221] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.684763] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a00'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.685077] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a02'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.685469] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a03'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.686715] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2834'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.742832] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.743300] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_if0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.743678] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_4500_noserial'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.744977] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.745719] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.746402] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if0_bluetooth_hci'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.747253] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if1'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.747796] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if2'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.748415] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if3'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.748730] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_4502_noserial'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.749454] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_4502_noserial_if0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.749771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_4503_noserial'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.750086] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_4503_noserial_if0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.750398] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_4500_noserial_if0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.800494] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2835'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.800830] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.801149] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_if0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.801467] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283a'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.801818] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.802138] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_if0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.802544] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.802873] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283f'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.803289] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2841'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.803630] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_4222'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.805436] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2845'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.805755] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2830'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.806070] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.806384] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.806731] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2831'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.807162] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.807502] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.807845] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2832'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.808168] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.808497] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.808810] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2836'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.809123] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.809426] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.809732] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5a9_2640_noserial'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.810038] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5a9_2640_noserial_if0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.810344] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5a9_2640_noserial_if1'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.810651] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.810958] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.811262] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.811567] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.811872] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.812176] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.812494] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.812797] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2815'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.813100] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2850'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.813404] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2850_scsi_host'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.813708] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2850_scsi_host_scsi_device_lun0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.814012] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2829'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.814315] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2829_scsi_host'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.814618] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2829_scsi_host_scsi_device_lun0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.814922] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_283e'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.815225] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.815528] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.815831] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.816133] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.816453] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.816756] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_Synaptics_pass_through'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.817059] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.817360] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.817665] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.817967] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.818269] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.818570] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.818872] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.819173] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.819475] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.819775] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.820075] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.820402] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.820769] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.821096] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.821389] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.821705] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.822048] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.822374] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_4503_noserial_if0_logicaldev_input'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.822665] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.822978] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.823318] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_4502_noserial_if0_logicaldev_input'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.823637] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.823963] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.824259] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_19_b9_85_ab_e9'). 
Apr 13 19:18:24 mamsaac-laptop kernel: [   28.148000] b44: eth0: BUG!  Timeout waiting for bit 00000002 of register 42c to clear.
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'b44'. 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <info>  Deactivating device eth0. 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.893473] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1b_77_81_09_77'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw3945'. 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <info>  Deactivating device eth1. 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.956512] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2829_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.956853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2850_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.957188] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_pcm_1'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.957516] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_pcm_0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.957811] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_control__1'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.958128] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_pcm_0_0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.958443] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_hw_specific_0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.958759] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_hw_specific_1'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.959077] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_oss_mixer__1'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.959397] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_capture_0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.959717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_playback_0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.960064] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_284b_alsa_playback_1'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.960409] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.960731] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.961054] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.961379] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.961714] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.962038] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.962355] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.962692] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.963081] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_0_usbraw'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.963402] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_4500_noserial_usbraw'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.963716] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_usbraw'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.964040] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_4502_noserial_usbraw'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.964345] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_a5c_4503_noserial_usbraw'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.964660] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_1_usbraw'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.965004] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.965324] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.965646] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.965974] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1a_7_usbraw'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.966289] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.966635] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5a9_2640_noserial_usbraw'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.966954] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5a9_2640_noserial_video4linux'). 
Apr 13 19:18:24 mamsaac-laptop NetworkManager: <debug> [1208132304.967306] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST9160821AS_5MA3CQJ4'). 
Apr 13 19:18:25 mamsaac-laptop NetworkManager: <debug> [1208132305.048341] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_07D7_0904'). 
Apr 13 19:18:25 mamsaac-laptop NetworkManager: <debug> [1208132305.375690] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_B260AEF260AEBD0B'). 
Apr 13 19:18:25 mamsaac-laptop NetworkManager: <debug> [1208132305.426105] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part3_size_1024'). 
Apr 13 19:18:25 mamsaac-laptop NetworkManager: <debug> [1208132305.709450] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_46E7_6E22'). 
Apr 13 19:18:25 mamsaac-laptop NetworkManager: <debug> [1208132305.713273] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_129c410f_4e08_4ec5_a341_8d996b8221bf'). 
Apr 13 19:18:25 mamsaac-laptop NetworkManager: <debug> [1208132305.716694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_bb33f962_1938_4220_a2ac_8c5e4ee33160'). 
Apr 13 19:18:25 mamsaac-laptop kernel: [   29.172000] ppdev: user-space parallel port driver
Apr 13 19:18:25 mamsaac-laptop NetworkManager: <debug> [1208132305.863593] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_07D7_0904_0'). 
Apr 13 19:18:25 mamsaac-laptop NetworkManager: <debug> [1208132305.949390] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Apr 13 19:18:25 mamsaac-laptop NetworkManager: <debug> [1208132305.981557] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Apr 13 19:18:25 mamsaac-laptop NetworkManager: <debug> [1208132305.981870] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Apr 13 19:18:25 mamsaac-laptop NetworkManager: <debug> [1208132305.982169] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Apr 13 19:18:25 mamsaac-laptop NetworkManager: <debug> [1208132305.982663] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRWDVD_CRX880A'). 
Apr 13 19:18:26 mamsaac-laptop kernel: [   29.544000] audit(1208132305.841:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5495 profile="/usr/sbin/cupsd"
Apr 13 19:18:27 mamsaac-laptop mysqld_safe[5569]: started
Apr 13 19:18:27 mamsaac-laptop mysqld[5572]: 080413 19:18:27  InnoDB: Started; log sequence number 0 43655
Apr 13 19:18:27 mamsaac-laptop mysqld[5572]: 080413 19:18:27 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
Apr 13 19:18:27 mamsaac-laptop mysqld[5572]: 080413 19:18:27 [Note] Starting crash recovery...
Apr 13 19:18:27 mamsaac-laptop mysqld[5572]: 080413 19:18:27 [Note] Crash recovery finished.
Apr 13 19:18:27 mamsaac-laptop mysqld[5572]: 080413 19:18:27 [Note] /usr/sbin/mysqld: ready for connections.
Apr 13 19:18:27 mamsaac-laptop mysqld[5572]: Version: '5.0.45-Debian_1ubuntu3.3-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Debian etch distribution
Apr 13 19:18:28 mamsaac-laptop /etc/mysql/debian-start[5607]: Upgrading MySQL tables if necessary.
Apr 13 19:18:28 mamsaac-laptop kernel: [   31.580000] apm: BIOS not found.
Apr 13 19:18:28 mamsaac-laptop /etc/mysql/debian-start[5613]: Looking for 'mysql' in: /usr/bin/mysql
Apr 13 19:18:28 mamsaac-laptop /etc/mysql/debian-start[5613]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Apr 13 19:18:28 mamsaac-laptop /etc/mysql/debian-start[5613]: This installation of MySQL is already upgraded to 5.0.45, use --force if you still need to run mysql_upgrade
Apr 13 19:18:28 mamsaac-laptop /etc/mysql/debian-start[5650]: Checking for insecure root accounts.
Apr 13 19:18:28 mamsaac-laptop /etc/mysql/debian-start[5654]: Checking for crashed MySQL tables.
Apr 13 19:18:28 mamsaac-laptop kernel: [   32.136000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Apr 13 19:18:28 mamsaac-laptop kernel: [   32.260000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Apr 13 19:18:28 mamsaac-laptop kernel: [   32.284000] NFSD: starting 90-second grace period
Apr 13 19:18:30 mamsaac-laptop kernel: [   33.536000] Failure registering capabilities with primary security module.
Apr 13 19:18:30 mamsaac-laptop avahi-daemon[5921]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Apr 13 19:18:30 mamsaac-laptop avahi-daemon[5921]: Successfully dropped root privileges.
Apr 13 19:18:30 mamsaac-laptop avahi-daemon[5921]: avahi-daemon 0.6.20 starting up.
Apr 13 19:18:30 mamsaac-laptop avahi-daemon[5921]: Successfully called chroot().
Apr 13 19:18:30 mamsaac-laptop avahi-daemon[5921]: Successfully dropped remaining capabilities.
Apr 13 19:18:30 mamsaac-laptop avahi-daemon[5921]: No service file found in /etc/avahi/services.
Apr 13 19:18:30 mamsaac-laptop avahi-daemon[5921]: Network interface enumeration completed.
Apr 13 19:18:30 mamsaac-laptop avahi-daemon[5921]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 13 19:18:30 mamsaac-laptop avahi-daemon[5921]: Server startup complete. Host name is mamsaac-laptop.local. Local service cookie is 1092785904.
Apr 13 19:18:30 mamsaac-laptop dhcdbd: Started up.
Apr 13 19:18:30 mamsaac-laptop hcid[5956]: Bluetooth HCI daemon
Apr 13 19:18:30 mamsaac-laptop hcid[5956]: HCI dev 0 registered
Apr 13 19:18:30 mamsaac-laptop hcid[5956]: Starting SDP server
Apr 13 19:18:30 mamsaac-laptop hcid[5956]: Created local server at unix:abstract=/var/run/dbus-JlSE7LPnqA,guid=ad6b4236a1641a04a33783004802a2d6
Apr 13 19:18:30 mamsaac-laptop kernel: [   33.848000] Bluetooth: L2CAP ver 2.8
Apr 13 19:18:30 mamsaac-laptop kernel: [   33.848000] Bluetooth: L2CAP socket layer initialized
Apr 13 19:18:30 mamsaac-laptop audio[5964]: Bluetooth Audio daemon
Apr 13 19:18:30 mamsaac-laptop audio[5964]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Apr 13 19:18:30 mamsaac-laptop hcid[5956]: HCI dev 0 up
Apr 13 19:18:30 mamsaac-laptop hcid[5956]: Device hci0 has been added
Apr 13 19:18:30 mamsaac-laptop input[5965]: Bluetooth Input daemon
Apr 13 19:18:30 mamsaac-laptop audio[5964]: Unix socket created: 5
Apr 13 19:18:30 mamsaac-laptop input[5965]: Registered input manager path:/org/bluez/input
Apr 13 19:18:30 mamsaac-laptop hcid[5956]: Starting security manager 0
Apr 13 19:18:30 mamsaac-laptop kernel: [   33.932000] Bluetooth: RFCOMM socket layer initialized
Apr 13 19:18:30 mamsaac-laptop kernel: [   33.932000] Bluetooth: RFCOMM TTY layer initialized
Apr 13 19:18:30 mamsaac-laptop kernel: [   33.932000] Bluetooth: RFCOMM ver 1.8
Apr 13 19:18:30 mamsaac-laptop hcid[5956]: Device hci0 has been activated
Apr 13 19:18:30 mamsaac-laptop audio[5964]: add_service_record: got record id 0x10000
Apr 13 19:18:30 mamsaac-laptop audio[5964]: add_service_record: got record id 0x10001
Apr 13 19:18:30 mamsaac-laptop audio[5964]: Registered manager path:/org/bluez/audio
Apr 13 19:18:33 mamsaac-laptop /usr/sbin/cron[6063]: (CRON) INFO (pidfile fd = 3)
Apr 13 19:18:33 mamsaac-laptop /usr/sbin/cron[6064]: (CRON) STARTUP (fork ok)
Apr 13 19:18:33 mamsaac-laptop /usr/sbin/cron[6064]: (CRON) INFO (Running @reboot jobs)
Apr 13 19:18:35 mamsaac-laptop kernel: [   38.956000] [drm] Initialized drm 1.1.0 20060810
Apr 13 19:18:35 mamsaac-laptop kernel: [   38.976000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Apr 13 19:18:35 mamsaac-laptop kernel: [   38.980000] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr 13 19:18:53 mamsaac-laptop hcid[5956]: Default passkey agent (:1.17, /org/bluez/passkey) registered
Apr 13 19:18:53 mamsaac-laptop hcid[5956]: Default authorization agent (:1.17, /org/bluez/auth) registered
Apr 13 19:19:01 mamsaac-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Apr 13 19:19:11 mamsaac-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Apr 13 19:19:11 mamsaac-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Apr 13 19:19:11 mamsaac-laptop NetworkManager: <info>  Will activate connection 'eth1/Veracruz'. 
Apr 13 19:19:11 mamsaac-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Apr 13 19:19:11 mamsaac-laptop NetworkManager: <info>  Activation (eth1) started... 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Veracruz' is encrypted, but NO valid key exists.  New key needed. 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Veracruz'. 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Veracruz' received. 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Apr 13 19:19:18 mamsaac-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Veracruz' is encrypted, and a key exists.  No new key needed. 
Apr 13 19:19:19 mamsaac-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (2/10). 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (3/10). 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (4/10). 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (5/10). 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Apr 13 19:19:20 mamsaac-laptop kernel: [   84.096000] NET: Registered protocol family 17
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: response was '0' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 566572616372757a' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  SUP: response was 'OK' 
Apr 13 19:19:20 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Apr 13 19:19:24 mamsaac-laptop kernel: [   87.412000] ieee80211_crypt: registered algorithm 'WEP'
Apr 13 19:19:24 mamsaac-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Veracruz'. 
Apr 13 19:19:24 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 13 19:19:24 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Apr 13 19:19:25 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Apr 13 19:19:25 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Apr 13 19:19:25 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Apr 13 19:19:27 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Apr 13 19:19:29 mamsaac-laptop kernel: [   93.108000] ata1.00: exception Emask 0x2 SAct 0x4 SErr 0x0 action 0x2 frozen
Apr 13 19:19:29 mamsaac-laptop kernel: [   93.108000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x4 FIS=004040a1:00000002)
Apr 13 19:19:29 mamsaac-laptop kernel: [   93.108000] ata1.00: cmd 60/08:10:74:31:fe/00:00:11:00:00/40 tag 2 cdb 0x0 data 4096 in
Apr 13 19:19:29 mamsaac-laptop kernel: [   93.108000]          res 40/00:10:74:31:fe/00:00:11:00:00/40 Emask 0x2 (HSM violation)
Apr 13 19:19:30 mamsaac-laptop kernel: [   93.424000] ata1: soft resetting port
Apr 13 19:19:30 mamsaac-laptop kernel: [   93.596000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 13 19:19:30 mamsaac-laptop kernel: [   93.604000] ata1.00: configured for UDMA/133
Apr 13 19:19:30 mamsaac-laptop kernel: [   93.604000] ata1: EH complete
Apr 13 19:19:30 mamsaac-laptop kernel: [   93.604000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Apr 13 19:19:30 mamsaac-laptop kernel: [   93.604000] sd 0:0:0:0: [sda] Write Protect is off
Apr 13 19:19:30 mamsaac-laptop kernel: [   93.604000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 13 19:19:30 mamsaac-laptop kernel: [   93.604000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 13 19:19:31 mamsaac-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr 13 19:19:31 mamsaac-laptop dhclient: DHCPOFFER from 192.168.0.1
Apr 13 19:19:31 mamsaac-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Apr 13 19:19:32 mamsaac-laptop dhclient: DHCPACK from 192.168.0.1
Apr 13 19:19:32 mamsaac-laptop avahi-daemon[5921]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.4.
Apr 13 19:19:32 mamsaac-laptop avahi-daemon[5921]: New relevant interface eth1.IPv4 for mDNS.
Apr 13 19:19:32 mamsaac-laptop avahi-daemon[5921]: Registering new address record for 192.168.0.4 on eth1.IPv4.
Apr 13 19:19:32 mamsaac-laptop dhclient: bound to 192.168.0.4 -- renewal in 1477 seconds.
Apr 13 19:19:32 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Apr 13 19:19:32 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr 13 19:19:32 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Apr 13 19:19:37 mamsaac-laptop kernel: [  100.932000] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Apr 13 19:19:54 mamsaac-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Apr 13 19:19:54 mamsaac-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Apr 13 19:19:54 mamsaac-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Apr 13 19:19:54 mamsaac-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr 13 19:19:54 mamsaac-laptop NetworkManager: <info>    address 192.168.0.4 
Apr 13 19:19:54 mamsaac-laptop NetworkManager: <info>    netmask 255.255.255.0 
Apr 13 19:19:54 mamsaac-laptop NetworkManager: <info>    broadcast 192.168.0.255 
Apr 13 19:19:54 mamsaac-laptop NetworkManager: <info>    gateway 192.168.0.1 
Apr 13 19:19:54 mamsaac-laptop NetworkManager: <info>    nameserver 10.1.2.116 
Apr 13 19:19:54 mamsaac-laptop NetworkManager: <info>    nameserver 10.1.2.8 
Apr 13 19:19:54 mamsaac-laptop NetworkManager: <info>    nameserver 10.1.2.2 
Apr 13 19:19:54 mamsaac-laptop NetworkManager: <info>    domain name 'mmredes.net' 
Apr 13 19:19:54 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 13 19:19:54 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Apr 13 19:19:54 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Apr 13 19:19:54 mamsaac-laptop avahi-daemon[5921]: Withdrawing address record for 192.168.0.4 on eth1.
Apr 13 19:19:54 mamsaac-laptop avahi-daemon[5921]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.4.
Apr 13 19:19:54 mamsaac-laptop avahi-daemon[5921]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 13 19:19:54 mamsaac-laptop avahi-daemon[5921]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.4.
Apr 13 19:19:54 mamsaac-laptop avahi-daemon[5921]: New relevant interface eth1.IPv4 for mDNS.
Apr 13 19:19:54 mamsaac-laptop avahi-daemon[5921]: Registering new address record for 192.168.0.4 on eth1.IPv4.
Apr 13 19:19:55 mamsaac-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr 13 19:19:55 mamsaac-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr 13 19:19:55 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Apr 13 19:19:55 mamsaac-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 13 19:19:55 mamsaac-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Apr 13 19:19:55 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 19:19:57 mamsaac-laptop last message repeated 2 times
Apr 13 19:20:02 mamsaac-laptop ntpdate[6634]: step time server 200.23.51.205 offset 1.808115 sec
Apr 13 19:23:57 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 19:38:25 mamsaac-laptop -- MARK --
Apr 13 19:39:01 mamsaac-laptop /USR/SBIN/CRON[6985]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 13 19:44:10 mamsaac-laptop dhclient: DHCPREQUEST on eth1 to 192.168.0.1 port 67
Apr 13 19:44:11 mamsaac-laptop dhclient: DHCPACK from 192.168.0.1
Apr 13 19:44:11 mamsaac-laptop dhclient: bound to 192.168.0.4 -- renewal in 1557 seconds.
Apr 13 19:44:11 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Apr 13 19:58:25 mamsaac-laptop -- MARK --
Apr 13 20:09:01 mamsaac-laptop /USR/SBIN/CRON[7336]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 13 20:10:08 mamsaac-laptop dhclient: DHCPREQUEST on eth1 to 192.168.0.1 port 67
Apr 13 20:10:08 mamsaac-laptop dhclient: DHCPACK from 192.168.0.1
Apr 13 20:10:09 mamsaac-laptop dhclient: bound to 192.168.0.4 -- renewal in 1755 seconds.
Apr 13 20:10:09 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Apr 13 20:17:01 mamsaac-laptop /USR/SBIN/CRON[7408]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 13 20:38:25 mamsaac-laptop -- MARK --
Apr 13 20:39:01 mamsaac-laptop /USR/SBIN/CRON[7791]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 13 20:39:24 mamsaac-laptop dhclient: DHCPREQUEST on eth1 to 192.168.0.1 port 67
Apr 13 20:39:25 mamsaac-laptop dhclient: DHCPACK from 192.168.0.1
Apr 13 20:39:25 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Apr 13 20:39:25 mamsaac-laptop dhclient: bound to 192.168.0.4 -- renewal in 1569 seconds.
Apr 13 20:58:25 mamsaac-laptop -- MARK --
Apr 13 21:05:34 mamsaac-laptop dhclient: DHCPREQUEST on eth1 to 192.168.0.1 port 67
Apr 13 21:05:35 mamsaac-laptop dhclient: DHCPACK from 192.168.0.1
Apr 13 21:05:35 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Apr 13 21:05:35 mamsaac-laptop dhclient: bound to 192.168.0.4 -- renewal in 1466 seconds.
Apr 13 21:09:01 mamsaac-laptop /USR/SBIN/CRON[8297]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 13 21:17:01 mamsaac-laptop /USR/SBIN/CRON[8408]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 13 21:30:01 mamsaac-laptop dhclient: DHCPREQUEST on eth1 to 192.168.0.1 port 67
Apr 13 21:30:02 mamsaac-laptop dhclient: DHCPACK from 192.168.0.1
Apr 13 21:30:02 mamsaac-laptop dhclient: bound to 192.168.0.4 -- renewal in 1579 seconds.
Apr 13 21:30:02 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Apr 13 21:30:08 mamsaac-laptop anacron[8598]: Anacron 2.3 started on 2008-04-13
Apr 13 21:30:08 mamsaac-laptop anacron[8598]: Normal exit (0 jobs run)
Apr 13 21:39:01 mamsaac-laptop /USR/SBIN/CRON[8704]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 13 21:56:21 mamsaac-laptop dhclient: DHCPREQUEST on eth1 to 192.168.0.1 port 67
Apr 13 21:56:22 mamsaac-laptop dhclient: DHCPACK from 192.168.0.1
Apr 13 21:56:22 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Apr 13 21:56:22 mamsaac-laptop dhclient: bound to 192.168.0.4 -- renewal in 1796 seconds.
Apr 13 22:09:01 mamsaac-laptop /USR/SBIN/CRON[8805]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 13 22:15:59 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:17:01 mamsaac-laptop /USR/SBIN/CRON[8987]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 13 22:17:42 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:22:16 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:22:59 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:24:05 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:26:18 mamsaac-laptop dhclient: DHCPREQUEST on eth1 to 192.168.0.1 port 67
Apr 13 22:26:19 mamsaac-laptop dhclient: DHCPACK from 192.168.0.1
Apr 13 22:26:19 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Apr 13 22:26:19 mamsaac-laptop dhclient: bound to 192.168.0.4 -- renewal in 1667 seconds.
Apr 13 22:27:44 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:28:34 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:29:46 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:30:28 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:32:33 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:33:51 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:37:54 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:38:37 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:39:01 mamsaac-laptop /USR/SBIN/CRON[9543]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 13 22:39:36 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:39:42 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:41:44 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:43:55 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:54:06 mamsaac-laptop dhclient: DHCPREQUEST on eth1 to 192.168.0.1 port 67
Apr 13 22:54:07 mamsaac-laptop dhclient: DHCPACK from 192.168.0.1
Apr 13 22:54:07 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Apr 13 22:54:07 mamsaac-laptop dhclient: bound to 192.168.0.4 -- renewal in 1701 seconds.
Apr 13 22:56:59 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 22:59:50 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 23:05:17 mamsaac-laptop modprobe: WARNING: Not loading blacklisted module ipv6 
Apr 13 23:09:01 mamsaac-laptop /USR/SBIN/CRON[10147]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 13 23:17:02 mamsaac-laptop /USR/SBIN/CRON[10194]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 13 23:22:28 mamsaac-laptop dhclient: DHCPREQUEST on eth1 to 192.168.0.1 port 67
Apr 13 23:22:29 mamsaac-laptop dhclient: DHCPACK from 192.168.0.1
Apr 13 23:22:29 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Apr 13 23:22:29 mamsaac-laptop dhclient: bound to 192.168.0.4 -- renewal in 1396 seconds.
Apr 13 23:38:25 mamsaac-laptop -- MARK --
Apr 13 23:39:01 mamsaac-laptop /USR/SBIN/CRON[10313]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 13 23:45:45 mamsaac-laptop dhclient: DHCPREQUEST on eth1 to 192.168.0.1 port 67
Apr 13 23:45:46 mamsaac-laptop dhclient: DHCPACK from 192.168.0.1
Apr 13 23:45:46 mamsaac-laptop dhclient: bound to 192.168.0.4 -- renewal in 1535 seconds.
Apr 13 23:45:46 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Apr 13 23:58:25 mamsaac-laptop -- MARK --
Apr 14 00:09:01 mamsaac-laptop /USR/SBIN/CRON[10444]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 14 00:11:21 mamsaac-laptop dhclient: DHCPREQUEST on eth1 to 192.168.0.1 port 67
Apr 14 00:11:22 mamsaac-laptop dhclient: DHCPACK from 192.168.0.1
Apr 14 00:11:22 mamsaac-laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Apr 14 00:11:22 mamsaac-laptop dhclient: bound to 192.168.0.4 -- renewal in 1639 seconds.
```

That was syslog on /var/log/

I find it interesting how there are many mistakes and errors related to ipw3945 and even more about NetworkManager.

I will come back tomorrow to see if there's any information. I have to wake up in a few hours for college.

Thanks for the help, good night =)

---

### Post by Mamsaac on 2008-04-14
Back.

Thanks for the comments yesterday. I'm still looking at the problem, help will be appreciated.

---

