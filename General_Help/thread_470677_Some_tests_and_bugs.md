---
title: "Some tests and bugs"
date: 2007-06-11
forum: General Help
---

### Post by CrazyGuy123 on 2007-06-11
I have 6 PC's here, and I've been testing Wubi on them since I've been watching this project for a while.  To make it clear, I'm not looking for tech support to get wubi working on these, just doing it hopefully to identify problems and support development.

Test 1:
Two identical PC's, one running a fresh Wubi installation, one running a fresh Ubuntu installation (on a real partition).  Comparing the speed of them, the Wubi one is MUCH slower, by a factor of about 5x.  I don't know how to debug the problem, but for example when running updates it doesn't appear the system is disk or cpu bound (disk access is very infrequent, and CPU never rises above 20%).  I did notice a lot of swap usage, more than I'd expect.  I suspect DMA is off for the disk drive, but I don't know how to find out.  (and it seems odd when dma is on for the other pc with identical hardware)  Also, I seemed to get a slight performance improvement by increasing the priority of the ntfs-3g process to -19.   This is old hardware (1997), so no extra drivers have been installed as none seem required.

Test 2:
On a vista PC, the bootloader installation doesn't work, as of Wubi-7.04-minefield-194.53.exe.  Simple solution, the path the installer used for bcdedit was "wubi\boot\winboot\wubildr.mbr", when it should be "\wubi\boot\winboot\wubildr.mbr" - changing that made it work.  Also, I see the installer uses a custom app to add the bootloader.  Do the devs realise you can just add registry entries to HKEY_LOCAL_MACHINE\BCD00000000\OBJECTS?  Although Microsoft use a complex layout of those registry keys, you can just pick the one involved with WUBI and export it to a .reg file.  Then have the installer just add that reg file to any system where you want it installed.  Although the long id number is randomly generated, it is no harm to have them the same for everybody, and it makes uninstallation easy (just delete that registry key)

Test 3:
On a PC with a HD (NTFS formatted by vista), and the vista bootloader, the wubildr.mbr can't find the wubildr file.  It does exist, but can't be found.  It's the same error as many other people (from memory)  "try (hd0,0) ntfs5P : 3".  To those with trouble, you can copy wubildr to a floppy disk, and then it'll work.  the FStest1.txt file attached is the results of fstest on this pc.

Test 4:
RAID.  Wasn't expecting this to work, but it gets a long way.  vista loader loads wubildr.mbr, which loads wubildr, which reads the menu, and loads initrd and the kernel.  The kernel starts, but about 5 secs into boot it gives up with IO errors saying access attempted past end of block device.  It was trying to access an address about 990GB into my striped (RAID0) array of 2 500GB disks.  It looks like that could easily be fixed with a linux raid driver included in the initrd.  It's an "Intel(R) 82801ER SATA RAID Controller", which is fairly common hardware.

Test 5:
On a PC with two NTFS disks (both formatted by vista), the grub command line tab completion can't find any files on one of the disks, whereas the other disk is fine.  (so probably not a bios disk access issue, unless it's large disk issues) A log is included (same log as test 3, with the disk moved to another pc in case it was a buggy BIOS).

Test 6:
I did some fragmentation tests, and it seems both initrd and the kernel can be severely fragmented and still work.  I had the kernel in 18 pieces and the initrd in 32 pieces, and it caused no problems whatsoever.  While fragmented files may increase the chances of faliure, fragmentation doesn't necessaraly cause faliure.   I didn't test fragmentation of wubildr, as it was too small and refused to fragment.  Could it instead be directory fragmentation or MFT fragmentation causing issues?

Test 7:
On the windows installer, when downloading the iso file, the file is progressively allocated, causing significant fragmentation (on my test system it was in ~20,000 fragments, even though the disk had been defragged first).  While fragmentation in itself doesn't cause an issue, it slows down the next part of the installation, as a lot of disk seeks are required.   It also makes the computer make an almost constant disk seek graunchy noise while downloading at 500kbps or more.  Maybe build in a buffer to the downloader code so it only writes to the disk every 5MB or so.  Other downloading apps, like µTorrent have a disk cache to solve this problem - maybe windows write cache isn't good for hundreds of tiny writes.

Test 8:
While reinstalling from a pre-existaing iso, the crc check seems to take much longer than necessary, with 100% CPU.  Maybe the algorithm needs some optimisation, or it could do with processing the file in larger chunks.  I don't know how it's done, but I expect NSIS code isn't suitable for hashing due to slow execution speed.  Even if the check is a hash, a SHA1 hash only takes 12 secs for a 700MB file on the same system, whereas the installer takes over a minute, and if it just a CRC32 check, it should be even quicker.  Note this isn't caused by the fragmentation issue above, as I defragmented the file so it was contiguous before trying this.

Test 9:
I'm sure this has been spotted already, but when updating the system, the lupin-target package needs to be reconfigured, and it spews out a few errors every time about an incorrect syntax in one of the scripts.  Don't have the exact error here, although I can get it if required.


