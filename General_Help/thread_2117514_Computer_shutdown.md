---
title: "Computer shutdown"
date: 2013-02-18
forum: General Help
---

### Post by Rschil on 2013-02-18
Im a new user to linux in general, and I have no idea whats going on wrong here.
 
So I installed ubuntu yesterday, all was working well. All I installed was I installed the alsamixer, and the ubuntu unrestricted extras. It worked fine all of yesterday, I was able to shut it down and turn it on, use the internet. However, when I went to turn it on today it turned off right after the I selected ubuntu (currently dualbooting with vista, plan to go full ubuntu when I get it working) it shuts the computer down completely, i dont even make it to the log in screen. Help?

---

### Post by Rschil on 2013-02-18
So, after looking around for 5 hours and after a lot, A LOT, of frustration I decided to uninstall Ubuntu and go back to my windows vista to try redownloading it via Wubi. Turns out, it wont install becuase the c:\ubuntu folder refuses to delete, and it wont give me permission to delete it. So I installed xubuntu, and after an hour it finally finished. During the first run of xubuntu, the same thing happened. Shutdown the computer completely (as if I pulled the power cord)after selecting xubuntu in the boot menu and before it even reached the log in screen.
 
 
God #$%^&*

---

### Post by bcbc on 2013-02-18
If the folder won't delete it indicates some sort of file system corruption. I'd advise running chkdsk /f on the 'drive' in question. If it's the C: drive you'll have to reboot to let it complete.

I don't know why that would make the computer shut down though. That's a bit odd.

---

### Post by Rschil on 2013-02-19
I ran CHKDSK C: /f and it recorded 0 bad files. Also noticed that after installing xubuntu the C:\ubuntu folder now contains files, where as after I uninstalled ubuntu it contained nothing and was 0 bytes. I assumed wubi created a folder named xubuntu, I find it kinda weird that the ubuntu folder worked when I installed xubuntu, but when i tried to reinstall ubuntu before xubuntu it said that the folder had to be deleted (which windows was having none of).

---

### Post by fdrake on 2013-02-19
> **Rschil said:**
> I ran CHKDSK C: /f and it recorded 0 bad files. Also noticed that after installing xubuntu the C:\ubuntu folder now contains files, where as after I uninstalled ubuntu it contained nothing and was 0 bytes. I assumed wubi created a folder named xubuntu, I find it kinda weird that the ubuntu folder worked when I installed xubuntu, but when i tried to reinstall ubuntu before xubuntu it said that the folder had to be deleted (which windows was having none of).

check if the files aren being used by a process: click Start > enter program name field "cmd" > type:
```
 openfiles / u admin_userna /p admin_pass  | find "C:\ubuntu" | more 
```
where  admin_userna= username of the administrator-level user  
       admin_pass= administrator's passwod

also check that the process wubi is not running on the background
```
tasklist |sort

```

---

### Post by Rschil on 2013-02-19
I couldn't get your first command to work, I tried using 
 
openfiles /u USERNAME /p PASSWORD |find "C:/ubuntu" |more
 
and I get a syntax error, tried putting space inbetween the | and find/more but still get the syntax error.
 
Also, I can confirm via task manager and tasklist |sort that nothing out of the ordinary/related to wubi is running.
 
Would this ubuntu folder in vista really cause my ubuntu/xubuntu to turn off my comp on boot?

---

### Post by fdrake on 2013-02-19
> **Rschil said:**
> I couldn't get your first command to work, I tried using 
 
openfiles /u USERNAME /p PASSWORD |find "C:/ubuntu" |more
 
and I get a syntax error, tried putting space inbetween the | and find/more but still get the syntax error.
 
Also, I can confirm via task manager and tasklist |sort that nothing out of the ordinary/related to wubi is running.
 
Would this ubuntu folder in vista really cause my ubuntu/xubuntu to turn off my comp on boot?


NOTE: I am not in windows at the moment so I cannot test my command . try this instead:
```

openfiles /u USERNAME /p PASSWORD |sort |more

```and check for a file inside the ubuntu folder.


------------------------Possible solutions-------------------------
boot into admin mode (usually by pressing f10 at boot time) and see if you can do something about it. Can you remove the folder completely?

or 

why don't you burn an ubuntu cd , and boot into "TRY out UBUNTU". Use the live section. Mount your windows partition and delete the file.

---

### Post by c2tarun on 2013-02-19
If nothing suggested by anyone works, then try booting in ubuntu recovery mode and share the contents of file /var/log/syslog
Also please tell the exact time when your machine gets shutdown, so that we can track that in logs.
 
This might not give a perfect solution, but it might help us in tracking your problem.
 
 
Also if you are on Dell laptop then try disabling Wi-fi and then starting Ubuntu/Xubuntu. See if the problem persists

---

### Post by Rschil on 2013-02-19
> **fdrake said:**
> NOTE: I am not in windows at the moment so I cannot test my command . try this instead:
```

openfiles /u USERNAME /p PASSWORD |sort |more

```and check for a file inside the ubuntu folder.
 
 
------------------------Possible solutions-------------------------
boot into admin mode (usually by pressing f10 at boot time) and see if you can do something about it. Can you remove the folder completely?
 
or 
 
why don't you burn an ubuntu cd , and boot into "TRY out UBUNTU". Use the live section. Mount your windows partition and delete the file.
 
That command line has a syntax error as well for me, my bios doesnt seem to have a admin mode either. I dont have any cds atm too, I might go and get some tomorrow.
 
> **c2tarun said:**
> If nothing suggested by anyone works, then try booting in ubuntu recovery mode and share the contents of file /var/log/syslog
Also please tell the exact time when your machine gets shutdown, so that we can track that in logs.
 
This might not give a perfect solution, but it might help us in tracking your problem.
 
 
Also if you are on Dell laptop then try disabling Wi-fi and then starting Ubuntu/Xubuntu. See if the problem persists
 
Ubuntu wont load in recovery mode either, same thing happens but I see text fly across the monitor beforehand. Im running on a tower too, specs from computer properties are:
 
CPU: AMD Athlon 64 x2 5200+
GPU: NVIDIA GeFore 7300 GT
2GB RAM

---

### Post by fdrake on 2013-02-19
administrator togin is not in the BIOS:[http://www.ehow.com/video_4983482_log-as-administrator-windows-vista.html](http://www.ehow.com/video_4983482_log-as-administrator-windows-vista.html)

the function key may fdiffer from computer to computer

---

### Post by Rschil on 2013-02-19
So, I got the recovery mode to work a while ago and I had no idea how. Turns out it I randomly press keys during the boot it loads (must of bumped the keyboard with my elbow)! Did it again, this time out of frustration and to my surprise it actually went into recovery mode without shutting down. Heres my syslog:

```
Feb 18 23:12:18 ubuntu kernel: imklog 5.8.6, log source = /proc/kmsg started.
Feb 18 23:12:18 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1539" x-info="http://www.rsyslog.com"] start
Feb 18 23:12:18 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Feb 18 23:12:18 ubuntu rsyslogd: rsyslogd's userid changed to 101
Feb 18 23:12:18 ubuntu rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Linux version 3.2.0-37-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 (Ubuntu 3.2.0-37.58-generic 3.2.35)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic root=UUID=5884B5E584B5C632 loop=/ubuntu/disks/root.disk ro recovery nomodeset
Feb 18 23:12:18 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Feb 18 23:12:18 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007bee0000 (usable)
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007bee0000 - 000000007bee3000 (ACPI NVS)
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007bee3000 - 000000007bef0000 (ACPI data)
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007bef0000 - 000000007bf00000 (reserved)
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007c000000 - 0000000080000000 (reserved)
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Feb 18 23:12:18 ubuntu kernel: [    0.000000] DMI 2.2 present.
Feb 18 23:12:18 ubuntu kernel: [    0.000000] DMI:   NF-M2S/NF-M2S, BIOS 6.00 PG 11/08/2006
Feb 18 23:12:18 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] No AGP bridge found
Feb 18 23:12:18 ubuntu kernel: [    0.000000] last_pfn = 0x7bee0 max_arch_pfn = 0x400000000
Feb 18 23:12:18 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Feb 18 23:12:18 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   C0000-C7FFF write-protect
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   C8000-FFFFF uncachable
Feb 18 23:12:18 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   0 base 0000000000 mask FFC0000000 write-back
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   1 base 0040000000 mask FFE0000000 write-back
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   2 base 0060000000 mask FFF0000000 write-back
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   3 base 0070000000 mask FFF8000000 write-back
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   4 base 0078000000 mask FFFC000000 write-back
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   5 base 007BF00000 mask FFFFF00000 uncachable
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   6 disabled
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   7 disabled
Feb 18 23:12:18 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb 18 23:12:18 ubuntu kernel: [    0.000000] original variable MTRRs
Feb 18 23:12:18 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 1GB, type WB
Feb 18 23:12:18 ubuntu kernel: [    0.000000] reg 1, base: 1GB, range: 512MB, type WB
Feb 18 23:12:18 ubuntu kernel: [    0.000000] reg 2, base: 1536MB, range: 256MB, type WB
Feb 18 23:12:18 ubuntu kernel: [    0.000000] reg 3, base: 1792MB, range: 128MB, type WB
Feb 18 23:12:18 ubuntu kernel: [    0.000000] reg 4, base: 1920MB, range: 64MB, type WB
Feb 18 23:12:18 ubuntu kernel: [    0.000000] reg 5, base: 1983MB, range: 1MB, type UC
Feb 18 23:12:18 ubuntu kernel: [    0.000000] total RAM covered: 1983M
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Found optimal setting for mtrr clean up
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 3      lose cover RAM: 0G
Feb 18 23:12:18 ubuntu kernel: [    0.000000] New variable MTRRs
Feb 18 23:12:18 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Feb 18 23:12:18 ubuntu kernel: [    0.000000] reg 1, base: 1983MB, range: 1MB, type UC
Feb 18 23:12:18 ubuntu kernel: [    0.000000] reg 2, base: 1984MB, range: 64MB, type UC
Feb 18 23:12:18 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000f3a00] f3a00
Feb 18 23:12:18 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 20000000
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
Feb 18 23:12:18 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000007bee0000
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  0000000000 - 007be00000 page 2M
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  007be00000 - 007bee0000 page 4k
Feb 18 23:12:18 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 7bee0000 @ 1fffc000-20000000
Feb 18 23:12:18 ubuntu kernel: [    0.000000] RAMDISK: 364d0000 - 37260000
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: RSDP 00000000000f7a10 00014 (v00 Nvidia)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: RSDT 000000007bee3040 00038 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: FACP 000000007bee30c0 00074 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: DSDT 000000007bee3180 06378 (v01 NVIDIA AWRDACPI 00001000 MSFT 0100000E)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: FACS 000000007bee0000 00040
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: SSDT 000000007bee9600 0028A (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: _HPT 000000007bee9900 00038 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000098)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: MCFG 000000007bee9980 0003C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: APIC 000000007bee9540 0007C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Feb 18 23:12:18 ubuntu kernel: [    0.000000] No NUMA configuration found
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-000000007bee0000
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000007bee0000
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   NODE_DATA [000000007bedb000 - 000000007bedffff]
Feb 18 23:12:18 ubuntu kernel: [    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff880079600000-ffff88007b5fffff] on node 0
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Zone PFN ranges:
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   Normal   empty
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Feb 18 23:12:18 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Feb 18 23:12:18 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Feb 18 23:12:18 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007bee0
Feb 18 23:12:18 ubuntu kernel: [    0.000000] On node 0 totalpages: 507503
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   DMA zone: 5 pages reserved
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   DMA zone: 3914 pages, LIFO batch:0
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   DMA32 zone: 7868 pages used for memmap
Feb 18 23:12:18 ubuntu kernel: [    0.000000]   DMA32 zone: 495652 pages, LIFO batch:31
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Feb 18 23:12:18 ubuntu kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb 18 23:12:18 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 0 dfl dfl)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: BIOS IRQ0 override ignored.
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: IRQ14 used by override.
Feb 18 23:12:18 ubuntu kernel: [    0.000000] ACPI: IRQ15 used by override.
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 18 23:12:18 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Feb 18 23:12:18 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Feb 18 23:12:18 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb 18 23:12:18 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Feb 18 23:12:18 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:70000000)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Feb 18 23:12:18 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
Feb 18 23:12:18 ubuntu kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007bc00000 s83136 r8192 d23360 u1048576
Feb 18 23:12:18 ubuntu kernel: [    0.000000] pcpu-alloc: s83136 r8192 d23360 u1048576 alloc=1*2097152
Feb 18 23:12:18 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 499566
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Policy zone: DMA32
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic root=UUID=5884B5E584B5C632 loop=/ubuntu/disks/root.disk ro recovery nomodeset
Feb 18 23:12:18 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Checking aperture...
Feb 18 23:12:18 ubuntu kernel: [    0.000000] No AGP bridge found
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Node 0: aperture @ 6ed6000000 size 32 MB
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Memory: 1967300k/2030464k available (6569k kernel code, 452k absent, 62712k reserved, 6634k data, 924k init)
Feb 18 23:12:18 ubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Feb 18 23:12:18 ubuntu kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Feb 18 23:12:18 ubuntu kernel: [    0.000000] NR_IRQS:16640 nr_irqs:512 16
Feb 18 23:12:18 ubuntu kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Feb 18 23:12:18 ubuntu kernel: [    0.000000] console [tty0] enabled
Feb 18 23:12:18 ubuntu kernel: [    0.000000] allocated 16777216 bytes of page_cgroup
Feb 18 23:12:18 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Detected 2612.166 MHz processor.
Feb 18 23:12:18 ubuntu kernel: [    0.000000] Marking TSC unstable due to TSCs unsynchronized
Feb 18 23:12:18 ubuntu kernel: [    0.008062] Calibrating delay loop (skipped), value calculated using timer frequency.. 5224.33 BogoMIPS (lpj=10448664)
Feb 18 23:12:18 ubuntu kernel: [    0.008178] pid_max: default: 32768 minimum: 301
Feb 18 23:12:18 ubuntu kernel: [    0.008259] Security Framework initialized
Feb 18 23:12:18 ubuntu kernel: [    0.008334] AppArmor: AppArmor initialized
Feb 18 23:12:18 ubuntu kernel: [    0.008390] Yama: becoming mindful.
Feb 18 23:12:18 ubuntu kernel: [    0.008664] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Feb 18 23:12:18 ubuntu kernel: [    0.009798] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Feb 18 23:12:18 ubuntu kernel: [    0.012576] Mount-cache hash table entries: 256
Feb 18 23:12:18 ubuntu kernel: [    0.012784] Initializing cgroup subsys cpuacct
Feb 18 23:12:18 ubuntu kernel: [    0.012846] Initializing cgroup subsys memory
Feb 18 23:12:18 ubuntu kernel: [    0.012911] Initializing cgroup subsys devices
Feb 18 23:12:18 ubuntu kernel: [    0.012968] Initializing cgroup subsys freezer
Feb 18 23:12:18 ubuntu kernel: [    0.013025] Initializing cgroup subsys blkio
Feb 18 23:12:18 ubuntu kernel: [    0.013088] Initializing cgroup subsys perf_event
Feb 18 23:12:18 ubuntu kernel: [    0.013175] tseg: 007bf00000
Feb 18 23:12:18 ubuntu kernel: [    0.013177] CPU: Physical Processor ID: 0
Feb 18 23:12:18 ubuntu kernel: [    0.013233] CPU: Processor Core ID: 0
Feb 18 23:12:18 ubuntu kernel: [    0.013290] mce: CPU supports 5 MCE banks
Feb 18 23:12:18 ubuntu kernel: [    0.013357] using AMD E400 aware idle routine
Feb 18 23:12:18 ubuntu kernel: [    0.014925] ACPI: Core revision 20110623
Feb 18 23:12:18 ubuntu kernel: [    0.020012] ftrace: allocating 27033 entries in 107 pages
Feb 18 23:12:18 ubuntu kernel: [    0.028528] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Feb 18 23:12:18 ubuntu kernel: [    0.068290] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02
Feb 18 23:12:18 ubuntu kernel: [    0.072003] Performance Events: AMD PMU driver.
Feb 18 23:12:18 ubuntu kernel: [    0.072003] ... version:                0
Feb 18 23:12:18 ubuntu kernel: [    0.072003] ... bit width:              48
Feb 18 23:12:18 ubuntu kernel: [    0.072003] ... generic registers:      4
Feb 18 23:12:18 ubuntu kernel: [    0.072003] ... value mask:             0000ffffffffffff
Feb 18 23:12:18 ubuntu kernel: [    0.072003] ... max period:             00007fffffffffff
Feb 18 23:12:18 ubuntu kernel: [    0.072003] ... fixed-purpose events:   0
Feb 18 23:12:18 ubuntu kernel: [    0.072003] ... event mask:             000000000000000f
Feb 18 23:12:18 ubuntu kernel: [    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
Feb 18 23:12:18 ubuntu kernel: [    0.072003] Booting Node   0, Processors  #1 Ok.
Feb 18 23:12:18 ubuntu kernel: [    0.072003] smpboot cpu 1: start_ip = 9a000
Feb 18 23:12:18 ubuntu kernel: [    0.156069] NMI watchdog enabled, takes one hw-pmu counter.
Feb 18 23:12:18 ubuntu kernel: [    0.156148] Brought up 2 CPUs
Feb 18 23:12:18 ubuntu kernel: [    0.156204] Total of 2 processors activated (10448.73 BogoMIPS).
Feb 18 23:12:18 ubuntu kernel: [    0.157095] devtmpfs: initialized
Feb 18 23:12:18 ubuntu kernel: [    0.157287] EVM: security.selinux
Feb 18 23:12:18 ubuntu kernel: [    0.157343] EVM: security.SMACK64
Feb 18 23:12:18 ubuntu kernel: [    0.157399] EVM: security.capability
Feb 18 23:12:18 ubuntu kernel: [    0.157516] PM: Registering ACPI NVS region at 7bee0000 (12288 bytes)
Feb 18 23:12:18 ubuntu kernel: [    0.157516] print_constraints: dummy: 
Feb 18 23:12:18 ubuntu kernel: [    0.157516] RTC time: 23:10:08, date: 02/18/13
Feb 18 23:12:18 ubuntu kernel: [    0.157516] NET: Registered protocol family 16
Feb 18 23:12:18 ubuntu kernel: [    0.160043] Trying to unpack rootfs image as initramfs...
Feb 18 23:12:18 ubuntu kernel: [    0.157516] node 0 link 0: io port [9000, ffff]
Feb 18 23:12:18 ubuntu kernel: [    0.157516] TOM: 0000000080000000 aka 2048M
Feb 18 23:12:18 ubuntu kernel: [    0.160018] node 0 link 0: mmio [a0000, bffff]
Feb 18 23:12:18 ubuntu kernel: [    0.160020] node 0 link 0: mmio [80000000, efffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.160022] node 0 link 0: mmio [f4000000, fe02ffff]
Feb 18 23:12:18 ubuntu kernel: [    0.160024] node 0 link 0: mmio [f0000000, f04fffff]
Feb 18 23:12:18 ubuntu kernel: [    0.160026] bus: [00, 04] on node 0 link 0
Feb 18 23:12:18 ubuntu kernel: [    0.160028] bus: 00 index 0 [io  0x0000-0xffff]
Feb 18 23:12:18 ubuntu kernel: [    0.160030] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Feb 18 23:12:18 ubuntu kernel: [    0.160032] bus: 00 index 2 [mem 0x80000000-0xf3ffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.160033] bus: 00 index 3 [mem 0xf4000000-0xfcffffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.160043] ACPI: bus type pci registered
Feb 18 23:12:18 ubuntu kernel: [    0.160115] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
Feb 18 23:12:18 ubuntu kernel: [    0.160117] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
Feb 18 23:12:18 ubuntu kernel: [    0.164254] PCI: Using configuration type 1 for base access
Feb 18 23:12:18 ubuntu kernel: [    0.172146] bio: create slab <bio-0> at 0
Feb 18 23:12:18 ubuntu kernel: [    0.172212] ACPI: Added _OSI(Module Device)
Feb 18 23:12:18 ubuntu kernel: [    0.172269] ACPI: Added _OSI(Processor Device)
Feb 18 23:12:18 ubuntu kernel: [    0.172326] ACPI: Added _OSI(3.0 _SCP Extensions)
Feb 18 23:12:18 ubuntu kernel: [    0.172383] ACPI: Added _OSI(Processor Aggregator Device)
Feb 18 23:12:18 ubuntu kernel: [    0.173462] ACPI: EC: Look up EC in DSDT
Feb 18 23:12:18 ubuntu kernel: [    0.177178] ACPI: Interpreter enabled
Feb 18 23:12:18 ubuntu kernel: [    0.177236] ACPI: (supports S0 S3 S4 S5)
Feb 18 23:12:18 ubuntu kernel: [    0.177487] ACPI: Using IOAPIC for interrupt routing
Feb 18 23:12:18 ubuntu kernel: [    0.183381] ACPI: No dock devices found.
Feb 18 23:12:18 ubuntu kernel: [    0.183438] HEST: Table not found.
Feb 18 23:12:18 ubuntu kernel: [    0.183496] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Feb 18 23:12:18 ubuntu kernel: [    0.184112] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-04])
Feb 18 23:12:18 ubuntu kernel: [    0.185207] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af] (ignored)
Feb 18 23:12:18 ubuntu kernel: [    0.185210] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7] (ignored)
Feb 18 23:12:18 ubuntu kernel: [    0.185212] pci_root PNP0A08:00: host bridge window [io  0x9000-0xffff] (ignored)
Feb 18 23:12:18 ubuntu kernel: [    0.185215] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03df] (ignored)
Feb 18 23:12:18 ubuntu kernel: [    0.185217] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Feb 18 23:12:18 ubuntu kernel: [    0.185219] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xefffffff] (ignored)
Feb 18 23:12:18 ubuntu kernel: [    0.185222] pci_root PNP0A08:00: host bridge window [mem 0xf4000000-0xfe02ffff] (ignored)
Feb 18 23:12:18 ubuntu kernel: [    0.185224] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff] (ignored)
Feb 18 23:12:18 ubuntu kernel: [    0.185227] pci_root PNP0A08:00: host bridge window [io  0x4700-0x470b] (ignored)
Feb 18 23:12:18 ubuntu kernel: [    0.185229] pci_root PNP0A08:00: host bridge window [io  0x1c00-0x1c80] (ignored)
Feb 18 23:12:18 ubuntu kernel: [    0.185231] pci_root PNP0A08:00: host bridge window [mem 0xfec80000-0xfecbffff] (ignored)
Feb 18 23:12:18 ubuntu kernel: [    0.185254] pci 0000:00:00.0: [10de:03ea] type 0 class 0x000500
Feb 18 23:12:18 ubuntu kernel: [    0.185425] pci 0000:00:01.0: [10de:03e0] type 0 class 0x000601
Feb 18 23:12:18 ubuntu kernel: [    0.185462] pci 0000:00:01.1: [10de:03eb] type 0 class 0x000c05
Feb 18 23:12:18 ubuntu kernel: [    0.185473] pci 0000:00:01.1: reg 10: [io  0xfc00-0xfc3f]
Feb 18 23:12:18 ubuntu kernel: [    0.185488] pci 0000:00:01.1: reg 20: [io  0x1c00-0x1c3f]
Feb 18 23:12:18 ubuntu kernel: [    0.185493] pci 0000:00:01.1: reg 24: [io  0xf400-0xf43f]
Feb 18 23:12:18 ubuntu kernel: [    0.185520] pci 0000:00:01.1: PME# supported from D3hot D3cold
Feb 18 23:12:18 ubuntu kernel: [    0.185526] pci 0000:00:01.1: PME# disabled
Feb 18 23:12:18 ubuntu kernel: [    0.185539] pci 0000:00:01.2: [10de:03f5] type 0 class 0x000500
Feb 18 23:12:18 ubuntu kernel: [    0.185580] pci 0000:00:02.0: [10de:03f1] type 0 class 0x000c03
Feb 18 23:12:18 ubuntu kernel: [    0.185588] pci 0000:00:02.0: reg 10: [mem 0xfe02f000-0xfe02ffff]
Feb 18 23:12:18 ubuntu kernel: [    0.185620] pci 0000:00:02.0: supports D1 D2
Feb 18 23:12:18 ubuntu kernel: [    0.185622] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:12:18 ubuntu kernel: [    0.185625] pci 0000:00:02.0: PME# disabled
Feb 18 23:12:18 ubuntu kernel: [    0.185637] pci 0000:00:02.1: [10de:03f2] type 0 class 0x000c03
Feb 18 23:12:18 ubuntu kernel: [    0.185646] pci 0000:00:02.1: reg 10: [mem 0xfe02e000-0xfe02e0ff]
Feb 18 23:12:18 ubuntu kernel: [    0.185685] pci 0000:00:02.1: supports D1 D2
Feb 18 23:12:18 ubuntu kernel: [    0.185686] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:12:18 ubuntu kernel: [    0.185690] pci 0000:00:02.1: PME# disabled
Feb 18 23:12:18 ubuntu kernel: [    0.185707] pci 0000:00:04.0: [10de:03f3] type 1 class 0x000604
Feb 18 23:12:18 ubuntu kernel: [    0.185746] pci 0000:00:05.0: [10de:03f0] type 0 class 0x000403
Feb 18 23:12:18 ubuntu kernel: [    0.185756] pci 0000:00:05.0: reg 10: [mem 0xfe028000-0xfe02bfff]
Feb 18 23:12:18 ubuntu kernel: [    0.185794] pci 0000:00:05.0: PME# supported from D3hot D3cold
Feb 18 23:12:18 ubuntu kernel: [    0.185797] pci 0000:00:05.0: PME# disabled
Feb 18 23:12:18 ubuntu kernel: [    0.185816] pci 0000:00:06.0: [10de:03ec] type 0 class 0x000101
Feb 18 23:12:18 ubuntu kernel: [    0.185836] pci 0000:00:06.0: reg 20: [io  0xf000-0xf00f]
Feb 18 23:12:18 ubuntu kernel: [    0.185865] pci 0000:00:08.0: [10de:03f6] type 0 class 0x000101
Feb 18 23:12:18 ubuntu kernel: [    0.185873] pci 0000:00:08.0: reg 10: [io  0x09f0-0x09f7]
Feb 18 23:12:18 ubuntu kernel: [    0.185877] pci 0000:00:08.0: reg 14: [io  0x0bf0-0x0bf3]
Feb 18 23:12:18 ubuntu kernel: [    0.185881] pci 0000:00:08.0: reg 18: [io  0x0970-0x0977]
Feb 18 23:12:18 ubuntu kernel: [    0.185886] pci 0000:00:08.0: reg 1c: [io  0x0b70-0x0b73]
Feb 18 23:12:18 ubuntu kernel: [    0.185890] pci 0000:00:08.0: reg 20: [io  0xdc00-0xdc0f]
Feb 18 23:12:18 ubuntu kernel: [    0.185894] pci 0000:00:08.0: reg 24: [mem 0xfe02d000-0xfe02dfff]
Feb 18 23:12:18 ubuntu kernel: [    0.185927] pci 0000:00:09.0: [10de:03e8] type 1 class 0x000604
Feb 18 23:12:18 ubuntu kernel: [    0.185950] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:12:18 ubuntu kernel: [    0.185953] pci 0000:00:09.0: PME# disabled
Feb 18 23:12:18 ubuntu kernel: [    0.185967] pci 0000:00:0b.0: [10de:03e9] type 1 class 0x000604
Feb 18 23:12:18 ubuntu kernel: [    0.185989] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:12:18 ubuntu kernel: [    0.185992] pci 0000:00:0b.0: PME# disabled
Feb 18 23:12:18 ubuntu kernel: [    0.186003] pci 0000:00:0c.0: [10de:03e9] type 1 class 0x000604
Feb 18 23:12:18 ubuntu kernel: [    0.186026] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:12:18 ubuntu kernel: [    0.186029] pci 0000:00:0c.0: PME# disabled
Feb 18 23:12:18 ubuntu kernel: [    0.186040] pci 0000:00:0d.0: [10de:03d1] type 0 class 0x000300
Feb 18 23:12:18 ubuntu kernel: [    0.186046] pci 0000:00:0d.0: reg 10: [mem 0xfc000000-0xfcffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.186052] pci 0000:00:0d.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
Feb 18 23:12:18 ubuntu kernel: [    0.186057] pci 0000:00:0d.0: reg 1c: [mem 0xfb000000-0xfbffffff 64bit]
Feb 18 23:12:18 ubuntu kernel: [    0.186063] pci 0000:00:0d.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Feb 18 23:12:18 ubuntu kernel: [    0.186089] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
Feb 18 23:12:18 ubuntu kernel: [    0.186107] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
Feb 18 23:12:18 ubuntu kernel: [    0.186121] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
Feb 18 23:12:18 ubuntu kernel: [    0.186136] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
Feb 18 23:12:18 ubuntu kernel: [    0.186158] PCI: peer root bus 00 res updated from pci conf
Feb 18 23:12:18 ubuntu kernel: [    0.186189] pci 0000:01:05.0: [1131:7130] type 0 class 0x000480
Feb 18 23:12:18 ubuntu kernel: [    0.186201] pci 0000:01:05.0: reg 10: [mem 0xfdaff000-0xfdaff3ff]
Feb 18 23:12:18 ubuntu kernel: [    0.186251] pci 0000:01:05.0: supports D1 D2
Feb 18 23:12:18 ubuntu kernel: [    0.186268] pci 0000:01:06.0: [10ec:8139] type 0 class 0x000200
Feb 18 23:12:18 ubuntu kernel: [    0.186280] pci 0000:01:06.0: reg 10: [io  0xcc00-0xccff]
Feb 18 23:12:18 ubuntu kernel: [    0.186287] pci 0000:01:06.0: reg 14: [mem 0xfdafe000-0xfdafe0ff]
Feb 18 23:12:18 ubuntu kernel: [    0.186316] pci 0000:01:06.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Feb 18 23:12:18 ubuntu kernel: [    0.186335] pci 0000:01:06.0: supports D1 D2
Feb 18 23:12:18 ubuntu kernel: [    0.186337] pci 0000:01:06.0: PME# supported from D1 D2 D3hot D3cold
Feb 18 23:12:18 ubuntu kernel: [    0.186340] pci 0000:01:06.0: PME# disabled
Feb 18 23:12:18 ubuntu kernel: [    0.186354] pci 0000:01:08.0: [10ec:8167] type 0 class 0x000200
Feb 18 23:12:18 ubuntu kernel: [    0.186366] pci 0000:01:08.0: reg 10: [io  0xc800-0xc8ff]
Feb 18 23:12:18 ubuntu kernel: [    0.186373] pci 0000:01:08.0: reg 14: [mem 0xfdafd000-0xfdafd0ff]
Feb 18 23:12:18 ubuntu kernel: [    0.186401] pci 0000:01:08.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Feb 18 23:12:18 ubuntu kernel: [    0.186419] pci 0000:01:08.0: supports D1 D2
Feb 18 23:12:18 ubuntu kernel: [    0.186421] pci 0000:01:08.0: PME# supported from D1 D2 D3hot D3cold
Feb 18 23:12:18 ubuntu kernel: [    0.186424] pci 0000:01:08.0: PME# disabled
Feb 18 23:12:18 ubuntu kernel: [    0.186449] pci 0000:00:04.0: PCI bridge to [bus 01-01] (subtractive decode)
Feb 18 23:12:18 ubuntu kernel: [    0.186510] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
Feb 18 23:12:18 ubuntu kernel: [    0.186513] pci 0000:00:04.0:   bridge window [mem 0xfda00000-0xfdafffff]
Feb 18 23:12:18 ubuntu kernel: [    0.186516] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
Feb 18 23:12:18 ubuntu kernel: [    0.186519] pci 0000:00:04.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Feb 18 23:12:18 ubuntu kernel: [    0.186521] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Feb 18 23:12:18 ubuntu kernel: [    0.186524] pci 0000:00:04.0:   bridge window [mem 0x80000000-0xf3ffffff] (subtractive decode)
Feb 18 23:12:18 ubuntu kernel: [    0.186526] pci 0000:00:04.0:   bridge window [mem 0xf4000000-0xfcffffffff] (subtractive decode)
Feb 18 23:12:18 ubuntu kernel: [    0.186552] pci 0000:02:00.0: [10de:0393] type 0 class 0x000300
Feb 18 23:12:18 ubuntu kernel: [    0.186559] pci 0000:02:00.0: reg 10: [mem 0xf8000000-0xf8ffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.186567] pci 0000:02:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
Feb 18 23:12:18 ubuntu kernel: [    0.186575] pci 0000:02:00.0: reg 1c: [mem 0xf9000000-0xf9ffffff 64bit]
Feb 18 23:12:18 ubuntu kernel: [    0.186581] pci 0000:02:00.0: reg 24: [io  0xbc00-0xbc7f]
Feb 18 23:12:18 ubuntu kernel: [    0.186586] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Feb 18 23:12:18 ubuntu kernel: [    0.186614] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Feb 18 23:12:18 ubuntu kernel: [    0.186687] pci 0000:00:09.0: PCI bridge to [bus 02-02]
Feb 18 23:12:18 ubuntu kernel: [    0.186746] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
Feb 18 23:12:18 ubuntu kernel: [    0.186748] pci 0000:00:09.0:   bridge window [mem 0xf8000000-0xfaffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.186752] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Feb 18 23:12:18 ubuntu kernel: [    0.186768] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
Feb 18 23:12:18 ubuntu kernel: [    0.186827] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
Feb 18 23:12:18 ubuntu kernel: [    0.186830] pci 0000:00:0b.0:   bridge window [mem 0xfde00000-0xfdefffff]
Feb 18 23:12:18 ubuntu kernel: [    0.186833] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
Feb 18 23:12:18 ubuntu kernel: [    0.186849] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
Feb 18 23:12:18 ubuntu kernel: [    0.186908] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
Feb 18 23:12:18 ubuntu kernel: [    0.186911] pci 0000:00:0c.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
Feb 18 23:12:18 ubuntu kernel: [    0.186914] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Feb 18 23:12:18 ubuntu kernel: [    0.186924] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb 18 23:12:18 ubuntu kernel: [    0.187028] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Feb 18 23:12:18 ubuntu kernel: [    0.187153]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Feb 18 23:12:18 ubuntu kernel: [    0.187213]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Feb 18 23:12:18 ubuntu kernel: [    0.187280] ACPI _OSC control for PCIe not granted, disabling ASPM
Feb 18 23:12:18 ubuntu kernel: [    0.219080] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
Feb 18 23:12:18 ubuntu kernel: [    0.219583] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
Feb 18 23:12:18 ubuntu kernel: [    0.220058] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
Feb 18 23:12:18 ubuntu kernel: [    0.220558] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.221155] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.221751] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.222348] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.222946] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 *10 11 14 15)
Feb 18 23:12:18 ubuntu kernel: [    0.223446] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 *11 14 15)
Feb 18 23:12:18 ubuntu kernel: [    0.224055] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.224654] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
Feb 18 23:12:18 ubuntu kernel: [    0.225153] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.225752] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
Feb 18 23:12:18 ubuntu kernel: [    0.226259] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.226857] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
Feb 18 23:12:18 ubuntu kernel: [    0.228055] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
Feb 18 23:12:18 ubuntu kernel: [    0.228565] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.229164] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Feb 18 23:12:18 ubuntu kernel: [    0.229668] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.230297] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
Feb 18 23:12:18 ubuntu kernel: [    0.230600] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
Feb 18 23:12:18 ubuntu kernel: [    0.230904] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Feb 18 23:12:18 ubuntu kernel: [    0.231207] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.231558] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.231908] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.232272] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.232622] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
Feb 18 23:12:18 ubuntu kernel: [    0.232926] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
Feb 18 23:12:18 ubuntu kernel: [    0.233365] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Feb 18 23:12:18 ubuntu kernel: [    0.233804] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.234289] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.234774] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Feb 18 23:12:18 ubuntu kernel: [    0.235213] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Feb 18 23:12:18 ubuntu kernel: [    0.235652] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Feb 18 23:12:18 ubuntu kernel: [    0.236082] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.236567] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.237052] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Feb 18 23:12:18 ubuntu kernel: [    0.237494] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:12:18 ubuntu kernel: [    0.238041] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=none,locks=none
Feb 18 23:12:18 ubuntu kernel: [    0.238114] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
Feb 18 23:12:18 ubuntu kernel: [    0.238181] vgaarb: loaded
Feb 18 23:12:18 ubuntu kernel: [    0.238236] vgaarb: bridge control possible 0000:02:00.0
Feb 18 23:12:18 ubuntu kernel: [    0.238293] vgaarb: no bridge control possible 0000:00:0d.0
Feb 18 23:12:18 ubuntu kernel: [    0.238472] i2c-core: driver [aat2870] using legacy suspend method
Feb 18 23:12:18 ubuntu kernel: [    0.238530] i2c-core: driver [aat2870] using legacy resume method
Feb 18 23:12:18 ubuntu kernel: [    0.238661] SCSI subsystem initialized
Feb 18 23:12:18 ubuntu kernel: [    0.238791] libata version 3.00 loaded.
Feb 18 23:12:18 ubuntu kernel: [    0.238851] usbcore: registered new interface driver usbfs
Feb 18 23:12:18 ubuntu kernel: [    0.238919] usbcore: registered new interface driver hub
Feb 18 23:12:18 ubuntu kernel: [    0.239010] usbcore: registered new device driver usb
Feb 18 23:12:18 ubuntu kernel: [    0.239164] PCI: Using ACPI for IRQ routing
Feb 18 23:12:18 ubuntu kernel: [    0.240662] PCI: pci_cache_line_size set to 64 bytes
Feb 18 23:12:18 ubuntu kernel: [    0.240724] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
Feb 18 23:12:18 ubuntu kernel: [    0.240727] reserve RAM buffer: 000000007bee0000 - 000000007bffffff 
Feb 18 23:12:18 ubuntu kernel: [    0.240837] NetLabel: Initializing
Feb 18 23:12:18 ubuntu kernel: [    0.240893] NetLabel:  domain hash size = 128
Feb 18 23:12:18 ubuntu kernel: [    0.240950] NetLabel:  protocols = UNLABELED CIPSOv4
Feb 18 23:12:18 ubuntu kernel: [    0.241018] NetLabel:  unlabeled traffic allowed by default
Feb 18 23:12:18 ubuntu kernel: [    0.249724] AppArmor: AppArmor Filesystem Enabled
Feb 18 23:12:18 ubuntu kernel: [    0.249832] pnp: PnP ACPI init
Feb 18 23:12:18 ubuntu kernel: [    0.249907] ACPI: bus type pnp registered
Feb 18 23:12:18 ubuntu kernel: [    0.250593] pnp 00:00: [bus 00-04]
Feb 18 23:12:18 ubuntu kernel: [    0.250600] pnp 00:00: [io  0x0cf8-0x0cff]
Feb 18 23:12:18 ubuntu kernel: [    0.250602] pnp 00:00: [io  0x0000-0x03af window]
Feb 18 23:12:18 ubuntu kernel: [    0.250604] pnp 00:00: [io  0x03e0-0x0cf7 window]
Feb 18 23:12:18 ubuntu kernel: [    0.250606] pnp 00:00: [io  0x9000-0xffff window]
Feb 18 23:12:18 ubuntu kernel: [    0.250608] pnp 00:00: [io  0x03b0-0x03df window]
Feb 18 23:12:18 ubuntu kernel: [    0.250610] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Feb 18 23:12:18 ubuntu kernel: [    0.250613] pnp 00:00: [mem 0x80000000-0xefffffff window]
Feb 18 23:12:18 ubuntu kernel: [    0.250615] pnp 00:00: [mem 0xf4000000-0xfe02ffff window]
Feb 18 23:12:18 ubuntu kernel: [    0.250617] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Feb 18 23:12:18 ubuntu kernel: [    0.250619] pnp 00:00: [io  0x4700-0x470b window]
Feb 18 23:12:18 ubuntu kernel: [    0.250621] pnp 00:00: [io  0x1c00-0x1c80 window]
Feb 18 23:12:18 ubuntu kernel: [    0.250624] pnp 00:00: [mem 0xfec80000-0xfecbffff window]
Feb 18 23:12:18 ubuntu kernel: [    0.250718] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Feb 18 23:12:18 ubuntu kernel: [    0.250830] pnp 00:01: [io  0x1000-0x107f]
Feb 18 23:12:18 ubuntu kernel: [    0.250832] pnp 00:01: [io  0x1080-0x10ff]
Feb 18 23:12:18 ubuntu kernel: [    0.250834] pnp 00:01: [io  0x1400-0x147f]
Feb 18 23:12:18 ubuntu kernel: [    0.250835] pnp 00:01: [io  0x1480-0x14ff]
Feb 18 23:12:18 ubuntu kernel: [    0.250837] pnp 00:01: [io  0x1800-0x187f]
Feb 18 23:12:18 ubuntu kernel: [    0.250839] pnp 00:01: [io  0x1880-0x18ff]
Feb 18 23:12:18 ubuntu kernel: [    0.250842] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Feb 18 23:12:18 ubuntu kernel: [    0.250844] pnp 00:01: [mem 0xfefe0000-0xfefe01ff]
Feb 18 23:12:18 ubuntu kernel: [    0.250846] pnp 00:01: [mem 0xfefe1000-0xfefe10ff]
Feb 18 23:12:18 ubuntu kernel: [    0.250848] pnp 00:01: [mem 0x7c000000-0x7fffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.250917] system 00:01: [io  0x1000-0x107f] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.250976] system 00:01: [io  0x1080-0x10ff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.251035] system 00:01: [io  0x1400-0x147f] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.251093] system 00:01: [io  0x1480-0x14ff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.251152] system 00:01: [io  0x1800-0x187f] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.251211] system 00:01: [io  0x1880-0x18ff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.251270] system 00:01: [mem 0xfefe0000-0xfefe01ff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.251330] system 00:01: [mem 0xfefe1000-0xfefe10ff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.251389] system 00:01: [mem 0x7c000000-0x7fffffff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.251449] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 18 23:12:18 ubuntu kernel: [    0.252071] pnp 00:02: [io  0x0010-0x001f]
Feb 18 23:12:18 ubuntu kernel: [    0.252073] pnp 00:02: [io  0x0022-0x003f]
Feb 18 23:12:18 ubuntu kernel: [    0.252075] pnp 00:02: [io  0x0044-0x004d]
Feb 18 23:12:18 ubuntu kernel: [    0.252076] pnp 00:02: [io  0x0050-0x005e]
Feb 18 23:12:18 ubuntu kernel: [    0.252078] pnp 00:02: [io  0x0062-0x0063]
Feb 18 23:12:18 ubuntu kernel: [    0.252080] pnp 00:02: [io  0x0065-0x006f]
Feb 18 23:12:18 ubuntu kernel: [    0.252082] pnp 00:02: [io  0x0074-0x007f]
Feb 18 23:12:18 ubuntu kernel: [    0.252083] pnp 00:02: [io  0x0091-0x0093]
Feb 18 23:12:18 ubuntu kernel: [    0.252085] pnp 00:02: [io  0x00a2-0x00bf]
Feb 18 23:12:18 ubuntu kernel: [    0.252087] pnp 00:02: [io  0x00e0-0x00ef]
Feb 18 23:12:18 ubuntu kernel: [    0.252089] pnp 00:02: [io  0x04d0-0x04d1]
Feb 18 23:12:18 ubuntu kernel: [    0.252091] pnp 00:02: [io  0x0800-0x087f]
Feb 18 23:12:18 ubuntu kernel: [    0.252093] pnp 00:02: [io  0x0290-0x0297]
Feb 18 23:12:18 ubuntu kernel: [    0.252163] system 00:02: [io  0x04d0-0x04d1] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.252222] system 00:02: [io  0x0800-0x087f] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.252281] system 00:02: [io  0x0290-0x0297] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.252340] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 18 23:12:18 ubuntu kernel: [    0.252351] pnp 00:03: [dma 4]
Feb 18 23:12:18 ubuntu kernel: [    0.252353] pnp 00:03: [io  0x0000-0x000f]
Feb 18 23:12:18 ubuntu kernel: [    0.252355] pnp 00:03: [io  0x0080-0x0090]
Feb 18 23:12:18 ubuntu kernel: [    0.252357] pnp 00:03: [io  0x0094-0x009f]
Feb 18 23:12:18 ubuntu kernel: [    0.252358] pnp 00:03: [io  0x00c0-0x00df]
Feb 18 23:12:18 ubuntu kernel: [    0.252402] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Feb 18 23:12:18 ubuntu kernel: [    0.252448] pnp 00:04: [io  0x0070-0x0073]
Feb 18 23:12:18 ubuntu kernel: [    0.252467] pnp 00:04: [irq 8]
Feb 18 23:12:18 ubuntu kernel: [    0.252512] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Feb 18 23:12:18 ubuntu kernel: [    0.252522] pnp 00:05: [io  0x0061]
Feb 18 23:12:18 ubuntu kernel: [    0.252564] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Feb 18 23:12:18 ubuntu kernel: [    0.252573] pnp 00:06: [io  0x00f0-0x00ff]
Feb 18 23:12:18 ubuntu kernel: [    0.252581] pnp 00:06: [irq 13]
Feb 18 23:12:18 ubuntu kernel: [    0.252631] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Feb 18 23:12:18 ubuntu kernel: [    0.252795] pnp 00:07: [io  0x03f0-0x03f5]
Feb 18 23:12:18 ubuntu kernel: [    0.252797] pnp 00:07: [io  0x03f7]
Feb 18 23:12:18 ubuntu kernel: [    0.252805] pnp 00:07: [irq 6]
Feb 18 23:12:18 ubuntu kernel: [    0.252807] pnp 00:07: [dma 2]
Feb 18 23:12:18 ubuntu kernel: [    0.252863] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
Feb 18 23:12:18 ubuntu kernel: [    0.253086] pnp 00:08: [io  0x03f8-0x03ff]
Feb 18 23:12:18 ubuntu kernel: [    0.253095] pnp 00:08: [irq 4]
Feb 18 23:12:18 ubuntu kernel: [    0.253164] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Feb 18 23:12:18 ubuntu kernel: [    0.253726] pnp 00:09: [io  0x0378-0x037f]
Feb 18 23:12:18 ubuntu kernel: [    0.253728] pnp 00:09: [io  0x0778-0x077b]
Feb 18 23:12:18 ubuntu kernel: [    0.253736] pnp 00:09: [irq 7]
Feb 18 23:12:18 ubuntu kernel: [    0.253738] pnp 00:09: [dma 3]
Feb 18 23:12:18 ubuntu kernel: [    0.253800] pnp 00:09: Plug and Play ACPI device, IDs PNP0401 (active)
Feb 18 23:12:18 ubuntu kernel: [    0.253859] pnp 00:0a: [mem 0xf0000000-0xf3ffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.253919] system 00:0a: [mem 0xf0000000-0xf3ffffff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.253980] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 18 23:12:18 ubuntu kernel: [    0.254057] pnp 00:0b: [mem 0x000f0000-0x000fffff]
Feb 18 23:12:18 ubuntu kernel: [    0.254059] pnp 00:0b: [mem 0xfeff0000-0xfeff00ff]
Feb 18 23:12:18 ubuntu kernel: [    0.254061] pnp 00:0b: [mem 0x7bee0000-0x7befffff]
Feb 18 23:12:18 ubuntu kernel: [    0.254063] pnp 00:0b: [mem 0xffff0000-0xffffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.254068] pnp 00:0b: [mem 0x00000000-0x0009ffff]
Feb 18 23:12:18 ubuntu kernel: [    0.254070] pnp 00:0b: [mem 0x00100000-0x7bedffff]
Feb 18 23:12:18 ubuntu kernel: [    0.254072] pnp 00:0b: [mem 0x7bf00000-0x7fefffff]
Feb 18 23:12:18 ubuntu kernel: [    0.254074] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
Feb 18 23:12:18 ubuntu kernel: [    0.254076] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
Feb 18 23:12:18 ubuntu kernel: [    0.254078] pnp 00:0b: [mem 0xfefff000-0xfeffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.254080] pnp 00:0b: [mem 0xfff80000-0xfff80fff]
Feb 18 23:12:18 ubuntu kernel: [    0.254082] pnp 00:0b: [mem 0xfff90000-0xfffbffff]
Feb 18 23:12:18 ubuntu kernel: [    0.254084] pnp 00:0b: [mem 0xfffed000-0xfffeffff]
Feb 18 23:12:18 ubuntu kernel: [    0.254162] system 00:0b: [mem 0x000f0000-0x000fffff] could not be reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254223] system 00:0b: [mem 0xfeff0000-0xfeff00ff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254282] system 00:0b: [mem 0x7bee0000-0x7befffff] could not be reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254342] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254401] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254461] system 00:0b: [mem 0x00100000-0x7bedffff] could not be reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254521] system 00:0b: [mem 0x7bf00000-0x7fefffff] could not be reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254581] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254641] system 00:0b: [mem 0xfee00000-0xfeefffff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254700] system 00:0b: [mem 0xfefff000-0xfeffffff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254759] system 00:0b: [mem 0xfff80000-0xfff80fff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254819] system 00:0b: [mem 0xfff90000-0xfffbffff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254878] system 00:0b: [mem 0xfffed000-0xfffeffff] has been reserved
Feb 18 23:12:18 ubuntu kernel: [    0.254938] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
Feb 18 23:12:18 ubuntu kernel: [    0.254947] pnp: PnP ACPI: found 12 devices
Feb 18 23:12:18 ubuntu kernel: [    0.255004] ACPI: ACPI bus type pnp unregistered
Feb 18 23:12:18 ubuntu kernel: [    0.261345] Switching to clocksource acpi_pm
Feb 18 23:12:18 ubuntu kernel: [    0.261581] PCI: max bus depth: 1 pci_try_num: 2
Feb 18 23:12:18 ubuntu kernel: [    0.261601] pci 0000:00:0d.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
Feb 18 23:12:18 ubuntu kernel: [    0.261670] pci 0000:01:06.0: BAR 6: assigned [mem 0xfdf00000-0xfdf1ffff pref]
Feb 18 23:12:18 ubuntu kernel: [    0.261737] pci 0000:01:08.0: BAR 6: assigned [mem 0xfdf20000-0xfdf3ffff pref]
Feb 18 23:12:18 ubuntu kernel: [    0.261804] pci 0000:00:04.0: PCI bridge to [bus 01-01]
Feb 18 23:12:18 ubuntu kernel: [    0.261862] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
Feb 18 23:12:18 ubuntu kernel: [    0.261922] pci 0000:00:04.0:   bridge window [mem 0xfda00000-0xfdafffff]
Feb 18 23:12:18 ubuntu kernel: [    0.261982] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
Feb 18 23:12:18 ubuntu kernel: [    0.262051] pci 0000:02:00.0: BAR 6: assigned [mem 0xfa000000-0xfa01ffff pref]
Feb 18 23:12:18 ubuntu kernel: [    0.262118] pci 0000:00:09.0: PCI bridge to [bus 02-02]
Feb 18 23:12:18 ubuntu kernel: [    0.262176] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
Feb 18 23:12:18 ubuntu kernel: [    0.262235] pci 0000:00:09.0:   bridge window [mem 0xf8000000-0xfaffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262295] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Feb 18 23:12:18 ubuntu kernel: [    0.262363] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
Feb 18 23:12:18 ubuntu kernel: [    0.262421] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
Feb 18 23:12:18 ubuntu kernel: [    0.262480] pci 0000:00:0b.0:   bridge window [mem 0xfde00000-0xfdefffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262540] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
Feb 18 23:12:18 ubuntu kernel: [    0.262608] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
Feb 18 23:12:18 ubuntu kernel: [    0.262666] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
Feb 18 23:12:18 ubuntu kernel: [    0.262725] pci 0000:00:0c.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262785] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Feb 18 23:12:18 ubuntu kernel: [    0.262858] pci 0000:00:04.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.262862] pci 0000:00:09.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.262866] pci 0000:00:0b.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.262870] pci 0000:00:0c.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.262873] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262875] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262877] pci_bus 0000:00: resource 6 [mem 0x80000000-0xf3ffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262880] pci_bus 0000:00: resource 7 [mem 0xf4000000-0xfcffffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262882] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Feb 18 23:12:18 ubuntu kernel: [    0.262885] pci_bus 0000:01: resource 1 [mem 0xfda00000-0xfdafffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262887] pci_bus 0000:01: resource 2 [mem 0xfdf00000-0xfdffffff pref]
Feb 18 23:12:18 ubuntu kernel: [    0.262889] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262892] pci_bus 0000:01: resource 5 [mem 0x000a0000-0x000bffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262894] pci_bus 0000:01: resource 6 [mem 0x80000000-0xf3ffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262896] pci_bus 0000:01: resource 7 [mem 0xf4000000-0xfcffffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262899] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
Feb 18 23:12:18 ubuntu kernel: [    0.262901] pci_bus 0000:02: resource 1 [mem 0xf8000000-0xfaffffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262904] pci_bus 0000:02: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
Feb 18 23:12:18 ubuntu kernel: [    0.262906] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
Feb 18 23:12:18 ubuntu kernel: [    0.262909] pci_bus 0000:03: resource 1 [mem 0xfde00000-0xfdefffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262911] pci_bus 0000:03: resource 2 [mem 0xfdd00000-0xfddfffff 64bit pref]
Feb 18 23:12:18 ubuntu kernel: [    0.262914] pci_bus 0000:04: resource 0 [io  0x9000-0x9fff]
Feb 18 23:12:18 ubuntu kernel: [    0.262916] pci_bus 0000:04: resource 1 [mem 0xfdc00000-0xfdcfffff]
Feb 18 23:12:18 ubuntu kernel: [    0.262918] pci_bus 0000:04: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
Feb 18 23:12:18 ubuntu kernel: [    0.262962] NET: Registered protocol family 2
Feb 18 23:12:18 ubuntu kernel: [    0.263134] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Feb 18 23:12:18 ubuntu kernel: [    0.264010] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Feb 18 23:12:18 ubuntu kernel: [    0.264705] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Feb 18 23:12:18 ubuntu kernel: [    0.265364] TCP: Hash tables configured (established 262144 bind 65536)
Feb 18 23:12:18 ubuntu kernel: [    0.265424] TCP reno registered
Feb 18 23:12:18 ubuntu kernel: [    0.265490] UDP hash table entries: 1024 (order: 3, 32768 bytes)
Feb 18 23:12:18 ubuntu kernel: [    0.265570] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
Feb 18 23:12:18 ubuntu kernel: [    0.265747] NET: Registered protocol family 1
Feb 18 23:12:18 ubuntu kernel: [    0.266063] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
Feb 18 23:12:18 ubuntu kernel: [    0.266139] pci 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
Feb 18 23:12:18 ubuntu kernel: [    0.336035] pci 0000:00:02.0: PCI INT A disabled
Feb 18 23:12:18 ubuntu kernel: [    0.336233] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
Feb 18 23:12:18 ubuntu kernel: [    0.336300] pci 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
Feb 18 23:12:18 ubuntu kernel: [    0.336376] pci 0000:00:02.1: PCI INT B disabled
Feb 18 23:12:18 ubuntu kernel: [    0.336473] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:12:18 ubuntu kernel: [    0.336575] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:12:18 ubuntu kernel: [    0.336684] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:12:18 ubuntu kernel: [    0.336792] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:12:18 ubuntu kernel: [    0.336903] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:12:18 ubuntu kernel: [    0.337017] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:12:18 ubuntu kernel: [    0.337100] pci 0000:02:00.0: Boot video device
Feb 18 23:12:18 ubuntu kernel: [    0.337102] PCI: CLS 64 bytes, default 64
Feb 18 23:12:18 ubuntu kernel: [    0.340029] audit: initializing netlink socket (disabled)
Feb 18 23:12:18 ubuntu kernel: [    0.340096] type=2000 audit(1361229008.336:1): initialized
Feb 18 23:12:18 ubuntu kernel: [    0.364360] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb 18 23:12:18 ubuntu kernel: [    0.366641] VFS: Disk quotas dquot_6.5.2
Feb 18 23:12:18 ubuntu kernel: [    0.366752] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb 18 23:12:18 ubuntu kernel: [    0.367358] fuse init (API version 7.17)
Feb 18 23:12:18 ubuntu kernel: [    0.367502] msgmni has been set to 3842
Feb 18 23:12:18 ubuntu kernel: [    0.367889] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Feb 18 23:12:18 ubuntu kernel: [    0.367981] io scheduler noop registered
Feb 18 23:12:18 ubuntu kernel: [    0.368065] io scheduler deadline registered
Feb 18 23:12:18 ubuntu kernel: [    0.368156] io scheduler cfq registered (default)
Feb 18 23:12:18 ubuntu kernel: [    0.368395] pcieport 0000:00:09.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.368485] pcieport 0000:00:0b.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.368536] pcieport 0000:00:0c.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.368612] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 18 23:12:18 ubuntu kernel: [    0.368695] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb 18 23:12:18 ubuntu kernel: [    0.368898] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Feb 18 23:12:18 ubuntu kernel: [    0.368970] ACPI: Power Button [PWRB]
Feb 18 23:12:18 ubuntu kernel: [    0.369081] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Feb 18 23:12:18 ubuntu kernel: [    0.369149] ACPI: Power Button [PWRF]
Feb 18 23:12:18 ubuntu kernel: [    0.369259] ACPI: Fan [FAN] (on)
Feb 18 23:12:18 ubuntu kernel: [    0.371726] thermal LNXTHERM:00: registered as thermal_zone0
Feb 18 23:12:18 ubuntu kernel: [    0.371784] ACPI: Thermal Zone [THRM] (40 C)
Feb 18 23:12:18 ubuntu kernel: [    0.371878] ERST: Table is not found!
Feb 18 23:12:18 ubuntu kernel: [    0.371934] GHES: HEST is not enabled!
Feb 18 23:12:18 ubuntu kernel: [    0.372086] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Feb 18 23:12:18 ubuntu kernel: [    0.392493] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 18 23:12:18 ubuntu kernel: [    0.434686] Freeing initrd memory: 13888k freed
Feb 18 23:12:18 ubuntu kernel: [    0.536577] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 18 23:12:18 ubuntu kernel: [    0.536919] Linux agpgart interface v0.103
Feb 18 23:12:18 ubuntu kernel: [    0.538701] brd: module loaded
Feb 18 23:12:18 ubuntu kernel: [    0.539684] loop: module loaded
Feb 18 23:12:18 ubuntu kernel: [    0.540038] pata_acpi 0000:00:06.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.540285] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
Feb 18 23:12:18 ubuntu kernel: [    0.540365] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
Feb 18 23:12:18 ubuntu kernel: [    0.540445] pata_acpi 0000:00:08.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.540451] pata_acpi 0000:00:08.0: PCI INT A disabled
Feb 18 23:12:18 ubuntu kernel: [    0.540918] Fixed MDIO Bus: probed
Feb 18 23:12:18 ubuntu kernel: [    0.540996] tun: Universal TUN/TAP device driver, 1.6
Feb 18 23:12:18 ubuntu kernel: [    0.541054] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Feb 18 23:12:18 ubuntu kernel: [    0.541171] PPP generic driver version 2.4.2
Feb 18 23:12:18 ubuntu kernel: [    0.541350] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb 18 23:12:18 ubuntu kernel: [    0.541433] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
Feb 18 23:12:18 ubuntu kernel: [    0.541517] ehci_hcd 0000:00:02.1: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.541520] ehci_hcd 0000:00:02.1: EHCI Host Controller
Feb 18 23:12:18 ubuntu kernel: [    0.542444] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Feb 18 23:12:18 ubuntu kernel: [    0.542532] ehci_hcd 0000:00:02.1: debug port 1
Feb 18 23:12:18 ubuntu kernel: [    0.542594] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Feb 18 23:12:18 ubuntu kernel: [    0.542618] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
Feb 18 23:12:18 ubuntu kernel: [    0.552025] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Feb 18 23:12:18 ubuntu kernel: [    0.552250] hub 1-0:1.0: USB hub found
Feb 18 23:12:18 ubuntu kernel: [    0.552309] hub 1-0:1.0: 8 ports detected
Feb 18 23:12:18 ubuntu kernel: [    0.552466] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb 18 23:12:18 ubuntu kernel: [    0.552552] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
Feb 18 23:12:18 ubuntu kernel: [    0.552628] ohci_hcd 0000:00:02.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.552631] ohci_hcd 0000:00:02.0: OHCI Host Controller
Feb 18 23:12:18 ubuntu kernel: [    0.552747] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Feb 18 23:12:18 ubuntu kernel: [    0.552836] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
Feb 18 23:12:18 ubuntu kernel: [    0.610130] hub 2-0:1.0: USB hub found
Feb 18 23:12:18 ubuntu kernel: [    0.610190] hub 2-0:1.0: 8 ports detected
Feb 18 23:12:18 ubuntu kernel: [    0.610329] uhci_hcd: USB Universal Host Controller Interface driver
Feb 18 23:12:18 ubuntu kernel: [    0.610442] usbcore: registered new interface driver libusual
Feb 18 23:12:18 ubuntu kernel: [    0.610545] i8042: PNP: No PS/2 controller found. Probing ports directly.
Feb 18 23:12:18 ubuntu kernel: [    0.611010] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 18 23:12:18 ubuntu kernel: [    0.611072] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 18 23:12:18 ubuntu kernel: [    0.611290] mousedev: PS/2 mouse device common for all mice
Feb 18 23:12:18 ubuntu kernel: [    0.611512] rtc_cmos 00:04: RTC can wake from S4
Feb 18 23:12:18 ubuntu kernel: [    0.611706] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Feb 18 23:12:18 ubuntu kernel: [    0.611796] rtc0: alarms up to one year, y3k, 242 bytes nvram
Feb 18 23:12:18 ubuntu kernel: [    0.611936] device-mapper: uevent: version 1.0.3
Feb 18 23:12:18 ubuntu kernel: [    0.612093] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Feb 18 23:12:18 ubuntu kernel: [    0.612168] cpuidle: using governor ladder
Feb 18 23:12:18 ubuntu kernel: [    0.612225] cpuidle: using governor menu
Feb 18 23:12:18 ubuntu kernel: [    0.612281] EFI Variables Facility v0.08 2004-May-17
Feb 18 23:12:18 ubuntu kernel: [    0.612578] TCP cubic registered
Feb 18 23:12:18 ubuntu kernel: [    0.612742] NET: Registered protocol family 10
Feb 18 23:12:18 ubuntu kernel: [    0.613285] NET: Registered protocol family 17
Feb 18 23:12:18 ubuntu kernel: [    0.613345] Registering the dns_resolver key type
Feb 18 23:12:18 ubuntu kernel: [    0.613541] PM: Hibernation image not present or could not be loaded.
Feb 18 23:12:18 ubuntu kernel: [    0.613552] registered taskstats version 1
Feb 18 23:12:18 ubuntu kernel: [    0.620244]   Magic number: 1:385:201
Feb 18 23:12:18 ubuntu kernel: [    0.620426] rtc_cmos 00:04: setting system clock to 2013-02-18 23:10:08 UTC (1361229008)
Feb 18 23:12:18 ubuntu kernel: [    0.620500] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ (2 cpu cores) (version 2.20.00)
Feb 18 23:12:18 ubuntu kernel: [    0.620611] powernow-k8: fid 0x12 (2600 MHz), vid 0x8
Feb 18 23:12:18 ubuntu kernel: [    0.620668] powernow-k8: fid 0x10 (2400 MHz), vid 0xa
Feb 18 23:12:18 ubuntu kernel: [    0.620725] powernow-k8: fid 0xe (2200 MHz), vid 0xc
Feb 18 23:12:18 ubuntu kernel: [    0.620782] powernow-k8: fid 0xc (2000 MHz), vid 0xe
Feb 18 23:12:18 ubuntu kernel: [    0.620840] powernow-k8: fid 0xa (1800 MHz), vid 0x10
Feb 18 23:12:18 ubuntu kernel: [    0.620897] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
Feb 18 23:12:18 ubuntu kernel: [    0.621034] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 18 23:12:18 ubuntu kernel: [    0.621093] EDD information not available.
Feb 18 23:12:18 ubuntu kernel: [    0.622836] Freeing unused kernel memory: 924k freed
Feb 18 23:12:18 ubuntu kernel: [    0.623334] Write protecting the kernel read-only data: 12288k
Feb 18 23:12:18 ubuntu kernel: [    0.628633] Freeing unused kernel memory: 1604k freed
Feb 18 23:12:18 ubuntu kernel: [    0.633472] Freeing unused kernel memory: 1196k freed
Feb 18 23:12:18 ubuntu kernel: [    0.706094] Floppy drive(s): fd0 is 1.44M
Feb 18 23:12:18 ubuntu kernel: [    0.724172] FDC 0 is a post-1991 82077
Feb 18 23:12:18 ubuntu kernel: [    0.759756] sata_nv 0000:00:08.0: version 3.5
Feb 18 23:12:18 ubuntu kernel: [    0.759773] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
Feb 18 23:12:18 ubuntu kernel: [    0.759893] sata_nv 0000:00:08.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.763800] scsi0 : sata_nv
Feb 18 23:12:18 ubuntu kernel: [    0.766313] scsi1 : sata_nv
Feb 18 23:12:18 ubuntu kernel: [    0.766531] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 21
Feb 18 23:12:18 ubuntu kernel: [    0.766592] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 21
Feb 18 23:12:18 ubuntu kernel: [    0.771212] pata_amd 0000:00:06.0: version 0.4.1
Feb 18 23:12:18 ubuntu kernel: [    0.771262] pata_amd 0000:00:06.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    0.773430] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Feb 18 23:12:18 ubuntu kernel: [    0.773706] scsi2 : pata_amd
Feb 18 23:12:18 ubuntu kernel: [    0.775407] scsi3 : pata_amd
Feb 18 23:12:18 ubuntu kernel: [    0.775907] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Feb 18 23:12:18 ubuntu kernel: [    0.775968] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Feb 18 23:12:18 ubuntu kernel: [    0.776110] 8139cp 0000:01:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Feb 18 23:12:18 ubuntu kernel: [    0.778935] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Feb 18 23:12:18 ubuntu kernel: [    0.779184] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Feb 18 23:12:18 ubuntu kernel: [    0.779258] r8169 0000:01:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Feb 18 23:12:18 ubuntu kernel: [    0.779348] r8169 0000:01:08.0: (unregistered net_device): not PCI Express
Feb 18 23:12:18 ubuntu kernel: [    0.779811] r8169 0000:01:08.0: eth0: RTL8169sc/8110sc at 0xffffc90000328000, 00:50:8d:ca:5b:5d, XID 18000000 IRQ 18
Feb 18 23:12:18 ubuntu kernel: [    0.779881] r8169 0000:01:08.0: eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Feb 18 23:12:18 ubuntu kernel: [    0.940331] ata3.00: ATAPI: SONY    DVD RW AW-Q170A, 1.72, max UDMA/66
Feb 18 23:12:18 ubuntu kernel: [    0.940400] ata3: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
Feb 18 23:12:18 ubuntu kernel: [    0.956259] ata3.00: configured for UDMA/66
Feb 18 23:12:18 ubuntu kernel: [    0.976025] usb 1-2: new high-speed USB device number 3 using ehci_hcd
Feb 18 23:12:18 ubuntu kernel: [    1.109892] hub 1-2:1.0: USB hub found
Feb 18 23:12:18 ubuntu kernel: [    1.110200] hub 1-2:1.0: 4 ports detected
Feb 18 23:12:18 ubuntu kernel: [    1.232039] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 18 23:12:18 ubuntu kernel: [    1.259408] ata1.00: ATA-7: WDC WD2500JS-00SGB0, 20.06C03, max UDMA/133
Feb 18 23:12:18 ubuntu kernel: [    1.259468] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Feb 18 23:12:18 ubuntu kernel: [    1.265059] ata1.00: configured for UDMA/133
Feb 18 23:12:18 ubuntu kernel: [    1.265266] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JS-00S 20.0 PQ: 0 ANSI: 5
Feb 18 23:12:18 ubuntu kernel: [    1.265490] sd 0:0:0:0: Attached scsi generic sg0 type 0
Feb 18 23:12:18 ubuntu kernel: [    1.265549] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Feb 18 23:12:18 ubuntu kernel: [    1.265592] sd 0:0:0:0: [sda] Write Protect is off
Feb 18 23:12:18 ubuntu kernel: [    1.265594] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 18 23:12:18 ubuntu kernel: [    1.265612] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 18 23:12:18 ubuntu kernel: [    1.267192]  sda: sda1
Feb 18 23:12:18 ubuntu kernel: [    1.267533] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 18 23:12:18 ubuntu kernel: [    1.412022] usb 2-1: new full-speed USB device number 2 using ohci_hcd
Feb 18 23:12:18 ubuntu kernel: [    1.586224] ata2: SATA link down (SStatus 0 SControl 300)
Feb 18 23:12:18 ubuntu kernel: [    1.587348] scsi 2:0:0:0: CD-ROM            SONY     DVD RW AW-Q170A  1.72 PQ: 0 ANSI: 5
Feb 18 23:12:18 ubuntu kernel: [    1.588557] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Feb 18 23:12:18 ubuntu kernel: [    1.588618] cdrom: Uniform CD-ROM driver Revision: 3.20
Feb 18 23:12:18 ubuntu kernel: [    1.588783] sr 2:0:0:0: Attached scsi CD-ROM sr0
Feb 18 23:12:18 ubuntu kernel: [    1.588907] sr 2:0:0:0: Attached scsi generic sg1 type 5
Feb 18 23:12:18 ubuntu kernel: [    1.589066] ata4: port disabled--ignoring
Feb 18 23:12:18 ubuntu kernel: [    1.589978] 8139too: 8139too Fast Ethernet driver 0.9.28
Feb 18 23:12:18 ubuntu kernel: [    1.590503] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
Feb 18 23:12:18 ubuntu kernel: [    1.590576] 8139too 0000:01:06.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
Feb 18 23:12:18 ubuntu kernel: [    1.591420] 8139too 0000:01:06.0: eth1: RealTek RTL8139 at 0xcc00, 6c:fd:b9:22:e6:17, IRQ 17
Feb 18 23:12:18 ubuntu kernel: [    1.645313] input: Razer Razer DeathAdder as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input2
Feb 18 23:12:18 ubuntu kernel: [    1.645521] generic-usb 0003:1532:0016.0001: input,hidraw0: USB HID v1.11 Mouse [Razer Razer DeathAdder] on usb-0000:00:02.0-1/input0
Feb 18 23:12:18 ubuntu kernel: [    1.645612] usbcore: registered new interface driver usbhid
Feb 18 23:12:18 ubuntu kernel: [    1.645672] usbhid: USB HID core driver
Feb 18 23:12:18 ubuntu kernel: [    1.708331] usb 1-2.1: new low-speed USB device number 4 using ehci_hcd
Feb 18 23:12:18 ubuntu kernel: [    1.812710] input: LOGITECH G110 G-keys as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.1/1-2.1:1.0/input/input3
Feb 18 23:12:18 ubuntu kernel: [    1.812931] generic-usb 0003:046D:C22B.0002: input,hiddev0,hidraw1: USB HID v1.00 Keypad [LOGITECH G110 G-keys] on usb-0000:00:02.1-2.1/input0
Feb 18 23:12:18 ubuntu kernel: [    1.813065] usbhid 1-2.1:1.1: couldn't find an input interrupt endpoint
Feb 18 23:12:18 ubuntu kernel: [    1.884338] usb 1-2.3: new low-speed USB device number 5 using ehci_hcd
Feb 18 23:12:18 ubuntu kernel: [    1.986085] input: Gaming Keyboard G110 as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/input/input4
Feb 18 23:12:18 ubuntu kernel: [    1.986682] generic-usb 0003:046D:C22A.0003: input,hidraw2: USB HID v1.10 Keyboard [Gaming Keyboard G110] on usb-0000:00:02.1-2.3/input0
Feb 18 23:12:18 ubuntu kernel: [    1.992896] input: Gaming Keyboard G110 as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.1/input/input5
Feb 18 23:12:18 ubuntu kernel: [    1.993121] generic-usb 0003:046D:C22A.0004: input,hiddev0,hidraw3: USB HID v1.10 Device [Gaming Keyboard G110] on usb-0000:00:02.1-2.3/input1
Feb 18 23:12:18 ubuntu kernel: [    2.230126] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
Feb 18 23:12:18 ubuntu kernel: [    4.955028] MCE: In-kernel MCE decoding enabled.
Feb 18 23:12:18 ubuntu kernel: [    4.965639] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
Feb 18 23:12:18 ubuntu kernel: [    5.002731] EDAC MC: Ver: 2.1.0
Feb 18 23:12:18 ubuntu kernel: [    5.084559] AMD64 EDAC driver v3.4.0
Feb 18 23:12:18 ubuntu kernel: [    5.084670] EDAC amd64: DRAM ECC disabled.
Feb 18 23:12:18 ubuntu kernel: [    5.084738] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Feb 18 23:12:18 ubuntu kernel: [    5.084740]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Feb 18 23:12:18 ubuntu kernel: [    5.084741]  (Note that use of the override may cause unknown side effects.)
Feb 18 23:12:18 ubuntu kernel: [    5.085036] parport_pc 00:09: reported by Plug and Play ACPI
Feb 18 23:12:18 ubuntu kernel: [    5.085153] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Feb 18 23:12:18 ubuntu kernel: [    5.112445] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
Feb 18 23:12:18 ubuntu kernel: [    5.112533] i2c i2c-1: nForce2 SMBus adapter at 0xf400
Feb 18 23:12:18 ubuntu kernel: [    5.185592] ppdev: user-space parallel port driver
Feb 18 23:12:18 ubuntu kernel: [    5.219772] wmi: Mapper loaded
Feb 18 23:12:18 ubuntu kernel: [    5.415231] Linux video capture interface: v2.00
Feb 18 23:12:18 ubuntu kernel: [    5.512964] [drm] Initialized drm 1.1.0 20060810
Feb 18 23:12:18 ubuntu kernel: [    5.652924] IR NEC protocol handler initialized
Feb 18 23:12:18 ubuntu kernel: [    5.670118] saa7130/34: v4l2 driver version 0, 2, 17 loaded
Feb 18 23:12:18 ubuntu kernel: [    5.670608] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Feb 18 23:12:18 ubuntu kernel: [    5.670691] saa7134 0000:01:05.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Feb 18 23:12:18 ubuntu kernel: [    5.670763] saa7130[0]: found at 0000:01:05.0, rev: 1, irq: 16, latency: 15, mmio: 0xfdaff000
Feb 18 23:12:18 ubuntu kernel: [    5.670834] saa7134 0000:01:05.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    5.670838] saa7134: Board is currently unknown. You might try to use the card=<nr>
Feb 18 23:12:18 ubuntu kernel: [    5.670839] saa7134: insmod option to specify which board do you have, but this is
Feb 18 23:12:18 ubuntu kernel: [    5.670840] saa7134: somewhat risky, as might damage your card. It is better to ask
Feb 18 23:12:18 ubuntu kernel: [    5.670841] saa7134: for support at linux-media@vger.kernel.org.
Feb 18 23:12:18 ubuntu kernel: [    5.670842] saa7134: The supported cards are:
Feb 18 23:12:18 ubuntu kernel: [    5.671947] saa7134:   card=0 -> UNKNOWN/GENERIC                         
Feb 18 23:12:18 ubuntu kernel: [    5.672084] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
Feb 18 23:12:18 ubuntu kernel: [    5.672292] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
Feb 18 23:12:18 ubuntu kernel: [    5.672498] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
Feb 18 23:12:18 ubuntu kernel: [    5.672706] saa7134:   card=4 -> EMPRESS                                  1131:6752
Feb 18 23:12:18 ubuntu kernel: [    5.672864] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
Feb 18 23:12:18 ubuntu kernel: [    5.673022] saa7134:   card=6 -> Tevion MD 9717                          
Feb 18 23:12:18 ubuntu kernel: [    5.673128] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
Feb 18 23:12:18 ubuntu kernel: [    5.673331] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
Feb 18 23:12:18 ubuntu kernel: [    5.673488] saa7134:   card=9 -> Medion 5044                             
Feb 18 23:12:18 ubuntu kernel: [    5.673593] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
Feb 18 23:12:18 ubuntu kernel: [    5.673697] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
Feb 18 23:12:18 ubuntu kernel: [    5.673855] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
Feb 18 23:12:18 ubuntu kernel: [    5.674060] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
Feb 18 23:12:18 ubuntu kernel: [    5.674165] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
Feb 18 23:12:18 ubuntu kernel: [    5.674322] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
Feb 18 23:12:18 ubuntu kernel: [    5.674482] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
Feb 18 23:12:18 ubuntu kernel: [    5.674731] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
Feb 18 23:12:18 ubuntu kernel: [    5.674889] saa7134:   card=18 -> BMK MPEX No Tuner                       
Feb 18 23:12:18 ubuntu kernel: [    5.674993] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
Feb 18 23:12:18 ubuntu kernel: [    5.675151] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
Feb 18 23:12:18 ubuntu kernel: [    5.675308] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
Feb 18 23:12:18 ubuntu kernel: [    5.675466] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
Feb 18 23:12:18 ubuntu kernel: [    5.675623] saa7134:   card=23 -> BMK MPEX Tuner                          
Feb 18 23:12:18 ubuntu kernel: [    5.675728] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
Feb 18 23:12:18 ubuntu kernel: [    5.675886] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
Feb 18 23:12:18 ubuntu kernel: [    5.676077] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
Feb 18 23:12:18 ubuntu kernel: [    5.676234] saa7134:   card=27 -> Manli MuchTV M-TV002                    
Feb 18 23:12:18 ubuntu kernel: [    5.676339] saa7134:   card=28 -> Manli MuchTV M-TV001                    
Feb 18 23:12:18 ubuntu kernel: [    5.676444] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
Feb 18 23:12:18 ubuntu kernel: [    5.676601] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
Feb 18 23:12:18 ubuntu kernel: [    5.676759] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
Feb 18 23:12:18 ubuntu kernel: [    5.676917] saa7134:   card=32 -> AVACS SmartTV                           
Feb 18 23:12:18 ubuntu kernel: [    5.677021] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
Feb 18 23:12:18 ubuntu kernel: [    5.677179] saa7134:   card=34 -> Noval Prime TV 7133                     
Feb 18 23:12:18 ubuntu kernel: [    5.677284] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
Feb 18 23:12:18 ubuntu kernel: [    5.677441] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
Feb 18 23:12:18 ubuntu kernel: [    5.677599] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
Feb 18 23:12:18 ubuntu kernel: [    5.677703] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
Feb 18 23:12:18 ubuntu kernel: [    5.677861] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
Feb 18 23:12:18 ubuntu kernel: [    5.678110] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
Feb 18 23:12:18 ubuntu kernel: [    5.678268] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
Feb 18 23:12:18 ubuntu kernel: [    5.678425] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
Feb 18 23:12:18 ubuntu kernel: [    5.678530] saa7134:   card=43 -> :Zolid Xpert TV7134                     
Feb 18 23:12:18 ubuntu kernel: [    5.678635] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
Feb 18 23:12:18 ubuntu kernel: [    5.678739] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
Feb 18 23:12:18 ubuntu kernel: [    5.678897] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
Feb 18 23:12:18 ubuntu kernel: [    5.679055] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
Feb 18 23:12:18 ubuntu kernel: [    5.679212] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
Feb 18 23:12:18 ubuntu kernel: [    5.679370] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
Feb 18 23:12:18 ubuntu kernel: [    5.679527] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
Feb 18 23:12:18 ubuntu kernel: [    5.679685] saa7134:   card=51 -> ProVideo PV952                           1540:9524
Feb 18 23:12:18 ubuntu kernel: [    5.679842] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
Feb 18 23:12:18 ubuntu kernel: [    5.680014] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
Feb 18 23:12:18 ubuntu kernel: [    5.680175] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
Feb 18 23:12:18 ubuntu kernel: [    5.680471] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
Feb 18 23:12:18 ubuntu kernel: [    5.680674] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
Feb 18 23:12:18 ubuntu kernel: [    5.680832] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
Feb 18 23:12:18 ubuntu kernel: [    5.680990] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
Feb 18 23:12:18 ubuntu kernel: [    5.681285] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
Feb 18 23:12:18 ubuntu kernel: [    5.681390] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
Feb 18 23:12:18 ubuntu kernel: [    5.681640] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
Feb 18 23:12:18 ubuntu kernel: [    5.681797] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
Feb 18 23:12:18 ubuntu kernel: [    5.681902] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
Feb 18 23:12:18 ubuntu kernel: [    5.682007] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
Feb 18 23:12:18 ubuntu kernel: [    5.682164] saa7134:   card=65 -> V-Stream Studio TV Terminator           
Feb 18 23:12:18 ubuntu kernel: [    5.682269] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
Feb 18 23:12:18 ubuntu kernel: [    5.682374] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
Feb 18 23:12:18 ubuntu kernel: [    5.682531] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
Feb 18 23:12:18 ubuntu kernel: [    5.682689] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
Feb 18 23:12:18 ubuntu kernel: [    5.682847] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
Feb 18 23:12:18 ubuntu kernel: [    5.683004] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
Feb 18 23:12:18 ubuntu kernel: [    5.683162] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
Feb 18 23:12:18 ubuntu kernel: [    5.683319] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
Feb 18 23:12:18 ubuntu kernel: [    5.683477] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
Feb 18 23:12:18 ubuntu kernel: [    5.683634] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
Feb 18 23:12:18 ubuntu kernel: [    5.683791] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
Feb 18 23:12:18 ubuntu kernel: [    5.683949] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
Feb 18 23:12:18 ubuntu kernel: [    5.684124] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
Feb 18 23:12:18 ubuntu kernel: [    5.684282] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
Feb 18 23:12:18 ubuntu kernel: [    5.684386] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
Feb 18 23:12:18 ubuntu kernel: [    5.684544] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
Feb 18 23:12:18 ubuntu kernel: [    5.684702] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
Feb 18 23:12:18 ubuntu kernel: [    5.684906] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
Feb 18 23:12:18 ubuntu kernel: [    5.685063] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
Feb 18 23:12:18 ubuntu kernel: [    5.685221] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
Feb 18 23:12:18 ubuntu kernel: [    5.685430] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
Feb 18 23:12:18 ubuntu kernel: [    5.685634] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
Feb 18 23:12:18 ubuntu kernel: [    5.685791] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
Feb 18 23:12:18 ubuntu kernel: [    5.685949] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
Feb 18 23:12:18 ubuntu kernel: [    5.686106] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
Feb 18 23:12:18 ubuntu kernel: [    5.686310] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
Feb 18 23:12:18 ubuntu kernel: [    5.686467] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
Feb 18 23:12:18 ubuntu kernel: [    5.686624] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
Feb 18 23:12:18 ubuntu kernel: [    5.686782] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
Feb 18 23:12:18 ubuntu kernel: [    5.687077] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
Feb 18 23:12:18 ubuntu kernel: [    5.687235] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
Feb 18 23:12:18 ubuntu kernel: [    5.687484] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
Feb 18 23:12:18 ubuntu kernel: [    5.687688] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
Feb 18 23:12:18 ubuntu kernel: [    5.687845] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
Feb 18 23:12:18 ubuntu kernel: [    5.688813] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
Feb 18 23:12:18 ubuntu kernel: [    5.688971] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
Feb 18 23:12:18 ubuntu kernel: [    5.689128] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
Feb 18 23:12:18 ubuntu kernel: [    5.689286] saa7134:   card=103 -> Compro Videomate DVB-T200A              
Feb 18 23:12:18 ubuntu kernel: [    5.689391] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
Feb 18 23:12:18 ubuntu kernel: [    5.689778] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
Feb 18 23:12:18 ubuntu kernel: [    5.689936] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
Feb 18 23:12:18 ubuntu kernel: [    5.690185] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
Feb 18 23:12:18 ubuntu kernel: [    5.690343] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
Feb 18 23:12:18 ubuntu kernel: [    5.690500] saa7134:   card=109 -> Philips Tiger - S Reference design      
Feb 18 23:12:18 ubuntu kernel: [    5.690605] saa7134:   card=110 -> Avermedia M102                           1461:f31e
Feb 18 23:12:18 ubuntu kernel: [    5.690763] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
Feb 18 23:12:18 ubuntu kernel: [    5.690920] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
Feb 18 23:12:18 ubuntu kernel: [    5.691078] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
Feb 18 23:12:18 ubuntu kernel: [    5.691236] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
Feb 18 23:12:18 ubuntu kernel: [    5.691393] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
Feb 18 23:12:18 ubuntu kernel: [    5.691551] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
Feb 18 23:12:18 ubuntu kernel: [    5.691708] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
Feb 18 23:12:18 ubuntu kernel: [    5.691866] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
Feb 18 23:12:18 ubuntu kernel: [    5.692043] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
Feb 18 23:12:18 ubuntu kernel: [    5.692210] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
Feb 18 23:12:18 ubuntu kernel: [    5.692377] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
Feb 18 23:12:18 ubuntu kernel: [    5.692535] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
Feb 18 23:12:18 ubuntu kernel: [    5.692693] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
Feb 18 23:12:18 ubuntu kernel: [    5.692850] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
Feb 18 23:12:18 ubuntu kernel: [    5.693008] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
Feb 18 23:12:18 ubuntu kernel: [    5.693165] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
Feb 18 23:12:18 ubuntu kernel: [    5.693323] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
Feb 18 23:12:18 ubuntu kernel: [    5.693527] saa7134:   card=128 -> Beholder BeholdTV Columbus TV/FM         0000:5201
Feb 18 23:12:18 ubuntu kernel: [    5.693684] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
Feb 18 23:12:18 ubuntu kernel: [    5.693842] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
Feb 18 23:12:18 ubuntu kernel: [    5.694000] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
Feb 18 23:12:18 ubuntu kernel: [    5.694157] saa7134:   card=132 -> Genius TVGO AM11MCE                     
Feb 18 23:12:18 ubuntu kernel: [    5.694262] saa7134:   card=133 -> NXP Snake DVB-S reference design        
Feb 18 23:12:18 ubuntu kernel: [    5.694367] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
Feb 18 23:12:18 ubuntu kernel: [    5.694525] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
Feb 18 23:12:18 ubuntu kernel: [    5.694682] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
Feb 18 23:12:18 ubuntu kernel: [    5.694840] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
Feb 18 23:12:18 ubuntu kernel: [    5.694997] saa7134:   card=138 -> Avermedia M115                           1461:a836
Feb 18 23:12:18 ubuntu kernel: [    5.695155] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
Feb 18 23:12:18 ubuntu kernel: [    5.695313] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
Feb 18 23:12:18 ubuntu kernel: [    5.695470] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
Feb 18 23:12:18 ubuntu kernel: [    5.695628] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
Feb 18 23:12:18 ubuntu kernel: [    5.695786] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
Feb 18 23:12:18 ubuntu kernel: [    5.695943] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
Feb 18 23:12:18 ubuntu kernel: [    5.696120] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
Feb 18 23:12:18 ubuntu kernel: [    5.696324] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
Feb 18 23:12:18 ubuntu kernel: [    5.696429] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
Feb 18 23:12:18 ubuntu kernel: [    5.696586] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
Feb 18 23:12:18 ubuntu kernel: [    5.696744] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
Feb 18 23:12:18 ubuntu kernel: [    5.696902] saa7134:   card=150 -> Zogis Real Angel 220                    
Feb 18 23:12:18 ubuntu kernel: [    5.697006] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
Feb 18 23:12:18 ubuntu kernel: [    5.697164] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
Feb 18 23:12:18 ubuntu kernel: [    5.697322] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
Feb 18 23:12:18 ubuntu kernel: [    5.697479] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
Feb 18 23:12:18 ubuntu kernel: [    5.697637] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
Feb 18 23:12:18 ubuntu kernel: [    5.697841] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
Feb 18 23:12:18 ubuntu kernel: [    5.698090] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
Feb 18 23:12:18 ubuntu kernel: [    5.698248] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
Feb 18 23:12:18 ubuntu kernel: [    5.698405] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
Feb 18 23:12:18 ubuntu kernel: [    5.698563] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
Feb 18 23:12:18 ubuntu kernel: [    5.698720] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
Feb 18 23:12:18 ubuntu kernel: [    5.698878] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
Feb 18 23:12:18 ubuntu kernel: [    5.699036] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
Feb 18 23:12:18 ubuntu kernel: [    5.699193] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
Feb 18 23:12:18 ubuntu kernel: [    5.699351] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
Feb 18 23:12:18 ubuntu kernel: [    5.699508] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
Feb 18 23:12:18 ubuntu kernel: [    5.699666] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
Feb 18 23:12:18 ubuntu kernel: [    5.699824] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
Feb 18 23:12:18 ubuntu kernel: [    5.699981] saa7134:   card=169 -> Compro VideoMate S350/S300               185b:c900
Feb 18 23:12:18 ubuntu kernel: [    5.700155] saa7134:   card=170 -> AverMedia AverTV Studio 505              1461:a115
Feb 18 23:12:18 ubuntu kernel: [    5.700313] saa7134:   card=171 -> Beholder BeholdTV X7                     5ace:7595
Feb 18 23:12:18 ubuntu kernel: [    5.700471] saa7134:   card=172 -> RoverMedia TV Link Pro FM                19d1:0138
Feb 18 23:12:18 ubuntu kernel: [    5.700628] saa7134:   card=173 -> Zolid Hybrid TV Tuner PCI                1131:2004
Feb 18 23:12:18 ubuntu kernel: [    5.700786] saa7134:   card=174 -> Asus Europa Hybrid OEM                   1043:4847
Feb 18 23:12:18 ubuntu kernel: [    5.700944] saa7134:   card=175 -> Leadtek Winfast DTV1000S                 107d:6655
Feb 18 23:12:18 ubuntu kernel: [    5.701101] saa7134:   card=176 -> Beholder BeholdTV 505 RDS                0000:5051
Feb 18 23:12:18 ubuntu kernel: [    5.701259] saa7134:   card=177 -> Hawell HW-404M7                         
Feb 18 23:12:18 ubuntu kernel: [    5.701364] saa7134:   card=178 -> Beholder BeholdTV H7                     5ace:7190
Feb 18 23:12:18 ubuntu kernel: [    5.701521] saa7134:   card=179 -> Beholder BeholdTV A7                     5ace:7090
Feb 18 23:12:18 ubuntu kernel: [    5.701679] saa7134:   card=180 -> Avermedia PCI M733A                      1461:4155 1461:4255
Feb 18 23:12:18 ubuntu kernel: [    5.701883] saa7134:   card=181 -> TechoTrend TT-budget T-3000              13c2:2804
Feb 18 23:12:18 ubuntu kernel: [    5.702040] saa7134:   card=182 -> Kworld PCI SBTVD/ISDB-T Full-Seg Hybrid  17de:b136
Feb 18 23:12:18 ubuntu kernel: [    5.702198] saa7134:   card=183 -> Compro VideoMate Vista M1F               185b:c900
Feb 18 23:12:18 ubuntu kernel: [    5.702356] saa7134:   card=184 -> Encore ENLTV-FM 3                        1a7f:2108
Feb 18 23:12:18 ubuntu kernel: [    5.702513] saa7134:   card=185 -> MagicPro ProHDTV Pro2 DMB-TH/Hybrid      17de:d136
Feb 18 23:12:18 ubuntu kernel: [    5.702671] saa7134:   card=186 -> Beholder BeholdTV 501                    5ace:5010
Feb 18 23:12:18 ubuntu kernel: [    5.702828] saa7134:   card=187 -> Beholder BeholdTV 503 FM                 5ace:5030
Feb 18 23:12:18 ubuntu kernel: [    5.702987] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
Feb 18 23:12:18 ubuntu kernel: [    5.703070] saa7130[0]: board init: gpio is 804000
Feb 18 23:12:18 ubuntu kernel: [    5.737242] IR RC5(x) protocol handler initialized
Feb 18 23:12:18 ubuntu kernel: [    5.786619] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 18 23:12:18 ubuntu kernel: [    5.786627] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 18 23:12:18 ubuntu kernel: [    5.804225] saa7130[0]: Huh, no eeprom present (err=-5)?
Feb 18 23:12:18 ubuntu kernel: [    5.804322] saa7130[0]: registered device video0 [v4l2]
Feb 18 23:12:18 ubuntu kernel: [    5.804378] saa7130[0]: registered device vbi0
Feb 18 23:12:18 ubuntu kernel: [    5.809019] IR RC6 protocol handler initialized
Feb 18 23:12:18 ubuntu kernel: [    5.849500] IR JVC protocol handler initialized
Feb 18 23:12:18 ubuntu kernel: [    5.902404] saa7134 ALSA driver for DMA sound loaded
Feb 18 23:12:18 ubuntu kernel: [    5.902409] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio
Feb 18 23:12:18 ubuntu kernel: [    5.918615] IR Sony protocol handler initialized
Feb 18 23:12:18 ubuntu kernel: [    5.931970] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
Feb 18 23:12:18 ubuntu kernel: [    5.931989] snd_hda_intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
Feb 18 23:12:18 ubuntu kernel: [    5.931992] hda_intel: Disabling MSI
Feb 18 23:12:18 ubuntu kernel: [    5.932090] snd_hda_intel 0000:00:05.0: setting latency timer to 64
Feb 18 23:12:18 ubuntu kernel: [    5.946247] IR MCE Keyboard/mouse protocol handler initialized
Feb 18 23:12:18 ubuntu kernel: [    5.960591] lirc_dev: IR Remote Control driver registered, major 250 
Feb 18 23:12:18 ubuntu kernel: [    5.969351] IR LIRC bridge handler initialized
Feb 18 23:12:18 ubuntu kernel: [    6.568035] hda_codec: ALC883: BIOS auto-probing.
Feb 18 23:12:18 ubuntu kernel: [    7.776102] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input6
Feb 18 23:12:18 ubuntu kernel: [    7.776232] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input7
Feb 18 23:12:18 ubuntu kernel: [    7.776308] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
Feb 18 23:12:18 ubuntu kernel: [    7.776393] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
Feb 18 23:12:18 ubuntu kernel: [    7.776486] input: HDA NVidia Line-Out Side as /devices/pci0000:00/0000:00:05.0/sound/card0/input10
Feb 18 23:12:18 ubuntu kernel: [    7.776577] input: HDA NVidia Line-Out CLFE as /devices/pci0000:00/0000:00:05.0/sound/card0/input11
Feb 18 23:12:18 ubuntu kernel: [    7.776674] input: HDA NVidia Line-Out Surround as /devices/pci0000:00/0000:00:05.0/sound/card0/input12
Feb 18 23:12:18 ubuntu kernel: [    7.776765] input: HDA NVidia Line-Out Front as /devices/pci0000:00/0000:00:05.0/sound/card0/input13
Feb 18 23:12:18 ubuntu kernel: [   26.965981] Adding 262140k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262140k 
Feb 18 23:12:18 ubuntu kernel: [   27.106256] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
Feb 18 23:12:18 ubuntu kernel: [  129.391882] lp0: using parport0 (interrupt-driven).
Feb 18 23:12:18 ubuntu kernel: [  129.666370] AMD64 EDAC driver v3.4.0
Feb 18 23:12:18 ubuntu kernel: [  129.666414] EDAC amd64: DRAM ECC disabled.
Feb 18 23:12:18 ubuntu kernel: [  129.666419] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Feb 18 23:12:18 ubuntu kernel: [  129.666420]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Feb 18 23:12:18 ubuntu kernel: [  129.666422]  (Note that use of the override may cause unknown side effects.)
Feb 18 23:12:18 ubuntu kernel: [  129.704521] init: failsafe main process (1288) killed by TERM signal
Feb 18 23:12:18 ubuntu udev-configure-printer: add /module/lp
Feb 18 23:12:18 ubuntu udev-configure-printer: Failed to get parent
Feb 18 23:12:18 ubuntu udev-configure-printer: add /devices/pnp0/00:09/printer/lp0
Feb 18 23:12:18 ubuntu udev-configure-printer: Failed to get parent
Feb 18 23:12:18 ubuntu kernel: [  130.646669] type=1400 audit(1361257938.519:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1570 comm="apparmor_parser"
Feb 18 23:12:18 ubuntu kernel: [  130.669200] type=1400 audit(1361257938.543:3): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=1571 comm="apparmor_parser"
Feb 18 23:12:18 ubuntu kernel: [  130.669664] type=1400 audit(1361257938.543:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1571 comm="apparmor_parser"
Feb 18 23:12:18 ubuntu kernel: [  130.669917] type=1400 audit(1361257938.543:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=1571 comm="apparmor_parser"
Feb 18 23:12:18 ubuntu kernel: [  130.736861] type=1400 audit(1361257938.611:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1581 comm="apparmor_parser"
Feb 18 23:12:18 ubuntu kernel: [  130.737405] type=1400 audit(1361257938.611:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1581 comm="apparmor_parser"
Feb 18 23:12:18 ubuntu kernel: [  130.808244] init: udev-fallback-graphics main process (1579) terminated with status 1
Feb 18 23:12:18 ubuntu kernel: [  130.849586] type=1400 audit(1361257938.723:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1597 comm="apparmor_parser"
Feb 18 23:12:18 ubuntu kernel: [  130.858374] init: friendly-recovery post-stop process (1116) terminated with status 1
Feb 18 23:12:18 ubuntu kernel: [  130.985688] type=1400 audit(1361257938.859:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1615 comm="apparmor_parser"
Feb 18 23:12:18 ubuntu kernel: [  130.986234] type=1400 audit(1361257938.859:10): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1615 comm="apparmor_parser"
Feb 18 23:12:18 ubuntu kernel: [  130.988630] type=1400 audit(1361257938.863:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1577 comm="apparmor_parser"
Feb 18 23:12:19 ubuntu bluetoothd[1620]: Bluetooth daemon 4.98
Feb 18 23:12:19 ubuntu bluetoothd[1620]: Starting SDP server
Feb 18 23:12:19 ubuntu avahi-daemon[1628]: Found user 'avahi' (UID 106) and group 'avahi' (GID 118).
Feb 18 23:12:19 ubuntu avahi-daemon[1628]: Successfully dropped root privileges.
Feb 18 23:12:19 ubuntu avahi-daemon[1628]: avahi-daemon 0.6.30 starting up.
Feb 18 23:12:19 ubuntu avahi-daemon[1628]: Successfully called chroot().
Feb 18 23:12:19 ubuntu avahi-daemon[1628]: Successfully dropped remaining capabilities.
Feb 18 23:12:19 ubuntu kernel: [  131.517675] Bluetooth: Core ver 2.16
Feb 18 23:12:19 ubuntu kernel: [  131.517698] NET: Registered protocol family 31
Feb 18 23:12:19 ubuntu kernel: [  131.517700] Bluetooth: HCI device and connection manager initialized
Feb 18 23:12:19 ubuntu kernel: [  131.517704] Bluetooth: HCI socket layer initialized
Feb 18 23:12:19 ubuntu kernel: [  131.517706] Bluetooth: L2CAP socket layer initialized
Feb 18 23:12:19 ubuntu kernel: [  131.517712] Bluetooth: SCO socket layer initialized
Feb 18 23:12:19 ubuntu avahi-daemon[1628]: Loading service file /services/udisks.service.
Feb 18 23:12:19 ubuntu avahi-daemon[1628]: Network interface enumeration completed.
Feb 18 23:12:19 ubuntu avahi-daemon[1628]: Registering HINFO record with values 'X86_64'/'LINUX'.
Feb 18 23:12:19 ubuntu avahi-daemon[1628]: Server startup complete. Host name is ubuntu.local. Local service cookie is 3951485250.
Feb 18 23:12:19 ubuntu avahi-daemon[1628]: Service "ubuntu" (/services/udisks.service) successfully established.
Feb 18 23:12:19 ubuntu bluetoothd[1620]: Failed to init alert plugin
Feb 18 23:12:19 ubuntu bluetoothd[1620]: Failed to init time plugin
Feb 18 23:12:19 ubuntu bluetoothd[1620]: Failed to init proximity plugin
Feb 18 23:12:19 ubuntu modem-manager[1602]: <info>  ModemManager (version 0.5.2.0) starting...
Feb 18 23:12:19 ubuntu kernel: [  131.731004] Bluetooth: RFCOMM TTY layer initialized
Feb 18 23:12:19 ubuntu kernel: [  131.731011] Bluetooth: RFCOMM socket layer initialized
Feb 18 23:12:19 ubuntu kernel: [  131.731013] Bluetooth: RFCOMM ver 1.11
Feb 18 23:12:19 ubuntu kernel: [  131.751601] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 18 23:12:19 ubuntu kernel: [  131.751605] Bluetooth: BNEP filters: protocol multicast
Feb 18 23:12:19 ubuntu bluetoothd[1620]: Failed to init gatt_example plugin
Feb 18 23:12:19 ubuntu modem-manager[1602]: <info>  Loaded plugin SimTech
Feb 18 23:12:19 ubuntu modem-manager[1602]: <info>  Loaded plugin Sierra
Feb 18 23:12:19 ubuntu modem-manager[1602]: <info>  Loaded plugin Generic
Feb 18 23:12:19 ubuntu modem-manager[1602]: <info>  Loaded plugin MotoC
Feb 18 23:12:19 ubuntu modem-manager[1602]: <info>  Loaded plugin AnyData
Feb 18 23:12:19 ubuntu modem-manager[1602]: <info>  Loaded plugin Nokia
Feb 18 23:12:19 ubuntu modem-manager[1602]: <info>  Loaded plugin Option High-Speed
Feb 18 23:12:19 ubuntu modem-manager[1602]: <info>  Loaded plugin Samsung
Feb 18 23:12:19 ubuntu modem-manager[1602]: <info>  Loaded plugin Novatel
Feb 18 23:12:19 ubuntu modem-manager[1602]: <info>  Loaded plugin ZTE
Feb 18 23:12:20 ubuntu modem-manager[1602]: <info>  Loaded plugin Huawei
Feb 18 23:12:20 ubuntu modem-manager[1602]: <info>  Loaded plugin Wavecom
Feb 18 23:12:20 ubuntu modem-manager[1602]: <info>  Loaded plugin X22X
Feb 18 23:12:20 ubuntu modem-manager[1602]: <info>  Loaded plugin Ericsson MBM
Feb 18 23:12:20 ubuntu modem-manager[1602]: <info>  Loaded plugin Linktop
Feb 18 23:12:20 ubuntu kernel: [  132.258542] init: alsa-restore main process (1668) terminated with status 99
Feb 18 23:12:20 ubuntu anacron[1681]: Anacron 2.3 started on 2013-02-18
Feb 18 23:12:20 ubuntu cron[1669]: (CRON) INFO (pidfile fd = 3)
Feb 18 23:12:20 ubuntu acpid: starting up with proc fs
Feb 18 23:12:20 ubuntu NetworkManager[1667]: <info> NetworkManager (version 0.9.4.0) is starting...
Feb 18 23:12:20 ubuntu NetworkManager[1667]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Feb 18 23:12:20 ubuntu cron[1690]: (CRON) STARTUP (fork ok)
Feb 18 23:12:20 ubuntu modem-manager[1602]: <info>  Loaded plugin Option
Feb 18 23:12:20 ubuntu anacron[1681]: Will run job `cron.daily' in 5 min.
Feb 18 23:12:20 ubuntu anacron[1681]: Will run job `cron.weekly' in 10 min.
Feb 18 23:12:20 ubuntu anacron[1681]: Will run job `cron.monthly' in 15 min.
Feb 18 23:12:20 ubuntu anacron[1681]: Jobs will be executed sequentially
Feb 18 23:12:20 ubuntu modem-manager[1602]: <info>  Loaded plugin Gobi
Feb 18 23:12:20 ubuntu modem-manager[1602]: <info>  Loaded plugin Longcheer
Feb 18 23:12:20 ubuntu cron[1690]: (CRON) INFO (Running @reboot jobs)
Feb 18 23:12:20 ubuntu NetworkManager[1667]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Feb 18 23:12:20 ubuntu NetworkManager[1667]: <info> DNS: loaded plugin dnsmasq
Feb 18 23:12:20 ubuntu acpid: 35 rules loaded
Feb 18 23:12:20 ubuntu acpid: waiting for events: event logging is off
Feb 18 23:12:20 ubuntu dbus[1588]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Feb 18 23:12:21 ubuntu udev-configure-printer: add /devices/pnp0/00:09/printer/lp0
Feb 18 23:12:21 ubuntu udev-configure-printer: Failed to get parent
Feb 18 23:12:21 ubuntu udev-configure-printer: add /module/lp
Feb 18 23:12:21 ubuntu udev-configure-printer: Failed to get parent
Feb 18 23:12:22 ubuntu polkitd[1757]: started daemon version 0.104 using authority implementation `local' version `0.104'
Feb 18 23:12:22 ubuntu dbus[1588]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    SCPlugin-Ifupdown: init!
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    SCPlugin-Ifupdown: update_system_hostname
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    SCPluginIfupdown: management mode: unmanaged
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:06.0/net/eth1, iface: eth1)
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:06.0/net/eth1, iface: eth1): no ifupdown configuration found.
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0/net/eth0, iface: eth0)
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0/net/eth0, iface: eth0): no ifupdown configuration found.
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    SCPlugin-Ifupdown: end _init.
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    Ifupdown: get unmanaged devices count: 0
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    SCPlugin-Ifupdown: (13169456) ... get_connections.
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    SCPlugin-Ifupdown: (13169456) ... get_connections (managed=false): return empty list.
Feb 18 23:12:23 ubuntu NetworkManager[1667]:    Ifupdown: get unmanaged devices count: 0
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> modem-manager is now available
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> monitoring kernel firmware directory '/lib/firmware'.
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> WiFi enabled by radio killswitch; enabled by state file
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> WWAN enabled by radio killswitch; enabled by state file
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> WiMAX enabled by radio killswitch; enabled by state file
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> Networking is enabled by state file
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <warn> failed to allocate link cache: (-10) Operation not supported
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth1): carrier is OFF
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth1): new Ethernet device (driver: '8139too' ifindex: 3)
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth1): now managed
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth1): bringing up device.
Feb 18 23:12:23 ubuntu kernel: [  135.163441] 8139too 0000:01:06.0: eth1: link down
Feb 18 23:12:23 ubuntu kernel: [  135.164196] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth1): preparing device.
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth1): deactivating device (reason 'managed') [2]
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:04.0/0000:01:06.0/net/eth1
Feb 18 23:12:23 ubuntu kernel: [  135.164999] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <warn> failed to allocate link cache: (-10) Operation not supported
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth0): carrier is OFF
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth0): now managed
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth0): bringing up device.
Feb 18 23:12:23 ubuntu kernel: [  135.177282] r8169 0000:01:08.0: eth0: link down
Feb 18 23:12:23 ubuntu kernel: [  135.177292] r8169 0000:01:08.0: eth0: link down
Feb 18 23:12:23 ubuntu kernel: [  135.179217] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth0): preparing device.
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> (eth0): deactivating device (reason 'managed') [2]
Feb 18 23:12:23 ubuntu NetworkManager[1667]: <info> Added default wired connection 'Wired connection 2' for /sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0/net/eth0
Feb 18 23:12:23 ubuntu kernel: [  135.180823] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 18 23:12:23 ubuntu acpid: client connected from 1739[0:0]
Feb 18 23:12:23 ubuntu acpid: 1 client rule loaded
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> (eth0): carrier now ON (device state 20)
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Auto-activating connection 'Wired connection 2'.
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) starting connection 'Wired connection 2'
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb 18 23:12:24 ubuntu kernel: [  136.897033] r8169 0000:01:08.0: eth0: link up
Feb 18 23:12:24 ubuntu kernel: [  136.897347] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> dhclient started with pid 1910
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) Beginning IP6 addrconf.
Feb 18 23:12:24 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 18 23:12:25 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Feb 18 23:12:25 ubuntu dhclient: Copyright 2004-2011 Internet Systems Consortium.
Feb 18 23:12:25 ubuntu dhclient: All rights reserved.
Feb 18 23:12:25 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Feb 18 23:12:25 ubuntu dhclient: 
Feb 18 23:12:25 ubuntu NetworkManager[1667]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Feb 18 23:12:25 ubuntu dhclient: Listening on LPF/eth0/00:50:8d:ca:5b:5d
Feb 18 23:12:25 ubuntu dhclient: Sending on   LPF/eth0/00:50:8d:ca:5b:5d
Feb 18 23:12:25 ubuntu dhclient: Sending on   Socket/fallback
Feb 18 23:12:25 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Feb 18 23:12:25 ubuntu dhclient: DHCPREQUEST of 192.168.1.13 on eth0 to 255.255.255.255 port 67
Feb 18 23:12:25 ubuntu dhclient: DHCPOFFER of 192.168.1.13 from 192.168.1.1
Feb 18 23:12:25 ubuntu dhclient: DHCPACK of 192.168.1.13 from 192.168.1.1
Feb 18 23:12:25 ubuntu dhclient: bound to 192.168.1.13 -- renewal in 34149 seconds.
Feb 18 23:12:25 ubuntu NetworkManager[1667]: <info> (eth0): DHCPv4 state changed preinit -> bound
Feb 18 23:12:25 ubuntu NetworkManager[1667]: <info>   address 192.168.1.13
Feb 18 23:12:25 ubuntu NetworkManager[1667]: <info>   prefix 24 (255.255.255.0)
Feb 18 23:12:25 ubuntu NetworkManager[1667]: <info>   gateway 192.168.1.1
Feb 18 23:12:25 ubuntu NetworkManager[1667]: <info>   nameserver '192.168.1.1'
Feb 18 23:12:25 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Feb 18 23:12:25 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Feb 18 23:12:25 ubuntu avahi-daemon[1628]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.13.
Feb 18 23:12:25 ubuntu avahi-daemon[1628]: New relevant interface eth0.IPv4 for mDNS.
Feb 18 23:12:25 ubuntu avahi-daemon[1628]: Registering new address record for 192.168.1.13 on eth0.IPv4.
Feb 18 23:12:26 ubuntu dbus[1588]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Feb 18 23:12:26 ubuntu dbus[1588]: [system] Successfully activated service 'org.freedesktop.Accounts'
Feb 18 23:12:26 ubuntu accounts-daemon[1926]: started daemon version 0.6.15
Feb 18 23:12:26 ubuntu NetworkManager[1667]: <info> DNS: starting dnsmasq...
Feb 18 23:12:26 ubuntu NetworkManager[1667]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Feb 18 23:12:26 ubuntu dnsmasq[1928]: started, version 2.59 cache disabled
Feb 18 23:12:26 ubuntu dnsmasq[1928]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Feb 18 23:12:26 ubuntu dnsmasq[1928]: using nameserver 192.168.1.1#53
Feb 18 23:12:26 ubuntu avahi-daemon[1628]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::250:8dff:feca:5b5d.
Feb 18 23:12:26 ubuntu avahi-daemon[1628]: New relevant interface eth0.IPv6 for mDNS.
Feb 18 23:12:26 ubuntu avahi-daemon[1628]: Registering new address record for fe80::250:8dff:feca:5b5d on eth0.*.
Feb 18 23:12:26 ubuntu dbus[1588]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Feb 18 23:12:26 ubuntu NetworkManager[1667]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Feb 18 23:12:26 ubuntu NetworkManager[1667]: <info> Policy set 'Wired connection 2' (eth0) as default for IPv4 routing and DNS.
Feb 18 23:12:26 ubuntu NetworkManager[1667]: <info> Activation (eth0) successful, device activated.
Feb 18 23:12:26 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Feb 18 23:12:26 ubuntu dbus[1588]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb 18 23:12:26 ubuntu dbus[1588]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb 18 23:12:26 ubuntu dbus[1588]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Feb 18 23:12:29 ubuntu dbus[1588]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Feb 18 23:12:29 ubuntu dbus[1588]: [system] Successfully activated service 'org.freedesktop.UPower'
Feb 18 23:12:35 ubuntu kernel: [  147.440017] eth0: no IPv6 routers present
Feb 18 23:12:35 ubuntu ntpdate[2093]: adjust time server 91.189.94.4 offset 0.170815 sec
Feb 18 23:12:44 ubuntu NetworkManager[1667]: <info> (eth0): IP6 addrconf timed out or failed.
Feb 18 23:12:44 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Feb 18 23:12:44 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Feb 18 23:12:44 ubuntu NetworkManager[1667]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Feb 18 23:12:51 ubuntu dbus[1588]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Feb 18 23:12:52 ubuntu dbus[1588]: [system] Successfully activated service 'org.freedesktop.UDisks'
Feb 18 23:12:53 ubuntu dbus[1588]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Feb 18 23:12:54 ubuntu dbus[1588]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Feb 18 23:12:54 ubuntu rtkit-daemon[2435]: Successfully called chroot.
Feb 18 23:12:54 ubuntu rtkit-daemon[2435]: Successfully dropped privileges.
Feb 18 23:12:54 ubuntu rtkit-daemon[2435]: Successfully limited resources.
Feb 18 23:12:54 ubuntu rtkit-daemon[2435]: Running.
Feb 18 23:12:54 ubuntu rtkit-daemon[2435]: Watchdog thread running.
Feb 18 23:12:54 ubuntu rtkit-daemon[2435]: Canary thread running.
Feb 18 23:12:54 ubuntu rtkit-daemon[2435]: Successfully made thread 2433 of process 2433 (n/a) owned by '1000' high priority at nice level -11.
Feb 18 23:12:54 ubuntu rtkit-daemon[2435]: Supervising 1 threads of 1 processes of 1 users.
Feb 18 23:12:56 ubuntu dbus[1588]: [system] Activating service name='com.ubuntu.DeviceDriver' (using servicehelper)
Feb 18 23:12:57 ubuntu dbus[1588]: [system] Successfully activated service 'com.ubuntu.DeviceDriver'
Feb 18 23:12:58 ubuntu rtkit-daemon[2435]: Successfully made thread 2484 of process 2433 (n/a) owned by '1000' RT at priority 5.
Feb 18 23:12:58 ubuntu rtkit-daemon[2435]: Supervising 2 threads of 1 processes of 1 users.
Feb 18 23:12:58 ubuntu rtkit-daemon[2435]: Successfully made thread 2485 of process 2433 (n/a) owned by '1000' RT at priority 5.
Feb 18 23:12:58 ubuntu rtkit-daemon[2435]: Supervising 3 threads of 1 processes of 1 users.
Feb 18 23:13:00 ubuntu rtkit-daemon[2435]: Successfully made thread 2497 of process 2497 (n/a) owned by '1000' high priority at nice level -11.
Feb 18 23:13:00 ubuntu rtkit-daemon[2435]: Supervising 4 threads of 2 processes of 1 users.
Feb 18 23:13:00 ubuntu pulseaudio[2497]: [pulseaudio] pid.c: Daemon already running.
Feb 18 23:13:01 ubuntu dbus[1588]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Feb 18 23:13:02 ubuntu blueman-mechanism: Starting blueman-mechanism 
Feb 18 23:13:02 ubuntu dbus[1588]: [system] Successfully activated service 'org.blueman.Mechanism'
Feb 18 23:13:02 ubuntu blueman-mechanism: loading Network 
Feb 18 23:13:02 ubuntu blueman-mechanism: loading Ppp 
Feb 18 23:13:02 ubuntu blueman-mechanism: loading RfKill 
Feb 18 23:13:02 ubuntu blueman-mechanism: loading Config 
Feb 18 23:13:32 ubuntu blueman-mechanism: Exiting 
Feb 18 23:13:37 ubuntu dbus[1588]: [system] Activating service name='org.debian.apt' (using servicehelper)
Feb 18 23:13:38 ubuntu AptDaemon: INFO: Initializing daemon
Feb 18 23:13:38 ubuntu dbus[1588]: [system] Successfully activated service 'org.debian.apt'
Feb 18 23:13:38 ubuntu AptDaemon: INFO: UpdateCache() was called
Feb 18 23:13:39 ubuntu AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/9a29d52f78e745e0bd1146cc7c34b26c
Feb 18 23:13:39 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/9a29d52f78e745e0bd1146cc7c34b26c
Feb 18 23:13:39 ubuntu AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/9a29d52f78e745e0bd1146cc7c34b26c
Feb 18 23:13:39 ubuntu AptDaemon.Worker: INFO: Updating cache
Feb 18 23:13:55 ubuntu AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/9a29d52f78e745e0bd1146cc7c34b26c
Feb 18 23:17:01 ubuntu CRON[3257]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 18 23:17:20 ubuntu anacron[1681]: Job `cron.daily' started
Feb 18 23:17:20 ubuntu anacron[3325]: Updated timestamp for job `cron.daily' to 2013-02-18
Feb 18 23:19:11 ubuntu kernel: Kernel logging (proc) stopped.
Feb 18 23:19:11 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1539" x-info="http://www.rsyslog.com"] exiting on signal 15.
Feb 18 23:42:37 ubuntu kernel: imklog 5.8.6, log source = /proc/kmsg started.
Feb 18 23:42:37 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1319" x-info="http://www.rsyslog.com"] start
Feb 18 23:42:37 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Feb 18 23:42:37 ubuntu rsyslogd: rsyslogd's userid changed to 101
Feb 18 23:42:37 ubuntu rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Linux version 3.2.0-37-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 (Ubuntu 3.2.0-37.58-generic 3.2.35)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic root=UUID=5884B5E584B5C632 loop=/ubuntu/disks/root.disk ro recovery nomodeset
Feb 18 23:42:37 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Feb 18 23:42:37 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007bee0000 (usable)
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007bee0000 - 000000007bee3000 (ACPI NVS)
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007bee3000 - 000000007bef0000 (ACPI data)
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007bef0000 - 000000007bf00000 (reserved)
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007c000000 - 0000000080000000 (reserved)
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Feb 18 23:42:37 ubuntu kernel: [    0.000000] DMI 2.2 present.
Feb 18 23:42:37 ubuntu kernel: [    0.000000] DMI:   NF-M2S/NF-M2S, BIOS 6.00 PG 11/08/2006
Feb 18 23:42:37 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] No AGP bridge found
Feb 18 23:42:37 ubuntu kernel: [    0.000000] last_pfn = 0x7bee0 max_arch_pfn = 0x400000000
Feb 18 23:42:37 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Feb 18 23:42:37 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   C0000-C7FFF write-protect
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   C8000-FFFFF uncachable
Feb 18 23:42:37 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   0 base 0000000000 mask FFC0000000 write-back
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   1 base 0040000000 mask FFE0000000 write-back
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   2 base 0060000000 mask FFF0000000 write-back
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   3 base 0070000000 mask FFF8000000 write-back
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   4 base 0078000000 mask FFFC000000 write-back
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   5 base 007BF00000 mask FFFFF00000 uncachable
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   6 disabled
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   7 disabled
Feb 18 23:42:37 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb 18 23:42:37 ubuntu kernel: [    0.000000] original variable MTRRs
Feb 18 23:42:37 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 1GB, type WB
Feb 18 23:42:37 ubuntu kernel: [    0.000000] reg 1, base: 1GB, range: 512MB, type WB
Feb 18 23:42:37 ubuntu kernel: [    0.000000] reg 2, base: 1536MB, range: 256MB, type WB
Feb 18 23:42:37 ubuntu kernel: [    0.000000] reg 3, base: 1792MB, range: 128MB, type WB
Feb 18 23:42:37 ubuntu kernel: [    0.000000] reg 4, base: 1920MB, range: 64MB, type WB
Feb 18 23:42:37 ubuntu kernel: [    0.000000] reg 5, base: 1983MB, range: 1MB, type UC
Feb 18 23:42:37 ubuntu kernel: [    0.000000] total RAM covered: 1983M
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Found optimal setting for mtrr clean up
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 3      lose cover RAM: 0G
Feb 18 23:42:37 ubuntu kernel: [    0.000000] New variable MTRRs
Feb 18 23:42:37 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Feb 18 23:42:37 ubuntu kernel: [    0.000000] reg 1, base: 1983MB, range: 1MB, type UC
Feb 18 23:42:37 ubuntu kernel: [    0.000000] reg 2, base: 1984MB, range: 64MB, type UC
Feb 18 23:42:37 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000f3a00] f3a00
Feb 18 23:42:37 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 20000000
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
Feb 18 23:42:37 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000007bee0000
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  0000000000 - 007be00000 page 2M
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  007be00000 - 007bee0000 page 4k
Feb 18 23:42:37 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 7bee0000 @ 1fffc000-20000000
Feb 18 23:42:37 ubuntu kernel: [    0.000000] RAMDISK: 364d0000 - 37260000
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: RSDP 00000000000f7a10 00014 (v00 Nvidia)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: RSDT 000000007bee3040 00038 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: FACP 000000007bee30c0 00074 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: DSDT 000000007bee3180 06378 (v01 NVIDIA AWRDACPI 00001000 MSFT 0100000E)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: FACS 000000007bee0000 00040
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: SSDT 000000007bee9600 0028A (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: _HPT 000000007bee9900 00038 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000098)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: MCFG 000000007bee9980 0003C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: APIC 000000007bee9540 0007C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Feb 18 23:42:37 ubuntu kernel: [    0.000000] No NUMA configuration found
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-000000007bee0000
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000007bee0000
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   NODE_DATA [000000007bedb000 - 000000007bedffff]
Feb 18 23:42:37 ubuntu kernel: [    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff880079600000-ffff88007b5fffff] on node 0
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Zone PFN ranges:
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   Normal   empty
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Feb 18 23:42:37 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Feb 18 23:42:37 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Feb 18 23:42:37 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007bee0
Feb 18 23:42:37 ubuntu kernel: [    0.000000] On node 0 totalpages: 507503
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   DMA zone: 5 pages reserved
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   DMA zone: 3914 pages, LIFO batch:0
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   DMA32 zone: 7868 pages used for memmap
Feb 18 23:42:37 ubuntu kernel: [    0.000000]   DMA32 zone: 495652 pages, LIFO batch:31
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Feb 18 23:42:37 ubuntu kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb 18 23:42:37 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 0 dfl dfl)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: BIOS IRQ0 override ignored.
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: IRQ14 used by override.
Feb 18 23:42:37 ubuntu kernel: [    0.000000] ACPI: IRQ15 used by override.
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 18 23:42:37 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Feb 18 23:42:37 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Feb 18 23:42:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb 18 23:42:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Feb 18 23:42:37 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:70000000)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Feb 18 23:42:37 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
Feb 18 23:42:37 ubuntu kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007bc00000 s83136 r8192 d23360 u1048576
Feb 18 23:42:37 ubuntu kernel: [    0.000000] pcpu-alloc: s83136 r8192 d23360 u1048576 alloc=1*2097152
Feb 18 23:42:37 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 499566
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Policy zone: DMA32
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic root=UUID=5884B5E584B5C632 loop=/ubuntu/disks/root.disk ro recovery nomodeset
Feb 18 23:42:37 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Checking aperture...
Feb 18 23:42:37 ubuntu kernel: [    0.000000] No AGP bridge found
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Node 0: aperture @ e194000000 size 32 MB
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Memory: 1967300k/2030464k available (6569k kernel code, 452k absent, 62712k reserved, 6634k data, 924k init)
Feb 18 23:42:37 ubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Feb 18 23:42:37 ubuntu kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Feb 18 23:42:37 ubuntu kernel: [    0.000000] NR_IRQS:16640 nr_irqs:512 16
Feb 18 23:42:37 ubuntu kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Feb 18 23:42:37 ubuntu kernel: [    0.000000] console [tty0] enabled
Feb 18 23:42:37 ubuntu kernel: [    0.000000] allocated 16777216 bytes of page_cgroup
Feb 18 23:42:37 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Fast TSC calibration failed
Feb 18 23:42:37 ubuntu kernel: [    0.000000] TSC: Unable to calibrate against PIT
Feb 18 23:42:37 ubuntu kernel: [    0.000000] TSC: using PMTIMER reference calibration
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Detected 2612.037 MHz processor.
Feb 18 23:42:37 ubuntu kernel: [    0.000000] Marking TSC unstable due to TSCs unsynchronized
Feb 18 23:42:37 ubuntu kernel: [    0.020062] Calibrating delay loop (skipped), value calculated using timer frequency.. 5224.07 BogoMIPS (lpj=10448148)
Feb 18 23:42:37 ubuntu kernel: [    0.020178] pid_max: default: 32768 minimum: 301
Feb 18 23:42:37 ubuntu kernel: [    0.020259] Security Framework initialized
Feb 18 23:42:37 ubuntu kernel: [    0.020333] AppArmor: AppArmor initialized
Feb 18 23:42:37 ubuntu kernel: [    0.020390] Yama: becoming mindful.
Feb 18 23:42:37 ubuntu kernel: [    0.020661] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Feb 18 23:42:37 ubuntu kernel: [    0.024452] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Feb 18 23:42:37 ubuntu kernel: [    0.025073] Mount-cache hash table entries: 256
Feb 18 23:42:37 ubuntu kernel: [    0.025278] Initializing cgroup subsys cpuacct
Feb 18 23:42:37 ubuntu kernel: [    0.025339] Initializing cgroup subsys memory
Feb 18 23:42:37 ubuntu kernel: [    0.025404] Initializing cgroup subsys devices
Feb 18 23:42:37 ubuntu kernel: [    0.025461] Initializing cgroup subsys freezer
Feb 18 23:42:37 ubuntu kernel: [    0.025519] Initializing cgroup subsys blkio
Feb 18 23:42:37 ubuntu kernel: [    0.025581] Initializing cgroup subsys perf_event
Feb 18 23:42:37 ubuntu kernel: [    0.025668] tseg: 007bf00000
Feb 18 23:42:37 ubuntu kernel: [    0.025670] CPU: Physical Processor ID: 0
Feb 18 23:42:37 ubuntu kernel: [    0.025726] CPU: Processor Core ID: 0
Feb 18 23:42:37 ubuntu kernel: [    0.025783] mce: CPU supports 5 MCE banks
Feb 18 23:42:37 ubuntu kernel: [    0.025849] using AMD E400 aware idle routine
Feb 18 23:42:37 ubuntu kernel: [    0.027418] ACPI: Core revision 20110623
Feb 18 23:42:37 ubuntu kernel: [    0.032013] ftrace: allocating 27033 entries in 107 pages
Feb 18 23:42:37 ubuntu kernel: [    0.036636] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Feb 18 23:42:37 ubuntu kernel: [    0.077911] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02
Feb 18 23:42:37 ubuntu kernel: [    0.080004] Performance Events: AMD PMU driver.
Feb 18 23:42:37 ubuntu kernel: [    0.080004] ... version:                0
Feb 18 23:42:37 ubuntu kernel: [    0.080004] ... bit width:              48
Feb 18 23:42:37 ubuntu kernel: [    0.080004] ... generic registers:      4
Feb 18 23:42:37 ubuntu kernel: [    0.080004] ... value mask:             0000ffffffffffff
Feb 18 23:42:37 ubuntu kernel: [    0.080004] ... max period:             00007fffffffffff
Feb 18 23:42:37 ubuntu kernel: [    0.080004] ... fixed-purpose events:   0
Feb 18 23:42:37 ubuntu kernel: [    0.080004] ... event mask:             000000000000000f
Feb 18 23:42:37 ubuntu kernel: [    0.080004] NMI watchdog enabled, takes one hw-pmu counter.
Feb 18 23:42:37 ubuntu kernel: [    0.080004] Booting Node   0, Processors  #1 Ok.
Feb 18 23:42:37 ubuntu kernel: [    0.080004] smpboot cpu 1: start_ip = 9a000
Feb 18 23:42:37 ubuntu kernel: [    0.168122] NMI watchdog enabled, takes one hw-pmu counter.
Feb 18 23:42:37 ubuntu kernel: [    0.168201] Brought up 2 CPUs
Feb 18 23:42:37 ubuntu kernel: [    0.168258] Total of 2 processors activated (10448.49 BogoMIPS).
Feb 18 23:42:37 ubuntu kernel: [    0.169148] devtmpfs: initialized
Feb 18 23:42:37 ubuntu kernel: [    0.169288] EVM: security.selinux
Feb 18 23:42:37 ubuntu kernel: [    0.169344] EVM: security.SMACK64
Feb 18 23:42:37 ubuntu kernel: [    0.169400] EVM: security.capability
Feb 18 23:42:37 ubuntu kernel: [    0.169516] PM: Registering ACPI NVS region at 7bee0000 (12288 bytes)
Feb 18 23:42:37 ubuntu kernel: [    0.169516] print_constraints: dummy: 
Feb 18 23:42:37 ubuntu kernel: [    0.169516] RTC time: 23:42:00, date: 02/18/13
Feb 18 23:42:37 ubuntu kernel: [    0.172056] NET: Registered protocol family 16
Feb 18 23:42:37 ubuntu kernel: [    0.172284] Trying to unpack rootfs image as initramfs...
Feb 18 23:42:37 ubuntu kernel: [    0.172284] node 0 link 0: io port [9000, ffff]
Feb 18 23:42:37 ubuntu kernel: [    0.172284] TOM: 0000000080000000 aka 2048M
Feb 18 23:42:37 ubuntu kernel: [    0.172284] node 0 link 0: mmio [a0000, bffff]
Feb 18 23:42:37 ubuntu kernel: [    0.172284] node 0 link 0: mmio [80000000, efffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.172284] node 0 link 0: mmio [f4000000, fe02ffff]
Feb 18 23:42:37 ubuntu kernel: [    0.172284] node 0 link 0: mmio [f0000000, f04fffff]
Feb 18 23:42:37 ubuntu kernel: [    0.172284] bus: [00, 04] on node 0 link 0
Feb 18 23:42:37 ubuntu kernel: [    0.172284] bus: 00 index 0 [io  0x0000-0xffff]
Feb 18 23:42:37 ubuntu kernel: [    0.172284] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Feb 18 23:42:37 ubuntu kernel: [    0.172284] bus: 00 index 2 [mem 0x80000000-0xf3ffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.172284] bus: 00 index 3 [mem 0xf4000000-0xfcffffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.172284] ACPI: bus type pci registered
Feb 18 23:42:37 ubuntu kernel: [    0.172347] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
Feb 18 23:42:37 ubuntu kernel: [    0.172350] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
Feb 18 23:42:37 ubuntu kernel: [    0.176802] PCI: Using configuration type 1 for base access
Feb 18 23:42:37 ubuntu kernel: [    0.188101] bio: create slab <bio-0> at 0
Feb 18 23:42:37 ubuntu kernel: [    0.188101] ACPI: Added _OSI(Module Device)
Feb 18 23:42:37 ubuntu kernel: [    0.188153] ACPI: Added _OSI(Processor Device)
Feb 18 23:42:37 ubuntu kernel: [    0.188209] ACPI: Added _OSI(3.0 _SCP Extensions)
Feb 18 23:42:37 ubuntu kernel: [    0.188266] ACPI: Added _OSI(Processor Aggregator Device)
Feb 18 23:42:37 ubuntu kernel: [    0.189344] ACPI: EC: Look up EC in DSDT
Feb 18 23:42:37 ubuntu kernel: [    0.193312] ACPI: Interpreter enabled
Feb 18 23:42:37 ubuntu kernel: [    0.193370] ACPI: (supports S0 S3 S4 S5)
Feb 18 23:42:37 ubuntu kernel: [    0.193621] ACPI: Using IOAPIC for interrupt routing
Feb 18 23:42:37 ubuntu kernel: [    0.199874] ACPI: No dock devices found.
Feb 18 23:42:37 ubuntu kernel: [    0.199932] HEST: Table not found.
Feb 18 23:42:37 ubuntu kernel: [    0.199990] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Feb 18 23:42:37 ubuntu kernel: [    0.200559] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-04])
Feb 18 23:42:37 ubuntu kernel: [    0.201652] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af] (ignored)
Feb 18 23:42:37 ubuntu kernel: [    0.201655] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7] (ignored)
Feb 18 23:42:37 ubuntu kernel: [    0.201657] pci_root PNP0A08:00: host bridge window [io  0x9000-0xffff] (ignored)
Feb 18 23:42:37 ubuntu kernel: [    0.201659] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03df] (ignored)
Feb 18 23:42:37 ubuntu kernel: [    0.201662] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Feb 18 23:42:37 ubuntu kernel: [    0.201664] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xefffffff] (ignored)
Feb 18 23:42:37 ubuntu kernel: [    0.201666] pci_root PNP0A08:00: host bridge window [mem 0xf4000000-0xfe02ffff] (ignored)
Feb 18 23:42:37 ubuntu kernel: [    0.201669] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff] (ignored)
Feb 18 23:42:37 ubuntu kernel: [    0.201671] pci_root PNP0A08:00: host bridge window [io  0x4700-0x470b] (ignored)
Feb 18 23:42:37 ubuntu kernel: [    0.201674] pci_root PNP0A08:00: host bridge window [io  0x1c00-0x1c80] (ignored)
Feb 18 23:42:37 ubuntu kernel: [    0.201676] pci_root PNP0A08:00: host bridge window [mem 0xfec80000-0xfecbffff] (ignored)
Feb 18 23:42:37 ubuntu kernel: [    0.201699] pci 0000:00:00.0: [10de:03ea] type 0 class 0x000500
Feb 18 23:42:37 ubuntu kernel: [    0.201871] pci 0000:00:01.0: [10de:03e0] type 0 class 0x000601
Feb 18 23:42:37 ubuntu kernel: [    0.201908] pci 0000:00:01.1: [10de:03eb] type 0 class 0x000c05
Feb 18 23:42:37 ubuntu kernel: [    0.201919] pci 0000:00:01.1: reg 10: [io  0xfc00-0xfc3f]
Feb 18 23:42:37 ubuntu kernel: [    0.201933] pci 0000:00:01.1: reg 20: [io  0x1c00-0x1c3f]
Feb 18 23:42:37 ubuntu kernel: [    0.201939] pci 0000:00:01.1: reg 24: [io  0xf400-0xf43f]
Feb 18 23:42:37 ubuntu kernel: [    0.201966] pci 0000:00:01.1: PME# supported from D3hot D3cold
Feb 18 23:42:37 ubuntu kernel: [    0.201972] pci 0000:00:01.1: PME# disabled
Feb 18 23:42:37 ubuntu kernel: [    0.201985] pci 0000:00:01.2: [10de:03f5] type 0 class 0x000500
Feb 18 23:42:37 ubuntu kernel: [    0.202025] pci 0000:00:02.0: [10de:03f1] type 0 class 0x000c03
Feb 18 23:42:37 ubuntu kernel: [    0.202034] pci 0000:00:02.0: reg 10: [mem 0xfe02f000-0xfe02ffff]
Feb 18 23:42:37 ubuntu kernel: [    0.202065] pci 0000:00:02.0: supports D1 D2
Feb 18 23:42:37 ubuntu kernel: [    0.202067] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:42:37 ubuntu kernel: [    0.202070] pci 0000:00:02.0: PME# disabled
Feb 18 23:42:37 ubuntu kernel: [    0.202081] pci 0000:00:02.1: [10de:03f2] type 0 class 0x000c03
Feb 18 23:42:37 ubuntu kernel: [    0.202091] pci 0000:00:02.1: reg 10: [mem 0xfe02e000-0xfe02e0ff]
Feb 18 23:42:37 ubuntu kernel: [    0.202129] pci 0000:00:02.1: supports D1 D2
Feb 18 23:42:37 ubuntu kernel: [    0.202131] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:42:37 ubuntu kernel: [    0.202134] pci 0000:00:02.1: PME# disabled
Feb 18 23:42:37 ubuntu kernel: [    0.202152] pci 0000:00:04.0: [10de:03f3] type 1 class 0x000604
Feb 18 23:42:37 ubuntu kernel: [    0.202191] pci 0000:00:05.0: [10de:03f0] type 0 class 0x000403
Feb 18 23:42:37 ubuntu kernel: [    0.202201] pci 0000:00:05.0: reg 10: [mem 0xfe028000-0xfe02bfff]
Feb 18 23:42:37 ubuntu kernel: [    0.202239] pci 0000:00:05.0: PME# supported from D3hot D3cold
Feb 18 23:42:37 ubuntu kernel: [    0.202242] pci 0000:00:05.0: PME# disabled
Feb 18 23:42:37 ubuntu kernel: [    0.202261] pci 0000:00:06.0: [10de:03ec] type 0 class 0x000101
Feb 18 23:42:37 ubuntu kernel: [    0.202281] pci 0000:00:06.0: reg 20: [io  0xf000-0xf00f]
Feb 18 23:42:37 ubuntu kernel: [    0.202310] pci 0000:00:08.0: [10de:03f6] type 0 class 0x000101
Feb 18 23:42:37 ubuntu kernel: [    0.202318] pci 0000:00:08.0: reg 10: [io  0x09f0-0x09f7]
Feb 18 23:42:37 ubuntu kernel: [    0.202322] pci 0000:00:08.0: reg 14: [io  0x0bf0-0x0bf3]
Feb 18 23:42:37 ubuntu kernel: [    0.202326] pci 0000:00:08.0: reg 18: [io  0x0970-0x0977]
Feb 18 23:42:37 ubuntu kernel: [    0.202330] pci 0000:00:08.0: reg 1c: [io  0x0b70-0x0b73]
Feb 18 23:42:37 ubuntu kernel: [    0.202334] pci 0000:00:08.0: reg 20: [io  0xdc00-0xdc0f]
Feb 18 23:42:37 ubuntu kernel: [    0.202339] pci 0000:00:08.0: reg 24: [mem 0xfe02d000-0xfe02dfff]
Feb 18 23:42:37 ubuntu kernel: [    0.202371] pci 0000:00:09.0: [10de:03e8] type 1 class 0x000604
Feb 18 23:42:37 ubuntu kernel: [    0.202395] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:42:37 ubuntu kernel: [    0.202397] pci 0000:00:09.0: PME# disabled
Feb 18 23:42:37 ubuntu kernel: [    0.202412] pci 0000:00:0b.0: [10de:03e9] type 1 class 0x000604
Feb 18 23:42:37 ubuntu kernel: [    0.202434] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:42:37 ubuntu kernel: [    0.202437] pci 0000:00:0b.0: PME# disabled
Feb 18 23:42:37 ubuntu kernel: [    0.202449] pci 0000:00:0c.0: [10de:03e9] type 1 class 0x000604
Feb 18 23:42:37 ubuntu kernel: [    0.202471] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:42:37 ubuntu kernel: [    0.202474] pci 0000:00:0c.0: PME# disabled
Feb 18 23:42:37 ubuntu kernel: [    0.202484] pci 0000:00:0d.0: [10de:03d1] type 0 class 0x000300
Feb 18 23:42:37 ubuntu kernel: [    0.202490] pci 0000:00:0d.0: reg 10: [mem 0xfc000000-0xfcffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.202496] pci 0000:00:0d.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
Feb 18 23:42:37 ubuntu kernel: [    0.202501] pci 0000:00:0d.0: reg 1c: [mem 0xfb000000-0xfbffffff 64bit]
Feb 18 23:42:37 ubuntu kernel: [    0.202507] pci 0000:00:0d.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Feb 18 23:42:37 ubuntu kernel: [    0.202533] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
Feb 18 23:42:37 ubuntu kernel: [    0.202551] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
Feb 18 23:42:37 ubuntu kernel: [    0.202565] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
Feb 18 23:42:37 ubuntu kernel: [    0.202579] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
Feb 18 23:42:37 ubuntu kernel: [    0.202601] PCI: peer root bus 00 res updated from pci conf
Feb 18 23:42:37 ubuntu kernel: [    0.202632] pci 0000:01:05.0: [1131:7130] type 0 class 0x000480
Feb 18 23:42:37 ubuntu kernel: [    0.202644] pci 0000:01:05.0: reg 10: [mem 0xfdaff000-0xfdaff3ff]
Feb 18 23:42:37 ubuntu kernel: [    0.202694] pci 0000:01:05.0: supports D1 D2
Feb 18 23:42:37 ubuntu kernel: [    0.202711] pci 0000:01:06.0: [10ec:8139] type 0 class 0x000200
Feb 18 23:42:37 ubuntu kernel: [    0.202723] pci 0000:01:06.0: reg 10: [io  0xcc00-0xccff]
Feb 18 23:42:37 ubuntu kernel: [    0.202730] pci 0000:01:06.0: reg 14: [mem 0xfdafe000-0xfdafe0ff]
Feb 18 23:42:37 ubuntu kernel: [    0.202759] pci 0000:01:06.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Feb 18 23:42:37 ubuntu kernel: [    0.202778] pci 0000:01:06.0: supports D1 D2
Feb 18 23:42:37 ubuntu kernel: [    0.202780] pci 0000:01:06.0: PME# supported from D1 D2 D3hot D3cold
Feb 18 23:42:37 ubuntu kernel: [    0.202783] pci 0000:01:06.0: PME# disabled
Feb 18 23:42:37 ubuntu kernel: [    0.202797] pci 0000:01:08.0: [10ec:8167] type 0 class 0x000200
Feb 18 23:42:37 ubuntu kernel: [    0.202809] pci 0000:01:08.0: reg 10: [io  0xc800-0xc8ff]
Feb 18 23:42:37 ubuntu kernel: [    0.202816] pci 0000:01:08.0: reg 14: [mem 0xfdafd000-0xfdafd0ff]
Feb 18 23:42:37 ubuntu kernel: [    0.202844] pci 0000:01:08.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Feb 18 23:42:37 ubuntu kernel: [    0.202862] pci 0000:01:08.0: supports D1 D2
Feb 18 23:42:37 ubuntu kernel: [    0.202864] pci 0000:01:08.0: PME# supported from D1 D2 D3hot D3cold
Feb 18 23:42:37 ubuntu kernel: [    0.202867] pci 0000:01:08.0: PME# disabled
Feb 18 23:42:37 ubuntu kernel: [    0.202892] pci 0000:00:04.0: PCI bridge to [bus 01-01] (subtractive decode)
Feb 18 23:42:37 ubuntu kernel: [    0.202953] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
Feb 18 23:42:37 ubuntu kernel: [    0.202956] pci 0000:00:04.0:   bridge window [mem 0xfda00000-0xfdafffff]
Feb 18 23:42:37 ubuntu kernel: [    0.202959] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
Feb 18 23:42:37 ubuntu kernel: [    0.202961] pci 0000:00:04.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Feb 18 23:42:37 ubuntu kernel: [    0.202964] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Feb 18 23:42:37 ubuntu kernel: [    0.202966] pci 0000:00:04.0:   bridge window [mem 0x80000000-0xf3ffffff] (subtractive decode)
Feb 18 23:42:37 ubuntu kernel: [    0.202969] pci 0000:00:04.0:   bridge window [mem 0xf4000000-0xfcffffffff] (subtractive decode)
Feb 18 23:42:37 ubuntu kernel: [    0.202995] pci 0000:02:00.0: [10de:0393] type 0 class 0x000300
Feb 18 23:42:37 ubuntu kernel: [    0.203002] pci 0000:02:00.0: reg 10: [mem 0xf8000000-0xf8ffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.203010] pci 0000:02:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
Feb 18 23:42:37 ubuntu kernel: [    0.203018] pci 0000:02:00.0: reg 1c: [mem 0xf9000000-0xf9ffffff 64bit]
Feb 18 23:42:37 ubuntu kernel: [    0.203023] pci 0000:02:00.0: reg 24: [io  0xbc00-0xbc7f]
Feb 18 23:42:37 ubuntu kernel: [    0.203029] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Feb 18 23:42:37 ubuntu kernel: [    0.203057] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Feb 18 23:42:37 ubuntu kernel: [    0.203130] pci 0000:00:09.0: PCI bridge to [bus 02-02]
Feb 18 23:42:37 ubuntu kernel: [    0.203188] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
Feb 18 23:42:37 ubuntu kernel: [    0.203191] pci 0000:00:09.0:   bridge window [mem 0xf8000000-0xfaffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.203194] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Feb 18 23:42:37 ubuntu kernel: [    0.203211] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
Feb 18 23:42:37 ubuntu kernel: [    0.203269] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
Feb 18 23:42:37 ubuntu kernel: [    0.203272] pci 0000:00:0b.0:   bridge window [mem 0xfde00000-0xfdefffff]
Feb 18 23:42:37 ubuntu kernel: [    0.203275] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
Feb 18 23:42:37 ubuntu kernel: [    0.203292] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
Feb 18 23:42:37 ubuntu kernel: [    0.203350] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
Feb 18 23:42:37 ubuntu kernel: [    0.203353] pci 0000:00:0c.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
Feb 18 23:42:37 ubuntu kernel: [    0.203356] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Feb 18 23:42:37 ubuntu kernel: [    0.203366] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb 18 23:42:37 ubuntu kernel: [    0.203614] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Feb 18 23:42:37 ubuntu kernel: [    0.203741]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Feb 18 23:42:37 ubuntu kernel: [    0.203800]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Feb 18 23:42:37 ubuntu kernel: [    0.203867] ACPI _OSC control for PCIe not granted, disabling ASPM
Feb 18 23:42:37 ubuntu kernel: [    0.237522] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
Feb 18 23:42:37 ubuntu kernel: [    0.238024] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
Feb 18 23:42:37 ubuntu kernel: [    0.238524] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
Feb 18 23:42:37 ubuntu kernel: [    0.239022] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.239893] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.240473] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.241068] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.242450] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 *10 11 14 15)
Feb 18 23:42:37 ubuntu kernel: [    0.242950] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 *11 14 15)
Feb 18 23:42:37 ubuntu kernel: [    0.243451] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.244340] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
Feb 18 23:42:37 ubuntu kernel: [    0.244839] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.245436] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
Feb 18 23:42:37 ubuntu kernel: [    0.245942] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.246539] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
Feb 18 23:42:37 ubuntu kernel: [    0.247041] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
Feb 18 23:42:37 ubuntu kernel: [    0.247827] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.248432] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Feb 18 23:42:37 ubuntu kernel: [    0.248936] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.249564] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
Feb 18 23:42:37 ubuntu kernel: [    0.249867] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
Feb 18 23:42:37 ubuntu kernel: [    0.250170] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Feb 18 23:42:37 ubuntu kernel: [    0.250473] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.250825] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.251174] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.251801] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.252136] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
Feb 18 23:42:37 ubuntu kernel: [    0.252439] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
Feb 18 23:42:37 ubuntu kernel: [    0.252877] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Feb 18 23:42:37 ubuntu kernel: [    0.253315] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.253800] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.254283] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Feb 18 23:42:37 ubuntu kernel: [    0.254721] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Feb 18 23:42:37 ubuntu kernel: [    0.255159] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Feb 18 23:42:37 ubuntu kernel: [    0.255874] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.256362] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.256846] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Feb 18 23:42:37 ubuntu kernel: [    0.257286] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:42:37 ubuntu kernel: [    0.257829] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=none,locks=none
Feb 18 23:42:37 ubuntu kernel: [    0.257902] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
Feb 18 23:42:37 ubuntu kernel: [    0.257969] vgaarb: loaded
Feb 18 23:42:37 ubuntu kernel: [    0.258024] vgaarb: bridge control possible 0000:02:00.0
Feb 18 23:42:37 ubuntu kernel: [    0.258081] vgaarb: no bridge control possible 0000:00:0d.0
Feb 18 23:42:37 ubuntu kernel: [    0.258260] i2c-core: driver [aat2870] using legacy suspend method
Feb 18 23:42:37 ubuntu kernel: [    0.258318] i2c-core: driver [aat2870] using legacy resume method
Feb 18 23:42:37 ubuntu kernel: [    0.258447] SCSI subsystem initialized
Feb 18 23:42:37 ubuntu kernel: [    0.258583] libata version 3.00 loaded.
Feb 18 23:42:37 ubuntu kernel: [    0.258641] usbcore: registered new interface driver usbfs
Feb 18 23:42:37 ubuntu kernel: [    0.258709] usbcore: registered new interface driver hub
Feb 18 23:42:37 ubuntu kernel: [    0.258798] usbcore: registered new device driver usb
Feb 18 23:42:37 ubuntu kernel: [    0.258950] PCI: Using ACPI for IRQ routing
Feb 18 23:42:37 ubuntu kernel: [    0.260727] PCI: pci_cache_line_size set to 64 bytes
Feb 18 23:42:37 ubuntu kernel: [    0.260791] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
Feb 18 23:42:37 ubuntu kernel: [    0.260794] reserve RAM buffer: 000000007bee0000 - 000000007bffffff 
Feb 18 23:42:37 ubuntu kernel: [    0.260902] NetLabel: Initializing
Feb 18 23:42:37 ubuntu kernel: [    0.260959] NetLabel:  domain hash size = 128
Feb 18 23:42:37 ubuntu kernel: [    0.261015] NetLabel:  protocols = UNLABELED CIPSOv4
Feb 18 23:42:37 ubuntu kernel: [    0.261083] NetLabel:  unlabeled traffic allowed by default
Feb 18 23:42:37 ubuntu kernel: [    0.270312] AppArmor: AppArmor Filesystem Enabled
Feb 18 23:42:37 ubuntu kernel: [    0.270413] pnp: PnP ACPI init
Feb 18 23:42:37 ubuntu kernel: [    0.270487] ACPI: bus type pnp registered
Feb 18 23:42:37 ubuntu kernel: [    0.271121] pnp 00:00: [bus 00-04]
Feb 18 23:42:37 ubuntu kernel: [    0.271128] pnp 00:00: [io  0x0cf8-0x0cff]
Feb 18 23:42:37 ubuntu kernel: [    0.271131] pnp 00:00: [io  0x0000-0x03af window]
Feb 18 23:42:37 ubuntu kernel: [    0.271133] pnp 00:00: [io  0x03e0-0x0cf7 window]
Feb 18 23:42:37 ubuntu kernel: [    0.271135] pnp 00:00: [io  0x9000-0xffff window]
Feb 18 23:42:37 ubuntu kernel: [    0.271137] pnp 00:00: [io  0x03b0-0x03df window]
Feb 18 23:42:37 ubuntu kernel: [    0.271139] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Feb 18 23:42:37 ubuntu kernel: [    0.271141] pnp 00:00: [mem 0x80000000-0xefffffff window]
Feb 18 23:42:37 ubuntu kernel: [    0.271143] pnp 00:00: [mem 0xf4000000-0xfe02ffff window]
Feb 18 23:42:37 ubuntu kernel: [    0.271146] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Feb 18 23:42:37 ubuntu kernel: [    0.271148] pnp 00:00: [io  0x4700-0x470b window]
Feb 18 23:42:37 ubuntu kernel: [    0.271150] pnp 00:00: [io  0x1c00-0x1c80 window]
Feb 18 23:42:37 ubuntu kernel: [    0.271152] pnp 00:00: [mem 0xfec80000-0xfecbffff window]
Feb 18 23:42:37 ubuntu kernel: [    0.271250] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Feb 18 23:42:37 ubuntu kernel: [    0.271356] pnp 00:01: [io  0x1000-0x107f]
Feb 18 23:42:37 ubuntu kernel: [    0.271358] pnp 00:01: [io  0x1080-0x10ff]
Feb 18 23:42:37 ubuntu kernel: [    0.271359] pnp 00:01: [io  0x1400-0x147f]
Feb 18 23:42:37 ubuntu kernel: [    0.271361] pnp 00:01: [io  0x1480-0x14ff]
Feb 18 23:42:37 ubuntu kernel: [    0.271363] pnp 00:01: [io  0x1800-0x187f]
Feb 18 23:42:37 ubuntu kernel: [    0.271365] pnp 00:01: [io  0x1880-0x18ff]
Feb 18 23:42:37 ubuntu kernel: [    0.271367] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Feb 18 23:42:37 ubuntu kernel: [    0.271369] pnp 00:01: [mem 0xfefe0000-0xfefe01ff]
Feb 18 23:42:37 ubuntu kernel: [    0.271371] pnp 00:01: [mem 0xfefe1000-0xfefe10ff]
Feb 18 23:42:37 ubuntu kernel: [    0.271373] pnp 00:01: [mem 0x7c000000-0x7fffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.271439] system 00:01: [io  0x1000-0x107f] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.271778] system 00:01: [io  0x1080-0x10ff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.271836] system 00:01: [io  0x1400-0x147f] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.271895] system 00:01: [io  0x1480-0x14ff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.271953] system 00:01: [io  0x1800-0x187f] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.272028] system 00:01: [io  0x1880-0x18ff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.272087] system 00:01: [mem 0xfefe0000-0xfefe01ff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.272147] system 00:01: [mem 0xfefe1000-0xfefe10ff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.272206] system 00:01: [mem 0x7c000000-0x7fffffff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.272266] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 18 23:42:37 ubuntu kernel: [    0.272844] pnp 00:02: [io  0x0010-0x001f]
Feb 18 23:42:37 ubuntu kernel: [    0.272846] pnp 00:02: [io  0x0022-0x003f]
Feb 18 23:42:37 ubuntu kernel: [    0.272848] pnp 00:02: [io  0x0044-0x004d]
Feb 18 23:42:37 ubuntu kernel: [    0.272850] pnp 00:02: [io  0x0050-0x005e]
Feb 18 23:42:37 ubuntu kernel: [    0.272852] pnp 00:02: [io  0x0062-0x0063]
Feb 18 23:42:37 ubuntu kernel: [    0.272853] pnp 00:02: [io  0x0065-0x006f]
Feb 18 23:42:37 ubuntu kernel: [    0.272855] pnp 00:02: [io  0x0074-0x007f]
Feb 18 23:42:37 ubuntu kernel: [    0.272857] pnp 00:02: [io  0x0091-0x0093]
Feb 18 23:42:37 ubuntu kernel: [    0.272859] pnp 00:02: [io  0x00a2-0x00bf]
Feb 18 23:42:37 ubuntu kernel: [    0.272861] pnp 00:02: [io  0x00e0-0x00ef]
Feb 18 23:42:37 ubuntu kernel: [    0.272862] pnp 00:02: [io  0x04d0-0x04d1]
Feb 18 23:42:37 ubuntu kernel: [    0.272864] pnp 00:02: [io  0x0800-0x087f]
Feb 18 23:42:37 ubuntu kernel: [    0.272866] pnp 00:02: [io  0x0290-0x0297]
Feb 18 23:42:37 ubuntu kernel: [    0.272935] system 00:02: [io  0x04d0-0x04d1] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.272994] system 00:02: [io  0x0800-0x087f] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.273053] system 00:02: [io  0x0290-0x0297] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.273111] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 18 23:42:37 ubuntu kernel: [    0.273123] pnp 00:03: [dma 4]
Feb 18 23:42:37 ubuntu kernel: [    0.273125] pnp 00:03: [io  0x0000-0x000f]
Feb 18 23:42:37 ubuntu kernel: [    0.273126] pnp 00:03: [io  0x0080-0x0090]
Feb 18 23:42:37 ubuntu kernel: [    0.273128] pnp 00:03: [io  0x0094-0x009f]
Feb 18 23:42:37 ubuntu kernel: [    0.273130] pnp 00:03: [io  0x00c0-0x00df]
Feb 18 23:42:37 ubuntu kernel: [    0.273172] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Feb 18 23:42:37 ubuntu kernel: [    0.273215] pnp 00:04: [io  0x0070-0x0073]
Feb 18 23:42:37 ubuntu kernel: [    0.273230] pnp 00:04: [irq 8]
Feb 18 23:42:37 ubuntu kernel: [    0.273273] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Feb 18 23:42:37 ubuntu kernel: [    0.273284] pnp 00:05: [io  0x0061]
Feb 18 23:42:37 ubuntu kernel: [    0.273324] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Feb 18 23:42:37 ubuntu kernel: [    0.273333] pnp 00:06: [io  0x00f0-0x00ff]
Feb 18 23:42:37 ubuntu kernel: [    0.273341] pnp 00:06: [irq 13]
Feb 18 23:42:37 ubuntu kernel: [    0.273389] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Feb 18 23:42:37 ubuntu kernel: [    0.273546] pnp 00:07: [io  0x03f0-0x03f5]
Feb 18 23:42:37 ubuntu kernel: [    0.273548] pnp 00:07: [io  0x03f7]
Feb 18 23:42:37 ubuntu kernel: [    0.273557] pnp 00:07: [irq 6]
Feb 18 23:42:37 ubuntu kernel: [    0.273558] pnp 00:07: [dma 2]
Feb 18 23:42:37 ubuntu kernel: [    0.273613] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
Feb 18 23:42:37 ubuntu kernel: [    0.273827] pnp 00:08: [io  0x03f8-0x03ff]
Feb 18 23:42:37 ubuntu kernel: [    0.273836] pnp 00:08: [irq 4]
Feb 18 23:42:37 ubuntu kernel: [    0.273903] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Feb 18 23:42:37 ubuntu kernel: [    0.274439] pnp 00:09: [io  0x0378-0x037f]
Feb 18 23:42:37 ubuntu kernel: [    0.274441] pnp 00:09: [io  0x0778-0x077b]
Feb 18 23:42:37 ubuntu kernel: [    0.274449] pnp 00:09: [irq 7]
Feb 18 23:42:37 ubuntu kernel: [    0.274451] pnp 00:09: [dma 3]
Feb 18 23:42:37 ubuntu kernel: [    0.274512] pnp 00:09: Plug and Play ACPI device, IDs PNP0401 (active)
Feb 18 23:42:37 ubuntu kernel: [    0.274567] pnp 00:0a: [mem 0xf0000000-0xf3ffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.274626] system 00:0a: [mem 0xf0000000-0xf3ffffff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.274686] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 18 23:42:37 ubuntu kernel: [    0.274769] pnp 00:0b: [mem 0x000f0000-0x000fffff]
Feb 18 23:42:37 ubuntu kernel: [    0.274771] pnp 00:0b: [mem 0xfeff0000-0xfeff00ff]
Feb 18 23:42:37 ubuntu kernel: [    0.274773] pnp 00:0b: [mem 0x7bee0000-0x7befffff]
Feb 18 23:42:37 ubuntu kernel: [    0.274775] pnp 00:0b: [mem 0xffff0000-0xffffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.274780] pnp 00:0b: [mem 0x00000000-0x0009ffff]
Feb 18 23:42:37 ubuntu kernel: [    0.274782] pnp 00:0b: [mem 0x00100000-0x7bedffff]
Feb 18 23:42:37 ubuntu kernel: [    0.274784] pnp 00:0b: [mem 0x7bf00000-0x7fefffff]
Feb 18 23:42:37 ubuntu kernel: [    0.274786] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
Feb 18 23:42:37 ubuntu kernel: [    0.274788] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
Feb 18 23:42:37 ubuntu kernel: [    0.274789] pnp 00:0b: [mem 0xfefff000-0xfeffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.274791] pnp 00:0b: [mem 0xfff80000-0xfff80fff]
Feb 18 23:42:37 ubuntu kernel: [    0.274793] pnp 00:0b: [mem 0xfff90000-0xfffbffff]
Feb 18 23:42:37 ubuntu kernel: [    0.274795] pnp 00:0b: [mem 0xfffed000-0xfffeffff]
Feb 18 23:42:37 ubuntu kernel: [    0.274873] system 00:0b: [mem 0x000f0000-0x000fffff] could not be reserved
Feb 18 23:42:37 ubuntu kernel: [    0.274933] system 00:0b: [mem 0xfeff0000-0xfeff00ff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.274992] system 00:0b: [mem 0x7bee0000-0x7befffff] could not be reserved
Feb 18 23:42:37 ubuntu kernel: [    0.275052] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.275111] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
Feb 18 23:42:37 ubuntu kernel: [    0.275171] system 00:0b: [mem 0x00100000-0x7bedffff] could not be reserved
Feb 18 23:42:37 ubuntu kernel: [    0.275230] system 00:0b: [mem 0x7bf00000-0x7fefffff] could not be reserved
Feb 18 23:42:37 ubuntu kernel: [    0.275290] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
Feb 18 23:42:37 ubuntu kernel: [    0.275350] system 00:0b: [mem 0xfee00000-0xfeefffff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.275409] system 00:0b: [mem 0xfefff000-0xfeffffff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.275468] system 00:0b: [mem 0xfff80000-0xfff80fff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.275803] system 00:0b: [mem 0xfff90000-0xfffbffff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.275862] system 00:0b: [mem 0xfffed000-0xfffeffff] has been reserved
Feb 18 23:42:37 ubuntu kernel: [    0.275922] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
Feb 18 23:42:37 ubuntu kernel: [    0.275930] pnp: PnP ACPI: found 12 devices
Feb 18 23:42:37 ubuntu kernel: [    0.275987] ACPI: ACPI bus type pnp unregistered
Feb 18 23:42:37 ubuntu kernel: [    0.282337] Switching to clocksource acpi_pm
Feb 18 23:42:37 ubuntu kernel: [    0.282542] PCI: max bus depth: 1 pci_try_num: 2
Feb 18 23:42:37 ubuntu kernel: [    0.282562] pci 0000:00:0d.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
Feb 18 23:42:37 ubuntu kernel: [    0.282631] pci 0000:01:06.0: BAR 6: assigned [mem 0xfdf00000-0xfdf1ffff pref]
Feb 18 23:42:37 ubuntu kernel: [    0.282697] pci 0000:01:08.0: BAR 6: assigned [mem 0xfdf20000-0xfdf3ffff pref]
Feb 18 23:42:37 ubuntu kernel: [    0.282765] pci 0000:00:04.0: PCI bridge to [bus 01-01]
Feb 18 23:42:37 ubuntu kernel: [    0.282823] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
Feb 18 23:42:37 ubuntu kernel: [    0.282883] pci 0000:00:04.0:   bridge window [mem 0xfda00000-0xfdafffff]
Feb 18 23:42:37 ubuntu kernel: [    0.282943] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
Feb 18 23:42:37 ubuntu kernel: [    0.283011] pci 0000:02:00.0: BAR 6: assigned [mem 0xfa000000-0xfa01ffff pref]
Feb 18 23:42:37 ubuntu kernel: [    0.283078] pci 0000:00:09.0: PCI bridge to [bus 02-02]
Feb 18 23:42:37 ubuntu kernel: [    0.283136] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
Feb 18 23:42:37 ubuntu kernel: [    0.283195] pci 0000:00:09.0:   bridge window [mem 0xf8000000-0xfaffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283254] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Feb 18 23:42:37 ubuntu kernel: [    0.283322] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
Feb 18 23:42:37 ubuntu kernel: [    0.283380] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
Feb 18 23:42:37 ubuntu kernel: [    0.283439] pci 0000:00:0b.0:   bridge window [mem 0xfde00000-0xfdefffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283499] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
Feb 18 23:42:37 ubuntu kernel: [    0.283845] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
Feb 18 23:42:37 ubuntu kernel: [    0.283904] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci 0000:00:0c.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci 0000:00:04.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci 0000:00:09.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci 0000:00:0b.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci 0000:00:0c.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:00: resource 6 [mem 0x80000000-0xf3ffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:00: resource 7 [mem 0xf4000000-0xfcffffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:01: resource 1 [mem 0xfda00000-0xfdafffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:01: resource 2 [mem 0xfdf00000-0xfdffffff pref]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:01: resource 5 [mem 0x000a0000-0x000bffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:01: resource 6 [mem 0x80000000-0xf3ffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:01: resource 7 [mem 0xf4000000-0xfcffffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:02: resource 1 [mem 0xf8000000-0xfaffffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:02: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:03: resource 1 [mem 0xfde00000-0xfdefffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:03: resource 2 [mem 0xfdd00000-0xfddfffff 64bit pref]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:04: resource 0 [io  0x9000-0x9fff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:04: resource 1 [mem 0xfdc00000-0xfdcfffff]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] pci_bus 0000:04: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
Feb 18 23:42:37 ubuntu kernel: [    0.283973] NET: Registered protocol family 2
Feb 18 23:42:37 ubuntu kernel: [    0.283973] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Feb 18 23:42:37 ubuntu kernel: [    0.283973] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Feb 18 23:42:37 ubuntu kernel: [    0.284967] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Feb 18 23:42:37 ubuntu kernel: [    0.285925] TCP: Hash tables configured (established 262144 bind 65536)
Feb 18 23:42:37 ubuntu kernel: [    0.285985] TCP reno registered
Feb 18 23:42:37 ubuntu kernel: [    0.286052] UDP hash table entries: 1024 (order: 3, 32768 bytes)
Feb 18 23:42:37 ubuntu kernel: [    0.286132] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
Feb 18 23:42:37 ubuntu kernel: [    0.286305] NET: Registered protocol family 1
Feb 18 23:42:37 ubuntu kernel: [    0.286615] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
Feb 18 23:42:37 ubuntu kernel: [    0.286691] pci 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
Feb 18 23:42:37 ubuntu kernel: [    0.356036] pci 0000:00:02.0: PCI INT A disabled
Feb 18 23:42:37 ubuntu kernel: [    0.356233] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
Feb 18 23:42:37 ubuntu kernel: [    0.356299] pci 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
Feb 18 23:42:37 ubuntu kernel: [    0.356376] pci 0000:00:02.1: PCI INT B disabled
Feb 18 23:42:37 ubuntu kernel: [    0.356474] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:42:37 ubuntu kernel: [    0.356576] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:42:37 ubuntu kernel: [    0.356685] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:42:37 ubuntu kernel: [    0.356793] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:42:37 ubuntu kernel: [    0.356904] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:42:37 ubuntu kernel: [    0.357019] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:42:37 ubuntu kernel: [    0.357101] pci 0000:02:00.0: Boot video device
Feb 18 23:42:37 ubuntu kernel: [    0.357104] PCI: CLS 64 bytes, default 64
Feb 18 23:42:37 ubuntu kernel: [    0.359573] audit: initializing netlink socket (disabled)
Feb 18 23:42:37 ubuntu kernel: [    0.359640] type=2000 audit(1361230920.352:1): initialized
Feb 18 23:42:37 ubuntu kernel: [    0.384355] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb 18 23:42:37 ubuntu kernel: [    0.386639] VFS: Disk quotas dquot_6.5.2
Feb 18 23:42:37 ubuntu kernel: [    0.386750] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb 18 23:42:37 ubuntu kernel: [    0.387353] fuse init (API version 7.17)
Feb 18 23:42:37 ubuntu kernel: [    0.387498] msgmni has been set to 3842
Feb 18 23:42:37 ubuntu kernel: [    0.387881] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Feb 18 23:42:37 ubuntu kernel: [    0.387972] io scheduler noop registered
Feb 18 23:42:37 ubuntu kernel: [    0.388058] io scheduler deadline registered
Feb 18 23:42:37 ubuntu kernel: [    0.388147] io scheduler cfq registered (default)
Feb 18 23:42:37 ubuntu kernel: [    0.388352] pcieport 0000:00:09.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.388442] pcieport 0000:00:0b.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.388644] pcieport 0000:00:0c.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.388719] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 18 23:42:37 ubuntu kernel: [    0.388802] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb 18 23:42:37 ubuntu kernel: [    0.389009] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Feb 18 23:42:37 ubuntu kernel: [    0.389080] ACPI: Power Button [PWRB]
Feb 18 23:42:37 ubuntu kernel: [    0.389193] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Feb 18 23:42:37 ubuntu kernel: [    0.389261] ACPI: Power Button [PWRF]
Feb 18 23:42:37 ubuntu kernel: [    0.389369] ACPI: Fan [FAN] (on)
Feb 18 23:42:37 ubuntu kernel: [    0.391920] thermal LNXTHERM:00: registered as thermal_zone0
Feb 18 23:42:37 ubuntu kernel: [    0.391979] ACPI: Thermal Zone [THRM] (40 C)
Feb 18 23:42:37 ubuntu kernel: [    0.392087] ERST: Table is not found!
Feb 18 23:42:37 ubuntu kernel: [    0.392144] GHES: HEST is not enabled!
Feb 18 23:42:37 ubuntu kernel: [    0.392272] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Feb 18 23:42:37 ubuntu kernel: [    0.412684] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 18 23:42:37 ubuntu kernel: [    0.453166] Freeing initrd memory: 13888k freed
Feb 18 23:42:37 ubuntu kernel: [    0.556577] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 18 23:42:37 ubuntu kernel: [    0.556917] Linux agpgart interface v0.103
Feb 18 23:42:37 ubuntu kernel: [    0.558691] brd: module loaded
Feb 18 23:42:37 ubuntu kernel: [    0.559671] loop: module loaded
Feb 18 23:42:37 ubuntu kernel: [    0.560022] pata_acpi 0000:00:06.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.560261] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
Feb 18 23:42:37 ubuntu kernel: [    0.560341] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
Feb 18 23:42:37 ubuntu kernel: [    0.560420] pata_acpi 0000:00:08.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.560427] pata_acpi 0000:00:08.0: PCI INT A disabled
Feb 18 23:42:37 ubuntu kernel: [    0.560899] Fixed MDIO Bus: probed
Feb 18 23:42:37 ubuntu kernel: [    0.560977] tun: Universal TUN/TAP device driver, 1.6
Feb 18 23:42:37 ubuntu kernel: [    0.561034] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Feb 18 23:42:37 ubuntu kernel: [    0.561151] PPP generic driver version 2.4.2
Feb 18 23:42:37 ubuntu kernel: [    0.561329] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb 18 23:42:37 ubuntu kernel: [    0.561413] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
Feb 18 23:42:37 ubuntu kernel: [    0.562282] ehci_hcd 0000:00:02.1: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.562285] ehci_hcd 0000:00:02.1: EHCI Host Controller
Feb 18 23:42:37 ubuntu avahi-daemon[1340]: Found user 'avahi' (UID 106) and group 'avahi' (GID 118).
Feb 18 23:42:37 ubuntu avahi-daemon[1340]: Successfully dropped root privileges.
Feb 18 23:42:37 ubuntu avahi-daemon[1340]: avahi-daemon 0.6.30 starting up.
Feb 18 23:42:37 ubuntu avahi-daemon[1340]: Successfully called chroot().
Feb 18 23:42:37 ubuntu avahi-daemon[1340]: Successfully dropped remaining capabilities.
Feb 18 23:42:37 ubuntu kernel: [    0.562416] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Feb 18 23:42:37 ubuntu kernel: [    0.562503] ehci_hcd 0000:00:02.1: debug port 1
Feb 18 23:42:37 ubuntu kernel: [    0.562565] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Feb 18 23:42:37 ubuntu kernel: [    0.562590] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
Feb 18 23:42:37 ubuntu kernel: [    0.572026] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Feb 18 23:42:37 ubuntu kernel: [    0.572251] hub 1-0:1.0: USB hub found
Feb 18 23:42:37 ubuntu kernel: [    0.572310] hub 1-0:1.0: 8 ports detected
Feb 18 23:42:37 ubuntu kernel: [    0.572466] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb 18 23:42:37 ubuntu kernel: [    0.572552] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
Feb 18 23:42:37 ubuntu kernel: [    0.572627] ohci_hcd 0000:00:02.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.572630] ohci_hcd 0000:00:02.0: OHCI Host Controller
Feb 18 23:42:37 ubuntu kernel: [    0.572745] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Feb 18 23:42:37 ubuntu kernel: [    0.572834] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
Feb 18 23:42:37 ubuntu kernel: [    0.630131] hub 2-0:1.0: USB hub found
Feb 18 23:42:37 ubuntu kernel: [    0.630190] hub 2-0:1.0: 8 ports detected
Feb 18 23:42:37 ubuntu kernel: [    0.630330] uhci_hcd: USB Universal Host Controller Interface driver
Feb 18 23:42:37 ubuntu kernel: [    0.630442] usbcore: registered new interface driver libusual
Feb 18 23:42:37 ubuntu kernel: [    0.630544] i8042: PNP: No PS/2 controller found. Probing ports directly.
Feb 18 23:42:37 ubuntu kernel: [    0.631012] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 18 23:42:37 ubuntu kernel: [    0.631074] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 18 23:42:37 ubuntu kernel: [    0.631292] mousedev: PS/2 mouse device common for all mice
Feb 18 23:42:37 ubuntu kernel: [    0.631514] rtc_cmos 00:04: RTC can wake from S4
Feb 18 23:42:37 ubuntu kernel: [    0.631708] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Feb 18 23:42:37 ubuntu kernel: [    0.631799] rtc0: alarms up to one year, y3k, 242 bytes nvram
Feb 18 23:42:37 ubuntu kernel: [    0.631937] device-mapper: uevent: version 1.0.3
Feb 18 23:42:37 ubuntu kernel: [    0.632095] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Feb 18 23:42:37 ubuntu kernel: [    0.632170] cpuidle: using governor ladder
Feb 18 23:42:37 ubuntu kernel: [    0.632226] cpuidle: using governor menu
Feb 18 23:42:37 ubuntu kernel: [    0.632283] EFI Variables Facility v0.08 2004-May-17
Feb 18 23:42:37 ubuntu kernel: [    0.632577] TCP cubic registered
Feb 18 23:42:37 ubuntu kernel: [    0.632740] NET: Registered protocol family 10
Feb 18 23:42:37 ubuntu kernel: [    0.633278] NET: Registered protocol family 17
Feb 18 23:42:37 ubuntu kernel: [    0.633337] Registering the dns_resolver key type
Feb 18 23:42:37 ubuntu kernel: [    0.633530] PM: Hibernation image not present or could not be loaded.
Feb 18 23:42:37 ubuntu kernel: [    0.633542] registered taskstats version 1
Feb 18 23:42:37 ubuntu kernel: [    0.640270]   Magic number: 1:453:757
Feb 18 23:42:37 ubuntu kernel: [    0.640353] tty ttyS8: hash matches
Feb 18 23:42:37 ubuntu kernel: [    0.640506] rtc_cmos 00:04: setting system clock to 2013-02-18 23:42:00 UTC (1361230920)
Feb 18 23:42:37 ubuntu kernel: [    0.640579] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ (2 cpu cores) (version 2.20.00)
Feb 18 23:42:37 ubuntu kernel: [    0.640685] powernow-k8: fid 0x12 (2600 MHz), vid 0x8
Feb 18 23:42:37 ubuntu kernel: [    0.640743] powernow-k8: fid 0x10 (2400 MHz), vid 0xa
Feb 18 23:42:37 ubuntu kernel: [    0.640800] powernow-k8: fid 0xe (2200 MHz), vid 0xc
Feb 18 23:42:37 ubuntu kernel: [    0.640857] powernow-k8: fid 0xc (2000 MHz), vid 0xe
Feb 18 23:42:37 ubuntu kernel: [    0.640914] powernow-k8: fid 0xa (1800 MHz), vid 0x10
Feb 18 23:42:37 ubuntu kernel: [    0.640971] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
Feb 18 23:42:37 ubuntu kernel: [    0.641105] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 18 23:42:37 ubuntu kernel: [    0.641167] EDD information not available.
Feb 18 23:42:37 ubuntu kernel: [    0.642907] Freeing unused kernel memory: 924k freed
Feb 18 23:42:37 ubuntu kernel: [    0.643379] Write protecting the kernel read-only data: 12288k
Feb 18 23:42:37 ubuntu kernel: [    0.648682] Freeing unused kernel memory: 1604k freed
Feb 18 23:42:37 ubuntu kernel: [    0.654458] Freeing unused kernel memory: 1196k freed
Feb 18 23:42:37 ubuntu kernel: [    0.730830] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Feb 18 23:42:37 ubuntu kernel: [    0.730948] 8139cp 0000:01:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Feb 18 23:42:37 ubuntu kernel: [    0.738166] Floppy drive(s): fd0 is 1.44M
Feb 18 23:42:37 ubuntu kernel: [    0.745601] 8139too: 8139too Fast Ethernet driver 0.9.28
Feb 18 23:42:37 ubuntu kernel: [    0.745901] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
Feb 18 23:42:37 ubuntu kernel: [    0.745976] 8139too 0000:01:06.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
Feb 18 23:42:37 ubuntu kernel: [    0.746810] 8139too 0000:01:06.0: eth0: RealTek RTL8139 at 0xcc00, 6c:fd:b9:22:e6:17, IRQ 17
Feb 18 23:42:37 ubuntu kernel: [    0.754049] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Feb 18 23:42:37 ubuntu kernel: [    0.754331] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Feb 18 23:42:37 ubuntu kernel: [    0.754406] r8169 0000:01:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Feb 18 23:42:37 ubuntu kernel: [    0.754501] r8169 0000:01:08.0: (unregistered net_device): not PCI Express
Feb 18 23:42:37 ubuntu kernel: [    0.755044] r8169 0000:01:08.0: eth1: RTL8169sc/8110sc at 0xffffc90000326000, 00:50:8d:ca:5b:5d, XID 18000000 IRQ 18
Feb 18 23:42:37 ubuntu kernel: [    0.755114] r8169 0000:01:08.0: eth1: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Feb 18 23:42:37 ubuntu kernel: [    0.757950] FDC 0 is a post-1991 82077
Feb 18 23:42:37 ubuntu kernel: [    0.770155] pata_amd 0000:00:06.0: version 0.4.1
Feb 18 23:42:37 ubuntu kernel: [    0.770211] pata_amd 0000:00:06.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.773448] scsi0 : pata_amd
Feb 18 23:42:37 ubuntu kernel: [    0.774186] scsi1 : pata_amd
Feb 18 23:42:37 ubuntu kernel: [    0.774678] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Feb 18 23:42:37 ubuntu kernel: [    0.774740] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Feb 18 23:42:37 ubuntu kernel: [    0.775174] sata_nv 0000:00:08.0: version 3.5
Feb 18 23:42:37 ubuntu kernel: [    0.775189] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
Feb 18 23:42:37 ubuntu kernel: [    0.775307] sata_nv 0000:00:08.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    0.777812] scsi2 : sata_nv
Feb 18 23:42:37 ubuntu kernel: [    0.779457] scsi3 : sata_nv
Feb 18 23:42:37 ubuntu kernel: [    0.779672] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 21
Feb 18 23:42:37 ubuntu kernel: [    0.779732] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 21
Feb 18 23:42:37 ubuntu kernel: [    0.936355] ata1.00: ATAPI: SONY    DVD RW AW-Q170A, 1.72, max UDMA/66
Feb 18 23:42:37 ubuntu kernel: [    0.936425] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
Feb 18 23:42:37 ubuntu kernel: [    0.952261] ata1.00: configured for UDMA/66
Feb 18 23:42:37 ubuntu kernel: [    0.953505] scsi 0:0:0:0: CD-ROM            SONY     DVD RW AW-Q170A  1.72 PQ: 0 ANSI: 5
Feb 18 23:42:37 ubuntu kernel: [    0.954787] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Feb 18 23:42:37 ubuntu kernel: [    0.954847] cdrom: Uniform CD-ROM driver Revision: 3.20
Feb 18 23:42:37 ubuntu kernel: [    0.955068] sr 0:0:0:0: Attached scsi CD-ROM sr0
Feb 18 23:42:37 ubuntu kernel: [    0.955200] sr 0:0:0:0: Attached scsi generic sg0 type 5
Feb 18 23:42:37 ubuntu kernel: [    0.955392] ata2: port disabled--ignoring
Feb 18 23:42:37 ubuntu kernel: [    0.996036] usb 1-2: new high-speed USB device number 3 using ehci_hcd
Feb 18 23:42:37 ubuntu kernel: [    1.129859] hub 1-2:1.0: USB hub found
Feb 18 23:42:37 ubuntu kernel: [    1.130170] hub 1-2:1.0: 4 ports detected
Feb 18 23:42:37 ubuntu kernel: [    1.248043] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 18 23:42:37 ubuntu kernel: [    1.277974] ata3.00: ATA-7: WDC WD2500JS-00SGB0, 20.06C03, max UDMA/133
Feb 18 23:42:37 ubuntu kernel: [    1.278035] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Feb 18 23:42:37 ubuntu kernel: [    1.292260] ata3.00: configured for UDMA/133
Feb 18 23:42:37 ubuntu kernel: [    1.292429] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500JS-00S 20.0 PQ: 0 ANSI: 5
Feb 18 23:42:37 ubuntu kernel: [    1.292645] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Feb 18 23:42:37 ubuntu kernel: [    1.292657] sd 2:0:0:0: Attached scsi generic sg1 type 0
Feb 18 23:42:37 ubuntu kernel: [    1.292892] sd 2:0:0:0: [sda] Write Protect is off
Feb 18 23:42:37 ubuntu kernel: [    1.292952] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 18 23:42:37 ubuntu kernel: [    1.293002] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 18 23:42:37 ubuntu kernel: [    1.302453]  sda: sda1
Feb 18 23:42:37 ubuntu kernel: [    1.302804] sd 2:0:0:0: [sda] Attached SCSI disk
Feb 18 23:42:37 ubuntu kernel: [    1.432021] usb 2-1: new full-speed USB device number 2 using ohci_hcd
Feb 18 23:42:37 ubuntu kernel: [    1.614228] ata4: SATA link down (SStatus 0 SControl 300)
Feb 18 23:42:37 ubuntu kernel: [    1.670315] input: Razer Razer DeathAdder as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input2
Feb 18 23:42:37 ubuntu kernel: [    1.670526] generic-usb 0003:1532:0016.0001: input,hidraw0: USB HID v1.11 Mouse [Razer Razer DeathAdder] on usb-0000:00:02.0-1/input0
Feb 18 23:42:37 ubuntu kernel: [    1.670617] usbcore: registered new interface driver usbhid
Feb 18 23:42:37 ubuntu kernel: [    1.670678] usbhid: USB HID core driver
Feb 18 23:42:37 ubuntu kernel: [    1.732302] usb 1-2.1: new low-speed USB device number 4 using ehci_hcd
Feb 18 23:42:37 ubuntu kernel: [    1.836685] input: LOGITECH G110 G-keys as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.1/1-2.1:1.0/input/input3
Feb 18 23:42:37 ubuntu kernel: [    1.836904] generic-usb 0003:046D:C22B.0002: input,hiddev0,hidraw1: USB HID v1.00 Keypad [LOGITECH G110 G-keys] on usb-0000:00:02.1-2.1/input0
Feb 18 23:42:37 ubuntu kernel: [    1.837040] usbhid 1-2.1:1.1: couldn't find an input interrupt endpoint
Feb 18 23:42:37 ubuntu kernel: [    1.908310] usb 1-2.3: new low-speed USB device number 5 using ehci_hcd
Feb 18 23:42:37 ubuntu kernel: [    2.010091] input: Gaming Keyboard G110 as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/input/input4
Feb 18 23:42:37 ubuntu kernel: [    2.010279] generic-usb 0003:046D:C22A.0003: input,hidraw2: USB HID v1.10 Keyboard [Gaming Keyboard G110] on usb-0000:00:02.1-2.3/input0
Feb 18 23:42:37 ubuntu kernel: [    2.016863] input: Gaming Keyboard G110 as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.1/input/input5
Feb 18 23:42:37 ubuntu kernel: [    2.017070] generic-usb 0003:046D:C22A.0004: input,hiddev0,hidraw3: USB HID v1.10 Device [Gaming Keyboard G110] on usb-0000:00:02.1-2.3/input1
Feb 18 23:42:37 ubuntu kernel: [    2.298950] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
Feb 18 23:42:37 ubuntu kernel: [    5.050129] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
Feb 18 23:42:37 ubuntu kernel: [    5.065128] MCE: In-kernel MCE decoding enabled.
Feb 18 23:42:37 ubuntu kernel: [    5.135874] EDAC MC: Ver: 2.1.0
Feb 18 23:42:37 ubuntu kernel: [    5.147701] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
Feb 18 23:42:37 ubuntu kernel: [    5.147786] i2c i2c-1: nForce2 SMBus adapter at 0xf400
Feb 18 23:42:37 ubuntu kernel: [    5.194674] AMD64 EDAC driver v3.4.0
Feb 18 23:42:37 ubuntu kernel: [    5.194776] EDAC amd64: DRAM ECC disabled.
Feb 18 23:42:37 ubuntu kernel: [    5.194838] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Feb 18 23:42:37 ubuntu kernel: [    5.194840]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Feb 18 23:42:37 ubuntu kernel: [    5.194841]  (Note that use of the override may cause unknown side effects.)
Feb 18 23:42:37 ubuntu kernel: [    5.200389] parport_pc 00:09: reported by Plug and Play ACPI
Feb 18 23:42:37 ubuntu kernel: [    5.200519] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Feb 18 23:42:37 ubuntu kernel: [    5.303207] wmi: Mapper loaded
Feb 18 23:42:37 ubuntu kernel: [    5.387263] ppdev: user-space parallel port driver
Feb 18 23:42:37 ubuntu kernel: [    5.404462] Linux video capture interface: v2.00
Feb 18 23:42:37 ubuntu kernel: [    5.563539] [drm] Initialized drm 1.1.0 20060810
Feb 18 23:42:37 ubuntu kernel: [    5.604847] IR NEC protocol handler initialized
Feb 18 23:42:37 ubuntu kernel: [    5.643558] IR RC5(x) protocol handler initialized
Feb 18 23:42:37 ubuntu kernel: [    5.645344] saa7130/34: v4l2 driver version 0, 2, 17 loaded
Feb 18 23:42:37 ubuntu kernel: [    5.645773] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Feb 18 23:42:37 ubuntu kernel: [    5.645856] saa7134 0000:01:05.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Feb 18 23:42:37 ubuntu kernel: [    5.645930] saa7130[0]: found at 0000:01:05.0, rev: 1, irq: 16, latency: 15, mmio: 0xfdaff000
Feb 18 23:42:37 ubuntu kernel: [    5.646787] saa7134 0000:01:05.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    5.646791] saa7134: Board is currently unknown. You might try to use the card=<nr>
Feb 18 23:42:37 ubuntu kernel: [    5.646792] saa7134: insmod option to specify which board do you have, but this is
Feb 18 23:42:37 ubuntu kernel: [    5.646793] saa7134: somewhat risky, as might damage your card. It is better to ask
Feb 18 23:42:37 ubuntu kernel: [    5.646794] saa7134: for support at linux-media@vger.kernel.org.
Feb 18 23:42:37 ubuntu kernel: [    5.646795] saa7134: The supported cards are:
Feb 18 23:42:37 ubuntu kernel: [    5.647101] saa7134:   card=0 -> UNKNOWN/GENERIC                         
Feb 18 23:42:37 ubuntu kernel: [    5.647212] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
Feb 18 23:42:37 ubuntu kernel: [    5.647415] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
Feb 18 23:42:37 ubuntu kernel: [    5.647618] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
Feb 18 23:42:37 ubuntu kernel: [    5.647821] saa7134:   card=4 -> EMPRESS                                  1131:6752
Feb 18 23:42:37 ubuntu kernel: [    5.647979] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
Feb 18 23:42:37 ubuntu kernel: [    5.648190] saa7134:   card=6 -> Tevion MD 9717                          
Feb 18 23:42:37 ubuntu kernel: [    5.648295] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
Feb 18 23:42:37 ubuntu kernel: [    5.648498] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
Feb 18 23:42:37 ubuntu kernel: [    5.648655] saa7134:   card=9 -> Medion 5044                             
Feb 18 23:42:37 ubuntu kernel: [    5.648760] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
Feb 18 23:42:37 ubuntu kernel: [    5.648864] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
Feb 18 23:42:37 ubuntu kernel: [    5.649021] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
Feb 18 23:42:37 ubuntu kernel: [    5.649225] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
Feb 18 23:42:37 ubuntu kernel: [    5.649329] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
Feb 18 23:42:37 ubuntu kernel: [    5.649486] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
Feb 18 23:42:37 ubuntu kernel: [    5.649643] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
Feb 18 23:42:37 ubuntu kernel: [    5.649892] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
Feb 18 23:42:37 ubuntu kernel: [    5.650049] saa7134:   card=18 -> BMK MPEX No Tuner                       
Feb 18 23:42:37 ubuntu kernel: [    5.650153] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
Feb 18 23:42:37 ubuntu kernel: [    5.650311] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
Feb 18 23:42:37 ubuntu kernel: [    5.650468] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
Feb 18 23:42:37 ubuntu kernel: [    5.650625] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
Feb 18 23:42:37 ubuntu kernel: [    5.650782] saa7134:   card=23 -> BMK MPEX Tuner                          
Feb 18 23:42:37 ubuntu kernel: [    5.650886] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
Feb 18 23:42:37 ubuntu kernel: [    5.651043] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
Feb 18 23:42:37 ubuntu kernel: [    5.651201] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
Feb 18 23:42:37 ubuntu kernel: [    5.651358] saa7134:   card=27 -> Manli MuchTV M-TV002                    
Feb 18 23:42:37 ubuntu kernel: [    5.651462] saa7134:   card=28 -> Manli MuchTV M-TV001                    
Feb 18 23:42:37 ubuntu kernel: [    5.651567] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
Feb 18 23:42:37 ubuntu kernel: [    5.651724] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
Feb 18 23:42:37 ubuntu kernel: [    5.651882] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
Feb 18 23:42:37 ubuntu kernel: [    5.652056] saa7134:   card=32 -> AVACS SmartTV                           
Feb 18 23:42:37 ubuntu kernel: [    5.652161] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
Feb 18 23:42:37 ubuntu kernel: [    5.652318] saa7134:   card=34 -> Noval Prime TV 7133                     
Feb 18 23:42:37 ubuntu kernel: [    5.652422] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
Feb 18 23:42:37 ubuntu kernel: [    5.652579] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
Feb 18 23:42:37 ubuntu kernel: [    5.652736] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
Feb 18 23:42:37 ubuntu kernel: [    5.652840] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
Feb 18 23:42:37 ubuntu kernel: [    5.652997] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
Feb 18 23:42:37 ubuntu kernel: [    5.653246] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
Feb 18 23:42:37 ubuntu kernel: [    5.653403] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
Feb 18 23:42:37 ubuntu kernel: [    5.653560] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
Feb 18 23:42:37 ubuntu kernel: [    5.653664] saa7134:   card=43 -> :Zolid Xpert TV7134                     
Feb 18 23:42:37 ubuntu kernel: [    5.653768] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
Feb 18 23:42:37 ubuntu kernel: [    5.653872] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
Feb 18 23:42:37 ubuntu kernel: [    5.654029] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
Feb 18 23:42:37 ubuntu kernel: [    5.654142] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
Feb 18 23:42:37 ubuntu kernel: [    5.654144] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
Feb 18 23:42:37 ubuntu kernel: [    5.654147] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
Feb 18 23:42:37 ubuntu kernel: [    5.654152] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
Feb 18 23:42:37 ubuntu kernel: [    5.654155] saa7134:   card=51 -> ProVideo PV952                           1540:9524
Feb 18 23:42:37 ubuntu kernel: [    5.654158] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
Feb 18 23:42:37 ubuntu kernel: [    5.654161] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
Feb 18 23:42:37 ubuntu kernel: [    5.654164] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
Feb 18 23:42:37 ubuntu kernel: [    5.654168] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
Feb 18 23:42:37 ubuntu kernel: [    5.654171] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
Feb 18 23:42:37 ubuntu kernel: [    5.654174] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
Feb 18 23:42:37 ubuntu kernel: [    5.654177] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
Feb 18 23:42:37 ubuntu kernel: [    5.654181] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
Feb 18 23:42:37 ubuntu kernel: [    5.654183] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
Feb 18 23:42:37 ubuntu kernel: [    5.654187] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
Feb 18 23:42:37 ubuntu kernel: [    5.654190] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
Feb 18 23:42:37 ubuntu kernel: [    5.654192] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
Feb 18 23:42:37 ubuntu kernel: [    5.654195] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
Feb 18 23:42:37 ubuntu kernel: [    5.654197] saa7134:   card=65 -> V-Stream Studio TV Terminator           
Feb 18 23:42:37 ubuntu kernel: [    5.654200] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
Feb 18 23:42:37 ubuntu kernel: [    5.654202] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
Feb 18 23:42:37 ubuntu kernel: [    5.654205] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
Feb 18 23:42:37 ubuntu kernel: [    5.654208] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
Feb 18 23:42:37 ubuntu kernel: [    5.654211] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
Feb 18 23:42:37 ubuntu kernel: [    5.654214] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
Feb 18 23:42:37 ubuntu kernel: [    5.654217] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
Feb 18 23:42:37 ubuntu kernel: [    5.654220] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
Feb 18 23:42:37 ubuntu kernel: [    5.654222] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
Feb 18 23:42:37 ubuntu kernel: [    5.654225] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
Feb 18 23:42:37 ubuntu kernel: [    5.654228] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
Feb 18 23:42:37 ubuntu kernel: [    5.654231] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
Feb 18 23:42:37 ubuntu kernel: [    5.654234] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
Feb 18 23:42:37 ubuntu kernel: [    5.654237] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
Feb 18 23:42:37 ubuntu kernel: [    5.654239] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
Feb 18 23:42:37 ubuntu kernel: [    5.654242] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
Feb 18 23:42:37 ubuntu kernel: [    5.654245] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
Feb 18 23:42:37 ubuntu kernel: [    5.654248] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
Feb 18 23:42:37 ubuntu kernel: [    5.654251] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
Feb 18 23:42:37 ubuntu kernel: [    5.654254] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
Feb 18 23:42:37 ubuntu kernel: [    5.654257] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
Feb 18 23:42:37 ubuntu kernel: [    5.654260] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
Feb 18 23:42:37 ubuntu kernel: [    5.654263] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
Feb 18 23:42:37 ubuntu kernel: [    5.654266] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
Feb 18 23:42:37 ubuntu kernel: [    5.654269] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
Feb 18 23:42:37 ubuntu kernel: [    5.654272] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
Feb 18 23:42:37 ubuntu kernel: [    5.654275] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
Feb 18 23:42:37 ubuntu kernel: [    5.654278] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
Feb 18 23:42:37 ubuntu kernel: [    5.654281] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
Feb 18 23:42:37 ubuntu kernel: [    5.654285] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
Feb 18 23:42:37 ubuntu kernel: [    5.654288] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
Feb 18 23:42:37 ubuntu kernel: [    5.654291] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
Feb 18 23:42:37 ubuntu kernel: [    5.654294] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
Feb 18 23:42:37 ubuntu kernel: [    5.654297] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
Feb 18 23:42:37 ubuntu kernel: [    5.654300] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
Feb 18 23:42:37 ubuntu kernel: [    5.654303] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
Feb 18 23:42:37 ubuntu kernel: [    5.654306] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
Feb 18 23:42:37 ubuntu kernel: [    5.654309] saa7134:   card=103 -> Compro Videomate DVB-T200A              
Feb 18 23:42:37 ubuntu kernel: [    5.654311] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
Feb 18 23:42:37 ubuntu kernel: [    5.654316] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
Feb 18 23:42:37 ubuntu kernel: [    5.654319] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
Feb 18 23:42:37 ubuntu kernel: [    5.654323] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
Feb 18 23:42:37 ubuntu kernel: [    5.654325] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
Feb 18 23:42:37 ubuntu kernel: [    5.654328] saa7134:   card=109 -> Philips Tiger - S Reference design      
Feb 18 23:42:37 ubuntu kernel: [    5.654331] saa7134:   card=110 -> Avermedia M102                           1461:f31e
Feb 18 23:42:37 ubuntu kernel: [    5.654334] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
Feb 18 23:42:37 ubuntu kernel: [    5.654337] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
Feb 18 23:42:37 ubuntu kernel: [    5.654339] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
Feb 18 23:42:37 ubuntu kernel: [    5.654342] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
Feb 18 23:42:37 ubuntu kernel: [    5.654345] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
Feb 18 23:42:37 ubuntu kernel: [    5.654348] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
Feb 18 23:42:37 ubuntu kernel: [    5.654351] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
Feb 18 23:42:37 ubuntu kernel: [    5.654354] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
Feb 18 23:42:37 ubuntu kernel: [    5.654357] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
Feb 18 23:42:37 ubuntu kernel: [    5.654359] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
Feb 18 23:42:37 ubuntu kernel: [    5.654362] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
Feb 18 23:42:37 ubuntu kernel: [    5.654365] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
Feb 18 23:42:37 ubuntu kernel: [    5.654368] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
Feb 18 23:42:37 ubuntu kernel: [    5.654371] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
Feb 18 23:42:37 ubuntu kernel: [    5.654374] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
Feb 18 23:42:37 ubuntu kernel: [    5.654376] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
Feb 18 23:42:37 ubuntu kernel: [    5.654379] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
Feb 18 23:42:37 ubuntu kernel: [    5.654383] saa7134:   card=128 -> Beholder BeholdTV Columbus TV/FM         0000:5201
Feb 18 23:42:37 ubuntu kernel: [    5.654385] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
Feb 18 23:42:37 ubuntu kernel: [    5.654391] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
Feb 18 23:42:37 ubuntu kernel: [    5.654394] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
Feb 18 23:42:37 ubuntu kernel: [    5.654397] saa7134:   card=132 -> Genius TVGO AM11MCE                     
Feb 18 23:42:37 ubuntu kernel: [    5.654399] saa7134:   card=133 -> NXP Snake DVB-S reference design        
Feb 18 23:42:37 ubuntu kernel: [    5.654402] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
Feb 18 23:42:37 ubuntu kernel: [    5.654405] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
Feb 18 23:42:37 ubuntu kernel: [    5.654408] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
Feb 18 23:42:37 ubuntu kernel: [    5.654411] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
Feb 18 23:42:37 ubuntu kernel: [    5.654413] saa7134:   card=138 -> Avermedia M115                           1461:a836
Feb 18 23:42:37 ubuntu kernel: [    5.654416] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
Feb 18 23:42:37 ubuntu kernel: [    5.654419] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
Feb 18 23:42:37 ubuntu kernel: [    5.654422] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
Feb 18 23:42:37 ubuntu kernel: [    5.654425] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
Feb 18 23:42:37 ubuntu kernel: [    5.654428] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
Feb 18 23:42:37 ubuntu kernel: [    5.654430] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
Feb 18 23:42:37 ubuntu kernel: [    5.654433] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
Feb 18 23:42:37 ubuntu kernel: [    5.654437] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
Feb 18 23:42:37 ubuntu kernel: [    5.654439] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
Feb 18 23:42:37 ubuntu kernel: [    5.654442] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
Feb 18 23:42:37 ubuntu kernel: [    5.654445] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
Feb 18 23:42:37 ubuntu kernel: [    5.654447] saa7134:   card=150 -> Zogis Real Angel 220                    
Feb 18 23:42:37 ubuntu kernel: [    5.654450] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
Feb 18 23:42:37 ubuntu kernel: [    5.654453] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
Feb 18 23:42:37 ubuntu kernel: [    5.654456] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
Feb 18 23:42:37 ubuntu kernel: [    5.654459] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
Feb 18 23:42:37 ubuntu kernel: [    5.654462] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
Feb 18 23:42:37 ubuntu kernel: [    5.654465] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
Feb 18 23:42:37 ubuntu kernel: [    5.654469] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
Feb 18 23:42:37 ubuntu kernel: [    5.654471] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
Feb 18 23:42:37 ubuntu kernel: [    5.654474] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
Feb 18 23:42:37 ubuntu kernel: [    5.654477] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
Feb 18 23:42:37 ubuntu kernel: [    5.654480] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
Feb 18 23:42:37 ubuntu kernel: [    5.654483] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
Feb 18 23:42:37 ubuntu kernel: [    5.654486] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
Feb 18 23:42:37 ubuntu kernel: [    5.654489] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
Feb 18 23:42:37 ubuntu kernel: [    5.654491] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
Feb 18 23:42:37 ubuntu kernel: [    5.654494] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
Feb 18 23:42:37 ubuntu kernel: [    5.654497] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
Feb 18 23:42:37 ubuntu kernel: [    5.654500] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
Feb 18 23:42:37 ubuntu kernel: [    5.654503] saa7134:   card=169 -> Compro VideoMate S350/S300               185b:c900
Feb 18 23:42:37 ubuntu kernel: [    5.654506] saa7134:   card=170 -> AverMedia AverTV Studio 505              1461:a115
Feb 18 23:42:37 ubuntu kernel: [    5.654509] saa7134:   card=171 -> Beholder BeholdTV X7                     5ace:7595
Feb 18 23:42:37 ubuntu kernel: [    5.654511] saa7134:   card=172 -> RoverMedia TV Link Pro FM                19d1:0138
Feb 18 23:42:37 ubuntu kernel: [    5.654514] saa7134:   card=173 -> Zolid Hybrid TV Tuner PCI                1131:2004
Feb 18 23:42:37 ubuntu kernel: [    5.654517] saa7134:   card=174 -> Asus Europa Hybrid OEM                   1043:4847
Feb 18 23:42:37 ubuntu kernel: [    5.654520] saa7134:   card=175 -> Leadtek Winfast DTV1000S                 107d:6655
Feb 18 23:42:37 ubuntu kernel: [    5.654523] saa7134:   card=176 -> Beholder BeholdTV 505 RDS                0000:5051
Feb 18 23:42:37 ubuntu kernel: [    5.654526] saa7134:   card=177 -> Hawell HW-404M7                         
Feb 18 23:42:37 ubuntu kernel: [    5.654528] saa7134:   card=178 -> Beholder BeholdTV H7                     5ace:7190
Feb 18 23:42:37 ubuntu kernel: [    5.654531] saa7134:   card=179 -> Beholder BeholdTV A7                     5ace:7090
Feb 18 23:42:37 ubuntu kernel: [    5.654534] saa7134:   card=180 -> Avermedia PCI M733A                      1461:4155 1461:4255
Feb 18 23:42:37 ubuntu kernel: [    5.654537] saa7134:   card=181 -> TechoTrend TT-budget T-3000              13c2:2804
Feb 18 23:42:37 ubuntu kernel: [    5.654540] saa7134:   card=182 -> Kworld PCI SBTVD/ISDB-T Full-Seg Hybrid  17de:b136
Feb 18 23:42:37 ubuntu kernel: [    5.654543] saa7134:   card=183 -> Compro VideoMate Vista M1F               185b:c900
Feb 18 23:42:37 ubuntu kernel: [    5.654546] saa7134:   card=184 -> Encore ENLTV-FM 3                        1a7f:2108
Feb 18 23:42:37 ubuntu kernel: [    5.654549] saa7134:   card=185 -> MagicPro ProHDTV Pro2 DMB-TH/Hybrid      17de:d136
Feb 18 23:42:37 ubuntu kernel: [    5.654551] saa7134:   card=186 -> Beholder BeholdTV 501                    5ace:5010
Feb 18 23:42:37 ubuntu kernel: [    5.654554] saa7134:   card=187 -> Beholder BeholdTV 503 FM                 5ace:5030
Feb 18 23:42:37 ubuntu kernel: [    5.654558] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
Feb 18 23:42:37 ubuntu kernel: [    5.658733] saa7130[0]: board init: gpio is 804000
Feb 18 23:42:37 ubuntu kernel: [    5.694242] IR RC6 protocol handler initialized
Feb 18 23:42:37 ubuntu kernel: [    5.751648] IR JVC protocol handler initialized
Feb 18 23:42:37 ubuntu kernel: [    5.760230] saa7130[0]: Huh, no eeprom present (err=-5)?
Feb 18 23:42:37 ubuntu kernel: [    5.760374] saa7130[0]: registered device video0 [v4l2]
Feb 18 23:42:37 ubuntu kernel: [    5.760474] saa7130[0]: registered device vbi0
Feb 18 23:42:37 ubuntu kernel: [    5.799725] IR Sony protocol handler initialized
Feb 18 23:42:37 ubuntu kernel: [    5.812955] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 18 23:42:37 ubuntu kernel: [    5.812964] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 18 23:42:37 ubuntu kernel: [    5.845949] saa7134 ALSA driver for DMA sound loaded
Feb 18 23:42:37 ubuntu kernel: [    5.845954] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio
Feb 18 23:42:37 ubuntu kernel: [    5.847342] IR MCE Keyboard/mouse protocol handler initialized
Feb 18 23:42:37 ubuntu kernel: [    5.886747] lirc_dev: IR Remote Control driver registered, major 250 
Feb 18 23:42:37 ubuntu kernel: [    5.942747] IR LIRC bridge handler initialized
Feb 18 23:42:37 ubuntu kernel: [    5.975449] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
Feb 18 23:42:37 ubuntu kernel: [    5.975471] snd_hda_intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
Feb 18 23:42:37 ubuntu kernel: [    5.975474] hda_intel: Disabling MSI
Feb 18 23:42:37 ubuntu kernel: [    5.975516] snd_hda_intel 0000:00:05.0: setting latency timer to 64
Feb 18 23:42:37 ubuntu kernel: [    6.612031] hda_codec: ALC883: BIOS auto-probing.
Feb 18 23:42:37 ubuntu kernel: [    7.820104] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input6
Feb 18 23:42:37 ubuntu kernel: [    7.820206] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input7
Feb 18 23:42:37 ubuntu kernel: [    7.820272] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
Feb 18 23:42:37 ubuntu kernel: [    7.820334] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
Feb 18 23:42:37 ubuntu kernel: [    7.820397] input: HDA NVidia Line-Out Side as /devices/pci0000:00/0000:00:05.0/sound/card0/input10
Feb 18 23:42:37 ubuntu kernel: [    7.820461] input: HDA NVidia Line-Out CLFE as /devices/pci0000:00/0000:00:05.0/sound/card0/input11
Feb 18 23:42:37 ubuntu kernel: [    7.820522] input: HDA NVidia Line-Out Surround as /devices/pci0000:00/0000:00:05.0/sound/card0/input12
Feb 18 23:42:37 ubuntu kernel: [    7.820580] input: HDA NVidia Line-Out Front as /devices/pci0000:00/0000:00:05.0/sound/card0/input13
Feb 18 23:42:37 ubuntu kernel: [   20.912708] lp0: using parport0 (interrupt-driven).
Feb 18 23:42:37 ubuntu kernel: [   21.003654] AMD64 EDAC driver v3.4.0
Feb 18 23:42:37 ubuntu kernel: [   21.003700] EDAC amd64: DRAM ECC disabled.
Feb 18 23:42:37 ubuntu kernel: [   21.003710] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Feb 18 23:42:37 ubuntu kernel: [   21.003712]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Feb 18 23:42:37 ubuntu kernel: [   21.003713]  (Note that use of the override may cause unknown side effects.)
Feb 18 23:42:37 ubuntu kernel: [   22.105270] init: udev-fallback-graphics main process (1063) terminated with status 1
Feb 18 23:42:37 ubuntu kernel: [   36.951622] Adding 262140k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262140k 
Feb 18 23:42:37 ubuntu kernel: [   36.964139] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
Feb 18 23:42:37 ubuntu kernel: [   37.091102] init: failsafe main process (1259) killed by TERM signal
Feb 18 23:42:37 ubuntu kernel: [   37.129819] init: friendly-recovery post-stop process (836) terminated with status 1
Feb 18 23:42:37 ubuntu kernel: [   37.147400] Bluetooth: Core ver 2.16
Feb 18 23:42:37 ubuntu kernel: [   37.147434] NET: Registered protocol family 31
Feb 18 23:42:37 ubuntu kernel: [   37.147436] Bluetooth: HCI device and connection manager initialized
Feb 18 23:42:37 ubuntu kernel: [   37.147440] Bluetooth: HCI socket layer initialized
Feb 18 23:42:37 ubuntu bluetoothd[1297]: Failed to init gatt_example plugin
Feb 18 23:42:37 ubuntu kernel: [   37.147442] Bluetooth: L2CAP socket layer initialized
Feb 18 23:42:37 ubuntu kernel: [   37.147448] Bluetooth: SCO socket layer initialized
Feb 18 23:42:37 ubuntu kernel: [   37.163071] type=1400 audit(1361259757.018:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1320 comm="apparmor_parser"
Feb 18 23:42:37 ubuntu kernel: [   37.163622] type=1400 audit(1361259757.018:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1320 comm="apparmor_parser"
Feb 18 23:42:37 ubuntu kernel: [   37.186644] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 18 23:42:37 ubuntu kernel: [   37.186649] Bluetooth: BNEP filters: protocol multicast
Feb 18 23:42:37 ubuntu kernel: [   37.196449] Bluetooth: RFCOMM TTY layer initialized
Feb 18 23:42:37 ubuntu kernel: [   37.196456] Bluetooth: RFCOMM socket layer initialized
Feb 18 23:42:37 ubuntu kernel: [   37.196458] Bluetooth: RFCOMM ver 1.11
Feb 18 23:42:37 ubuntu avahi-daemon[1340]: Loading service file /services/udisks.service.
Feb 18 23:42:37 ubuntu avahi-daemon[1340]: Network interface enumeration completed.
Feb 18 23:42:37 ubuntu avahi-daemon[1340]: Registering HINFO record with values 'X86_64'/'LINUX'.
Feb 18 23:42:37 ubuntu avahi-daemon[1340]: Server startup complete. Host name is ubuntu.local. Local service cookie is 3484911257.
Feb 18 23:42:37 ubuntu avahi-daemon[1340]: Service "ubuntu" (/services/udisks.service) successfully established.
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> NetworkManager (version 0.9.4.0) is starting...
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> DNS: loaded plugin dnsmasq
Feb 18 23:42:37 ubuntu kernel: [   37.223083] type=1400 audit(1361259757.078:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1356 comm="apparmor_parser"
Feb 18 23:42:37 ubuntu dbus[1271]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Feb 18 23:42:37 ubuntu kernel: [   37.224489] type=1400 audit(1361259757.082:5): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=1357 comm="apparmor_parser"
Feb 18 23:42:37 ubuntu kernel: [   37.224955] type=1400 audit(1361259757.082:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1357 comm="apparmor_parser"
Feb 18 23:42:37 ubuntu kernel: [   37.225210] type=1400 audit(1361259757.082:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=1357 comm="apparmor_parser"
Feb 18 23:42:37 ubuntu kernel: [   37.232255] type=1400 audit(1361259757.090:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1364 comm="apparmor_parser"
Feb 18 23:42:37 ubuntu kernel: [   37.232965] type=1400 audit(1361259757.090:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1364 comm="apparmor_parser"
Feb 18 23:42:37 ubuntu polkitd[1363]: started daemon version 0.104 using authority implementation `local' version `0.104'
Feb 18 23:42:37 ubuntu kernel: [   37.243190] type=1400 audit(1361259757.098:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1360 comm="apparmor_parser"
Feb 18 23:42:37 ubuntu dbus[1271]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Feb 18 23:42:37 ubuntu kernel: [   37.246573] type=1400 audit(1361259757.102:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1368 comm="apparmor_parser"
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    SCPlugin-Ifupdown: init!
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    SCPlugin-Ifupdown: update_system_hostname
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    SCPluginIfupdown: management mode: unmanaged
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:06.0/net/eth1, iface: eth1)
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:06.0/net/eth1, iface: eth1): no ifupdown configuration found.
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0/net/eth0, iface: eth0)
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0/net/eth0, iface: eth0): no ifupdown configuration found.
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    SCPlugin-Ifupdown: end _init.
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    Ifupdown: get unmanaged devices count: 0
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    SCPlugin-Ifupdown: (9707680) ... get_connections.
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    SCPlugin-Ifupdown: (9707680) ... get_connections (managed=false): return empty list.
Feb 18 23:42:37 ubuntu NetworkManager[1358]:    Ifupdown: get unmanaged devices count: 0
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> modem-manager is now available
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> monitoring kernel firmware directory '/lib/firmware'.
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> WiFi enabled by radio killswitch; enabled by state file
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> WWAN enabled by radio killswitch; enabled by state file
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> WiMAX enabled by radio killswitch; enabled by state file
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> Networking is enabled by state file
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <warn> failed to allocate link cache: (-10) Operation not supported
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth1): carrier is OFF
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth1): new Ethernet device (driver: '8139too' ifindex: 2)
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth1): now managed
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth1): bringing up device.
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth1): preparing device.
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth1): deactivating device (reason 'managed') [2]
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:04.0/0000:01:06.0/net/eth1
Feb 18 23:42:37 ubuntu kernel: [   37.256844] 8139too 0000:01:06.0: eth1: link down
Feb 18 23:42:37 ubuntu kernel: [   37.257247] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 18 23:42:37 ubuntu kernel: [   37.257854] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <warn> failed to allocate link cache: (-10) Operation not supported
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth0): carrier is OFF
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 3)
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth0): now managed
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth0): bringing up device.
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth0): preparing device.
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> (eth0): deactivating device (reason 'managed') [2]
Feb 18 23:42:37 ubuntu NetworkManager[1358]: <info> Added default wired connection 'Wired connection 2' for /sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0/net/eth0
Feb 18 23:42:37 ubuntu kernel: [   37.277706] r8169 0000:01:08.0: eth0: link down
Feb 18 23:42:37 ubuntu kernel: [   37.277712] r8169 0000:01:08.0: eth0: link down
Feb 18 23:42:37 ubuntu kernel: [   37.278087] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 18 23:42:37 ubuntu kernel: [   37.278432] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 18 23:42:37 ubuntu anacron[1431]: Anacron 2.3 started on 2013-02-18
Feb 18 23:42:37 ubuntu acpid: starting up with proc fs
Feb 18 23:42:37 ubuntu cron[1405]: (CRON) INFO (pidfile fd = 3)
Feb 18 23:42:37 ubuntu acpid: 35 rules loaded
Feb 18 23:42:37 ubuntu acpid: waiting for events: event logging is off
Feb 18 23:42:37 ubuntu anacron[1431]: Will run job `cron.weekly' in 10 min.
Feb 18 23:42:37 ubuntu anacron[1431]: Will run job `cron.monthly' in 15 min.
Feb 18 23:42:37 ubuntu anacron[1431]: Jobs will be executed sequentially
Feb 18 23:42:37 ubuntu cron[1443]: (CRON) STARTUP (fork ok)
Feb 18 23:42:37 ubuntu cron[1443]: (CRON) INFO (Running @reboot jobs)
Feb 18 23:42:37 ubuntu acpid: client connected from 1474[0:0]
Feb 18 23:42:37 ubuntu acpid: 1 client rule loaded
Feb 18 23:42:37 ubuntu udev-configure-printer: add /devices/pnp0/00:09/printer/lp0
Feb 18 23:42:37 ubuntu udev-configure-printer: Failed to get parent
Feb 18 23:42:37 ubuntu udev-configure-printer: add /module/lp
Feb 18 23:42:37 ubuntu udev-configure-printer: Failed to get parent
Feb 18 23:42:38 ubuntu dbus[1271]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Feb 18 23:42:38 ubuntu dbus[1271]: [system] Successfully activated service 'org.freedesktop.Accounts'
Feb 18 23:42:38 ubuntu accounts-daemon[1615]: started daemon version 0.6.15
Feb 18 23:42:38 ubuntu dbus[1271]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Feb 18 23:42:38 ubuntu dbus[1271]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Feb 18 23:42:38 ubuntu dbus[1271]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Feb 18 23:42:38 ubuntu dbus[1271]: [system] Successfully activated service 'org.freedesktop.UPower'
Feb 18 23:42:38 ubuntu kernel: [   38.871456] r8169 0000:01:08.0: eth0: link up
Feb 18 23:42:38 ubuntu kernel: [   38.871782] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> (eth0): carrier now ON (device state 20)
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Auto-activating connection 'Wired connection 2'.
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) starting connection 'Wired connection 2'
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb 18 23:42:38 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> dhclient started with pid 1781
Feb 18 23:42:38 ubuntu dhclient: Copyright 2004-2011 Internet Systems Consortium.
Feb 18 23:42:38 ubuntu dhclient: All rights reserved.
Feb 18 23:42:38 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Feb 18 23:42:38 ubuntu dhclient: 
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Beginning IP6 addrconf.
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Feb 18 23:42:38 ubuntu dhclient: Listening on LPF/eth0/00:50:8d:ca:5b:5d
Feb 18 23:42:38 ubuntu dhclient: Sending on   LPF/eth0/00:50:8d:ca:5b:5d
Feb 18 23:42:38 ubuntu dhclient: Sending on   Socket/fallback
Feb 18 23:42:38 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Feb 18 23:42:38 ubuntu dhclient: DHCPREQUEST of 192.168.1.13 on eth0 to 255.255.255.255 port 67
Feb 18 23:42:38 ubuntu dhclient: DHCPOFFER of 192.168.1.13 from 192.168.1.1
Feb 18 23:42:38 ubuntu dhclient: DHCPACK of 192.168.1.13 from 192.168.1.1
Feb 18 23:42:38 ubuntu dhclient: bound to 192.168.1.13 -- renewal in 33628 seconds.
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> (eth0): DHCPv4 state changed preinit -> bound
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info>   address 192.168.1.13
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info>   prefix 24 (255.255.255.0)
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info>   gateway 192.168.1.1
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info>   nameserver '192.168.1.1'
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Feb 18 23:42:38 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Feb 18 23:42:38 ubuntu avahi-daemon[1340]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.13.
Feb 18 23:42:38 ubuntu avahi-daemon[1340]: New relevant interface eth0.IPv4 for mDNS.
Feb 18 23:42:38 ubuntu avahi-daemon[1340]: Registering new address record for 192.168.1.13 on eth0.IPv4.
Feb 18 23:42:39 ubuntu NetworkManager[1358]: <info> DNS: starting dnsmasq...
Feb 18 23:42:39 ubuntu NetworkManager[1358]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Feb 18 23:42:39 ubuntu dnsmasq[1853]: started, version 2.59 cache disabled
Feb 18 23:42:39 ubuntu dnsmasq[1853]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Feb 18 23:42:39 ubuntu dnsmasq[1853]: using nameserver 192.168.1.1#53
Feb 18 23:42:39 ubuntu NetworkManager[1358]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Feb 18 23:42:40 ubuntu avahi-daemon[1340]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::250:8dff:feca:5b5d.
Feb 18 23:42:40 ubuntu avahi-daemon[1340]: New relevant interface eth0.IPv6 for mDNS.
Feb 18 23:42:40 ubuntu avahi-daemon[1340]: Registering new address record for fe80::250:8dff:feca:5b5d on eth0.*.
Feb 18 23:42:40 ubuntu NetworkManager[1358]: <info> Policy set 'Wired connection 2' (eth0) as default for IPv4 routing and DNS.
Feb 18 23:42:40 ubuntu NetworkManager[1358]: <info> Activation (eth0) successful, device activated.
Feb 18 23:42:40 ubuntu NetworkManager[1358]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Feb 18 23:42:40 ubuntu dbus[1271]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb 18 23:42:40 ubuntu dbus[1271]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb 18 23:42:48 ubuntu ntpdate[1915]: adjust time server 91.189.94.4 offset 0.314916 sec
Feb 18 23:42:49 ubuntu kernel: [   49.168028] eth0: no IPv6 routers present
Feb 18 23:42:54 ubuntu kernel: Kernel logging (proc) stopped.
Feb 18 23:42:54 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1319" x-info="http://www.rsyslog.com"] exiting on signal 15.
Feb 18 23:45:14 ubuntu kernel: imklog 5.8.6, log source = /proc/kmsg started.
Feb 18 23:45:14 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1940" x-info="http://www.rsyslog.com"] start
Feb 18 23:45:14 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Feb 18 23:45:14 ubuntu rsyslogd: rsyslogd's userid changed to 101
Feb 18 23:45:14 ubuntu rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Feb 18 23:45:14 ubuntu avahi-daemon[1946]: Found user 'avahi' (UID 106) and group 'avahi' (GID 118).
Feb 18 23:45:14 ubuntu avahi-daemon[1946]: Successfully dropped root privileges.
Feb 18 23:45:14 ubuntu avahi-daemon[1946]: avahi-daemon 0.6.30 starting up.
Feb 18 23:45:14 ubuntu avahi-daemon[1946]: Successfully called chroot().
Feb 18 23:45:14 ubuntu avahi-daemon[1946]: Successfully dropped remaining capabilities.
Feb 18 23:45:14 ubuntu avahi-daemon[1946]: Loading service file /services/udisks.service.
Feb 18 23:45:14 ubuntu avahi-daemon[1946]: Network interface enumeration completed.
Feb 18 23:45:14 ubuntu avahi-daemon[1946]: Registering HINFO record with values 'X86_64'/'LINUX'.
Feb 18 23:45:14 ubuntu avahi-daemon[1946]: Server startup complete. Host name is ubuntu.local. Local service cookie is 113588315.
Feb 18 23:45:14 ubuntu avahi-daemon[1946]: Service "ubuntu" (/services/udisks.service) successfully established.
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Linux version 3.2.0-37-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 (Ubuntu 3.2.0-37.58-generic 3.2.35)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic root=UUID=5884B5E584B5C632 loop=/ubuntu/disks/root.disk ro recovery nomodeset
Feb 18 23:45:14 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Feb 18 23:45:14 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007bee0000 (usable)
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007bee0000 - 000000007bee3000 (ACPI NVS)
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007bee3000 - 000000007bef0000 (ACPI data)
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007bef0000 - 000000007bf00000 (reserved)
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  BIOS-e820: 000000007c000000 - 0000000080000000 (reserved)
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Feb 18 23:45:14 ubuntu kernel: [    0.000000] DMI 2.2 present.
Feb 18 23:45:14 ubuntu kernel: [    0.000000] DMI:   NF-M2S/NF-M2S, BIOS 6.00 PG 11/08/2006
Feb 18 23:45:14 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] No AGP bridge found
Feb 18 23:45:14 ubuntu kernel: [    0.000000] last_pfn = 0x7bee0 max_arch_pfn = 0x400000000
Feb 18 23:45:14 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Feb 18 23:45:14 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   C0000-C7FFF write-protect
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   C8000-FFFFF uncachable
Feb 18 23:45:14 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   0 base 0000000000 mask FFC0000000 write-back
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   1 base 0040000000 mask FFE0000000 write-back
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   2 base 0060000000 mask FFF0000000 write-back
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   3 base 0070000000 mask FFF8000000 write-back
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   4 base 0078000000 mask FFFC000000 write-back
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   5 base 007BF00000 mask FFFFF00000 uncachable
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   6 disabled
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   7 disabled
Feb 18 23:45:14 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb 18 23:45:14 ubuntu kernel: [    0.000000] original variable MTRRs
Feb 18 23:45:14 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 1GB, type WB
Feb 18 23:45:14 ubuntu kernel: [    0.000000] reg 1, base: 1GB, range: 512MB, type WB
Feb 18 23:45:14 ubuntu kernel: [    0.000000] reg 2, base: 1536MB, range: 256MB, type WB
Feb 18 23:45:14 ubuntu kernel: [    0.000000] reg 3, base: 1792MB, range: 128MB, type WB
Feb 18 23:45:14 ubuntu kernel: [    0.000000] reg 4, base: 1920MB, range: 64MB, type WB
Feb 18 23:45:14 ubuntu kernel: [    0.000000] reg 5, base: 1983MB, range: 1MB, type UC
Feb 18 23:45:14 ubuntu kernel: [    0.000000] total RAM covered: 1983M
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Found optimal setting for mtrr clean up
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 3      lose cover RAM: 0G
Feb 18 23:45:14 ubuntu kernel: [    0.000000] New variable MTRRs
Feb 18 23:45:14 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Feb 18 23:45:14 ubuntu kernel: [    0.000000] reg 1, base: 1983MB, range: 1MB, type UC
Feb 18 23:45:14 ubuntu kernel: [    0.000000] reg 2, base: 1984MB, range: 64MB, type UC
Feb 18 23:45:14 ubuntu kernel: [    0.000000] found SMP MP-table at [ffff8800000f3a00] f3a00
Feb 18 23:45:14 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 20000000
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
Feb 18 23:45:14 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000007bee0000
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  0000000000 - 007be00000 page 2M
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  007be00000 - 007bee0000 page 4k
Feb 18 23:45:14 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 7bee0000 @ 1fffc000-20000000
Feb 18 23:45:14 ubuntu kernel: [    0.000000] RAMDISK: 364d0000 - 37260000
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: RSDP 00000000000f7a10 00014 (v00 Nvidia)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: RSDT 000000007bee3040 00038 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: FACP 000000007bee30c0 00074 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: DSDT 000000007bee3180 06378 (v01 NVIDIA AWRDACPI 00001000 MSFT 0100000E)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: FACS 000000007bee0000 00040
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: SSDT 000000007bee9600 0028A (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: _HPT 000000007bee9900 00038 (v01 Nvidia AWRDACPI 42302E31 AWRD 00000098)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: MCFG 000000007bee9980 0003C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: APIC 000000007bee9540 0007C (v01 Nvidia AWRDACPI 42302E31 AWRD 00000000)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Feb 18 23:45:14 ubuntu kernel: [    0.000000] No NUMA configuration found
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Faking a node at 0000000000000000-000000007bee0000
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000007bee0000
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   NODE_DATA [000000007bedb000 - 000000007bedffff]
Feb 18 23:45:14 ubuntu kernel: [    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff880079600000-ffff88007b5fffff] on node 0
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Zone PFN ranges:
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   Normal   empty
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Feb 18 23:45:14 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Feb 18 23:45:14 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Feb 18 23:45:14 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0007bee0
Feb 18 23:45:14 ubuntu kernel: [    0.000000] On node 0 totalpages: 507503
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   DMA zone: 5 pages reserved
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   DMA zone: 3914 pages, LIFO batch:0
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   DMA32 zone: 7868 pages used for memmap
Feb 18 23:45:14 ubuntu kernel: [    0.000000]   DMA32 zone: 495652 pages, LIFO batch:31
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Feb 18 23:45:14 ubuntu kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb 18 23:45:14 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 0 dfl dfl)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: BIOS IRQ0 override ignored.
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: IRQ14 used by override.
Feb 18 23:45:14 ubuntu kernel: [    0.000000] ACPI: IRQ15 used by override.
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 18 23:45:14 ubuntu kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Feb 18 23:45:14 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Feb 18 23:45:14 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb 18 23:45:14 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Feb 18 23:45:14 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:70000000)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Feb 18 23:45:14 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
Feb 18 23:45:14 ubuntu kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007bc00000 s83136 r8192 d23360 u1048576
Feb 18 23:45:14 ubuntu kernel: [    0.000000] pcpu-alloc: s83136 r8192 d23360 u1048576 alloc=1*2097152
Feb 18 23:45:14 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 499566
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Policy zone: DMA32
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic root=UUID=5884B5E584B5C632 loop=/ubuntu/disks/root.disk ro recovery nomodeset
Feb 18 23:45:14 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Checking aperture...
Feb 18 23:45:14 ubuntu kernel: [    0.000000] No AGP bridge found
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Node 0: aperture @ e596000000 size 32 MB
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Memory: 1967300k/2030464k available (6569k kernel code, 452k absent, 62712k reserved, 6634k data, 924k init)
Feb 18 23:45:14 ubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Feb 18 23:45:14 ubuntu kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Feb 18 23:45:14 ubuntu kernel: [    0.000000] NR_IRQS:16640 nr_irqs:512 16
Feb 18 23:45:14 ubuntu kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Feb 18 23:45:14 ubuntu kernel: [    0.000000] console [tty0] enabled
Feb 18 23:45:14 ubuntu kernel: [    0.000000] allocated 16777216 bytes of page_cgroup
Feb 18 23:45:14 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Detected 2612.038 MHz processor.
Feb 18 23:45:14 ubuntu kernel: [    0.000000] Marking TSC unstable due to TSCs unsynchronized
Feb 18 23:45:14 ubuntu kernel: [    0.008061] Calibrating delay loop (skipped), value calculated using timer frequency.. 5224.07 BogoMIPS (lpj=10448152)
Feb 18 23:45:14 ubuntu kernel: [    0.008178] pid_max: default: 32768 minimum: 301
Feb 18 23:45:14 ubuntu kernel: [    0.008259] Security Framework initialized
Feb 18 23:45:14 ubuntu kernel: [    0.008333] AppArmor: AppArmor initialized
Feb 18 23:45:14 ubuntu kernel: [    0.008390] Yama: becoming mindful.
Feb 18 23:45:14 ubuntu kernel: [    0.008663] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Feb 18 23:45:14 ubuntu kernel: [    0.009798] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Feb 18 23:45:14 ubuntu kernel: [    0.012574] Mount-cache hash table entries: 256
Feb 18 23:45:14 ubuntu kernel: [    0.012782] Initializing cgroup subsys cpuacct
Feb 18 23:45:14 ubuntu kernel: [    0.012844] Initializing cgroup subsys memory
Feb 18 23:45:14 ubuntu kernel: [    0.012909] Initializing cgroup subsys devices
Feb 18 23:45:14 ubuntu kernel: [    0.012966] Initializing cgroup subsys freezer
Feb 18 23:45:14 ubuntu kernel: [    0.013023] Initializing cgroup subsys blkio
Feb 18 23:45:14 ubuntu kernel: [    0.013085] Initializing cgroup subsys perf_event
Feb 18 23:45:14 ubuntu kernel: [    0.013172] tseg: 007bf00000
Feb 18 23:45:14 ubuntu kernel: [    0.013174] CPU: Physical Processor ID: 0
Feb 18 23:45:14 ubuntu kernel: [    0.013231] CPU: Processor Core ID: 0
Feb 18 23:45:14 ubuntu kernel: [    0.013288] mce: CPU supports 5 MCE banks
Feb 18 23:45:14 ubuntu kernel: [    0.013354] using AMD E400 aware idle routine
Feb 18 23:45:14 ubuntu kernel: [    0.014922] ACPI: Core revision 20110623
Feb 18 23:45:14 ubuntu kernel: [    0.020012] ftrace: allocating 27033 entries in 107 pages
Feb 18 23:45:14 ubuntu kernel: [    0.028516] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Feb 18 23:45:14 ubuntu kernel: [    0.068276] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02
Feb 18 23:45:14 ubuntu kernel: [    0.072003] Performance Events: AMD PMU driver.
Feb 18 23:45:14 ubuntu kernel: [    0.072003] ... version:                0
Feb 18 23:45:14 ubuntu kernel: [    0.072003] ... bit width:              48
Feb 18 23:45:14 ubuntu kernel: [    0.072003] ... generic registers:      4
Feb 18 23:45:14 ubuntu kernel: [    0.072003] ... value mask:             0000ffffffffffff
Feb 18 23:45:14 ubuntu kernel: [    0.072003] ... max period:             00007fffffffffff
Feb 18 23:45:14 ubuntu kernel: [    0.072003] ... fixed-purpose events:   0
Feb 18 23:45:14 ubuntu kernel: [    0.072003] ... event mask:             000000000000000f
Feb 18 23:45:14 ubuntu kernel: [    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
Feb 18 23:45:14 ubuntu kernel: [    0.072003] Booting Node   0, Processors  #1 Ok.
Feb 18 23:45:14 ubuntu kernel: [    0.072003] smpboot cpu 1: start_ip = 9a000
Feb 18 23:45:14 ubuntu kernel: [    0.156067] NMI watchdog enabled, takes one hw-pmu counter.
Feb 18 23:45:14 ubuntu kernel: [    0.156145] Brought up 2 CPUs
Feb 18 23:45:14 ubuntu kernel: [    0.156202] Total of 2 processors activated (10448.48 BogoMIPS).
Feb 18 23:45:14 ubuntu kernel: [    0.157094] devtmpfs: initialized
Feb 18 23:45:14 ubuntu kernel: [    0.157287] EVM: security.selinux
Feb 18 23:45:14 ubuntu kernel: [    0.157343] EVM: security.SMACK64
Feb 18 23:45:14 ubuntu kernel: [    0.157399] EVM: security.capability
Feb 18 23:45:14 ubuntu kernel: [    0.157515] PM: Registering ACPI NVS region at 7bee0000 (12288 bytes)
Feb 18 23:45:14 ubuntu kernel: [    0.157515] print_constraints: dummy: 
Feb 18 23:45:14 ubuntu kernel: [    0.157515] RTC time: 23:43:51, date: 02/18/13
Feb 18 23:45:14 ubuntu kernel: [    0.157515] NET: Registered protocol family 16
Feb 18 23:45:14 ubuntu kernel: [    0.160039] Trying to unpack rootfs image as initramfs...
Feb 18 23:45:14 ubuntu kernel: [    0.157515] node 0 link 0: io port [9000, ffff]
Feb 18 23:45:14 ubuntu kernel: [    0.157515] TOM: 0000000080000000 aka 2048M
Feb 18 23:45:14 ubuntu kernel: [    0.157515] node 0 link 0: mmio [a0000, bffff]
Feb 18 23:45:14 ubuntu kernel: [    0.160018] node 0 link 0: mmio [80000000, efffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.160020] node 0 link 0: mmio [f4000000, fe02ffff]
Feb 18 23:45:14 ubuntu kernel: [    0.160022] node 0 link 0: mmio [f0000000, f04fffff]
Feb 18 23:45:14 ubuntu kernel: [    0.160024] bus: [00, 04] on node 0 link 0
Feb 18 23:45:14 ubuntu kernel: [    0.160026] bus: 00 index 0 [io  0x0000-0xffff]
Feb 18 23:45:14 ubuntu kernel: [    0.160028] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Feb 18 23:45:14 ubuntu kernel: [    0.160030] bus: 00 index 2 [mem 0x80000000-0xf3ffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.160031] bus: 00 index 3 [mem 0xf4000000-0xfcffffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.160041] ACPI: bus type pci registered
Feb 18 23:45:14 ubuntu kernel: [    0.160112] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
Feb 18 23:45:14 ubuntu kernel: [    0.160115] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
Feb 18 23:45:14 ubuntu kernel: [    0.164247] PCI: Using configuration type 1 for base access
Feb 18 23:45:14 ubuntu kernel: [    0.172143] bio: create slab <bio-0> at 0
Feb 18 23:45:14 ubuntu kernel: [    0.172212] ACPI: Added _OSI(Module Device)
Feb 18 23:45:14 ubuntu kernel: [    0.172269] ACPI: Added _OSI(Processor Device)
Feb 18 23:45:14 ubuntu kernel: [    0.172326] ACPI: Added _OSI(3.0 _SCP Extensions)
Feb 18 23:45:14 ubuntu kernel: [    0.172383] ACPI: Added _OSI(Processor Aggregator Device)
Feb 18 23:45:14 ubuntu kernel: [    0.173463] ACPI: EC: Look up EC in DSDT
Feb 18 23:45:14 ubuntu kernel: [    0.177179] ACPI: Interpreter enabled
Feb 18 23:45:14 ubuntu kernel: [    0.177237] ACPI: (supports S0 S3 S4 S5)
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> NetworkManager (version 0.9.4.0) is starting...
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> DNS: loaded plugin dnsmasq
Feb 18 23:45:14 ubuntu kernel: [    0.177488] ACPI: Using IOAPIC for interrupt routing
Feb 18 23:45:14 ubuntu kernel: [    0.183401] ACPI: No dock devices found.
Feb 18 23:45:14 ubuntu kernel: [    0.183459] HEST: Table not found.
Feb 18 23:45:14 ubuntu kernel: [    0.183518] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Feb 18 23:45:14 ubuntu kernel: [    0.184130] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-04])
Feb 18 23:45:14 ubuntu kernel: [    0.185225] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af] (ignored)
Feb 18 23:45:14 ubuntu kernel: [    0.185228] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7] (ignored)
Feb 18 23:45:14 ubuntu kernel: [    0.185230] pci_root PNP0A08:00: host bridge window [io  0x9000-0xffff] (ignored)
Feb 18 23:45:14 ubuntu kernel: [    0.185232] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03df] (ignored)
Feb 18 23:45:14 ubuntu kernel: [    0.185235] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Feb 18 23:45:14 ubuntu kernel: [    0.185237] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xefffffff] (ignored)
Feb 18 23:45:14 ubuntu kernel: [    0.185239] pci_root PNP0A08:00: host bridge window [mem 0xf4000000-0xfe02ffff] (ignored)
Feb 18 23:45:14 ubuntu kernel: [    0.185242] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff] (ignored)
Feb 18 23:45:14 ubuntu kernel: [    0.185244] pci_root PNP0A08:00: host bridge window [io  0x4700-0x470b] (ignored)
Feb 18 23:45:14 ubuntu kernel: [    0.185246] pci_root PNP0A08:00: host bridge window [io  0x1c00-0x1c80] (ignored)
Feb 18 23:45:14 ubuntu kernel: [    0.185249] pci_root PNP0A08:00: host bridge window [mem 0xfec80000-0xfecbffff] (ignored)
Feb 18 23:45:14 ubuntu kernel: [    0.185272] pci 0000:00:00.0: [10de:03ea] type 0 class 0x000500
Feb 18 23:45:14 ubuntu kernel: [    0.185443] pci 0000:00:01.0: [10de:03e0] type 0 class 0x000601
Feb 18 23:45:14 ubuntu kernel: [    0.185481] pci 0000:00:01.1: [10de:03eb] type 0 class 0x000c05
Feb 18 23:45:14 ubuntu kernel: [    0.185491] pci 0000:00:01.1: reg 10: [io  0xfc00-0xfc3f]
Feb 18 23:45:14 ubuntu kernel: [    0.185506] pci 0000:00:01.1: reg 20: [io  0x1c00-0x1c3f]
Feb 18 23:45:14 ubuntu kernel: [    0.185511] pci 0000:00:01.1: reg 24: [io  0xf400-0xf43f]
Feb 18 23:45:14 ubuntu kernel: [    0.185538] pci 0000:00:01.1: PME# supported from D3hot D3cold
Feb 18 23:45:14 ubuntu kernel: [    0.185544] pci 0000:00:01.1: PME# disabled
Feb 18 23:45:14 ubuntu kernel: [    0.185558] pci 0000:00:01.2: [10de:03f5] type 0 class 0x000500
Feb 18 23:45:14 ubuntu kernel: [    0.185598] pci 0000:00:02.0: [10de:03f1] type 0 class 0x000c03
Feb 18 23:45:14 ubuntu kernel: [    0.185607] pci 0000:00:02.0: reg 10: [mem 0xfe02f000-0xfe02ffff]
Feb 18 23:45:14 ubuntu kernel: [    0.185638] pci 0000:00:02.0: supports D1 D2
Feb 18 23:45:14 ubuntu kernel: [    0.185640] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:45:14 ubuntu kernel: [    0.185643] pci 0000:00:02.0: PME# disabled
Feb 18 23:45:14 ubuntu kernel: [    0.185655] pci 0000:00:02.1: [10de:03f2] type 0 class 0x000c03
Feb 18 23:45:14 ubuntu kernel: [    0.185664] pci 0000:00:02.1: reg 10: [mem 0xfe02e000-0xfe02e0ff]
Feb 18 23:45:14 ubuntu kernel: [    0.185702] pci 0000:00:02.1: supports D1 D2
Feb 18 23:45:14 ubuntu kernel: [    0.185704] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:45:14 ubuntu kernel: [    0.185707] pci 0000:00:02.1: PME# disabled
Feb 18 23:45:14 ubuntu kernel: [    0.185725] pci 0000:00:04.0: [10de:03f3] type 1 class 0x000604
Feb 18 23:45:14 ubuntu kernel: [    0.185764] pci 0000:00:05.0: [10de:03f0] type 0 class 0x000403
Feb 18 23:45:14 ubuntu kernel: [    0.185774] pci 0000:00:05.0: reg 10: [mem 0xfe028000-0xfe02bfff]
Feb 18 23:45:14 ubuntu kernel: [    0.185813] pci 0000:00:05.0: PME# supported from D3hot D3cold
Feb 18 23:45:14 ubuntu kernel: [    0.185816] pci 0000:00:05.0: PME# disabled
Feb 18 23:45:14 ubuntu kernel: [    0.185834] pci 0000:00:06.0: [10de:03ec] type 0 class 0x000101
Feb 18 23:45:14 ubuntu kernel: [    0.185854] pci 0000:00:06.0: reg 20: [io  0xf000-0xf00f]
Feb 18 23:45:14 ubuntu kernel: [    0.185884] pci 0000:00:08.0: [10de:03f6] type 0 class 0x000101
Feb 18 23:45:14 ubuntu kernel: [    0.185891] pci 0000:00:08.0: reg 10: [io  0x09f0-0x09f7]
Feb 18 23:45:14 ubuntu kernel: [    0.185896] pci 0000:00:08.0: reg 14: [io  0x0bf0-0x0bf3]
Feb 18 23:45:14 ubuntu kernel: [    0.185900] pci 0000:00:08.0: reg 18: [io  0x0970-0x0977]
Feb 18 23:45:14 ubuntu kernel: [    0.185904] pci 0000:00:08.0: reg 1c: [io  0x0b70-0x0b73]
Feb 18 23:45:14 ubuntu kernel: [    0.185908] pci 0000:00:08.0: reg 20: [io  0xdc00-0xdc0f]
Feb 18 23:45:14 ubuntu kernel: [    0.185913] pci 0000:00:08.0: reg 24: [mem 0xfe02d000-0xfe02dfff]
Feb 18 23:45:14 ubuntu kernel: [    0.185945] pci 0000:00:09.0: [10de:03e8] type 1 class 0x000604
Feb 18 23:45:14 ubuntu kernel: [    0.185969] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:45:14 ubuntu kernel: [    0.185971] pci 0000:00:09.0: PME# disabled
Feb 18 23:45:14 ubuntu kernel: [    0.185986] pci 0000:00:0b.0: [10de:03e9] type 1 class 0x000604
Feb 18 23:45:14 ubuntu kernel: [    0.186008] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:45:14 ubuntu kernel: [    0.186010] pci 0000:00:0b.0: PME# disabled
Feb 18 23:45:14 ubuntu kernel: [    0.186023] pci 0000:00:0c.0: [10de:03e9] type 1 class 0x000604
Feb 18 23:45:14 ubuntu kernel: [    0.186045] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 18 23:45:14 ubuntu kernel: [    0.186048] pci 0000:00:0c.0: PME# disabled
Feb 18 23:45:14 ubuntu kernel: [    0.186058] pci 0000:00:0d.0: [10de:03d1] type 0 class 0x000300
Feb 18 23:45:14 ubuntu kernel: [    0.186065] pci 0000:00:0d.0: reg 10: [mem 0xfc000000-0xfcffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.186070] pci 0000:00:0d.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
Feb 18 23:45:14 ubuntu kernel: [    0.186075] pci 0000:00:0d.0: reg 1c: [mem 0xfb000000-0xfbffffff 64bit]
Feb 18 23:45:14 ubuntu kernel: [    0.186081] pci 0000:00:0d.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Feb 18 23:45:14 ubuntu kernel: [    0.186107] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
Feb 18 23:45:14 ubuntu kernel: [    0.186125] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
Feb 18 23:45:14 ubuntu kernel: [    0.186140] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
Feb 18 23:45:14 ubuntu kernel: [    0.186155] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
Feb 18 23:45:14 ubuntu kernel: [    0.186177] PCI: peer root bus 00 res updated from pci conf
Feb 18 23:45:14 ubuntu kernel: [    0.186208] pci 0000:01:05.0: [1131:7130] type 0 class 0x000480
Feb 18 23:45:14 ubuntu kernel: [    0.186220] pci 0000:01:05.0: reg 10: [mem 0xfdaff000-0xfdaff3ff]
Feb 18 23:45:14 ubuntu kernel: [    0.186270] pci 0000:01:05.0: supports D1 D2
Feb 18 23:45:14 ubuntu kernel: [    0.186286] pci 0000:01:06.0: [10ec:8139] type 0 class 0x000200
Feb 18 23:45:14 ubuntu kernel: [    0.186298] pci 0000:01:06.0: reg 10: [io  0xcc00-0xccff]
Feb 18 23:45:14 ubuntu kernel: [    0.186306] pci 0000:01:06.0: reg 14: [mem 0xfdafe000-0xfdafe0ff]
Feb 18 23:45:14 ubuntu kernel: [    0.186334] pci 0000:01:06.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Feb 18 23:45:14 ubuntu kernel: [    0.186353] pci 0000:01:06.0: supports D1 D2
Feb 18 23:45:14 ubuntu kernel: [    0.186355] pci 0000:01:06.0: PME# supported from D1 D2 D3hot D3cold
Feb 18 23:45:14 ubuntu kernel: [    0.186359] pci 0000:01:06.0: PME# disabled
Feb 18 23:45:14 ubuntu kernel: [    0.186372] pci 0000:01:08.0: [10ec:8167] type 0 class 0x000200
Feb 18 23:45:14 ubuntu kernel: [    0.186384] pci 0000:01:08.0: reg 10: [io  0xc800-0xc8ff]
Feb 18 23:45:14 ubuntu kernel: [    0.186391] pci 0000:01:08.0: reg 14: [mem 0xfdafd000-0xfdafd0ff]
Feb 18 23:45:14 ubuntu kernel: [    0.186419] pci 0000:01:08.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Feb 18 23:45:14 ubuntu kernel: [    0.186437] pci 0000:01:08.0: supports D1 D2
Feb 18 23:45:14 ubuntu kernel: [    0.186439] pci 0000:01:08.0: PME# supported from D1 D2 D3hot D3cold
Feb 18 23:45:14 ubuntu kernel: [    0.186442] pci 0000:01:08.0: PME# disabled
Feb 18 23:45:14 ubuntu kernel: [    0.186467] pci 0000:00:04.0: PCI bridge to [bus 01-01] (subtractive decode)
Feb 18 23:45:14 ubuntu kernel: [    0.186528] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
Feb 18 23:45:14 ubuntu kernel: [    0.186531] pci 0000:00:04.0:   bridge window [mem 0xfda00000-0xfdafffff]
Feb 18 23:45:14 ubuntu kernel: [    0.186534] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
Feb 18 23:45:14 ubuntu kernel: [    0.186537] pci 0000:00:04.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Feb 18 23:45:14 ubuntu kernel: [    0.186539] pci 0000:00:04.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Feb 18 23:45:14 ubuntu kernel: [    0.186542] pci 0000:00:04.0:   bridge window [mem 0x80000000-0xf3ffffff] (subtractive decode)
Feb 18 23:45:14 ubuntu kernel: [    0.186544] pci 0000:00:04.0:   bridge window [mem 0xf4000000-0xfcffffffff] (subtractive decode)
Feb 18 23:45:14 ubuntu kernel: [    0.186570] pci 0000:02:00.0: [10de:0393] type 0 class 0x000300
Feb 18 23:45:14 ubuntu kernel: [    0.186577] pci 0000:02:00.0: reg 10: [mem 0xf8000000-0xf8ffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.186585] pci 0000:02:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
Feb 18 23:45:14 ubuntu dbus[1899]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Feb 18 23:45:14 ubuntu kernel: [    0.186593] pci 0000:02:00.0: reg 1c: [mem 0xf9000000-0xf9ffffff 64bit]
Feb 18 23:45:14 ubuntu kernel: [    0.186599] pci 0000:02:00.0: reg 24: [io  0xbc00-0xbc7f]
Feb 18 23:45:14 ubuntu kernel: [    0.186605] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Feb 18 23:45:14 ubuntu kernel: [    0.186632] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Feb 18 23:45:14 ubuntu kernel: [    0.186705] pci 0000:00:09.0: PCI bridge to [bus 02-02]
Feb 18 23:45:14 ubuntu kernel: [    0.186764] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
Feb 18 23:45:14 ubuntu kernel: [    0.186766] pci 0000:00:09.0:   bridge window [mem 0xf8000000-0xfaffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.186770] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Feb 18 23:45:14 ubuntu kernel: [    0.186786] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
Feb 18 23:45:14 ubuntu kernel: [    0.186845] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
Feb 18 23:45:14 ubuntu kernel: [    0.186847] pci 0000:00:0b.0:   bridge window [mem 0xfde00000-0xfdefffff]
Feb 18 23:45:14 ubuntu kernel: [    0.186851] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
Feb 18 23:45:14 ubuntu kernel: [    0.186867] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
Feb 18 23:45:14 ubuntu kernel: [    0.186925] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
Feb 18 23:45:14 ubuntu kernel: [    0.186928] pci 0000:00:0c.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
Feb 18 23:45:14 ubuntu kernel: [    0.186932] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Feb 18 23:45:14 ubuntu kernel: [    0.186941] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb 18 23:45:14 ubuntu kernel: [    0.187045] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Feb 18 23:45:14 ubuntu kernel: [    0.187170]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Feb 18 23:45:14 ubuntu kernel: [    0.187229]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Feb 18 23:45:14 ubuntu kernel: [    0.187296] ACPI _OSC control for PCIe not granted, disabling ASPM
Feb 18 23:45:14 ubuntu kernel: [    0.219087] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
Feb 18 23:45:14 ubuntu kernel: [    0.219589] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
Feb 18 23:45:14 ubuntu kernel: [    0.220057] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
Feb 18 23:45:14 ubuntu kernel: [    0.220556] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.221152] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.221747] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.222343] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.222940] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 *10 11 14 15)
Feb 18 23:45:14 ubuntu kernel: [    0.223440] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 *11 14 15)
Feb 18 23:45:14 ubuntu kernel: [    0.224055] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.224652] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
Feb 18 23:45:14 ubuntu kernel: [    0.225150] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.225747] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
Feb 18 23:45:14 ubuntu kernel: [    0.226254] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.226851] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
Feb 18 23:45:14 ubuntu kernel: [    0.228055] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
Feb 18 23:45:14 ubuntu kernel: [    0.228565] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.229163] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Feb 18 23:45:14 ubuntu kernel: [    0.229666] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.230293] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
Feb 18 23:45:14 ubuntu kernel: [    0.230595] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
Feb 18 23:45:14 ubuntu kernel: [    0.230897] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Feb 18 23:45:14 ubuntu kernel: [    0.231200] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.231550] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.231899] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.232272] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.232620] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
Feb 18 23:45:14 ubuntu kernel: [    0.232923] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
Feb 18 23:45:14 ubuntu kernel: [    0.233361] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Feb 18 23:45:14 ubuntu kernel: [    0.233799] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.234283] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.234767] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Feb 18 23:45:14 ubuntu kernel: [    0.235205] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Feb 18 23:45:14 ubuntu kernel: [    0.235643] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Feb 18 23:45:14 ubuntu kernel: [    0.236082] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.236566] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.237050] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Feb 18 23:45:14 ubuntu kernel: [    0.237491] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
Feb 18 23:45:14 ubuntu kernel: [    0.238036] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=none,locks=none
Feb 18 23:45:14 ubuntu kernel: [    0.238109] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
Feb 18 23:45:14 ubuntu kernel: [    0.238176] vgaarb: loaded
Feb 18 23:45:14 ubuntu kernel: [    0.238231] vgaarb: bridge control possible 0000:02:00.0
Feb 18 23:45:14 ubuntu kernel: [    0.238288] vgaarb: no bridge control possible 0000:00:0d.0
Feb 18 23:45:14 ubuntu kernel: [    0.238467] i2c-core: driver [aat2870] using legacy suspend method
Feb 18 23:45:14 ubuntu kernel: [    0.238525] i2c-core: driver [aat2870] using legacy resume method
Feb 18 23:45:14 ubuntu kernel: [    0.238658] SCSI subsystem initialized
Feb 18 23:45:14 ubuntu kernel: [    0.238786] libata version 3.00 loaded.
Feb 18 23:45:14 ubuntu kernel: [    0.238853] usbcore: registered new interface driver usbfs
Feb 18 23:45:14 ubuntu kernel: [    0.238921] usbcore: registered new interface driver hub
Feb 18 23:45:14 ubuntu kernel: [    0.239009] usbcore: registered new device driver usb
Feb 18 23:45:14 ubuntu kernel: [    0.239162] PCI: Using ACPI for IRQ routing
Feb 18 23:45:14 ubuntu kernel: [    0.240631] PCI: pci_cache_line_size set to 64 bytes
Feb 18 23:45:14 ubuntu kernel: [    0.240694] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
Feb 18 23:45:14 ubuntu kernel: [    0.240696] reserve RAM buffer: 000000007bee0000 - 000000007bffffff 
Feb 18 23:45:14 ubuntu kernel: [    0.240808] NetLabel: Initializing
Feb 18 23:45:14 ubuntu kernel: [    0.240864] NetLabel:  domain hash size = 128
Feb 18 23:45:14 ubuntu kernel: [    0.240920] NetLabel:  protocols = UNLABELED CIPSOv4
Feb 18 23:45:14 ubuntu kernel: [    0.240988] NetLabel:  unlabeled traffic allowed by default
Feb 18 23:45:14 ubuntu kernel: [    0.249703] AppArmor: AppArmor Filesystem Enabled
Feb 18 23:45:14 ubuntu kernel: [    0.249804] pnp: PnP ACPI init
Feb 18 23:45:14 ubuntu kernel: [    0.249878] ACPI: bus type pnp registered
Feb 18 23:45:14 ubuntu kernel: [    0.250561] pnp 00:00: [bus 00-04]
Feb 18 23:45:14 ubuntu kernel: [    0.250568] pnp 00:00: [io  0x0cf8-0x0cff]
Feb 18 23:45:14 ubuntu kernel: [    0.250570] pnp 00:00: [io  0x0000-0x03af window]
Feb 18 23:45:14 ubuntu kernel: [    0.250572] pnp 00:00: [io  0x03e0-0x0cf7 window]
Feb 18 23:45:14 ubuntu kernel: [    0.250574] pnp 00:00: [io  0x9000-0xffff window]
Feb 18 23:45:14 ubuntu kernel: [    0.250576] pnp 00:00: [io  0x03b0-0x03df window]
Feb 18 23:45:14 ubuntu kernel: [    0.250579] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Feb 18 23:45:14 ubuntu kernel: [    0.250581] pnp 00:00: [mem 0x80000000-0xefffffff window]
Feb 18 23:45:14 ubuntu kernel: [    0.250583] pnp 00:00: [mem 0xf4000000-0xfe02ffff window]
Feb 18 23:45:14 ubuntu kernel: [    0.250585] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Feb 18 23:45:14 ubuntu kernel: [    0.250587] pnp 00:00: [io  0x4700-0x470b window]
Feb 18 23:45:14 ubuntu kernel: [    0.250590] pnp 00:00: [io  0x1c00-0x1c80 window]
Feb 18 23:45:14 ubuntu kernel: [    0.250592] pnp 00:00: [mem 0xfec80000-0xfecbffff window]
Feb 18 23:45:14 ubuntu kernel: [    0.250684] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Feb 18 23:45:14 ubuntu kernel: [    0.250795] pnp 00:01: [io  0x1000-0x107f]
Feb 18 23:45:14 ubuntu kernel: [    0.250797] pnp 00:01: [io  0x1080-0x10ff]
Feb 18 23:45:14 ubuntu kernel: [    0.250799] pnp 00:01: [io  0x1400-0x147f]
Feb 18 23:45:14 ubuntu kernel: [    0.250801] pnp 00:01: [io  0x1480-0x14ff]
Feb 18 23:45:14 ubuntu kernel: [    0.250803] pnp 00:01: [io  0x1800-0x187f]
Feb 18 23:45:14 ubuntu kernel: [    0.250805] pnp 00:01: [io  0x1880-0x18ff]
Feb 18 23:45:14 ubuntu kernel: [    0.250807] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Feb 18 23:45:14 ubuntu kernel: [    0.250809] pnp 00:01: [mem 0xfefe0000-0xfefe01ff]
Feb 18 23:45:14 ubuntu kernel: [    0.250812] pnp 00:01: [mem 0xfefe1000-0xfefe10ff]
Feb 18 23:45:14 ubuntu kernel: [    0.250814] pnp 00:01: [mem 0x7c000000-0x7fffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.250882] system 00:01: [io  0x1000-0x107f] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.250941] system 00:01: [io  0x1080-0x10ff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.251000] system 00:01: [io  0x1400-0x147f] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.251059] system 00:01: [io  0x1480-0x14ff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.251117] system 00:01: [io  0x1800-0x187f] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.251176] system 00:01: [io  0x1880-0x18ff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.251235] system 00:01: [mem 0xfefe0000-0xfefe01ff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.251295] system 00:01: [mem 0xfefe1000-0xfefe10ff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.251354] system 00:01: [mem 0x7c000000-0x7fffffff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.251414] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 18 23:45:14 ubuntu kernel: [    0.252034] pnp 00:02: [io  0x0010-0x001f]
Feb 18 23:45:14 ubuntu kernel: [    0.252037] pnp 00:02: [io  0x0022-0x003f]
Feb 18 23:45:14 ubuntu kernel: [    0.252038] pnp 00:02: [io  0x0044-0x004d]
Feb 18 23:45:14 ubuntu kernel: [    0.252040] pnp 00:02: [io  0x0050-0x005e]
Feb 18 23:45:14 ubuntu kernel: [    0.252042] pnp 00:02: [io  0x0062-0x0063]
Feb 18 23:45:14 ubuntu kernel: [    0.252044] pnp 00:02: [io  0x0065-0x006f]
Feb 18 23:45:14 ubuntu kernel: [    0.252045] pnp 00:02: [io  0x0074-0x007f]
Feb 18 23:45:14 ubuntu kernel: [    0.252047] pnp 00:02: [io  0x0091-0x0093]
Feb 18 23:45:14 ubuntu kernel: [    0.252049] pnp 00:02: [io  0x00a2-0x00bf]
Feb 18 23:45:14 ubuntu kernel: [    0.252051] pnp 00:02: [io  0x00e0-0x00ef]
Feb 18 23:45:14 ubuntu kernel: [    0.252053] pnp 00:02: [io  0x04d0-0x04d1]
Feb 18 23:45:14 ubuntu kernel: [    0.252055] pnp 00:02: [io  0x0800-0x087f]
Feb 18 23:45:14 ubuntu kernel: [    0.252056] pnp 00:02: [io  0x0290-0x0297]
Feb 18 23:45:14 ubuntu kernel: [    0.252128] system 00:02: [io  0x04d0-0x04d1] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.252187] system 00:02: [io  0x0800-0x087f] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.252246] system 00:02: [io  0x0290-0x0297] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.252305] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 18 23:45:14 ubuntu kernel: [    0.252316] pnp 00:03: [dma 4]
Feb 18 23:45:14 ubuntu kernel: [    0.252318] pnp 00:03: [io  0x0000-0x000f]
Feb 18 23:45:14 ubuntu kernel: [    0.252320] pnp 00:03: [io  0x0080-0x0090]
Feb 18 23:45:14 ubuntu kernel: [    0.252322] pnp 00:03: [io  0x0094-0x009f]
Feb 18 23:45:14 ubuntu kernel: [    0.252323] pnp 00:03: [io  0x00c0-0x00df]
Feb 18 23:45:14 ubuntu kernel: [    0.252367] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Feb 18 23:45:14 ubuntu kernel: [    0.252413] pnp 00:04: [io  0x0070-0x0073]
Feb 18 23:45:14 ubuntu kernel: [    0.252429] pnp 00:04: [irq 8]
Feb 18 23:45:14 ubuntu kernel: [    0.252475] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Feb 18 23:45:14 ubuntu kernel: [    0.252486] pnp 00:05: [io  0x0061]
Feb 18 23:45:14 ubuntu kernel: [    0.252528] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Feb 18 23:45:14 ubuntu kernel: [    0.252536] pnp 00:06: [io  0x00f0-0x00ff]
Feb 18 23:45:14 ubuntu kernel: [    0.252545] pnp 00:06: [irq 13]
Feb 18 23:45:14 ubuntu kernel: [    0.252594] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Feb 18 23:45:14 ubuntu kernel: [    0.252757] pnp 00:07: [io  0x03f0-0x03f5]
Feb 18 23:45:14 ubuntu kernel: [    0.252759] pnp 00:07: [io  0x03f7]
Feb 18 23:45:14 ubuntu kernel: [    0.252767] pnp 00:07: [irq 6]
Feb 18 23:45:14 ubuntu kernel: [    0.252769] pnp 00:07: [dma 2]
Feb 18 23:45:14 ubuntu kernel: [    0.252826] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
Feb 18 23:45:14 ubuntu kernel: [    0.253048] pnp 00:08: [io  0x03f8-0x03ff]
Feb 18 23:45:14 ubuntu kernel: [    0.253056] pnp 00:08: [irq 4]
Feb 18 23:45:14 ubuntu kernel: [    0.253126] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Feb 18 23:45:14 ubuntu kernel: [    0.253685] pnp 00:09: [io  0x0378-0x037f]
Feb 18 23:45:14 ubuntu kernel: [    0.253687] pnp 00:09: [io  0x0778-0x077b]
Feb 18 23:45:14 ubuntu kernel: [    0.253695] pnp 00:09: [irq 7]
Feb 18 23:45:14 ubuntu kernel: [    0.253697] pnp 00:09: [dma 3]
Feb 18 23:45:14 ubuntu kernel: [    0.253759] pnp 00:09: Plug and Play ACPI device, IDs PNP0401 (active)
Feb 18 23:45:14 ubuntu kernel: [    0.253818] pnp 00:0a: [mem 0xf0000000-0xf3ffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.253878] system 00:0a: [mem 0xf0000000-0xf3ffffff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.253938] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 18 23:45:14 ubuntu kernel: [    0.254014] pnp 00:0b: [mem 0x000f0000-0x000fffff]
Feb 18 23:45:14 ubuntu kernel: [    0.254016] pnp 00:0b: [mem 0xfeff0000-0xfeff00ff]
Feb 18 23:45:14 ubuntu kernel: [    0.254018] pnp 00:0b: [mem 0x7bee0000-0x7befffff]
Feb 18 23:45:14 ubuntu kernel: [    0.254020] pnp 00:0b: [mem 0xffff0000-0xffffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.254025] pnp 00:0b: [mem 0x00000000-0x0009ffff]
Feb 18 23:45:14 ubuntu kernel: [    0.254027] pnp 00:0b: [mem 0x00100000-0x7bedffff]
Feb 18 23:45:14 ubuntu kernel: [    0.254029] pnp 00:0b: [mem 0x7bf00000-0x7fefffff]
Feb 18 23:45:14 ubuntu kernel: [    0.254031] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
Feb 18 23:45:14 ubuntu kernel: [    0.254033] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
Feb 18 23:45:14 ubuntu kernel: [    0.254035] pnp 00:0b: [mem 0xfefff000-0xfeffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.254037] pnp 00:0b: [mem 0xfff80000-0xfff80fff]
Feb 18 23:45:14 ubuntu kernel: [    0.254039] pnp 00:0b: [mem 0xfff90000-0xfffbffff]
Feb 18 23:45:14 ubuntu kernel: [    0.254041] pnp 00:0b: [mem 0xfffed000-0xfffeffff]
Feb 18 23:45:14 ubuntu kernel: [    0.254120] system 00:0b: [mem 0x000f0000-0x000fffff] could not be reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254180] system 00:0b: [mem 0xfeff0000-0xfeff00ff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254240] system 00:0b: [mem 0x7bee0000-0x7befffff] could not be reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254300] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254359] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254419] system 00:0b: [mem 0x00100000-0x7bedffff] could not be reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254478] system 00:0b: [mem 0x7bf00000-0x7fefffff] could not be reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254538] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254598] system 00:0b: [mem 0xfee00000-0xfeefffff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254657] system 00:0b: [mem 0xfefff000-0xfeffffff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254716] system 00:0b: [mem 0xfff80000-0xfff80fff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254776] system 00:0b: [mem 0xfff90000-0xfffbffff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254835] system 00:0b: [mem 0xfffed000-0xfffeffff] has been reserved
Feb 18 23:45:14 ubuntu kernel: [    0.254895] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
Feb 18 23:45:14 ubuntu kernel: [    0.254904] pnp: PnP ACPI: found 12 devices
Feb 18 23:45:14 ubuntu kernel: [    0.254960] ACPI: ACPI bus type pnp unregistered
Feb 18 23:45:14 ubuntu kernel: [    0.261295] Switching to clocksource acpi_pm
Feb 18 23:45:14 ubuntu kernel: [    0.261572] PCI: max bus depth: 1 pci_try_num: 2
Feb 18 23:45:14 ubuntu kernel: [    0.261592] pci 0000:00:0d.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
Feb 18 23:45:14 ubuntu kernel: [    0.261661] pci 0000:01:06.0: BAR 6: assigned [mem 0xfdf00000-0xfdf1ffff pref]
Feb 18 23:45:14 ubuntu kernel: [    0.261728] pci 0000:01:08.0: BAR 6: assigned [mem 0xfdf20000-0xfdf3ffff pref]
Feb 18 23:45:14 ubuntu kernel: [    0.261795] pci 0000:00:04.0: PCI bridge to [bus 01-01]
Feb 18 23:45:14 ubuntu kernel: [    0.261853] pci 0000:00:04.0:   bridge window [io  0xc000-0xcfff]
Feb 18 23:45:14 ubuntu kernel: [    0.261913] pci 0000:00:04.0:   bridge window [mem 0xfda00000-0xfdafffff]
Feb 18 23:45:14 ubuntu kernel: [    0.261973] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
Feb 18 23:45:14 ubuntu kernel: [    0.262042] pci 0000:02:00.0: BAR 6: assigned [mem 0xfa000000-0xfa01ffff pref]
Feb 18 23:45:14 ubuntu kernel: [    0.262109] pci 0000:00:09.0: PCI bridge to [bus 02-02]
Feb 18 23:45:14 ubuntu kernel: [    0.262166] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
Feb 18 23:45:14 ubuntu kernel: [    0.262226] pci 0000:00:09.0:   bridge window [mem 0xf8000000-0xfaffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262285] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
Feb 18 23:45:14 ubuntu kernel: [    0.262353] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
Feb 18 23:45:14 ubuntu kernel: [    0.262411] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
Feb 18 23:45:14 ubuntu kernel: [    0.262470] pci 0000:00:0b.0:   bridge window [mem 0xfde00000-0xfdefffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262530] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
Feb 18 23:45:14 ubuntu kernel: [    0.262598] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
Feb 18 23:45:14 ubuntu kernel: [    0.262655] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
Feb 18 23:45:14 ubuntu kernel: [    0.262715] pci 0000:00:0c.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262774] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
Feb 18 23:45:14 ubuntu kernel: [    0.262847] pci 0000:00:04.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.262852] pci 0000:00:09.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.262855] pci 0000:00:0b.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.262859] pci 0000:00:0c.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.262862] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262865] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262867] pci_bus 0000:00: resource 6 [mem 0x80000000-0xf3ffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262869] pci_bus 0000:00: resource 7 [mem 0xf4000000-0xfcffffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262872] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Feb 18 23:45:14 ubuntu kernel: [    0.262874] pci_bus 0000:01: resource 1 [mem 0xfda00000-0xfdafffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262876] pci_bus 0000:01: resource 2 [mem 0xfdf00000-0xfdffffff pref]
Feb 18 23:45:14 ubuntu kernel: [    0.262879] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262881] pci_bus 0000:01: resource 5 [mem 0x000a0000-0x000bffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262883] pci_bus 0000:01: resource 6 [mem 0x80000000-0xf3ffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262886] pci_bus 0000:01: resource 7 [mem 0xf4000000-0xfcffffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262888] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
Feb 18 23:45:14 ubuntu kernel: [    0.262891] pci_bus 0000:02: resource 1 [mem 0xf8000000-0xfaffffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262893] pci_bus 0000:02: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
Feb 18 23:45:14 ubuntu kernel: [    0.262896] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
Feb 18 23:45:14 ubuntu kernel: [    0.262898] pci_bus 0000:03: resource 1 [mem 0xfde00000-0xfdefffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262900] pci_bus 0000:03: resource 2 [mem 0xfdd00000-0xfddfffff 64bit pref]
Feb 18 23:45:14 ubuntu kernel: [    0.262903] pci_bus 0000:04: resource 0 [io  0x9000-0x9fff]
Feb 18 23:45:14 ubuntu kernel: [    0.262905] pci_bus 0000:04: resource 1 [mem 0xfdc00000-0xfdcfffff]
Feb 18 23:45:14 ubuntu kernel: [    0.262908] pci_bus 0000:04: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
Feb 18 23:45:14 ubuntu kernel: [    0.262952] NET: Registered protocol family 2
Feb 18 23:45:14 ubuntu kernel: [    0.263124] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Feb 18 23:45:14 ubuntu kernel: [    0.264002] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Feb 18 23:45:14 ubuntu kernel: [    0.264699] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Feb 18 23:45:14 ubuntu kernel: [    0.265351] TCP: Hash tables configured (established 262144 bind 65536)
Feb 18 23:45:14 ubuntu kernel: [    0.265411] TCP reno registered
Feb 18 23:45:14 ubuntu kernel: [    0.265476] UDP hash table entries: 1024 (order: 3, 32768 bytes)
Feb 18 23:45:14 ubuntu kernel: [    0.265557] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
Feb 18 23:45:14 ubuntu kernel: [    0.265734] NET: Registered protocol family 1
Feb 18 23:45:14 ubuntu kernel: [    0.266048] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
Feb 18 23:45:14 ubuntu kernel: [    0.266124] pci 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
Feb 18 23:45:14 ubuntu kernel: [    0.336035] pci 0000:00:02.0: PCI INT A disabled
Feb 18 23:45:14 ubuntu kernel: [    0.336232] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
Feb 18 23:45:14 ubuntu kernel: [    0.336298] pci 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
Feb 18 23:45:14 ubuntu kernel: [    0.336374] pci 0000:00:02.1: PCI INT B disabled
Feb 18 23:45:14 ubuntu kernel: [    0.336471] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:45:14 ubuntu kernel: [    0.336574] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:45:14 ubuntu kernel: [    0.336682] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:45:14 ubuntu kernel: [    0.336791] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:45:14 ubuntu kernel: [    0.336902] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:45:14 ubuntu kernel: [    0.337016] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 18 23:45:14 ubuntu kernel: [    0.337098] pci 0000:02:00.0: Boot video device
Feb 18 23:45:14 ubuntu kernel: [    0.337101] PCI: CLS 64 bytes, default 64
Feb 18 23:45:14 ubuntu kernel: [    0.340175] audit: initializing netlink socket (disabled)
Feb 18 23:45:14 ubuntu kernel: [    0.340241] type=2000 audit(1361231030.336:1): initialized
Feb 18 23:45:14 ubuntu kernel: [    0.364356] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb 18 23:45:14 ubuntu kernel: [    0.366630] VFS: Disk quotas dquot_6.5.2
Feb 18 23:45:14 ubuntu kernel: [    0.366742] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb 18 23:45:14 ubuntu kernel: [    0.367342] fuse init (API version 7.17)
Feb 18 23:45:14 ubuntu kernel: [    0.367486] msgmni has been set to 3842
Feb 18 23:45:14 ubuntu kernel: [    0.367851] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Feb 18 23:45:14 ubuntu kernel: [    0.367940] io scheduler noop registered
Feb 18 23:45:14 ubuntu kernel: [    0.367997] io scheduler deadline registered
Feb 18 23:45:14 ubuntu kernel: [    0.368115] io scheduler cfq registered (default)
Feb 18 23:45:14 ubuntu kernel: [    0.368327] pcieport 0000:00:09.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.368573] pcieport 0000:00:0b.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.368626] pcieport 0000:00:0c.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.368701] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 18 23:45:14 ubuntu kernel: [    0.368783] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb 18 23:45:14 ubuntu kernel: [    0.368987] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Feb 18 23:45:14 ubuntu kernel: [    0.369058] ACPI: Power Button [PWRB]
Feb 18 23:45:14 ubuntu kernel: [    0.369170] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Feb 18 23:45:14 ubuntu kernel: [    0.369237] ACPI: Power Button [PWRF]
Feb 18 23:45:14 ubuntu kernel: [    0.369346] ACPI: Fan [FAN] (on)
Feb 18 23:45:14 ubuntu kernel: [    0.371814] thermal LNXTHERM:00: registered as thermal_zone0
Feb 18 23:45:14 ubuntu kernel: [    0.371873] ACPI: Thermal Zone [THRM] (40 C)
Feb 18 23:45:14 ubuntu kernel: [    0.371966] ERST: Table is not found!
Feb 18 23:45:14 ubuntu kernel: [    0.372040] GHES: HEST is not enabled!
Feb 18 23:45:14 ubuntu kernel: [    0.372173] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Feb 18 23:45:14 ubuntu kernel: [    0.392581] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 18 23:45:14 ubuntu kernel: [    0.434590] Freeing initrd memory: 13888k freed
Feb 18 23:45:14 ubuntu kernel: [    0.536579] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 18 23:45:14 ubuntu kernel: [    0.536922] Linux agpgart interface v0.103
Feb 18 23:45:14 ubuntu kernel: [    0.538702] brd: module loaded
Feb 18 23:45:14 ubuntu kernel: [    0.539688] loop: module loaded
Feb 18 23:45:14 ubuntu kernel: [    0.540042] pata_acpi 0000:00:06.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.540291] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
Feb 18 23:45:14 ubuntu kernel: [    0.540371] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
Feb 18 23:45:14 ubuntu kernel: [    0.540450] pata_acpi 0000:00:08.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.540457] pata_acpi 0000:00:08.0: PCI INT A disabled
Feb 18 23:45:14 ubuntu kernel: [    0.540924] Fixed MDIO Bus: probed
Feb 18 23:45:14 ubuntu kernel: [    0.541002] tun: Universal TUN/TAP device driver, 1.6
Feb 18 23:45:14 ubuntu kernel: [    0.541059] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Feb 18 23:45:14 ubuntu kernel: [    0.541176] PPP generic driver version 2.4.2
Feb 18 23:45:14 ubuntu kernel: [    0.541354] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb 18 23:45:14 ubuntu kernel: [    0.541438] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
Feb 18 23:45:14 ubuntu kernel: [    0.541521] ehci_hcd 0000:00:02.1: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.541524] ehci_hcd 0000:00:02.1: EHCI Host Controller
Feb 18 23:45:14 ubuntu kernel: [    0.542447] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Feb 18 23:45:14 ubuntu kernel: [    0.542536] ehci_hcd 0000:00:02.1: debug port 1
Feb 18 23:45:14 ubuntu kernel: [    0.542598] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
Feb 18 23:45:14 ubuntu kernel: [    0.542622] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
Feb 18 23:45:14 ubuntu kernel: [    0.552025] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Feb 18 23:45:14 ubuntu kernel: [    0.552249] hub 1-0:1.0: USB hub found
Feb 18 23:45:14 ubuntu kernel: [    0.552308] hub 1-0:1.0: 8 ports detected
Feb 18 23:45:14 ubuntu kernel: [    0.552465] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb 18 23:45:14 ubuntu kernel: [    0.552551] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
Feb 18 23:45:14 ubuntu kernel: [    0.552626] ohci_hcd 0000:00:02.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.552629] ohci_hcd 0000:00:02.0: OHCI Host Controller
Feb 18 23:45:14 ubuntu kernel: [    0.552745] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Feb 18 23:45:14 ubuntu kernel: [    0.552834] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
Feb 18 23:45:14 ubuntu kernel: [    0.610130] hub 2-0:1.0: USB hub found
Feb 18 23:45:14 ubuntu kernel: [    0.610189] hub 2-0:1.0: 8 ports detected
Feb 18 23:45:14 ubuntu kernel: [    0.610329] uhci_hcd: USB Universal Host Controller Interface driver
Feb 18 23:45:14 ubuntu kernel: [    0.610442] usbcore: registered new interface driver libusual
Feb 18 23:45:14 ubuntu kernel: [    0.610544] i8042: PNP: No PS/2 controller found. Probing ports directly.
Feb 18 23:45:14 ubuntu kernel: [    0.611011] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 18 23:45:14 ubuntu kernel: [    0.611073] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 18 23:45:14 ubuntu kernel: [    0.611292] mousedev: PS/2 mouse device common for all mice
Feb 18 23:45:14 ubuntu kernel: [    0.611515] rtc_cmos 00:04: RTC can wake from S4
Feb 18 23:45:14 ubuntu kernel: [    0.611708] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Feb 18 23:45:14 ubuntu kernel: [    0.611799] rtc0: alarms up to one year, y3k, 242 bytes nvram
Feb 18 23:45:14 ubuntu kernel: [    0.611939] device-mapper: uevent: version 1.0.3
Feb 18 23:45:14 ubuntu kernel: [    0.612097] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Feb 18 23:45:14 ubuntu kernel: [    0.612172] cpuidle: using governor ladder
Feb 18 23:45:14 ubuntu kernel: [    0.612228] cpuidle: using governor menu
Feb 18 23:45:14 ubuntu kernel: [    0.612285] EFI Variables Facility v0.08 2004-May-17
Feb 18 23:45:14 ubuntu kernel: [    0.612580] TCP cubic registered
Feb 18 23:45:14 ubuntu kernel: [    0.612744] NET: Registered protocol family 10
Feb 18 23:45:14 ubuntu kernel: [    0.613287] NET: Registered protocol family 17
Feb 18 23:45:14 ubuntu kernel: [    0.613347] Registering the dns_resolver key type
Feb 18 23:45:14 ubuntu kernel: [    0.613543] PM: Hibernation image not present or could not be loaded.
Feb 18 23:45:14 ubuntu kernel: [    0.613554] registered taskstats version 1
Feb 18 23:45:14 ubuntu kernel: [    0.620316]   Magic number: 1:453:757
Feb 18 23:45:14 ubuntu kernel: [    0.620399] tty ttyS8: hash matches
Feb 18 23:45:14 ubuntu kernel: [    0.620553] rtc_cmos 00:04: setting system clock to 2013-02-18 23:43:51 UTC (1361231031)
Feb 18 23:45:14 ubuntu kernel: [    0.620627] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ (2 cpu cores) (version 2.20.00)
Feb 18 23:45:14 ubuntu kernel: [    0.620733] powernow-k8: fid 0x12 (2600 MHz), vid 0x8
Feb 18 23:45:14 ubuntu kernel: [    0.620790] powernow-k8: fid 0x10 (2400 MHz), vid 0xa
Feb 18 23:45:14 ubuntu kernel: [    0.620847] powernow-k8: fid 0xe (2200 MHz), vid 0xc
Feb 18 23:45:14 ubuntu kernel: [    0.620904] powernow-k8: fid 0xc (2000 MHz), vid 0xe
Feb 18 23:45:14 ubuntu kernel: [    0.620961] powernow-k8: fid 0xa (1800 MHz), vid 0x10
Feb 18 23:45:14 ubuntu kernel: [    0.621018] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
Feb 18 23:45:14 ubuntu kernel: [    0.621152] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 18 23:45:14 ubuntu kernel: [    0.621215] EDD information not available.
Feb 18 23:45:14 ubuntu kernel: [    0.622957] Freeing unused kernel memory: 924k freed
Feb 18 23:45:14 ubuntu kernel: [    0.623429] Write protecting the kernel read-only data: 12288k
Feb 18 23:45:14 ubuntu kernel: [    0.628712] Freeing unused kernel memory: 1604k freed
Feb 18 23:45:14 ubuntu kernel: [    0.633529] Freeing unused kernel memory: 1196k freed
Feb 18 23:45:14 ubuntu kernel: [    0.681103] pata_amd 0000:00:06.0: version 0.4.1
Feb 18 23:45:14 ubuntu kernel: [    0.681155] pata_amd 0000:00:06.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.691916] scsi0 : pata_amd
Feb 18 23:45:14 ubuntu kernel: [    0.695081] scsi1 : pata_amd
Feb 18 23:45:14 ubuntu kernel: [    0.695644] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Feb 18 23:45:14 ubuntu kernel: [    0.695705] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Feb 18 23:45:14 ubuntu kernel: [    0.718381] sata_nv 0000:00:08.0: version 3.5
Feb 18 23:45:14 ubuntu kernel: [    0.718400] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
Feb 18 23:45:14 ubuntu kernel: [    0.718527] sata_nv 0000:00:08.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    0.724161] scsi2 : sata_nv
Feb 18 23:45:14 ubuntu kernel: [    0.726546] scsi3 : sata_nv
Feb 18 23:45:14 ubuntu kernel: [    0.726778] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 21
Feb 18 23:45:14 ubuntu kernel: [    0.726838] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 21
Feb 18 23:45:14 ubuntu kernel: [    0.733658] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Feb 18 23:45:14 ubuntu kernel: [    0.733918] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Feb 18 23:45:14 ubuntu kernel: [    0.733994] r8169 0000:01:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Feb 18 23:45:14 ubuntu kernel: [    0.734084] r8169 0000:01:08.0: (unregistered net_device): not PCI Express
Feb 18 23:45:14 ubuntu kernel: [    0.734568] r8169 0000:01:08.0: eth0: RTL8169sc/8110sc at 0xffffc90000328000, 00:50:8d:ca:5b:5d, XID 18000000 IRQ 18
Feb 18 23:45:14 ubuntu kernel: [    0.734638] r8169 0000:01:08.0: eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Feb 18 23:45:14 ubuntu kernel: [    0.737588] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Feb 18 23:45:14 ubuntu kernel: [    0.761251] Floppy drive(s): fd0 is 1.44M
Feb 18 23:45:14 ubuntu kernel: [    0.764205] 8139cp 0000:01:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Feb 18 23:45:14 ubuntu kernel: [    0.780501] FDC 0 is a post-1991 82077
Feb 18 23:45:14 ubuntu kernel: [    0.856334] ata1.00: ATAPI: SONY    DVD RW AW-Q170A, 1.72, max UDMA/66
Feb 18 23:45:14 ubuntu kernel: [    0.856404] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
Feb 18 23:45:14 ubuntu kernel: [    0.872262] ata1.00: configured for UDMA/66
Feb 18 23:45:14 ubuntu kernel: [    0.873470] scsi 0:0:0:0: CD-ROM            SONY     DVD RW AW-Q170A  1.72 PQ: 0 ANSI: 5
Feb 18 23:45:14 ubuntu kernel: [    0.874886] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Feb 18 23:45:14 ubuntu kernel: [    0.874946] cdrom: Uniform CD-ROM driver Revision: 3.20
Feb 18 23:45:14 ubuntu kernel: [    0.875167] sr 0:0:0:0: Attached scsi CD-ROM sr0
Feb 18 23:45:14 ubuntu kernel: [    0.875300] sr 0:0:0:0: Attached scsi generic sg0 type 5
Feb 18 23:45:14 ubuntu kernel: [    0.875477] ata2: port disabled--ignoring
Feb 18 23:45:14 ubuntu kernel: [    0.976023] usb 1-2: new high-speed USB device number 3 using ehci_hcd
Feb 18 23:45:14 ubuntu kernel: [    1.109896] hub 1-2:1.0: USB hub found
Feb 18 23:45:14 ubuntu kernel: [    1.110203] hub 1-2:1.0: 4 ports detected
Feb 18 23:45:14 ubuntu kernel: [    1.196040] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 18 23:45:14 ubuntu kernel: [    1.228532] ata3.00: ATA-7: WDC WD2500JS-00SGB0, 20.06C03, max UDMA/133
Feb 18 23:45:14 ubuntu kernel: [    1.228592] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Feb 18 23:45:14 ubuntu kernel: [    1.236720] ata3.00: configured for UDMA/133
Feb 18 23:45:14 ubuntu kernel: [    1.236890] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500JS-00S 20.0 PQ: 0 ANSI: 5
Feb 18 23:45:14 ubuntu kernel: [    1.237099] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Feb 18 23:45:14 ubuntu kernel: [    1.237116] sd 2:0:0:0: Attached scsi generic sg1 type 0
Feb 18 23:45:14 ubuntu kernel: [    1.237283] sd 2:0:0:0: [sda] Write Protect is off
Feb 18 23:45:14 ubuntu kernel: [    1.237349] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 18 23:45:14 ubuntu kernel: [    1.237405] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 18 23:45:14 ubuntu kernel: [    1.244699]  sda: sda1
Feb 18 23:45:14 ubuntu kernel: [    1.245054] sd 2:0:0:0: [sda] Attached SCSI disk
Feb 18 23:45:14 ubuntu kernel: [    1.412021] usb 2-1: new full-speed USB device number 2 using ohci_hcd
Feb 18 23:45:14 ubuntu kernel: [    1.558223] ata4: SATA link down (SStatus 0 SControl 300)
Feb 18 23:45:14 ubuntu kernel: [    1.558842] 8139too: 8139too Fast Ethernet driver 0.9.28
Feb 18 23:45:14 ubuntu kernel: [    1.559252] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
Feb 18 23:45:14 ubuntu kernel: [    1.559326] 8139too 0000:01:06.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
Feb 18 23:45:14 ubuntu kernel: [    1.560200] 8139too 0000:01:06.0: eth1: RealTek RTL8139 at 0xcc00, 6c:fd:b9:22:e6:17, IRQ 17
Feb 18 23:45:14 ubuntu kernel: [    1.644288] input: Razer Razer DeathAdder as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input2
Feb 18 23:45:14 ubuntu kernel: [    1.644491] generic-usb 0003:1532:0016.0001: input,hidraw0: USB HID v1.11 Mouse [Razer Razer DeathAdder] on usb-0000:00:02.0-1/input0
Feb 18 23:45:14 ubuntu kernel: [    1.644578] usbcore: registered new interface driver usbhid
Feb 18 23:45:14 ubuntu kernel: [    1.644641] usbhid: USB HID core driver
Feb 18 23:45:14 ubuntu kernel: [    1.708333] usb 1-2.1: new low-speed USB device number 4 using ehci_hcd
Feb 18 23:45:14 ubuntu kernel: [    1.812591] input: LOGITECH G110 G-keys as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.1/1-2.1:1.0/input/input3
Feb 18 23:45:14 ubuntu kernel: [    1.812817] generic-usb 0003:046D:C22B.0002: input,hiddev0,hidraw1: USB HID v1.00 Keypad [LOGITECH G110 G-keys] on usb-0000:00:02.1-2.1/input0
Feb 18 23:45:14 ubuntu kernel: [    1.812951] usbhid 1-2.1:1.1: couldn't find an input interrupt endpoint
Feb 18 23:45:14 ubuntu kernel: [    1.884346] usb 1-2.3: new low-speed USB device number 5 using ehci_hcd
Feb 18 23:45:14 ubuntu kernel: [    1.985982] input: Gaming Keyboard G110 as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.0/input/input4
Feb 18 23:45:14 ubuntu kernel: [    1.986161] generic-usb 0003:046D:C22A.0003: input,hidraw2: USB HID v1.10 Keyboard [Gaming Keyboard G110] on usb-0000:00:02.1-2.3/input0
Feb 18 23:45:14 ubuntu kernel: [    1.992391] input: Gaming Keyboard G110 as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.3/1-2.3:1.1/input/input5
Feb 18 23:45:14 ubuntu kernel: [    1.992598] generic-usb 0003:046D:C22A.0004: input,hiddev0,hidraw3: USB HID v1.10 Device [Gaming Keyboard G110] on usb-0000:00:02.1-2.3/input1
Feb 18 23:45:14 ubuntu kernel: [    2.182624] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
Feb 18 23:45:14 ubuntu kernel: [    4.890766] MCE: In-kernel MCE decoding enabled.
Feb 18 23:45:14 ubuntu kernel: [    4.900602] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
Feb 18 23:45:14 ubuntu kernel: [    4.939625] EDAC MC: Ver: 2.1.0
Feb 18 23:45:14 ubuntu kernel: [    5.014909] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
Feb 18 23:45:14 ubuntu kernel: [    5.014995] i2c i2c-1: nForce2 SMBus adapter at 0xf400
Feb 18 23:45:14 ubuntu kernel: [    5.028860] AMD64 EDAC driver v3.4.0
Feb 18 23:45:14 ubuntu kernel: [    5.028967] EDAC amd64: DRAM ECC disabled.
Feb 18 23:45:14 ubuntu kernel: [    5.029029] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Feb 18 23:45:14 ubuntu kernel: [    5.029030]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Feb 18 23:45:14 ubuntu kernel: [    5.029031]  (Note that use of the override may cause unknown side effects.)
Feb 18 23:45:14 ubuntu kernel: [    5.040883] parport_pc 00:09: reported by Plug and Play ACPI
Feb 18 23:45:14 ubuntu kernel: [    5.041004] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Feb 18 23:45:14 ubuntu kernel: [    5.147381] wmi: Mapper loaded
Feb 18 23:45:14 ubuntu kernel: [    5.162735] ppdev: user-space parallel port driver
Feb 18 23:45:14 ubuntu kernel: [    5.330089] Linux video capture interface: v2.00
Feb 18 23:45:14 ubuntu kernel: [    5.401041] [drm] Initialized drm 1.1.0 20060810
Feb 18 23:45:14 ubuntu kernel: [    5.580953] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 18 23:45:14 ubuntu kernel: [    5.580961] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 18 23:45:14 ubuntu kernel: [    5.605455] IR NEC protocol handler initialized
Feb 18 23:45:14 ubuntu bluetoothd[1931]: Failed to init alert plugin
Feb 18 23:45:14 ubuntu bluetoothd[1931]: Failed to init time plugin
Feb 18 23:45:14 ubuntu bluetoothd[1931]: Failed to init proximity plugin
Feb 18 23:45:14 ubuntu kernel: [    5.607548] saa7130/34: v4l2 driver version 0, 2, 17 loaded
Feb 18 23:45:14 ubuntu kernel: [    5.607792] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Feb 18 23:45:14 ubuntu kernel: [    5.607813] saa7134 0000:01:05.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Feb 18 23:45:14 ubuntu kernel: [    5.607819] saa7130[0]: found at 0000:01:05.0, rev: 1, irq: 16, latency: 15, mmio: 0xfdaff000
Feb 18 23:45:14 ubuntu kernel: [    5.607824] saa7134 0000:01:05.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    5.607828] saa7134: Board is currently unknown. You might try to use the card=<nr>
Feb 18 23:45:14 ubuntu kernel: [    5.607829] saa7134: insmod option to specify which board do you have, but this is
Feb 18 23:45:14 ubuntu kernel: [    5.607830] saa7134: somewhat risky, as might damage your card. It is better to ask
Feb 18 23:45:14 ubuntu kernel: [    5.607831] saa7134: for support at linux-media@vger.kernel.org.
Feb 18 23:45:14 ubuntu kernel: [    5.607832] saa7134: The supported cards are:
Feb 18 23:45:14 ubuntu kernel: [    5.607834] saa7134:   card=0 -> UNKNOWN/GENERIC                         
Feb 18 23:45:14 ubuntu kernel: [    5.607837] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
Feb 18 23:45:14 ubuntu kernel: [    5.607841] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
Feb 18 23:45:14 ubuntu kernel: [    5.607845] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
Feb 18 23:45:14 ubuntu kernel: [    5.607849] saa7134:   card=4 -> EMPRESS                                  1131:6752
Feb 18 23:45:14 ubuntu kernel: [    5.607852] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
Feb 18 23:45:14 ubuntu kernel: [    5.607855] saa7134:   card=6 -> Tevion MD 9717                          
Feb 18 23:45:14 ubuntu kernel: [    5.607858] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
Feb 18 23:45:14 ubuntu kernel: [    5.607862] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
Feb 18 23:45:14 ubuntu kernel: [    5.607865] saa7134:   card=9 -> Medion 5044                             
Feb 18 23:45:14 ubuntu kernel: [    5.607867] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
Feb 18 23:45:14 ubuntu kernel: [    5.607870] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
Feb 18 23:45:14 ubuntu kernel: [    5.607873] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
Feb 18 23:45:14 ubuntu kernel: [    5.607877] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
Feb 18 23:45:14 ubuntu kernel: [    5.607879] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
Feb 18 23:45:14 ubuntu kernel: [    5.607882] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
Feb 18 23:45:14 ubuntu kernel: [    5.607885] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
Feb 18 23:45:14 ubuntu kernel: [    5.607890] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
Feb 18 23:45:14 ubuntu kernel: [    5.607893] saa7134:   card=18 -> BMK MPEX No Tuner                       
Feb 18 23:45:14 ubuntu kernel: [    5.607895] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
Feb 18 23:45:14 ubuntu kernel: [    5.607898] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
Feb 18 23:45:14 ubuntu kernel: [    5.607901] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
Feb 18 23:45:14 ubuntu kernel: [    5.607905] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
Feb 18 23:45:14 ubuntu kernel: [    5.607908] saa7134:   card=23 -> BMK MPEX Tuner                          
Feb 18 23:45:14 ubuntu kernel: [    5.607910] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
Feb 18 23:45:14 ubuntu kernel: [    5.607913] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
Feb 18 23:45:14 ubuntu kernel: [    5.607917] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
Feb 18 23:45:14 ubuntu kernel: [    5.607920] saa7134:   card=27 -> Manli MuchTV M-TV002                    
Feb 18 23:45:14 ubuntu kernel: [    5.607922] saa7134:   card=28 -> Manli MuchTV M-TV001                    
Feb 18 23:45:14 ubuntu kernel: [    5.607925] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
Feb 18 23:45:14 ubuntu kernel: [    5.607928] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
Feb 18 23:45:14 ubuntu kernel: [    5.607931] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
Feb 18 23:45:14 ubuntu kernel: [    5.607934] saa7134:   card=32 -> AVACS SmartTV                           
Feb 18 23:45:14 ubuntu kernel: [    5.607937] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
Feb 18 23:45:14 ubuntu kernel: [    5.607940] saa7134:   card=34 -> Noval Prime TV 7133                     
Feb 18 23:45:14 ubuntu kernel: [    5.607942] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
Feb 18 23:45:14 ubuntu kernel: [    5.607946] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
Feb 18 23:45:14 ubuntu kernel: [    5.607949] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
Feb 18 23:45:14 ubuntu kernel: [    5.607951] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
Feb 18 23:45:14 ubuntu kernel: [    5.607954] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
Feb 18 23:45:14 ubuntu kernel: [    5.607959] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
Feb 18 23:45:14 ubuntu kernel: [    5.607962] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
Feb 18 23:45:14 ubuntu kernel: [    5.607965] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
Feb 18 23:45:14 ubuntu kernel: [    5.607967] saa7134:   card=43 -> :Zolid Xpert TV7134                     
Feb 18 23:45:14 ubuntu kernel: [    5.607970] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
Feb 18 23:45:14 ubuntu kernel: [    5.607972] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
Feb 18 23:45:14 ubuntu kernel: [    5.607976] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
Feb 18 23:45:14 ubuntu kernel: [    5.607979] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
Feb 18 23:45:14 ubuntu kernel: [    5.607982] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
Feb 18 23:45:14 ubuntu kernel: [    5.607985] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
Feb 18 23:45:14 ubuntu kernel: [    5.607988] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
Feb 18 23:45:14 ubuntu kernel: [    5.607991] saa7134:   card=51 -> ProVideo PV952                           1540:9524
Feb 18 23:45:14 ubuntu kernel: [    5.607994] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
Feb 18 23:45:14 ubuntu kernel: [    5.607997] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
Feb 18 23:45:14 ubuntu kernel: [    5.608037] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
Feb 18 23:45:14 ubuntu kernel: [    5.608042] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
Feb 18 23:45:14 ubuntu kernel: [    5.608045] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
Feb 18 23:45:14 ubuntu kernel: [    5.608048] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
Feb 18 23:45:14 ubuntu kernel: [    5.608052] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
Feb 18 23:45:14 ubuntu kernel: [    5.608056] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
Feb 18 23:45:14 ubuntu kernel: [    5.608059] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
Feb 18 23:45:14 ubuntu kernel: [    5.608063] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
Feb 18 23:45:14 ubuntu kernel: [    5.608066] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
Feb 18 23:45:14 ubuntu kernel: [    5.608069] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
Feb 18 23:45:14 ubuntu kernel: [    5.608071] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
Feb 18 23:45:14 ubuntu kernel: [    5.608074] saa7134:   card=65 -> V-Stream Studio TV Terminator           
Feb 18 23:45:14 ubuntu kernel: [    5.608077] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
Feb 18 23:45:14 ubuntu kernel: [    5.608080] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
Feb 18 23:45:14 ubuntu kernel: [    5.608083] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
Feb 18 23:45:14 ubuntu kernel: [    5.608086] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
Feb 18 23:45:14 ubuntu kernel: [    5.608089] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
Feb 18 23:45:14 ubuntu kernel: [    5.608092] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
Feb 18 23:45:14 ubuntu kernel: [    5.608095] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
Feb 18 23:45:14 ubuntu kernel: [    5.608098] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
Feb 18 23:45:14 ubuntu kernel: [    5.608102] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
Feb 18 23:45:14 ubuntu kernel: [    5.608105] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
Feb 18 23:45:14 ubuntu kernel: [    5.608108] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
Feb 18 23:45:14 ubuntu kernel: [    5.608111] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
Feb 18 23:45:14 ubuntu kernel: [    5.608114] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
Feb 18 23:45:14 ubuntu kernel: [    5.608117] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
Feb 18 23:45:14 ubuntu kernel: [    5.608120] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
Feb 18 23:45:14 ubuntu kernel: [    5.608123] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
Feb 18 23:45:14 ubuntu kernel: [    5.608126] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
Feb 18 23:45:14 ubuntu kernel: [    5.608130] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
Feb 18 23:45:14 ubuntu kernel: [    5.608133] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
Feb 18 23:45:14 ubuntu kernel: [    5.608136] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
Feb 18 23:45:14 ubuntu kernel: [    5.608140] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
Feb 18 23:45:14 ubuntu kernel: [    5.608143] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
Feb 18 23:45:14 ubuntu kernel: [    5.608146] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
Feb 18 23:45:14 ubuntu kernel: [    5.608149] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
Feb 18 23:45:14 ubuntu kernel: [    5.608153] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
Feb 18 23:45:14 ubuntu kernel: [    5.608156] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
Feb 18 23:45:14 ubuntu kernel: [    5.608159] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
Feb 18 23:45:14 ubuntu kernel: [    5.608162] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
Feb 18 23:45:14 ubuntu kernel: [    5.608166] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
Feb 18 23:45:14 ubuntu kernel: [    5.608171] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
Feb 18 23:45:14 ubuntu kernel: [    5.608174] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
Feb 18 23:45:14 ubuntu kernel: [    5.608178] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
Feb 18 23:45:14 ubuntu kernel: [    5.608182] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
Feb 18 23:45:14 ubuntu kernel: [    5.608185] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
Feb 18 23:45:14 ubuntu kernel: [    5.608188] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
Feb 18 23:45:14 ubuntu kernel: [    5.608191] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
Feb 18 23:45:14 ubuntu kernel: [    5.608195] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
Feb 18 23:45:14 ubuntu kernel: [    5.608198] saa7134:   card=103 -> Compro Videomate DVB-T200A              
Feb 18 23:45:14 ubuntu kernel: [    5.608200] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
Feb 18 23:45:14 ubuntu kernel: [    5.608206] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
Feb 18 23:45:14 ubuntu kernel: [    5.608209] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
Feb 18 23:45:14 ubuntu kernel: [    5.608213] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
Feb 18 23:45:14 ubuntu kernel: [    5.608217] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
Feb 18 23:45:14 ubuntu kernel: [    5.608220] saa7134:   card=109 -> Philips Tiger - S Reference design      
Feb 18 23:45:14 ubuntu kernel: [    5.608222] saa7134:   card=110 -> Avermedia M102                           1461:f31e
Feb 18 23:45:14 ubuntu kernel: [    5.608225] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
Feb 18 23:45:14 ubuntu kernel: [    5.608229] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
Feb 18 23:45:14 ubuntu kernel: [    5.608232] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
Feb 18 23:45:14 ubuntu kernel: [    5.608235] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
Feb 18 23:45:14 ubuntu kernel: [    5.608238] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
Feb 18 23:45:14 ubuntu kernel: [    5.608241] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
Feb 18 23:45:14 ubuntu kernel: [    5.608244] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
Feb 18 23:45:14 ubuntu kernel: [    5.608247] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
Feb 18 23:45:14 ubuntu kernel: [    5.608251] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
Feb 18 23:45:14 ubuntu kernel: [    5.608254] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
Feb 18 23:45:14 ubuntu kernel: [    5.608257] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
Feb 18 23:45:14 ubuntu kernel: [    5.608260] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
Feb 18 23:45:14 ubuntu kernel: [    5.608263] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
Feb 18 23:45:14 ubuntu kernel: [    5.608267] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
Feb 18 23:45:14 ubuntu kernel: [    5.608270] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
Feb 18 23:45:14 ubuntu kernel: [    5.608273] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
Feb 18 23:45:14 ubuntu kernel: [    5.608276] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
Feb 18 23:45:14 ubuntu kernel: [    5.608280] saa7134:   card=128 -> Beholder BeholdTV Columbus TV/FM         0000:5201
Feb 18 23:45:14 ubuntu kernel: [    5.608283] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
Feb 18 23:45:14 ubuntu kernel: [    5.608286] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
Feb 18 23:45:14 ubuntu kernel: [    5.608289] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
Feb 18 23:45:14 ubuntu kernel: [    5.608292] saa7134:   card=132 -> Genius TVGO AM11MCE                     
Feb 18 23:45:14 ubuntu kernel: [    5.608295] saa7134:   card=133 -> NXP Snake DVB-S reference design        
Feb 18 23:45:14 ubuntu kernel: [    5.608298] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
Feb 18 23:45:14 ubuntu kernel: [    5.608301] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
Feb 18 23:45:14 ubuntu kernel: [    5.608304] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
Feb 18 23:45:14 ubuntu kernel: [    5.608307] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
Feb 18 23:45:14 ubuntu kernel: [    5.608310] saa7134:   card=138 -> Avermedia M115                           1461:a836
Feb 18 23:45:14 ubuntu kernel: [    5.608313] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
Feb 18 23:45:14 ubuntu kernel: [    5.608316] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
Feb 18 23:45:14 ubuntu kernel: [    5.608320] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
Feb 18 23:45:14 ubuntu kernel: [    5.608323] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
Feb 18 23:45:14 ubuntu kernel: [    5.608326] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
Feb 18 23:45:14 ubuntu kernel: [    5.608329] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
Feb 18 23:45:14 ubuntu kernel: [    5.608332] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
Feb 18 23:45:14 ubuntu kernel: [    5.608336] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
Feb 18 23:45:14 ubuntu kernel: [    5.608339] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
Feb 18 23:45:14 ubuntu kernel: [    5.608342] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
Feb 18 23:45:14 ubuntu kernel: [    5.608345] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
Feb 18 23:45:14 ubuntu kernel: [    5.608348] saa7134:   card=150 -> Zogis Real Angel 220                    
Feb 18 23:45:14 ubuntu kernel: [    5.608350] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
Feb 18 23:45:14 ubuntu kernel: [    5.608354] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
Feb 18 23:45:14 ubuntu kernel: [    5.608357] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
Feb 18 23:45:14 ubuntu kernel: [    5.608360] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
Feb 18 23:45:14 ubuntu kernel: [    5.608363] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
Feb 18 23:45:14 ubuntu kernel: [    5.608367] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
Feb 18 23:45:14 ubuntu kernel: [    5.608372] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
Feb 18 23:45:14 ubuntu kernel: [    5.608375] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
Feb 18 23:45:14 ubuntu kernel: [    5.608378] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
Feb 18 23:45:14 ubuntu kernel: [    5.608382] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
Feb 18 23:45:14 ubuntu kernel: [    5.608385] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
Feb 18 23:45:14 ubuntu kernel: [    5.608388] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
Feb 18 23:45:14 ubuntu kernel: [    5.608391] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
Feb 18 23:45:14 ubuntu kernel: [    5.608394] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
Feb 18 23:45:14 ubuntu kernel: [    5.608398] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
Feb 18 23:45:14 ubuntu kernel: [    5.608401] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
Feb 18 23:45:14 ubuntu kernel: [    5.608404] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
Feb 18 23:45:14 ubuntu kernel: [    5.608407] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
Feb 18 23:45:14 ubuntu kernel: [    5.608411] saa7134:   card=169 -> Compro VideoMate S350/S300               185b:c900
Feb 18 23:45:14 ubuntu kernel: [    5.608414] saa7134:   card=170 -> AverMedia AverTV Studio 505              1461:a115
Feb 18 23:45:14 ubuntu kernel: [    5.608417] saa7134:   card=171 -> Beholder BeholdTV X7                     5ace:7595
Feb 18 23:45:14 ubuntu kernel: [    5.608420] saa7134:   card=172 -> RoverMedia TV Link Pro FM                19d1:0138
Feb 18 23:45:14 ubuntu kernel: [    5.608423] saa7134:   card=173 -> Zolid Hybrid TV Tuner PCI                1131:2004
Feb 18 23:45:14 ubuntu kernel: [    5.608426] saa7134:   card=174 -> Asus Europa Hybrid OEM                   1043:4847
Feb 18 23:45:14 ubuntu kernel: [    5.608429] saa7134:   card=175 -> Leadtek Winfast DTV1000S                 107d:6655
Feb 18 23:45:14 ubuntu kernel: [    5.608432] saa7134:   card=176 -> Beholder BeholdTV 505 RDS                0000:5051
Feb 18 23:45:14 ubuntu kernel: [    5.608435] saa7134:   card=177 -> Hawell HW-404M7                         
Feb 18 23:45:14 ubuntu kernel: [    5.608438] saa7134:   card=178 -> Beholder BeholdTV H7                     5ace:7190
Feb 18 23:45:14 ubuntu kernel: [    5.608441] saa7134:   card=179 -> Beholder BeholdTV A7                     5ace:7090
Feb 18 23:45:14 ubuntu kernel: [    5.608444] saa7134:   card=180 -> Avermedia PCI M733A                      1461:4155 1461:4255
Feb 18 23:45:14 ubuntu kernel: [    5.608448] saa7134:   card=181 -> TechoTrend TT-budget T-3000              13c2:2804
Feb 18 23:45:14 ubuntu kernel: [    5.608451] saa7134:   card=182 -> Kworld PCI SBTVD/ISDB-T Full-Seg Hybrid  17de:b136
Feb 18 23:45:14 ubuntu kernel: [    5.608454] saa7134:   card=183 -> Compro VideoMate Vista M1F               185b:c900
Feb 18 23:45:14 ubuntu kernel: [    5.608457] saa7134:   card=184 -> Encore ENLTV-FM 3                        1a7f:2108
Feb 18 23:45:14 ubuntu kernel: [    5.608461] saa7134:   card=185 -> MagicPro ProHDTV Pro2 DMB-TH/Hybrid      17de:d136
Feb 18 23:45:14 ubuntu kernel: [    5.608464] saa7134:   card=186 -> Beholder BeholdTV 501                    5ace:5010
Feb 18 23:45:14 ubuntu kernel: [    5.608467] saa7134:   card=187 -> Beholder BeholdTV 503 FM                 5ace:5030
Feb 18 23:45:14 ubuntu kernel: [    5.608471] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
Feb 18 23:45:14 ubuntu kernel: [    5.608488] saa7130[0]: board init: gpio is 804000
Feb 18 23:45:14 ubuntu kernel: [    5.639916] IR RC5(x) protocol handler initialized
Feb 18 23:45:14 ubuntu kernel: [    5.703148] IR RC6 protocol handler initialized
Feb 18 23:45:14 ubuntu kernel: [    5.712246] saa7130[0]: Huh, no eeprom present (err=-5)?
Feb 18 23:45:14 ubuntu kernel: [    5.712340] saa7130[0]: registered device video0 [v4l2]
Feb 18 23:45:14 ubuntu kernel: [    5.712397] saa7130[0]: registered device vbi0
Feb 18 23:45:14 ubuntu kernel: [    5.727041] IR JVC protocol handler initialized
Feb 18 23:45:14 ubuntu kernel: [    5.796638] IR Sony protocol handler initialized
Feb 18 23:45:14 ubuntu kernel: [    5.814214] saa7134 ALSA driver for DMA sound loaded
Feb 18 23:45:14 ubuntu kernel: [    5.814219] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio
Feb 18 23:45:14 ubuntu kernel: [    5.814828] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
Feb 18 23:45:14 ubuntu kernel: [    5.814846] snd_hda_intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
Feb 18 23:45:14 ubuntu kernel: [    5.814849] hda_intel: Disabling MSI
Feb 18 23:45:14 ubuntu kernel: [    5.814887] snd_hda_intel 0000:00:05.0: setting latency timer to 64
Feb 18 23:45:14 ubuntu kernel: [    5.829841] IR MCE Keyboard/mouse protocol handler initialized
Feb 18 23:45:14 ubuntu kernel: [    5.847160] lirc_dev: IR Remote Control driver registered, major 250 
Feb 18 23:45:14 ubuntu kernel: [    5.861098] IR LIRC bridge handler initialized
Feb 18 23:45:14 ubuntu kernel: [    6.452033] hda_codec: ALC883: BIOS auto-probing.
Feb 18 23:45:14 ubuntu kernel: [    7.660100] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input6
Feb 18 23:45:14 ubuntu kernel: [    7.660221] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input7
Feb 18 23:45:14 ubuntu kernel: [    7.660315] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
Feb 18 23:45:14 ubuntu kernel: [    7.660407] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
Feb 18 23:45:14 ubuntu kernel: [    7.660500] input: HDA NVidia Line-Out Side as /devices/pci0000:00/0000:00:05.0/sound/card0/input10
Feb 18 23:45:14 ubuntu kernel: [    7.660593] input: HDA NVidia Line-Out CLFE as /devices/pci0000:00/0000:00:05.0/sound/card0/input11
Feb 18 23:45:14 ubuntu kernel: [    7.660684] input: HDA NVidia Line-Out Surround as /devices/pci0000:00/0000:00:05.0/sound/card0/input12
Feb 18 23:45:14 ubuntu kernel: [    7.660774] input: HDA NVidia Line-Out Front as /devices/pci0000:00/0000:00:05.0/sound/card0/input13
Feb 18 23:45:14 ubuntu kernel: [   21.015867] Adding 262140k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262140k 
Feb 18 23:45:14 ubuntu kernel: [   24.920805] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
Feb 18 23:45:14 ubuntu kernel: [   72.446172] lp0: using parport0 (interrupt-driven).
Feb 18 23:45:14 ubuntu kernel: [   72.569438] AMD64 EDAC driver v3.4.0
Feb 18 23:45:14 ubuntu kernel: [   72.569491] EDAC amd64: DRAM ECC disabled.
Feb 18 23:45:14 ubuntu kernel: [   72.569501] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Feb 18 23:45:14 ubuntu kernel: [   72.569502]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Feb 18 23:45:14 ubuntu kernel: [   72.569503]  (Note that use of the override may cause unknown side effects.)
Feb 18 23:45:14 ubuntu kernel: [   83.561761] init: udev-fallback-graphics main process (1743) terminated with status 1
Feb 18 23:45:14 ubuntu kernel: [   83.788130] init: friendly-recovery post-stop process (1473) terminated with status 1
Feb 18 23:45:14 ubuntu kernel: [   83.788851] init: failsafe main process (1891) killed by TERM signal
Feb 18 23:45:14 ubuntu kernel: [   83.870377] type=1400 audit(1361259914.745:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1944 comm="apparmor_parser"
Feb 18 23:45:14 ubuntu kernel: [   83.886438] type=1400 audit(1361259914.761:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1944 comm="apparmor_parser"
Feb 18 23:45:14 ubuntu kernel: [   83.890194] Bluetooth: Core ver 2.16
Feb 18 23:45:14 ubuntu kernel: [   83.890223] NET: Registered protocol family 31
Feb 18 23:45:14 ubuntu kernel: [   83.890225] Bluetooth: HCI device and connection manager initialized
Feb 18 23:45:14 ubuntu kernel: [   83.890228] Bluetooth: HCI socket layer initialized
Feb 18 23:45:14 ubuntu kernel: [   83.890230] Bluetooth: L2CAP socket layer initialized
Feb 18 23:45:14 ubuntu kernel: [   83.890239] Bluetooth: SCO socket layer initialized
Feb 18 23:45:14 ubuntu kernel: [   83.907476] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 18 23:45:14 ubuntu kernel: [   83.907479] Bluetooth: BNEP filters: protocol multicast
Feb 18 23:45:14 ubuntu bluetoothd[1931]: Failed to init gatt_example plugin
Feb 18 23:45:14 ubuntu polkitd[1962]: started daemon version 0.104 using authority implementation `local' version `0.104'
Feb 18 23:45:14 ubuntu dbus[1899]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    SCPlugin-Ifupdown: init!
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    SCPlugin-Ifupdown: update_system_hostname
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    SCPluginIfupdown: management mode: unmanaged
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:06.0/net/eth1, iface: eth1)
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:06.0/net/eth1, iface: eth1): no ifupdown configuration found.
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0/net/eth0, iface: eth0)
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0/net/eth0, iface: eth0): no ifupdown configuration found.
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    SCPlugin-Ifupdown: end _init.
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    Ifupdown: get unmanaged devices count: 0
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    SCPlugin-Ifupdown: (37666608) ... get_connections.
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    SCPlugin-Ifupdown: (37666608) ... get_connections (managed=false): return empty list.
Feb 18 23:45:14 ubuntu NetworkManager[1951]:    Ifupdown: get unmanaged devices count: 0
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> modem-manager is now available
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> monitoring kernel firmware directory '/lib/firmware'.
Feb 18 23:45:14 ubuntu kernel: [   83.924533] Bluetooth: RFCOMM TTY layer initialized
Feb 18 23:45:14 ubuntu kernel: [   83.924540] Bluetooth: RFCOMM socket layer initialized
Feb 18 23:45:14 ubuntu kernel: [   83.924542] Bluetooth: RFCOMM ver 1.11
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> WiFi enabled by radio killswitch; enabled by state file
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> WWAN enabled by radio killswitch; enabled by state file
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> WiMAX enabled by radio killswitch; enabled by state file
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> Networking is enabled by state file
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <warn> failed to allocate link cache: (-10) Operation not supported
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth1): carrier is OFF
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth1): new Ethernet device (driver: '8139too' ifindex: 3)
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth1): now managed
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth1): bringing up device.
Feb 18 23:45:14 ubuntu kernel: [   83.935795] 8139too 0000:01:06.0: eth1: link down
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth1): preparing device.
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth1): deactivating device (reason 'managed') [2]
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:04.0/0000:01:06.0/net/eth1
Feb 18 23:45:14 ubuntu kernel: [   83.936405] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 18 23:45:14 ubuntu kernel: [   83.936999] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 18 23:45:14 ubuntu kernel: [   83.941925] type=1400 audit(1361259914.817:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1990 comm="apparmor_parser"
Feb 18 23:45:14 ubuntu kernel: [   83.942194] type=1400 audit(1361259914.817:5): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=1991 comm="apparmor_parser"
Feb 18 23:45:14 ubuntu kernel: [   83.942867] type=1400 audit(1361259914.817:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1991 comm="apparmor_parser"
Feb 18 23:45:14 ubuntu kernel: [   83.943129] type=1400 audit(1361259914.817:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=1991 comm="apparmor_parser"
Feb 18 23:45:14 ubuntu kernel: [   83.947999] type=1400 audit(1361259914.821:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1994 comm="apparmor_parser"
Feb 18 23:45:14 ubuntu kernel: [   83.948741] type=1400 audit(1361259914.825:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1994 comm="apparmor_parser"
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <warn> failed to allocate link cache: (-10) Operation not supported
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth0): carrier is OFF
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth0): now managed
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth0): bringing up device.
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth0): preparing device.
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> (eth0): deactivating device (reason 'managed') [2]
Feb 18 23:45:14 ubuntu kernel: [   83.953196] type=1400 audit(1361259914.829:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1996 comm="apparmor_parser"
Feb 18 23:45:14 ubuntu kernel: [   83.954841] r8169 0000:01:08.0: eth0: link down
Feb 18 23:45:14 ubuntu kernel: [   83.954846] r8169 0000:01:08.0: eth0: link down
Feb 18 23:45:14 ubuntu kernel: [   83.955285] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 18 23:45:14 ubuntu kernel: [   83.955568] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 18 23:45:14 ubuntu NetworkManager[1951]: <info> Added default wired connection 'Wired connection 2' for /sys/devices/pci0000:00/0000:00:04.0/0000:01:08.0/net/eth0
Feb 18 23:45:14 ubuntu kernel: [   83.960694] type=1400 audit(1361259914.837:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1992 comm="apparmor_parser"
Feb 18 23:45:14 ubuntu anacron[2073]: Anacron 2.3 started on 2013-02-18
Feb 18 23:45:14 ubuntu acpid: starting up with proc fs
Feb 18 23:45:14 ubuntu acpid: 35 rules loaded
Feb 18 23:45:14 ubuntu acpid: waiting for events: event logging is off
Feb 18 23:45:14 ubuntu cron[2044]: (CRON) INFO (pidfile fd = 3)
Feb 18 23:45:14 ubuntu cron[2078]: (CRON) STARTUP (fork ok)
Feb 18 23:45:14 ubuntu cron[2078]: (CRON) INFO (Running @reboot jobs)
Feb 18 23:45:14 ubuntu anacron[2073]: Will run job `cron.weekly' in 10 min.
Feb 18 23:45:14 ubuntu anacron[2073]: Will run job `cron.monthly' in 15 min.
Feb 18 23:45:14 ubuntu anacron[2073]: Jobs will be executed sequentially
Feb 18 23:45:15 ubuntu acpid: client connected from 2126[0:0]
Feb 18 23:45:15 ubuntu acpid: 1 client rule loaded
Feb 18 23:45:15 ubuntu udev-configure-printer: add /devices/pnp0/00:09/printer/lp0
Feb 18 23:45:15 ubuntu udev-configure-printer: Failed to get parent
Feb 18 23:45:15 ubuntu udev-configure-printer: add /module/lp
Feb 18 23:45:15 ubuntu udev-configure-printer: Failed to get parent
Feb 18 23:45:15 ubuntu dbus[1899]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Feb 18 23:45:15 ubuntu dbus[1899]: [system] Successfully activated service 'org.freedesktop.Accounts'
Feb 18 23:45:15 ubuntu accounts-daemon[2244]: started daemon version 0.6.15
Feb 18 23:45:15 ubuntu dbus[1899]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Feb 18 23:45:15 ubuntu dbus[1899]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Feb 18 23:45:16 ubuntu dbus[1899]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Feb 18 23:45:16 ubuntu dbus[1899]: [system] Successfully activated service 'org.freedesktop.UPower'
Feb 18 23:45:16 ubuntu kernel: [   85.674681] r8169 0000:01:08.0: eth0: link up
Feb 18 23:45:16 ubuntu kernel: [   85.675014] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> (eth0): carrier now ON (device state 20)
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Auto-activating connection 'Wired connection 2'.
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) starting connection 'Wired connection 2'
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> dhclient started with pid 2478
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Beginning IP6 addrconf.
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 18 23:45:16 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Feb 18 23:45:16 ubuntu dhclient: Copyright 2004-2011 Internet Systems Consortium.
Feb 18 23:45:16 ubuntu dhclient: All rights reserved.
Feb 18 23:45:16 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Feb 18 23:45:16 ubuntu dhclient: 
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Feb 18 23:45:16 ubuntu dhclient: Listening on LPF/eth0/00:50:8d:ca:5b:5d
Feb 18 23:45:16 ubuntu dhclient: Sending on   LPF/eth0/00:50:8d:ca:5b:5d
Feb 18 23:45:16 ubuntu dhclient: Sending on   Socket/fallback
Feb 18 23:45:16 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Feb 18 23:45:16 ubuntu dhclient: DHCPREQUEST of 192.168.1.13 on eth0 to 255.255.255.255 port 67
Feb 18 23:45:16 ubuntu dhclient: DHCPOFFER of 192.168.1.13 from 192.168.1.1
Feb 18 23:45:16 ubuntu dhclient: DHCPACK of 192.168.1.13 from 192.168.1.1
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> (eth0): DHCPv4 state changed preinit -> bound
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info>   address 192.168.1.13
Feb 18 23:45:16 ubuntu dhclient: bound to 192.168.1.13 -- renewal in 33779 seconds.
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info>   prefix 24 (255.255.255.0)
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info>   gateway 192.168.1.1
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info>   nameserver '192.168.1.1'
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Feb 18 23:45:16 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Feb 18 23:45:16 ubuntu avahi-daemon[1946]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.13.
Feb 18 23:45:16 ubuntu avahi-daemon[1946]: New relevant interface eth0.IPv4 for mDNS.
Feb 18 23:45:16 ubuntu avahi-daemon[1946]: Registering new address record for 192.168.1.13 on eth0.IPv4.
Feb 18 23:45:17 ubuntu NetworkManager[1951]: <info> DNS: starting dnsmasq...
Feb 18 23:45:17 ubuntu NetworkManager[1951]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Feb 18 23:45:17 ubuntu dnsmasq[2482]: started, version 2.59 cache disabled
Feb 18 23:45:17 ubuntu dnsmasq[2482]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Feb 18 23:45:17 ubuntu dnsmasq[2482]: using nameserver 192.168.1.1#53
Feb 18 23:45:17 ubuntu NetworkManager[1951]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Feb 18 23:45:18 ubuntu NetworkManager[1951]: <info> Policy set 'Wired connection 2' (eth0) as default for IPv4 routing and DNS.
Feb 18 23:45:18 ubuntu NetworkManager[1951]: <info> Activation (eth0) successful, device activated.
Feb 18 23:45:18 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Feb 18 23:45:18 ubuntu dbus[1899]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb 18 23:45:18 ubuntu dbus[1899]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb 18 23:45:18 ubuntu avahi-daemon[1946]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::250:8dff:feca:5b5d.
Feb 18 23:45:18 ubuntu avahi-daemon[1946]: New relevant interface eth0.IPv6 for mDNS.
Feb 18 23:45:18 ubuntu avahi-daemon[1946]: Registering new address record for fe80::250:8dff:feca:5b5d on eth0.*.
Feb 18 23:45:27 ubuntu kernel: [   96.352019] eth0: no IPv6 routers present
Feb 18 23:45:27 ubuntu ntpdate[2542]: adjust time server 91.189.94.4 offset 0.344816 sec
Feb 18 23:45:36 ubuntu NetworkManager[1951]: <info> (eth0): IP6 addrconf timed out or failed.
Feb 18 23:45:36 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Feb 18 23:45:36 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Feb 18 23:45:36 ubuntu NetworkManager[1951]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Feb 18 23:45:50 ubuntu dbus[1899]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Feb 18 23:45:50 ubuntu dbus[1899]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Feb 18 23:45:50 ubuntu rtkit-daemon[2685]: Successfully called chroot.
Feb 18 23:45:50 ubuntu rtkit-daemon[2685]: Successfully dropped privileges.
Feb 18 23:45:50 ubuntu rtkit-daemon[2685]: Successfully limited resources.
Feb 18 23:45:50 ubuntu rtkit-daemon[2685]: Running.
Feb 18 23:45:50 ubuntu rtkit-daemon[2685]: Watchdog thread running.
Feb 18 23:45:50 ubuntu rtkit-daemon[2685]: Canary thread running.
Feb 18 23:45:50 ubuntu rtkit-daemon[2685]: Successfully made thread 2683 of process 2683 (n/a) owned by '1000' high priority at nice level -11.
Feb 18 23:45:50 ubuntu rtkit-daemon[2685]: Supervising 1 threads of 1 processes of 1 users.
Feb 18 23:45:50 ubuntu dbus[1899]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Feb 18 23:45:50 ubuntu dbus[1899]: [system] Successfully activated service 'org.freedesktop.UDisks'
Feb 18 23:45:51 ubuntu rtkit-daemon[2685]: Successfully made thread 2716 of process 2683 (n/a) owned by '1000' RT at priority 5.
Feb 18 23:45:51 ubuntu rtkit-daemon[2685]: Supervising 2 threads of 1 processes of 1 users.
Feb 18 23:45:51 ubuntu rtkit-daemon[2685]: Successfully made thread 2717 of process 2683 (n/a) owned by '1000' RT at priority 5.
Feb 18 23:45:51 ubuntu rtkit-daemon[2685]: Supervising 3 threads of 1 processes of 1 users.
Feb 18 23:45:51 ubuntu rtkit-daemon[2685]: Successfully made thread 2724 of process 2724 (n/a) owned by '1000' high priority at nice level -11.
Feb 18 23:45:51 ubuntu rtkit-daemon[2685]: Supervising 4 threads of 2 processes of 1 users.
Feb 18 23:45:51 ubuntu pulseaudio[2724]: [pulseaudio] pid.c: Daemon already running.
Feb 18 23:45:51 ubuntu dbus[1899]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Feb 18 23:45:51 ubuntu blueman-mechanism: Starting blueman-mechanism 
Feb 18 23:45:51 ubuntu dbus[1899]: [system] Successfully activated service 'org.blueman.Mechanism'
Feb 18 23:45:51 ubuntu blueman-mechanism: loading Network 
Feb 18 23:45:51 ubuntu blueman-mechanism: loading Ppp 
Feb 18 23:45:51 ubuntu blueman-mechanism: loading RfKill 
Feb 18 23:45:51 ubuntu blueman-mechanism: loading Config 
Feb 18 23:46:21 ubuntu blueman-mechanism: Exiting 
```

---

### Post by bcbc on 2013-02-19
Hold down the SHIFT key to pop the Grub menu. Recovery mode uses nomodeset to boot - which is often needed for nvidia/radeon cards. Maybe this has something to do with your problme.

Did you see if there was a graphics driver available to install in 'additional-drivers'?

---

### Post by Yellow Pasque on 2013-02-19
It might be shutting down automatically due to overheating. Monitor your temps.

---

