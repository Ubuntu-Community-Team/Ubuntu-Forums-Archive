---
title: "no power management in 16.04 and no shutdown"
date: 2016-08-05
forum: General Help
---

### Post by badcomputerkarma on 2016-08-05
Hello
I have Ubuntu Mate installed on a new laptop. It is the only OS.
The system always freezes when I shut it down - except when I reboot! So I figure that the issue is about something that sets reboot and power off apart.
At the same time I notice that the system doesn't recognize the battery. It always claims that there is none - even when running from the battery. Maybe the two things belong together that a broken power-management hinders a proper shut down?
The system uses upower. Or let&#347; say it is supposed to do so, because when I check, I get this:
#upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          (null)
  power supply:         no
  updated:              Do 01 Jan 1970 01:00:00 CET (1470386643 seconds ago)
  has history:          no
  has statistics:       no
  unknown
    warning-level:       unknown

Then I checked acpi and I got numerous error notifications:
#dmesg | grep ACPI
[    0.000000] BIOS-e820: [mem 0x00000000845b2000-0x00000000845b2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000008744c000-0x0000000087b97fff] ACPI NVS
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F05B0 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x0000000087B62090 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x0000000087B7C2C0 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x0000000087B621C0 01A0FA (v02 ALASKA A M I    01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x0000000087B97F80 000040
[    0.000000] ACPI: APIC 0x0000000087B7C3D0 0000BC (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x0000000087B7C490 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x0000000087B7C4D8 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x0000000087B7C578 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x0000000087B7C5B8 000038 (v01 ALASKA A M I    01072009 AMI. 0005000B)
[    0.000000] ACPI: SSDT 0x0000000087B7C5F0 00036D (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x0000000087B7C960 001100 (v01 INTEL  PtidDevc 00001000 INTL 20120913)
[    0.000000] ACPI: DBGP 0x0000000087B7DA60 000034 (v01 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: DBG2 0x0000000087B7DA98 000054 (v00 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x0000000087B7DAF0 001658 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x0000000087B7F148 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: SSDT 0x0000000087B7F190 000E73 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: DMAR 0x0000000087B80008 0000A8 (v01 INTEL  SKL      00000001 INTL 00000001)
[    0.000000] ACPI: ASF! 0x0000000087B800B0 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000043] ACPI: Core revision 20150930
[    0.005265] ACPI Error: [_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20150930/dswload-210)
[    0.005270] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20150930/psobject-227)
[    0.005522] ACPI Exception: AE_NOT_FOUND, [DSDT] table load failed (20150930/tbxfload-163)
[    0.005532] ACPI Error: [\_SB_.PCI0.SAT0] Namespace lookup failure, AE_NOT_FOUND (20150930/dswload-210)
[    0.005535] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20150930/psobject-227)
[    0.005538] ACPI Exception: AE_NOT_FOUND, (SSDT:SataTabl) while loading table (20150930/tbxfload-193)
[    0.005708] ACPI Error: [\_SB_.PCI0.PEG0] Namespace lookup failure, AE_NOT_FOUND (20150930/dswload-210)
[    0.005710] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20150930/psobject-227)
[    0.005719] ACPI Exception: AE_NOT_FOUND, (SSDT: SaSsdt ) while loading table (20150930/tbxfload-193)
[    0.005758] ACPI Error: [\_PR_.CPU0] Namespace lookup failure, AE_NOT_FOUND (20150930/dswload-210)
[    0.005761] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20150930/psobject-227)
[    0.005767] ACPI Exception: AE_NOT_FOUND, (SSDT: CpuSsdt) while loading table (20150930/tbxfload-193)
[    0.005769] ACPI Error: 4 table load failures, 1 successful (20150930/tbxfload-214)
[    0.106358] PM: Registering ACPI NVS region [mem 0x845b2000-0x845b2fff] (4096 bytes)
[    0.106360] PM: Registering ACPI NVS region [mem 0x8744c000-0x87b97fff] (7651328 bytes)
[    0.129971] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.129973] ACPI: bus type PCI registered
[    0.129975] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.142147] ACPI: Added _OSI(Module Device)
[    0.142149] ACPI: Added _OSI(Processor Device)
[    0.142150] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.142151] ACPI: Added _OSI(Processor Aggregator Device)
[    0.142388] ACPI Error: [ECR1] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142392] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142398] ACPI Error: [PCHV] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142400] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142405] ACPI Error: [SMD0] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142407] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142411] ACPI Error: [SMD1] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142413] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142418] ACPI Error: [SMD2] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142420] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142424] ACPI Error: [SMD3] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142426] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142430] ACPI Error: [SMD4] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142432] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142436] ACPI Error: [SMD5] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142438] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142442] ACPI Error: [SMD6] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142444] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142449] ACPI Error: [SMD7] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142450] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142454] ACPI Error: [SMD8] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142456] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142461] ACPI Error: [SMD9] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142463] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142467] ACPI Error: [SMDA] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142469] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142473] ACPI Error: [USTP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142475] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142479] ACPI Error: [S0ID] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    0.142481] ACPI Error: Method parse/execution failed [\] (Node c1d2df94), AE_NOT_FOUND (20150930/psparse-542)
[    0.142511] ACPI: Executed 20 blocks of module-level executable AML code
[    0.142629] ACPI: Interpreter enabled
[    0.142635] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150930/hwxface-580)
[    0.142637] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
[    0.142639] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20150930/hwxface-580)
[    0.142642] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S4_] (20150930/hwxface-580)
[    0.142643] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S5_] (20150930/hwxface-580)
[    0.142645] ACPI: (supports S0)
[    0.142646] ACPI: Using IOAPIC for interrupt routing
[    0.142656] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.143127] ACPI: bus type USB registered
[    0.143268] PCI: Using ACPI for IRQ routing
[    0.143294] ACPI: \: failed to evaluate _DSM (0x1001)
[    0.213908] pnp: PnP ACPI init
[    0.213922] pnp: PnP ACPI: found 0 devices
[    0.213926] PnPBIOS: Disabled by ACPI PNP
[    0.761145] ACPI: Power Button [PWRF]
[    0.796994] ACPI: \: failed to evaluate _DSM (0x1001)

Being a newbie in Linux I don't really understand anything. But it doesn't look good. 
What can I do? Any Ideas?
Yours
badcomputerkarma

---

