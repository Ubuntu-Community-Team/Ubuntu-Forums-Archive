---
title: "Embed a srt to m4v with MP4Box?"
date: 2013-01-03
forum: General Help
---

### Post by taunnt on 2013-01-03
Hello I'm trying to embed a srt files to my back up copy of Avengers.m4v. I tried this in MP4Box:

MP4Box -add Avengers.srt:lang=eng Avengers.m4v -out Avengers2.m4v

It makes a new file with no subs :\. What am doing wrong? Here's what my srt file looks like:

```

1
00:12:12,320 --> 00:12:16,051
This is not how I wanted this evening
to go.

2
00:12:16,158 --> 00:12:17,785
I know how you wanted this evening
to go.

3
00:12:17,993 --> 00:12:19,119
BeIieve me

4
00:12:19,227 --> 00:12:20,251
this is better.

5
00:12:21,229 --> 00:12:23,094
Who are you working for?

6
00:12:23,465 --> 00:12:25,023
Lermentov, yes?

7
00:12:27,002 --> 00:12:28,469
Does he think

8
00:12:29,070 --> 00:12:30,867
we have to go through him

9
00:12:31,173 --> 00:12:32,640
to move our cargo?

10
00:12:33,875 --> 00:12:38,403
I thought GeneraI SoIohob
is in charge of the export business.

11
00:12:38,814 --> 00:12:40,782
SoIohob

12
00:12:40,949 --> 00:12:43,008
a bagman, a front.

13
00:12:45,454 --> 00:12:49,652
Your outdated information betrays you.

14
00:12:51,226 --> 00:12:53,990
The famous BIack Widow

15
00:12:55,630 --> 00:12:59,999
and she turns out to be
simpIy another pretty face.

16
00:13:00,869 --> 00:13:04,032
You reaIIy think I'm pretty?

17
00:13:06,575 --> 00:13:08,839
TeII Lermentov we don't need him

18
00:13:09,144 --> 00:13:12,705
to move the tanks.

19
00:13:13,682 --> 00:13:16,310
TeII him he is out.

20
00:13:16,718 --> 00:13:18,345
WeII...

21
00:13:31,967 --> 00:13:33,400
It's for her.

22
00:13:36,872 --> 00:13:38,203
You Iisten carefuIIy

23
00:15:38,827 --> 00:15:39,794
Who are you?

24
00:15:40,228 --> 00:15:41,354
Get out!

25
00:15:41,463 --> 00:15:43,988
There is sickness here!

26
00:15:46,801 --> 00:15:48,098
My father's not waking up!

27
00:15:48,203 --> 00:15:50,068
He has a fever and he's moaning

28
00:15:50,171 --> 00:15:51,263
but his eyes won't open.

29
00:15:51,373 --> 00:15:52,340
SIow down.

30
00:15:53,942 --> 00:15:55,000
My father...

31
00:15:57,379 --> 00:15:58,346
Like them?

```

---

### Post by andrew.46 on 2013-01-04
Just tried a variation of your syntax here:

```

andrew@skamandros~/media/fist/test$ MP4Box -add Fist_of_Fury.srt:lang=eng Fist_of_Fury.mp4 -out Fist_of_Fury2.mp4
**[COLOR="Red"]Timed Text (SRT) import - text track 969 x 394, font Serif (size 18)[/COLOR]**
Saving to Fist_of_Fury2.mp4: 0.500 secs Interleaving 

```

and it worked perfectly:

```

andrew@skamandros~/media/fist/test$ mediainfo Fist_of_Fury2.mp4 
General
Complete name                            : Fist_of_Fury2.mp4
Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom
File size                                : 763 MiB
Duration                                 : 1h 41mn
Overall bit rate mode                    : Variable
Overall bit rate                         : 1 047 Kbps
Movie name                               : Fist of Fury
Recorded date                            : 1972
Encoded date                             : UTC 2011-05-16 20:12:28
Tagged date                              : UTC 2011-05-16 20:12:28
Writing application                      : FFmpeg git-r29991, x264 core:115 & NeroAacEnc 1.5.4.0

[...]                           

Text
ID                                       : 4
Format                                   : Timed text
Codec ID                                 : tx3g
Duration                                 : 1h 41mn
Bit rate mode                            : Variable
Bit rate                                 : 33 bps
Stream size                              : 24.6 KiB (0%)
**[COLOR="Red"]Title                                    : Fist_of_Fury.srt:lang=eng - Imported with GPAC 0.4.6-DEV-rev[/COLOR]**
Language                                 : English
Encoded date                             : UTC 2013-01-04 07:25:57
Tagged date                              : UTC 2013-01-04 07:25:57

```

Did you get an error message?

---

### Post by taunnt on 2013-01-04
Nope no error here's what it said:

```

/DVD# MP4Box -add Avengers.srt:lang=eng Avengers.m4v -out Avengers2.m4v
Timed Text (SRT) import - text track 853 x 480, font Serif (size 18)
Setting up iTunes/iPod file...                       
Saving to Avengers2.m4v: 0.500 secs Interleaving

```

but yet no subtitles.


> **andrew.46 said:**
> Just tried a variation of your syntax here:

