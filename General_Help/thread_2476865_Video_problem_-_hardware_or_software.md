---
title: "Video problem - hardware or software?"
date: 2022-07-09
forum: General Help
---

### Post by kurt18947 on 2022-07-09
This video lockup is occurring on a desktop machine. If I leave it alone for a few seconds it will often recover but I restart it anyway. It always happens in Firefox but that's no surprise, this machine spends 99% of its time in Firefox. MSI B450 MoBo, radeon HD7450 graphics card 16 GB system DRAM. OS is stock Ubuntu 20.04 updated. No PPAs, the only nonstandard thing I can think of is that LibreOffice is installed via FlatPak.  I'm going to attach a portion of the output of dmesg:

```
[22562.034829] rfkill: input handler enabled
[22562.043084] rfkill: input handler disabled
[22562.104718] Generic FE-GE Realtek PHY r8169-0-2500:00: attached PHY driver (mii_bus:phy_addr=r8169-0-2500:00, irq=MAC)
[22562.300842] r8169 0000:25:00.0 enp37s0: Link is Down
[22566.129749] r8169 0000:25:00.0 enp37s0: Link is Up - 1Gbps/Full - flow control rx/tx
[22566.129766] IPv6: ADDRCONF(NETDEV_CHANGE): enp37s0: link becomes ready
[25918.464533] radeon 0000:29:00.0: ring 3 stalled for more than 10240msec
[25918.464541] radeon 0000:29:00.0: ring 0 stalled for more than 10240msec
[25918.464543] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25918.464551] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25918.976340] radeon 0000:29:00.0: ring 0 stalled for more than 10752msec
[25918.976349] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25918.980340] radeon 0000:29:00.0: ring 3 stalled for more than 10756msec
[25918.980345] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25919.488335] radeon 0000:29:00.0: ring 3 stalled for more than 11264msec
[25919.488342] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25919.488356] radeon 0000:29:00.0: ring 0 stalled for more than 11264msec
[25919.488362] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25920.000554] radeon 0000:29:00.0: ring 3 stalled for more than 11776msec
[25920.000561] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25920.000561] radeon 0000:29:00.0: ring 0 stalled for more than 11776msec
[25920.000568] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25920.512537] radeon 0000:29:00.0: ring 0 stalled for more than 12288msec
[25920.512544] radeon 0000:29:00.0: ring 3 stalled for more than 12288msec
[25920.512547] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25920.512554] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25921.024348] radeon 0000:29:00.0: ring 3 stalled for more than 12800msec
[25921.024355] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25921.024536] radeon 0000:29:00.0: ring 0 stalled for more than 12800msec
[25921.024539] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25921.536352] radeon 0000:29:00.0: ring 0 stalled for more than 13312msec
[25921.536361] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25921.536379] radeon 0000:29:00.0: ring 3 stalled for more than 13312msec
[25921.536382] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25922.048351] radeon 0000:29:00.0: ring 3 stalled for more than 13824msec
[25922.048359] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25922.048376] radeon 0000:29:00.0: ring 0 stalled for more than 13824msec
[25922.048384] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25922.560384] radeon 0000:29:00.0: ring 0 stalled for more than 14336msec
[25922.560389] radeon 0000:29:00.0: ring 3 stalled for more than 14336msec
[25922.560390] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25922.560397] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25923.072556] radeon 0000:29:00.0: ring 3 stalled for more than 14848msec
[25923.072563] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25923.076569] radeon 0000:29:00.0: ring 0 stalled for more than 14852msec
[25923.076576] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25923.584375] radeon 0000:29:00.0: ring 0 stalled for more than 15360msec
[25923.584384] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25923.584401] radeon 0000:29:00.0: ring 3 stalled for more than 15360msec
[25923.584404] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25924.096391] radeon 0000:29:00.0: ring 3 stalled for more than 15872msec
[25924.096395] radeon 0000:29:00.0: ring 0 stalled for more than 15872msec
[25924.096400] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25924.096401] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25924.608586] radeon 0000:29:00.0: ring 0 stalled for more than 16384msec
[25924.608590] radeon 0000:29:00.0: ring 3 stalled for more than 16384msec
[25924.608593] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25924.608596] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25925.120586] radeon 0000:29:00.0: ring 3 stalled for more than 16896msec
[25925.120593] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25925.120609] radeon 0000:29:00.0: ring 0 stalled for more than 16896msec
[25925.120612] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25925.632387] radeon 0000:29:00.0: ring 0 stalled for more than 17408msec
[25925.632394] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25925.632409] radeon 0000:29:00.0: ring 3 stalled for more than 17408msec
[25925.632412] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25926.144590] radeon 0000:29:00.0: ring 3 stalled for more than 17920msec
[25926.144595] radeon 0000:29:00.0: ring 0 stalled for more than 17920msec
[25926.144599] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25926.144602] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25926.656407] radeon 0000:29:00.0: ring 0 stalled for more than 18432msec
[25926.656416] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25926.656594] radeon 0000:29:00.0: ring 3 stalled for more than 18432msec
[25926.656596] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25927.168610] radeon 0000:29:00.0: ring 3 stalled for more than 18944msec
[25927.168617] radeon 0000:29:00.0: ring 0 stalled for more than 18944msec
[25927.168618] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25927.168625] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25927.680407] radeon 0000:29:00.0: ring 3 stalled for more than 19456msec
[25927.680415] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25927.684800] radeon 0000:29:00.0: ring 0 stalled for more than 19460msec
[25927.684807] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25928.192416] radeon 0000:29:00.0: ring 0 stalled for more than 19968msec
[25928.192423] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25928.192438] radeon 0000:29:00.0: ring 3 stalled for more than 19968msec
[25928.192442] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25928.704623] radeon 0000:29:00.0: ring 3 stalled for more than 20480msec
[25928.704628] radeon 0000:29:00.0: ring 0 stalled for more than 20480msec
[25928.704630] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25928.704635] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25929.216411] radeon 0000:29:00.0: ring 0 stalled for more than 20992msec
[25929.216417] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25929.216432] radeon 0000:29:00.0: ring 3 stalled for more than 20992msec
[25929.216435] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25929.728491] radeon 0000:29:00.0: ring 3 stalled for more than 21504msec
[25929.728498] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25929.728506] radeon 0000:29:00.0: ring 0 stalled for more than 21504msec
[25929.728514] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25930.240417] radeon 0000:29:00.0: ring 3 stalled for more than 22016msec
[25930.240424] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25930.244439] radeon 0000:29:00.0: ring 0 stalled for more than 22020msec
[25930.244447] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25930.752768] radeon 0000:29:00.0: ring 0 stalled for more than 22528msec
[25930.752777] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25930.752790] radeon 0000:29:00.0: ring 3 stalled for more than 22528msec
[25930.752798] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25931.264650] radeon 0000:29:00.0: ring 0 stalled for more than 23040msec
[25931.264657] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25931.264661] radeon 0000:29:00.0: ring 3 stalled for more than 23040msec
[25931.264668] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25931.776440] radeon 0000:29:00.0: ring 3 stalled for more than 23552msec
[25931.776447] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25931.776651] radeon 0000:29:00.0: ring 0 stalled for more than 23552msec
[25931.776654] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25932.288682] radeon 0000:29:00.0: ring 0 stalled for more than 24064msec
[25932.288688] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25932.288704] radeon 0000:29:00.0: ring 3 stalled for more than 24064msec
[25932.288707] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25932.800440] radeon 0000:29:00.0: ring 3 stalled for more than 24576msec
[25932.800447] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25932.800463] radeon 0000:29:00.0: ring 0 stalled for more than 24576msec
[25932.800466] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25933.312542] radeon 0000:29:00.0: ring 0 stalled for more than 25088msec
[25933.312545] radeon 0000:29:00.0: ring 3 stalled for more than 25088msec
[25933.312551] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000685f1f last fence id 0x0000000000685f21 on ring 3)
[25933.312557] radeon 0000:29:00.0: GPU lockup (current fence id 0x0000000000199eb5 last fence id 0x0000000000199ebd on ring 0)
[25933.630749] radeon 0000:29:00.0: Saved 247 dwords of commands on ring 0.
[25933.630772] radeon 0000:29:00.0: GPU softreset: 0x0000000C
[25933.630776] radeon 0000:29:00.0:   GRBM_STATUS               = 0xA0001828
[25933.630779] radeon 0000:29:00.0:   GRBM_STATUS_SE0           = 0x00000003
[25933.630781] radeon 0000:29:00.0:   GRBM_STATUS_SE1           = 0x00000007
[25933.630784] radeon 0000:29:00.0:   SRBM_STATUS               = 0x200000C0
[25933.630786] radeon 0000:29:00.0:   SRBM_STATUS2              = 0x00000000
[25933.630788] radeon 0000:29:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[25933.630791] radeon 0000:29:00.0:   R_008678_CP_STALLED_STAT2 = 0x00004000
[25933.630793] radeon 0000:29:00.0:   R_00867C_CP_BUSY_STAT     = 0x00020186
[25933.630795] radeon 0000:29:00.0:   R_008680_CP_STAT          = 0x80028647
[25933.630798] radeon 0000:29:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83146
[25933.647941] radeon 0000:29:00.0: GRBM_SOFT_RESET=0x00004001
[25933.647995] radeon 0000:29:00.0: SRBM_SOFT_RESET=0x00100100
[25933.649143] radeon 0000:29:00.0:   GRBM_STATUS               = 0x00001828
[25933.649146] radeon 0000:29:00.0:   GRBM_STATUS_SE0           = 0x00000003
[25933.649148] radeon 0000:29:00.0:   GRBM_STATUS_SE1           = 0x00000007
[25933.649150] radeon 0000:29:00.0:   SRBM_STATUS               = 0x200000C0
[25933.649151] radeon 0000:29:00.0:   SRBM_STATUS2              = 0x00000000
[25933.649153] radeon 0000:29:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[25933.649155] radeon 0000:29:00.0:   R_008678_CP_STALLED_STAT2 = 0x00000000
[25933.649156] radeon 0000:29:00.0:   R_00867C_CP_BUSY_STAT     = 0x00000000
[25933.649158] radeon 0000:29:00.0:   R_008680_CP_STAT          = 0x00000000
[25933.649160] radeon 0000:29:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[25933.649180] radeon 0000:29:00.0: GPU reset succeeded, trying to resume
[25933.671639] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[25933.677303] [drm] PCIE GART of 1024M enabled (table at 0x0000000000162000).
[25933.677406] radeon 0000:29:00.0: WB enabled
[25933.677407] radeon 0000:29:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00
[25933.677409] radeon 0000:29:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c
[25933.678152] radeon 0000:29:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118
[25933.678352] debugfs: File 'radeon_ring_gfx' in directory '0' already present!
[25933.678356] debugfs: File 'radeon_ring_dma1' in directory '0' already present!
[25933.694306] [drm] ring test on 0 succeeded in 2 usecs
[25933.694318] [drm] ring test on 3 succeeded in 5 usecs
[25933.694319] debugfs: File 'radeon_ring_uvd' in directory '0' already present!
[25933.870097] [drm] ring test on 5 succeeded in 2 usecs
[25933.870110] [drm] UVD initialized successfully.
[25934.026345] [drm] ib test on ring 0 succeeded in 0 usecs
[25934.026397] [drm] ib test on ring 3 succeeded in 0 usecs
[25935.200477] [drm] ib test on ring 5 succeeded
[25959.503219] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c000 flags=0x0010]
[25959.503232] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c0a0 flags=0x0010]
[25959.503240] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c0e0 flags=0x0010]
[25959.503248] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c140 flags=0x0010]
[25959.503255] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c160 flags=0x0010]
[25959.503261] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c180 flags=0x0010]
[25959.503268] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c280 flags=0x0010]
[25959.503274] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c300 flags=0x0010]
[25959.503281] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c380 flags=0x0010]
[25959.503287] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c580 flags=0x0010]
[25959.503293] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c5a0 flags=0x0010]
[25959.503301] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c6a0 flags=0x0010]
[25959.503307] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c6c0 flags=0x0010]
[25959.503314] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c8a0 flags=0x0010]
[25960.496446] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00ccc0 flags=0x0010]
[25961.496474] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00cd40 flags=0x0010]
[25969.600710] radeon 0000:29:00.0: ring 0 stalled for more than 10108msec
[25969.600718] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25970.112714] radeon 0000:29:00.0: ring 0 stalled for more than 10620msec
[25970.112723] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25970.208714] radeon 0000:29:00.0: ring 3 stalled for more than 10240msec
[25970.208720] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25970.624717] radeon 0000:29:00.0: ring 0 stalled for more than 11132msec
[25970.624725] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25970.720718] radeon 0000:29:00.0: ring 3 stalled for more than 10752msec
[25970.720724] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25971.136714] radeon 0000:29:00.0: ring 0 stalled for more than 11644msec
[25971.136720] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25971.232738] radeon 0000:29:00.0: ring 3 stalled for more than 11264msec
[25971.232743] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25971.648941] radeon 0000:29:00.0: ring 0 stalled for more than 12156msec
[25971.648950] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25971.744750] radeon 0000:29:00.0: ring 3 stalled for more than 11776msec
[25971.744757] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25972.160748] radeon 0000:29:00.0: ring 0 stalled for more than 12668msec
[25972.160757] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25972.256751] radeon 0000:29:00.0: ring 3 stalled for more than 12288msec
[25972.256757] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25972.672758] radeon 0000:29:00.0: ring 0 stalled for more than 13180msec
[25972.672769] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25972.768946] radeon 0000:29:00.0: ring 3 stalled for more than 12800msec
[25972.768952] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25973.184748] radeon 0000:29:00.0: ring 0 stalled for more than 13692msec
[25973.184756] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25973.280945] radeon 0000:29:00.0: ring 3 stalled for more than 13312msec
[25973.280952] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25973.696945] radeon 0000:29:00.0: ring 0 stalled for more than 14204msec
[25973.696952] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25973.792739] radeon 0000:29:00.0: ring 3 stalled for more than 13824msec
[25973.792745] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25974.208966] radeon 0000:29:00.0: ring 0 stalled for more than 14716msec
[25974.208976] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25974.304764] radeon 0000:29:00.0: ring 3 stalled for more than 14336msec
[25974.304770] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25974.720767] radeon 0000:29:00.0: ring 0 stalled for more than 15228msec
[25974.720776] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25974.816770] radeon 0000:29:00.0: ring 3 stalled for more than 14848msec
[25974.816777] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25975.232969] radeon 0000:29:00.0: ring 0 stalled for more than 15740msec
[25975.232978] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25975.328754] radeon 0000:29:00.0: ring 3 stalled for more than 15360msec
[25975.328763] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25975.748749] radeon 0000:29:00.0: ring 0 stalled for more than 16256msec
[25975.748755] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25975.840758] radeon 0000:29:00.0: ring 3 stalled for more than 15872msec
[25975.840766] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25976.256758] radeon 0000:29:00.0: ring 0 stalled for more than 16764msec
[25976.256767] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25976.356763] radeon 0000:29:00.0: ring 3 stalled for more than 16388msec
[25976.356769] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25976.768761] radeon 0000:29:00.0: ring 0 stalled for more than 17276msec
[25976.768770] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25976.864764] radeon 0000:29:00.0: ring 3 stalled for more than 16896msec
[25976.864770] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25977.280768] radeon 0000:29:00.0: ring 0 stalled for more than 17788msec
[25977.280777] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25977.376778] radeon 0000:29:00.0: ring 3 stalled for more than 17408msec
[25977.376787] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25977.792792] radeon 0000:29:00.0: ring 0 stalled for more than 18300msec
[25977.792799] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25977.888792] radeon 0000:29:00.0: ring 3 stalled for more than 17920msec
[25977.888799] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25978.304789] radeon 0000:29:00.0: ring 0 stalled for more than 18812msec
[25978.304797] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25978.401007] radeon 0000:29:00.0: ring 3 stalled for more than 18432msec
[25978.401014] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25978.816797] radeon 0000:29:00.0: ring 0 stalled for more than 19324msec
[25978.816807] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25978.912796] radeon 0000:29:00.0: ring 3 stalled for more than 18944msec
[25978.912800] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25979.328776] radeon 0000:29:00.0: ring 0 stalled for more than 19836msec
[25979.328779] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25979.424825] radeon 0000:29:00.0: ring 3 stalled for more than 19456msec
[25979.424834] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25979.840826] radeon 0000:29:00.0: ring 0 stalled for more than 20348msec
[25979.840833] radeon 0000:29:00.0: GPU lockup (current fence id 0x000000000019a2e9 last fence id 0x000000000019a2f0 on ring 0)
[25979.936808] radeon 0000:29:00.0: ring 3 stalled for more than 19968msec
[25979.936818] radeon 0000:29:00.0: GPU lockup (current fence id 0x00000000006862cd last fence id 0x00000000006862ce on ring 3)
[25980.457672] radeon 0000:29:00.0: Saved 215 dwords of commands on ring 0.
[25980.457697] radeon 0000:29:00.0: GPU softreset: 0x0000000C
[25980.457701] radeon 0000:29:00.0:   GRBM_STATUS               = 0xA0003828
[25980.457704] radeon 0000:29:00.0:   GRBM_STATUS_SE0           = 0x00000007
[25980.457706] radeon 0000:29:00.0:   GRBM_STATUS_SE1           = 0x00000007
[25980.457709] radeon 0000:29:00.0:   SRBM_STATUS               = 0x200000C0
[25980.457711] radeon 0000:29:00.0:   SRBM_STATUS2              = 0x00000000
[25980.457713] radeon 0000:29:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[25980.457715] radeon 0000:29:00.0:   R_008678_CP_STALLED_STAT2 = 0x00010002
[25980.457718] radeon 0000:29:00.0:   R_00867C_CP_BUSY_STAT     = 0x00020186
[25980.457720] radeon 0000:29:00.0:   R_008680_CP_STAT          = 0x80038647
[25980.457722] radeon 0000:29:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83146
[25980.472039] radeon 0000:29:00.0: GRBM_SOFT_RESET=0x00004001
[25980.472097] radeon 0000:29:00.0: SRBM_SOFT_RESET=0x00100100
[25980.473248] radeon 0000:29:00.0:   GRBM_STATUS               = 0x00003828
[25980.473252] radeon 0000:29:00.0:   GRBM_STATUS_SE0           = 0x00000007
[25980.473255] radeon 0000:29:00.0:   GRBM_STATUS_SE1           = 0x00000007
[25980.473257] radeon 0000:29:00.0:   SRBM_STATUS               = 0x200000C0
[25980.473260] radeon 0000:29:00.0:   SRBM_STATUS2              = 0x00000000
[25980.473263] radeon 0000:29:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[25980.473265] radeon 0000:29:00.0:   R_008678_CP_STALLED_STAT2 = 0x00000000
[25980.473268] radeon 0000:29:00.0:   R_00867C_CP_BUSY_STAT     = 0x00000000
[25980.473270] radeon 0000:29:00.0:   R_008680_CP_STAT          = 0x00000000
[25980.473273] radeon 0000:29:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[25980.473294] radeon 0000:29:00.0: GPU reset succeeded, trying to resume
[25980.495969] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[25980.503178] [drm] PCIE GART of 1024M enabled (table at 0x0000000000162000).
[25980.503283] radeon 0000:29:00.0: WB enabled
[25980.503285] radeon 0000:29:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00
[25980.503288] radeon 0000:29:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c
[25980.504031] radeon 0000:29:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118
[25980.504229] debugfs: File 'radeon_ring_gfx' in directory '0' already present!
[25980.504235] debugfs: File 'radeon_ring_dma1' in directory '0' already present!
[25980.520193] [drm] ring test on 0 succeeded in 2 usecs
[25980.520207] [drm] ring test on 3 succeeded in 5 usecs
[25980.520209] debugfs: File 'radeon_ring_uvd' in directory '0' already present!
[25980.696040] [drm] ring test on 5 succeeded in 2 usecs
[25980.696053] [drm] UVD initialized successfully.
[25980.798479] amd_iommu_report_page_fault: 6 callbacks suppressed
[25980.798483] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c000 flags=0x0010]
[25980.798493] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c0a0 flags=0x0010]
[25980.798500] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c0c0 flags=0x0010]
[25980.798507] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c0e0 flags=0x0010]
[25980.798514] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c100 flags=0x0010]
[25980.798520] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c120 flags=0x0010]
[25980.798527] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c140 flags=0x0010]
[25980.798533] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c160 flags=0x0010]
[25980.798540] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c180 flags=0x0010]
[25980.798546] radeon 0000:29:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x0010 address=0xffff00c1c0 flags=0x0010]
[25980.798553] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c1e0 flags=0x0010]
[25980.798560] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c220 flags=0x0010]
[25980.798567] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c240 flags=0x0010]
[25980.798573] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c260 flags=0x0010]
[25980.798579] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c280 flags=0x0010]
[25980.798586] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c2a0 flags=0x0010]
[25980.798592] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c2c0 flags=0x0010]
[25980.798598] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c300 flags=0x0010]
[25980.798604] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c320 flags=0x0010]
[25980.798610] AMD-Vi: Event logged [IO_PAGE_FAULT device=29:00.0 domain=0x0010 address=0xffff00c360 flags=0x0010]
[25981.888934] [drm:r600_ib_test [radeon]] *ERROR* radeon: fence wait timed out.
[25981.888994] [drm:radeon_ib_ring_tests [radeon]] *ERROR* radeon: failed testing IB on GFX ring (-110).
[25982.002054] radeon 0000:29:00.0: GPU softreset: 0x00000008
[25982.002061] radeon 0000:29:00.0:   GRBM_STATUS               = 0xA0003828
[25982.002064] radeon 0000:29:00.0:   GRBM_STATUS_SE0           = 0x00000007
[25982.002067] radeon 0000:29:00.0:   GRBM_STATUS_SE1           = 0x00000007
[25982.002069] radeon 0000:29:00.0:   SRBM_STATUS               = 0x20000AC0
[25982.002071] radeon 0000:29:00.0:   SRBM_STATUS2              = 0x00000000
[25982.002074] radeon 0000:29:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[25982.002076] radeon 0000:29:00.0:   R_008678_CP_STALLED_STAT2 = 0x00010002
[25982.002078] radeon 0000:29:00.0:   R_00867C_CP_BUSY_STAT     = 0x00020184
[25982.002081] radeon 0000:29:00.0:   R_008680_CP_STAT          = 0x80038647
[25982.002084] radeon 0000:29:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[25982.017532] radeon 0000:29:00.0: GRBM_SOFT_RESET=0x00004001
[25982.017586] radeon 0000:29:00.0: SRBM_SOFT_RESET=0x00000100
[25982.018734] radeon 0000:29:00.0:   GRBM_STATUS               = 0x00003828
[25982.018736] radeon 0000:29:00.0:   GRBM_STATUS_SE0           = 0x00000007
[25982.018737] radeon 0000:29:00.0:   GRBM_STATUS_SE1           = 0x00000007
[25982.018739] radeon 0000:29:00.0:   SRBM_STATUS               = 0x200000C0
[25982.018741] radeon 0000:29:00.0:   SRBM_STATUS2              = 0x00000000
[25982.018742] radeon 0000:29:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[25982.018744] radeon 0000:29:00.0:   R_008678_CP_STALLED_STAT2 = 0x00000000
[25982.018745] radeon 0000:29:00.0:   R_00867C_CP_BUSY_STAT     = 0x00000000
[25982.018747] radeon 0000:29:00.0:   R_008680_CP_STAT          = 0x00000000
[25982.018749] radeon 0000:29:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[25982.018769] radeon 0000:29:00.0: GPU reset succeeded, trying to resume
[25982.041249] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[25982.046860] [drm] PCIE GART of 1024M enabled (table at 0x0000000000162000).
[25982.046963] radeon 0000:29:00.0: WB enabled
[25982.046965] radeon 0000:29:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00
[25982.046966] radeon 0000:29:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c
[25982.047709] radeon 0000:29:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118
[25982.047910] debugfs: File 'radeon_ring_gfx' in directory '0' already present!
[25982.047914] debugfs: File 'radeon_ring_dma1' in directory '0' already present!
[25982.063863] [drm] ring test on 0 succeeded in 2 usecs
[25982.063876] [drm] ring test on 3 succeeded in 5 usecs
[25982.063877] debugfs: File 'radeon_ring_uvd' in directory '0' already present!
[25982.239639] [drm] ring test on 5 succeeded in 2 usecs
[25982.239651] [drm] UVD initialized successfully.
[25982.412380] [drm] ib test on ring 0 succeeded in 0 usecs
[25982.412432] [drm] ib test on ring 3 succeeded in 0 usecs
[25983.584843] [drm] ib test on ring 5 succeeded
[36528.762842] kauditd_printk_skb: 37 callbacks suppressed
[36528.762845] audit: type=1326 audit(1657406410.306:69): auid=1001 uid=1001 gid=1001 ses=3 subj=snap.thunderbird.thunderbird pid=37852 comm="thunderbird-bin" exe="/snap/thunderbird/228/thunderbird-bin" sig=0 arch=c000003e syscall=314 compat=0 ip=0x7fb49ab1473d code=0x50000
[37021.189880] r8169 0000:25:00.0 enp37s0: Link is Down
[37022.365673] PM: suspend entry (deep)
[37022.367522] Filesystems sync: 0.001 seconds
[37022.612072] Freezing user space processes ... (elapsed 0.001 seconds) done.
[37022.613980] OOM killer disabled.
[37022.613981] Freezing remaining freezable tasks ... (elapsed 0.006 seconds) done.
[37022.620318] printk: Suspending console(s) (use no_console_suspend to debug)
[37022.624141] serial 00:04: disabled
[37022.624357] parport_pc 00:03: disabled
[37023.140606] ACPI: Preparing to enter system sleep state S3
[37023.464957] PM: Saving platform NVS memory
[37023.464990] Disabling non-boot CPUs ...
[37023.467539] smpboot: CPU 1 is now offline
[37023.470767] smpboot: CPU 2 is now offline
[37023.473850] smpboot: CPU 3 is now offline
[37023.476706] smpboot: CPU 4 is now offline
[37023.479423] smpboot: CPU 5 is now offline
[37023.481952] smpboot: CPU 6 is now offline
[37023.483448] irq_migrate_all_off_this_cpu: 10 callbacks suppressed
[37023.483451] IRQ 44: no longer affine to CPU7
[37023.483457] IRQ 47: no longer affine to CPU7
[37023.483462] IRQ 51: no longer affine to CPU7
[37023.483468] IRQ 74: no longer affine to CPU7
[37023.484487] smpboot: CPU 7 is now offline
[37023.485958] IRQ 46: no longer affine to CPU8
[37023.485968] IRQ 50: no longer affine to CPU8
[37023.485975] IRQ 71: no longer affine to CPU8
[37023.485983] IRQ 75: no longer affine to CPU8
[37023.486989] smpboot: CPU 8 is now offline
[37023.488488] IRQ 27: no longer affine to CPU9
[37023.488496] IRQ 28: no longer affine to CPU9
[37023.489525] smpboot: CPU 9 is now offline
[37023.491723] smpboot: CPU 10 is now offline
[37023.493882] smpboot: CPU 11 is now offline
[37023.495052] ACPI: Low-level resume complete
[37023.49
```

