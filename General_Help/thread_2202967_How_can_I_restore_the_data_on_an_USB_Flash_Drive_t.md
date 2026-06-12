---
title: "How can I restore the data on an USB Flash Drive that got wiped by a virus?"
date: 2014-02-01
forum: General Help
---

### Post by amjjawad on 2014-02-01
Hi everyone,

Might not be the best title of this thread but allow me to explain in details.

A neighbour with his daughter just visited me a while ago.
The daughter has an USB Flash Drive (2GB) which she is using at her school. One day, she plugged the USB to her School Computer (which is obviously running Windows) and all the data on that USB Flash Drive AND the Computer are gone. Seems very much like a nasty virus.

The family needed my help and I convinced them to switch to Linux AND also save the files on the USB Flash Drive because it has important data (school projects, etc).

When I plugged the USB to my machine, I got this screenshot:

[ATTACH=CONFIG]249982[/ATTACH]

I haven't yet seen a virus just as this. To wipe the entire disk and the partition? that is something new to me.

My Question is simple:
How can I save or get the data back? any chance?

Thank you in advance!

---

### Post by Bucky Ball on 2014-02-01
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Sure this wasn't user error? Just looks like a wiped dongle to me. Anyways, good luck. ;)

---

### Post by amjjawad on 2014-02-01
> **Bucky Ball said:**
> [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Sure this wasn't user error? Just looks like a wiped dongle to me. Anyways, good luck. ;)

Yes, just chatted with the daughter a while ago and she confirmed it is not a user error as in someone who did that. Of course, this is what she confirmed.

Thank you, will look into that while I convert her laptop to Linux ;)

---

### Post by mastablasta on 2014-02-01
well i just had the old drive's partition wiped. but this was done by antivirus it seems while it was removing the malware. testdisk seems might be abel to solve the data if it's still there.SMART test confirmed the disk is still in excelent shape.

---

### Post by amjjawad on 2014-02-01
```
No Partition found or selected for recovery
```

