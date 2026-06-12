---
title: "kworker stuck at 85%+, new install, new hardware"
date: 2018-10-19
forum: General Help
---

### Post by Peter_Brandon on 2018-10-19
So, ever since I started using Linux on a new Dell system (i7-8700 chip; Precision 3630), I've had a kworker process that is permanently at or above 85%.  I initially tried to work w/ Qubes on the new computer, and kworker was 85%+ there as well (under Fedora), but decided Qubes was too inefficient for my needs and switched to Ubuntu with a KDE desktop.  I tried to figure out what was running the process.  If I'm reading the following correctly, PPID is the parent process ID, so my out of control kworker is being called by PID=2 or kthreadd, which is being called by PID=1, /sbin/init, which I gather is the process that starts up the OS.  I don't know what +kac means below (this is what I get running mainline kernel 4.18; in 4.15 there's no +kac, but everything else is the same).  Anyway, a worker thread for the initializing process of the system seems important.  Incidentally, there seems to be no way to kill the kworker process, even as root.  pb@pb-tower:~/Downloads$ ps -elf F S UID        PID  PPID  C PRI  NI ADDR SZ WCHAN  STIME TTY          TIME CMD 4 S root         1     0  0  80   0 - 56471 -      18:30 ?        00:00:01 /sbin/init splash 1 S root         2     0  0  80   0 -     0 -      18:30 ?        00:00:00 [kthreadd]   1 R root        85     2 63  80   0 -     0 -      18:30 ?        00:03:03 [kworker/0:1+kac]   Another thing I tried is, as already hinted above, mainline upstream kernels.  kworker is at 85%+ for 4.15 and 4.16 (I used the most recent stable version of 4.16 and above as of about a week ago).  Under 4.17 and 4.18, kworker slows down to 65%.  So something in the kernel software makes a difference, though hardly removes the problem.  I'm not sure I can run VirtualBox, which I need, in kernels above 4.15, and I wonder about the security of upstream kernels so it's probably not worth it to switch for a 20% decrease.  What this suggests is that it will be a long time before this problem goes away due to a kernel upgrade, unless the kernel developers specifically address it.  I've also tried the full set of grub configuration changes that people have suggested: noapic; pci=routeirq; pc=noacpi; acpi=off; and irqpoll.  The system doesn't but on the ones that mention irq.  As for the rest, the problem remains or, with noapic, kworker decreases by 5% to about 79% permanently.  Maybe the problem is related to ACPI or other errors I encounter at boot-up.  Dmesg says the following.  Um, yeah, I'm not running secureboot.  ```
[    0.097480] ACPI: Dynamic OEM Table Load: [    0.097480] ACPI: SSDT 0xFFFFA07F57173000 000317 (v02 PmRef  ApHwp    00003000 INTL 20160527) [    0.097480] ACPI: Executed 1 blocks of module-level executable AML code [    0.100180] ACPI: Dynamic OEM Table Load: [    0.100186] ACPI: SSDT 0xFFFFA07F577EF400 00030A (v02 PmRef  ApCst    00003000 INTL 20160527) [    0.100473] ACPI: Executed 1 blocks of module-level executable AML code [    0.102187] ACPI: Interpreter enabled [    0.102222] ACPI: (supports S0 S3 S4 S5) [    0.102223] ACPI: Using IOAPIC for interrupt routing [    0.102275] HEST: Table parsing has been initialized. [    0.102277] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug [    0.103580] ACPI: GPE 0x20 active on init [    0.104031] ACPI Error: No handler for Region [WST1] (        (ptrval)) [GenericSerialBus] (20170831/evregion-166) [    0.104035] ACPI Error: Region GenericSerialBus (ID=9) has no handler (20170831/exfldio-299) [    0.104040]                 Initialized Local Variables for Method [PAS1]: [    0.104041]   Local0:         (ptrval)            Integer 0000000000000001 [    0.104045] No Arguments are initialized for method [PAS1] [    0.104046] ACPI Error: Method parse/execution failed \_SB.PCI0.I2C0.PAS1, AE_NOT_EXIST (20170831/psparse-550) [    0.104052] ACPI Error: Method parse/execution failed \_GPE._L20, AE_NOT_EXIST (20170831/psparse-550) [    0.104058] ACPI Exception: AE_NOT_EXIST, while evaluating GPE method [_L20] (20170831/evgpe-646) [    0.104005] ACPI: GPE 0x6F active on init [    0.104005] ACPI: Enabled 10 GPEs in block 00 to 7F [    0.212126] ACPI: Power Resource [USBC] (on)     [    0.444270] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot [    0.444270] pci 0000:06:00.1: [1033:00e0] type 00 class 0x0c0320 [    0.444270] pci 0000:06:00.1: reg 0x10: [mem 0xa2000000-0xa20000ff] [    0.444278] pci 0000:06:00.1: supports D1 D2 [    0.444278] pci 0000:06:00.1: PME# supported from D0 D1 D2 D3hot [    0.444278] pci 0000:05:00.0: PCI bridge to [bus 06] [    0.444278] pci 0000:05:00.0:   bridge window [mem 0xa2000000-0xa20fffff] [    0.456183] ACPI: PCI Interrupt Link [LNKA] (IRQs) *0 [    0.456183] ACPI: PCI Interrupt Link [LNKB] (IRQs) *1 [    0.456183] ACPI: PCI Interrupt Link [LNKC] (IRQs) *0 [    0.456183] ACPI: PCI Interrupt Link [LNKD] (IRQs) *1 [    0.456183] ACPI: PCI Interrupt Link [LNKE] (IRQs) *1 [    0.456183] ACPI: PCI Interrupt Link [LNKF] (IRQs) *1 [    0.456183] ACPI: PCI Interrupt Link [LNKG] (IRQs) *1 [    0.456183] ACPI: PCI Interrupt Link [LNKH] (IRQs) *1 [    0.464184] SCSI subsystem initialized [    0.464186] libata version 3.00 loaded. [    0.464186] pci 0000:00:02.0: vgaarb: setting as boot VGA device   [    1.225495] Scanning for low memory corruption every 60 seconds [    1.226265] Initialise system trusted keyrings [    1.226271] Key type blacklist registered [    1.226399] workingset: timestamp_bits=36 max_order=23 bucket_order=0 [    1.227127] zbud: loaded [    1.227482] squashfs: version 4.0 (2009/01/31) Phillip Lougher [    1.227769] fuse init (API version 7.26) [    1.233972] Key type asymmetric registered [    1.233973] Asymmetric key parser 'x509' registered [    1.233991] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 246) [    1.234105] io scheduler noop registered [    1.234105] io scheduler deadline registered [    1.234131] io scheduler cfq registered (default) [    1.238792] pcieport 0000:00:1b.0: AER enabled with IRQ 122 [    1.238819] pcieport 0000:00:1b.4: AER enabled with IRQ 123 [    1.238845] pcieport 0000:00:1d.2: AER enabled with IRQ 124 [    1.238863] dpc 0000:00:1b.0:pcie010: DPC error containment capabilities: Int Msg #0, RPExt+ PoisonedTLP+ SwTrigger+ RP PIO Log 4, DL_ActiveErr+ [    1.238874] dpc 0000:00:1b.4:pcie010: DPC error containment capabilities: Int Msg #0, RPExt+ PoisonedTLP+ SwTrigger+ RP PIO Log 4, DL_ActiveErr+ [    1.238886] dpc 0000:00:1d.2:pcie010: DPC error containment capabilities: Int Msg #0, RPExt+ PoisonedTLP+ SwTrigger+ RP PIO Log 4, DL_ActiveErr+ [    1.238925] efifb: probing for efifb   [    1.378346] ACPI: Thermal Zone [TZ00] (28 C) [    1.378390] ERST: Error Record Serialization Table (ERST) support is initialized. [    1.378391] pstore: using zlib compression [    1.378393] pstore: Registered erst as persistent store backend [    1.378456] GHES: APEI firmware first mode is enabled by APEI bit. [    1.378659] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled [    1.400977] 00:01: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A [    1.405952] Linux agpgart interface v0.103 [    1.433815] tpm_tis MSFT0101:00: 2.0 TPM (device-id 0xFC, rev-id 1) [    1.444950] tpm tpm0: A TPM error (2314) occurred continue selftest [    1.798436] loop: module loaded   
```   Anyone have any suggestions of anything else I might try?

---

### Post by Peter_Brandon on 2018-10-19
Wow, I found the solution to my problem not long after posting this (despite having looked for weeks beforehand).  I looked more into ACPI and GPE issues and found this:  

[https://superuser.com/questions/1117992/acpi-exception-ae-not-found-while-evaluating-gpe-method-floods-syslog](https://superuser.com/questions/1117992/acpi-exception-ae-not-found-while-evaluating-gpe-method-floods-syslog)

Apparently there was a known bug (reported) between the Skylake chipsets and linux.  Well, my chip is Coffee Lake and is exhibiting the same problem, so am guessing it wasn't fixed.

The solution is to run the following as root (sudo won't do):

echo "disable" > /sys/firmware/acpi/interrupts/gpe6F

I don't really know what this means or does.  If someone can explain this, I'm all ears.  For now I'm just happy I found something that works.

---

### Post by markackerman8@gmail.com on 2018-12-28
running as root
```
sudo su
```

```
 echo "disable" > /sys/firmware/acpi/interrupts/gpe6F
```

worked for me as well ... brought it from 15-20% to less than 1%

---

### Post by yetimon_64 on 2018-12-28
> **Peter_Brandon said:**
> ...
The solution is to run the following as root (sudo won't do):

echo "disable" > /sys/firmware/acpi/interrupts/gpe6F...

The correct command syntax for this situation using sudo only (no root prompt) is ...
```
echo "disable" | sudo tee -a /sys/firmware/acpi/interrupts/gpe6F
```

You don't need a root terminal when you construct the command as shown above.
See the rootsudo documentation link (1st green link) in my sig line for the source of the above information. Look under the section titled "Downsides of using sudo" for the explanation.

Cheers, yeti.

---

