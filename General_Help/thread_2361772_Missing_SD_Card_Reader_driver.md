---
title: "Missing SD Card Reader driver?"
date: 2017-05-20
forum: General Help
---

### Post by Zemtriz on 2017-05-20
Hello,

I have problems to run my builtin SD card reader in laptop.

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader (rev 01)

Full lspci output:
```
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader (rev 01)
    Subsystem: CLEVO/KAPOK Computer RTL8411B PCI Express Card Reader
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 124
    Region 0: Memory at df115000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at df100000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME+
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee00298  Data: 0000
    Capabilities: [70] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s unlimited, L1 <64us
            ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp+
        LnkCtl:    ASPM L1 Enabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR+, OBFF Via message/WAKE#
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [b0] MSI-X: Enable- Count=1 Masked-
        Vector table: BAR=0 offset=00000000
        PBA: BAR=0 offset=00000000
    Capabilities: [d0] Vital Product Data
pcilib: sysfs_read_vpd: read failed: Input/output error
        Not readable
    Capabilities: [100 v2] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr+ BadTLP- BadDLLP+ Rollover- Timeout- NonFatalErr+
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [140 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
            Status:    NegoPending- InProgress-
    Capabilities: [160 v1] Device Serial Number 00-00-00-00-00-00-00-00
    Capabilities: [170 v1] Latency Tolerance Reporting
        Max snoop latency: 3145728ns
        Max no snoop latency: 3145728ns
    Capabilities: [178 v1] L1 PM Substates
        L1SubCap: PCI-PM_L1.2+ PCI-PM_L1.1+ ASPM_L1.2+ ASPM_L1.1+ L1_PM_Substates+
              PortCommonModeRestoreTime=150us PortTPowerOnTime=150us
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci
00: ec 10 87 52 06 04 10 00 01 00 00 ff 10 00 80 00
10: 00 50 11 df 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 58 15 10 24
30: 00 00 10 df 40 00 00 00 00 00 00 00 ff 02 00 00
40: 01 50 c3 f7 00 80 00 00 00 00 00 00 00 00 00 00
50: 05 70 81 00 98 02 e0 fe 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 10 b0 02 00 c0 8c 90 05 10 20 19 00 11 7c 47 00
80: 42 01 11 10 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 1f 08 0c 00 00 00 00 00 02 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 11 d0 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00



```

Any ideas how to get it running, which module to load?

Thank you

EDIT: I've tried to download RTL8441B driver from Realtek website: 
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D(L)%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8168E/RTL8111F/RTL8411%3Cbr%3ERTL8111G/RTL8111GUS/RTL8411B(N)%3Cbr%3ERTL8118AS](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D(L)%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8168E/RTL8111F/RTL8411%3Cbr%3ERTL8111G/RTL8111GUS/RTL8411B(N)%3Cbr%3ERTL8118AS)
But it was stated in README.txt file as driver for ethernet controller.

So I was looking next and found on Dell website RTS5229/RTL8411B driver, so I lookef for RTS5229 driver on realtek and found this:
[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false)
I have tried to install it but there were errors after make command:
```
cp -f ./define.release ./define.h
make -C /lib/modules/4.10.0-21-generic/build/ SUBDIRS= modules
make[1]: Entering directory '/usr/src/linux-headers-4.10.0-21-generic'
make[2]: *** No rule to make target 'arch/x86/entry/syscalls/syscall_32.tbl', needed by 'arch/x86/entry/syscalls/../../include/generated/asm/syscalls_32.h'.  Stop.
arch/x86/Makefile:192: recipe for target 'archheaders' failed
make[1]: *** [archheaders] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-21-generic'
Makefile:35: recipe for target 'default' failed
make: *** [default] Error 2


```

So I've tried to update files how it was described in:
[https://askubuntu.com/questions/473848/ubuntu-14-04-realtek-semiconductor-co-ltd-rts5227-pci-express-card-reader-isn](https://askubuntu.com/questions/473848/ubuntu-14-04-realtek-semiconductor-co-ltd-rts5227-pci-express-card-reader-isn)
But same errors occured. Also tried to run is as root and reinstalled build-essentials and other required packages.

What should I do? Help me pls :(
I don't want to always give up and install windows.

---

