---
title: "k3b and burning a DVD-R"
date: 2017-04-01
forum: General Help
---

### Post by anon_private on 2017-04-01
I tried to burn the kubuntu 16.04 LTS iso file to a DVD-R.

I simulated the burning process and things appeared to go well.

I then attempted to burn the iso file to the DVD-R, and it failed.

The DVD-R is now recognised as blank, and the overall message stated: ' error while reading sector 0'.

I give below the debug report

```
Burned media
-----------------------
DVD-R Sequential

Devices
-----------------------
HL-DT-ST  DVD+-RW GSA-H31N B109 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R,  DVD-RW, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-RW  Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual  Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16,  RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]

K3b::DataTrackReader
-----------------------
reading sectors 0 to 775959 with sector size 2048. Length: 775960 sectors, 1589166080 bytes.

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.13.3
QT Version:  4.8.6
Kernel:      4.4.0-71-generic

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: engaging DVD-R DAO upon user request...
/dev/sr0: reserving 775960 blocks
/dev/sr0: "Current Write Speed" is 16.4x1352KBps.
          0/1589166080 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
=== last message repeated 2 times. ===
    1310720/1589166080 ( 0.1%) @0.3x, remaining 262:28 RBU 100.0% UBU   7.0%
   30146560/1589166080 ( 1.9%) @6.2x, remaining 13:47 RBU 100.0% UBU  83.9%
   61636608/1589166080 ( 3.9%) @6.8x, remaining 8:15 RBU 100.0% UBU  83.9%
   93585408/1589166080 ( 5.9%) @6.9x, remaining 6:07 RBU 100.0% UBU  83.9%
  126091264/1589166080 ( 7.9%) @7.0x, remaining 5:01 RBU 100.0% UBU  83.9%
  159023104/1589166080 (10.0%) @7.1x, remaining 4:29 RBU 100.0% UBU  83.9%
  192479232/1589166080 (12.1%) @7.2x, remaining 3:59 RBU  99.9% UBU  83.9%
  226361344/1589166080 (14.2%) @7.3x, remaining 3:36 RBU 100.0% UBU  83.9%
  260833280/1589166080 (16.4%) @7.5x, remaining 3:23 RBU 100.0% UBU  83.9%
  295698432/1589166080 (18.6%) @7.6x, remaining 3:08 RBU 100.0% UBU  83.9%
  331087872/1589166080 (20.8%) @7.7x, remaining 2:54 RBU 100.0% UBU  83.9%
  367001600/1589166080 (23.1%) @7.8x, remaining 2:46 RBU 100.0% UBU  83.9%
  403308544/1589166080 (25.4%) @7.9x, remaining 2:35 RBU 100.0% UBU  83.9%
  440139776/1589166080 (27.7%) @8.0x, remaining 2:26 RBU 100.0% UBU  83.9%
  477495296/1589166080 (30.0%) @8.1x, remaining 2:19 RBU 100.0% UBU  83.9%
  504856576/1589166080 (31.8%) @5.9x, remaining 2:15 RBU 100.0% UBU  83.9%
  529924096/1589166080 (33.3%) @5.4x, remaining 2:11 RBU 100.0% UBU  86.2%
  568426496/1589166080 (35.8%) @8.3x, remaining 2:05 RBU 100.0% UBU  86.2%
  607420416/1589166080 (38.2%) @8.4x, remaining 1:57 RBU 100.0% UBU  86.2%
  646905856/1589166080 (40.7%) @8.5x, remaining 1:50 RBU 100.0% UBU  86.2%
  686850048/1589166080 (43.2%) @8.6x, remaining 1:45 RBU 100.0% UBU  86.2%
  727285760/1589166080 (45.8%) @8.8x, remaining 1:38 RBU 100.0% UBU  86.2%
  768212992/1589166080 (48.3%) @8.9x, remaining 1:31 RBU 100.0% UBU  86.2%
  809631744/1589166080 (50.9%) @9.0x, remaining 1:26 RBU 100.0% UBU  86.2%
  851542016/1589166080 (53.6%) @9.1x, remaining 1:20 RBU 100.0% UBU  86.2%
  893976576/1589166080 (56.3%) @9.2x, remaining 1:14 RBU 100.0% UBU  86.2%
  936869888/1589166080 (59.0%) @9.3x, remaining 1:09 RBU 100.0% UBU  86.2%
  980221952/1589166080 (61.7%) @9.4x, remaining 1:03 RBU 100.0% UBU  86.2%
 1024032768/1589166080 (64.4%) @9.5x, remaining 0:58 RBU 100.0% UBU  86.2%
 1068400640/1589166080 (67.2%) @9.6x, remaining 0:53 RBU 100.0% UBU  86.2%
 1113260032/1589166080 (70.1%) @9.7x, remaining 0:48 RBU 100.0% UBU  86.2%
 1158545408/1589166080 (72.9%) @9.8x, remaining 0:43 RBU 100.0% UBU  86.2%
 1204387840/1589166080 (75.8%) @9.9x, remaining 0:38 RBU 100.0% UBU  86.2%
 1250656256/1589166080 (78.7%) @10.0x, remaining 0:33 RBU 100.0% UBU  86.2%
 1297448960/1589166080 (81.6%) @10.1x, remaining 0:28 RBU 100.0% UBU  86.2%
 1344733184/1589166080 (84.6%) @10.2x, remaining 0:23 RBU 100.0% UBU  86.2%
 1392476160/1589166080 (87.6%) @10.3x, remaining 0:18 RBU 100.0% UBU  86.2%
 1440710656/1589166080 (90.7%) @10.4x, remaining 0:14 RBU 100.0% UBU  86.2%
 1477935104/1589166080 (93.0%) @8.1x, remaining 0:10 RBU 100.0% UBU  86.2%
 1477935104/1589166080 (93.0%) @0.0x, remaining 0:10 RBU 100.0% UBU 100.0%
=== last message repeated 2 times. ===
 1512210432/1589166080 (95.2%) @7.4x, remaining 0:07 RBU 100.0% UBU  86.2%

growisofs command:
-----------------------
/usr/bin/growisofs  -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray  -use-the-force-luke=tty -use-the-force-luke=4gms  -use-the-force-luke=tracksize:775960 -use-the-force-luke=dao:775960  -dvd-compat -speed=16 -use-the-force-luke=bufsize:32m

```
Can anyone advise

