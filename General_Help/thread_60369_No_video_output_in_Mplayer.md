---
title: "No video output in Mplayer"
date: 2005-08-27
forum: General Help
---

### Post by cnayak on 2005-08-27
I installed a CVS version of Mplayer with all the required codecs. However on playing any video file, the video window doesn't open up, however the audio stream plays.I guess the following peice of output pinpoints the error:

 [I]vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
vosub_vidix: Couldn't find working VIDIX driver
[/I]

 How do I change the driver? I have an Intel Extreme 2 Mobile graphics adapter and haven't installed any driver from Intel.

---

### Post by arnieboy on 2005-08-27
[QUOTE=cnayak]I installed a CVS version of Mplayer with all the required codecs. However on playing any video file, the video window doesn't open up, however the audio stream plays.I guess the following peice of output pinpoints the error:

 [I]vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
vosub_vidix: Couldn't find working VIDIX driver
[/I]

 How do I change the driver? I have an Intel Extreme 2 Mobile graphics adapter and haven't installed any driver from Intel.[/QUOTE]
do the following:
```
sudo gedit /etc/mplayer/mplayer.conf
```
when the file opens change **vo=xv,**
save and close. test mplayer now.

---

