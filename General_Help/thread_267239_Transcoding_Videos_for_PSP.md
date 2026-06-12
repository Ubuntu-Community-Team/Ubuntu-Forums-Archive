---
title: "Transcoding Videos for PSP"
date: 2006-09-28
forum: General Help
---

### Post by mikesena on 2006-09-28
Hi,

I have a whole stack of videos that I want to watch on my PSP that are in rm format.  These play on Ubuntu, but I want to view them on my PSP.  When I had a windows platform, I used to use one of the many video conversion tools available to do this, however I can't now.  I have tried about 5 or 6 different programs, running through wine, but none have worked.  How can I convert my rm movie files into a format for the PSP?  I don't mind if I have to use a wine program, but preferably a native linux would be better.

Ps.  I have been experimenting with !vive, but haven't been able to encode, the encoding window doesn't remain open.

---

### Post by icarus.lnx on 2006-09-28
I've run into this on a couple other forums but this project looks like it may be a good option that's easy to use

[http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/)

The barbaric command line method would be something like ```
ffmpeg -i sourcemovie.avi -f psp -r 14.985 -s 320x240 -b 768 -ar 24000 -ab 32 M4V00002.MP4

or

ffmpeg -i Video.avi -f psp -r 29.970030 -b 768 -ar 24000 -ab 64 -s 320x240 M4V00001.MP4
```

---

### Post by mikesena on 2006-09-28
> **icarus.lnx said:**
> I've run into this on a couple other forums but this project looks like it may be a good option that's easy to use

[http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/)

The barbaric command line method would be something like ```
ffmpeg -i sourcemovie.avi -f psp -r 14.985 -s 320x240 -b 768 -ar 24000 -ab 32 M4V00002.MP4

or

ffmpeg -i Video.avi -f psp -r 29.970030 -b 768 -ar 24000 -ab 64 -s 320x240 M4V00001.MP4
```

does this support rm, and if not, is there another tool i can get that does?  This is going to be very useful regardless, for other videos :)  thanks

---

### Post by icarus.lnx on 2006-09-28
It's just a frontend for ffmpeg so if that has support for rm's pspvc should work

---

### Post by icarus.lnx on 2006-10-04
> **gambol said:**
> It's a pity which i [use]("http://www.winavi.com/psp%20video%20converter.htm") is only for Windows though it works well.

That's what things like Wine are for ;)

I have a [movie player for the GameBoy]("http://www.lik-sang.com/info.php?category=246&products_id=3983&") which has a a prioritory format that I need to use their Windows only software to use, which Wine has been able to do for me. I'll have to look around again to see if anyone has bothered to crack that yet :)

---

### Post by danpre on 2007-08-11
> **icarus.lnx said:**
> I've run into this on a couple other forums but this project looks like it may be a good option that's easy to use

[http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/)

The barbaric command line method would be something like ```
ffmpeg -i sourcemovie.avi -f psp -r 14.985 -s 320x240 -b 768 -ar 24000 -ab 32 M4V00002.MP4

or

ffmpeg -i Video.avi -f psp -r 29.970030 -b 768 -ar 24000 -ab 64 -s 320x240 M4V00001.MP4
```

If you want to see movie title while browsing movies at PSP, you have to add: -title "put your title here":

 ```
ffmpeg -i sourcemovie.avi -f psp  -title "put your title here" -r 14.985 -s 320x240 -b 768 -ar 24000 -ab 32 M4V00002.MP4
```

DANIeL

---

