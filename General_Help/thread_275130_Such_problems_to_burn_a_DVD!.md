---
title: "Such problems to burn a DVD!"
date: 2006-10-10
forum: General Help
---

### Post by motin on 2006-10-10
Hmmm... It was almost impossible to burn a folder of mine to a DVD. 

The folder has about 15-20 subfolders, each with about 1000 pictures in them. 

I do not really know if it is this folder which is the central problem, but it looks like it is problematic in some way... Here is what happens if i try to burn 3 folder to a DVD, one of them being the above mentioned folder:

[SIZE="5"]k3b[/SIZE]: Compilation i k3b works great, and I can save the project. But pressing BURN just yields 

```
System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-27-686
Devices
-----------------------
HL-DT-ST DVD-RW GWA-4082N CC15 (/dev/hdb, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

K3b
-----------------------
Size of filesystem calculated: 2285431

Used versions
-----------------------
growisofs: 5.21

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdb obs=32k seek=0'
:-( Failed to change write speed: 5540->11080

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdb=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2285431 -dvd-compat -speed=4 

mkisofs
-----------------------
2285431
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
Using ABSOLUTE_NUMBER_ONE_1984_198000 for  Till DVD-R/blacklisted-mp3/Various Artists/Absolute Number One 1984-1989 (disc 2) (Absolute Number One 1984-1989 (disc 1))
Using ABSOLUTE_NUMBER_ONE_1975_198000 for  Till DVD-R/blacklisted-mp3/Various Artists/Absolute Number One 1975-1983 Cd2 (Absolute Number One 1975-1983 CD1)
Using WINDOWS_2000_AND_XP_NETW000.EXE;1 for  Till DVD-R/n400c Drivers/ris/Windows 2000 and XP Network Adapter Driver Set - PRM2KXP.EXE (Windows 2000 and XP Network Adapter Base Drivers - PRM2KXPM.EXE)

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid Arkiv DVD 1 - 2006 -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-motin/k3bQj4mRb.tmp -rational-rock -hide-list /tmp/kde-motin/k3b9rA4Ob.tmp -joliet -hide-joliet-list /tmp/kde-motin/k3bHzbYoa.tmp -full-iso9660-filenames -disable-deep-relocation -iso-level 2 -path-list /tmp/kde-motin/k3bTvJTnb.tmp 

```

One more user has the same problem with the same DVD-writer and k3b here: [http://www.linuxquestions.org/questions/showthread.php?p=2406873](http://www.linuxquestions.org/questions/showthread.php?p=2406873)

[SIZE="5"]Gnomebaker[/SIZE]: I can add folders with not too many files in them, but as fast as I try to add my folder with thousands and thousands of files, it just goes up to 100% cpu usage for ages and then sometime sooner or later the gnomebaker process crashes. Burning the other folders works though. But I cannot burn my precious folder, not even make an iso of the disc. 

[SIZE="5"]Graveman[/SIZE]: Looks nice and handles the compilation fine, but the burning dialog always halts quickly with an "Input/Output error". Even trying to produce an iso produces an error. Gravemen to the grave that is... 

[SIZE="5"]Nautilus[/SIZE]: Nautilus needs 4.3 gb to make an iso, so I stuffed around stuff long enough to make the space free, and then produced an iso. This iso when mounted acts just as I want it to, but after I burned it with Gnomebaker, only one of the three folders were to be found, not including my mentioned folder. 

I do not want to tar my folder since that fold make it almost inusable, having to untar foles before looking at them (Photos). I do not want to split my folder into many small ones as I will be producing more and more of these files and need a long-lasting solution to this. 

I do not want to burn the iso as a data-disc (a data-disc with the iso-file on it that is)... 

I could copy the iso to my FAT32 (with a _lot_of stuffing around files first) and burn it from windows but I didn't want to. 

In the end I burned the iso with k3b, and that worked, albeit sloowly (about 2-3x on my 8x burner). Nautilus -> ISO -> k3b -> Disc seem to be the only way to burn a DVD on this computer through Ubuntu. 

This is just ventilation of thoughts and no replies are needed, but feel free to comment, share your experience.

---

