---
title: "Ubuntu keeps freezing"
date: 2007-06-21
forum: General Help
---

### Post by Keisad on 2007-06-21
Hey guys,

I just recently installed ubuntu on my toshiba from the boot cd. I'm using fiesty. For some reason, my system decides to completely freeze every once in a while. This could happen while I'm booting, recording, transferring files from usb, playing games, using firefox, basically while I'm doing anything. What happens is that the application I'm using first locks up, and then shortly followed by the rest of the computer. When this happens, I have no choice but to shut down my laptop using the on/off button. When it locks up, I can use my mouse for a little until that finally retaliates, and then my system is completely unresponsive. So.... I was hoping some of you might be able to help me. It's getting frustrating, since it happens very often. If you guys need any more information, let me know.

---

### Post by sbjaved on 2007-06-21
I have the same problem too...

It just decides to go "freeze" on me. Anybody give some help here?

---

### Post by OutCell on 2007-06-21
I have the same problem as well. This is a common bug/problem in ubuntu. There was a thread i saw a couple of days ago with some fixes but nothing effective or final on rectifying this problem.. It might work for you though..

Just search for ubuntu freeze and you will find it (You won't miss it, it's about 80 pages thread) lol

I hope they fix this problem because i am really getting to enjoy ubuntu and appreciate it over windows. This freezing problem is the only thing that makes this OS not as reliable as windows (I never had my system freeze before)..

---

### Post by tgalati4 on 2007-06-21
Try a Dapper 6.06.1 Live CD and see how long your machine stays up.  I get several weeks of uptime before I feel the need to reboot.

---

### Post by kuja on 2007-06-21
Post your /var/log/syslog and /var/log/dmesg

Perhaps there is an explanation.

---

### Post by Keisad on 2007-06-21
"edit"

Well, I had an idea this morning. I recently installed and started using a low-latency kernel, since it was recommended for an application I was using. So I switched to the regular, generic kernel and now it doesn't freeze *as much*. 

However, it still does often enough to be a problem.

Thanks kuja, I'll post the logs sometime tonight, as I am not with my home computer at the moment.

---

### Post by Keisad on 2007-06-21
And I do not have a dapper cd at the moment. I'm guessing I could download it, but my machine will not stay active long enough to make it worthwhile.

---

### Post by Marious on 2007-06-21
Got a question for you. OK when you are experiencing freezes are you running multiple applications or just one? You could have conflicts between applications, are the games your playing being ran in Wine or Linux Native? There could be a lot of problems here, could be something as simple as your sound drivers and what not I see it happen and I was having similar issues but my problem was that I had a bad power supply and possibly a bad CPU. Is this a fresh install? Have you updated and downloaded all the latest drivers for all your hardware?
The more you provide the easier it is for the guys around here to help you out, I'm no expert whatsoever but I know a bit and the more you can say the better the answer will be.

Marious

---

### Post by Keisad on 2007-06-21
The games I play are in wine. I have had it freeze when I am running one application, or multiple. I have even had it crash when it was booting a couple times. This is a fresh install, and I don't think my drivers are out of date. 

I tried to post my syslog, but it's fairly extensive. Is there any certain part you need, or should I get a snippet of what happens before it freezes?

---

### Post by Keisad on 2007-06-21
Well, here's a snippet of var/log/syslog at the time my computer freezes:

