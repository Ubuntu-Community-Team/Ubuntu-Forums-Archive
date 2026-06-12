---
title: "jumpy video playback in totem after pause/resume or skipping."
date: 2005-10-17
forum: General Help
---

### Post by bb002 on 2005-10-17
I had video issues in hoary when playing mpeg encoded video files but managed to fix it with a quick gst-register. I've since upgraded to breezy with a fresh install and installed all the nessecary mpeg components did gst-register.

I open a video in totem and it plays fine until I do one of two things. One pause/resume the video or skip to a different part of the video. After doing either of these the sound is ahead of the video by a few seconds while the video has become very jerky. If I watch the video from beginning to end it plays fine.

I tried reinstalling gstreamer and totem but got nothing. Even tried reinstalling breezy. I found a few faqs but they only told my what gstreamer plugins i need but i already knew which ones i needed.

One covered installing xine but it merely crashes after opening any video file.

---

### Post by ecobuntu on 2005-10-17
[QUOTE=bb002]I had video issues in hoary when playing mpeg encoded video files but managed to fix it with a quick gst-register. I've since upgraded to breezy with a fresh install and installed all the nessecary mpeg components did gst-register.

I open a video in totem and it plays fine until I do one of two things. One pause/resume the video or skip to a different part of the video. After doing either of these the sound is ahead of the video by a few seconds while the video has become very jerky. If I watch the video from beginning to end it plays fine.

I tried reinstalling gstreamer and totem but got nothing. Even tried reinstalling breezy. I found a few faqs but they only told my what gstreamer plugins i need but i already knew which ones i needed.

One covered installing xine but it merely crashes after opening any video file.[/QUOTE]

do you have the xine-engine installed?  maybe that would help

---

### Post by bb002 on 2005-10-17
wouldn't that have installed with xine-ui? I'm about to leave work I'll find out when i get home. since 5.10 is on my home machine.

---

### Post by hajk on 2005-10-18
Try using dma on your DVD/CD drive,

$ sudo hdparm /dev/hdc   ...or whatever drive

if dma is not on (= 1), then

$ sudo hdparm -d1 /dev/hdc

and, if this solves the jerkiness, make it permanent by 

$ sudo gedit /etc/hdparm.conf

and adding at the end 

/dev/hdc {
dma = on
}

For /dev/hdc use the device that your DVD player is actually on.
It solved a similar problem on my player.

---

