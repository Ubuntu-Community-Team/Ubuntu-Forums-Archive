---
title: "No sound on DVD playback?"
date: 2005-09-15
forum: General Help
---

### Post by 68Firebird on 2005-09-15
I can get only 1 player do play dvd's. VLC player but there is no sound? I can play back otther media like .avi files with sound. But not dvd. Also all the other players I have installed will not play anyd dvds. Any suggestions??

---

### Post by 68Firebird on 2005-09-15
Ok it seems I can only play dvd's on my prextor dvd burner. On my samsung dvd rom drive I cannot play dvd's??? Also on the plextor the dvd play back is choppy??? They both work fine in windows. What can I do to fix this problem in Ubuntu???

---

### Post by 68Firebird on 2005-09-15
bump,

Still trying to work this problem out also.

---

### Post by Miguel on 2005-09-20
I also have the same problem.

I installed VLC from hoary universe and libdvdcss2 from marillat. If it helps, I downloaded libdvdcss2 via wget and installed using dpkg. I just didn't want to add and remove repos.

And thus the thread is bumped.

Thanks in advance,

Miguel

---

### Post by Lord Illidan on 2005-09-20
Try and enable dma...

Look here for more info : [http://www.ubuntuforums.org/showthread.php?t=30949](http://www.ubuntuforums.org/showthread.php?t=30949)

BTW, try Xine for dvd playback.

---

### Post by Miguel on 2005-09-21
Cheers, Lod Illidan.

Will check as soon as I have a DVD on my hands!

---

### Post by 68Firebird on 2005-09-30
Well I needed to take a break for awhile being I was not getting anywhere but I am back at it again. I am still trying to get dma enabled. I tried building another kernal according to the guide and it still did not work. This is what I get in terminal,

/dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
steven@antec93utesjf37Steven:~$

dvd playback is still very choppy. 

My pc specs,
intel Pentium 4 2.4C Northwood
1 plextor dvd rw, ide
1 samsung dvd rom, ide
seagate 80gig hd, sata
soyo motherboard with a intel 865pe chipset.

I would really like to get this problem fixed.

---

