---
title: "Movie-image burning problem."
date: 2007-11-09
forum: General Help
---

### Post by stianmu on 2007-11-09
Downloaded a dvd movie in img format, lets call it a *free*] home movie, and tried to burn it out using image burn (renamed it to .iso). I put the burned disk in my dvdplayer, playback started and it seemed ok, but after chapter 6 it wouldn't play anymore. I took the disk out and it looked like it had only burned some info on it, the whole disk wasn't used. I burned it again, and same problem over again. 

I then renamed the file back to .img, and aptidue intalled udftools and then ran

```
stian@stian-laptop:/$ growisofs -Z /dev/dvd=/home/stian/Shared/path-of-my-home-movie/dl-ag.img 
Executing 'builtin_dd if=/home/stian/Shared/path-of-my-home-movie/dl-ag.img of=/dev/dvd obs=32k seek=0'
/dev/dvd: "Current Write Speed" is 8.2x1352KBps.
          0/4449134592 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4449134592 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4449134592 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4449134592 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4449134592 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4449134592 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
    7667712/4449134592 ( 0.2%) @1.7x, remaining 251:00 RBU 100.0% UBU   2.9%
   23429120/4449134592 ( 0.5%) @3.4x, remaining 91:18 RBU 100.0% UBU 100.0%
   39354368/4449134592 ( 0.9%) @3.4x, remaining 61:37 RBU  97.7% UBU 100.0%
   55377920/4449134592 ( 1.2%) @3.5x, remaining 47:36 RBU 100.0% UBU 100.0%
   71532544/4449134592 ( 1.6%) @3.5x, remaining 39:46 RBU 100.0% UBU 100.0%
   87851008/4449134592 ( 2.0%) @3.5x, remaining 35:34 RBU 100.0% UBU 100.0%
  104235008/4449134592 ( 2.3%) @3.5x, remaining 31:57 RBU 100.0% UBU 100.0%
  120815616/4449134592 ( 2.7%) @3.6x, remaining 29:15 RBU 100.0% UBU  85.3%
  137494528/4449134592 ( 3.1%) @3.6x, remaining 27:42 RBU 100.0% UBU 100.0%
  154304512/4449134592 ( 3.5%) @3.6x, remaining 25:58 RBU 100.0% UBU 100.0%
  171212800/4449134592 ( 3.8%) @3.7x, remaining 24:34 RBU 100.0% UBU  94.1%
  188252160/4449134592 ( 4.2%) @3.7x, remaining 23:45 RBU  99.2% UBU 100.0%
  205422592/4449134592 ( 4.6%) @3.7x, remaining 22:43 RBU 100.0% UBU 100.0%
  222724096/4449134592 ( 5.0%) @3.7x, remaining 21:49 RBU 100.0% UBU 100.0%
  240156672/4449134592 ( 5.4%) @3.8x, remaining 21:19 RBU  92.2% UBU 100.0%
  257720320/4449134592 ( 5.8%) @3.8x, remaining 20:36 RBU 100.0% UBU 100.0%
  275382272/4449134592 ( 6.2%) @3.8x, remaining 19:57 RBU 100.0% UBU  94.1%
  293208064/4449134592 ( 6.6%) @3.9x, remaining 19:36 RBU 100.0% UBU  97.1%
  311164928/4449134592 ( 7.0%) @3.9x, remaining 19:03 RBU 100.0% UBU 100.0%
  329220096/4449134592 ( 7.4%) @3.9x, remaining 18:33 RBU  98.4% UBU 100.0%
  347373568/4449134592 ( 7.8%) @3.9x, remaining 18:18 RBU  98.4% UBU  97.1%
  365658112/4449134592 ( 8.2%) @3.9x, remaining 17:52 RBU 100.0% UBU 100.0%
  378109952/4449134592 ( 8.5%) @2.7x, remaining 17:45 RBU  91.4% UBU  94.1%
  384139264/4449134592 ( 8.6%) @1.3x, remaining 18:09 RBU   0.0% UBU  38.2%
  397017088/4449134592 ( 8.9%) @2.8x, remaining 18:01 RBU 100.0% UBU  67.6%
  415662080/4449134592 ( 9.3%) @4.0x, remaining 17:37 RBU 100.0% UBU 100.0%
  434438144/4449134592 ( 9.8%) @4.1x, remaining 17:24 RBU 100.0% UBU 100.0%
  453345280/4449134592 (10.2%) @4.1x, remaining 17:02 RBU 100.0% UBU 100.0%
  472350720/4449134592 (10.6%) @4.1x, remaining 16:41 RBU 100.0% UBU 100.0%
  491520000/4449134592 (11.0%) @4.2x, remaining 16:30 RBU  12.5% UBU  91.2%
  510787584/4449134592 (11.5%) @4.2x, remaining 16:11 RBU 100.0% UBU  97.1%
  530186240/4449134592 (11.9%) @4.2x, remaining 15:53 RBU 100.0% UBU  97.1%
  549715968/4449134592 (12.4%) @4.2x, remaining 15:43 RBU 100.0% UBU 100.0%
  569376768/4449134592 (12.8%) @4.3x, remaining 15:26 RBU 100.0% UBU 100.0%
  586579968/4449134592 (13.2%) @3.7x, remaining 15:15 RBU   0.0% UBU 100.0%
  586579968/4449134592 (13.2%) @0.0x, remaining 15:41 RBU   0.0% UBU   8.8%
  586579968/4449134592 (13.2%) @0.0x, remaining 16:01 RBU   0.0% UBU   8.8%
  586579968/4449134592 (13.2%) @0.0x, remaining 16:21 RBU   0.0% UBU   8.8%
  586579968/4449134592 (13.2%) @0.0x, remaining 16:47 RBU   0.0% UBU   8.8%
  586579968/4449134592 (13.2%) @0.0x, remaining 17:07 RBU   0.0% UBU   8.8%
  586579968/4449134592 (13.2%) @0.0x, remaining 17:26 RBU   0.0% UBU   8.8%
  586579968/4449134592 (13.2%) @0.0x, remaining 17:53 RBU   0.0% UBU   8.8%
builtin_dd: 286416*2KB out @ average 2.6x1352KBps
/dev/dvd: flushing cache
/dev/dvd: updating RMA
/dev/dvd: closing session
stian@stian-laptop:/$ 
```

