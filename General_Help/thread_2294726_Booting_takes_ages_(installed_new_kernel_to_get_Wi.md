---
title: "Booting takes ages (installed new kernel to get WiFi working)"
date: 2015-09-12
forum: General Help
---

### Post by swatto on 2015-09-12
Good Evening all,

I recently compiled and installed a new Kernel to get my WiFi card working in Ubuntu 15.04, but now booting takes ages (I get to the tty1 screen and it waits), please could someone let me know what is causing it, here is the dmesg:

```

[   11.872767] wlan0: associatedwlan0: associated
[   65.768715] nouveau 0000:01:00.0: Direct firmware load for nouveau/fuc409c failed with error -2
[   65.768720] nouveau 0000:01:00.0: Falling back to user helper
[  125.816547] nouveau E[  PGRAPH][0000:01:00.0] failed to load fuc409c
[  125.816599] vga_switcheroo: enabled
[  125.816710] [TTM] Zone  kernel: Available graphics memory: 8174514 kiB
[  125.816712] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[  125.816713] [TTM] Initializing pool allocator
[  125.816717] [TTM] Initializing DMA pool allocator
[  125.816727] nouveau  [     DRM] VRAM: 3072 MiB
[  125.816729] nouveau  [     DRM] GART: 1048576 MiB
[  125.816732] nouveau E[     DRM] Pointer to TMDS table invalid
[  125.816751] nouveau  [     DRM] DCB version 4.1
[  125.816753] nouveau E[     DRM] Pointer to flat panel table invalid
[  125.823539] nouveau E[   PFIFO][0000:01:00.0] unsupported engines 0x00000001
[  125.823635] nouveau E[     DRM] failed to create kernel channel, -22
[  125.832745] [drm] Initialized nouveau 1.2.2 20120801 for 0000:01:00.0 on minor 1
[  126.241942] lo uses DEPRECATED zero tx_queue_len - convert driver to use IFF_NO_QUEUE instead.
[  130.989648] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[  130.989924] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[  130.989928] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[  135.467538] lo uses DEPRECATED zero tx_queue_len - convert driver to use IFF_NO_QUEUE instead.
[  145.598798] lo uses DEPRECATED zero tx_queue_len - convert driver to use IFF_NO_QUEUE instead.
[  145.612717] lo uses DEPRECATED zero tx_queue_len - convert driver to use IFF_NO_QUEUE instead.
[  171.496283] lo uses DEPRECATED zero tx_queue_len - convert driver to use IFF_NO_QUEUE instead.
[  172.140034] SGI XFS with ACLs, security attributes, realtime, no debug enabled
[  172.163019] JFS: nTxBlock = 8192, nTxLock = 65536
[  172.184383] ntfs: driver 2.1.32 [Flags: R/O MODULE].
[  172.236604] QNX4 filesystem 0.2.3 registered.
[  172.326656] raid6: sse2x1   gen()  9992 MB/s
[  172.394705] raid6: sse2x1   xor()  8871 MB/s
[  172.462740] raid6: sse2x2   gen() 14106 MB/s
[  172.530788] raid6: sse2x2   xor()  9265 MB/s
[  172.598835] raid6: sse2x4   gen() 16412 MB/s
[  172.666883] raid6: sse2x4   xor() 11553 MB/s
[  172.734932] raid6: avx2x1   gen() 21162 MB/s
[  172.802978] raid6: avx2x2   gen() 25467 MB/s
[  172.871027] raid6: avx2x4   gen() 29286 MB/s
[  172.871038] raid6: using algorithm avx2x4 gen() 29286 MB/s
[  172.871039] raid6: using avx2x2 recovery algorithm
[  172.872970] xor: automatically using best checksumming function:
[  172.911053]    avx       : 33889.000 MB/sec
[  172.993319] Btrfs loaded
[  173.748899] EXT4-fs (dm-4): VFS: Can't find ext4 filesystem
[  173.750269] EXT4-fs (dm-4): VFS: Can't find ext4 filesystem
[  173.751276] EXT4-fs (dm-4): VFS: Can't find ext4 filesystem
[  173.752274] FAT-fs (dm-4): bogus number of reserved sectors
[  173.752277] FAT-fs (dm-4): Can't find a valid FAT filesystem
[  173.757296] XFS (dm-4): Invalid superblock magic number
[  173.760110] FAT-fs (dm-4): bogus number of reserved sectors
[  173.760113] FAT-fs (dm-4): Can't find a valid FAT filesystem
[  173.762837] VFS: Can't find a Minix filesystem V1 | V2 | V3 on device dm-4.
[  173.766548] hfsplus: unable to find HFS+ superblock
[  173.767506] qnx4: no qnx4 filesystem (no root dir).
[  173.768337] ufs: You didn't specify the type of your ufs filesystem

mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...

>>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[  173.768493] ufs: ufs_fill_super(): bad magic number
[  173.770482] hfs: can't find a HFS filesystem on dev dm-4

```

---

### Post by swatto on 2015-09-12
I fixed this by choosing a proprietary driver for my graphics card.  I did a search on nouveau and as it was related to graphics I thought I would give it a shot.  Would still be nice to know why it failed though.

---

