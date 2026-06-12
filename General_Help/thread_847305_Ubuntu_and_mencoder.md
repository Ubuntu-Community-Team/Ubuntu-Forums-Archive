---
title: "Ubuntu and mencoder"
date: 2008-07-02
forum: General Help
---

### Post by adam35413 on 2008-07-02
I am trying to get mencoder to convert a .mpg file to a .flv file.  On my Pentium 4 box, everything converts fine.  On my Dual-Core Opteron box, the audio is complete static, but the video is fine.  As far as I can tell, I have the same OS version and libraries installed on both.  The command I am running is as follows:
```
/usr/bin/mencoder /pathToFile/BmVpBOTC2EQh3sMc2ADX.MPG -o
/pathToFile/BmVpBOTC2EQh3sMc2ADX.flv -of lavf -oac mp3lame -lameopts
abr:br=40 -ovc lavc -lavcopts
vcodec=flv:vbitrate=400:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -lavfopts
i_certify_that_my_video_stream_does_not_use_b_frames -vf scale=512:384
-srate 22050

```

Any thoughts?  :confused:

---

### Post by adam35413 on 2008-07-02
The issue appears to have been related to this:
[http://ubuntuforums.org/showthread.php?t=551444]("http://ubuntuforums.org/showthread.php?t=551444")

Enabling the backport distro and updating seems to have fixed my issue.

---