EDIT:  for the attached fstest log, it looks like something bad went wrong, so would it help if I sent the MFT sectors from the disk to a dev to analyse in more detail (I can't send an entire disk image as it's too big, and I'd prefer to send to a dev rather than publicly listing every past and present file on this system)

EDIT2:  Of the 6 systems, 3 worked straight off, and 2 others after swapping HD's and using a floppy to boot from.  The last one was RAID, which I don't think I could make work without recompiling, which sounds like a lot of faff to set up the built environment.

Also, thanks to the developers - looking great so far.

---

### Post by bean123 on 2007-06-11
It's strange, fstest should print more information. replace fstest.exe, and run fstest.bat again.

---

### Post by CrazyGuy123 on 2007-06-11
I get exactly the same results, except with "version: 1.0" added after the fstest info c:\ line

Note I'm running this under Vista, and I've given it full admin permissions, although that may not allow it to directly access the disk.  I can move the disk to an XP pc and re-run if it'd help.

---

### Post by ecology2007 on 2007-06-11
You get the award of the most exhaustive report.:KS

---

### Post by bean123 on 2007-06-11
Try the following commands:

fstest -v inode C:\#0

fstest -v inode C:\#5

---

### Post by CrazyGuy123 on 2007-06-11
C:\wubi\tools>fstest.exe -v inode c:\ #0
ntfs_dir: 17

C:\wubi\tools>fstest.exe -v inode c:\ #5
ntfs_dir: 17


EDIT:  woops - typed the wrong command...
```
D:\wubi\tools>fstest.exe -v inode c:\#0
00000000: 00 00 00 01  58 01 00 00  01 00 00 00  03 00 00 00 ; ....X...........
00000010: 01 00 01 00  38 00 01 00  18 02 00 00  00 04 00 00 ; ....8...........
00000020: 00 00 00 00  00 00 00 00  06 00 00 00  00 00 00 00 ; ................
00000030: 9B 12 01 1A  00 00 00 00  10 00 00 00  60 00 00 00 ; ............`...
00000040: 00 00 18 00  00 00 00 00  48 00 00 00  18 00 00 00 ; ........H.......
00000050: B8 AB B3 F2  B6 3B C5 01  B8 AB B3 F2  B6 3B C5 01 ; .....;.......;..
00000060: B8 AB B3 F2  B6 3B C5 01  B8 AB B3 F2  B6 3B C5 01 ; .....;.......;..
00000070: 06 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000080: 00 00 00 00  00 01 00 00  00 00 00 00  00 00 00 00 ; ................
00000090: 00 00 00 00  00 00 00 00  30 00 00 00  68 00 00 00 ; ........0...h...
000000A0: 00 00 18 00  00 00 03 00  4A 00 00 00  18 00 01 00 ; ........J.......
000000B0: 05 00 00 00  00 00 05 00  B8 AB B3 F2  B6 3B C5 01 ; .............;..
000000C0: B8 AB B3 F2  B6 3B C5 01  B8 AB B3 F2  B6 3B C5 01 ; .....;.......;..
000000D0: B8 AB B3 F2  B6 3B C5 01  00 40 00 00  00 00 00 00 ; .....;...@......
000000E0: 00 40 00 00  00 00 00 00  06 00 00 00  00 00 00 00 ; .@..............
000000F0: 04 03 24 00  4D 00 46 00  54 00 00 00  00 00 00 00 ; ..$.M.F.T.......
00000100: 80 00 00 00  58 00 00 00  01 00 40 00  00 00 01 00 ; ....X.....@.....
00000110: 00 00 00 00  00 00 00 00  77 62 02 00  00 00 00 00 ; ........wb......
00000120: 40 00 00 00  00 00 00 00  00 80 27 26  00 00 00 00 ; @.........'&....
00000130: 00 80 27 26  00 00 00 00  00 80 27 26  00 00 00 00 ; ..'&......'&....
00000140: 32 94 6B 00  00 0C 43 30  B0 00 BB C5  87 00 33 B4 ; 2.k...C0......3.
00000150: 46 01 A3 35  4F 00 79 82  B0 00 00 00  B8 00 00 00 ; F..5O.y.........
00000160: 01 00 40 00  00 00 05 00  00 00 00 00  00 00 00 00 ; ..@.............
00000170: 13 00 00 00  00 00 00 00  40 00 00 00  00 00 00 00 ; ........@.......
00000180: 00 40 01 00  00 00 00 00  40 31 01 00  00 00 00 00 ; .@......@1......
00000190: 40 31 01 00  00 00 00 00  31 01 FF FF  0B 41 01 B9 ; @1......1....A..
000001A0: 7F B1 00 31  01 8A 23 78  41 01 89 C0  DA FE 41 01 ; ...1..#xA.....A.
000001B0: E3 02 0B 01  41 01 44 AE  1B FF 41 01  C8 DA AA 01 ; ....A.D...A.....
000001C0: 41 01 15 B5  52 FF 31 01  58 3B FD 41  01 94 C3 04 ; A...R.1.X;.A....
000001D0: 01 31 01 71  55 02 31 01  4D C2 C3 31  01 71 CA B3 ; .1.qU.1.M..1.q..
000001E0: 41 01 75 BE  51 FE 31 01  17 52 0B 41  01 80 4A 9E ; A.u.Q.1..R.A..J.
000001F0: 00 41 01 61  7E 8A 01 41  01 62 D3 E4  FE 41 01 1A ; .A.a~..A.b...A..
00000200: 06 17 FF 41  01 5B 55 DA  01 00 79 86  00 10 99 C1 ; ...A.[U...y.....
00000210: FF FF FF FF  00 00 00 00  FF FF FF FF  00 00 00 00 ; ................
00000220: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000230: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000240: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000250: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000260: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000270: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000280: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000290: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000300: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000310: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000320: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000330: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000340: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000350: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000360: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000370: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000380: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000390: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=74)
    $MFT
  $DATA (0x80) (nr,sz=640122880)
    6291456+220320,77475288+360832,119003888+669088
  $BITMAP (0xB0) (nr,sz=78144)
    6291448+8,99352000+8,162339344+8,8592984+8,148583792+8,28878736+8,252673488+8,161818232+8,160366904+8,297082328+8,29
8305888+8,266722248+8,226766672+8,1188600+8,7123888+8,90113968+8,296942264+8,148477384+8,26330776+8,275018096+8
```

```
D:\wubi\tools>fstest.exe -v inode c:\#5
00000000: 46 49 4C 45  30 00 03 00  01 00 00 00  03 00 00 00 ; FILE0...........
00000010: 05 00 01 00  38 00 03 00  80 02 00 00  00 04 00 00 ; ....8...........
00000020: 00 00 00 00  00 00 00 00  35 00 00 00  05 00 00 00 ; ........5.......
00000030: C1 36 00 00  00 00 00 00  10 00 00 00  60 00 00 00 ; .6..........`...
00000040: 00 00 18 00  00 00 00 00  48 00 00 00  18 00 00 00 ; ........H.......
00000050: C2 79 C9 4D  68 FE C6 01  E5 29 ED 7B  CE AB C7 01 ; .y.Mh....).{....
00000060: E5 29 ED 7B  CE AB C7 01  E5 29 ED 7B  CE AB C7 01 ; .).{.....).{....
00000070: 26 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; &...............
00000080: 00 00 00 00  BB 0C 00 00  00 00 00 00  00 00 00 00 ; ................
00000090: 28 3F 4A 9F  00 00 00 00  20 00 00 00  48 00 00 00 ; (?J..... ...H...
000000A0: 01 00 00 00  00 00 1E 00  00 00 00 00  00 00 00 00 ; ................
000000B0: 00 00 00 00  00 00 00 00  40 00 00 00  00 00 00 00 ; ........@.......
000000C0: 00 10 00 00  00 00 00 00  90 05 00 00  00 00 00 00 ; ................
000000D0: 90 05 00 00  00 00 00 00  41 01 47 E7  5E 01 00 85 ; ........A.G.^...
000000E0: 30 00 00 00  60 00 00 00  00 00 18 00  00 00 01 00 ; 0...`...........
000000F0: 44 00 00 00  18 00 01 00  05 00 00 00  00 00 05 00 ; D...............
00000100: B8 AB B3 F2  B6 3B C5 01  B8 AB B3 F2  B6 3B C5 01 ; .....;.......;..
00000110: B8 AB B3 F2  B6 3B C5 01  B8 AB B3 F2  B6 3B C5 01 ; .....;.......;..
00000120: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000130: 06 00 00 10  00 00 00 00  01 03 2E 00  00 00 00 00 ; ................
00000140: 40 00 00 00  28 00 00 00  00 00 00 00  00 00 09 00 ; @...(...........
00000150: 10 00 00 00  18 00 00 00  F2 3D 7F 79  A8 AA D9 11 ; .........=.y....
00000160: 9D D8 00 11  11 79 A8 11  90 00 00 00  58 00 00 00 ; .....y......X...
00000170: 00 04 18 00  00 00 1F 00  38 00 00 00  20 00 00 00 ; ........8... ...
00000180: 24 00 49 00  33 00 30 00  30 00 00 00  01 00 00 00 ; $.I.3.0.0.......
00000190: 00 10 00 00  01 00 00 00  10 00 00 00  28 00 00 00 ; ............(...
000001A0: 28 00 00 00  01 00 00 00  00 00 00 00  00 00 00 00 ; (...............
000001B0: 18 00 00 00  03 00 00 00  A5 05 00 00  00 00 00 00 ; ................
000001C0: B0 00 00 00  50 00 00 00  01 04 40 00  00 00 20 00 ; ....P.....@... .
000001D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000001E0: 48 00 00 00  00 00 00 00  00 10 00 00  00 00 00 00 ; H...............
000001F0: 50 02 00 00  00 00 00 00  50 02 00 00  00 00 00 00 ; P.......P.......
00000200: 24 00 49 00  33 00 30 00  31 01 15 A7  6D 00 B0 E1 ; $.I.3.0.1...m...
00000210: 00 01 00 00  68 00 00 00  00 09 18 00  00 00 21 00 ; ....h.........!.
00000220: 38 00 00 00  30 00 00 00  24 00 54 00  58 00 46 00 ; 8...0...$.T.X.F.
00000230: 5F 00 44 00  41 00 54 00  41 00 EC 95  C2 01 00 00 ; _.D.A.T.A.......
00000240: 05 00 00 00  00 00 05 00  01 00 00 00  0B 00 00 00 ; ................
00000250: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000260: 00 00 00 00  00 00 00 00  02 D4 78 00  00 00 00 00 ; ..........x.....
00000270: 02 00 00 00  00 00 00 00  FF FF FF FF  00 00 00 00 ; ................
00000280: 41 00 EC 95  C2 01 00 00  05 00 00 00  00 00 05 00 ; A...............
00000290: 01 00 00 00  0B 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002B0: 02 D4 78 00  00 00 00 00  02 00 00 00  00 00 00 00 ; ..x.............
000002C0: FF FF FF FF  00 00 00 00  FF FF FF FF  FF FF FF FF ; ................
000002D0: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF ; ................
000002E0: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF ; ................
000002F0: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF ; ................
00000300: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF ; ................
00000310: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF ; ................
00000320: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF ; ................
00000330: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF ; ................
00000340: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF ; ................
00000350: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF ; ................
00000360: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF ; ................
00000370: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF ; ................
00000380: FF FF FF FF  FF FF FF FF  FF FF FF FF  FF FF FF FF ; ................
00000390: 00 01 00 00  68 00 00 00  00 09 18 00  00 00 0C 00 ; ....h...........
000003A0: 38 00 00 00  30 00 00 00  24 00 54 00  58 00 46 00 ; 8...0...$.T.X.F.
000003B0: 5F 00 44 00  41 00 54 00  41 00 EC 95  C2 01 00 00 ; _.D.A.T.A.......
000003C0: 05 00 00 00  00 00 05 00  01 00 00 00  09 00 00 00 ; ................
000003D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003F0: 03 00 00 00  00 00 00 00  FF FF FF FF  00 00 00 00 ; ................
Type: Directory
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $ATTRIBUTE_LIST (0x20) (nr,sz=1424)
    183974456+8
  $FILENAME (0x30) (r,sz=68)
    .
  $OBJECT_ID (0x40) (r,sz=16)
  $INDEX_ROOT (0x90) (r,nm=$I30,sz=56)
  $BITMAP (0xB0) (nr,nm=$I30,sz=592)
    57489576+8
  $UNKNOWN (0x0) (r,nm=$TXF_DATA,sz=56)
Attr List:
  $STANDARD_INFORMATION (0x10) (r,mft=0x5,sz=72)
  $FILENAME (0x30) (r,mft=0x5,sz=68)
    .
  $OBJECT_ID (0x40) (r,mft=0x5,sz=16)
  $INDEX_ROOT (0x90) (r,mft=0x5,nm=$I30,sz=56)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x575DB,vcn=0x0,nm=$I30,sz=19050496)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x592DF,vcn=0xD9,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x6354E,vcn=0x1A3,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x59AD4,vcn=0x1A4,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x5A2DC,vcn=0x281,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x5AABD,vcn=0x358,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x638E9,vcn=0x44E,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x5B33F,vcn=0x44F,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x63911,vcn=0x53D,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x5BD42,vcn=0x53E,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x5C73E,vcn=0x640,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x63914,vcn=0x754,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x5D17B,vcn=0x755,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x5DC1A,vcn=0x876,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x63919,vcn=0x990,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x5E646,vcn=0x991,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x6391B,vcn=0xAB8,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x5F0AB,vcn=0xAB9,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x6391C,vcn=0xBD7,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x5FA70,vcn=0xBD8,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x6391D,vcn=0xCFB,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x604A6,vcn=0xCFC,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x6391E,vcn=0xE1C,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x60E8B,vcn=0xE1D,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x6391F,vcn=0xF40,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x61854,vcn=0xF41,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x63920,vcn=0x1064,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x62236,vcn=0x1065,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x63921,vcn=0x1183,nm=$I30,sz=0)
  $INDEX_ALLOCATION (0xA0) (nr,mft=0x62C2F,vcn=0x1184,nm=$I30,sz=0)
  $BITMAP (0xB0) (nr,mft=0x5,vcn=0x0,nm=$I30,sz=592)
  $UNKNOWN (0x0) (r,mft=0x5,nm=$TXF_DATA,sz=56)

```


Bean, is the fstest utility a "home-brew" program of yours, or is it part of grub4dos?  If it's yours it seems like a very impressive app for diagnosing the bootloader.

---

### Post by bean123 on 2007-06-11
I know what happen, you have non-resident $BITMAP, which I ignore because they're rare.

> **CrazyGuy123 said:**
> 
Bean, is the fstest utility a "home-brew" program of yours, or is it part of grub4dos?  If it's yours it seems like a very impressive app for diagnosing the bootloader.

Internally, fstest use the same ntfs code as grub, but i add an interface so that it can be run in the windows environment.

---

### Post by bean123 on 2007-06-12
Try the new version, it should fix the problem.

---

### Post by bean123 on 2007-06-12
Fix a small bug in fstest.

---

### Post by CrazyGuy123 on 2007-06-12
New version does a lot better, but there's still some errors with getting directory listings, although that might not cause any issues with booting.   Also, the old fstest version ran very quickly, but this version takes about 30 secs with a lot of disk reads (about 13000 read calls, which read 20Mb of data) per call of fstest list as if it's looping through reading a lot of data until it finds what it's looking for.

As far as comparing the log with the actual files, from the root directory listing there seems to be one directory missing "$Recycle.Bin", although I'm guessing it might be ignored since it starts wit "$", although windows shows it as a real directory.

The 

I've attached the log file for if it helps.

---

### Post by bean123 on 2007-06-12
> **CrazyGuy123 said:**
> New version does a lot better, but there's still some errors with getting directory listings, although that might not cause any issues with booting.   Also, the old fstest version ran very quickly, but this version takes about 30 secs with a lot of disk reads (about 13000 read calls, which read 20Mb of data) per call of fstest list as if it's looping through reading a lot of data until it finds what it's looking for.

It's normal, your drive is extremely fragmental, so the driver need a lot a reads to get what it needs.

> As far as comparing the log with the actual files, from the root directory listing there seems to be one directory missing "$Recycle.Bin", although I'm guessing it might be ignored since it starts wit "$", although windows shows it as a real directory.

This is not a bug. NTFS have many hidden file that starts with $, it will be odd if they're in the list. So I hide them all. But there is a trick to get arond this, just use $ as the first character, and all files start with $ will be shown:

fstest list C:\$

---

### Post by CrazyGuy123 on 2007-06-12
Ite drive claims not to be significantly fragmented (a MS defrag is scheduled weekly anyway), but I suspect I might have pushed the filesystem hard a while back when I tried to compile some linux distros from source with cgywin, running on this NTFS drive.  That produced a massive numbner of tiny files.  All the files have since been deleted, but I heard somewhere that when a tiny file stored in the MFT is deleted the space isn't reclaimed, so that might be it.

I'm just gonna give booting with your updated grldr a go - brb

---

### Post by Computer Guru on 2007-06-12
MS defrag is useless - actually benchmarks prove that defragging a drive in Vista with the MS defrag utility *hurts* performance rather than improves it, since the defrag algorithm is totally messed up (like the rest of the OS). I'm not sure if you're using Vista to do this, but just a word for the wise.

I use and recommend PerfectDisk myself, it's amazing! :)

---

### Post by bean123 on 2007-06-12
After examining your list, I found out that the directory index is 20M, but there is only 28 items in it, I wonder what the other space is used for. Please run following commands to dump the allocation bitmap.

fstest dump C:57489576+8

fstest inode C:\#0x575DB

fstest inode C:\#0x592DF

---

### Post by CrazyGuy123 on 2007-06-12
That new grldr boots great - thanks loads for your efforts on it.

Here's the results of those commands:
```

C:\wubi\tools>fstest dump C:57489576+8
00000000: 29 00 00 00  00 00 20 00  00 00 00 00  00 00 00 00 ; )..... .........
00000010: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000020: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000030: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000040: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000050: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000060: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000070: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000080: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000090: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000000A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000000B0: 00 00 00 00  20 00 00 00  00 00 00 00  00 00 00 00 ; .... ...........
000000C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000000D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000000E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000000F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000100: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000110: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000120: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000130: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000140: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000150: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000160: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000170: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000180: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000190: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000001A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000001B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000001C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000001D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000001E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000001F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000200: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000210: 10 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000220: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000230: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000240: 00 00 00 00  00 01 00 00  00 00 00 00  00 00 00 00 ; ................
00000250: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000260: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000270: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000280: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000290: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000002F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000300: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000310: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000320: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000330: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000340: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000350: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000360: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000370: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000380: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000390: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
000003F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00 ; ................
00000400: CC FF 75 3A  E0 88 A3 04  4C CC 4B B4  66 48 47 B1 ; ..u:....L.K.fHG.
00000410: C0 0F 3D 19  AE 2E DC 6B  17 70 D1 56  E3 4A 70 8A ; ..=....k.p.V.Jp.
00000420: 98 04 4A D0  94 8E CC 18  D0 58 80 74  34 0D 30 4E ; ..J......X.t4.0N
00000430: 83 02 65 02  42 6C 31 02  39 8A 98 C8  97 24 75 51 ; ..e.Bl1.9....$uQ
00000440: A2 47 8C C4  0A 69 21 D3  7A C6 24 88  C1 A3 20 31 ; .G...i!.z.$... 1
00000450: 98 68 1C D0  00 C7 68 48  E8 53 D4 53  71 55 4C AE ; .h....hH.S.SqUL.
00000460: 38 7D C0 02  0C BC 99 04  5D 0F 34 49  A3 63 FA F8 ; 8}......].4I.c..
00000470: 66 3F 85 23  65 E6 78 02  84 42 51 12  9D 9F 5C 6F ; f?.#e.x..BQ...\o
00000480: 69 4B 01 06  59 B2 74 7D  7F 54 6C 9B  0A C0 89 17 ; iK..Y.t}.Tl.....
00000490: CC 1B BF DD  34 24 25 5A  93 F3 B2 3C  B1 D8 D5 65 ; ....4$%Z...<...e
000004A0: 05 CB D0 78  A3 46 8C 75  EE 3E D2 88  3A AE B9 0A ; ...x.F.u.>..:...
000004B0: 99 E6 72 BA  DD 18 6D C3  16 C1 8B 9A  61 6D 8C D6 ; ..r...m.....am..
000004C0: 6D 17 21 C9  28 A6 AC A3  47 5E F2 D2  1D 51 D4 EC ; m.!.(...G^...Q..
000004D0: 38 5D 79 94  28 1F 5B 02  A4 46 66 47  46 89 7C 5B ; 8]y.(.[..FfGF.|[
000004E0: 38 0E B7 40  09 04 A7 81  CA 1D 3A 1D  0D 77 93 2E ; 8..@......:..w..
000004F0: 48 F9 D9 A1  45 BC 50 04  73 B7 27 66  D4 A0 28 23 ; H...E.P.s.'f..(#
00000500: 85 02 D6 9D  9B BB 0C BE  AD 3B 2C 8A  5B 77 3A 44 ; .........;,.[w:D
00000510: 50 74 A0 A9  63 A9 63 F6  1B 3A F7 11  9B CC C1 D6 ; Pt..c.c..:......
00000520: 39 26 B1 A0  BB D9 26 07  98 D3 14 A8  32 51 1E 70 ; 9&....&.....2Q.p
00000530: 3A 46 A1 10  4D 7C 3E C3  26 92 A6 E2  72 EF 67 E8 ; :F..M|>.&...r.g.
00000540: 6D F0 71 C1  EE 91 7C 5A  71 12 D0 96  28 10 55 28 ; m.q...|Zq...(.U(
00000550: 17 91 24 98  88 F6 FA D1  27 1F 70 A6  2B 1A DF 73 ; ..$.....'.p.+..s
00000560: E0 34 5A 6C  C4 ED 27 30  35 4B BB 83  7B 35 B5 A1 ; .4Zl..'05K..{5..
00000570: 9B 9D D0 CF  81 54 A4 DD  D9 A9 63 BD  41 89 3F 2D ; .....T....c.A.?-
00000580: D5 46 2E 85  C2 B4 BC CA  5C 5D 29 1D  59 C6 9A FC ; .F......\]).Y...
00000590: 59 06 E8 67  20 E1 45 1E  ED 88 41 7B  E8 FC CA 0F ; Y..g .E...A{....
000005A0: D8 D2 58 FF  29 F0 91 D9  A6 42 FD 4A  94 13 F0 0B ; ..X.)....B.J....
000005B0: 85 1B BB 1A  2C 10 71 16  47 09 6E 73  A4 6B 80 60 ; ....,.q.G.ns.k.`
000005C0: 01 5A 60 9C  E3 0C 67 40  03 1C 00 39  D7 19 67 00 ; .Z`...g@...9..g.
000005D0: 8A 5D 38 56  BB CA 05 2B  DB DC CD 94  F0 18 08 0B ; .]8V...+........
000005E0: 4F EB 21 46  BA B6 E8 AB  AD 63 8E AD  5E 1F 05 26 ; O.!F.....c..^..&
000005F0: 6C 64 ED 8B  BA EE 9B 29  42 0D 49 DB  B2 06 FF 35 ; ld.....)B.I....5
00000600: E7 73 7C 69  22 0F 01 0F  E5 53 0E E4  16 EC 80 71 ; .s|i"....S.....q
00000610: C8 CC B1 C2  B5 40 4E B8  65 41 0B 1A  D0 98 E0 6A ; .....@N.eA.....j
00000620: BC 31 65 19  2E 18 0B D2  A2 F4 E6 CE  B3 DA 65 E3 ; .1e...........e.
00000630: EA D5 97 A6  11 85 05 82  F0 FD 13 67  6C 47 E0 C7 ; ...........glG..
00000640: 63 9F EB B5  2D 30 77 01  02 6B 4B C5  C6 D6 9D 3B ; c...-0w..kK....;
00000650: 3A 30 69 CD  A6 E8 34 72  DB 44 28 0B  15 C7 54 C3 ; :0i...4r.D(...T.
00000660: 18 3A E3 2C  5C 41 01 75  FE 72 D8 64  26 B6 8D 51 ; .:.,\A.u.r.d&..Q
00000670: 80 FE A8 2C  43 D3 5B 41  68 3C 93 37  A0 BC D0 13 ; ...,C.[Ah<.7....
00000680: 90 96 80 14  30 8B B1 17  92 B6 E5 26  90 04 4D DE ; ....0......&..M.
00000690: 15 82 66 77  F3 B6 B5 18  E6 82 04 39  0F AB F3 72 ; ..fw.......9...r
000006A0: 4C 8B B0 B4  03 2D 6D 03  4B A1 CE 38  90 91 A8 81 ; L....-m.K..8....
000006B0: 5D 83 82 1A  1A E6 79 71  0A CA BE 4C  62 8C 6F 7E ; ].....yq...Lb.o~
000006C0: 00 DE D9 AC  30 FA 52 E2  FE 26 25 52  1B 3F 5F C3 ; ....0.R..&%R.?_.
000006D0: 15 C9 82 B6  89 FA 98 99  C1 61 A4 59  C0 6D 86 19 ; .........a.Y.m..
000006E0: CC 80 06 38  58 6A CB 0C  33 E0 00 30  40 CC 65 06 ; ...8Xj..3..0@.e.
000006F0: 19 C0 40 97  5E 66 9A 01  03 7E 0C 35  6A 06 0C 38 ; ..@.^f...~.5j..8
00000700: 30 D5 98 19  66 C0 3F AC  FB D9 34 AA  C3 F8 29 5D ; 0...f.?...4...)]
00000710: A4 EF E0 13  5C 03 14 AC  AD 38 30 26  AA 4C E5 E2 ; ....\....80&.L..
00000720: 50 B2 33 CB  5D 7B 5F 14  46 B8 1C 24  3C 8C D8 44 ; P.3.]{_.F..$<..D
00000730: 30 13 46 19  4A 06 CA 80  36 19 06 40  C0 55 57 19 ; 0.F.J...6..@.UW.
00000740: 2B 4E D5 4B  83 91 72 BC  4D B7 1E 85  57 FF B9 EE ; +N.K..r.M...W...
00000750: DA 9A 24 01  30 40 A9 55  1D AC A2 79  0D 72 25 07 ; ..$.0@.U...y.r%.
00000760: E2 C8 6A 91  34 03 D1 5D  85 4D 94 B4  1B F7 60 61 ; ..j.4..].M....`a
00000770: 4F 96 43 3A  BE 16 D3 58  00 81 4B CB  08 3F DE E9 ; O.C:...X..K..?..
00000780: 8D 3C EA 57  4E 61 92 11  9F 11 96 0E  3C 06 DE EC ; .<.WNa......<...
00000790: 19 25 CC D0  0D 05 CA 08  BC 1C EB 84  92 63 24 E8 ; .%...........c$.
000007A0: 01 A4 34 2A  8C 30 D0 0A  05 D0 75 86  BA 59 E1 AA ; ..4*.0....u..Y..
000007B0: 77 E8 5C 36  2E 77 81 C2  07 60 11 75  36 7E 17 D1 ; w.\6.w...`.u6~..
000007C0: 8D 6E C5 C5  71 E1 D4 7C  F9 E8 F0 20  EC 10 D9 34 ; .n..q..|... ...4
000007D0: 6A 43 14 E7  91 FB AE 86  26 60 9C 29  D1 CE 00 A6 ; jC......&`.)....
000007E0: B1 54 4E 01  DA 84 D4 0C  31 61 30 E9  CC BB 4E 03 ; .TN.....1a0...N.
000007F0: EC EC 3B 10  23 62 9B 6F  7D CF 56 13  F5 21 AA D3 ; ..;.#b.o}.V..!..
00000800: 97 4F AC 13  AE 6C A0 41  23 BA B3 34  8C D4 39 24 ; .O...l.A#..4..9$
00000810: 0E 2D 19 B8  F9 7C 16 71  FB 63 6D EC  08 96 05 A1 ; .-...|.q.cm.....
00000820: 9F FA 1B ED  FF 80 2D F3  BF 0C 28 9B  15 F8 DE 78 ; ......-...(....x
00000830: CF 68 DD 48  0D 81 B1 3B  A7 CB EF 1A  AF 18 65 F9 ; .h.H...;......e.
00000840: 18 25 D1 61  36 F1 68 03  2C 05 38 B8  51 30 58 61 ; .%.a6.h.,.8.Q0Xa
00000850: 67 1F 1B E0  D7 33 5A 86  F6 C3 3C D8  E7 7D DA 86 ; g....3Z...<..}..
00000860: 5F 6F 75 E1  6F AB 22 19  FE EC 57 17  0A 6B 18 8C ; _ou.o."...W..k..
00000870: 91 D2 0E 52  95 6E F0 2A  4B E3 06 BA  8C 84 01 F7 ; ...R.n.*K.......
00000880: 46 85 96 96  06 17 ED B3  7D 4A 03 90  B2 5A C8 29 ; F.......}J...Z.)
00000890: 7D C7 92 FB  B6 DC 31 69  B1 C8 AE FA  D1 18 E5 48 ; }.....1i.......H
000008A0: 09 D2 5C 47  D3 F4 C6 58  A7 9F EA 40  0A 1A 90 C0 ; ..\G...X...@....
000008B0: 43 43 76 52  18 14 41 04  87 5C C6 3F  B7 C3 70 E4 ; CCvR..A..\.?..p.
000008C0: F9 75 3E A7  56 C0 73 49  9B 94 66 6C  C6 5C 31 8A ; .u>.V.sI..fl.\1.
000008D0: 33 51 1C 7C  BA 28 A2 F9  4A 43 4D 37  D4 01 24 9C ; 3Q.|.(..JCM7..$.
000008E0: 15 90 15 14  34 94 90 FF  A4 65 CD 50  FA 08 79 A1 ; ....4....e.P..y.
000008F0: D0 C8 C6 40  C3 22 C5 0B  7A 45 B9 72  42 C8 6A 49 ; ...@."..zE.rB.jI
00000900: C9 56 41 0B  BC 6C DD 62  7F 80 A3 BB  49 0E 9A DB ; .VA..l.b....I...
00000910: 20 6C 6A D6  43 B7 4C 0F  D0 02 53 8D  3E 2E 0C 46 ;  lj.C.L...S.>..F
00000920: 43 FB AE E6  F9 98 86 61  BC B6 64 5E  94 0E D4 0B ; C......a..d^....
00000930: CD FC A4 6F  3C 3A 44 13  AE 63 7A 3F  D6 63 DB 1B ; ...o<:D..cz?.c..
00000940: FB 18 4C F4  96 AB 32 76  D8 26 40 A0  20 25 FD 3E ; ..L...2v.&@. %.>
00000950: 4B E1 DF 9A  82 4E B0 5A  D4 0C B1 02  E7 A5 95 86 ; K....N.Z........
00000960: 67 C1 02 AC  D3 E5 30 19  5F 9F 19 D9  65 19 3B 63 ; g.....0._...e.;c
00000970: B2 EC 38 4B  4D B7 42 1A  4C DF CB BD  C1 15 86 28 ; ..8KM.B.L......(
00000980: 2F 44 43 5A  DC C5 3A DF  31 B8 4D EE  93 20 6E 8D ; /DCZ..:.1.M.. n.
00000990: D1 14 A8 C9  39 55 29 9F  5D CC 2D 3A  1A 01 DF F4 ; ....9U).].-:....
000009A0: 4A FB 04 1B  13 50 91 6E  4C 43 10 76  44 1B 9B 79 ; J....P.nLC.vD..y
000009B0: 18 DB F7 A1  02 FB A2 05  3A A9 93 3E  84 5E A9 1F ; ........:..>.^..
000009C0: 44 D2 8C B3  FB 68 94 88  27 40 06 12  51 9A F4 F4 ; D....h..'@..Q...
000009D0: CF 22 3E 9F  E3 2B AC 67  11 E6 BF FC  3B E2 BE 53 ; .">..+.g....;..S
000009E0: D1 EA 6A C8  F7 6A B3 CF  A6 B8 A1 6A  53 55 16 E1 ; ..j..j.....jSU..
000009F0: 86 C2 4D DD  81 D7 9D 9B  3B 96 01 62  8E F7 8B C1 ; ..M.....;..b....
00000A00: B5 75 A7 33  BD BB F7 5A  B0 9B 7A 91  0C 97 7F 9D ; .u.3...Z..z.....
00000A10: 9C CB 52 06  C0 14 47 12  2C 50 B2 F8  A7 CE 2A 60 ; ..R...G.,P....*`
00000A20: 23 14 23 E2  B9 7C 95 2B  DC E6 B7 71  25 3F 89 1B ; #.#..|.+...q%?..
00000A30: 1E A8 C6 E2  3E 1F 8E 92  A5 65 91 B5  4C 4A 88 D2 ; ....>....e..LJ..
00000A40: BA F3 2F B0  B0 74 68 59  F9 FF 3B 5A  ED 0D EE 77 ; ../..thY..;Z...w
00000A50: AF 54 A0 6B  0B D8 5E 00  11 E1 3F 9B  67 DC D7 A6 ; .T.k..^...?.g...
00000A60: 4D BF 82 3A  F8 67 AE 37  4C B3 08 AC  A9 B1 F6 67 ; M..:.g.7L......g
00000A70: 20 8C B0 2A  0F 45 19 50  EF 57 B4 73  A8 2F 96 E7 ;  ..*.E.P.W.s./..
00000A80: A7 5C 6E 47  D0 3A 56 77  7A 95 5E B1  DC D7 2C A3 ; .\nG.:Vwz.^...,.
00000A90: BA C1 0B 74  F4 9D B4 9D  35 84 20 91  BB B9 1C 93 ; ...t....5. .....
00000AA0: CF DF 16 1C  F3 75 D2 4E  53 E4 E6 6E  73 EF 4B 40 ; .....u.NS..ns.K@
00000AB0: DB 52 14 85  A8 47 4B D2  24 69 3F 6D  B3 84 7F 6C ; .R...GK.$i?m...l
00000AC0: CD B6 95 EC  FF 8C 4F 73  74 C4 F9 4C  B9 94 18 98 ; ......Ost..L....
00000AD0: CE 1A D0 EA  36 07 7C 44  98 DC 4A 9B  92 8F E6 3B ; ....6.|D..J....;
00000AE0: 58 EA E0 3E  92 3A 97 40  C3 83 B7 D5  82 23 0B 10 ; X..>.:.@.....#..
00000AF0: 8F 72 FE 3A  09 ED AF 5E  14 8A D7 AF  00 0F 1C 92 ; .r.:...^........
00000B00: C9 58 A4 B3  E6 77 D6 63  D3 6E B4 83  76 37 11 6A ; .X...w.c.n..v7.j
00000B10: 72 01 81 FC  C8 8C 12 F9  61 FB BA A2  A7 CA E6 F3 ; r.......a.......
00000B20: 05 0B A4 82  17 9F 0B F8  14 FD 1A F9  DC CD D1 65 ; ...............e
00000B30: 86 30 F4 A0  AD 00 69 C3  81 27 BD 21  3C 39 7F AD ; .0....i..'.!<9..
00000B40: 94 5E 03 21  D1 F0 BD C0  2A 64 CB 34  43 F2 FC 3F ; .^.!....*d.4C..?
00000B50: FA 29 73 E7  0E 08 F4 7E  67 8C 7F A4  3F E7 3D F0 ; .)s....~g...?.=.
00000B60: B2 44 45 2B  65 3D 76 DB  5D BD 06 D9  F0 6E 15 46 ; .DE+e=v.]....n.F
00000B70: C0 FA 52 C2  61 FF 09 65  CE 0A 86 F6  1D 41 2D 20 ; ..R.a..e.....A-
00000B80: 68 72 19 77  97 29 41 13  7B 7A 31 A0  FB 94 02 C0 ; hr.w.)A.{z1.....
00000B90: BF BF 58 02  3D F1 A6 44  7A BF 6A 3A  CB CD AF 0B ; ..X.=..Dz.j:....
00000BA0: 0C E6 8D 48  24 26 52 EB  37 F1 09 D7  4E F2 76 AA ; ...H$&R.7...N.v.
00000BB0: A4 94 BC 80  0B FA C0 48  4F 2C 13 A3  7F 13 27 C3 ; .......HO,....'.
00000BC0: E0 DD 09 BF  57 A6 1A EB  4F 6F 11 7F  36 A6 F8 2B ; ....W...Oo..6..+
00000BD0: 32 8D E8 5A  D3 98 33 72  34 D7 AE D3  A3 B1 01 7D ; 2..Z..3r4......}
00000BE0: E0 70 07 36  80 D1 12 58  4E E0 AB B9  FE DB 56 23 ; .p.6...XN.....V#
00000BF0: 1A 70 95 EC  5B 02 6C AC  52 9A 2B 9B  05 3A 28 90 ; .p..[.l.R.+..:(.
00000C00: D8 98 2B A5  88 32 06 16  B0 72 C3 41  B5 12 A8 EC ; ..+..2...r.A....
00000C10: 1A 95 D0 C4  BF 31 A9 EA  52 56 01 87  ED C1 30 40 ; .....1..RV....0@
00000C20: 4A 42 08 1F  E0 94 4B F4  17 FC 8C B1  C2 FA AF 63 ; JB....K........c
00000C30: 63 1D 94 22  8C C3 0C F8  23 6B 1A 4F  F9 73 0B B3 ; c.."....#k.O.s..
00000C40: 98 CE CF EB  92 D0 98 64  F8 33 A4 97  22 7E 81 28 ; .......d.3.."~.(
00000C50: 0E E0 1A 11  81 E2 03 61  50 3C 47 CA  F3 B5 75 EB ; .......aP<G...u.
00000C60: E2 2E 37 37  4E DD F6 BD  D4 8E A0 0D  CB 84 1F 63 ; ..77N..........c
00000C70: 6D DF 2A 8E  08 A4 AB D8  5B 23 EA FA  0E 09 A4 F4 ; m.*.....[#......
00000C80: A0 B1 58 73  6F 2C B2 C0  0C 3F 6C 4A  FA 0C 42 33 ; ..Xso,...?lJ..B3
00000C90: D8 E3 12 BD  36 EB D1 9F  EC 13 B1 0A  E5 6E 38 A4 ; ....6........n8.
00000CA0: 3A 62 18 10  B2 C6 6F C1  DB D2 D0 F0  40 F5 B6 08 ; :b....o.....@...
00000CB0: 79 5A 5B 01  DD A3 91 7C  3C 55 9B 3D  C5 DD A5 06 ; yZ[....|<U.=....
00000CC0: A9 3E 46 5C  D4 BD 9E E4  57 AC AD A1  4F F3 EE 5C ; .>F\....W...O..\
00000CD0: 54 AF 6D 0D  03 12 7B 04  FC BE 48 16  86 F1 9B 16 ; T.m...{...H.....
00000CE0: C5 3F 2D A8  B0 94 98 CB  18 E4 C2 25  D6 85 14 8B ; .?-........%....
00000CF0: 7C 0A EC 8F  3A 83 19 5A  8A C5 A6 03  55 09 32 08 ; |...:..Z....U.2.
00000D00: F6 3B 07 28  D9 29 51 A2  1A E5 57 CD  00 C6 40 62 ; .;.(.)Q...W...@b
00000D10: 11 03 57 E1  EC 03 3A 8F  95 A9 A8 53  F2 4E 69 D3 ; ..W...:....S.Ni.
00000D20: E1 B3 B5 DC  27 25 DF 5B  41 64 55 6E  36 08 A1 41 ; ....'%.[AdUn6..A
00000D30: DA EB 03 B3  47 93 BF F5  A4 78 85 91  D8 77 B2 38 ; ....G....x...w.8
00000D40: 05 16 AC FD  F1 D4 11 8A  84 C2 D4 0D  2C 70 D7 7A ; ............,p.z
00000D50: A0 73 D6 97  BE C9 7E 5E  F8 65 16 5B  BF AD D2 69 ; .s....~^.e.[...i
00000D60: 72 15 8D 66  CF 11 97 78  12 B9 69 1B  82 00 7F 30 ; r..f...x..i....0
00000D70: 3C 18 6D 73  76 F8 11 0D  7F 51 16 84  6C 4B 48 DA ; <.msv....Q..lKH.
00000D80: 81 21 47 40  33 72 14 57  58 0B 0A D0  38 C8 8B D6 ; .!G@3r.WX...8...
00000D90: DF 11 C2 BB  D5 B8 11 0F  83 7A D8 15  82 6B 2D FA ; .........z...k-.
00000DA0: 47 20 3B 46  02 C1 18 C9  2F 31 2E 80  67 BA 34 81 ; G ;F..../1..g.4.
00000DB0: 36 2F 16 6E  03 6B 56 41  67 EF 92 49  09 C6 58 32 ; 6/.n.kVAg..I..X2
00000DC0: 20 2B 29 9C  B7 58 F0 8D  9D 0D 71 56  80 A9 6B 31 ;  +)..X....qV..k1
00000DD0: CE A8 FF 57  67 FC BE 1A  39 FB 37 F8  89 9E 02 FD ; ...Wg...9.7.....
00000DE0: 5B 73 16 83  80 DA C9 9B  9B B8 7E 0B  E5 B4 34 0B ; [s........~...4.
00000DF0: F5 EE 51 49  D0 65 81 73  A0 C0 BE B6  7B 24 89 E6 ; ..QI.e.s....{$..
00000E00: CE 50 40 6C  F7 BE EC 12  8A 2D 65 FA  5E 58 6D 84 ; .P@l.....-e.^Xm.
00000E10: D5 63 81 92  84 B4 B6 46  BC 1A D1 B0  85 E4 04 A9 ; .c.....F........
00000E20: 02 12 F0 E2  BC 8A 43 64  21 2A E7 31  C9 B9 69 5C ; ......Cd!*.1..i\
00000E30: 83 A2 97 40  31 0F B8 56  34 A5 35 D5  A0 60 84 F2 ; ...@1..V4.5..`..
00000E40: 5D 18 2D 55  AA FF 54 5B  22 52 D7 8E  8A 38 C0 EE ; ].-U..T["R...8..
00000E50: 04 C1 7F BE  91 BA FB 4A  34 A7 34 B8  1D 71 F4 42 ; .......J4.4..q.B
00000E60: 79 49 A8 35  16 6D 61 C2  52 AE 36 A7  A1 39 D6 47 ; yI.5.ma.R.6..9.G
00000E70: 05 8F 25 AF  AE C5 D2 10  60 68 40 5F  55 23 D5 1C ; ..%.....`h@_U#..
00000E80: ED 0A 47 77  7B 7A E1 89  3E 7B 67 54  3F 47 B4 77 ; ..Gw{z..>{gT?G.w
00000E90: 2B 21 D8 63  E4 90 FD DD  12 77 2C 7C  4E 5E 15 C2 ; +!.c.....w,|N^..
00000EA0: 4C E3 52 A2  96 7C 92 10  62 34 BA 81  59 34 A5 EB ; L.R..|..b4..Y4..
00000EB0: A3 BB 8E D0  DA C2 7F D4  50 38 2C 59  3E B1 C9 7C ; ........P8,Y>..|
00000EC0: 34 23 93 E3  3E 38 A1 B1  51 67 76 6B  F3 FE 1B C3 ; 4#..>8..Qgvk....
00000ED0: 9A 7A 1F 91  7F 44 69 70  AB A4 B6 F8  0F 04 8A 0C ; .z...Dip........
00000EE0: B2 F0 18 07  AF D7 8F 60  28 3E A8 6C  E3 B1 E4 6B ; .......`(>.l...k
00000EF0: 32 EA 73 01  73 37 70 00  6A 06 58 40  56 6C 19 32 ; 2.s.s7p.j.X@Vl.2
00000F00: 00 1C B3 8D  99 8B 9A 2E  49 B4 BF 5D  30 6F E9 9F ; ........I..]0o..
00000F10: 35 D7 45 70  90 59 59 9F  92 2C 79 3C  2E A0 11 0D ; 5.Ep.YY..,y<....
00000F20: B4 76 28 E3  14 34 2B 60  AD 6C 59 4F  09 D0 64 58 ; .v(..4+`.lYO..dX
00000F30: A0 36 7B E9  F8 5B C6 15  07 38 19 EB  A8 8C 24 49 ; .6{..[...8....$I
00000F40: 92 D9 06 83  B8 73 41 7F  6F 20 49 AE  2C 13 86 3C ; .....sA.o I.,..<
00000F50: 72 AC 59 C3  BB A0 22 FD  AB 86 2E 96  FF 5B 8B A5 ; r.Y..."......[..
00000F60: 65 4C 4D 5C  C4 74 22 E6  BD C7 5F F3  64 0D 9F 67 ; eLM\.t"..._.d..g
00000F70: 99 DC B6 D9  5E E9 55 98  E5 D3 72 D3  59 BF F0 70 ; ....^.U...r.Y..p
00000F80: 1F E3 F5 2F  CF B7 15 16  AF CD A4 D5  77 31 C8 DB ; .../........w1..
00000F90: CE 84 B0 95  AC 8A A7 87  A5 BF CB E1  B1 77 C9 5D ; .............w.]
00000FA0: 9B B4 ED 7F  77 F6 06 F0  71 77 97 B0  62 33 D1 4C ; ....w...qw..b3.L
00000FB0: 75 3D 2B 63  3B C0 B5 B0  67 2D 99 6D  A3 A3 D8 FA ; u=+c;...g-.m....
00000FC0: 06 AA 1E DB  DC 9C 3E BC  5A 1B 36 9B  3E AC 85 E1 ; ......>.Z.6.>...
00000FD0: 3B 76 EC 35  D7 23 EB 6B  C3 87 B6 1B  C8 E6 E0 14 ; ;v.5.#.k........
00000FE0: 67 AF CA 98  9D F8 9E 65  2B 86 ED 9E  EC AA 13 59 ; g......e+......Y
00000FF0: FE FB FE AE  35 B4 EE 9C  75 E6 E6 05  B1 9C 5F 2F ; ....5...u....._/

C:\wubi\tools>
C:\wubi\tools>fstest inode C:\#0x575DB
Type: Directory
Base: 0x5
Attr:
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=19050496)
    2669208+1736

C:\wubi\tools>
C:\wubi\tools>fstest inode C:\#0x592DF
Type: Directory
Base: 0x5
Attr:
  $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=0)
    2670944+1616

```

Not a lot I understand in that lot,not knowing the innards of ntfs...

---

### Post by bean123 on 2007-06-12
Fix another bug in fstest, it should be much faster now.

---

### Post by CrazyGuy123 on 2007-06-12
Yep, that is much faster, and also removes the error after listing the root directory (the ntfs error 18 )

---

### Post by Computer Guru on 2007-06-12
Bean, does this release work with the old GRLDR.mbr?

---

### Post by bean123 on 2007-06-12
> **Computer Guru said:**
> Bean, does this release work with the old GRLDR.mbr?

Yes, grldr.mbr and grldr are independent, they don't need to be of the same version. but it's recommended to replace grldr.mbr with the one in #8, because it fixes the non-resident $BITMAP problem.

---

### Post by ago on 2007-06-12
CrazyGuy123 ,

Thanks a lot for the report. It was extremely heplful and we'll take it into account. I wish we had more like that! Thanks also to bean123!

---

### Post by ago on 2007-06-12
> **CrazyGuy123 said:**
> 
Test 1:
Two identical PC's, one running a fresh Wubi installation, one running a fresh Ubuntu installation (on a real partition).  Comparing the speed of them, the Wubi one is MUCH slower, by a factor of about 5x.  I don't know how to debug the problem, but for example when running updates it doesn't appear the system is disk or cpu bound (disk access is very infrequent, and CPU never rises above 20%).  I did notice a lot of swap usage, more than I'd expect.  I suspect DMA is off for the disk drive, but I don't know how to find out.  (and it seems odd when dma is on for the other pc with identical hardware)  Also, I seemed to get a slight performance improvement by increasing the priority of the ntfs-3g process to -19.   This is old hardware (1997), so no extra drivers have been installed as none seem required.

hdparm -I

try also to reduce/eliminate use of swap and see if that helps. Note that latest minefields have some settings to reduce performance in order to improve robustness (since many people seem to be hard booting more often than they should). See if you have a lupin session in /etc/sysctl.conf, try to comment it out. 

> Test 2:
On a vista PC, the bootloader installation doesn't work, as of Wubi-7.04-minefield-194.53.exe.  Simple solution, the path the installer used for bcdedit was "wubi\boot\winboot\wubildr.mbr", when it should be "\wubi\boot\winboot\wubildr.mbr" - changing that made it work.
I'll check that

> Also, I see the installer uses a custom app to add the bootloader.  Do the devs realise you can just add registry entries to HKEY_LOCAL_MACHINE\BCD00000000\OBJECTS?  Although Microsoft use a complex layout of those registry keys, you can just pick the one involved with WUBI and export it to a .reg file.  Then have the installer just add that reg file to any system where you want it installed.  Although the long id number is randomly generated, it is no harm to have them the same for everybody, and it makes uninstallation easy (just delete that registry key)
Most devs don't have vista... I'll pass this on, it seems a reasonable suggestion.

> Test 3:
On a PC with a HD (NTFS formatted by vista), and the vista bootloader, the wubildr.mbr can't find the wubildr file.  It does exist, but can't be found.  It's the same error as many other people (from memory)  "try (hd0,0) ntfs5P : 3".  To those with trouble, you can copy wubildr to a floppy disk, and then it'll work.  the FStest1.txt file attached is the results of fstest on this pc.
That's for bean123

> Test 4:
RAID.  Wasn't expecting this to work, but it gets a long way.  vista loader loads wubildr.mbr, which loads wubildr, which reads the menu, and loads initrd and the kernel.  The kernel starts, but about 5 secs into boot it gives up with IO errors saying access attempted past end of block device.  It was trying to access an address about 990GB into my striped (RAID0) array of 2 500GB disks.  It looks like that could easily be fixed with a linux raid driver included in the initrd.  It's an "Intel(R) 82801ER SATA RAID Controller", which is fairly common hardware.
Can you check the linux device under which the raid drive is normally "visible"? It is normally /dev/mapper

> Test 5
bean123

> Test 7:
On the windows installer, when downloading the iso file, the file is progressively allocated, causing significant fragmentation (on my test system it was in ~20,000 fragments, even though the disk had been defragged first).  While fragmentation in itself doesn't cause an issue, it slows down the next part of the installation, as a lot of disk seeks are required.   It also makes the computer make an almost constant disk seek graunchy noise while downloading at 500kbps or more.  Maybe build in a buffer to the downloader code so it only writes to the disk every 5MB or so.  Other downloading apps, like µTorrent have a disk cache to solve this problem - maybe windows write cache isn't good for hundreds of tiny writes.
Good point I'll pass it on to Hampus

> Test 8:
While reinstalling from a pre-existaing iso, the crc check seems to take much longer than necessary, with 100% CPU.  Maybe the algorithm needs some optimisation, or it could do with processing the file in larger chunks.  I don't know how it's done, but I expect NSIS code isn't suitable for hashing due to slow execution speed.  Even if the check is a hash, a SHA1 hash only takes 12 secs for a 700MB file on the same system, whereas the installer takes over a minute, and if it just a CRC32 check, it should be even quicker.  Note this isn't caused by the fragmentation issue above, as I defragmented the file so it was contiguous before trying this.
I'll check that

> Test 9:
I'm sure this has been spotted already, but when updating the system, the lupin-target package needs to be reconfigured, and it spews out a few errors every time about an incorrect syntax in one of the scripts.  Don't have the exact error here, although I can get it if required.
Cam you be more specific?

Thanks again

---

### Post by Computer Guru on 2007-06-12
We discussed the Registry BCD solution here: [http://ubuntuforums.org/showpost.php?p=2822692&postcount=145](http://ubuntuforums.org/showpost.php?p=2822692&postcount=145)


CrazyGuy, do you have Jabber or MSN/WLM?

---

### Post by CrazyGuy123 on 2007-06-12
> **ago said:**
> hdparm -I

try also to reduce/eliminate use of swap and see if that helps.
hdparm indicates dma is on, so it's not that.
swapoff ground the system to a halt.  As I said this is old hardware and it's only got 192Mb of ram so it wouldn't run full gnome with the swap off. I'll give it a few mins and see if it recovers, and if not I'll try with the swap off from the console.
UPDATE:  I used the console when not in gnome to disable swap and the system was usable, although it still behaved like a tortoise.  I've attached a few stats I think you'll be able to interpret better than I can.  Both are taken after swap is off.

> **ago said:**
> 
Most devs don't have vista... I'll pass this on, it seems a reasonable suggestion.

I've already discussed it a bit with "Computer Guru" - he said while it's a nice simple way to do it and appears to work, it's strongly discouraged by Microsoft, because there's some synchronisation problem if there's two vistas installed, but I suspect they don't want people accessing the BCD data directly, because then they can't change the data format in the next release without breaking stuff.

> **ago said:**
> 
Can you check the linux device under which the raid drive is normally "visible"? It is normally /dev/mapper

Unfortuantly this system has never had linux on it so I've no idea where it normally goes.  I'll get a listing of /dev/ in a moment after I've moved some hardware around.
UPDATE:  Yep, /dev/mapper does exist, but I don't really know where to go from there...  I'll send a log if I can figure out how to save it somewhere.

> **ago said:**
> 
Cam you be more specific?
the log:
```

Setting up lupin-traget (1.0) ...
 System startup links for /etc/init.d/cpkernel already exist.
 System startup links for /etc/init.d/fixsendsigs already exist.
 System startup links for /etc/init.d/umounthost already exist.
 System startup links for /etc/init.d/killntfs3g already exist.
/var/lib/dpkg/info/lupin-target.postinst: line 10: return: can only 'return' from a function or sourced script
dpkg: error processing lupin-target (--configure):
 sub-process post-installation script returned error exit status 1

```

Hope that helps.

---

### Post by ago on 2007-06-13
> **CrazyGuy123 said:**
> UPDATE:  I used the console when not in gnome to disable swap and the system was usable, although it still behaved like a tortoise.  I've attached a few stats I think you'll be able to interpret better than I can.  Both are taken after swap is off.
Did you check /etc/sysctl.conf? Disable any lupin/wubi setting and try also to set the swappines in there to 0. You may want to try a light desktop like icewm or openbox.

> Unfortuantly this system has never had linux on it so I've no idea where it normally goes.  I'll get a listing of /dev/ in a moment after I've moved some hardware around.
UPDATE:  Yep, /dev/mapper does exist, but I don't really know where to go from there...  I'll send a log if I can figure out how to save it somewhere.
Basically I need to know the device which is used when you want to mount the target partition. You can use a live CD for that. Also pls try the following script and see if the target device appears in the list (copy the following in a file and run the file with "sudo sh filename").

```

#!/bin/sh
set -e

. /usr/share/os-prober/common.sh

partitions () {
        if [ -d /dev/discs ]; then
                find /dev/discs/ -follow -type b | grep /part
        elif [ -d /sys/block ]; then
                for part in /sys/block/*/*[0-9]; do
                        if [ -f "$part/start" ]; then
                                name="$(echo "${part##*/}" | sed 's,[!.],/,g')"
                                if [ -e "/dev/$name" ]; then
                                        echo "/dev/$name"
                                fi
                        fi
                done
        else
                echo "Cannot find list of partitions!" >&2
                exit 1
        fi

        # Also detect OSes on LVM volumes (assumes LVM is active)
        if type lvs >/dev/null 2>&1; then
                echo "$(lvs --noheadings --separator : -o vg_name,lv_name |
                        sed "s|-|--|g;s|^[[:space:]]*\(.*\):\(.*\)$|/dev/mapper/\1-\2|")"
        fi
}

partitions

```

> the log:
```

Setting up lupin-traget (1.0) ...
 System startup links for /etc/init.d/cpkernel already exist.
 System startup links for /etc/init.d/fixsendsigs already exist.
 System startup links for /etc/init.d/umounthost already exist.
 System startup links for /etc/init.d/killntfs3g already exist.
/var/lib/dpkg/info/lupin-target.postinst: line 10: return: can only 'return' from a function or sourced script
dpkg: error processing lupin-target (--configure):
 sub-process post-installation script returned error exit status 1

```
I'll take care of that. Under what circumstances was lupin-target updated?

> Hope that helps.
Yes it does, thanks a lot

---

### Post by ago on 2007-06-13
> **bean123 said:**
> Fix another bug in fstest, it should be much faster now.

CrazyGuy123, does bean123 latest grldr fix the issue you were having?

---

### Post by ago on 2007-06-14
The new minefield should have the latest grldr, fix the vista path, and the lupin-target package. I did not test it yet though. If you provide me info on the raid0 device I will take care of that too. Hampus is looking into 7 and 8 we'll have that also sorted out.

---

### Post by CrazyGuy123 on 2007-06-14
Sounds great.  The raid is the same one as this ([http://ubuntuforums.org/showthread.php?t=472547&page=2](http://ubuntuforums.org/showthread.php?t=472547&page=2)), so since the issue seems to be the same I've posted details there.  (Havn't run that script yet though)

The latest grldr does fix the issue, yep - works perfectly now.

lupin-target was updated on letting it install all the other updates, but I think it was the installation of new linux kernel headers that triggered it.  After that it tried to install on any package installation as it was marked as "1 package neither installed or removed".

You mentioned disk image corruption on hard reboots.  I've done a bit of testing, and while I can't get anything that can be reproduced every time, I have seen a few occasions where disk corruption occured even though the system hadn't been hard rebooted at all since wubi installation.  I suspect maybe some buffer isn't being flushed on unmount.  Also, on some systems on every bootup, there's a warning that the disk last mount time is in the future, which is then repaired.  That occurs even though the date and time haven't been changed.  Usually the disk last mount time is something silly, like many thousands of days in the future.

Another issue, is that mounting the "usr" and "extra" disks fails on every boot up, which isn't a problem except usplash closes when it sees a mount faliure, which spoils the startup look and feel.  I know I could tell it not to mount those two to get rid of the error, but really that should be the default.  Prehaps another way is needed to make an "extra" disk image.

I'll just give that latest minefield a go. - be back soon.

---

### Post by ago on 2007-06-14
> **CrazyGuy123 said:**
> Sounds great.  The raid is the same one as this ([http://ubuntuforums.org/showthread.php?t=472547&page=2](http://ubuntuforums.org/showthread.php?t=472547&page=2)), so since the issue seems to be the same I've posted details there.  (Havn't run that script yet though)
We'll use the other thread for the raid then

> lupin-target was updated on letting it install all the other updates, but I think it was the installation of new linux kernel headers that triggered it.
hmmm will need to check that. Anyway see if it works with the new minefield

> I have seen a few occasions where disk corruption occured even though the system hadn't been hard rebooted at all since wubi installation.
Please try to confirm that. We'll need to fix it if confirmed.

> Also, on some systems on every bootup, there's a warning that the disk last mount time is in the future, which is then repaired.  That occurs even though the date and time haven't been changed.  Usually the disk last mount time is something silly, like many thousands of days in the future.
Does that occurred on every bootup or only on the first boot after installation?

> Another issue, is that mounting the "usr" and "extra" disks fails on every boot up, which isn't a problem except usplash closes when it sees a mount faliure, which spoils the startup look and feel.  I know I could tell it not to mount those two to get rid of the error, but really that should be the default.  Prehaps another way is needed to make an "extra" disk image.
I'll fix that for next minefield

---

### Post by CrazyGuy123 on 2007-06-14
The new minefield doesn't seem to include the new grldr.mbr/wubildr.mbr.  I successfully installed after changing wubildr.mbr for this file [http://ubuntuforums.org/showpost.php?p=2827526&postcount=8](http://ubuntuforums.org/showpost.php?p=2827526&postcount=8), and then had to rename c:\wubildr to c:\grldr because beans version there is looking for grldr rather than wubildr.  It's very hard to tell the difference between versions in these files.  Is the version number in the file anywhere?


The disk corruption occured without a hard reboot, and with seemingly no cause.  I can usually repeat it with the following:
1. Install wubi + updates
2. boot up + login to desktop
3. power off (properly, with the menu)
repeat steps 2 and 3 up to 20 times.

Some times, usually within the first 10 bootups, the corruption error occurs.  It isn't predictable when it occurs, because sometimes I can get to 20 without it happening.  Note that on some reboots I opened firefox to check this forum and other stuff, so that will have made a few temp files.  After the error occurs, I am prompted to reboot linux, and then it auto-reboots.  From every time after that, I get the "last mount time in the future.  FIXED" message.

The package error with lupin-target no longer occurs.

---

### Post by ago on 2007-06-14
> **CrazyGuy123 said:**
> The new minefield doesn't seem to include the new grldr.mbr/wubildr.mbr.  I successfully installed after changing wubildr.mbr for this file [http://ubuntuforums.org/showpost.php?p=2827526&postcount=8](http://ubuntuforums.org/showpost.php?p=2827526&postcount=8), and then had to rename c:\wubildr to c:\grldr because beans version there is looking for grldr rather than wubildr.  It's very hard to tell the difference between versions in these files.  Is the version number in the file anywhere?
You can just checksum grldr vs wubildr. But I am using #16 not  #8:

[http://ubuntuforums.org/showpost.php?p=2828562&postcount=16](http://ubuntuforums.org/showpost.php?p=2828562&postcount=16)

> The disk corruption occured without a hard reboot, and with seemingly no cause.  I can usually repeat it with the following:
1. Install wubi + updates
2. boot up + login to desktop
3. power off (properly, with the menu)
repeat steps 2 and 3 up to 20 times.

When you power off do you have I/O errors? You should have a higher "hit rate" if you leave a process that writes to disk open when you reboot.

> After the error occurs, I am prompted to reboot linux, and then it auto-reboots.  From every time after that, I get the "last mount time in the future.  FIXED" message.
Are there other symptoms other than that? Like ntfs/ext3 corruption? 
For the time in the future see [https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/43239](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/43239)

> The package error with lupin-target no longer occurs.
Good, one less. Can you check if lupin-target is uninstalled? It should stay there.

---

### Post by CrazyGuy123 on 2007-06-14
#16 doesn't include the .mbr version, so I couldn't use that - did you just use the first 8kb's worth?

I get loads of IO errors all over the place, but they're all referring to the RAID on this same machine.  I'll keep an eye out for next time it happens and see.  One thought, since ext3 on the loop image uses journalling, doesn't that mean that for it to become corrupted, something must have been written out of order?

Also, I suspect the time issue may be the key, because during installing updates, I am asked to set the correct time zone (prehaps because it's not preseeded properly...), and the time issue frequently occurs after that.  Maybe the fixing of the time by fsck is actually corrupting the drive?  I'll try and do a bit more investigation with those clues.

I haven't seen any ntfs corruption, but since it's writing to a single file without changing it's size, I wouldn't expect to.

---

### Post by ago on 2007-06-14
> **CrazyGuy123 said:**
> #16 doesn't include the .mbr version, so I couldn't use that - did you just use the first 8kb's worth?
I used the mbr from the official release 6/6 and grldr from #16. You can try that combination, or put the wubi.mbr from #8. I'll update the mbr as well in next release.

> I get loads of IO errors all over the place, but they're all referring to the RAID on this same machine.  I'll keep an eye out for next time it happens and see.  One thought, since ext3 on the loop image uses journalling, doesn't that mean that for it to become corrupted, something must have been written out of order?
It's still not clear to me what the symptoms are: ntfs corruption? ext3 corruption? timestamp in the future?You seem exclude ntfs corruption, then what are the ext3 issues exactly? Is the ext3 corrupted but fixeable, or is it the journal which is corrupted and ext3 cannot be fixed at all?

> Also, I suspect the time issue may be the key, because during installing updates, I am asked to set the correct time zone (prehaps because it's not preseeded properly...)
What should be your timezone? You should not be asked anything during installation

---

### Post by CrazyGuy123 on 2007-06-14
I should be in a london timezone, bu immediatly after installation, the timezone is set to "Unknown".  I don't know if timezone preseeding from windows should be working at the moment, but if it is, there's something wrong with it, at least for london timezones.

More importantly, I've been doing a few more trial runs and found out more worryingly, that even with no hard reboots, disk corruption to the underlying disk does occur.  Whats interesting is when it happens.  Here are my steps (not repeated):

Install wubi
system reboots at end of windows part of install
system reboots at end of d-i part of install
get to working desktop
install updates, and use firefox
reboot - select windows at bootloader
didn't do anything major in windows (web browsing and word docs)
reboot
Boot code corrupted.

I'm not yet sure if it's the partition table thats been corrupted, the MBR, or the partition boot code.  I know I can probably fix it with windows recovery tools, but I want to know whats been written there first, and to where, so thats what I'm trying to find now.

The thing that surprises me is that the boot code vanished, and the last OS running was windows.  I believe that points to the fact that it must have been windows that caused the corruption.  The thing is newer windows versions are pretty rock solid on their disk drivers, and don't even mind hard reboots at all, and other than messing with partitioning tools, I've never heard reports of a boot sector vanishing.  The other thing is I'm not the first person on this forum to witness this - there have been other people who've reported having a non-booting system, which shouldn't be the case when wubi doesn't touch the boot code.

If it actually is the boot sector, being sector 0, does rather point to a code bug rather than a random hardware issue.

As far as I can see, this points to only 2 causes:
1.  Windows happened to corrupt the disk by chance
2.  Some change made by wubi/ntfs3g triggered a bug in windows to corrupt the boot code.

1   seems unlikley since this isn't a one-off incident
2.  seems unlikley since ntfs-3g is well tested.

The only code paths I can see as not being well tested in ntfs3g are:
1. using non-zeroed files - maybe this is a bit more complex than we think, and ntfs-3g may not support them fully since non-zeroed files are vary rare for other purposes.
2.  using ntfs to host a loop file - presumably that means a non-standard unmount system, which may be less tested.
3.  using ntfs-3g on vistas newer version of ntfs, which may have structure changes.

I'm going to continue to investigate to see if I can find out exactly whats been changed on this disk that causes this particular issue, because if it's been overwritten by a file fragment it may give us a clue where to look next.

It would be good if we could contact the other people with this issue, and see if just before they had the problem the last OS they ran was windows or ubuntu.

---

### Post by ago on 2007-06-14
> **CrazyGuy123 said:**
> I should be in a london timezone, bu immediatly after installation, the timezone is set to "Unknown".  I don't know if timezone preseeding from windows should be working at the moment, but if it is, there's something wrong with it, at least for london timezones.
Do a fresh installation and copy c:\wubi\install\preseed.cfg. What is in there for the timezone?

> install updates, and use firefox
reboot - select windows at bootloader
didn't do anything major in windows (web browsing and word docs)
reboot
Does that happen also when you do not install the updates?

> Boot code corrupted.
Can you be a bit more explicit?

> The thing that surprises me is that the boot code vanished
What do you mean by that? What vanished? Do you see Ubuntu in the menu? What happens when you select it? You cannot boot windows either? What happens when you run disk checking utilities?

> and the last OS running was windows
Can you do a test without using windows at all? Also that seems to exclude mbr/ntfs corruption

> I've never heard reports of a boot sector vanishing.
There is a full industry about recovering windows, fixing mbr & co...

> The other thing is I'm not the first person on this forum to witness this - there have been other people who've reported having a non-booting system, which shouldn't be the case when wubi doesn't touch the boot code.
I do not see how that is possible. Particularly I do not see how wubi can cause boot corruption if the last OS running was windows. 

> 2.  Some change made by wubi/ntfs3g triggered a bug in windows to corrupt the boot code.
That might be, but it would be quite unlikely. 

> The only code paths I can see as not being well tested in ntfs3g are:
1. using non-zeroed files - maybe this is a bit more complex than we think, and ntfs-3g may not support them fully since non-zeroed files are vary rare for other purposes.
Not sure how is it possible for old data to affect current data. Once the image is correctly pre-allocated whether it is zeroed or not should not make much difference. But you can check that by generating a zeroed file and replacing system.virtual.disk

> 2.  using ntfs to host a loop file - presumably that means a non-standard unmount system, which may be less tested.
That makes the hosted filesystem more fragile, but hardly the hosting filesystem.

> 3.  using ntfs-3g on vistas newer version of ntfs, which may have structure changes.
That might be, but we should still have some bug reports by now.

---

### Post by CrazyGuy123 on 2007-06-14
Like you said, most of the possible causes are unlikley, which is what makes it more interesting.

I've got a dump of the first 10MB of the disk, and been looking through, it seems that sector 0 appears to be some unidentified boot code, which is getting executed on boot, and the only strings in it are generic things like "No Operating System".

Sector 1 and onwards seem to be grub - no idea how they got there, but since that area is outside the only partition, they aren't formatted with the rest of the disk so they could've been there years unused.

Thje partition table appears intact.

The partition boot code I havn't found yet.  I thought it was the first sector of the partition as shown in the partition table, but that seems to just point to what looks like part of the transaction log orMFT or something (it has fragments of file names in).  I suspect I'm starting counting sectors from the wrong place or something.  I'll research it further...

---

### Post by ago on 2007-06-14
back on grldr, can you please test with grldr provided in post #16?

I am using grldr.mbr from #8 and grldr from #16. Can you please see if that works for you? It should make no difference from the minefield.

---

### Post by CrazyGuy123 on 2007-06-14
OK - I got it working now, and took another disk image of the first few MB.  Did a compare and there's hundreds of differences, but I think the repair tool I used (from a vista boot dvd) probably mounted it, which will have changed loads of timestamps etc.  I'll go through the file with a fine toothcomb later...

Using #8 (ldr.mbr) and #16 (ldr) works.

Using #8 (ldr.mbr) and (ldr) from the minefield works.

Using (ldr.mbr) from the minefield and (ldr) from the minefield did not.

I think the issue with the minefield (as of this morning) was that the ldr file was fine, but the ldr.mbr file was old.

---

### Post by ago on 2007-06-14
hmmm not sure about grldr... anyway new minefield is out 207.57. Can you please test grldr again? Also the /usr /extra problem should be addressed. See also if there is any improvement with raid (unlikely).

---

