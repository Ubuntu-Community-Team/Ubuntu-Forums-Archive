---
title: "Chromium crash with SIGABRT possible nouveau_vieux_dri.so problem"
date: 2013-03-02
forum: General Help
---

### Post by Frozen Forest on 2013-03-02
Chromium have recently started crashing repeatedly, when running chromium from shell will it mention that it crash with flag SIGABRT, while checking syslog did I found the following.
```

chromium-browse[2112]: segfault at 4 ip 00f70e79 sp bfee5d90 error 4 in nouveau_vieux_dri.so[f67000+2f000]
chromium-browse[3220]: segfault at 4 ip 0d940e79 sp bfb940b0 error 4 in nouveau_vieux_dri.so[d937000+2f000]
chromium-browse[3404]: segfault at 4 ip 2603ee79 sp bfa589d0 error 4 in nouveau_vieux_dri.so[26035000+2f000]
chromium-browse[3564]: segfault at 4 ip 2c17ae79 sp bfed0970 error 4 in nouveau_vieux_dri.so[2c171000+2f000]
chromium-browse[3727]: segfault at 4 ip 5ac09e79 sp bfbfc610 error 4 in nouveau_vieux_dri.so[5ac00000+2f000]
chromium-browse[3949]: segfault at 4 ip 00b5be79 sp bfa935a0 error 4 in nouveau_vieux_dri.so[b52000+2f000]
chromium-browse[4165]: segfault at 4 ip 00d1fe79 sp bfa24300 error 4 in nouveau_vieux_dri.so[d16000+2f000]

``` 
nouveau_vieux_dri.so seem to be related to MesaDrivers, which I think is the graphic driver.
```

01:00.0 VGA compatible controller: NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: CardExpert Technology Device 0411
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (1250ns min, 250ns max)
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at de000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Expansion ROM at dfee0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [44] AGP version 3.0
        Status: RQ=32 Iso- ArqSz=0 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
        Command: RQ=32 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x8
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb

```

EDIT:
Found the following regarding the driver
[http://nouveau.freedesktop.org/wiki/MesaDrivers](http://nouveau.freedesktop.org/wiki/MesaDrivers)
[QUOTE="http://nouveau.freedesktop.org/wiki/MesaDrivers"]
**nouveau_vieux (NV04 - NV20)**

 nouveau_vieux_dri.so  is a classic Mesa DRI driver, and not a Gallium3D driver, because these  cards do not have enough shader capabilities to reasonably support the  Gallium3D infrastructure. 
Do not file bug reports about this driver.
[/QUOTE]

---

