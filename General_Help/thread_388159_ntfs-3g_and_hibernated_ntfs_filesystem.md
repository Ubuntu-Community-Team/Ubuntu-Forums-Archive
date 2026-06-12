---
title: "ntfs-3g and hibernated ntfs filesystem"
date: 2007-03-19
forum: General Help
---

### Post by guru369 on 2007-03-19
Hi.

I have installed ntfs-config to provide write support for my /dev/sda1 partition.
However, It for some reason detect that the partition is hibernated which is not true.

I have rebooted into windows a couple of time and still it wont allow me to mount the partition.

I also tried using the force flag.

See:
```

~$ sudo ntfs-3g /dev/sda1 /media/sda1/ -o force
Windows is hibernated, won't mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume Windows and turned it 
off properly, so mounting could be done safely.

```

Thanks in advance.
Dekel

---

### Post by szaka on 2007-03-19
Hi.

The ntfs-3g check seems to be too strict. Please mount the partition read-only and send the output of the below 'hexdump' command, so we could fix this problem.

```

sudo ntfs-3g /dev/sda1 /media/sda1/ -o force,ro
hexdump -C /media/sda1/hiberfil.sys | head -20

```

Thanks!

---

### Post by guru369 on 2007-03-19
There you go:
```

dekela@dekela-laptop:/$ hexdump -C /media/sda1/hiberfil.sys | head -20
00000000  f4 70 35 e8 48 7f f9 15  ff ac 4b 10 3b e9 ef 42  |.p5.H.....K.;..B|
*
00001000  00 ba 5d f1 c3 01 00 fb  49 00 d6 28 02 92 ff 02  |..].....I..(....|
00001010  bc 91 00 01 8e 2d 82 1a  85 5e 0e 00 0f 89 90 01  |.....-...^......|
00001020  84 c3 01 cc 00 bb 01 d2  05 b6 7a 98 34 00 f4 35  |..........z.4..5|
00001030  a8 07 e3 86 01 11 80 a3  02 a9 65 ab 08 8d 12 00  |..........e.....|
00001040  20 df ea 01 d4 06 11 00  82 e6 00 01 91 f7 01 fe  | ...............|
00001050  21 c9 c5 00 01 f5 17 c3  d9 01 ee 02 00 1b 96 e7  |!...............|
00001060  01 96 34 bc 2e 00 cd 12  a9 13 9c 08 88 01 00 ab  |..4.............|
00001070  1e e3 2f ab 1e fe 21 00  d8 0f b6 10 25 9e 01 30  |../...!.....%..0|
00001080  00 c1 04 97 37 22 22 8e  d4 00 02 82 85 01 d7 18  |....7"".........|
00001090  fa e0 00 01 e0 67 f3 0a  d6 33 0f 00 9a 4d ea 01  |.....g...3...M..|
000010a0  82 5c ea 01 01 75 00 9f  57 0d c0 a7 02 0d 00 dc  |.\...u..W.......|
000010b0  10 02 e7 06 f6 11 0d 00  81 1f c0 09 8e 67 e9 01  |.............g..|
000010c0  00 91 01 7b eb 03 7f d1  01 00 7d 40 7f 40 7b dc  |...{......}@.@{.|
000010d0  02 7f 00 42 7d d0 01 7b  3e 7d e7 11 00 01 7b ec  |...B}..{>}....{.|
000010e0  03 90 00 40 7f df 46 02  f0 01 80 01 cf 01 7d 20  |...@..F.......} |
000010f0  00 40 04 7b 3e 10 00 cd  01 7d e9 02 26 7f e1 00  |.@.{>....}..&...|
00001100  81 03 7d d8 e1 02 3e 7f  24 f9 02 00 03 de 01 20  |..}...>.$...... |
00001110  04 7d 40 40 7b dd 02 7b  eb 02 d2 01 cf 02 01 01  |.}@@{..{........|
dekela@dekela-laptop:/$ 

```

---

### Post by szaka on 2007-03-19
Hmm, what kind of Windows do you use? XP, Vista, service packs, etc. Anything special? Laptop, desktop, etc? This is a highly unusual hiberfil.sys ...