I don't know what this line means:

```
[drm:radeon_ib_ring_tests [radeon]] *ERROR* radeon: failed testing IB on GFX ring (-110).
```
but I don't think it's good.

I have no clue what the vast majority of that means but words like GPU lockup, IO_PAGE_FAULT, ring 0 stalled, ring 3 stalled don't look good. Unfortunately the different text colors didn't copy over. I guess the first question is what is likely, hardware problem or software/driver problem? I don't have a spare AMD Radeon card or I'd swap cards and see if the problem reoccurs. Thanks for any thoughts or insights.

---

### Post by &amp;KyT$0P# on 2022-07-09
What kernel version are you using?
Did this start around the same time as a kernel update?

---

### Post by kurt18947 on 2022-07-10
> **halogen2 said:**
> What kernel version are you using?
Did this start around the same time as a kernel update?

Interesting thought, thanks. Maybe I'll try an earlier kernel and see if that makes a difference. I don't really recall when this started but mid June is about right.

```
5.13.0-52-generic #59~20.04.1-Ubuntu SMP Thu Jun 16 21:21:28 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux


```

---

### Post by kurt18947 on 2022-07-12
UPDATE

I've tried different combinations of kernels and display servers and I was still getting graphics lockups. I decided to unplug one monitor; I've had two for a couple years working well. I've not had a video failure since and it's been a couple days. That sure makes it look like a hardware issue to me. I've ordered an AMD pull from Ebay and should be here in a couple days. I'm going to mark this solved and will amend if the different video card doesn't fix it long term.

---

### Post by t55am on 2022-12-01
I have same with Radeon R7 250 on Fedora 36. Tested it with kernels starting from 5.14 up to 6.0.10. Created bug about it in Freedesktop: [https://gitlab.freedesktop.org/drm/amd/-/issues/2252](https://gitlab.freedesktop.org/drm/amd/-/issues/2252)
Please add there your comment when this is the only right place to do so. The more comments with confirmations of the problem the better chance to get the fix. 

Thanks!

---

