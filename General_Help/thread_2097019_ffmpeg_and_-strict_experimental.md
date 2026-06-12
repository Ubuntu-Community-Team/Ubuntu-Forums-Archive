---
title: "ffmpeg and -strict experimental"
date: 2012-12-21
forum: General Help
---

### Post by Primefalcon on 2012-12-21
I am trying to convert a video to mp4 using ffmpeg

and I get the following message

```
encoder 'aac' is experimental and might produce bad results.
Add '-strict experimental' if you want to use it.
```

however when I do the following

```
ffmpeg -strict experimental -i video.mpeg -same_quant video.mp4
```

all I get is this

```
Unrecognized option 'strict experimental'
Failed to set value '-i' for option 'strict experimental'
```

I am using 12.10 and I never had this issue with previous versions of Ubuntu.....

---

### Post by FakeOutdoorsman on 2012-12-21
> **Primefalcon said:**
> I am trying to convert a video to mp4 using ffmpeg
Note that the mp4 container supports several video formats. The default encoder for mp4 used by ffmpeg will change depending on your version and configuration, either "mpeg4" for MPEG-4 Part 2 video or "libx264" for H.264 video.

> **Primefalcon said:**
> and I get the following message

```
encoder 'aac' is experimental and might produce bad results.
Add '-strict experimental' if you want to use it.
```

That message should be updated for two reasons. The native FFmpeg AAC encoder, "aac", isn't great at low bitrates, but it is [arguably better](http://d.hatena.ne.jp/kamedo2/20120729/1343545890) than vo-aacenc at "normal" bitrates of 128k and up. Secondly, it should mention that "-strict experimental" is an output option and should be moved after "-i video.mpeg".

> **Primefalcon said:**
> however when I do the following

```
ffmpeg -strict experimental -i video.mpeg -same_quant video.mp4
```

all I get is this

```
Unrecognized option 'strict experimental'
Failed to set value '-i' for option 'strict experimental'
```

Don't use -same_quant (alias for -sameq). It has been removed upstream (in FFmpeg). See [Why was the ffmpeg &#8216;-sameq&#8217; option removed? What to use instead?](http://ffmpeg.org/faq.html#Why-was-the-ffmpeg-_002dsameq-option-removed_003f-What-to-use-instead_003f) and [sameq does not mean "same quality"](http://superuser.com/a/478550/110524). See the  [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) for detailed examples on how to get a good quality output.

---

### Post by Primefalcon on 2012-12-21
> **FakeOutdoorsman said:**
> Note that the mp4 container supports several video formats. The default encoder for mp4 used by ffmpeg will change depending on your version and configuration, either "mpeg4" for MPEG-4 Part 2 video or "libx264" for H.264 video.



That message should be updated for two reasons. The native FFmpeg AAC encoder, "aac", isn't great at low bitrates, but it is [arguably better](http://d.hatena.ne.jp/kamedo2/20120729/1343545890) than vo-aacenc at "normal" bitrates of 128k and up. Secondly, it should mention that "-strict experimental" is an output option and should be moved after "-i video.mpeg".



Don't use -same_quant (alias for -sameq). It has been removed upstream (in FFmpeg). See [Why was the ffmpeg &#8216;-sameq&#8217; option removed? What to use instead?](http://ffmpeg.org/faq.html#Why-was-the-ffmpeg-_002dsameq-option-removed_003f-What-to-use-instead_003f) and [sameq does not mean "same quality"](http://superuser.com/a/478550/110524). See the  [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) for detailed examples on how to get a good quality output.
Got it working thanks, and yeah I know about sameq and same_quant whether your using the avconv or ffmpeg commands, in avconv man page it tells you that it doesn't equal same quality but I just didn't feel like entering all the bit rates and such

---

