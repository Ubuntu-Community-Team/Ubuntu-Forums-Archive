---
title: "freeze and intensive hdd use"
date: 2013-11-16
forum: General Help
---

### Post by AlexToind on 2013-11-16
It's about 1 month or so that Ubuntu freezes very often.
I use a 64bit version with 4GB RAM and if memory load exceeds 3GB the probability of freezing tends to 1.


I've noticed that if I don't touch anything, after 2-3 (and sometimes more) minutes the system come back alive, a bit sleepy, but by closing some processes I can solve the issue. You can understand that this is boring.


When the system freeze, the hdd led's status is always continously on and usually i can't even blink the capslock led.


I'm not very pratical, so I post you the syslog where are there many "errors": [ATTACH]247867[/ATTACH]


I think the problem should be here, but I don't know if this is the cause or a consequence:
```
...
Nov 15 16:30:09 Thor kernel: [11779.177439] Write(10): 2a 00 39 d1 c7 80 00 04 00 00
Nov 15 16:30:09 Thor kernel: [11779.177443] end_request: I/O error, dev sda, sector 970049408
Nov 15 16:30:09 Thor kernel: [11779.177446] Write-error on swap-device (252:1:1533824)
Nov 15 16:30:09 Thor kernel: [11779.177449] Write-error on swap-device (252:1:1533832)
Nov 15 16:30:09 Thor kernel: [11779.177450] Write-error on swap-device (252:1:1533840)
Nov 15 16:30:09 Thor kernel: [11779.177452] Write-error on swap-device (252:1:1533848)
Nov 15 16:30:09 Thor kernel: [11779.177453] Write-error on swap-device (252:1:1533856)
Nov 15 16:30:09 Thor kernel: [11779.177454] Write-error on swap-device (252:1:1533864)
Nov 15 16:30:09 Thor kernel: [11779.177456] Write-error on swap-device (252:1:1533872)
Nov 15 16:30:09 Thor kernel: [11779.177458] Write-error on swap-device (252:1:1533880)
Nov 15 16:30:09 Thor kernel: [11779.177459] Write-error on swap-device (252:1:1533888)
Nov 15 16:30:09 Thor kernel: [11779.177460] Write-error on swap-device (252:1:1533896)
Nov 15 16:30:09 Thor kernel: [11779.177461] Write-error on swap-device (252:1:1533904)
Nov 15 16:30:09 Thor kernel: [11779.177463] Write-error on swap-device (252:1:1533912)
Nov 15 16:30:09 Thor kernel: [11779.177464] Write-error on swap-device (252:1:1533920)
Nov 15 16:30:09 Thor kernel: [11779.177466] Write-error on swap-device (252:1:1533928)
Nov 15 16:30:09 Thor kernel: [11779.177467] Write-error on swap-device (252:1:1533936)
Nov 15 16:30:09 Thor kernel: [11779.177468] Write-error on swap-device (252:1:1533944)
Nov 15 16:30:09 Thor kernel: [11779.177470] Write-error on swap-device (252:1:1533952)
Nov 15 16:30:09 Thor kernel: [11779.177471] Write-error on swap-device (252:1:1533960)
Nov 15 16:30:09 Thor kernel: [11779.177472] Write-error on swap-device (252:1:1533968)
Nov 15 16:30:09 Thor kernel: [11779.177473] Write-error on swap-device (252:1:1533976)
Nov 15 16:30:09 Thor kernel: [11779.177474] Write-error on swap-device (252:1:1533984)
Nov 15 16:30:09 Thor kernel: [11779.177475] Write-error on swap-device (252:1:1533992)
Nov 15 16:30:09 Thor kernel: [11779.177476] Write-error on swap-device (252:1:1534000)
Nov 15 16:30:09 Thor kernel: [11779.177478] Write-error on swap-device (252:1:1534008)
Nov 15 16:30:09 Thor kernel: [11779.177479] Write-error on swap-device (252:1:1534016)
Nov 15 16:30:09 Thor kernel: [11779.177480] Write-error on swap-device (252:1:1534024)
Nov 15 16:30:09 Thor kernel: [11779.177481] Write-error on swap-device (252:1:1534032)
Nov 15 16:30:09 Thor kernel: [11779.177482] Write-error on swap-device (252:1:1534040)
Nov 15 16:30:09 Thor kernel: [11779.177483] Write-error on swap-device (252:1:1534048)
Nov 15 16:30:09 Thor kernel: [11779.177484] Write-error on swap-device (252:1:1534056)
Nov 15 16:30:09 Thor kernel: [11779.177486] Write-error on swap-device (252:1:1534064)
Nov 15 16:30:09 Thor kernel: [11779.177487] Write-error on swap-device (252:1:1534072)
Nov 15 16:30:09 Thor kernel: [11779.177488] Write-error on swap-device (252:1:1534080)
Nov 15 16:30:09 Thor kernel: [11779.177489] Write-error on swap-device (252:1:1534088)
Nov 15 16:30:09 Thor kernel: [11779.177490] Write-error on swap-device (252:1:1534096)
Nov 15 16:30:09 Thor kernel: [11779.177492] Write-error on swap-device (252:1:1534104)
Nov 15 16:30:09 Thor kernel: [11779.177493] Write-error on swap-device (252:1:1534112)
Nov 15 16:30:09 Thor kernel: [11779.177494] Write-error on swap-device (252:1:1534120)
Nov 15 16:30:09 Thor kernel: [11779.177495] Write-error on swap-device (252:1:1534128)
Nov 15 16:30:09 Thor kernel: [11779.177496] Write-error on swap-device (252:1:1534136)
Nov 15 16:30:09 Thor kernel: [11779.177497] Write-error on swap-device (252:1:1534144)
Nov 15 16:30:09 Thor kernel: [11779.177499] Write-error on swap-device (252:1:1534152)
Nov 15 16:30:09 Thor kernel: [11779.177500] Write-error on swap-device (252:1:1534160)
Nov 15 16:30:09 Thor kernel: [11779.177501] Write-error on swap-device (252:1:1534168)
Nov 15 16:30:09 Thor kernel: [11779.177502] Write-error on swap-device (252:1:1534176)
Nov 15 16:30:09 Thor kernel: [11779.177503] Write-error on swap-device (252:1:1534184)
Nov 15 16:30:09 Thor kernel: [11779.177505] Write-error on swap-device (252:1:1534192)
Nov 15 16:30:09 Thor kernel: [11779.177506] Write-error on swap-device (252:1:1534200)
Nov 15 16:30:09 Thor kernel: [11779.177507] Write-error on swap-device (252:1:1534208)
Nov 15 16:30:09 Thor kernel: [11779.177508] Write-error on swap-device (252:1:1534216)
Nov 15 16:30:09 Thor kernel: [11779.177509] Write-error on swap-device (252:1:1534224)
Nov 15 16:30:09 Thor kernel: [11779.177510] Write-error on swap-device (252:1:1534232)
Nov 15 16:30:09 Thor kernel: [11779.177511] Write-error on swap-device (252:1:1534240)
Nov 15 16:30:09 Thor kernel: [11779.177512] Write-error on swap-device (252:1:1534248)
Nov 15 16:30:09 Thor kernel: [11779.177514] Write-error on swap-device (252:1:1534256)
Nov 15 16:30:09 Thor kernel: [11779.177515] Write-error on swap-device (252:1:1534264)
Nov 15 16:30:09 Thor kernel: [11779.177516] Write-error on swap-device (252:1:1534272)
Nov 15 16:30:09 Thor kernel: [11779.177517] Write-error on swap-device (252:1:1534280)
Nov 15 16:30:09 Thor kernel: [11779.177518] Write-error on swap-device (252:1:1534288)
Nov 15 16:30:09 Thor kernel: [11779.177519] Write-error on swap-device (252:1:1534296)
Nov 15 16:30:09 Thor kernel: [11779.177521] Write-error on swap-device (252:1:1534304)
Nov 15 16:30:09 Thor kernel: [11779.177522] Write-error on swap-device (252:1:1534312)
Nov 15 16:30:09 Thor kernel: [11779.177523] Write-error on swap-device (252:1:1534320)
Nov 15 16:30:09 Thor kernel: [11779.177525] Write-error on swap-device (252:1:1534328)
Nov 15 16:30:09 Thor kernel: [11779.177526] Write-error on swap-device (252:1:1534336)
Nov 15 16:30:09 Thor kernel: [11779.177527] Write-error on swap-device (252:1:1534344)
Nov 15 16:30:09 Thor kernel: [11779.177528] Write-error on swap-device (252:1:1534352)
Nov 15 16:30:09 Thor kernel: [11779.177529] Write-error on swap-device (252:1:1534360)
Nov 15 16:30:09 Thor kernel: [11779.177530] Write-error on swap-device (252:1:1534368)
Nov 15 16:30:09 Thor kernel: [11779.177531] Write-error on swap-device (252:1:1534376)
Nov 15 16:30:09 Thor kernel: [11779.177532] Write-error on swap-device (252:1:1534384)
Nov 15 16:30:09 Thor kernel: [11779.177534] Write-error on swap-device (252:1:1534392)
Nov 15 16:30:09 Thor kernel: [11779.177535] Write-error on swap-device (252:1:1534400)
Nov 15 16:30:09 Thor kernel: [11779.177536] Write-error on swap-device (252:1:1534408)
Nov 15 16:30:09 Thor kernel: [11779.177537] Write-error on swap-device (252:1:1534416)
Nov 15 16:30:09 Thor kernel: [11779.177538] Write-error on swap-device (252:1:1534424)
Nov 15 16:30:09 Thor kernel: [11779.177539] Write-error on swap-device (252:1:1534432)
Nov 15 16:30:09 Thor kernel: [11779.177544] Write-error on swap-device (252:1:1534440)
Nov 15 16:30:09 Thor kernel: [11779.177545] Write-error on swap-device (252:1:1534448)
Nov 15 16:30:09 Thor kernel: [11779.177546] Write-error on swap-device (252:1:1534456)
Nov 15 16:30:09 Thor kernel: [11779.177547] Write-error on swap-device (252:1:1534464)
Nov 15 16:30:09 Thor kernel: [11779.177548] Write-error on swap-device (252:1:1534472)
Nov 15 16:30:09 Thor kernel: [11779.177556] Write-error on swap-device (252:1:1534480)
Nov 15 16:30:09 Thor kernel: [11779.177558] Write-error on swap-device (252:1:1534488)
Nov 15 16:30:09 Thor kernel: [11779.177559] Write-error on swap-device (252:1:1534496)
Nov 15 16:30:09 Thor kernel: [11779.177561] Write-error on swap-device (252:1:1534504)
Nov 15 16:30:09 Thor kernel: [11779.177563] Write-error on swap-device (252:1:1534512)
Nov 15 16:30:09 Thor kernel: [11779.177565] Write-error on swap-device (252:1:1534520)
Nov 15 16:30:09 Thor kernel: [11779.177567] Write-error on swap-device (252:1:1534528)
Nov 15 16:30:09 Thor kernel: [11779.177569] Write-error on swap-device (252:1:1534536)
Nov 15 16:30:09 Thor kernel: [11779.177571] Write-error on swap-device (252:1:1534544)
Nov 15 16:30:09 Thor kernel: [11779.177572] Write-error on swap-device (252:1:1534552)
Nov 15 16:30:09 Thor kernel: [11779.177573] Write-error on swap-device (252:1:1534560)
Nov 15 16:30:09 Thor kernel: [11779.177575] Write-error on swap-device (252:1:1534568)
Nov 15 16:30:09 Thor kernel: [11779.177576] Write-error on swap-device (252:1:1534576)
Nov 15 16:30:09 Thor kernel: [11779.177577] Write-error on swap-device (252:1:1534584)
Nov 15 16:30:09 Thor kernel: [11779.177578] Write-error on swap-device (252:1:1534592)
Nov 15 16:30:09 Thor kernel: [11779.177580] Write-error on swap-device (252:1:1534600)
Nov 15 16:30:09 Thor kernel: [11779.177581] Write-error on swap-device (252:1:1534608)
Nov 15 16:30:09 Thor kernel: [11779.177582] Write-error on swap-device (252:1:1534616)
Nov 15 16:30:09 Thor kernel: [11779.177583] Write-error on swap-device (252:1:1534624)
Nov 15 16:30:09 Thor kernel: [11779.177584] Write-error on swap-device (252:1:1534632)
Nov 15 16:30:09 Thor kernel: [11779.177585] Write-error on swap-device (252:1:1534640)
Nov 15 16:30:09 Thor kernel: [11779.177586] Write-error on swap-device (252:1:1534648)
Nov 15 16:30:09 Thor kernel: [11779.177588] Write-error on swap-device (252:1:1534656)
Nov 15 16:30:09 Thor kernel: [11779.177589] Write-error on swap-device (252:1:1534664)
Nov 15 16:30:09 Thor kernel: [11779.177590] Write-error on swap-device (252:1:1534672)
Nov 15 16:30:09 Thor kernel: [11779.177591] Write-error on swap-device (252:1:1534680)
Nov 15 16:30:09 Thor kernel: [11779.177592] Write-error on swap-device (252:1:1534688)
Nov 15 16:30:09 Thor kernel: [11779.177593] Write-error on swap-device (252:1:1534696)
Nov 15 16:30:09 Thor kernel: [11779.177594] Write-error on swap-device (252:1:1534704)
Nov 15 16:30:09 Thor kernel: [11779.177595] Write-error on swap-device (252:1:1534712)
Nov 15 16:30:09 Thor kernel: [11779.177596] Write-error on swap-device (252:1:1534720)
Nov 15 16:30:09 Thor kernel: [11779.177597] Write-error on swap-device (252:1:1534728)
Nov 15 16:30:09 Thor kernel: [11779.177599] Write-error on swap-device (252:1:1534736)
Nov 15 16:30:09 Thor kernel: [11779.177600] Write-error on swap-device (252:1:1534744)
Nov 15 16:30:09 Thor kernel: [11779.177601] Write-error on swap-device (252:1:1534752)
Nov 15 16:30:10 Thor kernel: [11779.177602] Write-error on swap-device (252:1:1534760)
Nov 15 16:30:10 Thor kernel: [11779.177603] Write-error on swap-device (252:1:1534768)
Nov 15 16:30:10 Thor kernel: [11779.177604] Write-error on swap-device (252:1:1534776)
Nov 15 16:30:10 Thor kernel: [11779.177605] Write-error on swap-device (252:1:1534784)
Nov 15 16:30:10 Thor kernel: [11779.177607] Write-error on swap-device (252:1:1534792)
Nov 15 16:30:10 Thor kernel: [11779.177608] Write-error on swap-device (252:1:1534800)
Nov 15 16:30:10 Thor kernel: [11779.177609] Write-error on swap-device (252:1:1534808)
Nov 15 16:30:10 Thor kernel: [11779.177610] Write-error on swap-device (252:1:1534816)
Nov 15 16:30:10 Thor kernel: [11779.177611] Write-error on swap-device (252:1:1534824)
Nov 15 16:30:10 Thor kernel: [11779.177612] Write-error on swap-device (252:1:1534832)
Nov 15 16:30:10 Thor kernel: [11779.177613] Write-error on swap-device (252:1:1534840)
Nov 15 16:30:10 Thor kernel: [11779.177619] ata1: EH complete
Nov 15 16:30:10 Thor kernel: [11782.135636] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 15 16:30:10 Thor kernel: [11782.135639] ata1.00: irq_stat 0x40000001
Nov 15 16:30:10 Thor kernel: [11782.135641] ata1.00: failed command: WRITE DMA EXT
Nov 15 16:30:10 Thor kernel: [11782.135644] ata1.00: cmd 35/00:00:80:cf:d1/00:04:39:00:00/e0 tag 0 dma 524288 out
Nov 15 16:30:10 Thor kernel: [11782.135644]          res 51/04:29:56:d1:d1/00:02:39:00:00/e9 Emask 0x1 (device error)
Nov 15 16:30:10 Thor kernel: [11782.135645] ata1.00: status: { DRDY ERR }
Nov 15 16:30:10 Thor kernel: [11782.135646] ata1.00: error: { ABRT }
Nov 15 16:30:10 Thor kernel: [11782.197778] ata1.00: configured for UDMA/100
...
```

[EDIT]
**System:** 64-bit 13.10 - Linux 3.11.0-13-generic - 4GB RAM - i7-2640M - TOSHIBA MK5061GSYN 500GB
[/EDIT]

---

### Post by lordbalmung on 2013-11-16
I second that!

**Issue:** Same issue
**System:** 64-bit 13.10 - 16 GB RAM - i7-4770

---

### Post by AlexToind on 2013-11-17
Humm, could be a software problem so?

I'll make a low level hdd check and will post if there are many errors or not.

---