```
Jun 21 16:02:26 casper NetworkManager: <information>^IClearing nscd hosts cache. 
Jun 21 16:02:26 casper NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jun 21 16:02:26 casper NetworkManager: <information>^IActivation (ath0) successful, device activated. 
Jun 21 16:02:26 casper NetworkManager: <information>^IActivation (ath0) Finish handler scheduled. 
Jun 21 16:02:26 casper NetworkManager: <information>^IActivation (ath0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun 21 16:02:27 casper avahi-daemon[4880]: Registering new address record for fe80::211:f5ff:fe1e:948f on ath0.*.
Jun 21 16:02:34 casper ntpdate[5729]: step time server 82.211.81.145 offset 0.874297 sec
Jun 21 16:02:37 casper kernel: [   73.880676] ath0: no IPv6 routers present
Jun 21 16:02:39 casper ntpdate[5741]: adjust time server 82.211.81.145 offset 0.000197 sec
Jun 21 16:02:40 casper ntpdate[5750]: adjust time server 82.211.81.145 offset -0.000071 sec
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): EVENT-CONNECTED - Connection to 00:17:3f:5a:50:ba completed (auth) [id=0 id_str=] 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 38 36 32 2d 32 00 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): wpa_driver_wext_set_operstate: operstate 0->1 (UP) 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): WEXT: Operstate: linkmode=-1, operstate=6 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Cancelling scan request 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Wireless event: cmd=0x8b06 len=8 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Wireless event: cmd=0x8b06 len=8 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Wireless event: cmd=0x8b19 len=8 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Received 539 bytes of scan results (3 BSSes) 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Scan results: 3 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Selecting BSS from priority group 0 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): 0: 00:17:3f:5a:50:ba ssid='belkin54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Jun 21 16:02:55 casper NetworkManager: <information>^Iwpa_supplicant(5616):    skip - no WPA/RSN IE 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): n=0 rsn_ie_len=0 caps=0x1 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616):    skip - no WPA/RSN IE 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): 2: 00:15:6d:53:33:3d ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616):    skip - no WPA/RSN IE 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616):    selected non-WPA AP 00:17:3f:5a:50:ba ssid='belkin54g' 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): Already associated with the selected AP. 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): Wireless event: cmd=0x8b06 len=8 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): Wireless event: cmd=0x8b19 len=8 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): Received 539 bytes of scan results (3 BSSes) 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): Scan results: 3 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): Selecting BSS from priority group 0 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): 0: 00:17:3f:5a:50:ba ssid='belkin54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616):    skip - no WPA/RSN IE 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): 1: 00:17:9a:2d:e0:f8 ssid='dlink' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616):    skip - no WPA/RSN IE 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): 2: 00:15:6d:53:33:3d ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616):    skip - no WPA/RSN IE 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616):    selected non-WPA AP 00:17:3f:5a:50:ba ssid='belkin54g' 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): Already associated with the selected AP. 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 21 16:03:35 casper NetworkManager: <information>^Iwpa_supplicant(5616): Wireless event: cmd=0x8b06 len=8 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): WLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Wireless event: cmd=0x8b19 len=8 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Received 539 bytes of scan results (3 BSSes) 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Scan results: 3 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Selecting BSS from priority group 0 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): 0: 00:17:3f:5a:50:ba ssid='belkin54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616):    skip - no WPA/RSN IE 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): 1: 00:17:9a:2d:e0:f8 ssid='dlink' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616):    skip - no WPA/RSN IE 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): 2: 00:15:6d:53:33:3d ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616):    skip - no WPA/RSN IE 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616):    selected non-WPA AP 00:17:3f:5a:50:ba ssid='belkin54g' 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Already associated with the selected AP. 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Wireless event: cmd=0x8b06 len=8 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Wireless event: cmd=0x8b19 len=8 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Received 539 bytes of scan results (3 BSSes) 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Scan results: 3 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): Selecting BSS from priority group 0 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616): 0: 00:17:3f:5a:50:ba ssid='belkin54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Jun 21 16:03:55 casper NetworkManager: <information>^Iwpa_supplicant(5616):    skip - no WPA/RSN IE 
```

