---
title: "Ubuntu Core 20 Boot Issues on CM4"
date: 2022-05-12
forum: General Help
---

### Post by shane-warner on 2022-05-12
I've flashed the image for ubuntu core 20 on a compute module 4 with emmc per the documentation, however it won't boot. 

This is the debug output from the CM4 serial UART:

```


U-Boot 2020.10+dfsg-1ubuntu0~20.04.2 (Jan 08 2021 - 13:03:11 +0000)


DRAM:  1.9 GiB
RPI: Board rev 0x14 outside known range
RPI Unknown model (0xb03140)
MMC:   mmcnr@7e300000: 1, emmc2@7e340000: 0
Loading Environment from FAT... *** Warning - bad CRC, using default environment


In:    serial
Out:   serial
Err:   serial
Net:   eth0: ethernet@7d580000
starting USB...
No working controllers found
Hit any key to stop autoboot:  0
switch to partitions #0, OK
mmc0(part 0) is current device
Scanning mmc 0:1...
Found U-Boot script /boot.scr
4638 bytes read in 20 ms (225.6 KiB/s)
## Executing script at 02400000
4096 bytes read in 18 ms (221.7 KiB/s)
8400421 bytes read in 646 ms (12.4 MiB/s)
Total of 1 halfword(s) were the same
Decompressing kernel...
Uncompressed size: 23843328 = 0x16BD200
12884480 bytes read in 975 ms (12.6 MiB/s)
Booting Ubuntu (with booti) from mmc 0:...
## Flattened Device Tree blob at 02600000
   Booting using the fdt blob at 0x2600000
   Using Device Tree in place at 0000000002600000, end 000000000260ef0e


Starting kernel ...


[    0.486408] Initramfs unpacking failed: Decoding failed
[    0.867686] brcm-pcie fd500000.pcie: link down
[    1.309537] spi-bcm2835 fe204000.spi: could not get clk: -517
**[    1.489514] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)**
[    1.497898] CPU: 3 PID: 1 Comm: swapper/0 Not tainted 5.4.0-1038-raspi #41-Ubuntu
[    1.505481] Hardware name: Raspberry Pi Compute Module 4 Rev 1.0 (DT)
[    1.512006] Call trace:
[    1.514487]  dump_backtrace+0x0/0x198
[    1.518193]  show_stack+0x28/0x38
[    1.521549]  dump_stack+0xd8/0x134
[    1.524991]  panic+0x160/0x35c
[    1.528084]  mount_block_root+0x244/0x300
[    1.532142]  mount_root+0x48/0x50
[    1.535496]  prepare_namespace+0x13c/0x1a0
[    1.539643]  kernel_init_freeable+0x25c/0x280
[    1.544053]  kernel_init+0x1c/0x110
[    1.547584]  ret_from_fork+0x10/0x18
[    1.551207] SMP: stopping secondary CPUs
[    1.555182] Kernel Offset: 0x31008e000000 from 0xffff800010000000
[    1.561354] PHYS_OFFSET: 0xffff8d8180000000
[    1.565589] CPU features: 0x0002,20806000
[    1.569647] Memory Limit: none



```

Any ideas why it's not seeing the rootfs?

---

