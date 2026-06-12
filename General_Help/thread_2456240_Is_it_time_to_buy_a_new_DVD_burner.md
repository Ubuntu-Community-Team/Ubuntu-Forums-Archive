---
title: "Is it time to buy a new DVD burner ?"
date: 2021-01-07
forum: General Help
---

### Post by linuxyogi on 2021-01-07
[ATTACH=CONFIG]287694[/ATTACH]
(Click to enlarge)

```
Burned media
-----------------------
DVD-R Sequential

Devices
-----------------------
HL-DT-ST DVDRAM GH24NSB0 LN00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 2097576 (4295835648 bytes)

System
-----------------------
K3b Version: 19.12.3
KDE Version: 5.67.0
Qt Version:  5.12.8
Kernel:      5.4.0-54-generic

Used versions
-----------------------
mkisofs: 1.1.11
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
:-[ PERFORM OPC failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=4gms -use-the-force-luke=tracksize:2097576 -dvd-compat -speed=16 -use-the-force-luke=bufsize:32m

mkisofs
-----------------------
2097576
I: -input-charset not specified, using utf-8 (detected in locale settings)
This size can only be represented in the UDF filesystem.
Make sure that your clients support and use it.
ISO9660, Joliet, RockRidge, HFS will display incorrect size.
  0.02% done, estimate finish Thu Nov 26 04:21:08 2020
  0.05% done, estimate finish Thu Nov 26 04:21:08 2020
  0.07% done, estimate finish Thu Nov 26 04:21:08 2020
  0.10% done, estimate finish Thu Nov 26 04:21:08 2020
  0.12% done, estimate finish Thu Nov 26 04:21:08 2020
  0.14% done, estimate finish Thu Nov 26 04:21:08 2020
  0.17% done, estimate finish Thu Nov 26 04:21:08 2020
  0.19% done, estimate finish Thu Nov 26 04:21:08 2020
  0.22% done, estimate finish Thu Nov 26 04:21:08 2020
  0.24% done, estimate finish Thu Nov 26 04:21:08 2020
  0.26% done, estimate finish Thu Nov 26 04:21:08 2020
  0.29% done, estimate finish Thu Nov 26 04:21:08 2020
  0.31% done, estimate finish Thu Nov 26 04:21:08 2020
  0.33% done, estimate finish Thu Nov 26 04:21:08 2020
  0.36% done, estimate finish Thu Nov 26 04:21:08 2020
  0.38% done, estimate finish Thu Nov 26 04:21:08 2020
  0.41% done, estimate finish Thu Nov 26 04:21:08 2020
  0.43% done, estimate finish Thu Nov 26 04:21:08 2020
  0.45% done, estimate finish Thu Nov 26 04:21:08 2020
  0.48% done, estimate finish Thu Nov 26 04:21:08 2020
  0.50% done, estimate finish Thu Nov 26 04:21:08 2020
  0.52% done, estimate finish Thu Nov 26 04:21:08 2020
  0.55% done, estimate finish Thu Nov 26 04:21:08 2020
  0.57% done, estimate finish Thu Nov 26 04:21:08 2020
  0.60% done, estimate finish Thu Nov 26 04:21:08 2020
  0.62% done, estimate finish Thu Nov 26 04:21:08 2020
  0.64% done, estimate finish Thu Nov 26 04:21:08 2020
  0.67% done, estimate finish Thu Nov 26 04:21:08 2020
  0.69% done, estimate finish Thu Nov 26 04:21:08 2020
  0.72% done, estimate finish Thu Nov 26 04:21:08 2020
  0.74% done, estimate finish Thu Nov 26 04:21:08 2020
  0.76% done, estimate finish Thu Nov 26 04:21:08 2020

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid DVD1 -volset  -appid K3B THE CD KREATOR (C) 1998-2018 SEBASTIAN TRUEG, MICHAL MALEK AND LESLIE ZHAI -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/k3b.vTxhUU -rational-rock -hide-list /tmp/k3b.akzPxX -joliet -joliet-long -hide-joliet-list /tmp/k3b.cjrePa -no-cache-inodes -allow-limited-size -udf -full-iso9660-filenames -iso-level 3 -path-list /tmp/k3b.mQUYxO

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid DVD1 -volset  -appid K3B THE CD KREATOR (C) 1998-2018 SEBASTIAN TRUEG, MICHAL MALEK AND LESLIE ZHAI -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/k3b.raBtID -rational-rock -hide-list /tmp/k3b.WIKrLS -joliet -joliet-long -hide-joliet-list /tmp/k3b.UkHPWL -no-cache-inodes -allow-limited-size -udf -full-iso9660-filenames -iso-level 3 -path-list /tmp/k3b.ksNdzt


```

