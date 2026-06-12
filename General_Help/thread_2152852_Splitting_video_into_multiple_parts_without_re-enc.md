---
title: "Splitting video into multiple parts without re-encoding?"
date: 2013-06-09
forum: General Help
---

### Post by colobix on 2013-06-09
Hello. I tried using ffmpeg to do the job for me, but I lose the sound and it doesn't split where I tell it to split.
Here's the code I use:
```
ffmpeg -i input.avi -an -vcodec copy -acodec copy -ss 00:23:16 -t 00:47:02 output1.avi -an -vcodec copy -acodec copy -ss 00:47:04 -t 01:10:50 output2.avi -an -vcodec copy -acodec copy -ss 01:10:52 -t 01:34:40 output3.avi -an -vcodec copy -acodec copy -ss 01:34:42 -t 01:58:29 output4.avi
```
I've tried without acodec and with libmp3lame instead of copy.
But nothing seem to work.
I used smplayer to see where the episodes start and end
Also, is there an actual app I can use for this instead so that I don't have to use the terminal and so I can see where I'm splitting the video?

---

### Post by andrew.46 on 2013-06-11
Not sure that you can cut multiple segments in a single command like that, and the -an option is probably responsible for the lack of audio:

```

       -an (output)
           Disable audio recording.

```

---

### Post by VanillaMozilla on 2013-06-11
The only program I know of that can accomplish that basic, essential task is Avidemux.  Open audio and video in "Copy" mode.  Set markers A and B.  If your file type (e.g., .VOB) does not encode each frame separately, A and B should be set on key frames.  Save to the same file type that you opened.  It will save the clip without transcoding.  It's astonishingly fast since you don't have to render anything.  You do have to save one clip at a time, but it's easy to do.

You may have trouble getting a sufficiently recent version, however.  Versions prior to 2.6.1 have severe synch problems with some files, and I would suggest version 2.6.4 if you can get it.

---

### Post by HiImTye on 2013-06-11
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
mencoder ;)
[http://www.misterhowto.com/?category=Computers&subcategory=Video&article=trim_or_split_with_mencoder](http://www.misterhowto.com/?category=Computers&subcategory=Video&article=trim_or_split_with_mencoder)

---

