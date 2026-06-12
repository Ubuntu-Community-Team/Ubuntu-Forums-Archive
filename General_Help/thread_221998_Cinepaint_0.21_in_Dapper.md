---
title: "Cinepaint 0.21 in Dapper"
date: 2006-07-24
forum: General Help
---

### Post by jcornuz on 2006-07-24
Hi !

For photographic work in 16 bits, color management, etc, Cinepaint is a great tool. However, the version provided with Dapper is 0.20 which is buggy - for me at least, it wouldn't save tiffs !!

To avoid the need to compile Cinepaint (and since cinepaint.org doesn't provide .deb) here are my steps:

1/ install cinepaint (version 0.20) so you have the dependencies met.

2/ install alien

3/ download cinepaint-0.21_i386.rpm (or so) from cinepaint.org.

4/ type 'sudo alien -d cinepaint-0.21_i386.rpm' - you get a deb version

5/ remove the 0.20 version of Cinepaint and install your new deb with gdebi

Enjoy deep paint, quick soft proofing & tiff saving... with a gtk1 interface, for now :-k 

Take care,

Joël

_______________________________

[jcornuz.awardspace.com]("http://jcornuz.awardspace.com")

---

### Post by zxee on 2006-07-24
Great guide! This should be in with the how to's.

---

### Post by longinus on 2006-07-25
Yep, thanks for the tutorial.
I tried using an older windows version, when I didn't use Ubuntu, but it was buggy as hell. I tried using it for rotoscoping, instead of normal compositing progs.

I'll try this version, and in linux. =D

---

### Post by longinus on 2006-07-25
I'm having a problem... I followed your steps, but when I try to install the new deb I get this..

> trying to overwite '/user/share/applications/cinepaint.desktop', which is also in package cinepaint-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)

Do you have a clue why?
Thanks

---

### Post by jcornuz on 2006-07-26
Hello Longinus !

I think I wasn't clear enough: when I say "remove cinepaint-0.20", I mean: "you need to remove cinepaint, cinepaint-datas and libcinepaint". Sorry for the confusion.

Hope this helps.

Take care,

Joël

PS: Cinepaint for now works only in Linux - the Windows version has been given up a while ago due to difficulties with gtk-1.2 on this platform...

PPS: For my information, what is "rotoscoping" ??

________________________________________

[jcornuz.awardspace.com]("http://jcornuz.awardspace.com")

---

### Post by MrSmith on 2006-07-26
Here is a good explaination:

[http://en.wikipedia.org/wiki/Rotoscope](http://en.wikipedia.org/wiki/Rotoscope)

Hope this helps,
MrSmith

---

### Post by longinus on 2006-07-26
> **jcornuz said:**
> I think I wasn't clear enough: when I say "remove cinepaint-0.20", I mean: "you need to remove cinepaint, cinepaint-datas and libcinepaint". Sorry for the confusion.

Aaaaaa, now it worked! Thanks! :D 

The wikipedia link MrSmith gave explains it better than me. But I used the term in a general way, not only for tracing over for animation. I use it for cleaning up frames... "The term "rotoscoping" is now generally used for the corresponding all-digital process of tracing outlines over digital film images to produce digital mattes.". I work with stop-motion animation, and sometimes you have to clean some stuff that support the puppets. 
Cinepaint has a tool called Flipbook.. it lets you flip to frames sequence like image0001, image0002, etc... in a very easy away.. autosaving the frames and stuff like that.

Sorry for the huge OT text..

---

### Post by jcornuz on 2006-07-27
Hi !

I only do still photography, so I don't know so much about the "cine" part. Thanks to you and Mr. Smith for enlightening me :-)

Take care,

Joël

___________________________

[jcornuz.awardspace.com]("http://jcornuz.awardspace.com")

---

