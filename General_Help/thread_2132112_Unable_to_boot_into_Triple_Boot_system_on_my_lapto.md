---
title: "Unable to boot into Triple Boot system on my laptop."
date: 2013-04-03
forum: General Help
---

### Post by archp2009 on 2013-04-03
I have (I should say had) a triple boot - Win7, Mint 14, Ubuntu 12.04 on my laptop.  At the moment I am unable to boot into anything because I am getting the grub restore prompt.  This problem started with a 57gb partition on my hard drive that came up as unusable in Linux which I was unable to use to increase the size of the Win 7 volume either, so I was trying to change it to a small basic volume for storage.  I was prompted to change one of the other partitions from primary to logical.  I changed one of the administrative Win7 partitions from primary to logical. It could have been PQ Service or the other one (can't recall the name) that gets installed with pre-installed Win 7 setups. By doing that I screwed up the boot numbers (letters) and got grub restore (no boot). I can still see all the partitions from inside a live dvd of either mint, ubuntu or pinguy, but when I try to install Peppermint 3, I only see one large partition marked unallocated. None of the other linux partitions show up.  I have tried restoring the grub using the boot repair utility in the Pinguy live CD but all it did was to remove grub. I couldn't find a boot repair utility on either of the other dvd's  Would you please help me get my grub restored and my laptop running again.  Please let me know what other technical information you need to help me. Please spell out what I need to do.  I haven't been at Linux for a few years and I want to stay interested.  Thanks so much.

---

### Post by oldfred on 2013-04-03
You can add the ppa and download into your existing liveCD/DVD/Flash.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by archp2009 on 2013-04-03
I really appreciate this reply.  It gives me something to get my teeth into.  Unfortunately the local time is 11 p.m. and I was about to retire for the day and I have to travel 400 miles tomorrow leaving early in the morning.  I will do the work and get back to you tomorrow evening or Friday morning.

---

### Post by archp2009 on 2013-04-05
[http://paste.ubuntu.com/5679908/](http://paste.ubuntu.com/5679908/)

---

### Post by archp2009 on 2013-04-05
I tried doing boot-repair but the terminal hung after the second line with ldconfig deferred processing.  Please advise as to what I should do from here.  Thanks again.

---

### Post by archp2009 on 2013-04-05
I tried doing the grub repair again and this time it gave me a choice of installing grub to the first or 15th partition.  I chose the first and it came back and said, "You have chose not to install grub." and didn't do so.  I didn't think the 15th partition would work but I can try it the next time.

---

### Post by oldfred on 2013-04-05
You will not be able to do much until you fix this.

 /dev/sda1 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda3

I would try fixparts even though it does not work on overlapping partitions. But yours is more the extended partition that is the issue. Did you use Windows tools to edit partitions? 

      
 To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

You also have 3 swap partitions, you should only need one, unless hiberating three different systems. And when multi-booting hibernation is not normally recomended.

If you wrote grub to sda1 you may have damaged Windows. All NTFS partitions have to have a NTFS boot sector not grub in the boot sector. You can use testdisk to restore the backup boot sector that NTFS has.

IF fixparts does not work then testdisk may rewrite partition table also.

      
 As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by archp2009 on 2013-04-05
Sorry this is way over my head.  I don't have a picture in my head of  what I need to do.  How do you tell that the partitions are overlapping?  .delete Stray gpt data from MBR drives - I don't know any linux  abbreviations . I knew about the duplicate swap files but they're only  2gb or less each.   Total reinstallation of both Linux distros sounds  easier to me.  And you say overlapping partitions can't be fixed.   How  can I attempt to restore the Windows 7 boot loader from a Win 7 install  disk or repair disk w/o regard to either of the Linux systems?  I do  have Pinguy on another computer which, all things considered is more  than enough for the nerves of this user. I hate Grub and Grub 2 is worse  IMO.  With both you can't change anything w/o creating a heavy paper  weight and having to restore grub which doesn't always work.  When  Windows 7 comes pre-installed it creates 2 other partitions besides  Win7.  What I did  wrong was to change the first of these two partitions  from primary to logical. Is there a way to change that back to primary  before attempting the bootloader restore?  Is that necessary?  I created  the unallocated spaces for LInux using Easeus.  I think it was Win 7  disk mgt that I used to change the system  partitiion from primary to  logical. It was only a right click of the mouse and "change to logical"  did not compain.  In 40 years I have never previously heard of  overlapping partiitions.   I have a backup image of Win 7 on an external  hard drive but the Win 7 restore image function has not worked for me  previously. It may relate to insufficient usb power to the hard drive.   Can I recover select partitions from a Win 7 backup image without  restoring the whole image which is likely to fail. I have Gparted  0.14-6-i486.  Haven't hear of fixpart. Will use as last resort.  Do you  know for a fact that my Windows 7 is irreparably damaged. Thanks for  your patience and understanding.

---

### Post by archp2009 on 2013-04-05
I need a step by step totally idiot proof guide.  I am a certifiable Linux idiot. Assume I am 12 years of age and installed Linux for the first time.  My Windows data (images and video) are more important to me.  No data on the Linux whatever. Most ot the images and data may be also backed up on dvds but not sure. Are you totally sure the FAT are damaged? I meant to say Partition tables.

---

### Post by archp2009 on 2013-04-05
I need a step by step totally idiot proof guide.  I am a certifiable Linux idiot. Assume I am 12 years of age and installed Linux for the first time.  My Windows data (images and video) are more important to me.  No data on the Linux whatever. Most ot the images and data may be also backed up on dvds but not sure.

---

### Post by archp2009 on 2013-04-05
I downloaded the latest edtion of GParted FDisk.  This seems like it has no GUI.  I will need to study the tutorial and pray a lot.

---

### Post by oldfred on 2013-04-05
See line 141 in BootInfo report. And if you then look at all the starts and ends of your partitions and the start & end of the extended partition you will see they overlap. 
Part of partition rules are sda1 thru sda4 are primary partitions. Any one primary partition may be the extended partition and you can have many logical partitions inside the extended. Logical partitions always start at sda5. All logicals have to be inside extended and there can of course be no overlap, or else you are writing different data into the same sectors on the drive as two different partitions.

The fixparts site has info on running program and it is pretty automatic. If it is just readjusting start & end of extended partition it may just do that automatically, but you do have to commit the changes with a w. Be sure to backup partition table first, so then if something goes totally awry you can restore current partition table.

 Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by archp2009 on 2013-04-06
In the backup command 

# [B]sfdisk -d /dev/sdc > parts.txt
what do I change sdc to for my system.  I currently get sfdisk: cannot open /dev/sdc for reading

[/B]

---

### Post by archp2009 on 2013-04-06
The gdisk I downloaded was for Windows!  Will look again for Ubuntu.

---

### Post by archp2009 on 2013-04-06
[http://download.opensuse.org/repositories/home:/srs5694/xUbuntu_10.10/](http://download.opensuse.org/repositories/home:/srs5694/xUbuntu_10.10/)

3rd from bottom 1.3k?

---

### Post by archp2009 on 2013-04-06
> **archp2009 said:**
> [http://download.opensuse.org/repositories/home:/srs5694/xUbuntu_10.10/](http://download.opensuse.org/repositories/home:/srs5694/xUbuntu_10.10/)

3rd from bottom 1.3k?

extracted to desktop - opened to get this which is over my head



--- gptfdisk-0.8.6.orig/debian/rules
+++ gptfdisk-0.8.6/debian/rules
@@ -0,0 +1,88 @@
+#!/usr/bin/make -f
+# Sample debian/rules that uses debhelper.
+# GNU copyright 1997 to 1999 by Joey Hess.
+
+# Uncomment this to turn on verbose mode.
+#export DH_VERBOSE=1
+
+# This is the debhelper compatibility version to use.
+export DH_COMPAT=4
+
+build: build-stamp
+build-stamp:
+    dh_testdir
+
+    # Add here commands to compile the package.
+    make
+
+    touch build-stamp
+
+clean:
+    dh_testdir
+    dh_testroot
+    rm -f build-stamp
+
+    # Add here commands to clean up after the build process.
+    make clean || true
+    # --- end custom part for cleaning up
+
+    dh_clean
+
+install: build
+    dh_testdir
+    dh_testroot
+    dh_clean -k
+    dh_installdirs
+
+    # Add here commands to install the package
+    # The DESTDIR Has To Be Exactly  /usr/src/packages/BUILD/debian/<nameOfPackage>
+    install -Dp gdisk    /usr/src/packages/BUILD/debian/gptfdisk/usr/sbin/gdisk
+    install -Dp cgdisk   /usr/src/packages/BUILD/debian/gptfdisk/usr/sbin/cgdisk
+    install -Dp sgdisk   /usr/src/packages/BUILD/debian/gptfdisk/usr/sbin/sgdisk
+    install -Dp fixparts /usr/src/packages/BUILD/debian/gptfdisk/usr/sbin/fixparts
+    install -Dp -m 0644 gdisk.8  /usr/src/packages/BUILD/debian/gptfdisk/usr/share/man/man8/gdisk.8
+    install -Dp -m 0644 cgdisk.8  /usr/src/packages/BUILD/debian/gptfdisk/usr/share/man/man8/cgdisk.8
+    install -Dp -m 0644 sgdisk.8  /usr/src/packages/BUILD/debian/gptfdisk/usr/share/man/man8/sgdisk.8
+    install -Dp -m 0644 fixparts.8  /usr/src/packages/BUILD/debian/gptfdisk/usr/share/man/man8/fixparts.8
+    install -Dp -m 0644 README /usr/src/packages/BUILD/debian/gptfdisk/usr/share/doc/gptfdisk/README
+    install -Dp -m 0644 NEWS /usr/src/packages/BUILD/debian/gptfdisk/usr/share/doc/gptfdisk/NEWS
+    install -Dp -m 0644 COPYING /usr/src/packages/BUILD/debian/gptfdisk/usr/share/doc/gptfdisk/COPYING
+
+    # --- end custom part for installing
+
+# Build architecture-independent files here.
+binary-indep: build install
+    # We have nothing to do by default.
+
+# Build architecture-dependent files here.
+binary-arch: build install
+    dh_testdir
+    dh_testroot
+#    dh_installdebconf
+    dh_installdocs
+    dh_installexamples
+    dh_installmenu
+#    dh_installlogrotate
+#    dh_installemacsen
+#    dh_installpam
+#    dh_installmime
+#    dh_installinit
+    dh_installcron
+    dh_installman
+    dh_installinfo
+#    dh_undocumented
+    dh_installchangelogs
+    dh_link
+    dh_strip
+    dh_compress
+    dh_fixperms
+#    dh_makeshlibs
+    dh_installdeb
+#    dh_perl
+    dh_shlibdeps
+    dh_gencontrol
+    dh_md5sums
+    dh_builddeb
+
+binary: binary-indep binary-arch
+.PHONY: build clean binary-indep binary-arch binary install
--- gptfdisk-0.8.6.orig/debian/changelog
+++ gptfdisk-0.8.6/debian/changelog
@@ -0,0 +1,6 @@
+gptfdisk (0.8.6-1) stable; urgency=low
+
+  * Initial Release
+
+ -- Rod Smith <rodsmith@rodsbooks.com>  Wed, 9 Jan 2011 15:11:38 +0100
+
--- gptfdisk-0.8.6.orig/debian/control
+++ gptfdisk-0.8.6/debian/control
@@ -0,0 +1,16 @@
+Source: gptfdisk
+Section: Applications/System
+Priority: extra
+Maintainer: Roderick Smith <rodsmith@rodsbooks.com>
+Build-Depends: debhelper (>= 4.1.16), build-essential, uuid-dev, libpopt-dev, libicu-dev
+
+Package: gptfdisk
+Architecture: any
+Depends: ${shlibs:Depends}
+Description: GPT partitioning and MBR repair software
+ Partitioning software for GPT disks and to repair MBR
+ disks. The gdisk and sgdisk utilities (in the gdisk
+ package) are GPT-enabled partitioning tools; the
+ fixparts utility (in the fixparts package) fixes some
+ problems with MBR disks that can be created by buggy
+ partitioning software.

---

### Post by oldfred on 2013-04-06
I think you installed gdisk which is for gpt partitioned drives. We wanted his other tool which is fixparts.

His instructions link to this, but you need to know if running 32 bit or 64 bit operating system and download the version for your system. If Ubuntu then a .deb.
[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/)

My instructions were to change to your drive which I believe is sda, but you have to confirm that is correct.
 sudo sfdisk -d /dev/sda > parts.txt

I think since you have a triple boot system, you were familiar with command line and adding software.

---

### Post by archp2009 on 2013-04-08
I am still waiting for help with step by step help with getting and using Fixparts.  I can't figure out how to backup my partition data (which partition to write to, and I can't figure out how to install Fixparts.  Actually I haven't had much luck installing anything except when given a series of commands to copy and paste into terminal.  When I download something I don't know where to put it nor how to run it.  Is Fixparts available in synaptic manager?  Sorry I was depressed and down on myself due to insomnia and personal stressors in eariler posts.  To be honest I think I could be certified as an intermediate Linux beginner. Thankfully I still have one fairly dependable PC which doesn't depend on Grub to boot.

---

### Post by archp2009 on 2013-04-08
Sorry I wasn't feeling well (discouraged) and down on myself in earlier posts. I am not usually like that.  I really would like t recover as much of the setup incl. the Linux distros as possible  Have I replied to your last post? I don't know how to install fixparts nor which partition to backup my partition data to e.g. sdc.

---

### Post by ppjdee on 2013-04-08
> **darkod said:**
> 1. Get the Debian package for fixparts from the  link on their homepage according to the version you have, 32bit or  64bit:
[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/)

2. When downloaded, right click on the file and select Install with package manager (or similar text). It will install it.

Dont know if that helps you or not.

---

### Post by archp2009 on 2013-04-10
It installed buy says that it has to be run from a terminal.  I have to look back and see if you gave me the terminal command for running it.  Thanks

---

### Post by archp2009 on 2013-04-10
The fixparts program installed but I don't know how to run it from terminal.  It installed with ubunut software package.  I get this for a previous command for backing up destination sudo sfdisk -d /dev/sda > parts.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently. Don't know how to respond to that.  Thanks for your continued patience.  I guess I need to do these partition backups first.  Thanks for your continued patience.

---

### Post by archp2009 on 2013-04-10
sometimes I see my replies and sometimes I don't.  for sda I get 
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > parts.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

---

### Post by archp2009 on 2013-04-10
which mbr command number do I select?

ubuntu@ubuntu:~$ sudo fixparts /dev/sda
FixParts 0.8.4

Loading MBR data from /dev/sda

MBR command (? for help): 

MBR comman? for help): ?   
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit

---

### Post by oldfred on 2013-04-10
Drives have not used cylinders since they went over 8GB, so you can ignore that error on the start of your extended partition.
Try p and see what it says. If it looks correct and only if it looks correct you can use w to write the corrected partition table.

Forum has two servers and sometimes it takes a few minutes before something appears as it has to be sync'd.

---

### Post by archp2009 on 2013-04-11
FixParts 0.8.4

Loading MBR data from /dev/sda

MBR command (? for help): ? 
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 1465149168 sectors (698.6 GiB)
MBR disk identifier: 0x0990D1D5
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *       27650048     27854847   primary              Y      0x07
   2             140488424   1348833464   primary              Y      0x07
   5                  2048     27650047   logical     Y        Y      0x07
   6            1348835328   1349810175   omitted                     0x83
   7            1349812224   1379106815   omitted                     0x83
   8            1379108864   1381060607   omitted                     0x82
   9            1381062656   1390055423   omitted                     0x83
  10            1390059520   1391034367   omitted                     0x83
  11            1391036416   1410566143   omitted                     0x83
  12            1410568192   1414471679   omitted                     0x82
  13            1414473728   1427535871   omitted                     0x83
  14            1427537920   1431295999   omitted                     0x82
  15            1431298048   1465147391   primary              Y      0x83

This is of no use to me at my level of understanding.  Also did not resolve problem regarding backing up partition data to text

---

### Post by oldfred on 2013-04-11
This only backs up partition table, so it could be restored if changes make it worse. But it does not backup data. 
sudo sfdisk -d /dev/sda > parts.txt

If you do not have data backups you should really make an image of the hard drive. Repairs may or may not work.

I do not know why fixparts shows most of your logical partitions as omitted. I would not write that. If testdisk does not show partition table correctly you may have to manually edit the parts.txt file.

Do you have any documentation of your partitions before? This would say that sda1 & sda2 are also inside the extended partition. But Windows will not boot from logicals so I assume the issue is really the start of sda3 or the extended partition. Then sda5 becomes a primary - sda3,  and the extended is really sda4 and starts after sda2's end. It does not matter that sda3 & sda2 are switched or were they really in a different order? 

I would try testdisk and see what it shows. You may be able to drill deeper and see files.
       [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

   repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by archp2009 on 2013-04-11
> **oldfred said:**
> This only backs up partition table, so it could be restored if changes make it worse. But it does not backup data. 
sudo sfdisk -d /dev/sda > parts.txt

If you do not have data backups you should really make an image of the hard drive. Repairs may or may not work.

[COLOR=#ff0000]I have an image of Windows 7 on a usb hard drive.   I had a similar image of Windows 8 on the same drive which I tried at one point to restore using a Windows 8 system restore disk or whatever it's called and I tried to restore it unsuccessfully, so I don't hold up much hope in being able to restore the Windows 7 either.  I figure my odds of being able to replace the Windows boot loader are good at this point.  After doing that I will have an "unusable" 56gb partition on one side of the Win 7 partition or the other which I won't be able to delete or merge with the main partition, but I'm thinking the Windows should still be usable in that state.  Also there is the issue of that I changed the second administrative partition  of the Win 7 from primary to logical.
[/COLOR]
I do not know why fixparts shows most of your logical partitions as omitted. I would not write that. If testdisk does not show partition table correctly you may have to manually edit the parts.txt file.

Do you have any documentation of your partitions before? 
[COLOR=#ff0000]The only thing I remember as being messed up was the unallocated 56gb partition next to the Win7 partition which came up as being unusable.  [/COLOR]
This would say that sda1 & sda2 are also inside the extended partition. But Windows will not boot from logicals so I assume the issue is really the start of sda3 or the extended partition. Then sda5 becomes a primary - sda3,  and the extended is really sda4 and starts after sda2's end. It does not matter that sda3 & sda2 are switched or were they really in a different order? 

I would try testdisk and see what it shows. You may be able to drill deeper and see files.
       [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

   repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[COLOR=#ff0000]Will try Testdisk to see what it shows.[/COLOR]

---

### Post by archp2009 on 2013-04-12
Downloaded testdisk and extracted  - don't know how to run or install.

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package testdisk
ubuntu@ubuntu:~$

---

### Post by oldfred on 2013-04-12
I have always had Universe enabled in my installed systems, so it just works. Maybe live installer does not have Universe enabled.

 enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.

Otherwise download Parted Magic, testdisk is on most repair Linux versions. I often use gparted from parted magic or gparted liveCD anyway.
      
 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by archp2009 on 2013-04-12
I already had parted magic disk but nothing called Test Disk on it.  This is result of disk health test

```
smartctl 6.0 2012-10-10 r3643 [x86_64-linux-3.7.9-pmagic64] (local build)
Copyright (C) 2002-12, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MK..59GSXP (AF)
Device Model:     TOSHIBA MK7559GSXP
Serial Number:    51BLB14HB
LU WWN Device Id: 5 000039 349b82f0f
Firmware Version: GN003J
User Capacity:    750,156,374,016 bytes [750 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Fri Apr 12 15:56:40 2013 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  120) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 191) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1602
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       1053
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       1689
 10 Spin_Retry_Count        0x0033   120   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1026
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       32
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       94
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       10239
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       27 (Min/Max 10/48)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       8269
222 Loaded_Hours            0x0032   097   097   000    Old_age   Always       -       1433
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       313
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1689         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
```
If Selective self-test is pending on power-up, resume after 0 minute delay.

Gparted just shows a single partition of 698 gib unallocated space. sda

---

### Post by archp2009 on 2013-04-12
I went over my frustration limit and decided to go the route of rewriting the Win7 mbr from the rescue disk at the command prompt.  That worked successfully and I am replying from inside Windows.  It is too bad that Windows and Ubuntu do not live together real comfortably for a person like myself who is often not content to leave well enough alone.  Thanks to the forum for trying.

---