And from dmesg

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d2000 size: 0000000000006000 end: 00000000000d8000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fe70000 end: 000000001ff70000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001ff70000 size: 000000000000b000 end: 000000001ff7b000 type: 3
[    0.000000] copy_e820_map() start: 000000001ff7b000 size: 0000000000005000 end: 000000001ff80000 type: 4
[    0.000000] copy_e820_map() start: 000000001ff80000 size: 0000000000080000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 000000002ff80000 size: 0000000000080000 end: 0000000030000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff7b000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff7b000 - 000000001ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 000000002ff80000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f68f0
[    0.000000] Entering add_active_range(0, 0, 130928) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130928
[    0.000000]   HighMem    130928 ->   130928
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130928
[    0.000000] On node 0 totalpages: 130928
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125842 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6950
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1ff75f3a
[    0.000000] ACPI: FADT (v001 TOSCPL Chinook  0x06040000 ATI  0x00000003) @ 0x1ff7af24
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x1ff7af98
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x1ff75f6a
[    0.000000] ACPI: DSDT (v001 TOSCPL    SB200 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] Detected 3200.290 MHz processor.
[   13.284838] Built 1 zonelists.  Total pages: 129906
[   13.284842] Kernel command line: root=UUID=07627c9e-5307-4d3f-838f-abf0b0c49795 ro quiet splash
[   13.284988] mapped APIC to ffffd000 (fee00000)
[   13.284991] mapped IOAPIC to ffffc000 (fec00000)
[   13.284994] Enabling fast FPU save and restore... done.
[   13.284997] Enabling unmasked SIMD FPU exception support... done.
[   13.285005] Initializing CPU#0
[   13.285050] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   13.286027] Console: colour VGA+ 80x25
[   13.286313] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.286565] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.297036] Memory: 508216k/523712k available (1992k kernel code, 14996k reserved, 900k data, 328k init, 0k highmem)
[   13.297046] virtual kernel memory layout:
[   13.297047]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   13.297048]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.297049]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   13.297050]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[   13.297051]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   13.297052]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   13.297053]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   13.297056] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.376776] Calibrating delay using timer specific routine.. 6408.17 BogoMIPS (lpj=12816357)
[   13.376839] Security Framework v1.0.0 initialized
[   13.376845] SELinux:  Disabled at boot.
[   13.376862] Mount-cache hash table entries: 512
[   13.377000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000459d 00000000 00000000
[   13.377008] monitor/mwait feature present.
[   13.377010] using mwait in idle threads.
[   13.377017] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   13.377019] CPU: L2 cache: 1024K
[   13.377022] CPU: Physical Processor ID: 0
[   13.377024] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000459d 00000000 00000000
[   13.377035] Compat vDSO mapped to ffffe000.
[   13.377038] Remapping vsyscall page to ffffe000
[   13.377054] Checking 'hlt' instruction... OK.
[   13.392811] SMP alternatives: switching to UP code
[   13.393164] Early unpacking initramfs... done
[   13.647847] ACPI: Core revision 20060707
[   13.648007] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   13.653454] CPU0: Intel Mobile Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 01
[   13.653483] SMP alternatives: switching to SMP code
[   13.653629] Booting processor 1/1 eip 3000
[   13.663924] Initializing CPU#1
[   13.743657] Calibrating delay using timer specific routine.. 6400.74 BogoMIPS (lpj=12801495)
[   13.743668] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000459d 00000000 00000000
[   13.743675] monitor/mwait feature present.
[   13.743682] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   13.743685] CPU: L2 cache: 1024K
[   13.743688] CPU: Physical Processor ID: 0
[   13.743690] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003180 0000459d 00000000 00000000
[   13.744063] CPU1: Intel Mobile Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 01
[   13.744104] Total of 2 processors activated (12808.92 BogoMIPS).
[   13.744168] ENABLING IO-APIC IRQs
[   13.744336] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   13.783951] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   13.783984] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   13.783989] ...trying to set up timer as Virtual Wire IRQ... works.
[   13.931094] checking TSC synchronization across 2 CPUs: passed.
[    0.003988] Brought up 2 CPUs
[    0.045188] migration_cost=26
[    0.045497] Booting paravirtualized kernel on bare hardware
[    0.045566] Time: 20:13:30  Date: 05/21/107
[    0.045600] NET: Registered protocol family 16
[    0.045700] EISA bus registered
[    0.045707] ACPI: bus type pci registered
[    0.045759] PCI: PCI BIOS revision 2.10 entry at 0xfd958, last bus=2
[    0.045761] PCI: Using configuration type 1
[    0.045763] Setting up standard PCI resources
[    0.052343] ACPI: Interpreter enabled
[    0.052349] ACPI: Using IOAPIC for interrupt routing
[    0.053995] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.054002] PCI: Probing PCI hardware (bus 00)
[    0.055727] Boot video device is 0000:01:05.0
[    0.056233] PCI: Transparent bridge - 0000:00:14.4
[    0.056315] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.058934] ACPI: PCI Interrupt Link [LNK0] (IRQs 10 11) *0, disabled.
[    0.059148] ACPI: PCI Interrupt Link [LNK1] (IRQs 10 11) *0, disabled.
[    0.059361] ACPI: PCI Interrupt Link [LNK2] (IRQs 10 11) *0, disabled.
[    0.059570] ACPI: PCI Interrupt Link [LNK3] (IRQs 10 11) *0, disabled.
[    0.099837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.100869] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.101309] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.101327] pnp: PnP ACPI init
[    0.123732] pnp: PnP ACPI: found 9 devices
[    0.123739] PnPBIOS: Disabled by ACPI PNP
[    0.123805] PCI: Using ACPI for IRQ routing
[    0.123809] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.129514] NET: Registered protocol family 8
[    0.129517] NET: Registered protocol family 20
[    0.129722] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[    0.129725] pnp: 00:07: ioport range 0x220-0x22f has been reserved
[    0.129728] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[    0.129730] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.130076] PCI: Bridge: 0000:00:01.0
[    0.130080]   IO window: 9000-9fff
[    0.130084]   MEM window: e8100000-e81fffff
[    0.130088]   PREFETCH window: f0000000-f7ffffff
[    0.130099] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[    0.130102]   IO window: 0000a800-0000a8ff
[    0.130107]   IO window: 0000ac00-0000acff
[    0.130112]   PREFETCH window: 40000000-43ffffff
[    0.130117]   MEM window: 44000000-47ffffff
[    0.130122] PCI: Bridge: 0000:00:14.4
[    0.130126]   IO window: a000-afff
[    0.130130]   MEM window: e8200000-e82fffff
[    0.130134]   PREFETCH window: 40000000-43ffffff
[    0.130167] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.130209] NET: Registered protocol family 2
[    0.167559] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.167653] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.167727] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.167763] TCP: Hash tables configured (established 16384 bind 8192)
[    0.167766] TCP reno registered
[    0.183573] checking if image is initramfs... it is
[    0.691191] Freeing initrd memory: 6768k freed
[    0.691949] audit: initializing netlink socket (disabled)
[    0.691969] audit(1182456810.384:1): initialized
[    0.692192] VFS: Disk quotas dquot_6.5.1
[    0.692213] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.692274] io scheduler noop registered
[    0.692277] io scheduler anticipatory registered
[    0.692280] io scheduler deadline registered
[    0.692292] io scheduler cfq registered (default)
[    1.204660] isapnp: Scanning for PnP cards...
[    1.555302] isapnp: No Plug & Play device found
[    1.581407] Real Time Clock Driver v1.12ac
[    1.581468] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.582076] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[    1.582084] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[    1.582162] mice: PS/2 mouse device common for all mice
[    1.582824] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.582991] input: Macintosh mouse button emulation as /class/input/input0
[    1.583031] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.583036] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.583249] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.583513] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.583559] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.583566] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.583570] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.583574] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.583578] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.583700] EISA: Probing bus 0 at eisa.0
[    1.583710] Cannot allocate resource for EISA slot 1
[    1.583729] Cannot allocate resource for EISA slot 8
[    1.583731] EISA: Detected 0 cards.
[    1.613741] TCP cubic registered
[    1.613751] NET: Registered protocol family 1
[    1.613781] Starting balanced_irq
[    1.613793] Using IPI No-Shortcut mode
[    1.613896] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.613972] ACPI: (supports S0 S3 S4 S5)
[    1.614020]   Magic number: 11:866:245
[    1.614073]   hash matches device ttyw1
[    1.614586] Freeing unused kernel memory: 328k freed
[    1.615077] Time: tsc clocksource has been installed.
[    2.806069] Capability LSM initialized
[    2.843769] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.843925] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.844758] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.844898] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    3.357640] usbcore: registered new interface driver usbfs
[    3.357710] usbcore: registered new interface driver hub
[    3.364106] ieee1394: Initialized config rom entry `ip1394'
[    3.365954] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.379042] usbcore: registered new device driver usb
[    3.416708] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
[    3.416725] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.416875] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    3.416911] ehci_hcd 0000:00:13.2: irq 18, io mem 0xe8003000
[    3.416920] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.417041] usb usb1: configuration #1 chosen from 1 choice
[    3.417079] hub 1-0:1.0: USB hub found
[    3.417086] hub 1-0:1.0: 6 ports detected
[    3.418693] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[e8210000-e82107ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.425142] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.427724] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.517754] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    3.517777] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[    3.517792] ATIIXP: chipset revision 0
[    3.517800] ATIIXP: not 100% native mode: will probe irqs later
[    3.517811]     ide0: BM-DMA at 0x8070-0x8077, BIOS settings: hda:DMA, hdb:pio
[    3.517832]     ide1: BM-DMA at 0x8078-0x807f, BIOS settings: hdc:DMA, hdd:pio
[    3.517852] Probing IDE interface ide0...
[    3.804677] hda: FUJITSU MHV2120AH, ATA DISK drive
[    4.478053] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.554809] Probing IDE interface ide1...
[    4.690004] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f555b4006c8]
[    5.288206] hdc: MATSHITADVD-RAM UJ-820S, ATAPI CD/DVD-ROM drive
[    5.623324] ide1 at 0x170-0x177,0x376 on irq 15
[    5.633543] SCSI subsystem initialized
[    5.639801] libata version 2.20 loaded.
[    5.641868] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[    5.641893] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.641947] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    5.641974] ohci_hcd 0000:00:13.0: irq 18, io mem 0xe8001000
[    5.650358] hda: max request size: 128KiB
[    5.650483] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[    5.654486] hda: cache flushes supported
[    5.654554]  hda: hda1 hda2 <<6>usb usb2: configuration #1 chosen from 1 choice
[    5.699346] hub 2-0:1.0: USB hub found
[    5.699360] hub 2-0:1.0: 3 ports detected
[    5.708927]  hda5 >
[    5.710831] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    5.710846] Uniform CD-ROM driver Revision: 3.20
[    5.802692] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    5.802699] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[    5.802703] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[    5.802739] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.802778] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    5.802803] ohci_hcd 0000:00:13.1: irq 18, io mem 0xe8002000
[    5.806298] 8139too Fast Ethernet driver 0.9.28
[    5.862395] usb usb3: configuration #1 chosen from 1 choice
[    5.862445] hub 3-0:1.0: USB hub found
[    5.862460] hub 3-0:1.0: 3 ports detected
[    5.919771] Attempting manual resume
[    5.919776] swsusp: Resume From Partition 3:5
[    5.919778] PM: Checking swsusp image.
[    5.919973] PM: Resume from disk failed.
[    5.966183] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 18
[    5.966649] eth0: RealTek RTL8139 at 0xe0956800, 00:0f:b0:84:1c:1c, IRQ 18
[    5.966652] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    5.967710] kjournald starting.  Commit interval 5 seconds
[    5.967742] EXT3-fs: mounted filesystem with ordered data mode.
[    6.105546] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    6.313391] usb 2-2: configuration #1 chosen from 1 choice
[   14.887999] eth0: link down
[   16.220953] Linux agpgart interface v0.102 (c) Dave Jones
[   16.236771] agpgart: Detected Ati IGP9100/M chipset
[   16.246107] NET: Registered protocol family 17
[   16.250616] agpgart: AGP aperture is 64M @ 0xec000000
[   16.262725] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   16.414706] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.417079] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.822500] input: PC Speaker as /class/input/input2
[   16.924280] Yenta: CardBus bridge found at 0000:02:04.0 [1179:ff01]
[   16.924303] Yenta: Using CSCINT to route CSC interrupts to PCI
[   16.924306] Yenta: Routing CardBus interrupts to PCI
[   16.924313] Yenta TI: socket 0000:02:04.0, mfunc 0x89501212, devctl 0x44
[   16.942699] input: PS/2 Mouse as /class/input/input3
[   16.961479] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   16.967047] usbcore: registered new interface driver hiddev
[   17.063117] ath_hal: module license 'Proprietary' taints kernel.
[   17.100509] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input5
[   17.100642] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:13.0-2
[   17.100663] usbcore: registered new interface driver usbhid
[   17.100669] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   17.153001] Yenta: ISA IRQ mask 0x0ad8, PCI irq 16
[   17.153007] Socket status: 30000006
[   17.153013] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   17.153018] cs: IO port probe 0xa000-0xafff: clean.
[   17.153365] pcmcia: parent PCI bridge Memory window: 0xe8200000 - 0xe82fffff
[   17.153369] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   17.193038] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   17.359088] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   17.360120] atiixp: codec reset timeout
[   17.450340] wlan: 0.8.4.2 (0.9.3)
[   17.475161] ath_pci: 0.9.4.5 (0.9.3)
[   17.553835] sdhci: Secure Digital Host Controller Interface driver
[   17.553841] sdhci: Copyright(c) Pierre Ossman
[   17.791943] cs: IO port probe 0x100-0x3af: clean.
[   17.801359] cs: IO port probe 0x3e0-0x4ff: clean.
[   17.801876] cs: IO port probe 0x820-0x8ff: clean.
[   17.802341] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcd7
[   17.802878] cs: IO port probe 0xa00-0xaff: clean.
[   17.871083] sdhci: SDHCI controller found at 0000:02:04.2 [1524:0550] (rev 0)
[   17.871116] ACPI: PCI Interrupt 0000:02:04.2[B] -> GSI 17 (level, low) -> IRQ 17
[   17.871222] mmc0: SDHCI at 0xe8211000 irq 17 DMA
[   17.871267] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 19
[   18.329957] ath_rate_sample: 1.2 (0.9.3)
[   18.330788] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   18.330795] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   18.330806] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   18.330812] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   18.330817] wifi0: mac 5.9 phy 4.3 radio 4.6
[   18.330822] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   18.330824] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   18.330826] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   18.330828] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   18.330829] wifi0: Use hw queue 8 for CAB traffic
[   18.330831] wifi0: Use hw queue 9 for beacons
[   18.350680] wifi0: Atheros 5212: mem=0xe8200000, irq=19
[   18.357828] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   18.528071] fuse init (API version 7.8)
[   18.581946] lp: driver loaded but no devices found
[   18.641411] Adding 1510068k swap on /dev/disk/by-uuid/ad288e35-dddc-4042-a7ae-f319369f2133.  Priority:-1 extents:1 across:1510068k
[   18.786011] EXT3 FS on hda1, internal journal
```

