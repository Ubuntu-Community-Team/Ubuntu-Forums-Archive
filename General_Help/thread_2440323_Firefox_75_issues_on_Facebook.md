---
title: "Firefox 75 issues on Facebook"
date: 2020-04-08
forum: General Help
---

### Post by stephanie-s on 2020-04-08
Running Ubuntu 18.4 on a Galago Pro  Firefox was updated to v75 a/nd I've been having issues on Facebook.  Videos in Stories no longer play, and gifs in the news feed no longer animate as they did in the previous version.  Anyone else experience this.  Any ideas?

---

### Post by mastablasta on 2020-04-09
i have found no such issues. i also do not have any report from wife that uses facebook more that she has any issues.

i would always try another browser, to see if it is a browser or some driver or OS issue. install chromium and try it there.

---

### Post by stephanie-s on 2020-04-09
I installed Opera and all media plays as usual, but in Firefox75 video's won't play in FB or Redit. If I inspect one of the video's that won't play I see this:

> All candidate resources failed to load. Media load paused. popular
The video on this page can’t be played. Your system may not have the required video codecs for: video/mp4;codecs="avc1.4d400d", audio/mp4;codecs="mp4a.40.2" popular
HTTP “Content-Type” of “video/mp4” is not supported. Load of media resource [https://v.redd.it/ns8wf7cyzmr41/DASH_96](https://v.redd.it/ns8wf7cyzmr41/DASH_96) failed. popular
Cannot play media. No decoders for requested formats: video/mp4

Any ideas?

---

### Post by mastablasta on 2020-04-09
check if codecs are installed and reinstall them if they are. if they are installed it looks like firefox doens't know that for some reason. 

i wonder if it would help to delete firefox config files. but don't do it yet. not at least someone can confirm this. but these are safe to try: [https://support.mozilla.org/en-US/kb/fix-common-audio-and-video-issues](https://support.mozilla.org/en-US/kb/fix-common-audio-and-video-issues)

---

### Post by stephanie-s on 2020-04-09
Thanks for the tips.  I'll give the link you provided a try.  Funny how all video's in FB and Reddit work in Opera, so I don't think it's an OS problem.

---

### Post by sdsurfer on 2020-04-09
Opera, now there's a name I haven't heard in a while. :-D Also running 75.0 here on a Gazelle, works fine but I would consider the animated GIF loss a good thing. :-)

As suggested, it's telling you what's up, odd that out of the box it's giving you issues.

---

### Post by stephanie-s on 2020-04-09
Thanks for thetips everyone.  I ended up doing:

```
sudo apt-get purge firefox
```

and re-installing it. Works great again.

---

