---
title: "I need a cdrecord expert, something wrong with my libscg"
date: 2005-05-17
forum: General Help
---

### Post by ishtvan222 on 2005-05-17
OK, so i installed ubuntu warty from a cd i got in the mail. Then i upgraded to hoary. Lately ive been trying to burn an iso from the command line and it hasnt been working. So I need to do cdrecord dev=ATAPI -scanbus to find the id of my CDRW. (im not doing scsi emulation) I know this drive works because i have burnt with it in scsi emulation in kernel 2.4.something

[COLOR=Navy]


garber@compaq:~ $ cdrecord dev=ATAPI -scanbus
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
cdrecord: No such file or directory. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
garber@compaq:~ $
[/COLOR]




Now here is what it is supposed to look like:

[COLOR=Red]$ /usr/bin/cdrecord dev=ATAPI -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools at packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.11.6-paobu
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1
'@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'SONY    ' 'DVD RW DRU-510A ' '1.0f' Removable CD-ROM

(other IDs skipped)

[/COLOR]


See mine says "[COLOR=Navy]cdrecord: No such file or directory. Cannot open SCSI driver.[/COLOR]" On most of the examples ive seen it says something like "[COLOR=Red]Using libscg version 'ubuntu-0.8ubuntu1'.[/COLOR]" And then mine does not show the id of my drive. Somewhere i read that libscg is built into cdrecord, but im not sure. Basically, i need to get my CDRW working from the commandline and my cdrecord does not do anything with libscg. But i dont see why i need a scsi driver though. By the way my kernel is 2.6.10-5.

Somebody please help me.

---

### Post by osde.info on 2005-06-02
Try the following

# su -

Discover devices to find your n,n,n
# cdrecord dev=ATAPI -scanbus

Put a pre-record CD in to test reading (replace 1,0,0 with your n,n,n)
# cdrecord dev=ATAPI:1,0,0 -v -toc | less

Put a CDRW in to test rewriting erase (replace 1,0,0 with your n,n,n)
WARNING this should ERASE your CD/RW
# cdrecord dev=ATAPI:1,0,0 blank=fast

Put a CDR or CDRW in to test burning (replace 1,0,0 with your n,n,n)
# cdrecord dev=ATAPI:1,0,0 -v -data KNOPPIX_V3.8.2-2005-05-05-EN.iso

or see the following for more details
[http://www.centos.org/modules/newbb/viewtopic.php?topic_id=755&forum=29&post_id=2938#forumpost2938](http://www.centos.org/modules/newbb/viewtopic.php?topic_id=755&forum=29&post_id=2938#forumpost2938)

---

