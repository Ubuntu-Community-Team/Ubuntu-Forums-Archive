---
title: "Put FFmpeg in the ./Core directory? Huh?"
date: 2008-04-01
forum: General Help
---

### Post by Ripfox on 2008-04-01
I am trying to use BAMVC to convert files to .amv for my video mp3 player, and i get this error...

FFmpeg could not be spawned. Please check if it is present in the ./Core directory

---

### Post by Ripfox on 2008-04-01
Bump, just got this thing, eager to try it out! :)

---

### Post by Ripfox on 2008-04-01
Ok getting a little further, copies the ffmpeg file from /usr/bin to the ./Core directory inside the BAMVC folder, then got "ffmpeg error 1"

I think it needs a patched ffmpeg?

---

### Post by Ripfox on 2008-04-01
Ok talking to mahself here, downloaded the patched ffmpeg, put it in the core directory, conversion SUCCEEDED! YA! 

Moved the file to the player...File format error! NOOOO!

??

---

### Post by Ripfox on 2008-04-01
Ok, for anyone that may become interested in file conversion to .amv format:

[http://www.bytessence.com/bamvc.html](http://www.bytessence.com/bamvc.html)

The ffmpeg file in the ./Core directory claims to be the one from AMV-Codec-Tools, but it wouldn't work. So I went and downloaded the patched ffmpeg for linux there and replaced the one in the ./Core directory of BAMVC and made it executable.

The errors i was getting on the player were due to the wrong output size, so it was EBKAC...:)

I chose the correct screen size and used 4 fps (which is all that would play smoothly) but hey, it works! Great job btw to the guys who came up with a linux version of BAMVC.

---

### Post by Mud.Knee.Havoc on 2008-04-13
hey, I just got a chipod, too, and am playing around with converting to .amv.  Anyway, I got to the point where you had your problem.  I googled the error, which is what brought me to your post.  Anyway, at first I thought that it might be looking for FFmpeg instead of ffmpeg (case sensitive), so I copied the file and renamed it.  Then I made sure that both files were executable (as well as BAMVC in the other directory).  It worked fine after this.  So I think your problem may have been with ffmpeg not being executable... and when you replaced it with your own from /usr/bin, it already was executable. :)  That's my theory, anyway.  

My video is already 30% ready (in the time it took me to write this - impressive!).

---

### Post by Ripfox on 2008-04-15
Yep...works like a charm, but watch the "output" settings on the player and I could only get 4 fps to play smoothly...:)

---

