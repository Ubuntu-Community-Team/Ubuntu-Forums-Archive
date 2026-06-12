---
title: "No console beep ..."
date: 2007-05-09
forum: General Help
---

### Post by BigBob on 2007-05-09
Hi all,

I have no console beep at all.

My sound card is reported like this with lspci :

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30aa
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at e8580000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0

```

Someone know why and how i can enable it ?

A++

---

### Post by jjmatt on 2007-05-09
Have you tried this: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_disable_beep_sound_in_Terminal_mode]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_disable_beep_sound_in_Terminal_mode")

---

### Post by BigBob on 2007-05-09
> **jjmatt said:**
> Have you tried this: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_disable_beep_sound_in_Terminal_mode]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_disable_beep_sound_in_Terminal_mode")

Yes, but looking the output of amixer, i don't see any pc speaker volume controler :-(

A++

---