Thank you.

---

### Post by Keith_Helms on 2017-04-02
Did you use Tools->Burn Image to try and burn the ISO to DVD?

---

### Post by scdbackup on 2017-04-02
Hi,

the growisofs run does not show error indications. Especially not with
the first block of the DVD+R. So it is probable that your drive and the
medium silently did not like each other.

To diagnose further, you could inspect the nominal structure of the
DVD+R medium in question (please show output here):
```

dvd+rw-mediainfo /dev/sr0

```
and also try to read its first block by the block device driver:
```

dd if=/dev/sr0 bs=2048 count=1 of=/dev/null

```
which possibly yields an i/o error message. If so, have a look in
the system error log (dmesg ? view /var/log/messages) whether you
see fresh messages like
```

Mar 13 20:19:39 ts6 kernel: [26793211.100763] Sense Key : Medium Error [current] 
Mar 13 20:19:39 ts6 kernel: [26793211.100764] Info fld=0x5a80
Mar 13 20:19:39 ts6 kernel: [26793211.100765] sr 2:0:0:0: [sr0]
Mar 13 20:19:39 ts6 kernel: [26793211.100766] Add. Sense: Unrecovered read error
Mar 13 20:19:39 ts6 kernel: [26793211.100767] sr 2:0:0:0: [sr0] CDB:
Mar 13 20:19:39 ts6 kernel: [26793211.100768] Read(10): 28 00 00 00 5a 42 00 00 40 00

```
If this does not yield error, try to read the whole medium:
```

dd if=/dev/sr0 bs=2048 count=775960 of=/dev/null

```
or via a burn program's i/o driver:
```

xorriso -outdev /dev/sr0 -check_media use=outdev --

```

-------------------

