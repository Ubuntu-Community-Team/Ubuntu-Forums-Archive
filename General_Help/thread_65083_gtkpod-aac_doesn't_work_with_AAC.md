---
title: "gtkpod-aac doesn't work with AAC"
date: 2005-09-12
forum: General Help
---

### Post by atf487 on 2005-09-12
Now, I've tried a ton of different versions of this software, and tried compiling the source too (but i couldn't get it to compile). None of the versions work with aac, it always gives an error about an mp4 library. After searching, this problem has never been fixed. 

Anyway, I'm getting a shuffle soon, and having aac support is mandatory. I really don't want to use windows just to use my shuffle. 

Is there any way for this to work? Also, converting to .mp3 is out of the question...

thanks.

---

### Post by arnieboy on 2005-09-13
[QUOTE=atf487]Now, I've tried a ton of different versions of this software, and tried compiling the source too (but i couldn't get it to compile). None of the versions work with aac, it always gives an error about an mp4 library. After searching, this problem has never been fixed. 

Anyway, I'm getting a shuffle soon, and having aac support is mandatory. I really don't want to use windows just to use my shuffle. 

Is there any way for this to work? Also, converting to .mp3 is out of the question...

thanks.[/QUOTE]
do the following and see if it helps:
```
sudo apt-get install faac gstreamer0.8-faac gtkpod-aac libfaac0 libfaac-dev
```

---

