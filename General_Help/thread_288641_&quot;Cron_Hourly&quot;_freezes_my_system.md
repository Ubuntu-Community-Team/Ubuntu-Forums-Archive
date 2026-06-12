---
title: "&quot;Cron Hourly&quot; freezes my system"
date: 2006-10-30
forum: General Help
---

### Post by sadiini on 2006-10-30
Every single cron job freezes my laptop. With Dapper there were no such hassle. So I must closely observe what time it is and shut down my machine every hour before cron. 
Same thing happens, when synaptic or update-notifier starts. It freezes system for on long period of time. It comes back about 15-20 min. but laptop is unusable then. 
With cron I never had so much time to wait till the end. Frustrating!

Why do I need hourly cron anyway?

I have FS K7600 laptop with 256 RAM and 1 Gb swap part. With Dapper it worked great. 

Any suggestions???

---

### Post by Azathoth_ on 2006-10-30
What is your script you add to cron?

---

### Post by jordilin on 2006-10-30
show us your cron, and take a look at system logs at /var/log/messages, to see the cause of such crashes.

---

### Post by sadiini on 2006-10-30
Crontab

I must shut my system down for now

---

### Post by sadiini on 2006-10-30
Oct 30 10:11:31 indrek-laptop kernel: [17182670.712000] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:40:95:08:e3:50:08:00 SRC=169.254.228.57 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=51863 PROTO=UDP SPT=137 DPT=137 LEN=58 
Oct 30 10:12:33 indrek-laptop kernel: [17182732.252000] Inbound IN=ppp0 OUT= MAC= SRC=141.104.27.241 DST=84.50.40.82 LEN=404 TOS=0x00 PREC=0x00 TTL=55 ID=35119 PROTO=UDP SPT=30374 DPT=1026 LEN=384 
Oct 30 10:15:33 indrek-laptop kernel: [17182912.008000] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:40:95:08:e3:50:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=330 TOS=0x00 PREC=0x00 TTL=128 ID=60933 PROTO=UDP SPT=68 DPT=67 LEN=310 
Oct 30 10:15:36 indrek-laptop kernel: [17182916.008000] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:40:95:08:e3:50:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=330 TOS=0x00 PREC=0x00 TTL=128 ID=61022 PROTO=UDP SPT=68 DPT=67 LEN=310 
Oct 30 10:15:45 indrek-laptop kernel: [17182924.008000] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:40:95:08:e3:50:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=330 TOS=0x00 PREC=0x00 TTL=128 ID=61207 PROTO=UDP SPT=68 DPT=67 LEN=310 
Oct 30 10:16:00 indrek-laptop kernel: [17182939.008000] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:40:95:08:e3:50:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=330 TOS=0x00 PREC=0x00 TTL=128 ID=61827 PROTO=UDP SPT=68 DPT=67 LEN=310 
Oct 30 10:17:54 indrek-laptop kernel: [17183051.120000] Inbound IN=ppp0 OUT= MAC= SRC=221.171.84.36 DST=84.50.40.82 LEN=78 TOS=0x00 PREC=0x00 TTL=104 ID=34198 PROTO=UDP SPT=1026 DPT=137 LEN=58 
Oct 30 10:20:25 indrek-laptop kernel: [17183197.592000] Inbound IN=ppp0 OUT= MAC= SRC=139.86.141.2 DST=84.50.40.82 LEN=514 TOS=0x00 PREC=0x00 TTL=54 ID=9360 PROTO=UDP SPT=30374 DPT=1026 LEN=494 
Oct 30 10:21:28 indrek-laptop kernel: [17183258.984000] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:40:95:08:e3:50:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=330 TOS=0x00 PREC=0x00 TTL=128 ID=6736 PROTO=UDP SPT=68 DPT=67 LEN=310 
Oct 30 10:21:45 indrek-laptop kernel: [17183261.984000] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:40:95:08:e3:50:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=330 TOS=0x00 PREC=0x00 TTL=128 ID=6829 PROTO=UDP SPT=68 DPT=67 LEN=310 
Oct 30 10:21:53 indrek-laptop kernel: [17183271.044000] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:40:95:08:e3:50:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=330 TOS=0x00 PREC=0x00 TTL=128 ID=7158 PROTO=UDP SPT=68 DPT=67 LEN=310 
Oct 30 10:21:58 indrek-laptop kernel: [17183284.780000] eth0: link down
Oct 30 10:24:03 indrek-laptop pppd[4998]: No response to 4 echo-requests
Oct 30 10:24:33 indrek-laptop pppd[4998]: Serial link appears to be disconnected.
Oct 30 10:24:36 indrek-laptop pppd[4998]: Connect time 61.5 minutes.
Oct 30 10:24:44 indrek-laptop pppd[4998]: Sent 329881 bytes, received 4223265 bytes.
Oct 30 10:24:57 indrek-laptop pppd[4998]: Connection terminated.
Oct 30 10:24:57 indrek-laptop pppd[4998]: Modem hangup
Oct 30 10:25:53 indrek-laptop pppd[4998]: Timeout waiting for PADO packets
Oct 30 10:28:12 indrek-laptop pppd[4998]: Timeout waiting for PADO packets
Oct 30 10:29:34 indrek-laptop pppd[4998]: Timeout waiting for PADO packets
Oct 30 10:30:59 indrek-laptop pppd[4998]: Timeout waiting for PADO packets
Oct 30 10:32:16 indrek-laptop pppd[4998]: Timeout waiting for PADO packets
Oct 30 10:32:35 indrek-laptop kernel: [17183933.936000] mtrr: no more MTRRs available
Oct 30 10:32:36 indrek-laptop last message repeated 3 times
Oct 30 10:33:17 indrek-laptop gconfd (indrek-4732): Aadress "xml:readwrite:/home/indrek/.gconf" lahendati positsioonil 0 kirjutatavaks seadistuste allikaks
Oct 30 10:33:20 indrek-laptop pppd[4998]: Timeout waiting for PADO packets
Oct 30 10:34:26 indrek-laptop pppd[4998]: Timeout waiting for PADO packets
Oct 30 10:35:31 indrek-laptop pppd[4998]: Timeout waiting for PADO packets
Oct 30 10:36:36 indrek-laptop pppd[4998]: Timeout waiting for PADO packets
Oct 30 10:37:41 indrek-laptop pppd[4998]: Timeout waiting for PADO packets
Oct 30 10:37:41 indrek-laptop pppd[4998]: Exit.
Oct 30 10:40:57 indrek-laptop kernel: [17184436.140000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Oct 30 10:40:58 indrek-laptop kernel: [17184436.140000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 30 10:41:22 indrek-laptop pppd[6638]: Plugin rp-pppoe.so loaded.
Oct 30 10:41:22 indrek-laptop pppd[6640]: pppd 2.4.4 started by indrek, uid 1000
Oct 30 10:41:22 indrek-laptop pppd[6640]: PPP session is 239
Oct 30 10:41:22 indrek-laptop pppd[6640]: Using interface ppp0
Oct 30 10:41:22 indrek-laptop pppd[6640]: Connect: ppp0 <--> eth0
Oct 30 10:41:22 indrek-laptop pppd[6640]: PAP authentication succeeded
Oct 30 10:41:22 indrek-laptop pppd[6640]: peer from calling number 00:90:1A:A0:31:D6 authorized
Oct 30 10:41:22 indrek-laptop pppd[6640]: local  IP address 84.50.155.47
Oct 30 10:41:22 indrek-laptop pppd[6640]: remote IP address 213.219.88.1
Oct 30 10:41:22 indrek-laptop pppd[6640]: primary   DNS address 194.126.115.18
Oct 30 10:41:22 indrek-laptop pppd[6640]: secondary DNS address 194.126.101.34
Oct 30 10:42:16 indrek-laptop pppd[6640]: Terminating on signal 15
Oct 30 10:42:17 indrek-laptop pppd[6640]: Connect time 0.9 minutes.
Oct 30 10:42:17 indrek-laptop pppd[6640]: Sent 807 bytes, received 1056 bytes.
Oct 30 10:42:17 indrek-laptop pppd[6640]: Connection terminated.
Oct 30 10:42:17 indrek-laptop pppd[6640]: Exit.
Oct 30 10:42:21 indrek-laptop pppd[6860]: Plugin rp-pppoe.so loaded.
Oct 30 10:42:21 indrek-laptop pppd[6862]: pppd 2.4.4 started by indrek, uid 1000
Oct 30 10:42:21 indrek-laptop pppd[6862]: PPP session is 249
Oct 30 10:42:21 indrek-laptop pppd[6862]: Using interface ppp0
Oct 30 10:42:21 indrek-laptop pppd[6862]: Connect: ppp0 <--> eth0
Oct 30 10:42:22 indrek-laptop pppd[6862]: PAP authentication succeeded
Oct 30 10:42:22 indrek-laptop pppd[6862]: peer from calling number 00:90:1A:A0:31:D6 authorized
Oct 30 10:42:22 indrek-laptop pppd[6862]: local  IP address 213.35.180.242
Oct 30 10:42:22 indrek-laptop pppd[6862]: remote IP address 213.219.88.1
Oct 30 10:42:22 indrek-laptop pppd[6862]: primary   DNS address 194.126.115.18
Oct 30 10:42:22 indrek-laptop pppd[6862]: secondary DNS address 194.126.101.34
Oct 30 10:44:05 indrek-laptop gconfd (indrek-4732): Väljumine
Oct 30 10:44:52 indrek-laptop exiting on signal 15
Oct 30 13:40:36 indrek-laptop syslogd 1.4.1#18ubuntu6: restart.
Oct 30 13:40:36 indrek-laptop kernel: Inspecting /boot/System.map-2.6.17-10-386
Oct 30 13:40:37 indrek-laptop kernel: Loaded 22425 symbols from /boot/System.map-2.6.17-10-386.
Oct 30 13:40:37 indrek-laptop kernel: Symbols match kernel version 2.6.17.
Oct 30 13:40:37 indrek-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] Linux version 2.6.17-10-386 (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40 UTC 2006 (Ubuntu 2.6.17-10.33-386)
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] BIOS-provided physical RAM map:
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000000dff0000 (usable)
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000]  BIOS-e820: 000000000dff0000 - 000000000dffffc0 (ACPI data)
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000]  BIOS-e820: 000000000dffffc0 - 000000000e000000 (ACPI NVS)
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] 0MB HIGHMEM available.
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] 223MB LOWMEM available.
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] DMI 2.3 present.
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x1008
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0e000000:f1f80000)
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] Built 1 zonelists
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] Kernel command line: root=UUID=8b0ba989-2ee6-42d9-916e-c585cc2f1303 ro quiet splash
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] Enabling fast FPU save and restore... done.
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] Enabling unmasked SIMD FPU exception support... done.
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] Initializing CPU#0
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] Detected 1990.392 MHz processor.
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] Using pmtmr for high-res timesource
Oct 30 13:40:37 indrek-laptop kernel: [17179569.184000] Console: colour VGA+ 80x25
Oct 30 13:40:37 indrek-laptop kernel: [17179573.156000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.156000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.168000] Memory: 216596k/229312k available (1829k kernel code, 12164k reserved, 1038k data, 288k init, 0k highmem)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.168000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 30 13:40:37 indrek-laptop kernel: [17179573.248000] Calibrating delay using timer specific routine.. 3984.59 BogoMIPS (lpj=7969196)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.248000] Security Framework v1.0.0 initialized
Oct 30 13:40:37 indrek-laptop kernel: [17179573.248000] SELinux:  Disabled at boot.
Oct 30 13:40:37 indrek-laptop kernel: [17179573.248000] Mount-cache hash table entries: 512
Oct 30 13:40:37 indrek-laptop kernel: [17179573.248000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.248000] CPU: L2 Cache: 512K (64 bytes/line)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.248000] CPU: AMD mobile AMD Athlon(tm) XP-M 2600+ stepping 00
Oct 30 13:40:37 indrek-laptop kernel: [17179573.248000] Checking 'hlt' instruction... OK.
Oct 30 13:40:37 indrek-laptop kernel: [17179573.264000] SMP alternatives: switching to UP code
Oct 30 13:40:37 indrek-laptop kernel: [17179573.264000] Freeing SMP alternatives: 0k freed
Oct 30 13:40:37 indrek-laptop kernel: [17179573.264000] checking if image is initramfs... it is
Oct 30 13:40:37 indrek-laptop kernel: [17179573.860000] Freeing initrd memory: 6588k freed
Oct 30 13:40:37 indrek-laptop kernel: [17179573.860000] ACPI: Core revision 20060707
Oct 30 13:40:37 indrek-laptop kernel: [17179573.860000] ACPI: Looking for DSDT ... not found!
Oct 30 13:40:37 indrek-laptop kernel: [17179573.860000] ACPI: setting ELCR to 0200 (from 0c20)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.872000] NET: Registered protocol family 16
Oct 30 13:40:37 indrek-laptop kernel: [17179573.872000] EISA bus registered
Oct 30 13:40:37 indrek-laptop kernel: [17179573.872000] ACPI: bus type pci registered
Oct 30 13:40:37 indrek-laptop kernel: [17179573.872000] PCI: PCI BIOS revision 2.10 entry at 0xe8b24, last bus=1
Oct 30 13:40:37 indrek-laptop kernel: [17179573.872000] PCI: Using configuration type 1
Oct 30 13:40:37 indrek-laptop kernel: [17179573.872000] Setting up standard PCI resources
Oct 30 13:40:37 indrek-laptop kernel: [17179573.876000] ACPI: Interpreter enabled
Oct 30 13:40:37 indrek-laptop kernel: [17179573.876000] ACPI: Using PIC for interrupt routing
Oct 30 13:40:37 indrek-laptop kernel: [17179573.876000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.876000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Oct 30 13:40:37 indrek-laptop kernel: [17179573.880000] PCI quirk: region 1000-107f claimed by vt8235 PM
Oct 30 13:40:37 indrek-laptop kernel: [17179573.880000] PCI quirk: region 1400-140f claimed by vt8235 SMB
Oct 30 13:40:37 indrek-laptop kernel: [17179573.880000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
Oct 30 13:40:37 indrek-laptop kernel: [17179573.884000] ACPI: Embedded Controller [EC0] (gpe 5) interrupt mode.
Oct 30 13:40:37 indrek-laptop kernel: [17179573.884000] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 *10 11)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.884000] ACPI: PCI Interrupt Link [LNKB] (IRQs 7) *11
Oct 30 13:40:37 indrek-laptop kernel: [17179573.884000] ACPI: PCI Interrupt Link [LNKC] (IRQs *5 7 10 11)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.884000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 *11)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.884000] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 30 13:40:37 indrek-laptop kernel: [17179573.884000] pnp: PnP ACPI init
Oct 30 13:40:37 indrek-laptop kernel: [17179573.884000] pnp: PnP ACPI: found 9 devices
Oct 30 13:40:37 indrek-laptop kernel: [17179573.884000] PnPBIOS: Disabled by ACPI PNP
Oct 30 13:40:37 indrek-laptop kernel: [17179573.884000] PCI: Using ACPI for IRQ routing
Oct 30 13:40:37 indrek-laptop kernel: [17179573.884000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000] pnp: 00:07: ioport range 0x330-0x331 has been reserved
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000] pnp: 00:07: ioport range 0x1000-0x107f could not be reserved
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000] pnp: 00:07: ioport range 0x1400-0x140f has been reserved
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000] PCI: Bridge: 0000:00:01.0
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000]   IO window: c000-dfff
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000]   MEM window: e0000000-efffffff
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000]   PREFETCH window: 90000000-9fffffff
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000] PCI: Bus 2, cardbus bridge: 0000:00:09.0
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000]   IO window: 00001800-000018ff
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000]   IO window: 00001c00-00001cff
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000]   PREFETCH window: 10000000-11ffffff
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000]   MEM window: 12000000-13ffffff
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
Oct 30 13:40:37 indrek-laptop kernel: [17179573.888000] NET: Registered protocol family 2
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] TCP: Hash tables configured (established 8192 bind 4096)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] TCP reno registered
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] Simple Boot Flag at 0x37 set to 0x1
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] audit: initializing netlink socket (disabled)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] audit(1162215607.928:1): initialized
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] VFS: Disk quotas dquot_6.5.1
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] Initializing Cryptographic API
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] io scheduler noop registered
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] io scheduler anticipatory registered
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] io scheduler deadline registered
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] io scheduler cfq registered (default)
Oct 30 13:40:37 indrek-laptop kernel: [17179573.928000] isapnp: Scanning for PnP cards...
Oct 30 13:40:37 indrek-laptop kernel: [17179574.280000] isapnp: No Plug & Play device found
Oct 30 13:40:37 indrek-laptop kernel: [17179574.304000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 30 13:40:37 indrek-laptop kernel: [17179574.304000] mice: PS/2 mouse device common for all mice
Oct 30 13:40:37 indrek-laptop kernel: [17179574.308000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 30 13:40:37 indrek-laptop kernel: [17179574.308000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Oct 30 13:40:37 indrek-laptop kernel: [17179574.308000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Oct 30 13:40:37 indrek-laptop kernel: [17179574.308000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 30 13:40:37 indrek-laptop kernel: [17179574.308000] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 30 13:40:37 indrek-laptop kernel: [17179574.312000] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 30 13:40:37 indrek-laptop kernel: [17179574.312000] EISA: Probing bus 0 at eisa.0
Oct 30 13:40:37 indrek-laptop kernel: [17179574.312000] Cannot allocate resource for EISA slot 1
Oct 30 13:40:37 indrek-laptop kernel: [17179574.312000] EISA: Detected 0 cards.
Oct 30 13:40:37 indrek-laptop kernel: [17179574.312000] TCP bic registered
Oct 30 13:40:37 indrek-laptop kernel: [17179574.312000] NET: Registered protocol family 1
Oct 30 13:40:37 indrek-laptop kernel: [17179574.312000] NET: Registered protocol family 8
Oct 30 13:40:37 indrek-laptop kernel: [17179574.312000] NET: Registered protocol family 20
Oct 30 13:40:37 indrek-laptop kernel: [17179574.312000] Using IPI Shortcut mode
Oct 30 13:40:37 indrek-laptop kernel: [17179574.312000] ACPI: (supports S0 S3 S4 S5)
Oct 30 13:40:37 indrek-laptop kernel: [17179574.312000] Freeing unused kernel memory: 288k freed
Oct 30 13:40:37 indrek-laptop kernel: [17179574.316000] input: AT Translated Set 2 keyboard as /class/input/input0
Oct 30 13:40:37 indrek-laptop kernel: [17179575.492000] Capability LSM initialized
Oct 30 13:40:37 indrek-laptop kernel: [17179575.524000] ACPI: CPU0 (power states: C1[C1] C2[C2])
Oct 30 13:40:37 indrek-laptop kernel: [17179575.816000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
Oct 30 13:40:37 indrek-laptop kernel: [17179575.816000] ACPI: Unable to derive IRQ for device 0000:00:11.1
Oct 30 13:40:37 indrek-laptop kernel: [17179575.816000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
Oct 30 13:40:37 indrek-laptop kernel: [17179575.816000] VP_IDE: chipset revision 6
Oct 30 13:40:37 indrek-laptop kernel: [17179575.816000] VP_IDE: not 100%% native mode: will probe irqs later
Oct 30 13:40:37 indrek-laptop kernel: [17179575.816000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Oct 30 13:40:37 indrek-laptop kernel: [17179575.816000]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
Oct 30 13:40:37 indrek-laptop kernel: [17179575.816000]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:pio, hdd:DMA
Oct 30 13:40:37 indrek-laptop kernel: [17179576.232000] hda: TOSHIBA MK3021GAS, ATA DISK drive
Oct 30 13:40:37 indrek-laptop kernel: [17179576.904000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Oct 30 13:40:37 indrek-laptop kernel: [17179578.112000] hdd: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, ATAPI CD/DVD-ROM drive
Oct 30 13:40:37 indrek-laptop kernel: [17179578.168000] ide1 at 0x170-0x177,0x376 on irq 15
Oct 30 13:40:37 indrek-laptop kernel: [17179578.176000] hda: max request size: 128KiB
Oct 30 13:40:37 indrek-laptop kernel: [17179578.184000] hda: 58605120 sectors (30005 MB), CHS=58140/16/63, UDMA(100)
Oct 30 13:40:37 indrek-laptop kernel: [17179578.184000] hda: cache flushes supported
Oct 30 13:40:37 indrek-laptop kernel: [17179578.184000]  hda: hda1 hda2 < hda5 hda6 hda7 >
Oct 30 13:40:37 indrek-laptop kernel: [17179578.332000] hdd: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Oct 30 13:40:37 indrek-laptop kernel: [17179578.332000] Uniform CD-ROM driver Revision: 3.20
Oct 30 13:40:37 indrek-laptop kernel: [17179578.684000] usbcore: registered new driver usbfs
Oct 30 13:40:37 indrek-laptop kernel: [17179578.684000] usbcore: registered new driver hub
Oct 30 13:40:37 indrek-laptop kernel: [17179578.704000] USB Universal Host Controller Interface driver v3.0
Oct 30 13:40:37 indrek-laptop kernel: [17179578.704000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Oct 30 13:40:37 indrek-laptop kernel: [17179578.704000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 30 13:40:37 indrek-laptop kernel: [17179578.704000] uhci_hcd 0000:00:10.0: UHCI Host Controller
Oct 30 13:40:37 indrek-laptop kernel: [17179578.708000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Oct 30 13:40:37 indrek-laptop kernel: [17179578.708000] uhci_hcd 0000:00:10.0: irq 10, io base 0x00001200
Oct 30 13:40:37 indrek-laptop kernel: [17179578.708000] usb usb1: configuration #1 chosen from 1 choice
Oct 30 13:40:37 indrek-laptop kernel: [17179578.708000] hub 1-0:1.0: USB hub found
Oct 30 13:40:37 indrek-laptop kernel: [17179578.708000] hub 1-0:1.0: 2 ports detected
Oct 30 13:40:37 indrek-laptop kernel: [17179578.812000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Oct 30 13:40:37 indrek-laptop kernel: [17179578.812000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Oct 30 13:40:37 indrek-laptop kernel: [17179578.812000] ehci_hcd 0000:00:10.3: EHCI Host Controller
Oct 30 13:40:37 indrek-laptop kernel: [17179578.812000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 2
Oct 30 13:40:37 indrek-laptop kernel: [17179578.812000] ehci_hcd 0000:00:10.3: irq 11, io mem 0xf0000000
Oct 30 13:40:37 indrek-laptop kernel: [17179578.812000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 30 13:40:37 indrek-laptop kernel: [17179578.812000] usb usb2: configuration #1 chosen from 1 choice
Oct 30 13:40:37 indrek-laptop kernel: [17179578.812000] hub 2-0:1.0: USB hub found
Oct 30 13:40:37 indrek-laptop kernel: [17179578.812000] hub 2-0:1.0: 4 ports detected
Oct 30 13:40:37 indrek-laptop kernel: [17179578.916000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
Oct 30 13:40:37 indrek-laptop kernel: [17179578.916000] PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 7
Oct 30 13:40:37 indrek-laptop kernel: [17179578.916000] uhci_hcd 0000:00:10.1: UHCI Host Controller
Oct 30 13:40:37 indrek-laptop kernel: [17179578.916000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Oct 30 13:40:37 indrek-laptop kernel: [17179578.916000] uhci_hcd 0000:00:10.1: irq 7, io base 0x00001300
Oct 30 13:40:37 indrek-laptop kernel: [17179578.916000] usb usb3: configuration #1 chosen from 1 choice
Oct 30 13:40:37 indrek-laptop kernel: [17179578.916000] hub 3-0:1.0: USB hub found
Oct 30 13:40:37 indrek-laptop kernel: [17179578.916000] hub 3-0:1.0: 2 ports detected
Oct 30 13:40:37 indrek-laptop kernel: [17179594.256000] Real Time Clock Driver v1.12ac
Oct 30 13:40:37 indrek-laptop kernel: [17179594.368000] input: PC Speaker as /class/input/input1
Oct 30 13:40:37 indrek-laptop kernel: [17179594.464000] NET: Registered protocol family 23
Oct 30 13:40:37 indrek-laptop kernel: [17179594.588000] Linux agpgart interface v0.101 (c) Dave Jones
Oct 30 13:40:37 indrek-laptop kernel: [17179594.592000] agpgart: Detected VIA Apollo Pro266 chipset
Oct 30 13:40:37 indrek-laptop kernel: [17179594.600000] agpgart: AGP aperture is 64M @ 0xa0000000
Oct 30 13:40:37 indrek-laptop kernel: [17179594.688000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 30 13:40:37 indrek-laptop kernel: [17179594.700000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 30 13:40:37 indrek-laptop kernel: [17179594.712000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
Oct 30 13:40:37 indrek-laptop kernel: [17179594.712000] Yenta: CardBus bridge found at 0000:00:09.0 [1734:1054]
Oct 30 13:40:37 indrek-laptop kernel: [17179594.712000] Yenta: Using CSCINT to route CSC interrupts to PCI
Oct 30 13:40:37 indrek-laptop kernel: [17179594.712000] Yenta: Routing CardBus interrupts to PCI
Oct 30 13:40:37 indrek-laptop kernel: [17179594.712000] Yenta TI: socket 0000:00:09.0, mfunc 0x010c1002, devctl 0x44
Oct 30 13:40:37 indrek-laptop kernel: [17179594.828000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
Oct 30 13:40:37 indrek-laptop kernel: [17179594.956000] Yenta: ISA IRQ mask 0x0050, PCI irq 7
Oct 30 13:40:37 indrek-laptop kernel: [17179594.956000] Socket status: 30000006
Oct 30 13:40:37 indrek-laptop kernel: [17179594.976000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Oct 30 13:40:37 indrek-laptop kernel: [17179594.980000] eth0: VIA Rhine II at 0x1e300, 00:40:d0:5a:83:7d, IRQ 10.
Oct 30 13:40:37 indrek-laptop kernel: [17179594.980000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
Oct 30 13:40:37 indrek-laptop kernel: [17179595.140000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
Oct 30 13:40:37 indrek-laptop kernel: [17179595.140000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
Oct 30 13:40:37 indrek-laptop kernel: [17179595.248000] eth0: link down
Oct 30 13:40:37 indrek-laptop kernel: [17179595.428000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0
Oct 30 13:40:37 indrek-laptop kernel: [17179595.460000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
Oct 30 13:40:37 indrek-laptop kernel: [17179595.484000] ts: Compaq touchscreen protocol output
Oct 30 13:40:37 indrek-laptop kernel: [17179595.652000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
Oct 30 13:40:37 indrek-laptop kernel: [17179595.684000] cs: IO port probe 0x100-0x3af: clean.
Oct 30 13:40:37 indrek-laptop kernel: [17179595.684000] cs: IO port probe 0x3e0-0x4ff: clean.
Oct 30 13:40:37 indrek-laptop kernel: [17179595.688000] cs: IO port probe 0x820-0x8ff: clean.
Oct 30 13:40:37 indrek-laptop kernel: [17179595.688000] cs: IO port probe 0xc00-0xcf7: clean.
Oct 30 13:40:37 indrek-laptop kernel: [17179595.688000] cs: IO port probe 0xa00-0xaff: clean.
Oct 30 13:40:37 indrek-laptop kernel: [17179596.332000] NET: Registered protocol family 17
Oct 30 13:40:37 indrek-laptop kernel: [17179596.452000] lp: driver loaded but no devices found
Oct 30 13:40:37 indrek-laptop kernel: [17179596.920000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Oct 30 13:40:37 indrek-laptop kernel: [17179596.920000] md: bitmap version 4.39
Oct 30 13:40:37 indrek-laptop kernel: [17179597.116000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
Oct 30 13:40:37 indrek-laptop kernel: [17179599.048000] kjournald starting.  Commit interval 5 seconds
Oct 30 13:40:37 indrek-laptop kernel: [17179599.056000] EXT3 FS on hda7, internal journal
Oct 30 13:40:37 indrek-laptop kernel: [17179599.056000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 30 13:40:37 indrek-laptop kernel: [17179599.108000] NTFS driver 2.1.27 [Flags: R/O MODULE].
Oct 30 13:40:37 indrek-laptop kernel: [17179599.180000] NTFS volume version 3.1.
Oct 30 13:40:37 indrek-laptop kernel: [17179605.536000] ACPI: AC Adapter [AC] (on-line)
Oct 30 13:40:37 indrek-laptop kernel: [17179605.572000] ACPI: Battery Slot [BAT0] (battery present)
Oct 30 13:40:37 indrek-laptop kernel: [17179605.588000] ACPI: Power Button (FF) [PWRF]
Oct 30 13:40:37 indrek-laptop kernel: [17179605.588000] ACPI: Sleep Button (CM) [SBTN]
Oct 30 13:40:37 indrek-laptop kernel: [17179605.588000] ACPI: Lid Switch [LID]
Oct 30 13:40:37 indrek-laptop kernel: [17179605.720000] pcc_acpi: loading...
Oct 30 13:40:37 indrek-laptop kernel: [17179606.072000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
Oct 30 13:40:37 indrek-laptop kernel: [17179606.096000] powernow: SGTC: 13333
Oct 30 13:40:37 indrek-laptop kernel: [17179606.096000] powernow: Minimum speed 663 MHz. Maximum speed 1990 MHz.
Oct 30 13:40:38 indrek-laptop kernel: [17179608.036000] mtrr: no more MTRRs available
Oct 30 13:40:38 indrek-laptop last message repeated 3 times
Oct 30 13:40:39 indrek-laptop hpiod: 1.6.9 accepting connections at 2208... 
Oct 30 13:40:40 indrek-laptop kernel: [17179610.128000] apm: BIOS not found.
Oct 30 13:40:48 indrek-laptop dhcdbd: Started up.
Oct 30 13:40:49 indrek-laptop kernel: [17179619.324000] Bluetooth: Core ver 2.8
Oct 30 13:40:49 indrek-laptop kernel: [17179619.324000] NET: Registered protocol family 31
Oct 30 13:40:49 indrek-laptop kernel: [17179619.324000] Bluetooth: HCI device and connection manager initialized
Oct 30 13:40:49 indrek-laptop kernel: [17179619.324000] Bluetooth: HCI socket layer initialized
Oct 30 13:40:50 indrek-laptop kernel: [17179619.360000] Bluetooth: L2CAP ver 2.8
Oct 30 13:40:50 indrek-laptop kernel: [17179619.360000] Bluetooth: L2CAP socket layer initialized
Oct 30 13:40:50 indrek-laptop kernel: [17179619.392000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
Oct 30 13:40:50 indrek-laptop kernel: [17179619.412000] Bluetooth: RFCOMM socket layer initialized
Oct 30 13:40:50 indrek-laptop kernel: [17179619.412000] Bluetooth: RFCOMM TTY layer initialized
Oct 30 13:40:50 indrek-laptop kernel: [17179619.412000] Bluetooth: RFCOMM ver 1.7
Oct 30 13:40:56 indrek-laptop gconfd (indrek-4709): käivitamine (versioon 2.16.0), pid 4709 kasutaja 'indrek'
Oct 30 13:40:56 indrek-laptop gconfd (indrek-4709): Aadress "xml:readonly:/etc/gconf/gconf.xml.mandatory" lahendati positsioonil 0 ainult lugemist võimaldavaks seadistuste allikaks
Oct 30 13:40:56 indrek-laptop gconfd (indrek-4709): Aadress "xml:readwrite:/home/indrek/.gconf" lahendati positsioonil 1 kirjutatavaks seadistuste allikaks
Oct 30 13:40:56 indrek-laptop gconfd (indrek-4709): Aadress "xml:readonly:/etc/gconf/gconf.xml.defaults" lahendati positsioonil 2 ainult lugemist võimaldavaks seadistuste allikaks
Oct 30 13:40:56 indrek-laptop gconfd (indrek-4709): Aadress "xml:readonly:/var/lib/gconf/debian.defaults" lahendati positsioonil 3 ainult lugemist võimaldavaks seadistuste allikaks
Oct 30 13:40:56 indrek-laptop gconfd (indrek-4709): Aadress "xml:readonly:/var/lib/gconf/defaults" lahendati positsioonil 4 ainult lugemist võimaldavaks seadistuste allikaks
Oct 30 13:41:01 indrek-laptop kernel: [17179630.920000] NET: Registered protocol family 10
Oct 30 13:41:01 indrek-laptop kernel: [17179630.920000] lo: Disabled Privacy Extensions
Oct 30 13:41:01 indrek-laptop kernel: [17179630.920000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 30 13:41:01 indrek-laptop kernel: [17179630.920000] IPv6 over IPv4 tunneling driver
Oct 30 13:41:09 indrek-laptop kernel: [17179638.548000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Oct 30 13:41:09 indrek-laptop kernel: [17179638.548000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 30 13:41:09 indrek-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 30 13:41:09 indrek-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 30 13:41:15 indrek-laptop gconfd (indrek-4709): Aadress "xml:readwrite:/home/indrek/.gconf" lahendati positsioonil 0 kirjutatavaks seadistuste allikaks
Oct 30 13:42:21 indrek-laptop gconfd (indrek-4709): Failed to send buffer
_____________________

/var/log/messages/

---

### Post by sadiini on 2006-10-30
I suspect, it is a Nautilus issue. I was holding few Nautilus windows open when my system constantly froze. 

O tempora, o mores.

---