This is what I get after doing quick and deep search :(

It doesn't seem as a good sign but I am not sure!

---

### Post by varunendra on 2014-02-01
Might produce a lot of broken/corrupt/unusable junk files in random order without their original names or directory structure, but you should still give PhotoRec a shot : [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

It is part of TestDisk package, so is already installed if you installed testdisk.

---

### Post by Portaro on 2014-02-01
can you post the result of command 
sudo sfdisk -l

to see if the problem is onMBR

---

### Post by amjjawad on 2014-02-01
> **Portaro said:**
> can you post the result of command 
sudo sfdisk -l

to see if the problem is onMBR

Hi,

```
 Disk /dev/sdb: 1015 cylinders, 65 heads, 62 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type
No partitions found



```

Is it a hopeless case?

---

### Post by Bucky Ball on 2014-02-02
> **amjjawad said:**
> 
Is it a hopeless case?

I'm guessing yes as that dongle is completely wiped and just looks like free space, but I would wait for wiser heads before taking my word ...

---

### Post by varunendra on 2014-02-02
> **amjjawad said:**
> Is it a hopeless case?

Unless the previous data is physically overwritten, there is always hope, just make sure to give testdisk/photorec correct information about the previously existing partition(s) *(usually just the partition table type (intel), or in rare cases disk geometry)*. Or use a software that is smarter than these tools and can 'guess' the correct parameters itself.

You can find many such (free) tools (including testdisk) on [HBCD]("http://www.hirensbootcd.org/download/"), or you may try some commercial solutions (trial mode is free, in which they will just list the recoverable files, won't actually recover them). Although based on my personal experience with many 'reputed' commercial tools (Runtime's Get Data Back, R-Tools's various tools, some others that I don't remember now), I trust testdisk/photorec the most. They are, in my personal experience so far, fastest and most capable. But I also remember one particular case where Get Data Back was more successful than TestDisk.

---

### Post by amjjawad on 2014-02-02
> **varunendra said:**
> Unless the previous data is physically overwritten, there is always hope, just make sure to give testdisk/photorec correct information about the previously existing partition(s) *(usually just the partition table type (intel), or in rare cases disk geometry)*. Or use a software that is smarter than these tools and can 'guess' the correct parameters itself.

You can find many such (free) tools (including testdisk) on [HBCD]("http://www.hirensbootcd.org/download/"), or you may try some commercial solutions (trial mode is free, in which they will just list the recoverable files, won't actually recover them). Although based on my personal experience with many 'reputed' commercial tools (Runtime's Get Data Back, R-Tools's various tools, some others that I don't remember now), I trust testdisk/photorec the most. They are, in my personal experience so far, fastest and most capable. But I also remember one particular case where Get Data Back was more successful than TestDisk.

This is what I am trying to explain but I am not sure if I made myself clear?!

1- There is 'no' partition table for this flash drive - see the very first post on this thread.
2- I have tried to choose Intel Partition Table and other options but 'testdisk' didn't find anything :(

The user confirmed that she didn't remove anything herself, neither her computer teacher at school.
Could it be some kind of anti-virus software that did this? when I used to deal with these useless programs, I haven't come across any program that could do this to an USB Drive.

It seems that testdisk is searching for the partition table but it can't find any.
So, I just want to make sure that I am doing the right thing here and I just want to make sure I am not wasting my time.

---

### Post by The Cog on 2014-02-02
Testdisk can also search an entire drive for what looks like the start of a partition, in order to be able to rebuild a damaged partition table. But don't make any changes to the stick until you have taken an image of it. A command like this should take an image - make sure you get the right device name though.
```
sudo dd if=/dev/sdb of=stick.img
```
It might be useful if we can see the contents of the start of the stick. Can you post the output of this command:
```
sudo sh -c 'dd if=/dev/sdb bs=1024 count=1 | hd'
```

P.S.
It may be that the stick didn't have a partition table anyway - it is possible to place a filesystem directly onto a disk or stick rather than creating a partition table and using partitions.

---

### Post by dragonfly41 on 2014-02-02
TestDisk is indeed a good tool for recovery .. so don't give up hope yet .. there are many other forensic tools to try ..

If you have selected in testdisk run .. Create testdisk.log .. look in your home directory /home/user/testdisk.log .. and publish log file here for us to look at.

p.s. another recommendation is to clone/copy contents of your failed USB (onto another USB drive) and using testdisk try to recover data from the copy .. in case you screw up the original copy [as in post#12 above].

[Further edit] .. this seems to be an unpartitioned device (or has been turned into that) .. so tread carefully .. do not be tempted to experiment by adding a partition .. until your data is recovered ...

Follow testdisk advice .. Do NOT select testdisk option "non partitioned media".

[http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)

> Note: Do NOT select 'None' for media with only a single partition. It's very
rare for a drive to be 'Non-partitioned'.

[http://askubuntu.com/questions/276582/is-it-safe-to-use-a-usb-external-drive-without-a-valid-partition-table](http://askubuntu.com/questions/276582/is-it-safe-to-use-a-usb-external-drive-without-a-valid-partition-table)

---

### Post by dragonfly41 on 2014-02-02
Here is a partition recovery tool which runs on windows ...

[http://www.partition-tool.com/partition-recovery-wizard/recover-lost-partition.htm](http://www.partition-tool.com/partition-recovery-wizard/recover-lost-partition.htm)

---

### Post by varunendra on 2014-02-02
> **amjjawad said:**
> This is what I am trying to explain but I am not sure if I made myself clear?!

I don't have a habit of posting without properly reading the problem (even if it spans across tens of posts) and properly understanding it. So yes, I know testdisk didn't find anything. But if data recovery were as simple as downloading a free application and running it with default options, or even as per a well written 'Generalized' guide, there wouldn't be so many pricey services out there for the same purpose and earning well.

That being said, I don't think rephrasing my post is going to help, and I don't have any further suggestions regarding the problem, sorry.

---

### Post by amjjawad on 2014-02-02
For some very weird reason, the USB Drive is no longer detectable by any computer :(

I don't know what happened!

---

### Post by amjjawad on 2014-02-02
I don't know what is going on?
My machine now can detect the USB.

> **The Cog said:**
> Testdisk can also search an entire drive for what looks like the start of a partition, in order to be able to rebuild a damaged partition table. But don't make any changes to the stick until you have taken an image of it. A command like this should take an image - make sure you get the right device name though.
```
sudo dd if=/dev/sdb of=stick.img
```

```
$ sudo dd if=/dev/sdc of=stick.img
4091904+0 records in
4091904+0 records out
2095054848 bytes (2.1 GB) copied, 149.673 s, 14.0 MB/s


```

> It might be useful if we can see the contents of the start of the stick. Can you post the output of this command:
```
sudo sh -c 'dd if=/dev/sdb bs=1024 count=1 | hd'
```


```
$ sudo sh -c 'dd if=/dev/sdc bs=1024 count=1 | hd'
1+0 records in
1+0 records out
1024 bytes (1.0 kB) copied, 0.00190474 s, 538 kB/s
00000000  55 aa 55 aa 56 4d 0d 1a  60 8e 68 88 2b b6 e6 64  |U.U.VM..`.h.+..d|
00000010  e2 d0 87 0d 3d b8 f3 46  e7 18 e9 21 ff 37 e6 83  |....=..F...!.7..|
00000020  44 74 7b f6 93 3d 78 7c  1d d3 0f b0 be ad 5e 05  |Dt{..=x|......^.|
00000030  b2 0c 2d 53 0c 5a d8 64  0f cc 77 c7 80 49 00 75  |..-S.Z.d..w..I.u|
00000040  3a 00 db 3a c3 e9 0b 0a  a8 35 b0 b6 27 41 9a 16  |:..:.....5..'A..|
00000050  40 8b 1b c2 9b a0 f0 d7  d3 21 ff 66 98 29 23 b6  |@........!.f.)#.|
00000060  79 20 b9 0e d2 05 60 5e  da dc ba ef ce 21 be df  |y ....`^.....!..|
00000070  86 5d 3e 0a b0 96 8f ee  ad 20 09 5f 22 01 96 de  |.]>...... ._"...|
00000080  aa 7b 52 e0 55 ce 84 55  e0 d7 91 1e 80 94 cb 20  |.{R.U..U....... |
00000090  61 f7 9d 06 99 3c 7e 03  4a 32 3b a4 0b 01 98 99  |a....<~.J2;.....|
000000a0  92 c8 61 d1 0c 56 1f c3  4f a2 6b 9b 52 2b 84 0c  |..a..V..O.k.R+..|
000000b0  a8 8e 1c b3 4c f7 37 f8  1c c1 5f 4b 1b 90 1d 44  |....L.7..._K...D|
000000c0  d5 65 1a f2 ca 9e a9 2d  7c f5 45 68 d2 d8 d4 31  |.e.....-|.Eh...1|
000000d0  77 d7 f9 9b a1 bd 86 04  99 90 d0 ce 60 22 c8 73  |w...........`".s|
000000e0  12 08 f6 5b 80 37 66 83  2f 37 86 03 ea 09 4a 5f  |...[.7f./7....J_|
000000f0  4c 23 19 f7 79 2d 32 35  f7 41 26 c7 75 90 3a 2d  |L#..y-25.A&.u.:-|
00000100  e6 fc 55 ac fc 13 24 46  d9 8c ac 8d f2 7c 26 d4  |..U...$F.....|&.|
00000110  df 80 fd fe 88 94 ac 8b  3c 1b 34 69 9a 69 94 8d  |........<.4i.i..|
00000120  d0 f3 1c f8 ec 8c 20 1e  23 13 0a f8 db ba 5a 0e  |...... .#.....Z.|
00000130  97 c8 60 1e 2e 97 15 ae  09 7b db 1a 2c d8 6e a1  |..`......{..,.n.|
00000140  cb 89 87 a0 6b 94 e9 71  41 c3 6d fd 2d 0e 0f 5f  |....k..qA.m.-.._|
00000150  86 34 6f 4c 88 52 7a 58  99 0b 3f fa 2b f8 ba 51  |.4oL.RzX..?.+..Q|
00000160  fb 11 f0 39 71 aa b3 cb  f2 5c 71 b7 2c 50 46 69  |...9q....\q.,PFi|
00000170  e2 12 cf 17 31 02 7a 4d  0c 21 88 87 11 f7 d0 74  |....1.zM.!.....t|
00000180  8a 1a 52 30 08 a7 90 fb  ef df 0c 01 8b 4b 24 12  |..R0.........K$.|
00000190  5d 82 3c 8b e2 f1 6c b1  16 dc 00 4a c2 32 47 cf  |].<...l....J.2G.|
000001a0  e8 89 6a 4b a5 fb be 4b  b2 ae 3f 0b f5 5c eb 33  |..jK...K..?..\.3|
000001b0  2e 7c e0 b2 ee 11 25 31  59 c5 fd 95 78 eb e2 ae  |.|....%1Y...x...|
000001c0  24 c6 47 db 2d ff 1b 30  f4 2f ef 7a 6c 3e df 5b  |$.G.-..0./.zl>.[|
000001d0  98 54 14 d8 8e d3 94 4e  08 85 93 ba f0 ac 91 b1  |.T.....N........|
000001e0  ea 78 d4 b4 bc 6a c4 68  78 cd 0f d4 7f 02 61 22  |.x...j.hx.....a"|
000001f0  2a f2 6f 73 9d c9 b9 4b  fc 51 6f 5d 63 3e 74 a8  |*.os...K.Qo]c>t.|
00000200  42 bd 77 d3 ba 14 f3 e4  d5 f4 7a 96 6d 65 ed d9  |B.w.......z.me..|
00000210  53 81 bb b4 3b 26 fb 52  9c be 32 a7 cc ff 8e df  |S...;&.R..2.....|
00000220  58 e6 17 35 68 c7 2b 76  da 7b be 3b 2f 39 dc 37  |X..5h.+v.{.;/9.7|
00000230  b6 77 68 af f7 68 6c 82  db bc a5 c4 17 fa 22 ef  |.wh..hl.......".|
00000240  bd e8 00 d2 7f b4 15 7b  30 2e a3 eb 1e 6f c0 8f  |.......{0....o..|
00000250  8c 2c 26 0e 28 80 60 83  6b b9 7b a8 3b 75 37 49  |.,&.(.`.k.{.;u7I|
00000260  26 5b c9 1c 4f 0b 81 01  b3 83 43 7f cb 2c a0 9f  |&[..O.....C..,..|
00000270  9e 94 f8 c7 c2 81 d4 cf  12 f6 45 df 1a cd 12 cb  |..........E.....|
00000280  66 d3 71 33 1b 9a 3d 31  78 cf 7b bb b4 88 ab 8d  |f.q3..=1x.{.....|
00000290  4a 23 58 8e 43 1b 49 03  e8 cb 7e 5a 7a 76 1e 33  |J#X.C.I...~Zzv.3|
000002a0  1a ed e3 f9 1a f7 af fe  9f 67 f9 3e 7d 69 5d b2  |.........g.>}i].|
000002b0  76 a2 a2 70 6c 52 02 de  4d 59 3c fc 0d 28 59 70  |v..plR..MY<..(Yp|
000002c0  ae ba a1 65 18 f7 a6 29  07 2d f1 7f f8 e6 1c b7  |...e...).-......|
000002d0  30 1f 0d dd 0c 07 26 68  29 33 4a da df 67 ce 9f  |0.....&h)3J..g..|
000002e0  23 9d f1 55 4e 35 bc 95  0b 78 c0 7f 47 b2 60 17  |#..UN5...x..G.`.|
000002f0  53 90 26 c6 b9 8d 02 10  4d 4f 55 6d 73 7c e9 e7  |S.&.....MOUms|..|
00000300  e1 8a d5 28 a4 4b f6 c8  de 55 10 5a ca 08 1f 82  |...(.K...U.Z....|
00000310  a0 73 fe 55 08 5c 9f a9  50 a7 76 22 62 3e 29 0e  |.s.U.\..P.v"b>).|
00000320  c2 b9 0b af 5a df 2e 69  5c e2 6f ca 56 93 92 cc  |....Z..i\.o.V...|
00000330  46 73 fd 8b 43 43 c4 1d  7c 44 9d 59 a2 e0 dd a9  |Fs..CC..|D.Y....|
00000340  f2 f9 f2 78 af 29 6e 57  c9 2c 47 bc 2c 83 c1 2d  |...x.)nW.,G.,..-|
00000350  13 fc 5f 67 31 ba fe 75  27 dc ae 35 9c 4d 25 ea  |.._g1..u'..5.M%.|
00000360  df 09 a5 2f 69 ce bf 24  59 4f a6 28 10 86 03 10  |.../i..$YO.(....|
00000370  50 1b 56 4f 4d f4 a8 a2  75 b9 4b 30 a8 6d a0 0c  |P.VOM...u.K0.m..|
00000380  2e e9 7f 28 b3 74 f4 df  23 e2 02 92 ef 61 8a 89  |...(.t..#....a..|
00000390  1d ee 63 d2 d7 e7 73 b2  11 00 59 ee 11 04 a5 ef  |..c...s...Y.....|
000003a0  69 bd f0 9a f7 a7 b5 92  bb b6 82 aa d7 f7 45 ed  |i.............E.|
000003b0  a8 57 2a e7 1e da 3d fb  8b 4d e3 35 e2 95 e5 86  |.W*...=..M.5....|
000003c0  82 7b 4d e4 2a c9 2e b5  a2 c6 b7 b1 a0 fa d6 31  |.{M.*..........1|
000003d0  3d 55 c7 6e fe 30 61 cf  70 0d 7d 8d 76 04 a9 04  |=U.n.0a.p.}.v...|
000003e0  a4 28 60 38 5e c9 76 17  fb d7 06 5b 0d 41 5c 6b  |.(`8^.v....[.A\k|
000003f0  28 03 12 30 bd ed 56 b8  ef f2 7f da d3 f9 7b 99  |(..0..V.......{.|
00000400


```

> P.S.
It may be that the stick didn't have a partition table anyway - it is possible to place a filesystem directly onto a disk or stick rather than creating a partition table and using partitions.
How come? if you check the very first post of this thread, you will notice that there is a read "i" sign next to the drive space gray area. That tells you without a partition table, there is no way you can use the drive. So, there should be a partition table IMHO and AFAIK to store any data :)
This is what we have studied at university unless someone changed it without telling :P

---

### Post by amjjawad on 2014-02-02
[HR][/HR]Does this make any sense?

```
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 2095 MB / 1998 MiB - CHS 1015 65 62
Current partition structure:
     Partition                  Start        End    Size in sectors


Partition sector doesn't have the endmark 0xAA55


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
>[Quick Search]
                            Try to locate partition


```

---

### Post by amjjawad on 2014-02-02
testdisk.log

```


Mon Feb  3 03:25:27 2014
Command line: TestDisk

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 3.11.0-12-generic (#19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013) i686
Compiler: GCC 4.8
Compilation date: 2013-08-23T16:52:16
ext2fs lib: 1.42.8, ntfs lib: libntfs-3g, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, DCO support
/dev/sda: size       78177792 sectors
/dev/sda: user_max   78177792 sectors
/dev/sda: native_max 78177792 sectors
/dev/sda: dco        78177792 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - 1 sectors, sector size=512
Hard disk list
Disk /dev/sda - 40 GB / 37 GiB - CHS 4866 255 63, sector size=512 - MAXTOR 6L040J2, S/N:662245240133, FW:AR1.0500
Disk /dev/sdb - 2095 MB / 1998 MiB - CHS 1015 65 62, sector size=512 - Generic Flash Disk 2.0, FW:2.20

Partition table type default to Intel
Disk /dev/sdb - 2095 MB / 1998 MiB - Generic Flash Disk 2.0
Partition table type: Intel

Analyse Disk /dev/sdb - 2095 MB / 1998 MiB - CHS 1015 65 62
Current partition structure:

Partition sector doesn't have the endmark 0xAA55

search_part()
Disk /dev/sdb - 2095 MB / 1998 MiB - CHS 1015 65 62

Results

interface_write()
 
No partition found or selected for recovery

search_part()
Disk /dev/sdb - 2095 MB / 1998 MiB - CHS 1015 65 62

Results

interface_write()
 
No partition found or selected for recovery


```

---

### Post by dragonfly41 on 2014-02-03
You should really read the testdisk forum (or even subscribe) for more tips on use of testdisk

The testdisk.log which you have at last posted has this important clue ..

[COLOR=blue]"Partition sector doesn't have the endmark 0xAA55"[/COLOR]

Google search with above phrase shows other users with same problem ..

[https://www.google.co.uk/search?client=ubuntu&channel=fs&q=Partition+sector+doesn%27t+have+the+endmark+0xAA55](https://www.google.co.uk/search?client=ubuntu&channel=fs&q=Partition+sector+doesn%27t+have+the+endmark+0xAA55)

Here are just a few examples from google search return ...

[http://forum.cgsecurity.org/phpBB3/usb-stick-unreadable-t462.html](http://forum.cgsecurity.org/phpBB3/usb-stick-unreadable-t462.html)

[http://ubuntuforums.org/showthread.php?t=2110027](http://ubuntuforums.org/showthread.php?t=2110027)

[http://www.techsupportforum.com/forums/f149/trying-to-recover-external-pen-drive-testdisk-731169.html](http://www.techsupportforum.com/forums/f149/trying-to-recover-external-pen-drive-testdisk-731169.html)


and this thread (which also recommends testdisk) dives into the depths of boot repair ...

[http://reboot.pro/topic/10571-disaster-partition-now-not-recognised-after-accident-with-bootice/](http://reboot.pro/topic/10571-disaster-partition-now-not-recognised-after-accident-with-bootice/)


Rather than suspecting a virus I believe that this has all the hallmarks of a flash drive just being yanked out without using the PC option "eject" or "safely remove hardware".  However your opening message says that the host computer has also lost files.   Is this the case?

---

### Post by mastablasta on 2014-02-03
well you wrote it yourself 
> . So, there should be a partition table IMHO and AFAIK to store any data 

- so create/restore a partition table first: 
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

hmm i have similar tough time with HDD still need to try a few tricks to restore the table before reformating it.

---

### Post by sudodus on 2014-02-03
> **varunendra said:**
> Might produce a lot of broken/corrupt/unusable junk files in random order without their original names or directory structure, but you should still give PhotoRec a shot : [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

It is part of TestDisk package, so is already installed if you installed testdisk.

+1

When the file system is borked beyond repair, but the file data still reside in the memory cells, you can use ***PhotoRec***, which uses only headers and data to localize what can be recovered. Please listen to *varunendra*'s advice! I know that it works. It started as a tool to recover photos from flash memory cards, but now it can identify and recover most common file types.

It has helped me, and many other people. It is not convenient, because the file names and directory structure is gone. Fragmented files might be only partially recovered ... but it can save quite a lot, because most of the time only a small part (not the whole drive) is overwritten.

---

### Post by The Cog on 2014-02-03
> How come? if you check the very first post of this thread, you will notice that there is a read "i" sign next to the drive space gray area. That tells you without a partition table, there is no way you can use the drive. So, there should be a partition table IMHO and AFAIK to store any data 
This is what we have studied at university unless someone changed it without telling 

What the "I" sign is telling you that without a partition table, there is no way you can use a partition editor.

It is possible to use a drive without giving it a partition table. You just write the filesystem to the drive as a whole rather than to a partition on the drive. You would then have to mount (e.g.) /dev/sdb instead of /dev/sdb1. 

The dump of the first 1024 bytes that you posted shows that the first sector does not end in the two bytes 0xaa, 0x55 which it would if it were a valid partition table. It doesn't look to me to contain boot code at the start either. Neither does it contain any strings that might help identify what it does contain. It does however start with 55AA55AA which as far as I can tell from a quick google search is the magic marker for a BIOS extension. On top of that, testdisk was unable to find any trace of the start of a partition further in, so it can't help in rebuilding any corrupt partition table.

I don't have the knowledge to go further than that. And without more knowledge, all I can suggest it using photorec to recover whatever files it can figure out, if there are any remnants on there.

---

### Post by amjjawad on 2014-02-04
Hi again,

Because I have a feeling that we're talking apples and oranges here, I wanted to make sure that we understand each others. Therefore, [I created this post]("http://amjjawad.blogspot.com/2014/02/trying-to-save-data-from-2gb-usb-drive.html").

I do hope now that we are on the same page.

Thank you!

---

### Post by dragonfly41 on 2014-02-04
This is only the first part of your troubleshooting.

As advised in earlier posts now, with command terminal still open, run ...

$ sudo photorec

Search and select Disk /dev/sdb

Proceed to look for files

Note that you may see older files which have been deleted on your flash USB.

You can add these additional screenshots from photorec (part of testdisk) to your blog.

---

### Post by amjjawad on 2014-02-04
Hi and thanks for posting :)

> **dragonfly41 said:**
> This is only the first part of your troubleshooting.
Okay, so I am glad that I wasn't doing something wrong and I am glad that we're at the same page. Now, I can carry on :)

> As advised in earlier posts now, with command terminal still open, run ...

$ sudo photorec

Search and select Disk /dev/sdb

Proceed to look for files

Note that you may see older files which have been deleted on your flash USB.

I will do that and report back :)

> You can add these additional screenshots from photorec (part of testdisk) to your blog.
Yes, that would be better to visualise (for everyone) what is doing on ;)

---

### Post by dragonfly41 on 2014-02-04
Here are fuller instructions (I've just tried the workflow on one of my flash drives).

First create a location in your home directory for recovery of your files .. 

perhaps /home/username/photorec_recovery

With command terminal open run

sudo photorec

select Disk /dev/sdb           Flash Disk

Proceed

select No partition [whole disk]

Choose filesystem type [Other]   FAT/NTFS/etc. (since your flash drive is probably FAT format for windows)

Select target directory for copying recovered files ... photorec_recovery

Press C to copy recovered files.

With luck you should see a message like ..

[color=blue]54 files saved in /home/username/photorec_recovery/recup_dir directory.
Recovery completed.[/color]

---

### Post by amjjawad on 2014-02-04
> **dragonfly41 said:**
> Here are fuller instructions (I've just tried the workflow on one of my flash drives).

First create a location in your home directory for recovery of your files .. 

perhaps /home/username/photorec_recovery

With command terminal open run

sudo photorec

select Disk /dev/sdb           Flash Disk

Proceed

select No partition [whole disk]

Choose filesystem type [Other]   FAT/NTFS/etc. (since your flash drive is probably FAT format for windows)

Select target directory for copying recovered files ... photorec_recovery

Press C to copy recovered files.

With luck you should see a message like ..

[COLOR=blue]54 files saved in /home/username/photorec_recovery/recup_dir directory.
Recovery completed.[/COLOR]

Thank you again for your efforts, I really appreciate that and I like to know there are other people like me who hate to give up :)

[It seems there are no files]("http://amjjawad.blogspot.com/2014/02/trying-to-save-data-from-2gb-usb-drive.html") :(

Anything else we can do?

---

### Post by Bucky Ball on 2014-02-04
If Photorec didn't find them, I doubt it. You might find an app that can do a deeper search.

---

### Post by dragonfly41 on 2014-02-04
If the lost data is very important then I would try these "last chance saloon" options .. but first try another recovery program such as RecoverMyFiles from GetData (advice earlier).

If pursuing the Ubuntu line .. first try to clone your Flash drive into another uncorrupted Flash drive so you can try to recover data from the COPY..

As suggested here ... [http://regex.info/blog/2008-12-03/1016](http://regex.info/blog/2008-12-03/1016)

> 
You should probably send a note to the PhotoRec guy, but in my case the card was recognized by my system&#8230; I it was just corrupt, so I couldn&#8217;t access it further (via the normal methods). There are plenty of things you can try (such as working out a deal to send the card to someone with more experience), but if you&#8217;ve completely run out of options, you could simply do a QUICK format in the computer, then mount it on your system, then run PhotoRec or the like. A QUICK format does not touch most of the data on the card, only the table of contents (so to speak). You might also look (first) into buying a new card that comes with photo-recovery software. Some of the upper-end cards used to. Good luck! &#8212;Jeffrey


The QUICK format (FAT) is found on Windows.   As written it does not overwrite the data.

Then after this QUICK format which will make the device usable try photorec again .. or testdisk.

Follow this advice at your own risk.   The backup/cloning is a particularly important step.

---

### Post by Portaro on 2014-02-04
IM visit the blog and in last pic i see that you try to save lost data of /dev/sdb, but i think that this partition is the primary partition - msdos or MBR  that make recognizable the pen drive, please test the command of photorec with this target -

/dev/sdb1

and give the result (if work) I hope.

---

### Post by amjjawad on 2014-02-04
> **Portaro said:**
> IM visit the blog and in last pic i see that you try to save lost data of /dev/sdb, but i think that this partition is the primary partition - msdos or MBR  that make recognizable the pen drive, please test the command of photorec with this target -

/dev/sdb1

and give the result (if work) I hope.

Hi, thanks for posting :)

Is this what you mean?

```
$ sudo photorec /dev/sdb1
PhotoRec 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Unable to open file or device /dev/sdb1

Usage: photorec [/log] [/debug] [/d recup_dir] [file.dd|file.e01|device]
       photorec /version

/log          : create a photorec.log file
/debug        : add debug information

PhotoRec searches various file formats (JPEG, Office...), it stores them
in recup_dir directory.

If you have problems with PhotoRec or bug reports, please contact me.


```

---

### Post by amjjawad on 2014-02-04
I thought to contact the user and ask her to re-tell her story so that, hopefully, we could reach to the solution:

> Okay I was using my usb completely fine in school and I ejected it SAFELY then I went home and not even two hours after I stuck my usb into my laptop at home like I do EVERY SINGLE DAY AFTER SCHOOL and then the usb came up with the message whicg comes up when you plyg it in now. I have a photo of the message on my phone if it says something else now but when ichecked into my documents the files had swiped. I didnt delete them nothing. So I've checked in the bin thing on the computer and there was nothing but some random files which werent important. The files that got deleted are the same files which I had on my usb but at a different stage in time.. then I plugged in the usb at school hoping it would work in school for some reason and the same thing happened.. I could safely eject the usb both times so there was no problem there but when I looked into the usb data it said there was no data found which was extremely strange.. Because I used it not even 2hours before that.. and I had no problems.. it was so sudden!  So if you can manage to retrieve any files of the usb then that would be super awesome! I have no explanation how my usb could swip my document files nor does my teacher and he was with me when it happened on the school computer :( 


When I asked her:
> [Did the USB Flash Drive of yours, when it was inserted to the PC at school, the USB has deleted the files on the Computer once you tried to access the USB] 


The answer was:
> Yes!

And, this is the picture she was talking about:

[ATTACH=CONFIG]250097[/ATTACH]

I didn't yet give up.
I will go through the other options suggested in this thread and I do hope we can achieve something :)

---

### Post by Bucky Ball on 2014-02-04
Has the old USB somehow been swapped with a new one in the bowels of her schoolbag? Perhaps she should empty that out and have a look because this is sounding more and more incredible! A USB with data on it ejects fine on one computer, goes in the bag, comes out two hours later, plug in, no data and asking to be formatted? Pranking? Practical joke? School bully? :-k

From the message 'You need to format the disk in drive E' it almost seems like someone has purposely wiped the drive, including all partitions. The fact that testdisk and photorec are showing nothing sounds even worse than that. Is there any possibility it was swapped with another of the same colour???

---

### Post by dragonfly41 on 2014-02-04
Reading a few posts on similar symptoms (including school/home scenario) I see that there is a virus which hides files and folders.

Recovery approach is to insert the infected removable flash drive back into host PC.

If you see any files named [kpcgrhynko..vbs] .. delete them.

Then run this command [color=blue]attrib -h -r -s /s /d [replace this with drive letter]:\*.*[/color]

[http://www.technize.info/how-to-manually-remove-virus-from-usb-flash-drive-without-formatting/](http://www.technize.info/how-to-manually-remove-virus-from-usb-flash-drive-without-formatting/)

I don't know the equivalent recovery workflow in ubuntu since I've not experienced that virus.

---

### Post by amjjawad on 2014-02-04
> **Bucky Ball said:**
> Has the old USB somehow been swapped with a new one in the bowels of her schoolbag? Perhaps she should empty that out and have a look because this is sounding more and more incredible! A USB with data on it ejects fine on one computer, goes in the bag, comes out two hours later, plug in, no data and asking to be formatted? Pranking? Practical joke? School bully? :-k

From the message 'You need to format the disk in drive E' it almost seems like someone has purposely wiped the drive, including all partitions. The fact that testdisk and photorec are showing nothing sounds even worse than that. Is there any possibility it was swapped with another of the same colour???

And, to add more fun to this story, I have tired the USB on Windows with two applications/programs to recover the data but ... these two didn't find anything whatsoever - same what Linux gave already.

I had already made a backup for the USB using the 'dd' command from post #12 if I remember correctly.

When I open the USB on Windows, it says the drive is not formatted and asked me to do so.
When I tried to do that, it said "Windows can NOT format this device".

Could be that someone has done that as a silly joke but a side from that, what is going on with this weird USB?!

Edit:
GParted installed on Lubuntu 13.10 can NOT detect the USB unless I boot my PC from the LiveUSB, that is the only way my Linux machine can detect or show the USB!!!

Yes, testdisk can detect it but Lubuntu can't. When I open GParted, Disk Utility or the File Manager, nothing whatsoever.

---

### Post by amjjawad on 2014-02-04
Booting my PC from Lubuntu 13.10 LiveUSB and using GParted:

Guess what?

GParted couldn't create 'new partition table' to this USB!

Stubborn USB, ha?

---

### Post by sudodus on 2014-02-04
Having a backup you can try some method to recover the drive itself.

1. Wipe the first megabyte. 

A guru like you would probably use ***dd*** to wipe the first megabyte. Otherwise I would recommend [mkusb]("http://ubuntuforums.org/showthread.php?t=1958073") for that task.

2. and after that create a new partition table with ***gparted***.

Device -- Create partition table

And then continue as usual ... for example make a partition with FAT32.

-o-

If this does not work, I'm afraid that the pendrive is bricked (maybe swapped as a practical joke or simply theft as indicated by Bucky Ball).

---

### Post by dragonfly41 on 2014-02-04
A few points to check ...

Your device is unmounted

You cannot create a new partition table if you haven't first created a partition  ... see below ...

[http://askubuntu.com/questions/12284/why-cant-i-create-a-partition-table-on-my-usb-flash-drive-using-gparted](http://askubuntu.com/questions/12284/why-cant-i-create-a-partition-table-on-my-usb-flash-drive-using-gparted)

...

---

### Post by amjjawad on 2014-02-04
> **dragonfly41 said:**
> A few points to check ...

Your device is unmounted

You cannot create a new partition table if you haven't first created a partition  ... see below ...

[http://askubuntu.com/questions/12284/why-cant-i-create-a-partition-table-on-my-usb-flash-drive-using-gparted](http://askubuntu.com/questions/12284/why-cant-i-create-a-partition-table-on-my-usb-flash-drive-using-gparted)

...

I am sorry my friend but you're wrong this time.

I've been using GParted for 3 years, daily, many many times every day. You can NOT create a partition UNLESS you have a partition table. Otherwise, my 3 years with GParted was a waste of time :)

---

### Post by amjjawad on 2014-02-04
> **sudodus said:**
> Having a backup you can try some method to recover the drive itself.

1. Wipe the first megabyte. 

A guru like you would probably use ***dd*** to wipe the first megabyte. Otherwise I would recommend [mkusb]("http://ubuntuforums.org/showthread.php?t=1958073") for that task.

2. and after that create a new partition table with ***gparted***.

Device -- Create partition table

And then continue as usual ... for example make a partition with FAT32.

-o-

If this does not work, I'm afraid that the pendrive is bricked (maybe swapped as a practical joke or simply theft as indicated by Bucky Ball).

I am not a GURU yet ;) but thanks for that :)

That was in mind while I was writing my last post. There is nothing left in my hand to try rather than use 'dd' and see what is the big puzzle behind his weird USB.

Even if someone was doing a silly bad joke, why it can't be formatted neither with Windows nor Linux?

---

### Post by amjjawad on 2014-02-04
> **dragonfly41 said:**
> A few points to check ...

Your device is unmounted

You cannot create a new partition table if you haven't first created a partition  ... see below ...

[http://askubuntu.com/questions/12284/why-cant-i-create-a-partition-table-on-my-usb-flash-drive-using-gparted](http://askubuntu.com/questions/12284/why-cant-i-create-a-partition-table-on-my-usb-flash-drive-using-gparted)

...

Check the attached screenshot on this post:
[http://ubuntuforums.org/showthread.php?t=2202967&p=12916280#post12916280](http://ubuntuforums.org/showthread.php?t=2202967&p=12916280#post12916280)

When I try to create new partition table, nothing happens. It will still show that red icon and as I explained earlier, without a partition table, you can NOT create any partition. Try it if you don't believe me :D

Edit:
That is why, the only possible way to get around this puzzle is to try 'dd' :)

---

### Post by sudodus on 2014-02-04
Sometimes there are some confusing data in the early part of the drive space and overwriting the first megabyte with zeros helps when gparted is to make a new partition table.

The drive might be electronically damaged or the tiny arm on-board chip might be programmed by a virus. Normal mortals can't do anything about such things.

---

### Post by dragonfly41 on 2014-02-04
Sounds like a lost cause ...

One last thought is to convince the school teacher to run testdisk on the school's host PC to see if any deleted files (belonging to your neighbour's daughter) can be recovered.   Or just look in school PC windows Trash bin where any deleted files owned by her might still be there.

Also suggest to teacher that students use personal [COLOR=blue]dropbox accounts[/COLOR] to sync their school projects files between school and home.   There are good educational offers by dropbox if you have an .edu mail account.

Avoiding flash devices for important files and carriers of viruses.

Good luck.

[p.s.] Download the windows version of testdisk from here ... [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Portaro on 2014-02-04
Puff at this momment we dont know if there are data or not in sdb ,

maybe try ddrescue is the only idea I can find on google->

[http://www.forensicswiki.org/wiki/Ddrescue](http://www.forensicswiki.org/wiki/Ddrescue)

---

### Post by varunendra on 2014-02-04
Windows not being able to format it, Gparted not being able to create a Partition table, and all the story in-between.... .... tells me that the drive is physically gone, end of story and any hopes with it.

That being said, there used to be times when I had some beliefs based on some previous knowledge and with new experience and knowledge, I was (thankfully) proven wrong. I maybe wrong this time as well.

But if not, this is a typical case of a flash chip reaching its eventual, inevitable end of life. The regular wear & tear, possibly combined with an accident or mishandling has turned the tiny 'holes' (that hold the electrons or 'Bits') into craters.

While a virus activity or similar things can be capable of erasing a partition table (not essential as The Cog already pointed out) and 'Whole' data on a drive (although 'whole data' part is very rare), it is almost impossible for a logical process to cause something that can prevent a fresh Partition Table from being created, **unless the process (usual suspect being a virus activity) is capable of doing physical damage** to the storage area or the circuitry - height of programming efficiency.

Apparently, either the storage area (the flash chip) has been physically damaged, or the underlying circuitry has lost its control over it (dry sold, damaged parts, whatever) thus not being able to properly read or write to it. In the former case, nothing can be done except what you have already tried (the dd image is the most promising outcome of all attempts so far, keep it safe). The latter one is just a theoretical possibility and I don't have any practical examples, but it *may be* possible to fix (like hot air to fix dry solds, or moving the chip to an identical working circuit module).

The dd command being successful at taking the image is a strong indication that the problem lies in the 'writing mechanism' of the key, the reading part is somewhat okay. Since you already have the dd image, you can safely try to zero out the drive using another dd command (assuming /dev/sdb is the flash drive) -
```
sudo dd if=/dev/zero of=/dev/sdb
```
..which I'm quite sure will fail, confirming the possibility that writing is not possible anymore on the drive.

But be aware that if the above succeeded (to my surprise), the whole data (if any is left anywhere) on the drive will be permanently lost. Not a problem since you already have the dd image. At least the drive will become usable again.

Lastly, moving the chip to an identical working circuit module (to ensure that the circuit's read/write mechanism is good) is probably your best hope (best, not much). If even that fails, it would mean the flash chip has succumbed to internal physical damage and is as good as dead.

**PS:**
That the data on the computer was also lost is a little mystery for me too. It, if true, makes me think that the damage was possibly caused by the computer itself - some problem in its power supply, I/O chip or related parts. Motherboards and logic cards of Hard Disks have physical protection systems in place, flash drives don't have any. So while the computer might be working again, the flash is trash now.

**PPS:**
Just noticed sudodus has already said it all in a nutshell. :)

---

### Post by amjjawad on 2014-02-05
```
lubuntu@lubuntu:~$ sudo dd if=/dev/zero of=/dev/sdc
dd: writing to &#8216;/dev/sdc&#8217;: No space left on device
4091905+0 records in
4091904+0 records out
2095054848 bytes (2.1 GB) copied, 392.405 s, 5.3 MB/s


```

```
lubuntu@lubuntu:~$ sudo shred -vzn 0 /dev/sdc
shred: /dev/sdc: pass 1/1 (000000)...
shred: /dev/sdc: pass 1/1 (000000)...146MiB/2.0GiB 7%
shred: /dev/sdc: pass 1/1 (000000)...225MiB/2.0GiB 11%
shred: /dev/sdc: pass 1/1 (000000)...311MiB/2.0GiB 15%
shred: /dev/sdc: pass 1/1 (000000)...395MiB/2.0GiB 19%
shred: /dev/sdc: pass 1/1 (000000)...480MiB/2.0GiB 24%
shred: /dev/sdc: pass 1/1 (000000)...564MiB/2.0GiB 28%
shred: /dev/sdc: pass 1/1 (000000)...647MiB/2.0GiB 32%
shred: /dev/sdc: pass 1/1 (000000)...732MiB/2.0GiB 36%
shred: /dev/sdc: pass 1/1 (000000)...817MiB/2.0GiB 40%
shred: /dev/sdc: pass 1/1 (000000)...898MiB/2.0GiB 44%
shred: /dev/sdc: pass 1/1 (000000)...985MiB/2.0GiB 49%
shred: /dev/sdc: pass 1/1 (000000)...1.0GiB/2.0GiB 53%
shred: /dev/sdc: pass 1/1 (000000)...1.1GiB/2.0GiB 57%
shred: /dev/sdc: pass 1/1 (000000)...1.2GiB/2.0GiB 61%
shred: /dev/sdc: pass 1/1 (000000)...1.3GiB/2.0GiB 66%
shred: /dev/sdc: pass 1/1 (000000)...1.4GiB/2.0GiB 71%
shred: /dev/sdc: pass 1/1 (000000)...1.5GiB/2.0GiB 76%
shred: /dev/sdc: pass 1/1 (000000)...1.6GiB/2.0GiB 82%
shred: /dev/sdc: pass 1/1 (000000)...1.7GiB/2.0GiB 87%
shred: /dev/sdc: pass 1/1 (000000)...1.8GiB/2.0GiB 92%
shred: /dev/sdc: pass 1/1 (000000)...1.9GiB/2.0GiB 97%
shred: /dev/sdc: pass 1/1 (000000)...2.0GiB/2.0GiB 100%


```
$ sudo fdisk -l

```
Disk /dev/sdc: 2095 MB, 2095054848 bytes
65 heads, 62 sectors/track, 1015 cylinders, total 4091904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c82da1e

Disk /dev/sdc doesn't contain a valid partition table


```

Still, GParted can't create any kind of Partition table (I have tried all the listed options).

---

### Post by amjjawad on 2014-02-05
```

lubuntu@lubuntu:~$ sudo dmesg 


[  962.267539] sd 8:0:0:0: [sdc] 4091904 512-byte logical blocks: (2.09 GB/1.95 GiB)
[  962.270821] sd 8:0:0:0: [sdc] Write Protect is off
[  962.270838] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[  962.272185] sd 8:0:0:0: [sdc] No Caching mode page found
[  962.272199] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  962.280466] sd 8:0:0:0: [sdc] No Caching mode page found
[  962.280481] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  962.282334]  sdc: unknown partition table
[  962.285082] sd 8:0:0:0: [sdc] No Caching mode page found
[  962.285092] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  962.285099] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 1075.508515] ieee80211 phy0: rt61pci_txdone: Warning - TX status report missed for entry 21
[ 1218.206610] usb 1-7: USB disconnect, device number 6
[ 1759.092063] usb 1-7: new high-speed USB device number 7 using ehci-pci
[ 1759.224775] usb 1-7: New USB device found, idVendor=2001, idProduct=2008
[ 1759.224782] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1759.224786] usb 1-7: Product: USB2.0 FlashDisk
[ 1759.224789] usb 1-7: Manufacturer: Ipgoal  
[ 1759.225257] usb-storage 1-7:1.0: USB Mass Storage device detected
[ 1759.225992] scsi9 : usb-storage 1-7:1.0
[ 1760.224705] scsi 9:0:0:0: Direct-Access     Generic  Flash Disk 2.0   2.20 PQ: 0 ANSI: 2
[ 1760.225271] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 1760.228367] sd 9:0:0:0: [sdc] 4091904 512-byte logical blocks: (2.09 GB/1.95 GiB)
[ 1760.229099] sd 9:0:0:0: [sdc] Write Protect is off
[ 1760.229112] sd 9:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 1760.229857] sd 9:0:0:0: [sdc] No Caching mode page found
[ 1760.229872] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 1760.242122] sd 9:0:0:0: [sdc] No Caching mode page found
[ 1760.242139] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 1760.244239]  sdc: unknown partition table
[ 1760.248978] sd 9:0:0:0: [sdc] No Caching mode page found
[ 1760.248992] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 1760.249002] sd 9:0:0:0: [sdc] Attached SCSI removable disk


```


```
lubuntu@lubuntu:~$ ls /dev
autofs           loop0               ram0    sda3      tty17  tty38  tty59      ttyS20   vcs2
block            loop1               ram1    sdb       tty18  tty39  tty6       ttyS21   vcs3
bsg              loop2               ram10   sdb1      tty19  tty4   tty60      ttyS22   vcs4
btrfs-control    loop3               ram11   sdc       tty2   tty40  tty61      ttyS23   vcs5
bus              loop4               ram12   sg0       tty20  tty41  tty62      ttyS24   vcs6
char             loop5               ram13   sg1       tty21  tty42  tty63      ttyS25   vcs7
console          loop6               ram14   sg2       tty22  tty43  tty7       ttyS26   vcsa
core             loop7               ram15   shm       tty23  tty44  tty8       ttyS27   vcsa1
cpu              loop-control        ram2    snapshot  tty24  tty45  tty9       ttyS28   vcsa2
cpu_dma_latency  lp0                 ram3    snd       tty25  tty46  ttyprintk  ttyS29   vcsa3
disk             mapper              ram4    stderr    tty26  tty47  ttyS0      ttyS3    vcsa4
dri              mcelog              ram5    stdin     tty27  tty48  ttyS1      ttyS30   vcsa5
ecryptfs         mem                 ram6    stdout    tty28  tty49  ttyS10     ttyS31   vcsa6
fb0              net                 ram7    tty       tty29  tty5   ttyS11     ttyS4    vcsa7
fd               network_latency     ram8    tty0      tty3   tty50  ttyS12     ttyS5    vga_arbiter
fd0              network_throughput  ram9    tty1      tty30  tty51  ttyS13     ttyS6    vhost-net
full             null                random  tty10     tty31  tty52  ttyS14     ttyS7    zero
fuse             parport0            rfkill  tty11     tty32  tty53  ttyS15     ttyS8    zram0
hidraw0          port                rtc     tty12     tty33  tty54  ttyS16     ttyS9    zram1
hpet             ppp                 rtc0    tty13     tty34  tty55  ttyS17     uinput
input            psaux               sda     tty14     tty35  tty56  ttyS18     urandom
kmsg             ptmx                sda1    tty15     tty36  tty57  ttyS19     vcs
log              pts                 sda2    tty16     tty37  tty58  ttyS2      vcs1


```

```
lubuntu@lubuntu:~$ sudo fdisk /dev/sdc
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x6a5610a0.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): o
Building a new DOS disklabel with disk identifier 0x51b26c44.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): p

Disk /dev/sdc: 2095 MB, 2095054848 bytes
65 heads, 62 sectors/track, 1015 cylinders, total 4091904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51b26c44

   Device Boot      Start         End      Blocks   Id  System




```

---

### Post by Bucky Ball on 2014-02-05
Hmmm. And? You have the option to write the new partition table with 'w'. So what are you now attempting to do?

---

### Post by amjjawad on 2014-02-05
> **Bucky Ball said:**
> Hmmm. And? You have the option to write the new partition table with 'w'. So what are you now attempting to do?

Have tried all the options and nothing has changed.

---

### Post by sudodus on 2014-02-05
It seems you can write with dd :-)

So I suggest that you try cloning an iso file, for example

[http://linuxvillage.org/Downloads/ISOS/LinuxVillage/Ubuntu/bento-to-tori-alpha1-i386-2012.04.4.iso](http://linuxvillage.org/Downloads/ISOS/LinuxVillage/Ubuntu/bento-to-tori-alpha1-i386-2012.04.4.iso)

```
sudo dd if=bento-to-tori-alpha1-i386-2012.04.4.iso of=/dev/sdx bs=4096
```

where x was c last time so of=/dev/sdc

-o-

or safer (for non-gurus) with mkusb according to [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

```
sudo ./mkusb bento-to-tori-alpha1-i386-2012.04.4.iso
``` if mkusb is in the current directory.

-o-

Edit: Then you will soon find if dd is really writing something that can be read afterwards. Maybe it only pretends to write or maybe it is the reading capability that is damaged.

Did you get a USB boot drive or not? Can you mount it and read some file?

---

### Post by Bucky Ball on 2014-02-05
Here:

```
lubuntu@lubuntu:~$ sudo fdisk /dev/sdc
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x6a5610a0.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): o
Building a new DOS disklabel with disk identifier 0x51b26c44.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): p

Disk /dev/sdc: 2095 MB, 2095054848 bytes
65 heads, 62 sectors/track, 1015 cylinders, total 4091904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51b26c44
```

I don't see you've hit 'w' anywhere to write the partition table. You use 'o' and 'p', but not 'w', which actually writes it. :-k

Fixed a machine using this very method a couple of weeks ago.

---

### Post by amjjawad on 2014-02-05
> **Bucky Ball said:**
> Here:

```
lubuntu@lubuntu:~$ sudo fdisk /dev/sdc
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x6a5610a0.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): o
Building a new DOS disklabel with disk identifier 0x51b26c44.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): p

Disk /dev/sdc: 2095 MB, 2095054848 bytes
65 heads, 62 sectors/track, 1015 cylinders, total 4091904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51b26c44
```

I don't see you've hit 'w' anywhere to write the partition table. You use 'o' and 'p', but not 'w', which actually writes it. :-k

Fixed a machine using this very method a couple of weeks ago.

I did try that. It didn't work.
I didn't post it because that didn't change anything. However, just for you to see:

```
lubuntu@lubuntu:~$ sudo fdisk /dev/sdd
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x7b6e19e3.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

```

There is NO partition table and as long as there is no partition table, there is nothing can be done.

I used Disks (Menu > Accessories > Disks) to restore the image I created earlier with 'dd' command. The process seemed to working fine. However, still nothing at all.

---

### Post by amjjawad on 2014-02-05
[ATTACH=CONFIG]250109[/ATTACH]

I just hope I didn't damage my new USB drive when I tried to restore the image I created earlier for the damaged USB drive.

By the way, the chances that the USB has been replaced with another one is zero. There is a sticker on the USB from both sides, one has a horse and the other has the girl last name so there is no way it got replaced. She would have known that.

---

### Post by sudodus on 2014-02-05
Try according to post #51

It ***might*** work, but at least you should find out if the problem is ***reading*** from the device.

---

### Post by amjjawad on 2014-02-05
> **sudodus said:**
> Try according to post #51

It ***might*** work, but at least you should find out if the problem is ***reading*** from the device.

What is the difference between your suggestion and between restoring an image using Disk (Menu > Accessories > Disks - Lubuntu LiveUSB) ?

Isn't what you're suggesting the same? 

If there is a difference, I'd do that :)

---

### Post by sudodus on 2014-02-05
What program is behind the menu item Disk?

---

### Post by amjjawad on 2014-02-05
> **sudodus said:**
> What program is behind the menu item Disk?

gnome-disks

---

### Post by sudodus on 2014-02-05
I don't know gnome-disks well enough. If the program that ultimately is performing the task is ***dd***, then it is the same, otherwise it is something else, more or less similar, but not exactly the same thing.

---

### Post by dragonfly41 on 2014-02-05
I'm puzzled. Why didn't you go to the "source of the Nile" .. the school PC .. as I suggested in post#44?

The longer you wait the less chance of original data recovery from that school PC.  Probably already gone by now.

---

### Post by amjjawad on 2014-02-05
> **dragonfly41 said:**
> I'm puzzled. Why didn't you go to the "source of the Nile" .. the school PC .. as I suggested in post#44?

The longer you wait the less chance of original data recovery from that school PC.  Probably already gone by now.

It appears that I have forgotten to add this, sorry:

The Girl:
> Every student has a file and it deleted my files not my teachers because he didnt plug the usb in his account. We all have log in usernames in our school. I have asked the school IT guy if he can get the backups from 2weeks ago.. he yet needs to get back to me


Me:
> What I want to understand is this:




[Did the USB Flash Drive of yours, when it was inserted to the PC at school, the USB has deleted the files on the Computer once you tried to access the USB] ??!!






The Girl:
> 
Yes.

I had a folder called ICT on my school area and that got wiped.. not my other folders and so I think because it was the same files as on the usb that it came from that? Does that make sense

I dont know! I cant imagine a human doing that.. I always carry my USB around school.. its not impossible that someone did it but I dont know who would..   And yes I understand your last question but I dont know.. I just dont know sorry 



I can't find where is the part when she said she looked at her recycle bin but she couldn't find anything. I am sure I have seen that some where ...

---

### Post by amjjawad on 2014-02-05
> **sudodus said:**
> I don't know gnome-disks well enough. If the program that ultimately is performing the task is ***dd***, then it is the same, otherwise it is something else, more or less similar, but not exactly the same thing.

I don't know either.

This is the situation that we have:

USB Drive 2GB
There is no Partition Table.
The backup image that was created earlier wasn't helpful - see: [http://ubuntuforums.org/showthread.php?t=2202967&page=6&p=12920485#post12920485](http://ubuntuforums.org/showthread.php?t=2202967&page=6&p=12920485#post12920485)
While it seems possible to 'write' on that USB, it seems impossible to read from it.

I think one of the earlier suggestions that the USB has already dead, at least 'reading' wise.

Now, the trick is, how to retrieve some files from the image, in case there are any!

Backup imaged created as per: [http://ubuntuforums.org/showthread.php?t=2202967&page=2&p=12917401#post12917401](http://ubuntuforums.org/showthread.php?t=2202967&page=2&p=12917401#post12917401)

---

### Post by sudodus on 2014-02-05
1. As a final attempt to revive the USB drive, I suggest that you try my suggestion from post #51.

2. It is possible to loop mount that image, but I think it is easier to flash it to a working pendrive, and then try ***PhotoRec*** on that drive.

Use the reversed dd command (from the image to the pendrive)

```
sudo dd if=stick.img of=/dev/sdx
```

Where x is to be changed to whatever is the device letter for the working pendrive.

---

### Post by amjjawad on 2014-02-05
> **sudodus said:**
> 1. As a final attempt to revive the USB drive, I suggest that you try my suggestion from post #51.
Can't refuse a request from a good friend :D

> 2. It is possible to loop mount that image, but I think it is easier to flash it to a working pendrive, and then try ***PhotoRec*** on that drive.

Use the reversed dd command (from the image to the pendrive)

```
sudo dd if=stick.img of=/dev/sdx
```

Where x is to be changed to whatever is the device letter for the working pendrive.

Are we talking about the same nasty stubborn USB drive? or you mean try to use different one? I used different one, I didn't work.

---

### Post by sudodus on 2014-02-05
> **amjjawad said:**
> Can't refuse a request from a good friend :D

:-D> 

Are we talking about the same nasty stubborn USB drive? or you mean try to use different one? I used different one, I didn't work.

Yes, I meant a different one.

---

### Post by amjjawad on 2014-02-06
I did as advised in post #51

```
$ sudo dd if=slitaz-4.0.iso of=/dev/sdb bs=4096
8891+1 records in
8891+1 records out
36419584 bytes (36 MB) copied, 2.30481 s, 15.8 MB/s

```

SliTaz has small ISO size so I used it ;)

As far as I can tell, nothing whatsoever has changed.

---

### Post by amjjawad on 2014-02-06
> **sudodus said:**
> 1. As a final attempt to revive the USB drive, I suggest that you try my suggestion from post #51.

Done but that didn't change anything - see my previous post.

> 2. It is possible to loop mount that image, but I think it is easier to flash it to a working pendrive, and then try ***PhotoRec*** on that drive.

Use the reversed dd command (from the image to the pendrive)

```
sudo dd if=stick.img of=/dev/sdx
```

Where x is to be changed to whatever is the device letter for the working pendrive.

Have done that and the result was a USB Drive with unformatted area (back color with GParted) and there was no data whatsoever. 
I don't have 2GB Flash Drive so I used one with 16GB.

---

### Post by sudodus on 2014-02-06
I think you have done all what can be expected and a lot more to recover this pendrive. I think it is time to tell the girl that it is dead :-(

---

### Post by amjjawad on 2014-02-06
[ATTACH=CONFIG]250146[/ATTACH]

Just tried yet again:

```
$ sudo dd if=stick.img of=/dev/sdb
4091904+0 records in
4091904+0 records out
2095054848 bytes (2.1 GB) copied, 748.703 s, 2.8 MB/s


```

---

### Post by amjjawad on 2014-02-06
> **sudodus said:**
> I think you have done all what can be expected and a lot more to recover this pendrive. 
But we should always expect the unexpected :D

> I think it is time to tell the girl that it is dead :-(
No. I shall never tell her that. You know why? because I have found the files :D :D :D

They are calling me the wizard over here and the doctor so how can I just give up and tell them the patient is dead? never :D

I have gone the extra miles because I don't want just to convert the girl to Linux, in fact, I am planning to convert her whole school :D

---

### Post by dragonfly41 on 2014-02-06
> in fact, I am planning to convert her whole school

so from this .. you had a hidden agenda throughout this thread?

---

### Post by amjjawad on 2014-02-06
```
PhotoRec 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 16 GB / 14 GiB (RO) - Imation ImationFlashDriv
     Partition                  Start        End    Size in sectors
   P Unknown                  0   0  1 15262  19 32   31257216


14458 files saved in /home/xxxxx/recup_dir directory.
Recovery completed.

You are welcome to donate to support further development and encouragement
http://www.cgsecurity.org/wiki/Donation



[ Quit ]


```

:D

---

### Post by amjjawad on 2014-02-06
> **dragonfly41 said:**
> so from this .. you had a hidden agenda throughout this thread?

Hidden agenda? do I look like a Microsoft guy? :P :D

Nuh, but the password that always work is "give up, you have tried all what you could" and it always work :D

What I was trying to say is: when Linux is able to restore the lost files, that is a strong enough reason to covert people ;)

---

### Post by amjjawad on 2014-02-06
Wait, there is something wrong :(

The files that I found are near 12GB in size while the USB that the girl gave it to me is just 2GB in size.

I have used a 16GB USB Flash Drive that has been used 'only once' so far. 

I will not give up.

I will use dd and shred to clear the USB that I have and re-try again.

Is there any other way to read from 'stick.img' without writing that to any drive?!

---

### Post by varunendra on 2014-02-06
> **amjjawad said:**
> Is there any other way to read from 'stick.img' without writing that to any drive?!

You can work with that image directly in testdisk/photorec -
```
sudo photorec <path to the image>
```

Or, you can try to loop mount it to some place (which will almost certainly fail since there would be no filesystem detected on the image) -
```
sudo mount -o loop <path to the image> <directory where you want to mount it>
```

---

### Post by amjjawad on 2014-02-06
> **varunendra said:**
> You can work with that image directly in testdisk/photorec -
```
sudo photorec <path to the image>
```

Or, you can try to loop mount it to some place (which will almost certainly fail since there would be no filesystem detected on the image) -
```
sudo mount -o loop <path to the image> <directory where you want to mount it>
```

Hi and thanks for posting,

```
$ sudo photorec stick.img
```

```
PhotoRec 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk stick.img - 2095 MB / 1998 MiB (RO)
     Partition                  Start        End    Size in sectors
   P Unknown                  0   0  1   254 180 54    4091904


0 files saved in /home/zxzxz/recup_dir directory.
Recovery completed.


```

---

### Post by Bucky Ball on 2014-02-06
Jumping at shadows? Good luck ... but actually doesn't seem like you're getting anywhere in the end ...

There's more inspiration for you! ;)

---

### Post by amjjawad on 2014-02-08
We didn't fail, we just found 1000 ways that didn't work :)

Just gave the girl her laptop and she was super happy with Ubuntu GNOME and so excited. I explained to her some basic stuff myself and as always, she can, just like any other neighbour, to reach me either in person or by phone or facebook. We're 5-10mins away anyway :)

I explained to her about her USB and she totally understood that and thanked me for the effort. The girl and her dad were just puzzled how the USB deleted the files on the Computer Machine and her machine as well.

I'd like to thank each and everyone who helped and it is good experience to learn from, really. [This project to convert my neighbourhood]("http://amjjawad.blogspot.com/2014/01/2014-report-project-convert-my.html") (which is the real life side of [StartUbuntu]("https://wiki.ubuntu.com/StartUbuntu")) is helping me a lot to learn new stuff. With each neighbour, it is a new story and experience. What I have learned in 3 years, I am learning new stuff in 3 months. Nothing better and faster than a real life experience, specially when you do it yourself.

Looking forward for a new challenge now ;)

Thank you once more!

---

### Post by col48 on 2014-02-08
A fascinating story of persistance rewarded - well done!

Why not summarise the problem and its solution in a wrap-up post, and mark as solved?

---

### Post by amjjawad on 2014-02-08
> **col48 said:**
> A fascinating story of persistance rewarded - well done!

Why not summarise the problem and its solution in a wrap-up post, and mark as solved?

Thank you for your words and yes, that is a good idea which I was thinking to do it on my blog and add the link here or maybe just here but I have no time at the moment to do so. This thread is not messy, it is easy to follow up :)

I can't mark it as 'solved' because the issue is not solved unless the moderators have different opinion ;)

Thank you!

---

### Post by Bucky Ball on 2014-02-08
Well, the support request was to retrieve the USB, you got a heap of advice and tried everything possible and the quest is complete and resolved rather than solved. The thread has gone about as far as it's going to and will venture off-topic if it goes any further.

I think the wrap up post has been posted, but, in the absence of a 'resolved' option, please mark as solved. Post a new thread for any further adventures. ;)

Good job and good luck with your Ubuntu crusade.

---

### Post by amjjawad on 2014-02-08
> **Bucky Ball said:**
> Well, the support request was to retrieve the USB, you got a heap of advice and tried everything possible and the quest is complete and resolved rather than solved. The thread has gone about as far as it's going to and will venture off-topic if it goes any further.

I think the wrap up post has been posted, but, in the absence of a 'resolved' option, please mark as solved. Post a new thread for any further adventures. ;)


Hi and thanks for posting :)

If you think I should mark this as 'Solved', then consider it done ;)

> Good job and good luck with your Ubuntu crusade.
Thank you, appreciate that :)

Edit:
I posted about this story on [by blog]("http://amjjawad.blogspot.com/2014/02/howto-saveretrieve-lost-data-from-usb.html").

Special thanks, once more, for each and everyone who helped. You guys are the best, period. No doubt about it :D

---

