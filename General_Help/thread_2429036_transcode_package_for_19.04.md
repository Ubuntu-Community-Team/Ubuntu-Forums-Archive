---
title: "transcode package for 19.04?"
date: 2019-10-12
forum: General Help
---

### Post by catalyst1987 on 2019-10-12
Hello,
 I am unable to find the transcode package at 19.04.  Latest I can find it is at 18.04 but the version there requires libvacodec57 when 19.04 has libvacodec58.  Will a transcode package be developed for 19.04 or will I have to find some way to downgrade?

Many Thanks!

---

### Post by PaulW2U on 2019-10-12
transcode was removed from Ubuntu during the Cosmic (18.10) development period.
Reason: un-maintained and buggy.
Obviously it remains in releases prior to Cosmic. See bug report [#1787222]("https://bugs.launchpad.net/ubuntu/+source/transcode/+bug/1787222")

---

### Post by TheFu on 2019-10-12
I have no idea what transcode does, but **ffmpeg**, **handbrake** come to mind as ways to transcode video and audio codecs.  If you just need audio, there are others, often specific to the desired output format, but ffmpeg usually does fine if you aren't too picky about almost 1-for-1 quality and file size isn't that important.

---

### Post by hk42 on 2019-10-12
I've never heard of "transcode".
Why don't you use "Handbrake" ?

---

