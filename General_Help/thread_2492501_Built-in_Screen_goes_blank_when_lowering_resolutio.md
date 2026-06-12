---
title: "Built-in Screen goes blank when lowering resolution"
date: 2023-11-13
forum: General Help
---

### Post by Notiz Me on 2023-11-13
Hi all,

This post is a duplicate of [my ask Ubuntu question]("https://askubuntu.com/questions/1490554/built-in-screen-goes-blank-when-lowering-resolution").

I started thinking that the question might need too much interaction for ask Ubuntu. That's why I'm posting it here.

I also didn't really know in which section to put it.

Please tell me if I can do anything better.


I have a three monitor setup like this.

[IMG]https://i.stack.imgur.com/jmo0G.png[/IMG]

Everything works fine like this. But whenever I set the Built-in Screen to a lower resolution, the Built-in Screen just goes blank. The other two screens keep working fine. When I set it back to 1920x1080 it comes back up. The screen space seems to be rendered, since I can move my mouse into it, and put windows in it. I can also take a screenshot of it.

[IMG]https://i.imgur.com/Pkz02RU.jpeg[/IMG]

But nothing shows up on the laptop screen. The backlight is on and can still be adjusted. System Settings just acts like everything is fine.

[IMG]https://i.imgur.com/YiXQneW.png[/IMG]

I did some searching and also tried ChatGPT, but the problem is so specific that I don&#8217;t really know what to look for.

I&#8217;m on **Kubuntu 23.10**. The laptop is an **HP Elitebook 845 G8**, with an **AMD Ryzen 7 PRO 5850U with Radeon Graphics**.

```
sudo lspci -k -vvv -P -PP
``` gives me:

```
00:08.1/04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cezanne [Radeon Vega Series / Radeon Vega Mobile Series] (rev d1) (prog-if 00 [VGA controller])
        DeviceName: Onboard IGD
        Subsystem: Hewlett-Packard Company Cezanne [Radeon Vega Series / Radeon Vega Mobile Series]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 74
        IOMMU group: 12
        Region 0: Memory at 460000000 (64-bit, prefetchable) [size=256M]
        Region 2: Memory at 470000000 (64-bit, prefetchable) [size=2M]
        Region 4: I/O ports at 1000 [size=256]
        Region 5: Memory at fb300000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [48] Vendor Specific Information: Len=08 <?>
        Capabilities: [50] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [64] Express (v2) Legacy Endpoint, MSI 00
                DevCap: MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: CorrErr- NonFatalErr- FatalErr- UnsupReq-
                        RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- NonFatalErr- FatalErr- UnsupReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 8GT/s, Width x16, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us
                        ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp+
                LnkCtl: ASPM Disabled; RCB 64 bytes, Disabled- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 8GT/s, Width x16
                        TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Range ABCD, TimeoutDis+ NROPrPrP- LTR-
                         10BitTagComp+ 10BitTagReq- OBFF Not Supported, ExtFmt+ EETLPPrefix+, MaxEETLPPrefixes 1
                         EmergencyPowerReduction Not Supported, EmergencyPowerReductionInit-
                         FRS-
                         AtomicOpsCap: 32bit- 64bit- 128bitCAS-
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- LTR- 10BitTagReq- OBFF Disabled,
                         AtomicOpsCtl: ReqEn-
                LnkCap2: Supported Link Speeds: 2.5-16GT/s, Crosslink- Retimer+ 2Retimers+ DRS-
                LnkCtl2: Target Link Speed: 8GT/s, EnterCompliance- SpeedDis-
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance Preset/De-emphasis: -6dB de-emphasis, 0dB preshoot
                LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete+ EqualizationPhase1+
                         EqualizationPhase2+ EqualizationPhase3+ LinkEqualizationRequest-
                         Retimer- 2Retimers- CrosslinkRes: unsupported
        Capabilities: [a0] MSI: Enable- Count=1/4 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [c0] MSI-X: Enable+ Count=4 Masked-
                Vector table: BAR=5 offset=00042000
                PBA: BAR=5 offset=00043000
        Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Capabilities: [270 v1] Secondary PCI Express
                LnkCtl3: LnkEquIntrruptEn- PerformEqu-
                LaneErrStat: 0
        Capabilities: [2a0 v1] Access Control Services
                ACSCap: SrcValid- TransBlk- ReqRedir- CmpltRedir- UpstreamFwd- EgressCtrl- DirectTrans-
                ACSCtl: SrcValid- TransBlk- ReqRedir- CmpltRedir- UpstreamFwd- EgressCtrl- DirectTrans-
        Capabilities: [2b0 v1] Address Translation Service (ATS)
                ATSCap: Invalidate Queue Depth: 00
                ATSCtl: Enable+, Smallest Translation Unit: 00
        Capabilities: [2c0 v1] Page Request Interface (PRI)
                PRICtl: Enable- Reset-
                PRISta: RF- UPRGI- Stopped+
                Page Request Capacity: 00000100, Page Request Allocation: 00000000
        Capabilities: [2d0 v1] Process Address Space ID (PASID)
                PASIDCap: Exec+ Priv+, Max PASID Width: 10
                PASIDCtl: Enable- Exec- Priv-
        Capabilities: [400 v1] Data Link Feature <?>
        Capabilities: [410 v1] Physical Layer 16.0 GT/s <?>
        Capabilities: [440 v1] Lane Margining at the Receiver <?>
        Kernel driver in use: amdgpu
        Kernel modules: amdgpu
```

