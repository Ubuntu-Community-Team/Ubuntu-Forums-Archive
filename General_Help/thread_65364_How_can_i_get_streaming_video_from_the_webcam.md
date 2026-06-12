---
title: "How can i get streaming video from the webcam?"
date: 2005-09-13
forum: General Help
---

### Post by drews_blunted on 2005-09-13
Alright so i have a webcam setup in linux 100% working on /dev/video1

My question is i know gaim-vv and other messanger programs do not work with webcams as of yet. But how would i go about setting up a streaming video server on gnome meetings or anyway of getting my pretty face on the cam to another persons computer screen. :) I have tryed a program called motion to stream images to my apache directory that was working well for a moment but then i realized it only took pictures of me when motion was detected. Is there any other way i can get my webcam working well enough for someone to remotly view me and or whats the deal with gnomemeetings?

---

### Post by mlomker on 2005-09-13
Look into VLC.  It's a command-line application, so not so pretty to look at but it'll do what you want.  [Check it out.](http://www.videolan.org/)

---

### Post by arnieboy on 2005-09-13
[QUOTE=drews_blunted]Alright so i have a webcam setup in linux 100% working on /dev/video1

My question is i know gaim-vv and other messanger programs do not work with webcams as of yet. But how would i go about setting up a streaming video server on gnome meetings or anyway of getting my pretty face on the cam to another persons computer screen. :) I have tryed a program called motion to stream images to my apache directory that was working well for a moment but then i realized it only took pictures of me when motion was detected. Is there any other way i can get my webcam working well enough for someone to remotly view me and or whats the deal with gnomemeetings?[/QUOTE]
look at this link too:
[http://www.linux.com/howtos/VideoLAN-HOWTO/softencoding.shtml](http://www.linux.com/howtos/VideoLAN-HOWTO/softencoding.shtml)

---

### Post by anil_robo on 2005-12-17
Hi Arnav

I was trying to play with VLC to somehow stream the video from my webcam to a file on a hard disk. But all it does is to make a 4-bytes file! If it can successfully dump video to a file, then it should be able to stream video to HTTP as well, I suppose.

The intention is, as declared by drews_blunted, is to bypass the absence of video support in GAIM. I looked into the link that you gave to VLC website, but it contains little information for non-techies like me. Someone should write a user-friendly how-to for setting up streaming video server. It'd be of great help to everyone! :)

---

### Post by anil_robo on 2006-03-22
I did it myself! :mrgreen:

[http://www.ubuntuforums.org/showthread.php?t=143732](http://www.ubuntuforums.org/showthread.php?t=143732)

---