Same problem yet again, the whole movie is not on the disk. I opened the .img file in vlc, and it worked great, the image is not broken, the whole movie could be watched in vlc. 

Could someone please help me, I am kind of new to linux.

---

### Post by geirha on 2007-11-09
Sounds to me like your dvd-recorder is faulty. I would have a -dvd-compat on that growisofs command, but it should still have burned the whole disk. If your dvd-recorder, or possibly driver, is faulty, the kernel-log should show some errors about that. If you don't mind a burning a new coaster, I would open a seperate terminal and run ```
tail -F /var/log/kern.log
```, then burn and see what messages the kernel gives.

---

### Post by stianmu on 2007-11-09
burning is done:

log:
```
stian@stian-laptop:~$ tail -F /var/log/kern.log
Nov  9 15:01:39 stian-laptop kernel: [ 8011.932000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  9 15:01:39 stian-laptop kernel: [ 8011.948000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  9 15:01:39 stian-laptop kernel: [ 8011.948000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Nov  9 15:01:39 stian-laptop kernel: [ 8011.948000] sd 0:0:0:0: [sda] Write Protect is off
Nov  9 15:01:39 stian-laptop kernel: [ 8011.948000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  9 15:01:39 stian-laptop kernel: [ 8011.948000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  9 15:17:36 stian-laptop kernel: [ 8968.696000] UDF-fs: Partition marked readonly; forcing readonly mount
Nov  9 15:17:37 stian-laptop kernel: [ 8968.756000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'AMERICAN_GANGSTER', timestamp 2007/10/23 22:41 (103c)
Nov  9 15:39:01 stian-laptop kernel: [10253.520000] cdrom: This disc doesn't have any tracks I recognize!
Nov  9 18:05:30 stian-laptop kernel: [19043.088000] cdrom: This disc doesn't have any tracks I recognize!
Nov  9 18:08:57 stian-laptop kernel: [19250.252000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov  9 18:08:57 stian-laptop kernel: [19250.252000] ata1.00: (irq_stat 0x40000001)
Nov  9 18:08:57 stian-laptop kernel: [19250.252000] ata1.00: cmd c8/00:40:df:e4:22/00:00:00:00:00/e4 tag 0 cdb 0x0 data 32768 in
Nov  9 18:08:57 stian-laptop kernel: [19250.252000]          res 51/40:06:19:e5:22/00:00:04:00:00/e4 Emask 0x9 (media error)
Nov  9 18:08:57 stian-laptop kernel: [19250.256000] ata1.00: configured for UDMA/100
Nov  9 18:08:57 stian-laptop kernel: [19250.256000] ata1: EH complete
Nov  9 18:09:02 stian-laptop kernel: [19255.068000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov  9 18:09:02 stian-laptop kernel: [19255.068000] ata1.00: (irq_stat 0x40000001)
Nov  9 18:09:02 stian-laptop kernel: [19255.068000] ata1.00: cmd c8/00:40:df:e4:22/00:00:00:00:00/e4 tag 0 cdb 0x0 data 32768 in
Nov  9 18:09:02 stian-laptop kernel: [19255.068000]          res 51/40:06:19:e5:22/00:00:04:00:00/e4 Emask 0x9 (media error)
Nov  9 18:09:02 stian-laptop kernel: [19255.072000] ata1.00: configured for UDMA/100
Nov  9 18:09:02 stian-laptop kernel: [19255.072000] ata1: EH complete
Nov  9 18:09:07 stian-laptop kernel: [19259.880000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov  9 18:09:07 stian-laptop kernel: [19259.880000] ata1.00: (irq_stat 0x40000001)
Nov  9 18:09:07 stian-laptop kernel: [19259.880000] ata1.00: cmd c8/00:40:df:e4:22/00:00:00:00:00/e4 tag 0 cdb 0x0 data 32768 in
Nov  9 18:09:07 stian-laptop kernel: [19259.880000]          res 51/40:06:19:e5:22/00:00:04:00:00/e4 Emask 0x9 (media error)
Nov  9 18:09:20 stian-laptop kernel: [19259.884000] ata1.00: configured for UDMA/100
Nov  9 18:09:20 stian-laptop kernel: [19259.884000] ata1: EH complete
Nov  9 18:09:20 stian-laptop kernel: [19264.004000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov  9 18:09:20 stian-laptop kernel: [19264.004000] ata1.00: (irq_stat 0x40000001)
Nov  9 18:09:20 stian-laptop kernel: [19264.004000] ata1.00: cmd c8/00:40:df:e4:22/00:00:00:00:00/e4 tag 0 cdb 0x0 data 32768 in
Nov  9 18:09:20 stian-laptop kernel: [19264.004000]          res 51/40:06:19:e5:22/00:00:04:00:00/e4 Emask 0x9 (media error)
Nov  9 18:09:20 stian-laptop kernel: [19264.008000] ata1.00: configured for UDMA/100
Nov  9 18:09:20 stian-laptop kernel: [19264.008000] ata1: EH complete
Nov  9 18:09:20 stian-laptop kernel: [19268.872000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov  9 18:09:20 stian-laptop kernel: [19268.872000] ata1.00: (irq_stat 0x40000001)
Nov  9 18:09:20 stian-laptop kernel: [19268.872000] ata1.00: cmd c8/00:40:df:e4:22/00:00:00:00:00/e4 tag 0 cdb 0x0 data 32768 in
Nov  9 18:09:20 stian-laptop kernel: [19268.872000]          res 51/40:06:19:e5:22/00:00:04:00:00/e4 Emask 0x9 (media error)
Nov  9 18:09:20 stian-laptop kernel: [19268.876000] ata1.00: configured for UDMA/100
Nov  9 18:09:20 stian-laptop kernel: [19268.876000] ata1: EH complete
Nov  9 18:09:20 stian-laptop kernel: [19273.024000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov  9 18:09:20 stian-laptop kernel: [19273.024000] ata1.00: (irq_stat 0x40000001)
Nov  9 18:09:20 stian-laptop kernel: [19273.024000] ata1.00: cmd c8/00:40:df:e4:22/00:00:00:00:00/e4 tag 0 cdb 0x0 data 32768 in
Nov  9 18:09:20 stian-laptop kernel: [19273.024000]          res 51/40:06:19:e5:22/00:00:04:00:00/e4 Emask 0x9 (media error)
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] ata1.00: configured for UDMA/100
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] Descriptor sense data with sense descriptors (in hex):
Nov  9 18:09:20 stian-laptop kernel: [19273.028000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Nov  9 18:09:20 stian-laptop kernel: [19273.028000]         04 22 e5 19 
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] end_request: I/O error, dev sda, sector 69395737
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] ata1: EH complete
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] sd 0:0:0:0: [sda] Write Protect is off
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  9 18:09:20 stian-laptop kernel: [19273.084000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  9 18:09:20 stian-laptop kernel: [19273.116000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Nov  9 18:09:20 stian-laptop kernel: [19273.116000] sd 0:0:0:0: [sda] Write Protect is off
Nov  9 18:09:20 stian-laptop kernel: [19273.116000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  9 18:09:20 stian-laptop kernel: [19273.116000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Burn prosess:
```

stian@stian-laptop:~$ growisofs -Z /dev/dvd=/home/stian/Shared/American.Gangster.DVD.SCREENER.DVDR-DREAMLiGHT/dl-ag.img 
Executing 'builtin_dd if=/home/stian/Shared/American.Gangster.DVD.SCREENER.DVDR-DREAMLiGHT/dl-ag.img of=/dev/dvd obs=32k seek=0'
/dev/dvd: "Current Write Speed" is 8.2x1352KBps.
          0/4449134592 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4449134592 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4449134592 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4449134592 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4449134592 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/4449134592 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
    7274496/4449134592 ( 0.2%) @1.6x, remaining 264:35 RBU  99.8% UBU   2.9%
   22937600/4449134592 ( 0.5%) @3.4x, remaining 93:16 RBU 100.0% UBU 100.0%
   38764544/4449134592 ( 0.9%) @3.4x, remaining 60:40 RBU 100.0% UBU 100.0%
   54689792/4449134592 ( 1.2%) @3.4x, remaining 48:12 RBU 100.0% UBU 100.0%
   70746112/4449134592 ( 1.6%) @3.5x, remaining 40:13 RBU 100.0% UBU 100.0%
   86933504/4449134592 ( 2.0%) @3.5x, remaining 35:07 RBU 100.0% UBU 100.0%
  103219200/4449134592 ( 2.3%) @3.5x, remaining 32:16 RBU 100.0% UBU 100.0%
  119668736/4449134592 ( 2.7%) @3.6x, remaining 29:32 RBU 100.0% UBU 100.0%
  136216576/4449134592 ( 3.1%) @3.6x, remaining 27:26 RBU 100.0% UBU 100.0%
  152895488/4449134592 ( 3.4%) @3.6x, remaining 26:13 RBU  99.8% UBU 100.0%
  169705472/4449134592 ( 3.8%) @3.6x, remaining 24:47 RBU  99.8% UBU 100.0%
  186646528/4449134592 ( 4.2%) @3.7x, remaining 23:35 RBU  99.8% UBU 100.0%
  203685888/4449134592 ( 4.6%) @3.7x, remaining 22:55 RBU  99.8% UBU 100.0%
  220856320/4449134592 ( 5.0%) @3.7x, remaining 22:01 RBU 100.0% UBU 100.0%
  238157824/4449134592 ( 5.4%) @3.7x, remaining 21:13 RBU 100.0% UBU 100.0%
  255590400/4449134592 ( 5.7%) @3.8x, remaining 20:46 RBU  99.8% UBU 100.0%
  273154048/4449134592 ( 6.1%) @3.8x, remaining 20:07 RBU  99.8% UBU 100.0%
  290816000/4449134592 ( 6.5%) @3.8x, remaining 19:32 RBU 100.0% UBU 100.0%
  308609024/4449134592 ( 6.9%) @3.9x, remaining 19:13 RBU 100.0% UBU 100.0%
  326533120/4449134592 ( 7.3%) @3.9x, remaining 18:43 RBU 100.0% UBU 100.0%
  344588288/4449134592 ( 7.7%) @3.9x, remaining 18:15 RBU 100.0% UBU 100.0%
  362774528/4449134592 ( 8.2%) @3.9x, remaining 18:01 RBU 100.0% UBU 100.0%
  375095296/4449134592 ( 8.4%) @2.7x, remaining 17:55 RBU  99.8% UBU  97.1%
  393478144/4449134592 ( 8.8%) @4.0x, remaining 17:31 RBU  99.8% UBU  97.1%
  411959296/4449134592 ( 9.3%) @4.0x, remaining 17:18 RBU 100.0% UBU 100.0%
  430604288/4449134592 ( 9.7%) @4.0x, remaining 16:57 RBU 100.0% UBU 100.0%
  449347584/4449134592 (10.1%) @4.1x, remaining 16:36 RBU 100.0% UBU 100.0%
  468254720/4449134592 (10.5%) @4.1x, remaining 16:26 RBU 100.0% UBU 100.0%
  487227392/4449134592 (11.0%) @4.1x, remaining 16:07 RBU 100.0% UBU 100.0%
  506396672/4449134592 (11.4%) @4.1x, remaining 15:49 RBU  99.8% UBU 100.0%
  525631488/4449134592 (11.8%) @4.2x, remaining 15:40 RBU 100.0% UBU 100.0%
  545030144/4449134592 (12.3%) @4.2x, remaining 15:24 RBU  99.8% UBU 100.0%
  564527104/4449134592 (12.7%) @4.2x, remaining 15:08 RBU 100.0% UBU 100.0%
  584155136/4449134592 (13.1%) @4.3x, remaining 14:59 RBU  14.5% UBU 100.0%
  586579968/4449134592 (13.2%) @0.5x, remaining 15:15 RBU   0.0% UBU 100.0%
  586579968/4449134592 (13.2%) @0.0x, remaining 15:35 RBU   0.0% UBU   8.8%
  586579968/4449134592 (13.2%) @0.0x, remaining 16:01 RBU   0.0% UBU   8.8%
  586579968/4449134592 (13.2%) @0.0x, remaining 16:21 RBU   0.0% UBU   8.8%
  586579968/4449134592 (13.2%) @0.0x, remaining 16:40 RBU   0.0% UBU   8.8%
  586579968/4449134592 (13.2%) @0.0x, remaining 17:07 RBU   0.0% UBU   8.8%
  586579968/4449134592 (13.2%) @0.0x, remaining 17:26 RBU   0.0% UBU   8.8%
builtin_dd: 286416*2KB out @ average 2.6x1352KBps
/dev/dvd: flushing cache
/dev/dvd: updating RMA
/dev/dvd: closing session
stian@stian-laptop:~$ 
```

What does this mean(what do i do next)?


thanks for your help:)

---

### Post by geirha on 2007-11-09
> **stianmu said:**
> ```

Nov  9 18:09:20 stian-laptop kernel: [19273.028000] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] Descriptor sense data with sense descriptors (in hex):
Nov  9 18:09:20 stian-laptop kernel: [19273.028000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Nov  9 18:09:20 stian-laptop kernel: [19273.028000]         04 22 e5 19 
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Nov  9 18:09:20 stian-laptop kernel: [19273.028000] end_request: I/O error, dev sda, sector 69395737
```
Looks like you have a bad sector on /dev/sda. I would try booting the ubuntu cd and run fsck on the partition the image is on. Could be a kernel bug too, a quick google search suggests both, but haven't found any definite answers.

---

### Post by stianmu on 2007-11-10
Problem one: As my cd burner don't want to burn out the whole live cd, and I can't find the one I used the last time, I have no live cd to use. Maybe I can get my hands on another computer later today and then burn out a live cd from there.

Problem two: As I am a complete n00b in linux I do not understand how to run fsck, I tried google'ing it, but every topic i found, people already knew how to run it, and just needed help further.

I run a laptop, and only have one partion, Could you please tell me how i run fsck.

Thanks again

---

### Post by knutschr on 2007-11-10
You could try gmount-iso.
The program will mount your image to a virtual CD on your HD.

---

### Post by geirha on 2007-11-10
You shouldn't run fsck on a filesystem that is mounted read/write, that's why you need the livecd. When you get a livecd somehow, and boot it, you just run "sudo fsck /dev/sda1" in a terminal. Read the man-pages for fsck and fsck.ext3 to see how to make fsck do more stuff. ```
man fsck
man fsck.ext3
```

---

