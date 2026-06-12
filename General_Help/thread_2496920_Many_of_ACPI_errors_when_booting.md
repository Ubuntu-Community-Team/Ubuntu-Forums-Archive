---
title: "Many of ACPI errors when booting"
date: 2024-04-17
forum: General Help
---

### Post by 79manuman on 2024-04-17
Hello,

I've been having trouble with Linux since my first installation. (ubuntu desktop 22.04.4 LTS kernel version: 6.5.0-27-generic)
Not only that I get a lot of ACPI Errors when booting, but my system also freezes regularly when watching Youtoube videos.
I have updated my Bios, checked if my memory and harddrive are ok. No problem there.
After researching a little I found that the random freezes are linked to the c-states so I changed the GRUB and set the C-state to 1 (intel_idle.max_cstate=1). This reduced the freezes significantly but did not eliminate them and my pc is running on all cylinders now.
I was wondering if the ACPI errors are linked to these crashes.
Any help or advise would be appreciated. Thanks to you all in advance!

Nolito
-------------------------------------------------------------------------------


```

nolito@Nolito-MINIPC-PN64:~$ inxi -Fxxxz
System:
  Kernel: 6.5.0-27-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    tk: GTK 3.24.33 wm: gnome-shell dm: GDM3 42.0
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Mini-pc System: ASUSTeK product: MINIPC PN64 v: N/A
    serial: <superuser required>
  Mobo: ASUSTeK model: PN64 serial: <superuser required> UEFI: ASUSTeK
    v: 2.14.00 date: 09/20/2023
CPU:
  Info: 14-core (6-mt/8-st) model: 12th Gen Intel Core i7-12700H bits: 64
    type: MST AMCP smt: enabled arch: Alder Lake rev: 3 cache: L1: 1.2 MiB
    L2: 11.5 MiB L3: 24 MiB
  Speed (MHz): avg: 3280 high: 3600 min/max: 400/4600:4700:3500 cores:
    1: 3600 2: 3600 3: 3600 4: 3600 5: 3600 6: 3600 7: 3600 8: 3600 9: 3600
    10: 3600 11: 3600 12: 3600 13: 2800 14: 2800 15: 2800 16: 2800 17: 2800
    18: 2800 19: 2800 20: 2800 bogomips: 107520
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Alder Lake-P Integrated Graphics vendor: ASUSTeK
    driver: i915 v: kernel ports: active: HDMI-A-1
    empty: DP-1, DP-2, HDMI-A-2, HDMI-A-3 bus-ID: 00:02.0 chip-ID: 8086:46a6
    class-ID: 0300
  Display: wayland server: X.org v: 1.21.1.4 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: i915 display-ID: 0
  Monitor-1: HDMI-A-1 model: VA24D serial: <filter> res: 1920x1080 dpi: 93
    size: 527x296mm (20.7x11.7") diag: 604mm (23.8") modes: max: 1920x1080
    min: 720x400
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2)
    v: 4.6 Mesa 24.0.5 - kisak-mesa PPA direct render: Yes
Audio:
  Device-1: Intel Alder Lake PCH-P High Definition Audio vendor: ASUSTeK
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3 chip-ID: 8086:51c8
    class-ID: 0403
  Sound Server-1: ALSA v: k6.5.0-27-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Ethernet I225-V vendor: ASUSTeK driver: igc v: kernel pcie:
    speed: 5 GT/s lanes: 1 port: N/A bus-ID: 01:00.0 chip-ID: 8086:15f3
    class-ID: 0200
  IF: enp1s0 state: down mac: <filter>
  Device-2: Intel Wi-Fi 6 AX210/AX211/AX411 160MHz driver: iwlwifi
    v: kernel pcie: speed: 5 GT/s lanes: 1 bus-ID: 02:00.0 chip-ID: 8086:2725
    class-ID: 0280
  IF: wlp2s0 state: up mac: <filter>
Bluetooth:
  Device-1: Intel AX210 Bluetooth type: USB driver: btusb v: 0.8
    bus-ID: 3-10:3 chip-ID: 8087:0032 class-ID: e001
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
RAID:
  Hardware-1: Intel Volume Management Device NVMe RAID Controller driver: vmd
    v: 0.6 port: N/A bus-ID: 00:0e.0 chip-ID: 8086:467f rev: class-ID: 0104
Drives:
  Local Storage: total: 931.51 GiB used: 28.91 GiB (3.1%)
  ID-1: /dev/sda vendor: Crucial model: CT1000BX500SSD1 size: 931.51 GiB
    speed: 6.0 Gb/s type: SSD serial: <filter> rev: 056 scheme: GPT
Partition:
  ID-1: / size: 915.32 GiB used: 28.9 GiB (3.2%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) priority: -2
    file: /swapfile
Sensors:
  System Temperatures: cpu: 79.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 465 Uptime: 3m wakeups: 0 Memory: 31.07 GiB
  used: 4.24 GiB (13.6%) Init: systemd v: 249 runlevel: 5 Compilers:
  gcc: 11.4.0 alt: 11 Packages: 1947 apt: 1903 flatpak: 24 snap: 20
  Shell: Bash v: 5.1.16 running-in: gnome-terminal inxi: 3.3.13

-----------------------------------------------------------------------------------------------------
nolito@Nolito-MINIPC-PN64:~$ sudo dmesg | grep ACPI
[    0.000000] BIOS-e820: [mem 0x0000000042345000-0x0000000042458fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000042459000-0x0000000042651fff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x0000000042345000-0x0000000042458fff] ACPI data
[    0.000000] reserve setup_data: [mem 0x0000000042459000-0x0000000042651fff] ACPI NVS
[    0.000000] efi: ACPI=0x42458000 ACPI 2.0=0x42458014 TPMFinalLog=0x4257f000 SMBIOS=0x43c5d000 SMBIOS 3.0=0x43c5c000 MEMATTR=0x3a876018 ESRT=0x3d2f4798 MOKvar=0x43cc7000 RNG=0x42397c18 TPMEventLog=0x2c6af018 
[    0.009045] ACPI: Early table checksum verification disabled
[    0.009048] ACPI: RSDP 0x0000000042458014 000024 (v02 ALASKA)
[    0.009053] ACPI: XSDT 0x0000000042457728 00010C (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.009060] ACPI: FACP 0x0000000042452000 000114 (v06 ALASKA A M I    01072009 AMI  01000013)
[    0.009066] ACPI: DSDT 0x00000000423BB000 096238 (v02 ALASKA A M I    01072009 INTL 20200717)
[    0.009069] ACPI: FACS 0x0000000042651000 000040
[    0.009073] ACPI: SSDT 0x0000000042453000 0032A4 (v02 DptfTb DptfTabl 00001000 INTL 20200717)
[    0.009076] ACPI: FIDT 0x00000000423BA000 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.009080] ACPI: WSMT 0x0000000042394000 000028 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.009083] ACPI: SSDT 0x00000000423B8000 00038C (v02 PmaxDv Pmax_Dev 00000001 INTL 20200717)
[    0.009087] ACPI: SSDT 0x00000000423B2000 005D34 (v02 CpuRef CpuSsdt  00003000 INTL 20200717)
[    0.009090] ACPI: SSDT 0x00000000423AF000 002915 (v02 SaSsdt SaSsdt   00003000 INTL 20200717)
[    0.009093] ACPI: SSDT 0x00000000423AB000 0033E9 (v02 INTEL  IgfxSsdt 00003000 INTL 20200717)
[    0.009096] ACPI: SSDT 0x000000004239D000 00D487 (v02 INTEL  TcssSsdt 00001000 INTL 20200717)
[    0.009100] ACPI: HPET 0x000000004239C000 000038 (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.009103] ACPI: APIC 0x000000004239B000 0001DC (v05 ALASKA A M I    01072009 AMI  01000013)
[    0.009106] ACPI: MCFG 0x000000004239A000 00003C (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.009109] ACPI: SSDT 0x0000000042398000 001F1A (v02 ALASKA Ther_Rvp 00001000 INTL 20200717)
[    0.009113] ACPI: NHLT 0x0000000042396000 00002D (v00 ALASKA A M I    01072009 AMI  01000013)
[    0.009116] ACPI: LPIT 0x0000000042395000 0000CC (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.009119] ACPI: SSDT 0x0000000042391000 002A83 (v02 ALASKA PtidDevc 00001000 INTL 20200717)
[    0.009122] ACPI: SSDT 0x000000004238E000 002357 (v02 ALASKA TbtTypeC 00000000 INTL 20200717)
[    0.009125] ACPI: DBGP 0x000000004238D000 000034 (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.009129] ACPI: DBG2 0x000000004238C000 000054 (v00 ALASKA A M I    01072009 AMI  01000013)
[    0.009132] ACPI: DMAR 0x000000004238B000 000088 (v02 INTEL  EDK2     00000002      01000013)
[    0.009135] ACPI: FPDT 0x000000004238A000 000044 (v01 ALASKA A M I    01072009 AMI  01000013)
[    0.009139] ACPI: SSDT 0x0000000042389000 000C0C (v02 INTEL  xh_adlLP 00000000 INTL 20200717)
[    0.009142] ACPI: SSDT 0x0000000042385000 003AEA (v02 SocGpe SocGpe   00003000 INTL 20200717)
[    0.009145] ACPI: SSDT 0x0000000042381000 0039DA (v02 SocCmn SocCmn   00003000 INTL 20200717)
[    0.009148] ACPI: SSDT 0x0000000042380000 000144 (v02 Intel  ADebTabl 00001000 INTL 20200717)
[    0.009152] ACPI: BGRT 0x000000004237F000 000038 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.009155] ACPI: TPM2 0x000000004237E000 00004C (v04 ALASKA A M I    00000001 AMI  00000000)
[    0.009158] ACPI: BERT 0x000000004237D000 000030 (v01 INTEL  EDK2     00000001 INTL 00000001)
[    0.009162] ACPI: PHAT 0x000000004237C000 0005B1 (v01 ALASKA A M I    00000005 MSFT 0100000D)
[    0.009164] ACPI: Reserving FACP table memory at [mem 0x42452000-0x42452113]
[    0.009166] ACPI: Reserving DSDT table memory at [mem 0x423bb000-0x42451237]
[    0.009167] ACPI: Reserving FACS table memory at [mem 0x42651000-0x4265103f]
[    0.009168] ACPI: Reserving SSDT table memory at [mem 0x42453000-0x424562a3]
[    0.009169] ACPI: Reserving FIDT table memory at [mem 0x423ba000-0x423ba09b]
[    0.009170] ACPI: Reserving WSMT table memory at [mem 0x42394000-0x42394027]
[    0.009171] ACPI: Reserving SSDT table memory at [mem 0x423b8000-0x423b838b]
[    0.009172] ACPI: Reserving SSDT table memory at [mem 0x423b2000-0x423b7d33]
[    0.009172] ACPI: Reserving SSDT table memory at [mem 0x423af000-0x423b1914]
[    0.009173] ACPI: Reserving SSDT table memory at [mem 0x423ab000-0x423ae3e8]
[    0.009174] ACPI: Reserving SSDT table memory at [mem 0x4239d000-0x423aa486]
[    0.009175] ACPI: Reserving HPET table memory at [mem 0x4239c000-0x4239c037]
[    0.009176] ACPI: Reserving APIC table memory at [mem 0x4239b000-0x4239b1db]
[    0.009177] ACPI: Reserving MCFG table memory at [mem 0x4239a000-0x4239a03b]
[    0.009178] ACPI: Reserving SSDT table memory at [mem 0x42398000-0x42399f19]
[    0.009178] ACPI: Reserving NHLT table memory at [mem 0x42396000-0x4239602c]
[    0.009179] ACPI: Reserving LPIT table memory at [mem 0x42395000-0x423950cb]
[    0.009180] ACPI: Reserving SSDT table memory at [mem 0x42391000-0x42393a82]
[    0.009181] ACPI: Reserving SSDT table memory at [mem 0x4238e000-0x42390356]
[    0.009182] ACPI: Reserving DBGP table memory at [mem 0x4238d000-0x4238d033]
[    0.009183] ACPI: Reserving DBG2 table memory at [mem 0x4238c000-0x4238c053]
[    0.009184] ACPI: Reserving DMAR table memory at [mem 0x4238b000-0x4238b087]
[    0.009185] ACPI: Reserving FPDT table memory at [mem 0x4238a000-0x4238a043]
[    0.009185] ACPI: Reserving SSDT table memory at [mem 0x42389000-0x42389c0b]
[    0.009186] ACPI: Reserving SSDT table memory at [mem 0x42385000-0x42388ae9]
[    0.009187] ACPI: Reserving SSDT table memory at [mem 0x42381000-0x423849d9]
[    0.009188] ACPI: Reserving SSDT table memory at [mem 0x42380000-0x42380143]
[    0.009189] ACPI: Reserving BGRT table memory at [mem 0x4237f000-0x4237f037]
[    0.009190] ACPI: Reserving TPM2 table memory at [mem 0x4237e000-0x4237e04b]
[    0.009190] ACPI: Reserving BERT table memory at [mem 0x4237d000-0x4237d02f]
[    0.009191] ACPI: Reserving PHAT table memory at [mem 0x4237c000-0x4237c5b0]
[    0.047700] ACPI: PM-Timer IO Port: 0x1808
[    0.047709] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.047710] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.047711] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.047712] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.047713] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.047713] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.047714] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.047715] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.047715] ACPI: LAPIC_NMI (acpi_id[0x09] high edge lint[0x1])
[    0.047716] ACPI: LAPIC_NMI (acpi_id[0x0a] high edge lint[0x1])
[    0.047716] ACPI: LAPIC_NMI (acpi_id[0x0b] high edge lint[0x1])
[    0.047717] ACPI: LAPIC_NMI (acpi_id[0x0c] high edge lint[0x1])
[    0.047718] ACPI: LAPIC_NMI (acpi_id[0x0d] high edge lint[0x1])
[    0.047718] ACPI: LAPIC_NMI (acpi_id[0x0e] high edge lint[0x1])
[    0.047719] ACPI: LAPIC_NMI (acpi_id[0x0f] high edge lint[0x1])
[    0.047720] ACPI: LAPIC_NMI (acpi_id[0x10] high edge lint[0x1])
[    0.047720] ACPI: LAPIC_NMI (acpi_id[0x11] high edge lint[0x1])
[    0.047721] ACPI: LAPIC_NMI (acpi_id[0x12] high edge lint[0x1])
[    0.047722] ACPI: LAPIC_NMI (acpi_id[0x13] high edge lint[0x1])
[    0.047722] ACPI: LAPIC_NMI (acpi_id[0x14] high edge lint[0x1])
[    0.047723] ACPI: LAPIC_NMI (acpi_id[0x15] high edge lint[0x1])
[    0.047724] ACPI: LAPIC_NMI (acpi_id[0x16] high edge lint[0x1])
[    0.047724] ACPI: LAPIC_NMI (acpi_id[0x17] high edge lint[0x1])
[    0.047725] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.047765] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.047767] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.047771] ACPI: Using ACPI (MADT) for SMP configuration information
[    0.047772] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.121618] ACPI: Core revision 20230331
[    0.158201] ACPI: PM: Registering ACPI NVS region [mem 0x42459000-0x42651fff] (2068480 bytes)
[    0.161004] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.161220] ACPI: Added _OSI(Module Device)
[    0.161220] ACPI: Added _OSI(Processor Device)
[    0.161220] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.161220] ACPI: Added _OSI(Processor Aggregator Device)
[    0.272397] ACPI: 14 ACPI AML tables successfully acquired and loaded
[    0.286109] ACPI: Dynamic OEM Table Load:
[    0.286119] ACPI: SSDT 0xFFFF97C6C02F0600 0001AB (v02 PmRef  Cpu0Psd  00003000 INTL 20200717)
[    0.287224] ACPI: \_SB_.PR00: _OSC native thermal LVT Acked
[    0.293144] ACPI: Dynamic OEM Table Load:
[    0.293151] ACPI: SSDT 0xFFFF97C6C294E400 000394 (v02 PmRef  Cpu0Cst  00003001 INTL 20200717)
[    0.294480] ACPI: Dynamic OEM Table Load:
[    0.294486] ACPI: SSDT 0xFFFF97C6C2966000 000626 (v02 PmRef  Cpu0Ist  00003000 INTL 20200717)
[    0.295917] ACPI: Dynamic OEM Table Load:
[    0.295922] ACPI: SSDT 0xFFFF97C6C2967000 0004B5 (v02 PmRef  Cpu0Hwp  00003000 INTL 20200717)
[    0.297618] ACPI: Dynamic OEM Table Load:
[    0.297626] ACPI: SSDT 0xFFFF97C6C1D92000 001BAF (v02 PmRef  ApIst    00003000 INTL 20200717)
[    0.299731] ACPI: Dynamic OEM Table Load:
[    0.299737] ACPI: SSDT 0xFFFF97C6C296A000 001038 (v02 PmRef  ApHwp    00003000 INTL 20200717)
[    0.301577] ACPI: Dynamic OEM Table Load:
[    0.301584] ACPI: SSDT 0xFFFF97C6C296C000 001349 (v02 PmRef  ApPsd    00003000 INTL 20200717)
[    0.303464] ACPI: Dynamic OEM Table Load:
[    0.303470] ACPI: SSDT 0xFFFF97C6C0161000 000FBB (v02 PmRef  ApCst    00003000 INTL 20200717)
[    0.314230] ACPI: EC: EC started
[    0.314231] ACPI: EC: interrupt blocked
[    0.314258] ACPI: EC: EC_CMD/EC_SC=0x66, EC_DATA=0x62
[    0.314260] ACPI: \_SB_.PC00.LPCB.EC0_: Boot DSDT EC used to handle transactions
[    0.314262] ACPI: Interpreter enabled
[    0.314326] ACPI: PM: (supports S0 S3 S4 S5)
[    0.314327] ACPI: Using IOAPIC for interrupt routing
[    0.318173] PCI: MMCONFIG at [mem 0xc0000000-0xce0fffff] reserved as ACPI motherboard resource
[    0.318183] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.319814] ACPI: Enabled 8 GPEs in block 00 to 7F
[    0.325015] ACPI: \_SB_.PC00.RP10.PXSX.WRST: New power resource
[    0.325038] ACPI: \_SB_.PC00.RP10.PXSX.DRST: New power resource
[    0.336480] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    0.336498] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS01._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    0.336527] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    0.336535] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS02._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    0.336561] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    0.336568] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS03._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    0.336692] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    0.336699] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS05._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    0.345612] ACPI: \_SB_.PC00.CNVW.WRST: New power resource
[    0.349723] ACPI: \_SB_.PC00.TBT0: New power resource
[    0.350111] ACPI: \_SB_.PC00.TBT1: New power resource
[    0.350490] ACPI: \_SB_.PC00.D3C_: New power resource
[    0.359096] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    0.359107] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS01._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    0.359135] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    0.359142] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS02._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    0.359169] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    0.359176] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS03._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    0.359204] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    0.359211] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS04._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    0.403188] ACPI: \_TZ_.FN00: New power resource
[    0.403247] ACPI: \_TZ_.FN01: New power resource
[    0.403303] ACPI: \_TZ_.FN02: New power resource
[    0.403358] ACPI: \_TZ_.FN03: New power resource
[    0.403412] ACPI: \_TZ_.FN04: New power resource
[    0.404087] ACPI: \PIN_: New power resource
[    0.404506] ACPI: PCI Root Bridge [PC00] (domain 0000 [bus 00-e0])
[    0.435618] ACPI: PCI: Interrupt link LNKA configured for IRQ 0
[    0.435742] ACPI: PCI: Interrupt link LNKB configured for IRQ 1
[    0.435863] ACPI: PCI: Interrupt link LNKC configured for IRQ 0
[    0.435983] ACPI: PCI: Interrupt link LNKD configured for IRQ 0
[    0.436103] ACPI: PCI: Interrupt link LNKE configured for IRQ 0
[    0.436224] ACPI: PCI: Interrupt link LNKF configured for IRQ 0
[    0.436344] ACPI: PCI: Interrupt link LNKG configured for IRQ 0
[    0.436483] ACPI: PCI: Interrupt link LNKH configured for IRQ 0
[    0.907698] ACPI: EC: interrupt unblocked
[    0.907700] ACPI: EC: event unblocked
[    0.907722] ACPI: EC: EC_CMD/EC_SC=0x66, EC_DATA=0x62
[    0.907723] ACPI: EC: GPE=0x6e
[    0.907724] ACPI: \_SB_.PC00.LPCB.EC0_: Boot DSDT EC initialization complete
[    0.907726] ACPI: \_SB_.PC00.LPCB.EC0_: EC: Used to handle transactions and events
[    0.907795] ACPI: bus type USB registered
[    0.908601] PCI: Using ACPI for IRQ routing
[    0.936763] pnp: PnP ACPI init
[    0.944281] pnp: PnP ACPI: found 5 devices
[    0.972112] ACPI: button: Sleep Button [SLPB]
[    0.972167] ACPI: button: Power Button [PWRB]
[    0.974868] ACPI: button: Power Button [PWRF]
[    0.980476] ACPI: thermal: Thermal Zone [TZ00] (28 C)
[    1.456915] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.456942] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS01._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.456968] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.456986] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS01._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.457012] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.457029] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS02._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.457052] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.457069] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS02._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.457093] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.457110] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS03._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.457133] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.457150] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS03._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.457174] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.457191] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS04._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.457215] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.457231] ACPI Error: Aborting method \_SB.PC00.TXHC.RHUB.SS04._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.459008] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.459033] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS01._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.459072] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.459094] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS01._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.459125] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.459142] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS02._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.459166] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.459183] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS02._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.459207] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.459224] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS03._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.459247] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.459264] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS03._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.459295] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.459312] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS05._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.459335] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.459352] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS05._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.868099] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.868123] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS03._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    1.868749] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.UBTC.RUCC], AE_NOT_FOUND (20230331/psargs-330)
[    1.868767] ACPI Error: Aborting method \_SB.PC00.XHCI.RHUB.HS03._PLD due to previous error (AE_NOT_FOUND) (20230331/psparse-529)
[    3.121336] ACPI: bus type drm_connector registered
[    4.025225] ACPI: video: Video Device [GFX0] (multi-head: yes  rom: no  post: no)

```
-------------------------

---

