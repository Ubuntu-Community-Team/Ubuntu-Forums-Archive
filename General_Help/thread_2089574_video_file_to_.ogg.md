---
title: "video file to .ogg"
date: 2012-11-29
forum: General Help
---

### Post by Chelidze on 2012-11-29
So I tried to look into this and surfed the ubuntu forums but I run into a problem I struggle with Gnu/linux because I am a quite new to it.
 So What I want is to convert video formats like .avi .mov etc to Ogg or ogv I can not understand which one does what :D
 So I found some terminally commends like this ```
ffmpeg -i input.avi -acodec libvorbis -ac 1 -b 768k output.ogg
``` 
but problem with this commends are that they change fps or bit rate or some times even resolution of the source video. how ever I want to output have the same fps, video/audio bit rate, resolution, aspect ratio.

 after this I typed ```
man ffmpeg
``` and found some usful information but then I realized I have no idea how spacing works in terminal or what (-a-b-c-d-e-f-g) commend should come after one  another and so on.
 So can you help me to get the same output videos parameters as I  have in source video.
 
 and if it is not too much trouble can you tell me what will be the commend to change bit rat like have top that it can not go over 
 
 Thank you in advanced and sorry for my horrible English

---

### Post by btindie on 2012-11-29
Use something like [mediainfo]("http://packages.ubuntu.com/precise/mediainfo") to get the properties of the source media file then use avconv (newer version of ffmpeg) to convert it.

E.g.
```
avconv -i infile.avi -b:v 800k -g 300 -bf 2 -b:a 128k outfile.ogv
```

change the video and audio bit rates to suit your needs.

---

### Post by Chelidze on 2012-11-29
> **btindie said:**
> Use something like [mediainfo]("http://packages.ubuntu.com/precise/mediainfo") to get the properties of the source media file then use avconv (newer version of ffmpeg) to convert it.

E.g.
```
avconv -i infile.avi -b:v 800k -g 300 -bf 2 -b:a 128k outfile.ogv
```

change the video and audio bit rates to suit your needs.

thank you so much for the reply but

what does this stands for 

[B]-b:v
-g 300 what is it ??[/B]
[B]-bf 2
-b:a[/B]

I am at a loss :) I understand how video encoding works but I should know what this commends stand for 
**-b:v** is this variable video bitrate and the average is 800K
**-g 300** can not even guess 
**bf 2** is this two channels 
**-b:a 128k** and this must be variable audio bitrate

sorry that I am not helpful to much

---

### Post by FakeOutdoorsman on 2012-11-29
> **Chelidze said:**
> how ever I want to output have the same fps, video/audio bit rate, resolution, aspect ratio.
That is usually a good idea.

> **Chelidze said:**
> after this I typed ```
man ffmpeg
``` and found some usful information but then I realized I have no idea how spacing works in terminal or what (-a-b-c-d-e-f-g) commend should come after one  another and so on.

The basic syntax is:
```
ffmpeg [input options] -i input [output options] output
```

[input options] will be applied to the input (decoding options). [output options] will be applied to the output (encoding options).

> **Chelidze said:**
> So can you help me to get the same output videos parameters as I have in source video.

By default ffmpeg will attempt to inherit most parameters, except bitrate, from the input to the output.
 
> **Chelidze said:**
> and if it is not too much trouble can you tell me what will be the commend to change bit rat like have top that it can not go over
Do you have a file size limit and/or a maximum bitrate per second you do not want to exceed?

> **btindie said:**
> Use something like [mediainfo]("http://packages.ubuntu.com/precise/mediainfo") to get the properties of the source media file then use avconv (newer version of ffmpeg) to convert it.

avconv is not a "newer" version of ffmpeg. It is libav's (a fork of FFmpeg) equivalent of ffmpeg. See [Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017) and [The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html).

---

### Post by Chelidze on 2012-11-29
> **FakeOutdoorsman said:**
> That is usually a good idea.



The basic syntax is:
```
ffmpeg [input options] -i input [output options] output
```

[input options] will be applied to the input (decoding options). [output options] will be applied to the output (encoding options).



By default ffmpeg will attempt to inherit most parameters, except bitrate, from the input to the output.
 

Do you have a file size limit and/or a maximum bitrate per second you do not want to exceed?



avconv is not a "newer" version of ffmpeg. It is libav's (a fork of FFmpeg) equivalent of ffmpeg. See [Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017) and [The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html).

