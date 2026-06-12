---
title: "Problem on burning CD"
date: 2008-06-21
forum: General Help
---

### Post by satimis on 2008-06-21
Hi folks,


Ubuntu 7.04 server amd64


Can any folk on the forum help me to understand following problem.


Blanking CD

$ cdrecord -v -eject dev=2,0,0 blank=all```

....
Performing OPC...
Blanking entire disk
Blanking time:  513.553s

```
It works seamlessly.


Burning ISO image

$ cdrecord -v -eject dvd=2,0,0 -tao -driveropts=burnproof /path/to/iso.image ```

wodim: Bad Option: dvd=2,0,0.
Usage: wodim [options] track1...trackn

Use     wodim -help
to get a list of valid options.

Use     wodim blank=help
to get a list of valid blanking options.

Use     wodim dev=b,t,l driveropts=help -checkdrive
to get a list of drive specific options.

Use     wodim dev=help
to get a list of possible SCSI transport specifiers.

```


$ cdrecord -v -eject -tao dvd=2,0,0 -driveropts=burnproof /path/to/iso.image
$ cdrecord -v -eject -tao dvd=2,0,0 /path/to/iso.image
$ cdrecord -v -eject dvd=2,0,0 -tao -driveropts=burnproof /path/to/iso.image
$ cdrecord -v -eject dvd=2,0,0 -driveropts=burnproof /path/to/iso.image
$ cdrecord -v -eject -tao /dev/dvd=2,0,0 -driveropts=burnproof /path/to/iso.image
$ cdrecord -v -eject -tao /dev/dvd=2,0,0 /path/to/iso.image
$ cdrecord -v -eject /dev/dvd=2,0,0 /path/to/iso.image
$ cdrecord -v -eject -tao /dev/dvd=ATA:2,0,0 -driveropts=burnproof /path/to/iso.image
$ cdrecord -v -eject /dev/dvd=ATA:2,0,0 /path/to/iso.image
etc.

Non of them can work.


Finally I ran;

$ cdrecord -v -eject -tao /path/to/iso.image```

.....
Min drive buffer fill was 100%
Fixating...
Fixating time:   34.575s
BURN-Free was never needed.

```
It worked w/o complaint.


It took me an hour to discover this trick.  Device can't be added on the command line.  Why?   TIA


Remark:  This is server no GUI burner installed.


B.R.
satimis

---

### Post by VMC on 2008-06-21
I don't have cdrecord installed. Have you tried "genisoimage -help" or "mksiofs -help".

I have been trying to find a better DVD+RW eraser. It looks like cdrecord does a better job than wodim does.

---

### Post by satimis on 2008-06-21
> **VMC said:**
> I don't have cdrecord installed. Have you tried "genisoimage -help" or "mksiofs -help".

I have been trying to find a better DVD+RW eraser. It looks like cdrecord does a better job than wodim does.
Hi VMC,


Thanks for your advice.


The ISO image was download on Internet NOT created.


B.R.
satimis

---