```

andrew@skamandros~/media/fist/test$ MP4Box -add Fist_of_Fury.srt:lang=eng Fist_of_Fury.mp4 -out Fist_of_Fury2.mp4
**[COLOR="Red"]Timed Text (SRT) import - text track 969 x 394, font Serif (size 18)[/COLOR]**
Saving to Fist_of_Fury2.mp4: 0.500 secs Interleaving 

```

and it worked perfectly:

```

andrew@skamandros~/media/fist/test$ mediainfo Fist_of_Fury2.mp4 
General
Complete name                            : Fist_of_Fury2.mp4
Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom
File size                                : 763 MiB
Duration                                 : 1h 41mn
Overall bit rate mode                    : Variable
Overall bit rate                         : 1 047 Kbps
Movie name                               : Fist of Fury
Recorded date                            : 1972
Encoded date                             : UTC 2011-05-16 20:12:28
Tagged date                              : UTC 2011-05-16 20:12:28
Writing application                      : FFmpeg git-r29991, x264 core:115 & NeroAacEnc 1.5.4.0

[...]                           

Text
ID                                       : 4
Format                                   : Timed text
Codec ID                                 : tx3g
Duration                                 : 1h 41mn
Bit rate mode                            : Variable
Bit rate                                 : 33 bps
Stream size                              : 24.6 KiB (0%)
**[COLOR="Red"]Title                                    : Fist_of_Fury.srt:lang=eng - Imported with GPAC 0.4.6-DEV-rev[/COLOR]**
Language                                 : English
Encoded date                             : UTC 2013-01-04 07:25:57
Tagged date                              : UTC 2013-01-04 07:25:57

```

Did you get an error message?

---

### Post by andrew.46 on 2013-01-04
Could you run mediainfor over your MP4Box generated file?

---

### Post by taunnt on 2013-01-04
```
/DVD# MP4Box -info Avengers2.m4v
* Movie Info *
	Timescale 90000 - Duration 02:22:55.624
	Fragmented File no - 3 track(s)
	File suitable for progressive download (moov before mdat)
	File Brand M4V  - version 1
	Created: GMT Thu Jan  3 12:22:11 2013

File has zzz IOD (9 bytes)
Scene PL 0xff - Graphics PL 0xff - OD PL 0xff
Visual PL: AVC/H264 Profile (0x15)
Audio PL: No audio capability required (0xff)
No streams included in zzz OD

iTunes Info:
	Encoder Software: HandBrake 0.9.8 2012071700

Track # 1 Info - TrackID 1 - TimeScale 90000 - Duration 02:22:55.624
Media Info: Language "Undetermined" - Type "vide:avc1" - 205608 samples
Visual Track layout: x=0 y=0 width=853 height=480
MPEG-4 Config: Visual Stream - ObjectTypeIndication 0x21
AVC/H264 Video - Visual Size 720 x 480
	AVC Info: 1 SPS - 1 PPS - Profile High @ Level 3
	NAL Unit length bits: 32
	Pixel Aspect Ratio 32:27 - Indicated track size 853 x 480
Self-synchronized

Track # 2 Info - TrackID 2 - TimeScale 48000 - Duration 02:22:55.584
Media Info: Language "English" - Type "soun:ac-3" - 267987 samples
	AC3 stream - Sample Rate 48000 - 5.1 channel(s) - bitrate 384000

Track # 3 Info - TrackID 3 - TimeScale 1000 - Duration 00:15:58.346
Media Info: Language "English" - Type "sbtl:tx3g" - 62 samples
3GPP/MPEG-4 Timed Text - Size 853 x 480 - Translation X=0 Y=0 - Layer 0

```



> **andrew.46 said:**
> Could you run mediainfor over your MP4Box generated file?

---

### Post by andrew.46 on 2013-01-04
So this must be the subtitle track from your sample:

```

Track # 3 Info - TrackID 3 - TimeScale 1000 - Duration 00:15:58.346
Media Info: Language "English" - Type "sbtl:tx3g" - 62 samples
3GPP/MPEG-4 Timed Text - Size 853 x 480 - Translation X=0 Y=0 - Layer 0

```

So like MP4Box* has *actually placed the subtitles. My own sample shows:

```

andrew@skamandros~/media/fist$ MP4Box -info Fist_of_Fury2.mp4 
* Movie Info *
	Timescale 600 - Duration 01:41:52.298
	Fragmented File no - 4 track(s)
	File suitable for progressive download (moov before mdat)
	File Brand isom - version 1
	Created: GMT Mon May 16 20:12:28 2011

File has root IOD (9 bytes)
Scene PL 0xff - Graphics PL 0xff - OD PL 0xff
Visual PL: AVC/H264 Profile (0x15)
Audio PL: AAC Profile @ Level 2 (0x29)
No streams included in root OD

iTunes Info:
	Name: Fist of Fury
	Created: 1972
	Encoder Software: FFmpeg git-r29991, x264 core:115 & NeroAacEnc 1.5.4.0

Track # 1 Info - TrackID 1 - TimeScale 25000 - Duration 01:41:52.240
Media Info: Language "Undetermined" - Type "vide:avc1" - 152806 samples
Visual Track layout: x=0 y=0 width=969 height=394
MPEG-4 Config: Visual Stream - ObjectTypeIndication 0x21
AVC/H264 Video - Visual Size 682 x 394
	AVC Info: 1 SPS - 1 PPS - Profile High @ Level 3
	NAL Unit length bits: 32
	Pixel Aspect Ratio 64:45 - Indicated track size 969 x 394
Self-synchronized

Track # 2 Info - TrackID 2 - TimeScale 48000 - Duration 01:41:52.298
Media Info: Language "Chinese" - Type "soun:mp4a" - 286514 samples
MPEG-4 Config: Audio Stream - ObjectTypeIndication 0x40
MPEG-4 Audio MPEG-4 Audio AAC LC - 2 Channel(s) - SampleRate 48000
Synchronized on stream 1

Track # 3 Info - TrackID 3 - TimeScale 48000 - Duration 01:41:52.298
Media Info: Language "English" - Type "soun:mp4a" - 286514 samples
MPEG-4 Config: Audio Stream - ObjectTypeIndication 0x40
MPEG-4 Audio MPEG-4 Audio AAC LC - 2 Channel(s) - SampleRate 48000
Synchronized on stream 1

Track # 4 Info - TrackID 4 - TimeScale 1000 - Duration 01:41:27.989
Media Info: Language "English" - Type "text:tx3g" - 1310 samples
3GPP/MPEG-4 Timed Text - Size 969 x 394 - Translation X=0 Y=0 - Layer 0

```

So either the subtitle track is malformed somehow or your playback applications are having trouble reading it. Have you tried using vlc and manually selecting the subtitle track from 'Video --> Subtitles track'?

---

### Post by taunnt on 2013-01-04
OK kinda got it... It looks like it was Movie Player not seeing any subs. I opened it in VLC and I could select a sub, but isn't this post to hardcode the subs? If not can you do that with MP4Box?

---

### Post by andrew.46 on 2013-01-04
> **taunnt said:**
> OK kinda got it... It looks like it was Movie Player not seeing any subs. I opened it in VLC and I could select a sub, but isn't this post to hardcode the subs? If not can you do that with MP4Box?

The subtitles *are* actually hard-coded in that they are 'built-in' to your media container and do not require an external file (such as your .srt file). I see that vlc will not use these subtitles by *default* whereas SMPlayer does. Curious, and I am not sure of the answer to that one.... But good to see that the subtitles have actually been added as you planned, just the fine details to sort out now :)

---

### Post by taunnt on 2013-01-04
Yep I thought wrong. I thought hardcoded subs where embedded in the picture. I take it that the Apple TV doesn't like hardcoded subs. Least I couldn't get mine to see the subtitles. It saw the English subs, but didn't show anything.

Thanks for your help.

> **andrew.46 said:**
> The subtitles *are* actually hard-coded in that they are 'built-in' to your media container and do not require an external file (such as your .srt file). I see that vlc will not use these subtitles by *default* whereas SMPlayer does. Curious, and I am not sure of the answer to that one.... But good to see that the subtitles have actually been added as you planned, just the fine details to sort out now :)

---

### Post by andrew.46 on 2013-01-04
> **taunnt said:**
> Yep I thought wrong. I thought hardcoded subs where embedded in the picture. I take it that the Apple TV doesn't like hardcoded subs. Least I couldn't get mine to see the subtitles. It saw the English subs, but didn't show anything.


Actually you are right but for mp4 container I believe Timed Text is the correct subtitle type and this is what MP4Box uses. To actually embed the subtitles in the video frame I am not sure, hopefully somebody more learnde than myself can help out...

---

### Post by evilsoup on 2013-01-05
It is possible to burn subtitles into a video from the command-line with ffmpeg's subtitles filter. Where input.m4v is your input file and subtitle.srt is your SRT subtitle file, this will burn the subtitles into the video and create a file called output.mp4:

```

ffmpeg -i input.m4v -filter:v subtitles=subtitle.srt -c:v libx264 -crf 22 -preset veryfast -c:a copy output.mp4

```The above should be a good quality conversion, but if you want a higher quality, you can use a lower crf value (I wouldn't go below 18, which should be considered 'visually lossless'). This will be at the expense of a larger file. To get a smaller file size, you can use a slower preset (see [here]("https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide#crf") for more information). The audio will be untouched.

And now, the catch...

Unfortunately, the version of ffmpeg included in the Ubuntu repositories doesn't have the subtitles filter. You can try the version from [this PPA]("https://launchpad.net/~jon-severinsson/+archive/ffmpeg"), though I haven't myself tested to see if it has the subtitles filter or not. If that doesn't work, you'll have to compile it yourself, following [this guide]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide").

However: unless you know you really need hardcoded subtitles, just stick with the MP4Box method. Softsubs are much more convenient.

---

### Post by andrew.46 on 2013-01-19
> **evilsoup said:**
> 

And now, the catch...

Unfortunately, the version of ffmpeg included in the Ubuntu repositories doesn't have the subtitles filter.

Yet another reason why the best policy is to use the most recent version of FFmpeg :)

---

