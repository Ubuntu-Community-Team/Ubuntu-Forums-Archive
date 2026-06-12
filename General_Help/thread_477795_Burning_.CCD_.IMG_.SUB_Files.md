---
title: "Burning .CCD .IMG .SUB Files"
date: 2007-06-18
forum: General Help
---

### Post by TreeFinger on 2007-06-18
I am having a hard time trying to burn this type of image.Does anyone know what program I can do it with?

I would like to learn to burn images, data, etc from the command line. Is that possible?

If this is in the wrong section move it to where it should be.

---

### Post by eZtaR on 2007-06-18
[Quote=http://linuxreviews.org/howtos/cdrecording/#toc16]A Windows tool called CloneCD is commonly used to burn backups of Playstaion and other copyprotected CDs.

CloneCD rips an image consisting of three files .ccd/.img/.sub, usually distributed archived as zip or rar. The .img is the CD data, the .cdd looks like a .cue and the .sub may contain extra information on specially marked sectors.

Sad to say these files can not be burned perfectly under Linux. You have to alternatives:

   1. Download the Clone-CD to ISO converter ccd2iso
          * Download now: ccd2iso-0.1.tar.gz (200 kb)
   2. Burn with cdrdao and use the .img as .bin, .cdd as .cue and ignore the .sub. This may work correct.
[/quote]

And you burn with cdrdao this way 
> cdrdao write --eject --speed 16 --device 0,3,0 --driver generic-mmc filename.cue

:)

---

### Post by TreeFinger on 2007-06-18
Hmm Well I converted the .img file to .iso. I am attempting to burn that .iso in k3b right now. I am not sure if it will work though. I tried running the command you said in terminal and got some errors.

```

o$ cdrdao write --eject --speed 12 --device 0,3,0 --driver generic-mmc Chrono.Cross.NTSC.US.CD1.CCD
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

ERROR: Chrono.Cross.NTSC.US.CD1.CCD:1: Illegal token: [
ERROR: Chrono.Cross.NTSC.US.CD1.CCD:1: Illegal token: C
ERROR: Chrono.Cross.NTSC.US.CD1.CCD:1: Illegal token: l
ERROR: Chrono.Cross.NTSC.US.CD1.CCD:1: Illegal token: o
ERROR: Chrono.Cross.NTSC.US.CD1.CCD:1: syntax error at "EOF" missing  { TrackDef CdText }

```

Just burning the .iso did not work. The CD Is not booting. I don't feel like having to get on windows to do this :)

---

### Post by phanter on 2007-06-20
I have this question how do I convert the .img file to .iso ??? Any help please !!! :(

---

### Post by Sigma on 2007-12-17
The following URL recommends using ccd2iso to convert CloneCD images to ISO images:

[https://help.ubuntu.com/community/ManageDiscImages]("https://help.ubuntu.com/community/ManageDiscImages")

I've given it a try and it seems to work perfectly!

---

### Post by ycason on 2007-12-18
Hey,

Quick and easy

sudo apt-get install k3b

then just run the program and burn an image.  You'll have to make it select from all files instead of just iso's.  That's it.  Burns like a champ:popcorn:

---

### Post by marlboro05 on 2008-03-25
sudo apt-get install ccd2iso

to get the ccd2iso

---

