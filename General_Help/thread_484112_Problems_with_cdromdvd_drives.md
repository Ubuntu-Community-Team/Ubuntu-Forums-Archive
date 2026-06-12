---
title: "Problems with cdrom/dvd drives"
date: 2007-06-25
forum: General Help
---

### Post by avg_po on 2007-06-25
I have both a dvd reader and a cd-RW drive in my machine. I have 2 problems both related to cdrom/dvd drives. I am running kubuntu 7.4.

(I do not know the manufacturer of my drives. It's a work PC and I'm hesitant to open it up and start taking things apart)

The following relevant lines are in my /etc/fstab file:

/dev/scd0 /media/cdrom0 auto user,noauto 0 0
/dev/scd1 /media/cdrom0 auto user,noauto 0 0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

I added the uncommented lines myself while I was playing around and debugging. Both sets of entries yield the same problems described below. scd0 = dvd reader: scd1 = CD-RW


Problem #1  (related to the dvd read-only drive)
It mounts/opens/reads data cd's fine. When I insert an audio cd, konqeror views 0 files. When the little konqeror window "Examining file progress" pops up, it never gets past 0%. When I attempt a manual mount "sudo mount -t iso9660 /dev/scd0 /media/cdrom", I get:
"mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0 ... blah blah blah".

A dmesg yields the following system message for every mount I attempt on an audio cd :
"[ 1268.079304] end_request: I/O error, dev sr0, sector 64
[ 1268.079833] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16"

Yes I have tried multiple audio cd's. 

The problem persists even if booting off the kubuntu live cd. The same cd's work and play just fine if I boot off the Fedora live cd.

# End Problem 1


Problem #2 (related to my burner)
Kubuntu does not detect my cd burner. As you saw above, there is a scd1 defined in the /etc/fstab file. However, doing a manual "sudo ls -l /dev/scd1" says that the device doesn't exist. Same problem when booting off the live Kubuntu cd. 

The drive is detected and reads/writes fine when booting from the fedora live cd.

# End Problem 2


It seems almost certain that these have something to do with how the Kubuntu kernel was built (driver related) as both problems are non-existent in a Fedora environment.

I'm at a loss at this point. My next step is to try and build my own kernel with everything related to CD/DVD support turned on.

Does anyone have any other fixes to try? Am I really the only one having this problem?

---

