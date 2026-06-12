---
title: "How to convert to .mp4 (for streaming)?"
date: 2013-05-17
forum: General Help
---

### Post by colobix on 2013-05-17
Hello.
I've tried various different things such as "ffmpeg -i input.avi output.mp4" and even included vcodec libx264 and a ton of things.
But it doesn't stream. It pre-buffers (downloads the whole thing first).
Now I have to upload them to youtube and then download the mp4 file, and then upload them to the web.
So, what setup do they use on youtube and other video streaming sites for that matter?

---

### Post by andrew.46 on 2013-05-17
Hmmmmm.... in the not too distant past you would run your file through qt-faststart after encoding with FFmpeg. Not sure if this is still the case though as I believe[ this can now be an option at the FFmpeg commandline]("http://git.videolan.org/?p=ffmpeg.git;a=blobdiff;f=Changelog;h=ce3c74b5cbd9502756e3a67a7d2fc5d0e3318a5e;hp=b92c2e1d37e8cd3e93f7ff9e0e3be546b35bb66b;hb=a714150827c70f8baf2ec42dfecd9363c17e803d;hpb=f379a108a45a800bff059034f939224e4535a8e7") in more recent FFmpeg versions.

---

### Post by Merrattic on 2013-05-17
From: [http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuideQuantal](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuideQuantal)       -    by you know who :D

**Optional Installation**

 **qt-faststart**

  This is a useful tool if you're showing your H.264 in MP4 videos on the  web. It relocates some data in the video to allow playback to begin  before the file is completely downloaded. Usage: qt-faststart input.mp4 output.mp4. When converting files with ffmpeg you can add -movflags faststart to have the same effect. 
 
```

cd ~/ffmpeg make tools/qt-faststart 

sudo checkinstall --pkgname=qt-faststart --pkgversion="$(date +%Y%m%d%H%M)-git" --backup=no \   
--deldoc=yes --fstrans=no --default install -Dm755 tools/qt-faststart \   
/usr/local/bin/qt-faststart 
```

---

### Post by colobix on 2013-05-17
> **Merrattic said:**
> From: [http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuideQuantal](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuideQuantal)       -    by you know who :D

**Optional Installation**

 **qt-faststart**

  This is a useful tool if you're showing your H.264 in MP4 videos on the  web. It relocates some data in the video to allow playback to begin  before the file is completely downloaded. Usage: qt-faststart input.mp4 output.mp4. When converting files with ffmpeg you can add -movflags faststart to have the same effect. 

Thanks. but it says it's for quicktime files.
I could convert the avi's to mov first, but I don't wanna lose more quality than necessarily.

Any other ideas?
Edit: what commands do they use over at youtube and other sites like that?
Do any of you know???

---

### Post by FakeOutdoorsman on 2013-05-17
> **colobix said:**
> So, what setup do they use on youtube and other video streaming sites for that matter?
"Streaming" generally means that the encoder is working in real time. What you're trying to do is called "progressive download" meaning that the content has already been encoded and you want the client to playback while the video is being downloaded.

> **colobix said:**
> Thanks. but it says it's for quicktime files.

It doesn't matter. Works for mp4 too:
```
ffmpeg -i input.mp4 -codec copy -map 0 -movflags faststart output.mp4
```
or
```
qt-faststart input.mp4 output.mp4
```
or
```
sudo apt-get install gpac
MP4Box -add input.mp4 output.mp4
```
These commands will basically all do the same thing, but the ffmpeg command is the most flexible because you can do other stuff too like add or change metadata:
```
ffmpeg -i input.mp4 -codec copy -map 0 -movflags faststart -metadata title="Merrattic's Avatar is a Weird Looking Rat" -metadata author="My Avatar is a guy from India with an old VCR" output.mp4
```

---

### Post by colobix on 2013-05-17
> **FakeOutdoorsman said:**
> "Streaming" generally means that the encoder is working in real time. What you're trying to do is called "progressive download" meaning that the content has already been encoded and you want the client to playback while the video is being downloaded.
Thanks. 
But just to clarify. you said input.mp4 output.mp4.
So what you're saying is, first I have to convert it to mp4 using ffmpeg and then use this qt software to encode it?
Because I tried avi to mp4 using your command, but it wouldn't work
Getting an error:

```
fmpeg -i in.avi -codec copy -map 0 -movflags faststart output.mp4
ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (24000/1001)
Input #0, avi, from 'in.avi':
  Metadata:
    encoder         : VirtualDubMod 1.5.4.1 (build 2178/release)
  Duration: 00:07:17.52, start: 0.000000, bitrate: 1128 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 640x480 [PAR 1:1 DAR 4:3], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 89 kb/s
[COLOR="#FF0000"]Unrecognized option 'codec'
Failed to set value 'copy' for option 'codec'
[/COLOR]
```

---

### Post by FakeOutdoorsman on 2013-05-17
> **colobix said:**
> Thanks. 
But just to clarify. you said input.mp4 output.mp4.
So what you're saying is, first I have to convert it to mp4 using ffmpeg and then use this qt software to encode it?

qt-faststart does not encode. It simply moves a chunk of information to the beginning of the file but must create a new output to do so.

> **colobix said:**
> Because I tried avi to mp4 using your command, but it wouldn't work
Getting an error:

```
fmpeg -i in.avi -codec copy -map 0 -movflags faststart output.mp4
ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (24000/1001)
Input #0, avi, from 'in.avi':
  Metadata:
    encoder         : VirtualDubMod 1.5.4.1 (build 2178/release)
  Duration: 00:07:17.52, start: 0.000000, bitrate: 1128 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 640x480 [PAR 1:1 DAR 4:3], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 89 kb/s
[COLOR="#FF0000"]Unrecognized option 'codec'
Failed to set value 'copy' for option 'codec'
[/COLOR]
```

That's because you're not using ffmpeg from FFmpeg, but an old, fake, crappy version from a fork (see my signature links). Get a [static build](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453) or [compile ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide), or use MP4Box as shown in the previous post.

---

### Post by colobix on 2013-05-18
> **FakeOutdoorsman said:**
> qt-faststart does not encode. It simply moves a chunk of information to the beginning of the file but must create a new output to do so.



That's because you're not using ffmpeg from FFmpeg, but an old, fake, crappy version from a fork (see my signature links). Get a [static build](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453) or [compile ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide), or use MP4Box as shown in the previous post.

Fake? I'm using the ubuntu repo's version.
Why would there even be a fake version of ffmpeg out there anyway?
Do you mean it has a virus or something?
Anyway, this is getting extremely ridiculous.
Is there or isn't there a possible way of doing this on linux?
I'm getting tired of things not working the way they should.

---

### Post by andrew.46 on 2013-05-18
Your copy of FFmpeg is a little old and syntax has moved around a little I'm afraid. But have you tried FakeOutdoorsman's suggested MP4Box syntax?

---

### Post by colobix on 2013-05-18
> **andrew.46 said:**
> Your copy of FFmpeg is a little old and syntax has moved around a little I'm afraid. But have you tried FakeOutdoorsman's suggested MP4Box syntax?

I tried his commands, but they didn't do it either.
Do you have a ppa for the up to date ffmpeg?

---

### Post by andrew.46 on 2013-05-18
> **colobix said:**
> Do you have a ppa for the up to date ffmpeg?

I would be the wrong person to advise on PPAs as, against current thinking in Ubuntu, I don't believe they are such a good thing. IMHO your best bet is to get a more recent copy of Ubuntu in this way:

[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

Trust me, I understand your frustration with this!

---

