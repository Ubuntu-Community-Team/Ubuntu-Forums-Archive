---
title: "Android phone not mounting after update"
date: 2016-10-13
forum: General Help
---

### Post by sn0m on 2016-10-13
Hi
Updated the linux firmware to: 4.4.0-38-generic
I can't connect my android phone since than, it goes into a crazy loop trying to automount.
This is what I get from dmesg:

 ```
dmesg | grep error
[   14.372285] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   15.795696] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3160-17.ucode failed with error -2
[  129.481897] usb 2-2: device descriptor read/all, error -110
[  160.338766] usb 2-2: device not accepting address 30, error -71
[  198.811908] usb 2-2: device not accepting address 49, error -71
[  215.248436] usb 2-2: device descriptor read/all, error -110
[  217.856285] blk_update_request: I/O error, dev sdb, sector 2055
[  217.856322] blk_update_request: I/O error, dev sdb, sector 2056
[  217.856420] blk_update_request: I/O error, dev sdb, sector 2296
[  218.724541] usb 2-2: device not accepting address 59, error -71
[  224.836693] usb 2-2: device not accepting address 62, error -71
[  230.868923] usb 2-2: device descriptor read/all, error -110
[  236.293094] usb 2-2: device descriptor read/all, error -110
[  251.561572] usb 2-2: device descriptor read/all, error -110
[  263.849896] usb 2-2: device not accepting address 80, error -71
[  267.834382] blk_update_request: I/O error, dev sdb, sector 1032
[  267.834453] blk_update_request: I/O error, dev sdb, sector 1272
[  986.896912] blk_update_request: I/O error, dev sdb, sector 504806
[  986.896941] blk_update_request: I/O error, dev sdb, sector 504807
[  986.896953] blk_update_request: I/O error, dev sdb, sector 504808
[  986.900553] blk_update_request: I/O error, dev sdb, sector 504809
[  986.927938] Buffer I/O error on dev sdb, logical block 5454, lost async page write
[  999.700270] usb 2-2: device not accepting address 92, error -71
[ 1005.232438] usb 2-2: device not accepting address 96, error -71
[ 6228.111579] blk_update_request: I/O error, dev sr0, sector 16457608
[ 6228.179616] blk_update_request: I/O error, dev sr0, sector 16457608
[ 6228.179624] Buffer I/O error on dev sr0, logical block 4114402, async page read
[ 6228.247678] blk_update_request: I/O error, dev sr0, sector 16457612
[ 6228.247683] Buffer I/O error on dev sr0, logical block 4114403, async page read
[ 6228.315501] blk_update_request: I/O error, dev sr0, sector 16457608
[ 6228.315505] Buffer I/O error on dev sr0, logical block 4114402, async page read
[ 6228.387616] blk_update_request: I/O error, dev sr0, sector 16457612
[ 6228.387623] Buffer I/O error on dev sr0, logical block 4114403, async page read
[ 6243.091891] blk_update_request: I/O error, dev sr0, sector 16457608
[ 6243.091894] Buffer I/O error on dev sr0, logical block 4114402, async page read
[ 6243.159960] blk_update_request: I/O error, dev sr0, sector 16457612
[ 6243.159964] Buffer I/O error on dev sr0, logical block 4114403, async page read
[ 6243.227852] blk_update_request: I/O error, dev sr0, sector 16457608
[ 6243.227856] Buffer I/O error on dev sr0, logical block 4114402, async page read
[ 6243.295815] blk_update_request: I/O error, dev sr0, sector 16457612
[ 6243.295818] Buffer I/O error on dev sr0, logical block 4114403, async page read
[ 6246.640060] blk_update_request: I/O error, dev sr0, sector 16457608
[ 6246.640065] Buffer I/O error on dev sr0, logical block 4114402, async page read
[ 6246.708100] blk_update_request: I/O error, dev sr0, sector 16457612
[ 6246.708104] Buffer I/O error on dev sr0, logical block 4114403, async page read
[ 6246.780058] blk_update_request: I/O error, dev sr0, sector 16457608
[ 6246.780061] Buffer I/O error on dev sr0, logical block 4114402, async page read
[ 6246.848067] blk_update_request: I/O error, dev sr0, sector 16457612
[ 6246.848070] Buffer I/O error on dev sr0, logical block 4114403, async page read
[ 6285.673329] blk_update_request: I/O error, dev sr0, sector 16457608
[ 6285.673334] Buffer I/O error on dev sr0, logical block 4114402, async page read
[ 6285.773219] blk_update_request: I/O error, dev sr0, sector 16457612
[ 6285.773222] Buffer I/O error on dev sr0, logical block 4114403, async page read
[ 6285.869260] blk_update_request: I/O error, dev sr0, sector 16457608
[ 6285.869264] Buffer I/O error on dev sr0, logical block 4114402, async page read
[ 6285.957229] blk_update_request: I/O error, dev sr0, sector 16457612
[ 6285.957232] Buffer I/O error on dev sr0, logical block 4114403, async page read
[ 6319.722340] blk_update_request: I/O error, dev sr0, sector 16457608
[ 6319.722347] Buffer I/O error on dev sr0, logical block 4114402, async page read
[ 6319.986289] blk_update_request: I/O error, dev sr0, sector 16457612
[ 6319.986293] Buffer I/O error on dev sr0, logical block 4114403, async page read
[ 6338.986782] blk_update_request: I/O error, dev sr0, sector 393848
[ 6339.050770] blk_update_request: I/O error, dev sr0, sector 393848
[ 6339.050773] Buffer I/O error on dev sr0, logical block 98462, async page read
[ 6339.114805] blk_update_request: I/O error, dev sr0, sector 393852
[ 6339.114809] Buffer I/O error on dev sr0, logical block 98463, async page read
[11661.391654] usb 2-3: device not accepting address 118, error -71
[11667.927834] usb 2-3: device not accepting address 122, error -71
[11680.856242] usb 2-3: device not accepting address 7, error -71
[11681.672252] usb 2-3: device not accepting address 9, error -71
[11696.468712] usb 2-3: device not accepting address 16, error -71
[11777.667203] usb 2-3: device not accepting address 40, error -71
[11916.203418] usb 2-3: device descriptor read/all, error -110
[11938.680071] usb 2-3: device not accepting address 87, error -71
[11966.264940] usb 2-3: device not accepting address 100, error -71
[11991.109944] usb 2-3: can't set config #1, error -110
```


Is this a bug of some sort? Is there anything I can do to fix it. It was working perfect before.
Many thanks for your help
Koli

---

### Post by mastablasta on 2016-10-13
mounting with what protocol? USB or MTP?

does it still work if you boot with older kernel?

---

### Post by sn0m on 2016-11-07
yea, I keep an old kernel, on a desktop, precisely 4.4.0-31-generic. It works perfect with that one. The 4.4.0-45-generic gone absolutely crazy, now dosen't even do the loop thing. It makes me scared of updating or upgrading.
Ubuntu has to come out of this habit of braking things up with new updates and fixing them in the next upgrade.

---

