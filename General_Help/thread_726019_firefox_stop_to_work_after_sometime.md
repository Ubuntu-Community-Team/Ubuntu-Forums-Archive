---
title: "firefox stop to work after sometime"
date: 2008-03-16
forum: General Help
---

### Post by il-mArCi0 on 2008-03-16
i've got ubuntu gutsy.
after about 30 minutes that i'm connected to internet firefox stop to work while all other programs (nicotine, amule) continues to work.
any suggestion?

---

### Post by danwood76 on 2008-03-16
What does firefox say in the bottom left hand corner (status bar) when it stops working?

It might say something like 'looking up xxxxxx.com'

It could be that its loosing the DNS for some reason, and amule and so on have already resolved IP addresses.

---

### Post by il-mArCi0 on 2008-03-16
> **danwood76 said:**
> What does firefox say in the bottom left hand corner (status bar) when it stops working?

It might say something like 'looking up xxxxxx.com'

It could be that its loosing the DNS for some reason, and amule and so on have already resolved IP addresses.

it says
"address not resolved"

---

### Post by sports fan Matt on 2008-03-16
What occurs  if you try [http://swiftweasel.tuxfamily.org/..SWiftweasel](http://swiftweasel.tuxfamily.org/..SWiftweasel) is an optimized build of firefox..It may be a dns issue but there is that as well..

---

### Post by Michalxo on 2008-03-16
What version of firefox do you use, addons, etc? Maybe you should try newest one or switfox / opera
I has started using FF 3 beta 4 today and it runs flawlessly ;)

---

### Post by il-mArCi0 on 2008-03-16
> **Michalxo said:**
> What version of firefox do you use, addons, etc? Maybe you should try newest one or switfox / opera
I has started using FF 3 beta 4 today and it runs flawlessly ;)
i tried with swiftfox..but same problem!

i can't surf the web and download the synaptic packets but i listen to audio streaming and amule keeps alive.
i post the dmesg result:

```
[  127.728000] ieee80211_crypt: registered algorithm 'NULL'
[  127.748000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  127.748000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  127.940000] usb 4-3: reset high speed USB device using ehci_hcd and address 3
[  128.184000] usb 4-3: firmware version 0x4330 and device bootcode version 0x4810 differ
[  128.280000] zd1211rw 4-3:1.0: firmware version 4605
[  128.324000] zd1211rw 4-3:1.0: zd1211 chip 0ace:1211 v4810 high 00-0e-2e AL2230_RF pa0 -----
[  128.328000] zd1211rw 4-3:1.0: eth1
[  128.328000] usbcore: registered new interface driver zd1211rw
[  133.980000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  134.568000] eth0: link down
[  134.568000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  134.592000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  134.764000] NET: Registered protocol family 17
[  135.168000] SoftMAC: Open Authentication completed with 00:19:3e:ed:6b:3b
[  135.180000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  135.228000] ieee80211_crypt: registered algorithm 'TKIP'
[  145.192000] eth1: no IPv6 routers present
[  155.512000] PPP generic driver version 2.4.2
[  155.804000] NET: Registered protocol family 24
[  156.680000] ip_tables: (C) 2000-2006 Netfilter Core Team
[13970.212000] UDF-fs: No VRS found
[13970.284000] ISO 9660 Extensions: Microsoft Joliet Level 3
[13970.404000] ISOFS: changing to secondary root
[14004.456000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[14004.456000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[14004.456000] ide: failed opcode was: unknown
[14004.456000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x11  ascq: 0x05
[14004.456000] end_request: I/O error, dev hdc, sector 7541324
[14004.456000] Buffer I/O error on device hdc, logical block 1885331
[14004.456000] Buffer I/O error on device hdc, logical block 1885332
[14006.044000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14006.044000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14006.044000] ide: failed opcode was: unknown
[14006.044000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14006.044000] end_request: I/O error, dev hdc, sector 7541324
[14006.044000] Buffer I/O error on device hdc, logical block 1885331
[14006.044000] Buffer I/O error on device hdc, logical block 1885332
[14007.120000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14007.120000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14007.120000] ide: failed opcode was: unknown
[14007.120000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14007.120000] end_request: I/O error, dev hdc, sector 7541324
[14007.120000] Buffer I/O error on device hdc, logical block 1885331
[14008.148000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14008.148000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14008.148000] ide: failed opcode was: unknown
[14008.148000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14008.148000] end_request: I/O error, dev hdc, sector 7541328
[14008.148000] Buffer I/O error on device hdc, logical block 1885332
[14009.532000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14009.532000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14009.532000] ide: failed opcode was: unknown
[14009.532000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14009.532000] end_request: I/O error, dev hdc, sector 5978828
[14009.532000] Buffer I/O error on device hdc, logical block 1494707
[14009.532000] Buffer I/O error on device hdc, logical block 1494708
[14010.428000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14010.428000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14010.428000] ide: failed opcode was: unknown
[14010.428000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14010.428000] end_request: I/O error, dev hdc, sector 5978828
[14010.428000] Buffer I/O error on device hdc, logical block 1494707
[14010.428000] Buffer I/O error on device hdc, logical block 1494708
[14011.720000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14011.720000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14011.720000] ide: failed opcode was: unknown
[14011.720000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14011.720000] end_request: I/O error, dev hdc, sector 7541324
[14011.720000] Buffer I/O error on device hdc, logical block 1885331
[14012.808000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14012.808000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14012.808000] ide: failed opcode was: unknown
[14012.808000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14012.808000] end_request: I/O error, dev hdc, sector 5978828
[14014.100000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14014.100000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14014.100000] ide: failed opcode was: unknown
[14014.100000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14014.100000] end_request: I/O error, dev hdc, sector 7541324
[14015.360000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14015.360000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14015.360000] ide: failed opcode was: unknown
[14015.360000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14015.360000] end_request: I/O error, dev hdc, sector 5978828
[14015.360000] printk: 5 messages suppressed.
[14015.360000] Buffer I/O error on device hdc, logical block 1494707
[14016.300000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14016.300000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14016.300000] ide: failed opcode was: unknown
[14016.300000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14016.300000] end_request: I/O error, dev hdc, sector 5978828
[14017.240000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14017.240000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14017.240000] ide: failed opcode was: unknown
[14017.240000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14017.240000] end_request: I/O error, dev hdc, sector 5978828
[14018.180000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14018.180000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14018.180000] ide: failed opcode was: unknown
[14018.180000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14018.180000] end_request: I/O error, dev hdc, sector 5978828
[14019.120000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14019.120000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14019.120000] ide: failed opcode was: unknown
[14019.120000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14019.120000] end_request: I/O error, dev hdc, sector 5978828
[14020.060000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14020.060000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14020.060000] ide: failed opcode was: unknown
[14020.060000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14020.060000] end_request: I/O error, dev hdc, sector 5978828
[14020.060000] printk: 9 messages suppressed.
[14020.060000] Buffer I/O error on device hdc, logical block 1494707
[14021.000000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14021.000000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14021.000000] ide: failed opcode was: unknown
[14021.000000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14021.000000] end_request: I/O error, dev hdc, sector 5978828
[14021.940000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14021.940000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14021.940000] ide: failed opcode was: unknown
[14021.940000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14021.940000] end_request: I/O error, dev hdc, sector 5978828
[14022.880000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14022.880000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14022.880000] ide: failed opcode was: unknown
[14022.880000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14022.880000] end_request: I/O error, dev hdc, sector 5978828
[14023.820000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14023.820000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14023.820000] ide: failed opcode was: unknown
[14023.820000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14023.820000] end_request: I/O error, dev hdc, sector 5978828
[14025.328000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14025.328000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14025.328000] ide: failed opcode was: unknown
[14025.328000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14025.328000] end_request: I/O error, dev hdc, sector 5978828
[14025.328000] printk: 9 messages suppressed.
[14025.328000] Buffer I/O error on device hdc, logical block 1494707
[14026.520000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14026.520000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14026.520000] ide: failed opcode was: unknown
[14026.520000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14026.520000] end_request: I/O error, dev hdc, sector 7526772
[14027.700000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14027.700000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14027.700000] ide: failed opcode was: unknown
[14027.700000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14027.700000] end_request: I/O error, dev hdc, sector 5978828
[14028.844000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14028.844000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14028.844000] ide: failed opcode was: unknown
[14028.848000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14028.848000] end_request: I/O error, dev hdc, sector 7526772
[14049.876000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14049.876000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14049.876000] ide: failed opcode was: unknown
[14049.876000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14049.876000] end_request: I/O error, dev hdc, sector 7541324
[14049.876000] printk: 7 messages suppressed.
[14049.876000] Buffer I/O error on device hdc, logical block 1885331
[14049.876000] Buffer I/O error on device hdc, logical block 1885332
[14050.904000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14050.904000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14050.904000] ide: failed opcode was: unknown
[14050.904000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14050.904000] end_request: I/O error, dev hdc, sector 7541324
[14050.904000] Buffer I/O error on device hdc, logical block 1885331
[14050.904000] Buffer I/O error on device hdc, logical block 1885332
[14051.932000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14051.932000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14051.932000] ide: failed opcode was: unknown
[14051.932000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14051.932000] end_request: I/O error, dev hdc, sector 7541324
[14051.932000] Buffer I/O error on device hdc, logical block 1885331
[14053.188000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14053.188000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14053.188000] ide: failed opcode was: unknown
[14053.188000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14053.188000] end_request: I/O error, dev hdc, sector 5978828
[14054.128000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14054.128000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14054.128000] ide: failed opcode was: unknown
[14054.128000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14054.128000] end_request: I/O error, dev hdc, sector 5978828
[14055.068000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14055.068000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14055.068000] ide: failed opcode was: unknown
[14055.068000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14055.068000] end_request: I/O error, dev hdc, sector 5978828
[14055.068000] printk: 5 messages suppressed.
[14055.068000] Buffer I/O error on device hdc, logical block 1494707
[14056.008000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14056.008000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14056.008000] ide: failed opcode was: unknown
[14056.008000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14056.008000] end_request: I/O error, dev hdc, sector 5978828
[14056.944000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14056.944000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14056.944000] ide: failed opcode was: unknown
[14056.948000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14056.948000] end_request: I/O error, dev hdc, sector 5978828
[14057.884000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14057.884000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14057.884000] ide: failed opcode was: unknown
[14057.888000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14057.888000] end_request: I/O error, dev hdc, sector 5978828
[14058.824000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14058.824000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14058.824000] ide: failed opcode was: unknown
[14058.824000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14058.824000] end_request: I/O error, dev hdc, sector 5978828
[14059.808000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14059.808000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14059.808000] ide: failed opcode was: unknown
[14059.808000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14059.808000] end_request: I/O error, dev hdc, sector 5978828
[14059.808000] printk: 9 messages suppressed.
[14059.808000] Buffer I/O error on device hdc, logical block 1494707
[14060.748000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14060.748000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14060.748000] ide: failed opcode was: unknown
[14060.748000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14060.748000] end_request: I/O error, dev hdc, sector 5978828
[14061.688000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14061.688000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14061.688000] ide: failed opcode was: unknown
[14061.688000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14061.688000] end_request: I/O error, dev hdc, sector 5978828
[14063.168000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14063.168000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14063.168000] ide: failed opcode was: unknown
[14063.168000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14063.168000] end_request: I/O error, dev hdc, sector 7526772
[14064.196000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14064.196000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14064.196000] ide: failed opcode was: unknown
[14064.196000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14064.196000] end_request: I/O error, dev hdc, sector 7526772
[14120.056000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14120.056000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14120.056000] ide: failed opcode was: unknown
[14120.056000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14120.056000] end_request: I/O error, dev hdc, sector 7541324
[14120.056000] printk: 9 messages suppressed.
[14120.056000] Buffer I/O error on device hdc, logical block 1885331
[14122.632000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14122.632000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14122.632000] ide: failed opcode was: unknown
[14122.632000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14122.632000] end_request: I/O error, dev hdc, sector 7541328
[14122.632000] Buffer I/O error on device hdc, logical block 1885332
[14125.180000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14125.180000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14125.180000] ide: failed opcode was: unknown
[14125.180000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14125.180000] end_request: I/O error, dev hdc, sector 7541324
[14125.180000] Buffer I/O error on device hdc, logical block 1885331
[14125.180000] Buffer I/O error on device hdc, logical block 1885332
[14127.424000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14127.424000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14127.424000] ide: failed opcode was: unknown
[14127.424000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14127.424000] end_request: I/O error, dev hdc, sector 5978828
[14127.424000] Buffer I/O error on device hdc, logical block 1494707
[14127.424000] Buffer I/O error on device hdc, logical block 1494708
[14128.956000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14128.956000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14128.956000] ide: failed opcode was: unknown
[14128.956000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14128.956000] end_request: I/O error, dev hdc, sector 5978828
[14128.956000] Buffer I/O error on device hdc, logical block 1494707
[14128.956000] Buffer I/O error on device hdc, logical block 1494708
[14130.484000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14130.484000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14130.484000] ide: failed opcode was: unknown
[14130.488000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14130.488000] end_request: I/O error, dev hdc, sector 5978828
[14130.488000] Buffer I/O error on device hdc, logical block 1494707
[14130.488000] Buffer I/O error on device hdc, logical block 1494708
[14132.016000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14132.016000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14132.016000] ide: failed opcode was: unknown
[14132.016000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14132.016000] end_request: I/O error, dev hdc, sector 5978828
[14132.016000] Buffer I/O error on device hdc, logical block 1494707
[14132.016000] Buffer I/O error on device hdc, logical block 1494708
[14133.636000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14133.636000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14133.636000] ide: failed opcode was: unknown
[14133.636000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14133.636000] end_request: I/O error, dev hdc, sector 5978828
[14135.124000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14135.124000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14135.124000] ide: failed opcode was: unknown
[14135.124000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14135.124000] end_request: I/O error, dev hdc, sector 5978828
[14135.124000] printk: 2 messages suppressed.
[14135.124000] Buffer I/O error on device hdc, logical block 1494707
[14136.568000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14136.568000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14136.568000] ide: failed opcode was: unknown
[14136.568000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14136.568000] end_request: I/O error, dev hdc, sector 5978828
[14138.244000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14138.244000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14138.244000] ide: failed opcode was: unknown
[14138.244000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14138.244000] end_request: I/O error, dev hdc, sector 5978828
[14139.772000] hdc: media error (blank): status=0x51 { DriveReady SeekComplete Error }
[14139.772000] hdc: media error (blank): error=0x80 { LastFailedSense=0x08 }
[14139.772000] ide: failed opcode was: unknown
[14139.772000] hdc: error code: 0x70  sense_key: 0x08  asc: 0x00  ascq: 0x00
[14139.772000] end_request: I/O error, dev hdc, sector 5978828
```

