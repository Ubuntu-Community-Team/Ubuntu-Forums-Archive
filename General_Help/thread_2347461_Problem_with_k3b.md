---
title: "Problem with k3b"
date: 2016-12-25
forum: General Help
---

### Post by anon_private on 2016-12-25
I am trying to burn an iso file.

First question. How do I erase the RW disk?

k3b does not seem to function. Is there a better burner for kubuntu.

From the debug:

 Burned media
 -----------------------
 DVD-RW Sequential
 

 Devices
 -----------------------
 HL-DT-ST DVD+-RW GSA-H31N B109 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]
 

 System
 -----------------------
 K3b Version: 2.0.2
 KDE Version: 4.13.3
 QT Version:  4.8.6
 Kernel:      4.4.0-57-generic
 

 Used versions
 -----------------------
 growisofs: 7.1
 

 growisofs
 -----------------------
 Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
 /dev/sr0: "Current Write Speed" is 4.1x1352KBps.
           0/1531445248 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
 === last message repeated 35 times. ===
 :-[ WRITE@LBA=0h failed with SK=1h/ASC=00h/ACQ=03h]: Input/output error
 :-( attempt to re-run with -dvd-compat -dvd-compat to engage DAO or apply full blanking procedure
 :-( write failed: Input/output error
 

 growisofs command:
 -----------------------
 /usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=4gms -use-the-force-luke=tracksize:747776 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m

---

### Post by scdbackup on 2016-12-26
Hi,

> First question. How do I erase the RW disk?

Try one of:
```

dvd+rw-format -blank=full /dev/sr0
cdrskin -v def=/dev/sr0 blank=all
xorriso -outdev /dev/sr0 -blank all

```

This lasts as long as a full write run. If you blank them with
```

dvd+rw-format -blank=fast /dev/sr0
cdrskin -v def=/dev/sr0 blank=deformat_sequential_quickest
xorriso -outdev /dev/sr0 -blank deformat_quickest

```
you will possibly get a shorter blank run. But the medium will not be
capable of multi-session.

If you format the medium once, then you do not have to blank any more before
overwriting:
```

dvd+rw-format /dev/sr0
cdrskin -v def=/dev/sr0 blank=format_overwrite
xorriso -outdev /dev/sr0 -format as_needed

```

-------------------------------------------------------------

But you have a more severe problem with your hardware or bus drivers.

```

:-[ WRITE@LBA=0h failed with SK=1h/ASC=00h/ACQ=03h]: Input/output error

```
is a known misperception of an error code which does not stem from the
burner but must rather be emitted by the controller hardware or the
Linux kernel.

growisofs shows this code, if it receives from the kernel an SCSI error code
```

5 21 04 UNALIGNED WRITE COMMAND

```
which seems to belong to the error list of shingled magnetic disks.
Because it is presented in format "Descriptor" rather than "Fixed",
growisofs and cdrecord pick and display the wrong bytes from the
received SCSI Sense Data.

Two (german) threads are known to me which report the same problem:
[https://forum.ubuntuusers.de/topic/brennen-mit-k3b-nicht-moeglich/](https://forum.ubuntuusers.de/topic/brennen-mit-k3b-nicht-moeglich/)
[https://debianforum.de/forum/viewtopic.php?f=13&t=157244](https://debianforum.de/forum/viewtopic.php?f=13&t=157244)

The remedy in the Debian thread was to attach another burner via USB.
The Ubuntu thread does not show a final success report yet.

I (as libburn developer) am sure it is not about the drive itself or
the way how the burn program operates it. But more i cannot say yet.
The problem seems rare.

The only known systematic hardware problem is about some Linux kernel
versions and burners attached to USB 3 ports. But the "unaligned write
command" seems to happen on SATA attached drives.

Have a nice day :)

Thomas

---

### Post by anon_private on 2016-12-26
I am lost

What can I do to ensure that I can erase RW disks if I choose; and to burn files to DVD media.

I believe that I should be able to erase from within the programme itself.

Many people say that k3b and Brassero are good programmes. But is there another that I could install to kubuntu and might give better results?

Generally my DVD drive appears to work well (in situ). I don't want to uses a usb connected drive.

Hope you have some ideas.

Is this problem likely to arise in UBUNTU  ver 16. I am using kubuntu ver 14 at present.

---

### Post by scdbackup on 2016-12-26
Hi,

> What can I do to ensure that I can erase RW disks if I choose;
> and to burn files to DVD media.

I assume that K3B, Brasero, or Xfburn offer you an opportunity to blank,
if the medium is in a blankable and blank-worthy state.

growisofs underneath K3B perceived it obviously as blank, because it tried
to write to it. Then it ran into the error reply forwarded by the kernel.
This reply then triggered a bug in growisofs error handling so that i can
only guess, what error code was really forwarded by the kernel. In other cases
it was 5,21,4.

If you want to follow the probably mislead advise of growisofs to apply
a full blanking procedure, then run
```
dvd+rw-format -blank=full /dev/sr0
```


> is there another that I could install to kubuntu and might give better
> results?

You may try Xfburn. But i expect any success to be rather incidential.
I am quite sure that the failure to write is not related to a particular
burn program. They all send SCSI WRITE commands to the drive and wait for
success indication.


> Generally my DVD drive appears to work well (in situ)

How often does writing succeed ? How often does it fail ?

Are there particular media types which work or fail reliably ?


> HL-DT-ST GSA-H31

How old is this drive ?

> Is this problem likely to arise in UBUNTU ver 16

The problem might come from low level bus drivers in the kernel.
It would be interesting to see whether it vanishes with a newer kernel.


Have a nice day :)

Thomas

---

