---
title: "Convert a DVD to a DIVX-CD"
date: 2006-09-17
forum: General Help
---

### Post by phibuntu on 2006-09-17
Hello
 
I have baught a DVD.
I have no problems to whatch this DVD on my Ubuntu Laptop (Dell).

I have tried to watch this DVD on two DVD-players but both are not able to play it (only ubuntu makes the job:!:). The first player only supports one language, the second hashes the picture.

Now, I want to convert my DVD to a DivX CD. My DVD Player is able to play DivX CDs. 

Any Idea how to bring the film I see on Ubuntu (great dvd, great operating System) to a DivX CD?

I have seen, that there are many programs (like dvd::rip, ...) on the "market". But I dont want to read 100 Pages of manuals of 10 different packeges, if somone already has done the above mentioned job.

To be more precise: 

I want to catch the film from DVD in a given (but not the default) language without subtitles from the DVD and copy only this version (no menus, no sceen selection menu, ...) to a DivX file. This file will be burned to a CD which I put into my DVD player.

Thanks in advance

---

### Post by pay on 2006-09-18
Avidemux is reasonbly straight foward to use and allows you to make a AVI with DIVX video.

---

### Post by StefanoCole on 2006-09-19
Well, you can try Acidrip. Look at the following link for a simple guide: [http://survivor.sarovar.org/AcidRip_Simple.html]("http://survivor.sarovar.org/AcidRip_Simple.html")

Stefano

---

### Post by phibuntu on 2007-01-17
Thank you all 

I finally solved it using DVD::RIP.

My problem was, that I had to use "XVID" codec (the divx-codec did not work).

My Problem is solved :)  and I hope, that your mentioned tools will help others to do their jobs.

---

### Post by bllambert on 2007-04-23
What settings did you use?  I tried this over the weekend.  It took several hours, and then the Xvid CD did not load in my home DVD Player.  The DVD player has no problems with files that I have downloaded in the Xvid or Divx formats.  I am assuming I didn't set it up right.  Any tips would be appreciated.

---

### Post by Selmer79 on 2007-04-23
> **phibuntu said:**
> Thank you all 

I finally solved it using DVD::RIP.

My problem was, that I had to use "XVID" codec (the divx-codec did not work).

My Problem is solved :)  and I hope, that your mentioned tools will help others to do their jobs.

No need to feel bad about that though, XviD dominates DivX hands down in quality.. Only thing now is that h.263 (DivX/XviD) is getting "outdated".. The new MPEG-4 standard (h.264) is coming in fast and hard, and for a good reason!

---

### Post by phibuntu on 2007-04-25
Sorry, I have not written down the configuration. 
All I remeber is that the format was "xvid" and the size was 1 CD (650MiB).
So the result is just one large *.avi file.
I never used it again, because all other DVDs I have baught, work fine in my player.

Sorry

---

### Post by bllambert on 2007-04-26
Thanks anyway.  I will keep playing with it.  How many hours did it take to convert the movie for you?

---

### Post by Selmer79 on 2007-04-26
> **bllambert said:**
> Thanks anyway.  I will keep playing with it.  How many hours did it take to convert the movie for you?

Video-conversion times vary greatly depending on your CPU speed, number of CPUs/cores, memory, memory-timings, what filters you use on the video, how many passes you do etc..

A simple 2-pass encoding on my computer (AMD64 X2 4600+ w/ 4GB RAM) with only a small crop and resize (no de-interlacing) is done in about 90% of the time it would take to play the source.
That is, a 45 minute episode of 24 takes about 40 minutes to do a full 2-pass video-encode with audio-conversion.

---

