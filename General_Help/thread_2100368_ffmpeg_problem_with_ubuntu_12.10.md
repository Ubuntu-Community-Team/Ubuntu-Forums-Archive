---
title: "ffmpeg problem with ubuntu 12.10"
date: 2013-01-01
forum: General Help
---

### Post by raedmohammadi on 2013-01-01
hello guys

i'm using ubuntu 12.10 32 bit , i just install 
ubuntu-restricted-extras - vlc - mplayer2 - gecko-mediaplayer - ffmpeg

now when i use ffmpeg to make videos by this command

ffmpeg -f alsa -i pulse -f x11grab -r 25 -s 1680x1050 -i :0.0 -vcodec mpeg4 -b 6000k -g 300 -bf 2 -acodec libmp3lame -ab 128k Screencast.avi

i notice slow animation when open windows and minimize it - just when start recording ! when i stop recording all the animation works smoothly 

i tried also kazam same issue  
this is my PC dell optiplex 790

CPU : Intel Core i3-2100 CPU
12 GB ram ddr3
intel vga

any idea !

---

### Post by ajgreeny on 2013-01-01
If you are using the repo version of **ffmpeg** you may experience problems as it has now been deprecated in favour of **avconv**.

A lot of the command syntax for avconv is identical to ffmpeg, so try the same command but change the "ffmpeg" to "avconv" and see what you get from that.  If the syntax needs amending an error message may tell you how to change it.

Alternatively, if you prefer to continue using ffmpeg you can compile it for 12.10 and use it easily; it is only the ubuntu repository version that has been deprecated, not upstream ffmpeg.

---

### Post by raedmohammadi on 2013-01-01
> **ajgreeny said:**
> If you are using the repo version of **ffmpeg** you may experience problems as it has now been deprecated in favour of **avconv**.

A lot of the command syntax for avconv is identical to ffmpeg, so try the same command but change the "ffmpeg" to "avconv" and see what you get from that.  If the syntax needs amending an error message may tell you how to change it.

Alternatively, if you prefer to continue using ffmpeg you can compile it for 12.10 and use it easily; it is only the ubuntu repository version that has been deprecated, not upstream ffmpeg.

i tried to compile ffmpeg from this link

[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuidesame](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuidesame) problem , someone told me to use this command
 
ffmpeg -f alsa -i pulse -f x11grab -r [COLOR=Red]15[/COLOR] -s 1680x1050 -i :0.0 -vcodec  mpeg4 -b 6000k -g 300 -bf 2 -acodec libmp3lame -ab 128k Screencast.avi

i will try **avconv and come back**

---

### Post by raedmohammadi on 2013-01-01
> **ajgreeny said:**
> If you are using the repo version of **ffmpeg** you may experience problems as it has now been deprecated in favour of **avconv**.

A lot of the command syntax for avconv is identical to ffmpeg, so try the same command but change the "ffmpeg" to "avconv" and see what you get from that.  If the syntax needs amending an error message may tell you how to change it.

Alternatively, if you prefer to continue using ffmpeg you can compile it for 12.10 and use it easily; it is only the ubuntu repository version that has been deprecated, not upstream ffmpeg.

thank you  ajgreeny ,  I see improvement , Could you see this video please is these animation in video normal ? it's a bit slow now

[http://www.youtube.com/watch?v=LAHSbhb9PZQ](http://www.youtube.com/watch?v=LAHSbhb9PZQ)

 when i stop recording the animations works much faster , i never faced this kind of problem in 12.04

---

### Post by FakeOutdoorsman on 2013-01-01
Perhaps you should try a potentially less demanding encoder:

```
ffmpeg -f alsa -i pulse -f x11grab -r 15 -s 1680x1050 -i :0.0 -c:v libx264 -preset ultrafast -qp 0 -c:a pcm_s16le output.mkv
```

This will create a lossless output file, and therefore the output file will be large, but that is fine since you can re-encode it later. The advantage of this two-step process is to use a fast yet high-quality encoder for the first step to reach your desired fps. Then, when you can dedicate the computer to encoding, you can ramp up the encoding complexity and re-encode the output from the first step to a more manageable size. That's the general idea at least: your bottleneck may be elsewhere.

Although the output is lossless it may not look as good as the screen due to colorspace conversion and sub-sampling.

See the [FFmpeg and x264 Encoding Guide](http://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) on how to re-encode the lossless file.

This command is for your compiled ffmpeg and not avconv/repository "ffmpeg".

---

### Post by raedmohammadi on 2013-01-02
> **FakeOutdoorsman said:**
> Perhaps you should try a potentially less demanding encoder:

```
ffmpeg -f alsa -i pulse -f x11grab -r 15 -s 1680x1050 -i :0.0 -c:v libx264 -preset ultrafast -qp 0 -c:a pcm_s16le output.mkv
```

This will create a lossless output file, and therefore the output file will be large, but that is fine since you can re-encode it later. The advantage of this two-step process is to use a fast yet high-quality encoder for the first step to reach your desired fps. Then, when you can dedicate the computer to encoding, you can ramp up the encoding complexity and re-encode the output from the first step to a more manageable size. That's the general idea at least: your bottleneck may be elsewhere.

Although the output is lossless it may not look as good as the screen due to colorspace conversion and sub-sampling.

See the [FFmpeg and x264 Encoding Guide](http://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) on how to re-encode the lossless file.

This command is for your compiled ffmpeg and not avconv/repository "ffmpeg".

thank you FakeOutdoorsman , still there is slow animations just when start recording also after upload it to youtube now there is no image :( .. see this video please

[http://www.youtube.com/watch?v=r9P-d595e7o](http://www.youtube.com/watch?v=r9P-d595e7o)

---

### Post by FakeOutdoorsman on 2013-01-03
Did you upload the lossless video, or the re-encoded file using the lossless video as an input?

---

### Post by raedmohammadi on 2013-01-03
> **FakeOutdoorsman said:**
> Did you upload the lossless video, or the re-encoded file using the lossless video as an input?

directly i record with this command and upload it

---