The classical workaround attempt is to try another medium. Better not from
the same pack as the one that failed. Best from a different medium type
(e.g. DVD-R instead of DVD+R).
If this always yields read errors when checking, then the purchase of
a new DVD burner has to be considered.

Have a nice day :)

Thomas

---

### Post by anon_private on 2017-04-02
> **scdbackup said:**
> Hi,

the growisofs run does not show error indications. Especially not with
the first block of the DVD+R. So it is probable that your drive and the
medium silently did not like each other.

To diagnose further, you could inspect the nominal structure of the
DVD+R medium in question (please show output here):
```

dvd+rw-mediainfo /dev/sr0

```
and also try to read its first block by the block device driver:
```

dd if=/dev/sr0 bs=2048 count=1 of=/dev/null

```
which possibly yields an i/o error message. If so, have a look in
the system error log (dmesg ? view /var/log/messages) whether you
see fresh messages like
```

Mar 13 20:19:39 ts6 kernel: [26793211.100763] Sense Key : Medium Error [current] 
Mar 13 20:19:39 ts6 kernel: [26793211.100764] Info fld=0x5a80
Mar 13 20:19:39 ts6 kernel: [26793211.100765] sr 2:0:0:0: [sr0]
Mar 13 20:19:39 ts6 kernel: [26793211.100766] Add. Sense: Unrecovered read error
Mar 13 20:19:39 ts6 kernel: [26793211.100767] sr 2:0:0:0: [sr0] CDB:
Mar 13 20:19:39 ts6 kernel: [26793211.100768] Read(10): 28 00 00 00 5a 42 00 00 40 00

```
If this does not yield error, try to read the whole medium:
```

dd if=/dev/sr0 bs=2048 count=775960 of=/dev/null

```
or via a burn program's i/o driver:
```

xorriso -outdev /dev/sr0 -check_media use=outdev --

```

-------------------

The classical workaround attempt is to try another medium. Better not from
the same pack as the one that failed. Best from a different medium type
(e.g. DVD-R instead of DVD+R).
If this always yields read errors when checking, then the purchase of
a new DVD burner has to be considered.

Have a nice day :)

Thomas

```
andrew@andrew-Dell-DM061:~$ dvd+rw-mediainfo /dev/sr0
INQUIRY:                [HL-DT-ST][DVD+-RW GSA-H31N][B109]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         11h, DVD-R Sequential
 Current Write Speed:   16.0x1385=22160KB/s
 Write Speed #0:        16.0x1385=22160KB/s
 Write Speed #1:        12.0x1385=16620KB/s
 Write Speed #2:        8.0x1385=11080KB/s
 Write Speed #3:        4.0x1385=5540KB/s
 Speed Descriptor#0:    00/4294967295 R@8.0x1385=11080KB/s W@16.0x1385=22160KB/s
 Speed Descriptor#1:    00/4294967295 R@8.0x1385=11080KB/s W@12.0x1385=16620KB/s
 Speed Descriptor#2:    00/4294967295 R@8.0x1385=11080KB/s W@8.0x1385=11080KB/s
 Speed Descriptor#3:    00/4294967295 R@8.0x1385=11080KB/s W@4.0x1385=5540KB/s
READ DVD STRUCTURE[#10h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2298496*2KB=4707319808
READ DVD STRUCTURE[#0h]:
 Media Book Type:       25h, DVD-R book [revision 5]
 Last border-out at:    4290775037*2KB=8787507275776
READ DISC INFORMATION:
 Disc status:           blank
 Number of Sessions:    1
 State of Last Session: empty
 "Next" Track:          1
 Number of Tracks:      1
READ TRACK INFORMATION[#1]:
 Track State:           blank
 Track Start Address:   0*2KB
 Next Writable Address: 0*2KB
 Free Blocks:           2297888*2KB
 Track Size:            2297888*2KB
READ CAPACITY:          0*2048=0
andrew@andrew-Dell-DM061:~$ 

```


```
andrew@andrew-Dell-DM061:~$ dd if=/dev/sr0 bs=2048 count=1 of=/dev/null
dd: error reading ‘/dev/sr0’: Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.108233 s, 0.0 kB/s
andrew@andrew-Dell-DM061:~$ 

```