---

### Post by kuja on 2007-06-21
ideally you could have gzipped the log files and attached them. But lets have a l ooksie at what we've got .....



It looks like most of the stuff near the end of the crash is wireless related. Try running without wireless loaded/in use for a while and see if the crashes continue, perhaps the wireless drivers are causing the crashes.

---

### Post by Keisad on 2007-06-22
I think disabling the wireless seemed to help, although I would like to test that theory a little more. I had my computer up and running for a couple hours without crashing at all. I was recording, playing linux native and wine-emulated games and it worked just fine.

There's something a little funny though, even though it's relevancy is questionable.

After I had my computer up and running successfully while my wireless was disabled, I was then unable to connect to my wireless network. It appeared to be connected, it said everything was just peachy, but it wasn't retrieving websites or downloading updates. Just saying though, it may not have anything in common.

---

### Post by kuja on 2007-06-22
mmhmm, like I thought. Guess the wireless driver isn't too stable. I have no idea of anything you can do about it though, but at least you've narrowed in on the probable problem.

---

### Post by OutCell on 2007-06-22
I have a theory (At least for my freezing problem) which i don't like.. I usually get 3-5 freezes per day but since yesterday and after turning off the Desktop Effects i have had none..
Now even though this fixed the problem of freezing, i really miss the Desktop Effects and want them back :(

I don't know what to do now, is there a fix after i narrowed the problem to the Desktop Effects?

---

### Post by i0Null on 2007-06-22
I get this sometimes. My common workaround is by switching to another session, killing the process and switching back to X.

---

### Post by OutCell on 2007-06-22
> **i0Null said:**
> I get this sometimes. My common workaround is by switching to another session, killing the process and switching back to X.

Could you please clarify a bit, i am a newbie to the whole linux life style lol

---

### Post by Keisad on 2007-06-22
Ok. More updates.

I am not so sure it's my wireless anymore. But it seems that if I leave my computer on and unattended for a while, and then come back and try to do anythign it freezes up with the first action I take, could be launching the command line or typing a password.

Any thoughts?

---

### Post by i0Null on 2007-06-22
> **OutCell said:**
> Could you please clarify a bit, i am a newbie to the whole linux life style lol

You can switch to your first session by pressing Ctrl+Alt+F1, and your second by Ctrl+Alt+F2 etc.. (X usually sits on top of 7)

So for example: you can switch to your first, log into it, and use commands such as 'ps' or 'top' to list your current processes and then use 'kill' or 'killall' to terminate the relevant process id or name. You can then switch back to X (Ctrl+Alt+F7).

Hope this helps
- i0null

---

### Post by Beefeater on 2007-06-22
I've had this problem on two computers.
One is a stationary beast that I unfortunately haven't seen for 10 months due to traveling.
The other one is my DELL laptop.

It's been connected to network/wireless on both of them.

I can't say why but I can say how.
Switched kernel up and down back and forth and finally I got two computers that never freezes.

Don't know if it will help anyone but it fixed the problem for me, 100%.

---

### Post by OutCell on 2007-06-22
> **i0Null said:**
> You can switch to your first session by pressing Ctrl+Alt+F1, and your second by Ctrl+Alt+F2 etc.. (X usually sits on top of 7)

So for example: you can switch to your first, log into it, and use commands such as 'ps' or 'top' to list your current processes and then use 'kill' or 'killall' to terminate the relevant process id or name. You can then switch back to X (Ctrl+Alt+F7).

Hope this helps
- i0null

Thanks.. I wasn't able to switch or do anything when the laptop froze except move the mouse, but i only tried the Ctrl+Alt+F1 (I read about this when i was searching for a fix a couple of days ago).. I will try Ctrl+Alt+F2 the next time and see if anything changes..

---

### Post by OutCell on 2007-06-22
> **Beefeater said:**
> I've had this problem on two computers.
One is a stationary beast that I unfortunately haven't seen for 10 months due to traveling.
The other one is my DELL laptop.

It's been connected to network/wireless on both of them.

I can't say why but I can say how.
Switched kernel up and down back and forth and finally I got two computers that never freezes.

Don't know if it will help anyone but it fixed the problem for me, 100%.

How did you fix them??

I did notice that the boot loader had 2 Ubuntu generic, with different kernel numbers (I was wondering why did i have 2 instead of one).. One was number.number.16, and the other was number.number.15 (If i remember correctly)..

---

### Post by incubus on 2007-06-22
> **OutCell said:**
> How did you fix them??

I did notice that the boot loader had 2 Ubuntu generic, with different kernel numbers (I was wondering why did i have 2 instead of one).. One was number.number.16, and the other was number.number.15 (If i remember correctly)..

That's because Ubuntu upgraded your kernel and kept the old one as a backup.  You could try running the old one to see if it solves the issue.

Since you're not the OP, it might help if you would also post your specs and log files (as suggested by kuja).

incubus

---

### Post by Keisad on 2007-06-22
Yeah, I know what your about. Spill the beans! Which kernel did you use?

---

### Post by Beefeater on 2007-06-22
> **OutCell said:**
> How did you fix them??

I did notice that the boot loader had 2 Ubuntu generic, with different kernel numbers (I was wondering why did i have 2 instead of one).. One was number.number.16, and the other was number.number.15 (If i remember correctly)..

I tried with different kernel versions.
2-6-22-rc3 on my laptop. Also worked fine with 2.6.20-16

---

### Post by Keisad on 2007-06-22
I will take your advice, oh wise beefeater, and trust my computer not to implode.

---

### Post by OutCell on 2007-06-22
> **incubus said:**
> That's because Ubuntu upgraded your kernel and kept the old one as a backup.  You could try running the old one to see if it solves the issue.

Since you're not the OP, it might help if you would also post your specs and log files (as suggested by kuja).

incubus

This is my first time to install Ubuntu on this laptop, but i did have SUSE 10.2 before (But didn't use it much) and now it's deleted. 

Ubuntu's kernels (Both 16 & 15) were there after a fresh install, I didn't upgrade. I always use the first one (The one with 16), and i never tried the one with 15.. Should i delete one of them? Would that make a difference? How do i change the kernel, say to the one that beefeater is using??

Thanks

---

### Post by Keisad on 2007-06-22
I am booting from the generic 2.6.20-16 kernel.
 
I have been the whole time, except for when I was using a low latency version, but I switched to the generic and was still having problems. 

Could I possibly install a different wireless driver? Would it help?

---

### Post by OutCell on 2007-06-23
> **Keisad said:**
> I am booting from the generic 2.6.20-16 kernel.
 
I have been the whole time, except for when I was using a low latency version, but I switched to the generic and was still having problems. 

Could I possibly install a different wireless driver? Would it help?

2.6.20-16-generic is what i am using as well.. I am certain that my freezing problem is from the Desktop Effects but the problem is that i do want to use desktop effects.. I have desktop effects disabled since yesterday and no freezes so far (Usually it was up to 5, daily).

---

### Post by OutCell on 2007-06-23
> **incubus said:**
> That's because Ubuntu upgraded your kernel and kept the old one as a backup.  You could try running the old one to see if it solves the issue.

Since you're not the OP, it might help if you would also post your specs and log files (as suggested by kuja).

incubus

I uploaded the log files (2 log files zipped in 1 tar file).. They are all stamped with today's stamp, so i don't think they are of good use since my system didn't crash today or yesterday (After disabling desktop effects)..

---

### Post by Keisad on 2007-06-23
BTW Outcell, to change which kernel you use, just keep pressing esc as you boot your computer, and a menu will pop up asking you which kernel you would like to use for that session.

---

### Post by OutCell on 2007-06-23
> **Keisad said:**
> BTW Outcell, to change which kernel you use, just keep pressing esc as you boot your computer, and a menu will pop up asking you which kernel you would like to use for that session.

Thanks

would all kernels be listed? And how would i make the kernel i choose permanent?

---

### Post by Keisad on 2007-06-23
All kernels you have installed on your computer would be listed. Switching permanently to a kernel I have no expertise on...

But, I believe by default it boots into the kernel at the top of the list.

---

### Post by OutCell on 2007-06-23
In my boot loader i have 2 kernels.. 16 & 15, but i always use the first one which is 16.

---

### Post by Keisad on 2007-06-23
Yeah the same with me. I don't think changing the kernel will do anything though. Does anyone else have suggestions? Please?

---

### Post by OutCell on 2007-06-23
> **Keisad said:**
> Yeah the same with me. I don't think changing the kernel will do anything though. Does anyone else have suggestions? Please?

Did you download Ubuntu yourself? Because i installed it from the DVD i got from Linux format magazine (UK version)..

---

### Post by Keisad on 2007-06-23
I was given a cd by my friend, and it was on cd.

I'm not sure what he did though.

The cd was burned, however.

---

### Post by OutCell on 2007-06-23
I will turn the desktop effects ON again. I didn't have any freezes after i turned it off..

---

### Post by OutCell on 2007-06-24
> **OutCell said:**
> I will turn the desktop effects ON again. I didn't have any freezes after i turned it off..

Damn it froze after 4 hours only :(

I will reinstall Ubuntu from a CD i just burned after downloading Feisty from the main Ubuntu site.
I will try the desktop effects again after that & if it freezes again, then i will just have to live without the desktop effects :( I hate that



EDIT: Yep, it freezes again :( but that's not all. I get 2 drives that are mounted on the desktop and i can't unmount them. I get the error msg "Cannot unmount volume"
details: unmount: /media/sda2/ mount disagrees with the fstab

My ubuntu installation is on sda3. How can i unmount these 2 volumes from my ubuntu desktop??

---