```
sudo lshw
``` gives me:

```
*-display
                description: VGA compatible controller
                product: Cezanne [Radeon Vega Series / Radeon Vega Mobile Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: /dev/fb0
                version: d1
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix vga_controller bus_master cap_list fb
                configuration: depth=32 driver=amdgpu latency=0 mode=1920x1080 resolution=1920,1080 visual=truecolor xres=1920 yres=1080
                resources: iomemory:40-3f iomemory:40-3f irq:74 memory:460000000-46fffffff memory:470000000-4701fffff ioport:1000(size=256) memory:fb300000-fb37ffff

```

```
xrandr
``` gives me:

```

Screen 0: minimum 320 x 200, current 4480 x 1080, maximum 16384 x 16384
eDP connected primary 1280x720+3200+0 (normal left inverted right x axis y axis) 309mm x 173mm
   1920x1080     60.00 +  40.00  
   1680x1050     60.00  
   1280x1024     60.00  
   1440x900      60.00  
   1280x800      60.00  
   1280x720      60.00* 
   1024x768      60.00  
   800x600       60.00  
   640x480       60.00  
HDMI-A-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
DisplayPort-2 connected 1920x1080+1280+0 (normal left inverted right x axis y axis) 480mm x 270mm
   1920x1080     60.00*+  50.00    59.94  
   1680x1050     59.88  
   1400x1050     59.95  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DisplayPort-3 connected 1280x1024+0+56 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024     60.02*+  75.02  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08
```

