---
title: "Weird GRLDR Error, Possible Bug?"
date: 2007-06-11
forum: General Help
---

### Post by Computer Guru on 2007-06-11
I'm having some issue with someone testing EasyBCD's Wubi support.

GRLDR has been embedded to look for and use \NST\menu.lst

The file exists on his system, but GRLDR cannot see it.

Here is the output from fstest on that machine:

```


----------------------------------------------------------------------------
--------------
C:\>fstest info C:
----------------------------------------------------------------------------
--------------
part_base: 0x800 (1M)
part_leng: 0x3A385000 (476938M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000

----------------------------------------------------------------------------
--------------
C:\>fstest inode C:\$MFT
----------------------------------------------------------------------------
--------------
Type: File
Attr:
 $STANDARD_INFORMATION (0x10) (r,sz=72)
 $FILENAME (0x30) (r,sz=74)
   $MFT
 $DATA (0x80) (nr,sz=144572416)
   6291456+110336,37639680+172032
 $BITMAP (0xB0) (nr,sz=20488)
   6291448+8,488384560+8,9595392+8,9459624+8,521901832+8,555469232+8

----------------------------------------------------------------------------
--------------
C:\>fstest inode C:
----------------------------------------------------------------------------
--------------
ntfs_dir: 17

----------------------------------------------------------------------------
--------------
C:\>Fstest list c:
----------------------------------------------------------------------------
--------------
000099F9         65536  FACTUR~1.LOG
0000003D             0  [PROGRA~1]
00020B8E          1024  .rnd
000033DC             0  [Archivos de programa]
000033DC             0  [ARCHIV~1]
00001D57            24  autoexec.bat
0000F565        162004  bar.emf
00009579             0  [Boot]
00021221            67  boot.ini
000095AD        438840  bootmgr
000095B8          8192  BOOTSECT.BAK
000099FA           160  cone.ini
0000C393             0  [Config.Msi]
00001D58            10  config.sys
00009769             0  [conn]
0000977B             0  [Control de Inventario]
0000977B             0  [CONTRO~1]
000097E5             0  [CursoNet]
0000D264             0  [dell]
0000930B             0  [Dll]
00001D5B             0  [Documents and Settings]
00001D5B             0  [DOCUME~1]
00014506             0  [Downloads]
00014506             0  [DOWNLO~1]
0000A610             0  [Emulator]
00009844             0  [Facturacion]
000099FB       1355776  facturacion.db
000099F9         65536  facturacion.log
00013D33         65536  facturacion.mlg
00009844             0  [FACTUR~1]
000099FB       1355776  FACTUR~1.DB
00013D33         65536  FACTUR~1.MLG
000221C7          4535  fstest.bat
000221C8         39096  fstest.exe
00021F61          6591  fstest.txt
0000FF30             0  [Games]
00021220        178629  grldr
000221C6          8192  grldr.mbr
0000B5CE            34  hcwclear.txt
00000031    2145558528  hiberfil.sys
0000E098             0  [IDE]
0000FB07           568  IDL.log
0000FF97             0  [inetpub]
0002129E             0  IO.SYS
000098B5             0  [JavaProjects]
000098B5             0  [JAVAPR~1]
0002121F          1867  menu.lst
00009821             0  [MSDN]
0002129D             0  MSDOS.SYS
0000DC0D             0  [MSOCache]
00013AD3             0  [MyVideos]
0002196E        178553  NeoGrub
00021A79             0  [NST]
0000ACB0             0  [NVIDIA]
000099B0             0  [Och]
000001E7   -1835483136  pagefile.sys
000099B8             0  [PowerBuilder]
000099B8             0  [POWERB~1]
0000003D             0  [Program Files]
00000115             0  [ProgramData]
00000115             0  [PROGRA~2]
00020B8E          1024  RND~1
0000D0B5           268  sqmdata00.sqm
0000D0B5           268  SQMDAT~1.SQM
0000D0B4           244  sqmnoopt00.sqm
0000D0B4           244  SQMNOO~1.SQM
000095C4             0  [System Volume Information]
000095C4             0  [SYSTEM~1]
00014A70             0  [The Tibetan Book Of The Dead]
00014A70             0  [THETIB~1]
000099E1             0  [Trabajo PRG3 REG3]
0001F834             0  [Trabajo PRG3 REG3 - copia]
000099E1             0  [TRABAJ~1]
0001F834             0  [TRABAJ~2]
000001A0             0  [Users]
00000232             0  [Windows]
0001E2EE             0  [wubi]
00014601           146  YServer.txt

----------------------------------------------------------------------------
--------------
C:\>fstest inode c:\wubi
----------------------------------------------------------------------------
--------------
Type: Directory
Attr:
 $STANDARD_INFORMATION (0x10) (r,sz=72)
 $FILENAME (0x30) (r,sz=74)
   wubi
 $INDEX_ROOT (0x90) (r,nm=$I30,sz=56)
 $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=4096)
   151920+8
 $BITMAP (0xB0) (r,nm=$I30,sz=8)

----------------------------------------------------------------------------
--------------
C:\>fstest inode c:\wubi
----------------------------------------------------------------------------
--------------
Type: Directory
Attr:
 $STANDARD_INFORMATION (0x10) (r,sz=72)
 $FILENAME (0x30) (r,sz=74)
   wubi
 $INDEX_ROOT (0x90) (r,nm=$I30,sz=56)
 $INDEX_ALLOCATION (0xA0) (nr,nm=$I30,sz=4096)
   151920+8
 $BITMAP (0xB0) (r,nm=$I30,sz=8)

----------------------------------------------------------------------------
--------------
C:\>fstest inode c:\wubi\boot
----------------------------------------------------------------------------
--------------
Type: Directory
Attr:
 $STANDARD_INFORMATION (0x10) (r,sz=72)
 $FILENAME (0x30) (r,sz=74)
   boot
 $INDEX_ROOT (0x90) (r,nm=$I30,sz=432)

----------------------------------------------------------------------------
--------------
C:\>fstest list c:\wubi\boot\
----------------------------------------------------------------------------
--------------
0001E377             0  [grub]
0002120C       7934327  initrd
0002120D       1745100  linux
0001E37C             0  [winboot]

----------------------------------------------------------------------------
--------------
C:\>fstest comp c:\grldr
----------------------------------------------------------------------------
--------------
File size : 178629
Comparing
Succeed

----------------------------------------------------------------------------
--------------
C:\>fstest comp c:\wubi\boot\linux
----------------------------------------------------------------------------
--------------
File size : 1745100
Comparing .
Succeed

----------------------------------------------------------------------------
--------------
C:\>fstest comp c:\wubi\boot\initrd
----------------------------------------------------------------------------
--------------
File size : 7934327
Comparing .......
Succeed
Warning: reading beyond the 137G limit

C:\>fstest inode c:\nst
Type: Directory
Attr:
 $STANDARD_INFORMATION (0x10) (r,sz=72)
 $FILENAME (0x30) (r,sz=72)
   NST
 $INDEX_ROOT (0x90) (r,nm=$I30,sz=256)

C:\>fstest comp c:\nst\menu.lst
File size : 407
Comparing
Succeed

```

