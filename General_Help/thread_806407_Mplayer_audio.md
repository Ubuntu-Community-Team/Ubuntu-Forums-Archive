---
title: "Mplayer audio"
date: 2008-05-24
forum: General Help
---

### Post by cosine352 on 2008-05-24
Hi all,
I have a problem with Mplayer. It is playing audio faster than video (audio video are not sync). Do anyone know how to fix it? 
I am using this code to play the file

> mplayer -vo x11 -fs -zoom "filename"

If I right click on the file and play with Mplayer I do not have the audio video sync problem. But in this case I can not see it in full screen (In full screen mode the picture size remain same with a large black border). 

thanks for your help.

---

### Post by omababy on 2008-05-25
Have you tried changing the audio and video drivers in the configuration of the gui? A temporary solution may be to use '-' and '+' to delay audio.

---

### Post by cosine352 on 2008-05-25
> Have you tried changing the audio and video drivers in the configuration of the gui? A temporary solution may be to use '-' and '+' to delay audio.

I have tried that one. But no result. 

Thanks for your reply

---

### Post by omababy on 2008-05-25
Best bet prob would be to modify either gnome's or kde's filetype association command adding to it '-zoom'. Gnome it's in /usr/share/applications/mplayer.desktop I think.

---

### Post by FuturePilot on 2008-05-25
Try using the Xv output. Using X11 usually results in no full screen view as you described

---

### Post by omababy on 2008-05-25
I think xv is bringing sync problems.

---

### Post by cosine352 on 2008-05-25
If I try XV I can not see any video (only audio)

> [VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.


I have to use x11.

---

