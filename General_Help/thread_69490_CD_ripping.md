---
title: "CD ripping"
date: 2005-09-27
forum: General Help
---

### Post by GrumpyBob on 2005-09-27
I've been trying grip to rip tracks for CDs to upload to an iPod.  I have installed lame as the encoder.  Everything seems in order with the configuration of grip (at least as far as I can tell!).  Grip does *eventually* rip all the tracks to mp3, but it takes a devil of a long time to do it - it says it's ripping at 0.3x!  

I am sure that in previous distros that I have tried CD ripping wasn't this slow.  Any suggestions as to how to perk the speed up a bit?

Robert

---

### Post by jeremy on 2005-09-27
Do you have dma enabled for your cd?

---

### Post by GrumpyBob on 2005-09-27
[QUOTE=jeremy]Do you have dma enabled for your cd?[/QUOTE]

Thanks jeremy - talk about rapid response!

I don't know, will check when I get home.

After I posted, I did another search of this forum (I did this a few days ago) and found this:
[http://ubuntuforums.org/showthread.php?t=47112&highlight=CD+ripping](http://ubuntuforums.org/showthread.php?t=47112&highlight=CD+ripping)

So I guess the solution is there, and the moral is to do a better search just before posting!

Robert

---

### Post by GrumpyBob on 2005-09-28
I tried the tips in the document linked from [http://ubuntuforums.org/showthread.p...ght=CD+ripping](http://ubuntuforums.org/showthread.p...ght=CD+ripping)
It worked very well for one CD, then returned to the slow 0.3X speed.

Just off to read up on dma and hdparm

Any suggestions most welcome!

Robert

---

### Post by jeremy on 2005-09-28
[http://ubuntuforums.org/showthread.php?p=93238#post93238](http://ubuntuforums.org/showthread.php?p=93238#post93238) has helped a lot of people (including myself!) .

---

### Post by manicka on 2005-09-28
I find goobox very good for ripping cd's

---

### Post by GrumpyBob on 2005-09-29
[QUOTE=manicka]I find goobox very good for ripping cd's[/QUOTE]

How do you set goobox to rip to mp3 (e.g. via lame) - I can't see any configuration options!

Robert

---

### Post by manicka on 2005-09-29
[QUOTE=GrumpyBob]How do you set goobox to rip to mp3 (e.g. via lame) - I can't see any configuration options!

Robert[/QUOTE]
If the mp3 options are greyed then you need to install the lame package.

---

### Post by GrumpyBob on 2005-09-29
[QUOTE=manicka]If the mp3 options are greyed then you need to install the lame package.[/QUOTE]
I had installed lame, it's what I'm using with grip - doesn't seem to come up as an mp3 option with goobox.
What's weird is that since I've enabled dma, sometimes grip works at 7X, sometimes at 1X, and soemtimes at 0.3X.  Not sure what the variable is here!
Robert

---

### Post by manicka on 2005-09-29
If you have lame then just go the Edit--> Preferences --> Encoding and choose your desired level for mp3 encoding

---

### Post by GrumpyBob on 2005-09-30
[QUOTE=manicka]If you have lame then just go the Edit--> Preferences --> Encoding and choose your desired level for mp3 encoding[/QUOTE]


Lame works just fine with grip.  In goobox I am unable to set anything.  EDit-Preferences leads to a dialogue box in which I can select a CD drive, nothing else.  Clicking CD-Extract Tracks leads to a dialogue box in which mp3 is greyed out.

I'm back with grip, which seems to do what I want, even if the CD-ROM speed (presumably not a grip issue) is really flaky.

Robert

---

### Post by mcduck on 2005-09-30
Do you have paranoia, extra paranoia, scratch detection and scrath repair set on? These all have serious effect in ripping speed.

With all these on, I get ripping speeds of 6x to 8x, and switching those off increases speed up to over 40x.

Anyway, I'd rather keep them on and get good mp3s slowly than switch them off for speed and loose the quality..

---

### Post by GrumpyBob on 2005-09-30
[QUOTE=mcduck]Do you have paranoia, extra paranoia, scratch detection and scrath repair set on? These all have serious effect in ripping speed.
With all these on, I get ripping speeds of 6x to 8x, and switching those off increases speed up to over 40x.
Anyway, I'd rather keep them on and get good mp3s slowly than switch them off for speed and loose the quality..[/QUOTE]

They are all off.  I can get up to 6X, usually it's 1X, and sometimes 0.3X.
dma is enabled.

Robert

---

### Post by Quirky on 2005-09-30
I think the lame you need is gstreamer-lame, which is not in universe and needss to be installed from elsewhere.

---

### Post by GrumpyBob on 2005-10-02
[QUOTE=Quirky]I think the lame you need is gstreamer-lame, which is not in universe and needss to be installed from elsewhere.[/QUOTE]


Mmmm...ripping to wav is slow, encoding to mp3 is pretty fast.

I'll just put up with 1X ripping for the time being.  Anyway, thanks for all the help!

Robert

---

### Post by Quirky on 2005-10-09
I've been having terrible problems with grip (and Sound Juicer just doesn't work.) - grip often just stopped completely on a CD, falling from X1.2 to X0.1... I think it uses cdda2wav 'under the hood' as this displays the same slowness. In the end I have had to use VLC to rip the cd to wav, then lame each track. VLC absolutely flies along compared to the other programs, ripping a CD in minutes compared to hours with grip. The problem of course is that VLC has no CDDB renaming incorporated, but for sheer speed I am willing to put up with this in the mean time. DMA is enabled. Anyone know what's going on?

---

