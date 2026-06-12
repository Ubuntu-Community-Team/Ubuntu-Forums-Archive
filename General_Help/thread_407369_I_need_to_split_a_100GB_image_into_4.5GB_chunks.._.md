---
title: "I need to split a 100GB image into 4.5GB chunks.. how??"
date: 2007-04-12
forum: General Help
---

### Post by billdotson on 2007-04-12
I used dd to make an image used for backup of my Windows partition.  Now I want to take that image, archive it and split it into DVD (Not dual layer) sized chunks.  I know rar supports multi-part archiving but I don't want to pay for it.. or keep the trial verison and rip the rar guys off.  

Does bzip2 support multi-part archiving or do I have to do what I want another way??

The Windows partition image is win.img.. I tried compressing by doing bzip2 -9 win.img but it gave me an I/O error like it did w/ a Linux ISO.  DOes it not work with images??

here is the message I got:

```

sgtmattbaker@sgtmattbaker:/media/Windows_backup/backup_of_Windows$ sudo bzip2 -9 win.img

bzip2: I/O or other error, bailing out.  Possible reason follows.
bzip2: No space left on device
        Input file = win.img, output file = win.img.bz2
bzip2: Deleting output file win.img.bz2, if it exists.

```

or maybe it ran out of space.. ?

---

### Post by kidders on 2007-04-12
Hi there,

> **billdotson said:**
> I tried compressing by doing bzip2 -9 win.img but it gave me an I/O error like it did w/ a Linux ISO.  DOes it not work with images??You can bzip anything. (Large files can take a very long time though!) I'm puzzled by the error you posted though. Presumably you would *know* if you were out of disk space, so I can't help wondering if something nastier is going on.

In terms of splitting the file, there's nothing stopping you using **head** or **tail** to chop bits off it, although many people find **split** more convenient.

---

### Post by Biochem on 2007-04-12
If you don't need compression you can make a multivolume tar.
 just add the
 --tape-length="size"  
"Set maximum length of a volume.  The size argument should then be the usable size of the tape in units of 1024 bytes." 
[http://www.gnu.org/software/tar/manual/html_node/Multi_002dVolume-Archives.html#Multi_002dVolume-Archives](http://www.gnu.org/software/tar/manual/html_node/Multi_002dVolume-Archives.html#Multi_002dVolume-Archives)

---

### Post by rsambuca on 2007-04-12
I strongly recommend using [[COLOR="Red"]Drive Snapshot[/COLOR]]("http://www.drivesnapshot.de/en/index.htm").  I first heard about the program from Leo Laporte's Call for Help Show.  Drive Snapshot has a free 30-day trial which is all you need for personal use.  It makes an image of your drive from within Windows.  You can then specify the size of the output files for putting the image onto CD's, DVD's, or just one file for putting the image onto another hard drive.  Once the image file(s) are made, you no longer need the Drive Snapshot software as the first disk is bootable.  It should work perfectly for what you want to do.

I used to routinely re-install my XP every six months or so to keep it running smoothly, but now I just go back to the image and it works great.  Just install XP, run Windows Update, install the drivers and programs you want, and then make the image files.

---

