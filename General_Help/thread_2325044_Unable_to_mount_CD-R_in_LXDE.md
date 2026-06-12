---
title: "Unable to mount CD-R in LXDE"
date: 2016-05-18
forum: General Help
---

### Post by nadrach on 2016-05-18
I have a CD-R of photos written on MS Win XP in 2007.
Opens fine on MS Win 7.
Won't mount on LXDE on Lubuntu 16.04.
Common to multiple machines running Lubuntu 16.04.
Have tried DVD (video and Data) in same drives, no problem.
Also CD-RW, no problem.
Second CD-R with photos - no mount.
Seems to be CD-R that is a problem. Philips and Verbatim brand so far.
I'm looking for other CD-R to try.
Any suggestions?

---

### Post by oldrocker99 on 2016-05-18
If everything else works in your drive, it would seem that it **is** a bad CD-ROM, although if it worked on Win7 (when?), you should be able to copy the files to a thumb drive in Windows and copy them to your /home folder.

---

### Post by Frogs Hair on 2016-05-18
Moved to *General Help*

---

### Post by nadrach on 2016-05-18
This started with one CD-R. I burned it with photos for a relative in 2007. My archive of the photos was damaged and I wanted to recover missing photos, so borrowed the disk back. Today, it would not load on Lubuntu. I tried in a second Lubuntu machine and got the same effect. OK, possibly damaged CD-R. Try in W7 machine and it is OK. Try in a dual-boot machine with W7 and Lubuntu and OK on W7, not on Lubuntu. Try several other disks, DVD (film) DVD-R, DVD-RW, DVD+R, CD-RW, CD-R, CD (support disk for camera) and find that everything works everywhere except for the two CD-R photo disks which do not mount in any Lubuntu machine (all on 16.04 64-bit). The second CD-R disk with photos was burned on a Vista machine in 2010.

The only common failure pattern is a CD-R and Lubuntu.

As you say, I was able to recover the missing photo files on W7 and port them to my Lubuntu machine.

But this has puzzled me, so I am going to investigate further. I have some spare blank CD-R disks at the office which I can test burn on different machines and OS's tomorrow, including on Lubuntu machines, with a mix of data files. I'll update with the results.

---

### Post by kansasnoob on 2016-05-19
It's a bug:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768)

There are at least three other forum threads:

[http://ubuntuforums.org/showthread.php?t=2323708](http://ubuntuforums.org/showthread.php?t=2323708)

[http://ubuntuforums.org/showthread.php?t=2323524](http://ubuntuforums.org/showthread.php?t=2323524)

[http://ubuntuforums.org/showthread.php?t=2323204](http://ubuntuforums.org/showthread.php?t=2323204)

I had hoped to turn the heat on that bug up further by reporting it on the QA Tracker but it turns out I can't find a CD or DVD in my collection that isn't recognized. One of those reporting the issue listed some discs that don't work here:

[http://ubuntuforums.org/showthread.php?t=2323204&page=2&p=13487541#post13487541](http://ubuntuforums.org/showthread.php?t=2323204&page=2&p=13487541#post13487541)

> I have a 100-pack of Memorex CD-R, and they never auto-mount, regardless of content. (does not work)

Philips CD-R does not work. I only tried one disc.

Sony DVD-R seems to work. I only tried one disc.

Older Memorex Black CD-R does not work. I only tried one disc.

Older Memorex CD-R from 2009 seems to work. I only tried one disc.

Staples brand CD-R does not work. I only tried one disc.

HP CD-R does not work. I only tried one disc.

If I had a disc or two in hand that I could use for testing I'd certainly try to turn up the heat on that bug so it can at least be fixed by 16.04.1 around July, but I'm stuck :(

---

### Post by sudodus on 2016-05-19
I have Verbatim CD-R 700 MB 52x disks. I tried one such disk (with Clonezilla on it)

- in my present main system Xubuntu + Lubuntu 16.04 LTS. It is up to date. I can read files on the CD-R disk.

- in a laptop booted from a pendrive with Lubuntu 16.04 LTS 32-bit , **lubuntu-14.04-desktop-i386.iso**. I can read files on the CD-R disk.

I tried other CD-R disks in the laptop with Lubuntu 16.04 LTS 32-bit:

- an old Platinum CD-R is recognized (the disk label) but the files are not readable until I unmount the previous mountpoint manually. Then it can be automounted and the content is possible to read.

- an old Traxdata CD-R is recognized and readable at once.

- an old FujiFilm CD-R is recognized and readable at once.

This computer is described here: [http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

with the DVD drive: TSSTcorp CDDVDW SN-208AB (Seagate rev. TO04)

It works for me, so I'm sorry, but I can't help much.

---

