---
title: "Converting Video for Mobile Phones"
date: 2006-07-02
forum: General Help
---

### Post by NiceGuy on 2006-07-02
Right here is the problem:

I own a Nokia 6680 which runs the Symbian 60 OS and I would like to put some video clips onto it to watch when I'm on the bus etc.

Does any one know how I can convert normal movie files (avi mpeg etc.) to a format I can play on my phone? At the moment the only formats I can play (I think) are 3gp and rm files.

After a bit of searching I found a way to compress avi's so I can play them on my phone using a program called SmartMovie but unfortunately I only have the demo version of that program and don't really want to pay for the full version.

So does anyone know of a free alternative to SmartMovie or a good program for converting avi/mpeg files to either 3gp or rm. I would hope there is 'something' out there to do this as there seem to be LOADS of windows apps to do this!

---

### Post by Lycaon on 2006-07-02
I just did a quick google entry and i hope this helps you:

[http://www.allaboutsymbian.com/archive/t-22589.html]("http://www.allaboutsymbian.com/archive/t-22589.html")

have fun reading... ;)

---

### Post by NiceGuy on 2006-07-02
Thanks but I already found that link and I agree with the last guys sentiments: 
"Can someone translate this in plain steps? I don't speak cvs" lol 8-[  

So It seems I need a special version of ffmpeg that I need to compile from CVS and then I need to import the 3pg codec...

sigh...

this may take a while! I can't believe how difficult this is going to be! There MUST be a easier way! Anyone got any ideas where I can find a .deb with the special cvs version of ffmpeg with the codecs installed? Or would that be hoping for too much? I would hate to have to use windows to do this!

---

### Post by scxtt on 2006-07-02
check out [http://www.niemueller.de/wiki/?ConvertVideoTo3GP](http://www.niemueller.de/wiki/?ConvertVideoTo3GP)

i think it's basically mencoder and ffmpeg ...

---

### Post by NiceGuy on 2006-07-02
Well I've had some success at last! After following the guide given in scxtt's link (thanks btw + thanks to Lycaon for your link*) I installed ffmpeg from cvs with the 3gp codecs and I've managed to make a 3gp file. The only problem is that the quality in naff but I guess I'll just have to tweak the settings till I get them to an acceptable level!

*I'll have to re-read that one to see if I can get some ideas for settings.

---

### Post by Zhukov on 2006-07-14
Im developing a quick solution for that, it automaticaly install the newest ffmpeg and the required codecs. Im working on the GUI now. Hope to have some progress in the next days.

---

### Post by NiceGuy on 2006-07-14
Wow! That sounds fantastic, keep us posted!

---

### Post by Zhukov on 2006-07-14
Done. Posted on HOWTOs, Tips & Tricks.

---

### Post by s.deleeuw on 2007-06-17
Here is a script that converts any (MPlayer compatible) video to a small XviD file, optimized for mobile phones.
It needs MEncoder with XviD and Lame MP3 support (Feisty's packages are fine).
Tested with Ubuntu 7.04 and Nokia E65 / SmartMovie 3.41.

```
video2mob.sh - Prepare any video clip for playback on your mobile device.
Written by Sander de Leeuw

Usage: video2mob.sh <input> [output] [options]

 -crop yes|no           crop video to 4:3 before scaling (yes)
 -width n               scaled width (320)
 -height n              scaled height (240)
 -fps n                 frames per second (15)
 -vbr n                 video bitrate (250kbit/s)

 -abr n                 audio bitrate (48kbit/s)
 -stereo yes|no|joint   stereo, joint-stereo or mono (no)
 -resample 11-44|no     sample rate (22KHz)
```

---

### Post by sliorda on 2007-12-08
great script, thank you.

do you know why the movie plays nice on ubuntu, but loses sync on the phone (smartmovie 3.41 on E65)?

---

### Post by s.deleeuw on 2007-12-09
Does it really "loses" sync on your phone?
On my phone, there is a small but constant delay between video and audio.
Fixed this by the "delay" setting in SmartMovie's options menu.

---

