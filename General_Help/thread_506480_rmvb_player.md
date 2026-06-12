---
title: "rmvb player"
date: 2007-07-21
forum: General Help
---

### Post by ali780 on 2007-07-21
Hi 
I am using ubuntu 7.04.
How can I play rmvb file?

---

### Post by Daveth on 2007-07-21
this post

[http://ubuntuforums.org/showthread.php?t=171548](http://ubuntuforums.org/showthread.php?t=171548)

suggests "Xfmedia can read rmvb."
"sudo aptitude install xfmedia"

never tried it myself though

---

### Post by wildkarde on 2007-08-05
xfmedia did not work for me.  I would suggest either using mplayer or using realplayer.

I recommend realplayer as i was not able to resize video with mplayer.  it kept the original resolution even after maximizing the window.  

According to [link]("https://help.ubuntu.com/community/RealplayerInstallationMethods")

[http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb](http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb)

After installing it, i was having issue playing the video.  It was slow and choppy.  

I was able to fix it by following this.  [http://blogorrhoea.wordpress.com/2006/03/01/linux-realplayer-choppy-video-fix-how-to/](http://blogorrhoea.wordpress.com/2006/03/01/linux-realplayer-choppy-video-fix-how-to/)

```
aoss realplayer
```

Hope this helps.

---

### Post by gaelfx on 2007-08-30
@wildkarde: That is the most remarkably easy and sensible solution I have seen for this yet. Thank you soooo much! :popcorn:

---

### Post by wildkarde on 2007-08-30
You're welcome. :)

---

