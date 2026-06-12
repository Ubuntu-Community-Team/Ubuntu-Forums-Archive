---
title: "What is the correct way to expose extra binaries from a snap package?"
date: 2018-09-18
forum: General Help
---

### Post by ikazama on 2018-09-18
Having installed the ffmpeg snappy package on 18.04 I've only got the ffmpeg bin exposed under /snap/bin/.

Let's say I want ffprobe to be exposed under /snap/bin/ as well. How do I do it the snappy way?

---

### Post by mc4man on 2018-09-18
Well not much you can do as far running in manner you run the ffmpeg from the snap,
[https://github.com/snapcrafters/ffmpeg/issues/3](https://github.com/snapcrafters/ffmpeg/issues/3)
I guess you could run it from it's current full path, the exact could change.. so currently something like,
/snap/ffmpeg/206/usr/bin/ffprobe

ex. 
/snap/ffmpeg/206/usr/bin/ffprobe -show_streams /path/to/a/filename

---

### Post by ikazama on 2018-09-19
Thanks for the issue url! The question is resolved.

---

