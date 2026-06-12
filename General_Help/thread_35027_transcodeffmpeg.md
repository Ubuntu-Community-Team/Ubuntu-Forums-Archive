---
title: "transcode/ffmpeg"
date: 2005-05-17
forum: General Help
---

### Post by forkboy on 2005-05-17
I'm trying to encode some video files. I finally got transcode installed, but now I get ```
[encode_ffmpeg] mpa codec not found !
[transcode] warning : (encoder.c) audio export module error: init failed
[transcode] critical: failed to init encoder
``` 
I read somewhere that compiling ffmpeg from source may help so I tried that, but no luck. Any help please?!

---

### Post by momo66 on 2005-05-17
I would remove transcode using sudo apt-get remove transcode and then reinstall.

Use the steps in ubuntuguide.org exactly and you shouldnt have a problem.

Make sure your sources.list is like it is in the guide.

The key line for installing transcode is 

```
sudo apt-get -t testing install transcode
```

Hope this helps.

---

### Post by forkboy on 2005-05-17
Thanks but didn't work, still get the same error

---

