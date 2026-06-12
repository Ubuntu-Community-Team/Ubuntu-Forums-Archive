---
title: "Devede ISO Size"
date: 2007-05-27
forum: General Help
---

### Post by lakerssuperman on 2007-05-27
I use Devede to convert various video files to DVD.  Everything works fine.  As I add files to the compilation the size indicator increases showing how much of the 4.7 gb's is still available.  I fill the disc up to what should be a 4gb file but when it finishes converting the resulting ISO is only around 1.6 gb.  This doesnt make any sense but the video is complete when I play it back on my DVD player.  Does anyone know why this happens.  This occurs under both Edgy and Feisty.

---

### Post by MoLE on 2007-06-02
I'd do a visual check of the burnt disc itselt to see if in fact the whole disc was used, or not?  If not, then I'd file a bug with the Devede developers.

---

### Post by yaztromo on 2008-02-13
Got the same problem, even with the latest version of Devede. Unfortunately most of the Devede site is in french and there's no forum.

edit: My guess is Devede is going wrong in it's calculations somewhere. My solution is just opt for 7mbs/s even if it looks like it'll be too much.

---

### Post by vdawg on 2008-06-19
Hey, I got the exact same problem with version 3.6, I then updated to version 3.8c but now the iso size is around 3.2 Gb (basically double, haha)

I'm on ubuntu hardy heron, AMD64 dual core ... everything is fine and I mount the iso and it plays fine, I burnt both the isos to a DVD and they play fine, but since I'm using a whole damn dvd I might as well use all of the 4.7 gb eh?

Anyone else notice the same thing?

> **lakerssuperman said:**
> I use Devede to convert various video files to DVD.  Everything works fine.  As I add files to the compilation the size indicator increases showing how much of the 4.7 gb's is still available.  I fill the disc up to what should be a 4gb file but when it finishes converting the resulting ISO is only around 1.6 gb.  This doesnt make any sense but the video is complete when I play it back on my DVD player.  Does anyone know why this happens.  This occurs under both Edgy and Feisty.

---

### Post by timcredible on 2008-06-19
that's probably due to the source files.  i'd bet that devede is basing the estimated size of the dvd by the source video files.  if the source file is much bigger than the converted mpeg file, then that would account for what you're seeing.  i'm using devede to take .avi files off my camera and put on dvd, and it's pretty accurate on the iso file size estimate.  

what type of file and what size (HxW) are the source files?

---

### Post by vdawg on 2008-06-19
> **timcredible said:**
> that's probably due to the source files.  i'd bet that devede is basing the estimated size of the dvd by the source video files.  if the source file is much bigger than the converted mpeg file, then that would account for what you're seeing.  i'm using devede to take .avi files off my camera and put on dvd, and it's pretty accurate on the iso file size estimate.  

what type of file and what size (HxW) are the source files?

So so the source files are you typical 1CD dvd rip, encoded by an xvid encoder. For example my cousin Done ;) made a backup of his latest movie "Brick lane" in the following format:

```

video codec........: XviD MPEG 4 Codec
video bitrate......: ~880 kbps 
audio codec........: MP3 VBR 128kbit/s 
resolution.........: 592 x 256 
runtime............: 907 min 

```

And devede at around 5001 kbps gave me an iso of 3.2 Gb, even though it estimated that it would use up all of the 4.7 gigs.

Right now I am trying to make another iso with 6001 kbps and devede says that it is using up about 139% of the 4.7 Gb disk, so we will see if this in reality creates a bigger iso that would fit the 4.7 Gb disk nicely :)

---