Partial data from dmesg ?

```
dmesg ? [10642.060064] blk_update_request: I/O error, dev fd0, sector 0
[10642.060074] floppy: error -5 while reading block 0
[10642.084051] blk_update_request: I/O error, dev fd0, sector 0
[10642.084060] floppy: error -5 while reading block 0
[10974.652747] sr 1:0:0:0: [sr0] tag#18 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10974.652757] sr 1:0:0:0: [sr0] tag#18 Sense Key : Illegal Request [current] 
[10974.652765] sr 1:0:0:0: [sr0] tag#18 Add. Sense: Illegal mode for this track
[10974.652772] sr 1:0:0:0: [sr0] tag#18 CDB: Read(10) 28 00 00 00 00 00 00 00 01 00
[10974.652778] blk_update_request: I/O error, dev sr0, sector 0
[10974.660725] sr 1:0:0:0: [sr0] tag#19 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10974.660732] sr 1:0:0:0: [sr0] tag#19 Sense Key : Illegal Request [current] 
[10974.660738] sr 1:0:0:0: [sr0] tag#19 Add. Sense: Illegal mode for this track
[10974.660743] sr 1:0:0:0: [sr0] tag#19 CDB: Read(10) 28 00 00 00 00 00 00 00 01 00
[10974.660747] blk_update_request: I/O error, dev sr0, sector 0
[10974.660752] Buffer I/O error on dev sr0, logical block 0, async page read
andrew@andrew-Dell-DM061:~$ 

```

I think that I prefer:

'The classical workaround attempt is to try another medium. Better not from
the same pack as the one that failed. Best from a different medium type
(e.g. DVD-R instead of DVD+R)'.

I used DVD-R. The next step could be DVD+R. What about makes of DVD-R - I assume that make is not important. It is formatting that counts.

I have been told that DVD RW tend to encourage more problems.

By the way. Thank you for all the work, and the thought.

---

### Post by scdbackup on 2017-04-02
Hi,

> > (e.g. DVD-R instead of DVD+R).
> I used DVD-R.

I need new glasses at it seems ... or an even larger screen.

> 
```

 Disc status:           blank
 Number of Sessions:    1
 State of Last Session: empty
 "Next" Track:          1
 Number of Tracks:      1
READ TRACK INFORMATION[#1]:
 Track State:           blank
 Track Start Address:   0*2KB
 Next Writable Address: 0*2KB

```

At least as far as the hardware table-of-content is concerned the medium
was not changed by the burn run. As if it was a done with growisofs option
-use-the-force-luke=dummy.


> 
```

[10974.652747] sr 1:0:0:0: [sr0] tag#18 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10974.652757] sr 1:0:0:0: [sr0] tag#18 Sense Key : Illegal Request [current]
[10974.652765] sr 1:0:0:0: [sr0] tag#18 Add. Sense: Illegal mode for this track
[10974.652772] sr 1:0:0:0: [sr0] tag#18 CDB: Read(10) 28 00 00 00 00 00 00 00 01 00

```

The drive seems to believe this too. It does not allow the block device
driver to read block 0. "Illegal Request"/"Illegal mode for this track" is
a message from the drive (translated by the kernel from sense code 5,64,00).


> What about makes of DVD-R - I assume that make is not important.
> It is formatting that counts.

Neither DVD+R nor DVD-R are formatted. But the light sensitive dye
may be of different chemical composition.

The drive's opinion about the medium after it was written indicates that
either the drive did not properly prepare the DVD-R Disc-at-Once run or
that the laser's power was not strong enough to imprint the
table-of-content and the data blocks into the dye.
As said, it looks like a dummy run although growisofs was not ordered
by K3B to do dummy and thus will hardly have told the drive to do so.

With DVD+R there is no opportunity for dummy runs. At least not as long
as the drive's laser can write.


> I have been told that DVD RW tend to encourage more problems.

DVD+RW are quite reliable.

