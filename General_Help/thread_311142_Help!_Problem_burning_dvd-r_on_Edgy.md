---
title: "Help! Problem burning dvd-r on Edgy"
date: 2006-12-02
forum: General Help
---

### Post by william_lee on 2006-12-02
Hi all-

I'm hoping someone can help with a problem that has me at my wit's end.   I am unable to burn DVDs under Edgy.   This is a new install on this machine, so I'm not sure if Dapper would have the same problem.

I am running on an Nvidia Nforce2 mobo (AMD Athlon XP) with an NEC ND-1300A DVD burner.   The burner and media both work fine under Windows XP.

I have installed all applicable packages, and am able to play DVDs and CDs including protected content, and burn CDs without problems.   

However, when I go to burn a DVD (I've tried many different apps) I can hear the drive clicking, and it fails shortly thereafter.   I've done an exhaustive search of the forums, and google, and have been unable to find a solution.

I keep getting an OPC error, and have been unable to get burning working.  In searching the forums, there often doesn't seem to be a solution to this problem.   I'm hoping someone more knowledgeable can help!  

Thanks in advance!

Here is the error log from K3b:

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-386
Devices
-----------------------
_NEC DVD_RW ND-1300A 1.0C (/dev/hdc, ) at /cdrom [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
growisofs: 6.1
mkisofs: 2.1.1a03-unofficial-iconv

growisofs
-----------------------
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
Total translation table size: 0
Total rockridge attributes bytes: 253
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 0
487 extents written (0 MB)
:-[ PERFORM OPC failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error

growisofs command:
-----------------------
/usr/X11R6/bin/growisofs -Z /dev/hdc -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=bufsize:32m -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-root/k3b9jlGza.tmp -rational-rock -hide-list /tmp/kde-root/k3bwG4o0b.tmp -joliet -hide-joliet-list /tmp/kde-root/k3bnCS8kb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-root/k3bSH6JKb.tmp

---

### Post by deep.tinker77 on 2006-12-02
I believe you have to give k3b permission to use the drive. When you open kb3, I believe you have to select your drive and hit the apply button at the bottom. It will change the permissions for your burner.

Edit: I'm sorry for not being clearer, I had the same exact thing happen to me when I installed my system. It should ask you or you can check the prefrences and/or settings when you open up K3b. Good luck.

---

### Post by todak on 2006-12-02
I have found that changing the brand of media helps. DVD burners are like cars. They seem to prefer a particular brand of fuel. Try changing the brand of media you are using and see if that will solve the errors;)

---

### Post by Angellis_ater on 2006-12-03
I have the same problem, fact is that the burners (k3b, brasero, gnomebaker) can't even find my empty DVDs

---

### Post by jaw1959 on 2007-03-21
I'm having a similar problem burning DVDs.  It seems I can burn CDs fine, but not DVDs.  The strange thing is I've burned DVDs using Ubnutu with the same hardware in the same configuration, though I just did a reinstall, and now it doesn't work.  When I try burning with gnomebaker, I click "start" to begin burning the disc, and then it runs for about a second and says: 


Executing 'builtin_dd if=/home/josh/DVD/iso/WAITING_FOR_GUFFMAN.iso of=/dev/hda obs=32k seek=0'
/dev/hda: "Current Write Speed" is 1.0x1385KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

Any ideas?

---