When setting the resolution from 1920x1080 to 1280x720 the Xorg log is:
```
[216181.451] (WW) AMDGPU(0): flip queue failed: Invalid argument
[216181.451] (WW) AMDGPU(0): Page flip failed: Invalid argument
[216181.484] (II) AMDGPU(0): Allocate new frame buffer 4480x1080
[216181.484] (II) AMDGPU(0):  => pitch 17920 bytes
[216181.598] (II) AMDGPU(0): EDID vendor "FUS", prod id 1686
[216181.598] (II) AMDGPU(0): Using hsync ranges from config file
[216181.598] (II) AMDGPU(0): Using vrefresh ranges from config file
[216181.598] (II) AMDGPU(0): Printing DDC gathered Modelines:
[216181.598] (II) AMDGPU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[216181.598] (II) AMDGPU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[216181.598] (II) AMDGPU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[216181.598] (II) AMDGPU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[216181.598] (II) AMDGPU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[216181.598] (II) AMDGPU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[216181.598] (II) AMDGPU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[216181.598] (II) AMDGPU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[216181.598] (II) AMDGPU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[216181.628] (II) AMDGPU(0): EDID vendor "FUS", prod id 1686
[216181.628] (II) AMDGPU(0): Using hsync ranges from config file
[216181.628] (II) AMDGPU(0): Using vrefresh ranges from config file
[216181.628] (II) AMDGPU(0): Printing DDC gathered Modelines:
[216181.628] (II) AMDGPU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[216181.628] (II) AMDGPU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[216181.628] (II) AMDGPU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[216181.628] (II) AMDGPU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[216181.628] (II) AMDGPU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[216181.628] (II) AMDGPU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[216181.628] (II) AMDGPU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[216181.628] (II) AMDGPU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[216181.628] (II) AMDGPU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[216181.664] (II) AMDGPU(0): EDID vendor "FUS", prod id 1686
[216181.664] (II) AMDGPU(0): Using hsync ranges from config file
[216181.664] (II) AMDGPU(0): Using vrefresh ranges from config file
[216181.664] (II) AMDGPU(0): Printing DDC gathered Modelines:
[216181.664] (II) AMDGPU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[216181.664] (II) AMDGPU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[216181.664] (II) AMDGPU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[216181.664] (II) AMDGPU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[216181.664] (II) AMDGPU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[216181.664] (II) AMDGPU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[216181.665] (II) AMDGPU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[216181.665] (II) AMDGPU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[216181.665] (II) AMDGPU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[216181.665] (WW) AMDGPU(0): flip queue failed: Invalid argument
[216181.665] (WW) AMDGPU(0): Page flip failed: Invalid argument
[216181.733] (II) AMDGPU(0): EDID vendor "FUS", prod id 1686
[216181.733] (II) AMDGPU(0): Using hsync ranges from config file
[216181.733] (II) AMDGPU(0): Using vrefresh ranges from config file
[216181.733] (II) AMDGPU(0): Printing DDC gathered Modelines:
[216181.733] (II) AMDGPU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[216181.733] (II) AMDGPU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[216181.733] (II) AMDGPU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[216181.733] (II) AMDGPU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[216181.733] (II) AMDGPU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[216181.733] (II) AMDGPU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[216181.733] (II) AMDGPU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[216181.733] (II) AMDGPU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[216181.733] (II) AMDGPU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[216181.759] (II) AMDGPU(0): EDID vendor "FUS", prod id 1686
[216181.760] (II) AMDGPU(0): Using hsync ranges from config file
[216181.760] (II) AMDGPU(0): Using vrefresh ranges from config file
[216181.760] (II) AMDGPU(0): Printing DDC gathered Modelines:
[216181.760] (II) AMDGPU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[216181.760] (II) AMDGPU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[216181.760] (II) AMDGPU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[216181.760] (II) AMDGPU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[216181.760] (II) AMDGPU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[216181.760] (II) AMDGPU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[216181.760] (II) AMDGPU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[216181.760] (II) AMDGPU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[216181.760] (II) AMDGPU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[216181.787] (II) AMDGPU(0): EDID vendor "FUS", prod id 1686
[216181.787] (II) AMDGPU(0): Using hsync ranges from config file
[216181.787] (II) AMDGPU(0): Using vrefresh ranges from config file
[216181.787] (II) AMDGPU(0): Printing DDC gathered Modelines:
[216181.787] (II) AMDGPU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[216181.787] (II) AMDGPU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[216181.787] (II) AMDGPU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[216181.787] (II) AMDGPU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[216181.787] (II) AMDGPU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[216181.787] (II) AMDGPU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[216181.787] (II) AMDGPU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[216181.787] (II) AMDGPU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[216181.787] (II) AMDGPU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[216181.816] (II) AMDGPU(0): EDID vendor "FUS", prod id 1686
[216181.817] (II) AMDGPU(0): Using hsync ranges from config file
[216181.817] (II) AMDGPU(0): Using vrefresh ranges from config file
[216181.817] (II) AMDGPU(0): Printing DDC gathered Modelines:
[216181.817] (II) AMDGPU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[216181.817] (II) AMDGPU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[216181.817] (II) AMDGPU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[216181.817] (II) AMDGPU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[216181.817] (II) AMDGPU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[216181.817] (II) AMDGPU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[216181.817] (II) AMDGPU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[216181.817] (II) AMDGPU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[216181.817] (II) AMDGPU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[216181.844] (II) AMDGPU(0): EDID vendor "FUS", prod id 1686
[216181.844] (II) AMDGPU(0): Using hsync ranges from config file
[216181.844] (II) AMDGPU(0): Using vrefresh ranges from config file
[216181.844] (II) AMDGPU(0): Printing DDC gathered Modelines:
[216181.844] (II) AMDGPU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[216181.844] (II) AMDGPU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[216181.844] (II) AMDGPU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[216181.844] (II) AMDGPU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[216181.844] (II) AMDGPU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[216181.844] (II) AMDGPU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[216181.844] (II) AMDGPU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[216181.844] (II) AMDGPU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[216181.844] (II) AMDGPU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[216181.869] (II) AMDGPU(0): EDID vendor "FUS", prod id 1686
[216181.869] (II) AMDGPU(0): Using hsync ranges from config file
[216181.869] (II) AMDGPU(0): Using vrefresh ranges from config file
[216181.869] (II) AMDGPU(0): Printing DDC gathered Modelines:
[216181.869] (II) AMDGPU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[216181.869] (II) AMDGPU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[216181.869] (II) AMDGPU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[216181.869] (II) AMDGPU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[216181.869] (II) AMDGPU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[216181.869] (II) AMDGPU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[216181.869] (II) AMDGPU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[216181.869] (II) AMDGPU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[216181.869] (II) AMDGPU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
```

