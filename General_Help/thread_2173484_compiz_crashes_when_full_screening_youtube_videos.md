---
title: "compiz crashes when full screening youtube videos"
date: 2013-09-09
forum: General Help
---

### Post by Kr0nZ on 2013-09-09
Whenever I try to fullscreen a youtube video the video freezes and after a few seconds I get a message saying "Compiz has closed unexpectedly"

this only happens with videos from youtube, videos from other sites fullscreen fine.
Im using Chromium browser on Ubuntu 12.04

And my crash log if it helps:
[http://pastebin.com/rcTrpi2Y](http://pastebin.com/rcTrpi2Y)

---

### Post by Kr0nZ on 2013-11-26
After just deciding to deal with this problem for the last couple months, I finally found the solution well trying to solve a different problem with youtube.

I just needed to remove 'chromium-codecs-ffmpeg' and install 'chromium-codecs-ffmpeg-extra'

Found this solution here:
[http://askubuntu.com/questions/309610/chromium-browser-not-loading-youtube-video#answer-316722](http://askubuntu.com/questions/309610/chromium-browser-not-loading-youtube-video#answer-316722)

---