---

### Post by guru369 on 2007-03-20
This is A laptop T60 (Lenovo) Running Windows XP SP2.
What is unusual about it?

Dekel

---

### Post by szaka on 2007-03-20
If the hiberfil.sys file start with 'hibr' then it's surely hibernated. If the first 4096 bytes are zero then it's not hibernated. Your first 4096 bytes are zero except the first 16 ones but it doesn't start with 'hibr'. Nobody has ever reported such scenario in the last four years.

What can we do? Reverse engineer the Windows code or collect more info and experiment a bit. No time for the former, but the second one is feasible. You could save 5-6 such outputs after you used Windows and booted Linux then send all of them. But it's enough the first two lines, e.g. 'head -2'. Maybe it's always the same. Maybe it's random.

Meanwhile I'll also do more research in this topic.

---

### Post by sublette131 on 2007-09-11
Thanks for posting this, I also get the same message.  Here's the output of those commands on my laptop (coincedentially also a Lenovo T60 - but with windows 2000).

00000000  6d ef 62 c8 df e8 c2 c8  6d ef 62 c8 df e8 c2 c8  |m.b.....m.b.....|
*
00001000  6b d0 03 00 ec bb 02 00  ed 7f 00 00 ee 62 01 00  |k............b..|
00001010  af 66 01 00 30 de 02 00  31 7b 03 00 f2 36 01 00  |.f..0...1{...6..|
00001020  f3 d0 03 00 74 bd 02 00  75 9a 03 00 b6 68 00 00  |....t...u....h..|
00001030  b7 f1 03 00 f8 65 02 00  b9 d1 03 00 fa 14 03 00  |.....e..........|
00001040  7b d5 02 00 bc b1 02 00  bd 1e 02 00 be 51 03 00  |{............Q..|
00001050  ff 2d 03 00 80 74 02 00  41 43 03 00 42 cf 02 00  |.-...t..AC..B...|
00001060  c3 d6 02 00 04 f2 03 00  05 76 03 00 c6 d4 02 00  |.........v......|
00001070  87 d2 02 00 48 2d 01 00  49 97 03 00 ca bc 03 00  |....H-..I.......|
00001080  0b 64 02 00 cc a2 03 00  cd aa 03 00 0e cd 03 00  |.d..............|
00001090  4f c3 02 00 50 00 00 00  91 4f 03 00 52 d2 03 00  |O...P....O..R...|
000010a0  d3 80 03 00 14 6d 03 00  95 68 02 00 56 d1 03 00  |.....m...h..V...|
000010b0  d7 5b 03 00 58 df 02 00  99 d7 02 00 da 44 02 00  |.[..X........D..|
000010c0  9b c5 03 00 dc ce 02 00  9d b7 02 00 5e e0 02 00  |............^...|
000010d0  5f bf 03 00 a0 8f 03 00  e1 3a 02 00 a2 74 02 00  |_........:...t..|
000010e0  e3 44 03 00 24 02 00 00  e5 54 03 00 a6 ac 02 00  |.D..$....T......|
000010f0  27 9a 03 00 a8 51 03 00  e9 38 02 00 aa 00 03 00  |'....Q...8......|
00001100  ab 2b 03 00 2c f1 03 00  ed 7d 00 00 ae 51 03 00  |.+..,....}...Q..|
00001110  af 48 03 00 30 1e 02 00  b1 6c 02 00 72 c2 02 00  |.H..0....l..r...|

Let me know if you figure out anything.  I'm having problems with chkdsk freezing up, as well as Windows locking up and/or rebooting.  I thought I'd see if I could resize the partition in linux and re-format the new partition without losing any data.  If not, I may just try to clone the partition and format the hard drive, then try to restore it again.

---

### Post by szaka on 2007-09-12
The NTFS-3G stable release 1.913 supports this situation: [http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)

Thank you for the help.

---

### Post by sublette131 on 2007-09-13
Not a problem...

By the way, there's a workaround also - just boot into windows (if you can) and disable the hibernation from the power settings.  Then there's no file, so the error goes away.

---