This is my last Desktop. When this Desktop fails I will move to a Laptop so I don't want to invest in new hardware. 
Can someone please tell if this issue is software related or my DVD burner has become faulty ?
I tried K3B & XFburn & both failed.

---

### Post by ActionParsnip on 2021-01-07
Didn't you post this on Facebook too :)

---

### Post by linuxyogi on 2021-01-07
> **ActionParsnip said:**
> Didn't you post this on Facebook too :)
Yes but unfortunately no solution. Within the last 10 mins some members have suggested that I replace the drive.

---

### Post by crip720 on 2021-01-07
A new DVD burner can also be used on a laptop if needed, so not really a waste of money.  Some laptops don't have DVD drives anymore.

---

### Post by ajgreeny on 2021-01-07
I have almost given up on DVD drives on my current desktop machine now as I have not really any use for them any more; not for me anyway.

I used to use them for mainly ripping the occasional DVD or audio CD in order to play the film or music through my Embymedia-server, and I still have a laptop with a good DVD drive.

Just consider how much you use a DVD drive nowadays; if you use it a lot then replace it (they're not expensive), if not , don't bother.  I assume, however, that as you asked you still make good use of the drive.

---

### Post by linuxyogi on 2021-01-07
I have decided that I will not waste money on a new DVD drive. Since this drive can still read discs I will leave it connected. I will buy a external drive, copy data from all my DVDs to the external drive & then physically destroy all the DVDs. Thanks everyone for the replies.

---

### Post by scdbackup on 2021-01-08
Hi,

the decisive message is from growisofs

> :-[ PERFORM OPC failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error

This is a problem between drive and medium, with some hope that not the 
drive alone is to blame.

Try other media from a different brand than the one that is failing.

Have a nice day :)

Thomas

---

### Post by TheFu on 2021-01-08
Or get an M-Drive to support M-discs.  These have 50 yr lifespans (estimated) and are for backups.  The discs come in 25G and 50G sizes. They can read and write DVDs of all sorts.  The cost of the M-Drive isn't all that much. $30 [https://www.amazon.com/LG-Electronics-Portable-Rewriter-GP60NB50/dp/B00C2AMK2M](https://www.amazon.com/LG-Electronics-Portable-Rewriter-GP60NB50/dp/B00C2AMK2M)

---

### Post by kurt18947 on 2021-01-08
> **TheFu said:**
> Or get an M-Drive to support M-discs.  These have 50 yr lifespans (estimated) and are for backups.  The discs come in 25G and 50G sizes. They can read and write DVDs of all sorts.  The cost of the M-Drive isn't all that much. $30 [https://www.amazon.com/LG-Electronics-Portable-Rewriter-GP60NB50/dp/B00C2AMK2M](https://www.amazon.com/LG-Electronics-Portable-Rewriter-GP60NB50/dp/B00C2AMK2M)

Wouldn't those capacities be bluray? Bluray M-discs are available but are not cheap, thanks Hollywood. I've wondered about those for long term archiving. M-disc DVD drives and media are much more reasonable.

---

### Post by TheFu on 2021-01-08
I didn't look too closely at the writer specs. Sorry.

[https://www.amazon.com/External-Burner-Wihool-Type-C-Windows/dp/B07TS5SHHY/](https://www.amazon.com/External-Burner-Wihool-Type-C-Windows/dp/B07TS5SHHY/) $91 and it does dual-layer 50G m-discs.

M-discs are designed for long term storage.  Put your wedding photos and child birth videos on that stuff.  Normal consumer burned DVDs have about a 10 yr expected lifespan.  I have some DVDs that are nearly 20 yrs old from back when HDDs were very expensive. Some have started failing. I always included 10% par2 files to have extended protections for knowing the data was corrupt.  I've had to use dd to image a self-burned DVD, then loop mounted and ran a par2 recovery to get back all the file data.

Eventually, HDD storage for backups became so cheap that the hassle of splitting up files into 8.4G chunks just wasn't worth it to me.

Commercially burned optical media life times should be much longer, but that doesn't help your wife understand why/how the wedding photos and new baby picts were lost due to bit-rot on any media we might select.

As for the costs of m-disc drives, they are usually backwards compatible with CDROM, DVD, HD and Bluray standards, which means lots of licensing needed.  I don't have any m-disc.  I've been using 2TB-8TB HDDs as 2nd and 3rd backup storage media for some time.  When an 8TB is $130, that's a bunch of files.

A friend has an m-disc 50G device.  He isn't cost sensitive like I am.

Really just providing options.  Somewhere inside our homes, we probably need a DVD data reader, perhaps a working 3.5" and perhaps a 5.25" floppy reader.  I have some 4mm tapes and QIC-250 tapes that I never expect to access again.  For home use, tapes are just too expensive. What is just sad is how expensive that Adaptec SCSI-2 HBA cost and it won't even fit in any of my current systems - no ISA bus.

---

