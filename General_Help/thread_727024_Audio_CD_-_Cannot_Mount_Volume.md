---
title: "Audio CD - Cannot Mount Volume"
date: 2008-03-17
forum: General Help
---

### Post by andrewk8 on 2008-03-17
When I load an audio CD, I get a pop-up window:  "Cannot mount volume.  Invalid mount option when attempting to mount the volume."

When I load a data CD, "cdrom0 - File Browser" pops up and shows the contents of the disc.  I also get an icon on the desktop showing the volume name.  I can browse through the folders on the data CD.  When I right click on the icon on the desktop and choose Eject, the CD tray opens.

I just loaded Ubuntu 7.10 clean install as a guest in VirtualBox 1.5.6, running on Windows XP SP2 host.  Since a data CD works correctly, it appears that the mappings from Windows XP CD-ROM devices through VirtualBox are working correctly.  It appears that Ubuntu isn't correctly identifying the disc as an audio CD.

Originally posted in Hardware & Laptops Forum.  Didn't get any responses.  Maybe the wrong place since my hardware appears to be working correctly and it may be a mis-configuration of Ubuntu during installation?  (REF:  [http://ubuntuforums.org/showthread.php?t=726301]("http://ubuntuforums.org/showthread.php?t=726301"))

(Linux newbie, so be gentle...)

---

### Post by DoctorMO on 2008-03-17
despite the error can you still access the audio cd rom in a music player?

---

### Post by andrewk8 on 2008-03-17
Sadly, no.  Nothing happens in Serpentine when I try to mount the CD.

I found a couple of related threads that were related, but didn't solve my problem.  Here is some more info.

[INDENT]andrew@andrew-desktop:~$ mount /media/cdrom0
mount /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

andrew@andrew-desktop:~$ dmesg | tail
[12319.902460] end_request: I/O error, dev sr0, sector 1024
[12319.904047] UDF-fs: No partition found (1)
[12319.918113] end_request: I/O error, dev sr0, sector 64
[12319.919357] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[12517.830441] end_request: I/O error, dev sr0, sector 64
[12517.838953] end_request: I/O error, dev sr0, sector 1248
[12517.843901] end_request: I/O error, dev sr0, sector 1024
[12517.845948] UDF-fs: No partition found (1)
[12517.867261] end_request: I/O error, dev sr0, sector 64
[12517.868775] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16[/INDENT]

[INDENT]andrew@andrew-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d4d1ea70-0ea6-4c03-b416-ca79c721c49a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5d1f01ec-d13e-4ab8-9f24-efae68b8a4d4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
[/INDENT]

---

### Post by DoctorMO on 2008-03-18
don't try to mount the file system, it's not a file system it's an audio cd. run vlc (install vlc) and open the cd with that by pointing it at /dev/hdx or /dev/sdx where x is the letter of the cdrom drive. other than that I don't think your going to have much luck since it's probably a virtulaisation problem (with the virt software).

---

### Post by andrewk8 on 2008-03-18
I was afraid VirtualBox might be an issue on this one.  In VirtualBox, I have to "mount" a CD-ROM drive to tell Windows to ignore it and to create the link between the physical drive and the virtual machine.  It may (or may not) have the same meaning as Linux mount.

I will try vlc and post a response.  (/dev/scd0 is the CD-ROM drive according to my fstab output from above).

I have two follow-up questions:

Follow-up #1:
Can you confirm the correct behavior on a real machine?  With the out-of-the-box install (7.10), GNOME maps Serpentine to audio CDs.  So when an audio CD is inserted, Ubuntu (GNOME?) creates a new icon on the desktop, launches Serpentine, and begins playing the audio CD.  Is this correct?

Follow-up #2:
In Windows I (think) I can map a networked CD-ROM drive to a Windows drive letter and have Windows launch WMP (or your favorite audio player) when an audio CD is inserted into the remote CD-ROM drive (now I have to actually try this one to confirm).  I have successfully integrated the virtual machine into my home network and connected Ubuntu to a networked printer on another Windows XP machine.  Could I connect my physical CD-ROM drive on the Windows host to the Ubuntu guest through NFS / SAMBA and obtain the same functionality?

---

### Post by DoctorMO on 2008-03-19
1. Yes
2. No, sorry.

---

### Post by andrewk8 on 2008-03-24
Follow-up to original question:
VirtualBox has a CD-ROM "passthru" setting that you can enable only when the virtual machine is turned off.  When I enabled this option and started the virtual machine, Serpentine ***did*** launch when I inserted a CD in the CD-ROM drive and it showed the correct CD title, artist, track names, etc.

I couldn't get it to do much more than that.  When I hit *Play*, the CD-ROM drive would spin up, then spin down, then spin up again, etc.

As for my second comment:
> **andrewk8 said:**
> Follow-up #2:
In Windows I (think) I can map a networked CD-ROM drive to a Windows drive letter and have Windows launch WMP (or your favorite audio player) when an audio CD is inserted into the remote CD-ROM drive (now I have to actually try this one to confirm).  I have successfully integrated the virtual machine into my home network and connected Ubuntu to a networked printer on another Windows XP machine.  Could I connect my physical CD-ROM drive on the Windows host to the Ubuntu guest through NFS / SAMBA and obtain the same functionality?
I couldn't do this in Windows.  Too optimistic.  I could see the the track names on the remote CD, but I couldn't get them to play.

It was wishful thinking to try to play / rip an audio CD through VirtualBox.  Thanks for your help.

---