Though his HD is > 137GB, and fstest points out that initrd will not be loadable. BUT, it doesn't give any errors whatsoever for c:\nst\menu.lst, which is where GRLDR is failing.

Do you have any idea what can be wrong? Is this an NTFS bug?

---

### Post by bean123 on 2007-06-11
Maybe the NSL directory is over 137G, try :

fstest list C:\NSL\

fstest comp C:\NSL\menu.lst

---

### Post by CrazyGuy123 on 2007-06-11
bean:
Is 137G a limitation of GRUB, or a limitation of the BIOS calls?  If it's the BIOS calls, how come the windows bootloader can load stuff beyond that?  It loads about 30 drivers etc. before the disk driver, so it must be using BIOS calls then, and I'm sure there's no restriction on where those files can be placed.

---

### Post by bean123 on 2007-06-11
It's a BIOS related problem. XP can boot because the startup files are normally at the beginning of the disk.

---

### Post by CrazyGuy123 on 2007-06-11
It surely can't be just chance that millions of XP pc's happen to all have every single one of the boot files near the start of the disk - quite a lot of people install XP to an already nearly full NTFS disk where the boot files couldn't be placed anywhere reliably, unless XP has some mechanism for putting some kind of tag on a file saying it must go at the start of the disk.

If this is the case, and wubi boots by moving it's files near the start of the disk, the installer could very easily move the files to the start, because the windows defragmentation API's allow files to be moved around.  I wouldn't call that reliable though because it's easily possible another program, like a backup utility or a defrag program could move them post installation.

