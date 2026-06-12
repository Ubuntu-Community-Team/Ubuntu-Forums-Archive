---
title: "encrypted partition issues"
date: 2013-01-26
forum: General Help
---

### Post by n00ne on 2013-01-26
about two weeks ago I've created an encrypted volume on one of my hard drives using - 
```
sudo cryptsetup -v -y luksFormat /dev/sdb1
```
I mounted and formated the drive and used it with no problems for the past
two weeks until last night I had to restart my computer.
after the restart I tried to use luksOpen to open the volume
but I it was not recognized as an luks device -
```

sudo cryptsetup luksOpen /dev/sdb1 secure
Device /dev/sdb1 is not a valid LUKS device.

```

I tried looking at the partition header and it seemed to be coruppted
```
 
sudo hd /dev/sdb1 | head -n 40
00000000  ef 2d a4 53 85 e9 0e 35  b7 d7 f7 6b 8e 4a 46 2a  |.-.S...5...k.JF*|
00000010  ee 3c 68 72 50 2e b8 e7  a1 6e 4e 1c 0b 58 48 91  |.<hrP....nN..XH.|
00000020  9b 44 1f 96 84 a2 a7 f9  f0 bd 50 e6 82 d8 6c 93  |.D........P...l.|
00000030  83 49 4e b5 21 07 b7 24  96 5b 64 0d 6b 16 4d e2  |.IN.!..$.[d.k.M.|
00000040  1f 3b 87 29 c2 c9 81 be  1f c1 78 8b 7e be 06 5b  |.;.)......x.~..[|
00000050  ae a7 44 59 2e 9c 23 9b  e5 27 a3 66 8b 19 e4 b4  |..DY..#..'.f....|
00000060  59 06 a1 e2 28 b4 37 b9  e7 83 b6 f1 e7 fa f2 de  |Y...(.7.........|
00000070  8c 88 c4 99 48 82 c1 72  77 58 27 32 28 90 6c 52  |....H..rwX'2(.lR|

```

Definitely doesn't look like the expected luks header.

stupidly I haven't backed up my luks headers yet so I had no choice but reformat the drive (I had abou 0.5TB of data on it its going to be annoying to recopy all the files back but luckily they are all backed up).

I also backed my headers but I was wondering what I was doing wrong and how can I avoid from this happening again.
I mean even if restoring the headers would have been working it isn't a process I want to do after each restart.

10x

---

