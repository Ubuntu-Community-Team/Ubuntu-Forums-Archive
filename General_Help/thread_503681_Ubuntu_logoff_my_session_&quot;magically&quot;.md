---
title: "Ubuntu logoff my session &quot;magically&quot;"
date: 2007-07-18
forum: General Help
---

### Post by pablosaro on 2007-07-18
Hi all!
I've got a big problem. Sometimes my Ubuntu logoff my session magically and automatically.
I use the PC intensively to figure out if the problem is caused by software, but I realize that is a random behavior. So, I discarded software problems. Hardware is new, I bought it a few days ago.
For example, I'm using Firefox, Terminal and Skype and suddenly my screen turns black and a few seconds later I'm in the login screen. I'm pulling out my hair!
I found in my dmesg the following:
```
[17610252.660000] ACPI: PCI interrupt for device 0000:00:12.0 disabled
[17610254.324000] Freezing cpus ...
[17610254.360000] CPU 1 is now offline
[17610254.360000] SMP alternatives: switching to UP code
[17610254.364000] CPU1 is down
[17610254.364000] Stopping tasks: ===================================================================================================|
[17610254.520000] pnp: Device 00:0b disabled.
[17610254.520000] pnp: Device 00:06 disabled.
[17610254.528000] ACPI: PCI interrupt for device 0000:04:01.0 disabled
[17610254.544000] ACPI: PCI interrupt for device 0000:00:10.4 disabled
[17610254.560000] ACPI: PCI interrupt for device 0000:00:10.3 disabled
[17610254.576000] ACPI: PCI interrupt for device 0000:00:10.2 disabled
[17610254.592000] ACPI: PCI interrupt for device 0000:00:10.1 disabled
[17610254.608000] ACPI: PCI interrupt for device 0000:00:10.0 disabled
[17610254.624000] Back to C!
[17610288.624000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17610288.624000] PM: Writing back config space on device 0000:00:02.0 at offset f (was 3010a, writing 30109)
[17610288.624000] PM: Writing back config space on device 0000:00:02.0 at offset 1 (was 100104, writing 100504)
[17610288.624000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 169
[17610288.624000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17610288.624000] PM: Writing back config space on device 0000:00:03.0 at offset f (was 3010a, writing 30101)
[17610288.624000] PM: Writing back config space on device 0000:00:03.0 at offset 1 (was 100104, writing 100504)
[17610288.624000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 177
[17610288.624000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[17610288.624000] PM: Writing back config space on device 0000:00:0f.0 at offset f (was 205, writing 201)
[17610288.624000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 209
[17610288.624000] PM: Writing back config space on device 0000:00:0f.1 at offset f (was ff, writing 0)
[17610288.640000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 217
[17610288.640000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
[17610288.640000] usb usb1: root hub lost power or was reset
[17610288.656000] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 225
[17610288.656000] PCI: Via IRQ fixup for 0000:00:10.1, from 5 to 1
[17610288.656000] usb usb2: root hub lost power or was reset
[17610288.672000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 209
[17610288.672000] PCI: Via IRQ fixup for 0000:00:10.2, from 3 to 1
[17610288.672000] usb usb3: root hub lost power or was reset
[17610288.688000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 233
[17610288.688000] PCI: Via IRQ fixup for 0000:00:10.3, from 10 to 9
[17610288.688000] usb usb4: root hub lost power or was reset
[17610288.704000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 209
[17610288.704000] PCI: Via IRQ fixup for 0000:00:10.4, from 3 to 1
[17610288.704000] PM: Writing back config space on device 0000:00:10.4 at offset 3 (was 804008, writing 804020)
[17610288.704000] usb usb5: root hub lost power or was reset
[17610288.704000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17610288.704000] PM: Writing back config space on device 0000:00:12.0 at offset f (was 803010b, writing 8030109)
[17610288.704000] PM: Writing back config space on device 0000:00:12.0 at offset 1 (was 2100117, writing 2100113)
[17610288.704000] PM: Writing back config space on device 0000:00:13.0 at offset 1 (was 20100001, writing 20100106)
[17610288.704000] PCI: Setting latency timer of device 0000:00:13.0 to 64
[17610288.704000] PM: Writing back config space on device 0000:04:01.0 at offset f (was 100, writing 102)
[17610288.704000] PM: Writing back config space on device 0000:04:01.0 at offset 4 (was 4, writing fbffc004)
[17610288.704000] PM: Writing back config space on device 0000:04:01.0 at offset 3 (was 0, writing 8)
[17610288.704000] PM: Writing back config space on device 0000:04:01.0 at offset 1 (was 100000, writing 100002)
[17610288.704000] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 50
[17610288.704000] PCI: Setting latency timer of device 0000:04:01.0 to 64
[17610288.752000] pnp: Device 00:06 activated.
[17610288.752000] pnp: Failed to activate device 00:09.
[17610288.752000] pnp: Failed to activate device 00:0a.
[17610288.756000] pnp: Device 00:0b activated.
[17610289.620000] Restarting tasks... done
[17610289.632000] Thawing cpus ...
[17610289.672000] SMP alternatives: switching to SMP code
[17610289.672000] Booting processor 1/1 eip 3000
[17610289.680000] Initializing CPU#1
[17610289.764000] Calibrating delay using timer specific routine.. 6001.02 BogoMIPS (lpj=12002045)
[17610289.764000] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e59d 00000000 00000001
[17610289.764000] CPU: After vendor identify, caps: bfebfbff 20000000 00000000 00000000 0000e59d 00000000 00000001
[17610289.764000] monitor/mwait feature present.
[17610289.764000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17610289.764000] CPU: L2 cache: 2048K
[17610289.764000] CPU: Hyper-Threading is disabled
[17610289.764000] CPU: After all inits, caps: bfebfbff 20000000 00000000 00000180 0000e59d 00000000 00000001
[17610289.764000] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[17610289.768000] APIC error on CPU1: 00(40)
[17610289.768000] CPU1 is up
[17610319.632000] ata2: command 0xc8 timeout, stat 0x50 host_stat 0x1
[17610319.632000] ata2: status=0x50 { DriveReady SeekComplete }
[17610319.632000] ata2: error=0x01 { AddrMarkNotFound }
[17610319.632000] sda: Current: sense key: No Sense
[17610319.632000]     Additional sense: No additional sense information
[17610319.632000] Info fld=0x1
[17610319.812000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17610319.812000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 233
[17610319.820000] eth0: VIA Rhine II at 0x1d000, 00:1b:fc:19:41:94, IRQ 233.
[17610319.820000] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[17610319.904000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17610321.272000] ACPI: Power Button (FF) [PWRF]
[17610321.272000] ACPI: Power Button (CM) [PWRB]
[17610322.340000] ACPI: Processor [CPU1] (supports 16 throttling states)
[17610322.340000] ACPI: Processor [CPU2] (supports 16 throttling states)
[17610322.340000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17610322.340000] ACPI: Getting cpuindex for acpiid 0x3
[17610322.340000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17610322.340000] ACPI: Getting cpuindex for acpiid 0x4
[17610330.824000] eth0: no IPv6 routers present
[17662029.096000] smb_add_request: request [d9288e80, mid=149] timed out!
[17665154.924000] smb_add_request: request [d9288e80, mid=150] timed out!
[17665184.924000] smb_add_request: request [d9288e80, mid=151] timed out!
[17665188.128000] smb_add_request: request [d9288d80, mid=152] timed out!
[17665189.076000] smb_add_request: request [d9288c80, mid=157] timed out!
```
I don't know what's going up!
Please if anybody can figure out what is the problem let me know.
Thanks a lot!
You can email me directly to pablosaro at gmail dot com
Pablo

---

### Post by alek01 on 2007-12-14
Pablo,
Have you eventually solved you "auto logoff" problem?
I have a similar issue but somehow less bad. My system logs off instead of going on the screen saver. So when I want to make a large download overnight or want my system up for some reason when I come back I get the Login screen.
Any idea.
Muchas gracias!
Alek

---

### Post by pablosaro on 2008-04-30
Hi everyone,

Sorry for this late update.
It seems to be an ACPI problem, I guess. I tried re installing Ubuntu again and again but the problem persists with the same hardware.
I changed the hardware and then I installed Ubuntu with the same media source and everything gone well.
I have no much information about my hardware changes (Sorry :neutral: ).

Pablo

---