---

### Post by Computer Guru on 2007-06-11
> **bean123 said:**
> Maybe the NSL directory is over 137G, try :

fstest list C:\NSL\

fstest comp C:\NSL\menu.lst

That's in the first post (NST, btw, not nsl)

See the very last output:

comp c:\nst\menu.lst

it comes out OK

---

### Post by tinybit on 2007-06-11
In the first post, it was "fstest inode c:\nst", but Bean needs "fstest list C:\NST\".

---

### Post by tinybit on 2007-06-11
> **CrazyGuy123 said:**
> It surely can't be just chance that millions of XP pc's happen to all have every single one of the boot files near the start of the disk - quite a lot of people install XP to an already nearly full NTFS disk where the boot files couldn't be placed anywhere reliably, unless XP has some mechanism for putting some kind of tag on a file saying it must go at the start of the disk.


I believe that is just the case. At least the NTLDR(or bootmgr) file should be accessible by BIOS. And XP has to ensure that. So wubi should move files if needed. All files that need to be  read by grub should also be readable by BIOS.

---

### Post by bean123 on 2007-06-11
> **CrazyGuy123 said:**
> It surely can't be just chance that millions of XP pc's happen to all have every single one of the boot files near the start of the disk - quite a lot of people install XP to an already nearly full NTFS disk where the boot files couldn't be placed anywhere reliably, unless XP has some mechanism for putting some kind of tag on a file saying it must go at the start of the disk.

If this is the case, and wubi boots by moving it's files near the start of the disk, the installer could very easily move the files to the start, because the windows defragmentation API's allow files to be moved around.  I wouldn't call that reliable though because it's easily possible another program, like a backup utility or a defrag program could move them post installation.

In fact, there is a simple way to verify it. Create a partition whose starting address is above 137G, and install XP. Then, move the disk to a machine not supporting large disk, and see if it can boot sucessfully.

---

### Post by bean123 on 2007-06-11
> **Computer Guru said:**
> That's in the first post (NST, btw, not nsl)

See the very last output:

comp c:\nst\menu.lst

it comes out OK

That's strange, fstest and the ntfs driver use the same code, if fstest can read it, so can grldr. You type command:

cat (hd0,0)/nst/menu.lst

in the grub console, see if it can read the content of /nst/menu.lst

---

### Post by bean123 on 2007-06-11
> **tinybit said:**
> I believe that is just the case. At least the NTLDR(or bootmgr) file should be accessible by BIOS. And XP has to ensure that. So wubi should move files if needed. All files that need to be  read by grub should also be readable by BIOS.

Yes, wubi should do an extra step of moving boot files as low as possile, if the partition cross the 137G boundary. In fact, it's not difficult to implement. First use FSCTL_GET_VOLUME_BITMAP to get a map of the clusters that are free in a volume, then FSCTL_GET_RETRIEVAL_POINTERS to get the cluster map for a specified file, finally FSCTL_MOVE_FILE to move the clusters of a particular file to a currently unallocated position on the volume. Here is a doc on this:

[http://www.microsoft.com/technet/sysinternals/information/diskdefragmenting.mspx](http://www.microsoft.com/technet/sysinternals/information/diskdefragmenting.mspx)

---

### Post by tinybit on 2007-06-12
> **bean123 said:**
> Yes, wubi should do an extra step of moving boot files as low as possile, if the partition cross the 137G boundary. In fact, it's not difficult to implement. First use FSCTL_GET_VOLUME_BITMAP to get a map of the clusters that are free in a volume, then FSCTL_GET_RETRIEVAL_POINTERS to get the cluster map for a specified file, finally FSCTL_MOVE_FILE to move the clusters of a particular file to a currently unallocated position on the volume. Here is a doc on this:

[http://www.microsoft.com/technet/sysinternals/information/diskdefragmenting.mspx](http://www.microsoft.com/technet/sysinternals/information/diskdefragmenting.mspx)

Bean, you can do it. Just create a new utility in grubinst or in grub4dos. I think it is very useful and very important.

---

### Post by tinybit on 2007-06-12
> **bean123 said:**
> That's strange, fstest and the ntfs driver use the same code, if fstest can read it, so can grldr. You type command:

cat (hd0,0)/nst/menu.lst

in the grub console, see if it can read the content of /nst/menu.lst

I don't think it is a strange thing. When you "cat", you use BIOS. But when you "fstest", you are in Windows (and in protected CPU mode) and the normal BIOS is bypassed. So a success in fstest does not mean a success in grub.

---

### Post by Computer Guru on 2007-06-12
OK, so where does that leave us?

If GRLDR via the BIOS fails to load the file, is this a GRLDR error or an NTFS error or a BIOS problem or what?

The $MFT info is in the first post, do I need to ask him to do anything else?

---

### Post by tinybit on 2007-06-12
> **Computer Guru said:**
> 
If GRLDR via the BIOS fails to load the file, is this a GRLDR error or an NTFS error or a BIOS problem or what?

I think it is a BIOS problem(the 137G bug). No solution but by moving files low. If we have no intention to support those buggy BIOSes, we could ignore the problem.

> The $MFT info is in the first post, do I need to ask him to do anything else?

Bean wanted to see the output of "fstest list c:\NST\". I guess it will tell the 137G info.

---

### Post by CrazyGuy123 on 2007-06-12
I might try the 137G test with XP (problem is I don't have any big disks I can format and mess around with).  I presume for a computer with a buggy bios to boot wubi, all the following needs to be before 128GiB:

Bootsector (so partition can't start after 137G)
Every fragment of the MFT, because you can't be certain which fragment the entry you need will be in.
ntldr
ntdetect.com
wubildr
menu.lst
initrd
kernel

Now it can move all the files with beans new found API, and we can be fairly sure the bootsector is before 137G, because usually the first partition is the active one, but how does it ensure all the MFT fragments are before 137G?


According to googleing it, xp can boot fine off disks over 137G as long as a service pack is installed.  Apparantly it was because that service pack enabled "EnableBigLba", but is that only for later in the boot sequence?

---

### Post by bean123 on 2007-06-12
> **CrazyGuy123 said:**
> I might try the 137G test with XP (problem is I don't have any big disks I can format and mess around with).  I presume for a computer with a buggy bios to boot wubi, all the following needs to be before 128GiB:

Bootsector (so partition can't start after 137G)
Every fragment of the MFT, because you can't be certain which fragment the entry you need will be in.
ntldr
ntdetect.com
wubildr
menu.lst
initrd
kernel

Now it can move all the files with beans new found API, and we can be fairly sure the bootsector is before 137G, because usually the first partition is the active one, but how does it ensure all the MFT fragments are before 137G?


According to googleing it, xp can boot fine off disks over 137G as long as a service pack is installed.  Apparantly it was because that service pack enabled "EnableBigLba", but is that only for later in the boot sequence?

We don't need to worry about MFT fragments, if it goes beyond 137G, XP can't boot either.

All services whose "Start" type is 0 is loaded using the int13 bios call, protected mode driver will take over after that.

---

### Post by Computer Guru on 2007-06-12
That's what I'm trying to say: fstest is *not* going past the 137GB limit. Compare:

```
----------------------------------------------------------------------------
--------------
C:\>fstest comp c:\wubi\boot\initrd
----------------------------------------------------------------------------
--------------
File size : 7934327
Comparing .......
Succeed
Warning: reading beyond the 137G limit
```

to

```
----------------------------------------------------------------------------
--------------
C:\>fstest comp c:\nst\menu.lst
----------------------------------------------------------------------------
--------------
File size : 407
Comparing
Succeed
```

`comp` returns a 137GB error for initrd, but *not* for menu.lst - yet GRLDR is getting stuck on menu.lst

---

### Post by bean123 on 2007-06-12
Can you go to the grub console ? If do, what's the result of the following command:

cat (hd0,0)/[TAB]

cat (hd0,0)/nst/[TAB]

cat (hd0,0)/nst/menu.lst

---

### Post by Computer Guru on 2007-06-12
OK, I asked him to test them, will post back soon as I hear from him :)

---

### Post by Computer Guru on 2007-06-12
Aha!

Obviously it would have been useful to know this from the very beginning, but he just told me that it's a *dynamic disk*, and that GRLDR cannot mount (hd0,0).

The BCD - using MS' code - finds, reads, and loads GRLDR without a problem off of the same dynamic disk.
GRLDR cannot load menu.lst from this dynamic disk.

Excellent in-depth info about Dynamic Disks: [http://technet2.microsoft.com/windowsserver/en/library/72c515fa-8acf-4de2-90af-ebca62b27f661033.mspx?mfr=true](http://technet2.microsoft.com/windowsserver/en/library/72c515fa-8acf-4de2-90af-ebca62b27f661033.mspx?mfr=true)

---

### Post by tinybit on 2007-06-12
Maybe we should add a comment in the README, claiming that dynamic disks are not supported.

---

### Post by bean123 on 2007-06-12
> **Computer Guru said:**
> Aha!

Obviously it would have been useful to know this from the very beginning, but he just told me that it's a *dynamic disk*, and that GRLDR cannot mount (hd0,0).

The BCD - using MS' code - finds, reads, and loads GRLDR without a problem off of the same dynamic disk.
GRLDR cannot load menu.lst from this dynamic disk.

Excellent in-depth info about Dynamic Disks: [http://technet2.microsoft.com/windowsserver/en/library/72c515fa-8acf-4de2-90af-ebca62b27f661033.mspx?mfr=true](http://technet2.microsoft.com/windowsserver/en/library/72c515fa-8acf-4de2-90af-ebca62b27f661033.mspx?mfr=true)

GRUB4DOS does not support dynamic disk. However, I believe GRUB2 may support dynamic disk through its lvm module, you can check it out if you're interested.

---

### Post by Computer Guru on 2007-06-12
Well thanks guys, I'll let him known.

Does GRUB itself by any chance support DDs?

---

### Post by bean123 on 2007-06-12
> **Computer Guru said:**
> Well thanks guys, I'll let him known.

Does GRUB itself by any chance support DDs?

It's not very likely.

---

### Post by miraalc on 2011-07-31
Hi guys,

I have no clue why but, I get this weird GRLDR error. :confused:

I am trying to learn linux and one of my friends advised me to get it from ubuntu website and I tried installation with windows and that didn't work out because of this GRLDR error.

I don't know what I should do. I have a 64bit i5 win7 m450@ 2.40 GHz

4gb RAM. I think it install like 17gb data

Please help me!

---

