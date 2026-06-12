---
title: "[SOLVED] Firefox - MPlayer Plugin - Sound but no Video"
date: 2008-02-21
forum: General Help
---

### Post by stooshbunutu on 2008-02-21
I installed on the prompt mplayer plugin for firefox (after finding xine not to work at all) and so now I get sound streamed in but not video.

Is there anyone outthere who can help me please?

As an alternate I do have the VLC plugin installed which is a good stand alone player but it doesn't seem to do anything at all as a firefox plugin. Any Ideas?

Thanks in advance for any help :)

---

### Post by stooshbunutu on 2008-02-21
I managed to solve this by following the tutorial on [this thread]("http://ubuntuforums.org/showthread.php?t=661833")

All works fine now :)

---

### Post by dooma on 2008-04-28
Can someone help me? I've gone through the steps of this tutorial and spent several hours trying different things to no avail.  

Here is the problem:

1) I just upgraded from Gutsy to Hardy Heron. 
2) Now when I go to a site like [www.apple.com/trailers](www.apple.com/trailers), mplayer plugin plays the audio, but NO VIDEO. 
3) changing preferences does not affect it. Flash works fine. 
4) Prior to the upgrade to Heron, everything worked great

I am using a Thinkpad T60P with Hardy Heron installed (as of April 26)
It has the Fire GL graphics card, so I'm using FGLRX. 

Please - any help would mean the world to me.

---

### Post by rahduke on 2008-06-17
i'm having the same problem, in fact i'm having nothing but problems with Firefox3 and the mplayer problem can't get anything to stream correctly since upgrading to 8.04

---

### Post by Hellaxe on 2008-06-18
Same here. I can see one video, but after that no more videos. Only sound is played. Firefox3 is the main browser but i've tryed opera and i have the same issue.
I checked with the processes and it has one opene that i can't kill. only with reboots the stupid process is killed.

---

### Post by daspooky on 2008-06-22
Same here. Since I installed Hardy I'm getting the same problem... With Gutsy playing videos in Firefox 2 with mplayer plugin was not a problem. Changing output from XV to X11 solves the problem. But I shouldn't have to do that in order for it to work.

Here are more details about this error. Because downloading a video from Internet, and opening it with mplayer through a console window, give more details about the problem:

[VO_XV] Could not find free Xvideo port - maybe another process is already
[VO_XV] using it. Close all video applications, and try again. If that does
[VO_XV] not help, see 'mplayer -vo help' for other (non-xv) video out drivers.
Error opening/initializing the selected video_out (-vo) device.

---