DVD-RW normally work fine on the first few usages in a new burner.
Then it depends much on your luck.
To my experience they last longer if formatted to "Restricted Overwrite":
```

dvd+rw-format -force /dev/sr0

```
This normally lasts as long as a full write run. Afterwards the DVD-RW
behaves much like DVD+RW (except the "Restriction" that one has to write
packets of 32 KB rather than 2 KB).

Have a nice day :)

Thomas

---

### Post by anon_private on 2017-04-02
Am I correct in assuming that the best way forward is to try different media, say DVD+R

---

### Post by Kris_M on 2017-04-02
Yeah I had a prob with k3b last night - 1.2GB iso - burnt 94% then stopped and didn't say anything. Twice. Picked a different program and worked fine. Weird.

---

### Post by scdbackup on 2017-04-02
Hi,

Kris_M wrote:
> k3b last night - 1.2GB iso - burnt 94% then stopped and didn't say anything.

@anon_private: Did your K3B get into that state too ?

If there was a final error message like
```

  :-[ WRITE@LBA=19c70h failed with SK=0h/ASC=00h/ACQ=03h]: Input/output error
  :-( write failed: Input/output error

```
then i would say you suffer from
  [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=794868](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=794868)

If K3B offers the opportunity to keep the DVD-R "appendable" or "open
for further writing", then this would choose write type "Incremental"
and thus avoid the bug.

But anon_private experiences that the medium appears to be unused
and still burnable after the run.
Re-reading the first message i begin to suspect that the first simulated
burn process caused drive or K3B to be stuck in simulation mode (aka dummy
burning).
Re-starting K3B or power-off-power-on at the burner (computer ?) might
help to bring everything into normal state again.


> Picked a different program and worked fine.

Do you know which backend it uses ? growisofs, wodim, cdrecord, libburn ?


Have a nice day :)

Thomas

---

### Post by Kris_M on 2017-04-02
I don't recall an error message - it just sat there - seemed to lock up. When I clicked cancel it took a couple minutes to cancel. like it suddenly went into very slow motion after a high speed burn of 94%.

The media was definitely burned.

I believe I then used Brasero to do it and it ran fine. Not a media prob or burner prob. I'll definitely stay away from K3B for a while, though it did burn a couple CDs fine.  I used it in very distant past with no probs.  Just a small hiccup on life's path!

Extremely rare that I burn plastic anyway - that one I tested and then put to USB.

I had just deleted my win7 partitions and was trying to find a bootable iso with a defragger, which I did.

---

### Post by anon_private on 2017-04-02
In my case, k3b stated that the DVD was empty. But when I put the disk into a Windows machine it said that the disk contained data and could not be written to!

---

### Post by scdbackup on 2017-04-02
Hi,

anon_private wrote:
> when I put the disk into a Windows machine it said that the disk 
> contained data and could not be written to!

Looks like the DVD drive at the Linux machine cannot read what it
wrote, whereas the one at the Windows machine sees something.
I doubt that this is due to the difference of operating systems.

Can you read the files on the DVD by help of the Windows machine ?


@Kris_M: Normally burn success is a matter of drive, media, and
burn (backend) program. Nevertheless the frontends like K3B or Brasero
sometimes manage to spoil success by their own means.
If you experience undesired behavior with libburn, we could enter the
joyful adventure of a bug hunt.

Have a nice day :)

Thomas

---

### Post by Kris_M on 2017-04-02
> **scdbackup said:**
> Hi,

anon_private wrote:
> when I put the disk into a Windows machine it said that the disk 
> contained data and could not be written to!

Looks like the DVD drive at the Linux machine cannot read what it
wrote, whereas the one at the Windows machine sees something.
I doubt that this is due to the difference of operating systems.

Can you read the files on the DVD by help of the Windows machine ?


@Kris_M: Normally burn success is a matter of drive, media, and
burn (backend) program. Nevertheless the frontends like K3B or Brasero
sometimes manage to spoil success by their own means.
If you experience undesired behavior with libburn, we could enter the
joyful adventure of a bug hunt.

Have a nice day :)

Thomas

definite no. I am on to other things and probably won't burn anything for another year! :D

Also - same media, same hardware, different program worked.

---

