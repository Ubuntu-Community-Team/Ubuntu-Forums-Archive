---
title: "DVD burning hell"
date: 2005-04-10
forum: General Help
---

### Post by Dracontopes on 2005-04-10
I am using Gnomebaker to burn dvd's.
Writing device: NEC 2500A

I am trying to erase a DVD+RW with gnomebaker, but I can't get it to work. Clicking "Format DVDRW", selecting NO options (Force / Fast) results in a question to insert dvdrw media. 

But then, when I click Okay the progress bar immeditely fills and the burn process is finished... The disc is NOT erased... :( Using options like "Force" and "Fast" (I think, using translated Ubuntu: Dutch) do not help.

The error code Gnomebaker gives (when running from terminal):
```

** Message: exec_run_cmd - umount /media/dvd
** Message: MessageDialog message [Fout koppelen /media/dvd.?
?
umount: /media/dvd is niet aangekoppeld (volgens mtab)
]
dvd+rw-format /dev/hda -format=full (null)
** Message: MessageDialog message [Plaats en herschrijfbare DVD in de DVD schrijver]
** Message: exec_thread - created child
** Message: exec_thread - parent created child with pid 9226
** Message: exec_thread - child exited with code [0]

** Message: exec_thread - exiting

```

The resultlog in Gnomebaker displays nothing, just an empty space. My guess is that there is something wrong with cdrecord?

FSTAB:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>	   <dump>  <pass>
proc		 /proc		 proc defaults	 0	 0
/dev/sda1	 /			 ext3	defaults,errors=remount-ro 0	 1
/dev/sda5	 none		 swap sw			 0	 0
/dev/hda	 /media/dvd	 udf,iso9660 ro,user,noauto 0	 0
/dev/fd0		/media/floppy0 auto	rw,user,noauto 0	 0
/dev/sdb1	 /home/chris/Backup	 ext3 defaults	 0	 0

```

cdrecord -scanbus
```

cdrecord: Warning: Running on Linux-2.6.10-5-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

```

cdrecord dev=/dev/hda -scanbus
```

cdrecord: Warning: Running on Linux-2.6.10-5-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hda'
devname: '/dev/hda'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
	 0,0,0	 0) '_NEC	' 'DVD_RW ND-2500A ' '1.08' Removable CD-ROM
		0,1,0	 1) *
		0,2,0	 2) *
		0,3,0	 3) *
		0,4,0	 4) *
		0,5,0	 5) *
		0,6,0	 6) *
		0,7,0	 7) *

```

I really need to completely erase the DVDRW's... Anyone? :shock:

---

### Post by ubuntu-geek on 2005-04-10
I haven't used gnomebaker with dvd media yet, however the folks at the Gnomebaker forum might be able to shed some light on your situation..

[http://gnomebaker.sourceforge.net/forum/](http://gnomebaker.sourceforge.net/forum/)

---

### Post by kleeman on 2005-04-10
Try looking through this thread as well (just finished):

[http://www.ubuntuforums.org/showthread.php?t=25174](http://www.ubuntuforums.org/showthread.php?t=25174)

---

### Post by Dracontopes on 2005-04-10
Thanks for replying \\:D/

I've bookmarked the thread, the problem is differs from mine but the solution might help... Right now I'm burning a DVD with NeroLINUX and it'sgoooood. (but I don't like the GTK1 look Nero has :shock:)

Anyway, I think I'll just post a topic on the dev.'s page yes.

---

### Post by cvmostert on 2005-11-02
if you get the answer to your problem, Dracontopes, please post it here... i have the same porblem with erasing dvdrw's

thanx

---

### Post by cvmostert on 2005-11-11
seems like you dont have to erase it... just overwrite it... (dvd)

---

