---
title: "laptop won't wake after suspend"
date: 2015-12-11
forum: General Help
---

### Post by rastadani on 2015-12-11
Hello everybody,
I recently installed Ubuntu 15.10 on my laptop. Everything seems fine except that my pc does not wake after suspend. The screen is completely black and my only way out is to restart the system using the power button. I know that there are many threads open on the same issue but I have still not found anything about Ubuntu 15.10, and the solutions I've found doesn't work in my case.

Here are some information about my laptop:

model:  Dell Inspiron 5559
Ubuntu version: 15.10 desktop - 64bit

The command:
   ```
 sudo lspci -vnn | grep -A12 VGA 
```
   returns:
```
00:02.0VGA compatible controller [0300]: Intel Corporation Sky LakeIntegrated Graphics [8086:1916] (rev 07) (prog-if 00 [VGAcontroller])    DeviceName: Onboard IGD
    Subsystem:Dell Device [1028:06b2]
    Flags:bus master, fast devsel, latency 0, IRQ 277
    Memoryat d1000000 (64-bit, non-prefetchable) [size=16M]
    Memoryat b0000000 (64-bit, prefetchable) [size=256M]
    I/Oports at f000 [size=64]
    ExpansionROM at <unassigned> [disabled]
    Capabilities:[40] Vendor Specific Information: Len=0c <?>
    Capabilities:[70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities:[ac] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities:[d0] Power Management version 2
    Capabilities:[100] #1b

```
and:
```
cat /proc/cmdline
```
returns:
```
BOOT_IMAGE=/boot/vmlinuz-4.2.0-19-genericroot=UUID=bbab357a-bb1b-4bd8-ab5e-60da4c7b5202 ro reboot=efi quietsplash vt.handoff=7

```

If you need some other information plese ask me.

Thanks in advance.

---