---

### Post by Woody1987 on 2008-03-16
i have exactly the same problem, after around 5-10min of use it just hangs and says stopped in the bottom right hand corner, although every other internet app i have works flawlessly despite this.

---

### Post by danwood76 on 2008-03-16
when firefox stops working go into the terminal and type:
```

ping www.google.com

```

it should give you output like:
```

PING www.l.google.com (66.249.91.99) 56(84) bytes of data.
64 bytes from ik-in-f99.google.com (66.249.91.99): icmp_seq=1 ttl=242 time=102 ms
64 bytes from ik-in-f99.google.com (66.249.91.99): icmp_seq=2 ttl=242 time=126 ms
64 bytes from ik-in-f99.google.com (66.249.91.99): icmp_seq=3 ttl=242 time=96.2 ms
64 bytes from ik-in-f99.google.com (66.249.91.99): icmp_seq=4 ttl=242 time=52.6 ms

```
if it fails to give that output then I would say the DNS has crashed.

how are you connected to the internet?

---

### Post by Woody1987 on 2008-03-16
just hung again and tried pinging google and other websites and it works fine. I have this same problem with firefox64bit, firefox32bit, swiftweasel32bit and firefox 3. No other app suffers. Obviously theres a problem with firefox somewhere or how my system reacts to it. I tried removing all my addons just in case and problem presists. Any suggestions?

---

### Post by il-mArCi0 on 2008-03-17
silvio@aspire:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

---

### Post by danwood76 on 2008-03-17
@il-mArCi0
It looks like you have a DNS issue.

How are you connected to the internet?

---

### Post by il-mArCi0 on 2008-03-17
> **danwood76 said:**
> @il-mArCi0
It looks like you have a DNS issue.

How are you connected to the internet?

with an usb wireless key and wicd with no static IP address

---

### Post by danwood76 on 2008-03-17
what model USB key is it and how have you installed the drivers?

---

### Post by il-mArCi0 on 2008-03-17
> **danwood76 said:**
> what model USB key is it and how have you installed the drivers?

the model is  ZyDAS 802.11b/g USB2 WiFi and is auto recognized by ubuntu

---