thank you for the reply but by default it down scales a 25mb+ bit rate video to 200 Kbps same with audio

---

### Post by FakeOutdoorsman on 2012-11-29
> **Chelidze said:**
> thank you for the reply but by default it down scales a 25mb+ bit rate video to 200 Kbps same with audio

Yes, depending on the encoder the default video bitrate is 200k, and the default audio bitrate is usually 128k (also encoder dependent). I didn't give an example because I thought you were attempting to get a specific file size and I wanted more information before giving an example:

> and if it is not too much trouble can you tell me what will be the commend to change bit rat like have top that it can not go over

---

### Post by Chelidze on 2012-11-29
> **FakeOutdoorsman said:**
> Yes, depending on the encoder the default video bitrate is 200k, and the default audio bitrate is usually 128k (also encoder dependent). I didn't give an example because I thought you were attempting to get a specific file size and I wanted more information before giving an example:

Ok for example I want to encode this video 

```
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42
File size                                : 478 MiB
Duration                                 : 3mn 34s
Overall bit rate mode                    : Variable
Overall bit rate                         : 18.7 Mbps
Encoded date                             : UTC 2011-12-27 00:05:27
Tagged date                              : UTC 2011-12-27 00:05:27

Video
ID                                       : 2
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.0
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 2 frames
Muxing mode                              : Container profile=Baseline@4.0
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 3mn 34s
Bit rate mode                            : Variable
Bit rate                                 : 18.4 Mbps
Maximum bit rate                         : 22.0 Mbps
Width                                    : 1 920 pixels
Height                                   : 1 080 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.355
Stream size                              : 470 MiB (98%)
Language                                 : English
Encoded date                             : UTC 2011-12-27 00:05:27
Tagged date                              : UTC 2011-12-27 00:05:27

Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 3mn 34s
Bit rate mode                            : Constant
Bit rate                                 : 320 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Delay relative to video                  : 40ms
Stream size                              : 8.17 MiB (2%)
Language                                 : English
Encoded date                             : UTC 2011-12-27 00:05:27
Tagged date                              : UTC 2011-12-27 00:05:27


```

I do not want to change audio/video bit rate, aspect ratio resolution or fps 

I tried this commend with my mad skills 
```
ffmpeg -i '/media/levan/BEEA60D8EA608E89/Downloads/Videos/Âîþ íà ëóíó (HD).mkv' -bt 19200k -ar 48000 -ab 320k ~/test.ogg
```

```
ffmpeg -i '/media/levan/BEEA60D8EA608E89/Downloads/Videos/Âîþ íà ëóíó (HD).mkv' -minrate 18842k -maxrate 22528k -ar 48000 -ab 320k ~/test.ogg
```

Tryed this commend I thought I would lock the mini fps to 18mb but nothing same story
got a 200k bit rate

any idea how to fix this

---

### Post by FakeOutdoorsman on 2012-11-29
Copying the bitrate from the input to the output is not an optimal solution. Not all encoders are equal, and how are you to know that the person who made the first file knew what they were doing?

The reason it used 200k is because you need to declare bitrate with the *-b:v* option (or *-b* for ancient ffmpeg).