I didn't have any troubles in my previous Ubuntu install, Kubuntu 22.04.

Could anybody give me some ideas. I don't know in which direction to look.

---

### Post by SeijiSensei on 2023-11-13
If you didn't have problems with 22.04, why are you moving on to 23.10, a release with only nine months of support? Is there some specific piece of software for which you need the very newest version? Remember that releases other than those with long-term support like 22.04 and the upcoming 24.04 can be buggy. Upgrading just because it's possible isn't always the best strategy with Linux. I'd go back to 22.04 and wait for 24.04 next April.

---

### Post by Yellow Pasque on 2023-11-13
[https://gitlab.freedesktop.org/agd5f/linux/-/commit/5ec3569d6add4ee94da1f35d9776293c6efe8487](https://gitlab.freedesktop.org/agd5f/linux/-/commit/5ec3569d6add4ee94da1f35d9776293c6efe8487)

> **SeijiSensei said:**
> If you didn't have problems with 22.04, why are you moving on to 23.10, a release with only nine months of support? ... Remember that releases other than those with long-term support like 22.04 and the upcoming 24.04 can be buggy. 

Maybe your personal philosophy is to only use LTS releases, but LTS releases can have bugs too. The biannual releases are stable and meant for regular users. They are not experimental releases meant just for devs and testers.

---

### Post by SeijiSensei on 2023-11-13
I've used both. Most times everything works but sometimes there are problems. Unless there is a compelling reason for upgrading from a 22.04 release that is working for him to 23.10, which is not, I would just revert.

---

### Post by MAFoElffen on 2023-11-14
Your resolution of 1280x720 does not match any of your supported modelines. The closest is 1280x1024... In the xorg log file, it's searching for 1280x720, probes the display for it's EDID table, only see's these
```

Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)

```
When it doesn't see it, it throws an error, then tries again...

That is what I see.

You could always declare a modeline for 1080x720@60, and it to an NN-XXX.conf file in /etc/X11/xorg.conf.d, and then try it.

---

### Post by Notiz Me on 2023-11-14
> **SeijiSensei said:**
> If you didn't have problems with 22.04, why are you moving on to 23.10, a release with only nine months of support? Is there some specific piece of software for which you need the very newest version? Remember that releases other than those with long-term support like 22.04 and the upcoming 24.04 can be buggy. Upgrading just because it's possible isn't always the best strategy with Linux. I'd go back to 22.04 and wait for 24.04 next April.

I did have problems on my previous install that urged me to upgrade, but they where different problems :D

Now that you mention that 22.04 was LTS, my previous version must have been 22.10. By the time I upgraded the repo's were unavailable :oops:

Anyway, not really the help I was looking for :P

Somewhere in my installation there's a misconfiguration or a bug, and I would like to solve it or post a bug report. I just feel like I can't pinpoint the problem yet.

> **Yellow Pasque said:**
> [https://gitlab.freedesktop.org/agd5f/linux/-/commit/5ec3569d6add4ee94da1f35d9776293c6efe8487](https://gitlab.freedesktop.org/agd5f/linux/-/commit/5ec3569d6add4ee94da1f35d9776293c6efe8487)

I'm not in mirror mode, so I guess this doesn't apply to me?

> **MAFoElffen said:**
> Your resolution of 1280x720 does not match any of your supported modelines. The closest is 1280x1024... In the xorg log file, it's searching for 1280x720, probes the display for it's EDID table, only see's these
```

Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)

```
When it doesn't see it, it throws an error, then tries again...

That is what I see.

You could always declare a modeline for 1080x720@60, and it to an NN-XXX.conf file in /etc/X11/xorg.conf.d, and then try it.

I didn't notice it yet, but for some reason, when I make one resolution change to my right screen (Built-in Screen) using the System Settings, the Xorg log contains 9 times the DDC Modelines of my left screen. "FUS" = Fujitsu Siemens". But that's not the screen of which I'm changing the resolution :P

The Fujitsu Siemens screen is a 4:3 aspect ratio, so that checks out, it's set to 1280x1024.


I went looking for EDID information of the Built-in Screen and found these results:

```

pieter@pieter-HP-EliteBook-845-G8-Notebook-PC:~$ sudo get-edid | parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 3
No EDID on bus 4
No EDID on bus 5
No EDID on bus 6
No EDID on bus 8
5 potential busses found: 2 7 9 10 11
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
Bus 2 doesn't really have an EDID...
128-byte EDID successfully retrieved from i2c bus 7
Looks like i2c was successful. Have a good day.
Checksum Correct

Section "Monitor"
        Identifier ""
        ModelName ""
        VendorName "CMN"
        # Monitor Manufactured week 2 of 2021
        # EDID version 1.4
        # Digital Display
        DisplaySize 310 170
        Gamma 2.20
        Option "DPMS" "false"
        Modeline        "Mode 0" +hsync -vsync
        Modeline        "Mode 1" +hsync -vsync
EndSection

pieter@pieter-HP-EliteBook-845-G8-Notebook-PC:~$ edid-decode /sys/class/drm/card0-eDP-1/edid
edid-decode (hex):

00 ff ff ff ff ff ff 00 0d ae 1d 14 00 00 00 00
02 1f 01 04 a5 1f 11 78 03 ee 95 a3 54 4c 99 26
0f 50 54 00 00 00 01 01 01 01 01 01 01 01 01 01
01 01 01 01 01 01 a4 38 80 e6 70 38 2c 40 30 20
a6 00 35 ad 10 00 00 1a c3 25 80 e6 70 38 2c 40
30 20 a6 00 35 ad 10 00 00 1a 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 02
00 0c 26 ff 14 3c c8 09 06 14 c8 00 00 00 00 6a

----------------

Block 0, Base EDID:
  EDID Structure Version & Revision: 1.4
  Vendor & Product Identification:
    Manufacturer: CMN
    Model: 5149
    Made in: week 2 of 2021
  Basic Display Parameters & Features:
    Digital display
    Bits per primary color channel: 8
    DisplayPort interface
    Maximum image size: 31 cm x 17 cm
    Gamma: 2.20
    Supported color formats: RGB 4:4:4
    First detailed timing includes the native pixel format and preferred refresh rate
    Display is continuous frequency
  Color Characteristics:
    Red  : 0.6396, 0.3300
    Green: 0.2998, 0.5996
    Blue : 0.1503, 0.0595
    White: 0.3134, 0.3291
  Established Timings I & II: none
  Standard Timings: none
  Detailed Timing Descriptors:
    DTD 1:  1920x1080   60.001655 Hz  16:9     67.442 kHz    145.000000 MHz (309 mm x 173 mm)
                 Hfront   48 Hsync  32 Hback  150 Hpol P
                 Vfront   10 Vsync   6 Vback   28 Vpol N
    DTD 2:  1920x1080   40.002483 Hz  16:9     44.963 kHz     96.670000 MHz (309 mm x 173 mm)
                 Hfront   48 Hsync  32 Hback  150 Hpol P
                 Vfront   10 Vsync   6 Vback   28 Vpol N
    Empty Descriptor
    Manufacturer-Specified Display Descriptor (0x02): 00 02 00 0c 26 ff 14 3c c8 09 06 14 c8 00 00 00 '....&..<........'
Checksum: 0x6a

pieter@pieter-HP-EliteBook-845-G8-Notebook-PC:~$ grep -B 1 -A 44 CMN /var/log/Xorg.0.log
[     9.841] (II) AMDGPU(0): EDID for output eDP
[     9.841] (II) AMDGPU(0): Manufacturer: CMN  Model: 141d  Serial#: 0
[     9.841] (II) AMDGPU(0): Year: 2021  Week: 2
[     9.841] (II) AMDGPU(0): EDID Version: 1.4
[     9.841] (II) AMDGPU(0): Digital Display Input
[     9.841] (II) AMDGPU(0): 8 bits per channel
[     9.841] (II) AMDGPU(0): Digital interface is DisplayPort
[     9.841] (II) AMDGPU(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[     9.841] (II) AMDGPU(0): Gamma: 2.20
[     9.841] (II) AMDGPU(0): No DPMS capabilities specified
[     9.841] (II) AMDGPU(0): Supported color encodings: RGB 4:4:4
[     9.841] (II) AMDGPU(0): First detailed timing is preferred mode
[     9.841] (II) AMDGPU(0): Preferred mode is native pixel format and refresh rate
[     9.841] (II) AMDGPU(0): Display is continuous-frequency
[     9.841] (II) AMDGPU(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[     9.841] (II) AMDGPU(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[     9.841] (II) AMDGPU(0): Manufacturer's mask: 0
[     9.841] (II) AMDGPU(0): Supported detailed timing:
[     9.841] (II) AMDGPU(0): clock: 145.0 MHz   Image Size:  309 x 173 mm
[     9.841] (II) AMDGPU(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2150 h_border: 0
[     9.841] (II) AMDGPU(0): v_active: 1080  v_sync: 1090  v_sync_end 1096 v_blanking: 1124 v_border: 0
[     9.841] (II) AMDGPU(0): Supported detailed timing:
[     9.841] (II) AMDGPU(0): clock: 96.7 MHz   Image Size:  309 x 173 mm
[     9.841] (II) AMDGPU(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2150 h_border: 0
[     9.841] (II) AMDGPU(0): v_active: 1080  v_sync: 1090  v_sync_end 1096 v_blanking: 1124 v_border: 0
[     9.841] (II) AMDGPU(0): Unknown vendor-specific block 2
[     9.841] (II) AMDGPU(0): EDID (in hex):
[     9.841] (II) AMDGPU(0):    00ffffffffffff000dae1d1400000000
[     9.841] (II) AMDGPU(0):    021f0104a51f117803ee95a3544c9926
[     9.841] (II) AMDGPU(0):    0f505400000001010101010101010101
[     9.841] (II) AMDGPU(0):    010101010101a43880e670382c403020
[     9.841] (II) AMDGPU(0):    a60035ad1000001ac32580e670382c40
[     9.841] (II) AMDGPU(0):    3020a60035ad1000001a000000000000
[     9.841] (II) AMDGPU(0):    00000000000000000000000000000002
[     9.841] (II) AMDGPU(0):    000c26ff143cc8090614c8000000006a
[     9.842] (II) AMDGPU(0): Printing probed modes for output eDP
[     9.842] (II) AMDGPU(0): Modeline "1920x1080"x60.0  145.00  1920 1968 2000 2150  1080 1090 1096 1124 +hsync -vsync (67.4 kHz eP)
[     9.842] (II) AMDGPU(0): Modeline "1920x1080"x40.0   96.67  1920 1968 2000 2150  1080 1090 1096 1124 +hsync -vsync (45.0 kHz e)
[     9.842] (II) AMDGPU(0): Modeline "1680x1050"x60.0  145.00  1680 1968 2000 2150  1050 1090 1096 1124 +hsync -vsync (67.4 kHz e)
[     9.842] (II) AMDGPU(0): Modeline "1280x1024"x60.0  145.00  1280 1968 2000 2150  1024 1090 1096 1124 +hsync -vsync (67.4 kHz e)
[     9.842] (II) AMDGPU(0): Modeline "1440x900"x60.0  145.00  1440 1968 2000 2150  900 1090 1096 1124 +hsync -vsync (67.4 kHz e)
[     9.842] (II) AMDGPU(0): Modeline "1280x800"x60.0  145.00  1280 1968 2000 2150  800 1090 1096 1124 +hsync -vsync (67.4 kHz e)
[     9.842] (II) AMDGPU(0): Modeline "1280x720"x60.0  145.00  1280 1968 2000 2150  720 1090 1096 1124 +hsync -vsync (67.4 kHz e)
[     9.842] (II) AMDGPU(0): Modeline "1024x768"x60.0  145.00  1024 1968 2000 2150  768 1090 1096 1124 +hsync -vsync (67.4 kHz e)
[     9.842] (II) AMDGPU(0): Modeline "800x600"x60.0  145.00  800 1968 2000 2150  600 1090 1096 1124 +hsync -vsync (67.4 kHz e)
[     9.842] (II) AMDGPU(0): Modeline "640x480"x60.0  145.00  640 1968 2000 2150  480 1090 1096 1124 +hsync -vsync (67.4 kHz e)

```

If I'm interpreting this correctly, the monitor only has 1920x1080 in it's EDID data, but Xorg adds some more modes.

---

### Post by Notiz Me on 2023-11-16
> **Notiz Me said:**
> [QUOTE=Yellow Pasque;14165245][https://gitlab.freedesktop.org/agd5f/linux/-/commit/5ec3569d6add4ee94da1f35d9776293c6efe8487](https://gitlab.freedesktop.org/agd5f/linux/-/commit/5ec3569d6add4ee94da1f35d9776293c6efe8487)

I'm not in mirror mode, so I guess this doesn't apply to me?[/QUOTE]

On second thought, it might apply to me, since the edid didn't give any resolution other than 1920x1080, this commit would add some common modes.


I managed to get things working by installing a newer version of the kernel.

I used the [ubuntu-mainline-kernel.sh]("https://github.com/pimlie/ubuntu-mainline-kernel.sh") script to download and install a different kernel version.

Since I have secure boot enabled, I had to be able to sign the different kernel version. I created and enrolled a kernel signing certificate using [ubuntu-sb-kernel-signing]("https://github.com/berglh/ubuntu-sb-kernel-signing#creating-a-mok-for-kernel-signing").

I turned kernel signing on in ubuntu-mainline-kernel.sh.

Since Ubuntu was on version 6.5.0, I started at v6.5.1, but all version from v6.5.1 up to v6.5.8 gave an error message

```

Downloading index from kernel.ubuntu.com
Abort, the amd64 build has not succeeded

```

So I ended up using v6.5.9.

The error for the amd64 build seems to be solved in the meantime for v6.5.1, v6.5.2 and v6.5.3, the others will probably also get solved.

I'm using v6.5.9 now and the screen is working perfectly again.

I hope someone will find use of my solution. If it's better to tackle this differently, please let me know :)

---

### Post by Notiz Me on 2024-01-30
As can be seen on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2046504](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2046504) a bugfix has been released. So the solution above is no longer valid.

I haven't had time to figure how to switch back to the standard Ubuntu kernel yet.

---

