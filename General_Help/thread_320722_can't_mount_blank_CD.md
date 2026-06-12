---
title: "can't mount blank CD"
date: 2006-12-17
forum: General Help
---

### Post by pixelterra on 2006-12-17
Hi good people,

I'm pretty new to linux and am trying to "make the switch" as so many others.

I would appreciate some help understading why my ubuntu doesn't recognize blank CD's. My drive loads CD's with data on them just fine. I've attempted this process through various burning programs and from nautilis. I've also used CD from 2 different manufacure's (I don't have more to try). Nothing I do gets a blank CD recognized.

Essentially the system doesn't recognize a blank CD as being present, and even when it "attempts to read" from it, the drive doesn't even move or make noise. WHen I insert the blank CD it sounds like the read process gets aborted early and then it goes silent.

This is the output of the "cdrecord -prcap" command. This output is the same whether I am root or not, and whethere is a blank CD in, or a data CD
> 
**benlieb@toshiba-satellite:~$ cdrecord -prcap**
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schi lling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
and thus may have bugs that are not present in the original version.
Please send bug reports and support requests to <cdrtools@packages.debian. org>.
The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-27-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
cdrecord: No such file or directory. Cannot open '/dev/cdrw'. Cannot open SCSI d river.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
I would really like to do something as simple as burn a CD, and this is pretty disappointing.](*,)

---

### Post by steve.horsley on 2006-12-18
I have never used cdrecord directly - I have only ever used the GUI tools that use cdrecord "behond the scenes". But normally, when I put a blank CD in, I get a nautilus CD creator window pop up so that I can just drag files into that and then click Burn. It may be worth your trying Go->CD Creator in nautilus and trying to burn anyway. Failing that, try gnomebaker or k3b.

You will never "mount" a blank CD because it has no filesystem to be able to mount.

---

### Post by pixelterra on 2006-12-19
Thanks for the help, but as I mentioned above:

> 
I've attempted this process through various burning programs and from nautilis. I've also used CD from 2 different manufacure's (I don't have more to try). Nothing I do gets a blank CD recognized.


Not the cammand line, not gui programs, and nothing seems to get my unbunto to recognize the existence of a blank disk (CDR).

Could this be a hardware thing?

---

### Post by pjalegria on 2007-07-07
same problem ...

---

### Post by skubisnack on 2007-10-26
This problem just popped up for me.  In the past, I have been able to burn CD's and DVD's.  Then, when I decided to upgrade to 7.10, I was trying to burn the 7.10 iso to cd, but the system will not recognize that there is a cd in it.  When I click on CD/DVD Creator, and attempt to burn, I'm told there is *probably* (this is the verbiage) not a cd in the drive.  I have tried several different blank CD-ROMs with no luck.  Here's the kicker.  I was able to burn an .iso to a DVD-ROM, however, not the 7.10 iso.

I have no idea how this happened, since I have not played with any settings for my drive ever.  It just worked when I installed Feisty.  I have since upgraded to 7.10 and that has not fixed the issue.

Any help would be appreciated.

The drive is on a gateway m52o laptop: DVD-RW GWA-4080N

Thanks

---

