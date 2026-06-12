---
title: "Using ffmpeg to convert Mpeg2 files to AVI"
date: 2008-07-07
forum: General Help
---

### Post by 50words on 2008-07-07
How would I use ffmpeg (or something else, if you have a better app in the repos) to convert a muxed Mpeg2 file from my hard drive camcorder to a more PiTiVi-friendly file format like AVI?

I have not been able to figure out anything from the documentation on the ffmpeg website.

---

### Post by DJYoshaBYD on 2008-07-07
get a DIVx or xVID encoder, and when you do it, just set the extension for avi..

---

### Post by 50words on 2008-07-07
I have no idea what you are talking about.

---

### Post by DJYoshaBYD on 2008-07-07
lol.. ok

an encoder will basically transform a file into another file.. thats the just of it.. dont worry about anything past that for now...

DIVx and xVID and file formats, like mp3 and wav.. divx/xvid encoders, take a video file, and make them into divx/xvid files.. the upshot, of which, is you can give it many different file types.. mpg, mp4, avi, etc..

It will take your mpeg2 that is NOT encoded with divx, and make an avi (or whatever you want) that IS divx/xvid encoded.. which is good.. divx-xvid is the ****..

to clear it up, divx is a commercial compression format.. xvid is the free one... from what I have heard, the people that wrote the xvid encoder format used to work for the same company that made divx.. they left, and made xvid in spite.. lol

so yeah.. get a divx or xvid encoder, and use that to transform your file.. look up xvid in synaptic or whatever your package manager is..

---

### Post by 50words on 2008-07-07
I don't see any encoders in add/remove programs. Is there one in particular that you would recommend. I thought ffmpeg was an encoder that handles, among other things, Xvid.

---

### Post by DJYoshaBYD on 2008-07-07
it may be.. I dont know... the only thing I have used ffmpeg for is playing the videos on final fantasy vii... if it encodes in divx/xvid, then use it...:)

---

### Post by 50words on 2008-07-07
Yes, but how?

---

### Post by cariboo on 2008-07-07
You might be better of using avidemux to convert your video it is available in the repositories and you can use Add/Remove Programs or Synaptic package manager to install it.

Jim

---

### Post by unutbu on 2008-07-07
```
ffmpeg -sameq -i movie.mpg movie.avi
```
-sameq means same quality
-i means input file

---

### Post by 50words on 2008-07-07
> **cariboo907 said:**
> You might be better of using avidemux to convert your video it is available in the repositories and you can use Add/Remove Programs or Synaptic package manager to install it.

Jim

Avidemux crashes at the mere sight of a video file on all of the computers I have tried to use it with.

---

### Post by 50words on 2008-07-07
> **unutbu said:**
> ```
ffmpeg -sameq -i movie.mpg movie.avi
```
-sameq means same quality
-i means input file

Piece of cake. Thanks!

---

