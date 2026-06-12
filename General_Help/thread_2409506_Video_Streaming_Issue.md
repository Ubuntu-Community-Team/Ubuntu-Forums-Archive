---
title: "Video Streaming Issue"
date: 2019-01-03
forum: General Help
---

### Post by mandagorn on 2019-01-03
I've taken the plunge and installed the latest version of Ubuntu - having been a long time Windows user (I was using W10)

However I stream a lot of content....I have no problem with sites like youtube but am having issues with others. The video shows but when I click play it just starts to buffer.....and that's it.....just buffers non stop.

I've tried various fixes.....installing the restricted content via the console.
Installing Chrome and Chromium
Installing VLC etc.

So any help would be appreciated.

---

### Post by HermanAB on 2019-01-03
If you install a bunch of video players, codecs and libraries, then they will pull in more libraries and codecs and eventually things should work:

sudo apt install ffmpeg mplayer xine vlc x264 x265

Another tip:
If you run the web browser (chromium or firefox) from a terminal, then you will be able to see the error messages, which may give you a clue as to what is the matter.

---

### Post by Autodave on 2019-01-03
Also possible that you have a display adapter problem.  What video card are you running? Did you install a driver for it? If so, what one and where did you get it from?

---