See [High quality ogv files - possible?](http://avp.stackexchange.com/a/4230/1760) for an example of using constant quality mode. It's not equivalent to "CRF" in x264, but it may give you acceptable results.

---

### Post by Chelidze on 2012-11-29
> **FakeOutdoorsman said:**
> Copying the bitrate from the input to the output is not an optimal solution. Not all encoders are equal, and how are you to know that the person who made the first file knew what they were doing?

The reason it used 200k is because you need to declare bitrate with the *-b:v* option (or *-b* for ancient ffmpeg).

See [High quality ogv files - possible?](http://avp.stackexchange.com/a/4230/1760) for an example of using constant quality mode. It's not equivalent to "CRF" in x264, but it may give you acceptable results.

I found this interesting web page
[http://www.rodrigopolo.com/ffmpeg/](http://www.rodrigopolo.com/ffmpeg/)

when I enter max bit rate value 22mb and target 18mb it crashes 
```
[libvorbis @ 0x99db80] oggvorbis_encode_init: init_encoder failed

```
but if I use 2mb preset it can render it. 
can this software render files with good bit rate at all ??



[COLOR="Red"]
little update I think it started to  work a bit[/COLOR]
```
ffmpeg -y -i '/media/levan/BEEA60D8EA608E89/Downloads/Videos/Âîþ íà ëóíó (HD).mkv' -s 1920x1080 -aspect 16:9 -r 25 -b 17550k -bt 19792k -vcodec libtheora -acodec libvorbis -ac 2 -ar 44100 -ab 128k lol.ogg
```
for example this commend works but if I change audio it crashes I am not sure if bit rate effects the audio or the audio rate

 any way 128 kb and 44100 is a step down from 320kb and 48.0 KHz is not it ??




**[COLOR="Red"]Finally I figured it out here is the commend[/COLOR]**


```
ffmpeg -y -i '/media/levan/BEEA60D8EA608E89/Downloads/Videos/Âîþ íà ëóíó (HD).mkv' -s 1920x1080 -aspect 16:9 -r 25 -b 18550k -bt 22792k -vcodec libtheora -acodec libvorbis -ac 2 -ar 48000 -ab 320k lol.ogg
```


Thanks every one for helping

---

### Post by andrew.46 on 2012-11-30
> **FakeOutdoorsman said:**
> 
See [High quality ogv files - possible?](http://avp.stackexchange.com/a/4230/1760) for an example of using constant quality mode. It's not equivalent to "CRF" in x264, but it may give you acceptable results.

Now this I have never seen before:

```

-flags:v qscale -global_quality:v "10*QP2LAMBDA"

```

Looks like I have some experimentation ahead with this one :)

---

### Post by FakeOutdoorsman on 2012-11-30
It's new to me too. I only noticed it from commit [9d2a7c0](http://git.videolan.org/gitweb.cgi/ffmpeg.git/?p=ffmpeg.git;a=blobdiff;f=doc/encoders.texi;h=c37f2565e1bc6b3a23cba09863b6c18746ae68e5;hp=a7a2761f1d381a7bb4114ad28b1a4f6cc59c5810;hb=9d2a7c04812ae6f3db2e58570242a15ff25a335a;hpb=8cb76ef275f7e4be049ac7d6dbfc23186ec73631). I prefer the simplicity of just *-q:v*, but maybe that usage was incorrect with this encoder.

---

### Post by andrew.46 on 2012-12-03
My interest was definitely raised raised by this thread and I have worked a little with the commandline that FakeOutdoorsman has suggested in conjunction with work I have done previously with converting dvd movies to h.264/aac mp4s:

FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

Using the original vob I simply ran this comandline (omitting the athleticisms documented on the page with the SoX volume adjustments):

```

ffmpeg -ss 01:24:17 -y -i fist.vob -t 00:07:53 -map 0:0 -map 0:2 \
       -vf crop=720:416:0:80 \
       -metadata title="Extract from Fist of Fury" \
       -metadata comment="An example of theora/vorbis encoding." \
       **[COLOR="Red"]-c:v libtheora -flags:v qscale -global_quality:v "10*QP2LAMBDA" \[/COLOR]**
       -c:a libvorbis -ac 2 -ar 44100 -q:a 6 \
       fof_sample.ogg

```

For those who are interested I have placed the resulting file *temporarily* on my website:

```

wget http://www.andrews-corner.org/samples/fof_sample.ogg

```

and in a big suprise to just about nobody encoding with h.264 and NeroAacEnc produces *vastly* superior results to theora and vorbis. I was disappointed that I could wrest no greater quality from theora/vorbis but it still gave me a great opportunity to stuff around with FFmpeg :). So my advice to the OP: bear in mind that you will probably not get great results with theora/vorbis, perhaps consider going with h.264 video and the audio codec of your choice. I would like the totally free format to be better but it is not....

---

### Post by FakeOutdoorsman on 2012-12-03
Now I know what movie I'm watching next.

---

### Post by andrew.46 on 2012-12-03
Moving even further off topic: It is vintage Bruce Lee with really appalling acting by many actors but absolutely classic fight scenes!

---

### Post by FakeOutdoorsman on 2012-12-26
> **andrew.46 said:**
> 
```

-c:v libtheora -flags:v qscale -global_quality:v "10*QP2LAMBDA"

```


Apparently this is the same as simply using:
```
-c:v libtheora -q:v 10
```
Range is 0-10, IIRC, where 0 is lowest quality and 10 is highest quality.

---

