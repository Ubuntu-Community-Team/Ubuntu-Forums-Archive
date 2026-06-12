---
title: "MKV rip for stand alone player (avi to cd/dvd)"
date: 2006-12-15
forum: General Help
---

### Post by stoer on 2006-12-15
I've recently aquired a film, contained in an MKV (container).
Plays fine in kaffeine.
I'd like to play it through my stand alone dvd(divx/xvid) player to my tv.
Yes, i could just connect my laptop to the tv, but i want to add the film to a compilation of divx's for my son.
Anyone have any suggestions or ideas how to unpack this from the MKV and into a burnable/playable avi?
Appreciate any help.

---

### Post by pay on 2006-12-15
Something like ```
mencoder /path/to/video.mkv -ovc copy -oac copy -o /output/path/video.avi
```should do the trick. MKV is a container for various sorts of video and audio codecs so the video and/or audio might need to be converted to another format if the format it is in is incompatible with the standalone.

---

### Post by stoer on 2006-12-15
Hey thanks for your reply...

Now all i need is MEncoder and the following how to ;) 

[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#Compiling_MEncoder](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#Compiling_MEncoder)

Steep learning curve, but hey, that's what makes it fun.

I'll go and do some more reading, this how to looks like it's going to longer than the film :-k 

Cheers.

---

### Post by pay on 2006-12-15
```
sudo aptitude install mencoder
```should install it if you have to right repos

---

### Post by stoer on 2006-12-16
Thanks, i'll give it a shot.
tried it under windows, using mkvmerge GUI....

"Install the Matroska full pack and run,
then install mkvmerge gui,
then install mkvtoolnix in the same folder,
in the tools there is a programme to extract the chosen files,extract to the same folder then use mkvmerge to merge the two streams together,
then simply rename the file .avi. "

My version of windows disagreed "violently" with the above ](*,) and refused to talk to me for 20  minutes [-(  (set a series of freezes in motion).  Other software (winxp) are buyable, not really worthwhile seeing as this is the only mkvi've ever encountered.

Let me see what linux makes of it.

---

### Post by pay on 2006-12-16
> **stoer said:**
> 
"Install the Matroska full pack and run,
then install mkvmerge gui,
then install mkvtoolnix in the same folder,
in the tools there is a programme to extract the chosen files,extract to the same folder then use mkvmerge to merge the two streams together,
then simply rename the file .avi. "Well if you do that i believe that the resulted file would be a .mkv just with a different file name (ie if you change the name of resume.doc to resume.txt it would still be a document but with the text file format extended to it.

---

### Post by stoer on 2006-12-16
Hi, again ;) 

Tried MEncoder.

Got this...

```
steve@laptop:~$ mencoder /home/steve/afilm/BYMKV/by.mkv -ovc copy -oac copy -o /output/home/steve/afilm/BYAVI/by.avi
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x470878a3
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_VOBSUB), -sid 0, -slang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8), -sid 1, -slang dut
[mkv] Will play video track 1
[mkv] Will play audio track 2
Matroska file format detected.
VIDEO:  [avc1]  624x352  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:31  fourcc:0x31637661  size:624x352  fps:23.98  ftime:=0.0417
Cannot open output file '/output/home/steve/afilm/BYAVI/by.avi'.

Exiting...

```

files are as seen above.
/home/steve/afilm/BYMKV/by.mkv 

output to

/home/steve/afilm/BYAVI/by.avi

Why, "Cannot open"? , why is it trying to open the output file? and not writing it?

Make any sense to you, or should i try again in daylight :-k

---

### Post by pay on 2006-12-16
```
Cannot open output file '/output/home/steve/afilm/BYAVI/by.avi'.
```it can't open it because output is not a directory, and even if it was you would not have permisions for it. try ```
mencoder /home/steve/afilm/BYMKV/by.mkv -ovc copy -oac copy -o /home/steve/afilm/BYAVI/by.avi
```

---

### Post by stoer on 2006-12-17
> **pay said:**
> ```
Cannot open output file '/output/home/steve/afilm/BYAVI/by.avi'.
```it can't open it because output is not a directory, and even if it was you would not have permisions for it. try ```
mencoder /home/steve/afilm/BYMKV/by.mkv -ovc copy -oac copy -o /home/steve/afilm/BYAVI/by.avi
```

Again thanks for  your reply, appreciate it.

        [I]copy -o /output/home/steve/afilm/BYAVI/by.avi
        copy -o /home/steve/afilm/BYAVI/by.avi    [/I]
Like i said, daylight helped (must have been very tired, thats my excuse and i'm sticking to it ;)  )

Now,
At least this time  i got some 'brief working' and then this....

```
Pos:  98.6s   2152f ( 1%) 663.79fps Trem:   3min 949mb  A-V:-0.088 [1291:128]
1 duplicate frame(s)!
Pos:  99.1s   2162f ( 1%) 660.15fps Trem:   3min 949mb  A-V:-0.088 [1297:127]
1 duplicate frame(s)!
Pos:  99.6s   2172f ( 1%) 663.00fps Trem:   2min 950mb  A-V:-0.088 [1300:128]
1 duplicate frame(s)!
Pos: 100.0s   2182f ( 1%) 665.85fps Trem:   2min 950mb  A-V:-0.088 [1300:128]
1 duplicate frame(s)!
Pos: 100.5s   2192f ( 1%) 628.44fps Trem:   3min 949mb  A-V:-0.088 [1298:128]
1 duplicate frame(s)!
Pos: 100.9s   2202f ( 1%) 630.95fps Trem:   3min 949mb  A-V:-0.088 [1297:127]
1 duplicate frame(s)!
Pos: 101.4s   2212f ( 1%) 633.63fps Trem:   3min 950mb  A-V:-0.088 [1297:128]
1 duplicate frame(s)!
Pos: 101.9s   2222f ( 1%) 633.41fps Trem:   3min 949mb  A-V:-0.088 [1295:128]
1 duplicate frame(s)!
Pos: 102.3s   2232f ( 1%) 636.08fps Trem:   3min 949mb  A-V:-0.088 [1294:127]
1 duplicate frame(s)!

```

```
1 duplicate frame(s)!
Pos: 209.7s   4572f ( 3%) 671.17fps Trem:   2min 948mb  A-V:-0.088 [1290:127]
1 duplicate frame(s)!
Pos: 210.1s   4582f ( 3%) 672.54fps Trem:   2min 948mb  A-V:-0.088 [1289:128]
Too many audio packets in the buffer: (4102 in 7350784 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 1289.614 kbit/s  (161201 B/s)  size: 33872775 bytes  210.127 secs  4582 frames

Audio stream:  128.000 kbit/s  (16000 B/s)  size: 3371520 bytes  210.720 secs
```

This make any sense to you? I'm afraid that for me it's just :confused:

---

### Post by stoer on 2006-12-17
Tried this again, under win  xp.  Using Avi2Dvd and also RiverPast video cleaner.
Both also seem to hang.
Now it's either one of three things...as isee it.
1. Me ](*,) 
2.the file (mkv) is corrupted- But it plays sweetly. :confused: 
3.Me again :(  ](*,)  ](*,) 
Maybe i've taxed you enough.  I'll try this  on the software/video boys and girls.
Thanks for your help, very kind of you.  :D

---

### Post by netyire on 2006-12-18
[SIZE="2"]I think I had this problem with a flash video when I was trying to convert it. Anyway, here is a workaround which I hope will work for you! First you need to install ffmpeg to do so type the following in the terminal:

```
sudo apt-get install ffmpeg
```

This is supposing that you have the required repositories enabled :). Ok, once you have ffmpeg installed, I think that you can use ffmpeg to create a dvd quality mpg and from there the avi which you want. (This may take a bit of time, so don't get mad at me) Ok, to convert the mkv to a dvd quality mpg, you may be able to do it by entering:

```
ffmpeg -i <filename.mkv> -target ntsc-dvd output.mpg
```
If it looks funny to you (maybe because the original was fullscreen and now its stretched) then try:
```
ffmpeg -i <filename.mkv> -target pal-dvd output.mpg
```

Ok, now that you have the mpg file, try encoding it to a .avi file. (This takes more time, but don't stare at me in rage...):rolleyes: For this lets use a 2 pass xvid to create a (hopefully) good quality .avi.

For Pass 1:
```
mencoder output.mpg -ovc xvid -xvidencopts pass=1 -oac mp3lame -lameopts vbr=3 -o /dev/null
```

For Pass 2:
```
mencoder output.mpg -ovc xvid -xvidencopts pass=2:bitrate=800 -oac mp3lame -lameopts vbr=3 -o final.avi
```

Ok, merry christmas if it works, if not... please don't bill me for the wasted electricity ;) 
Anyway, hope this works for you, if not just post! :D [/size]

---

### Post by stoer on 2006-12-18
"Ok, merry christmas if it works, if not... please don't bill me for the wasted electricity
Anyway, hope this works for you, if not just post!"

Firstly, cheers! :D  appreciate the help.
Having ripped and converted assorted films in the past i sort of get the message as to the time frame you're speeking of, never tried it on this laptop before (my windows PC being somewhat older and noisy used to take a whole night over such things, but then again it used to take all night to do alot of things...hence the laptop!).

I'll definately give this a go, i'm working "lates" all week, usually home by midnight...so the laptop  can go strut it's stuff in the night. \\:D/ 

Regardless of if it works or not, Merry Christmas!

---

### Post by stoer on 2006-12-18
What the heck...
I thought i'd give it a whirl now.... got an hour to kill;) 

Got the following faults... Ran for some 5- 10 minutes before dying.

```
steve@laptop:~$ ffmpeg -i /home/steve/afilm/BYMKV/by.mkv  -target ntsc-dvd /home/steve/afilm2/by.mpg
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr 
  built on Oct  4 2006 10:57:36, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
[matroska @ 0x82c8a80]Ignoring seekhead entry for ID=0x1549a966
[matroska @ 0x82c8a80]Ignoring seekhead entry for ID=0x1654ae6b
[matroska @ 0x82c8a80]Unknown entry 0x73a4 in info header
[matroska @ 0x82c8a80]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0xaa - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0xaa - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0xaa - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0x6d80 - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x82c8a80]Unknown track header entry 0xaa - ignoring
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration

Seems that stream 0 comes from film source: 1000.00 (1000/1) -> 15.75 (63/4)
Input #0, matroska, from '/home/steve/afilm/BYMKV/by.mkv':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Video: h264, yuv420p, 624x352, 1000.00 fps
  Stream #0.1: Audio: ac3, 48000 Hz, 5:1
Output #0, dvd, to '/home/steve/afilm2/by.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x480, 29.97 fps, q=2-31, 6000 kb/s
  Stream #0.1: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[h264 @ 0x8336c48]AVC: Consumed only 42 bytes instead of 2027578224
[h264 @ 0x8336c48]non existing PPS referenced
[h264 @ 0x8336c48]decode_slice_header error
Error while decoding stream #0.0
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration    
[h264 @ 0x8336c48]AVC: Consumed only 42 bytes instead of 2027578224 
[h264 @ 0x8336c48]non existing PPS referenced
[h264 @ 0x8336c48]decode_slice_header error
Error while decoding stream #0.0
[mpeg2video @ 0x8336c48]rc buffer underflow bitrate=3261.0kbits/s    
[matroska @ 0x82c8a80]FIXME: implement support for BlockDurations    
[h264 @ 0x8336c48]AVC: Consumed only 44 bytes instead of 2027578224  
[h264 @ 0x8336c48]non existing PPS referenced
[h264 @ 0x8336c48]decode_slice_header error
Error while decoding stream #0.0
[matroska @ 0x82c8a80]FIXME: implement support for BlockDurations    
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration
[h264 @ 0x8336c48]AVC: Consumed only 591 bytes instead of 2027586963 
[h264 @ 0x8336c48]Unknown NAL code: 17
Error while decoding stream #0.0
[h264 @ 0x8336c48]AVC: Consumed only 12 bytes instead of 1869333417
[h264 @ 0x8336c48]Unknown NAL code: 12
Error while decoding stream #0.0
[matroska @ 0x82c8a80]FIXME: implement support for BlockDurations    
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration
[h264 @ 0x8336c48]AVC: Consumed only 40 bytes instead of 1231757415
[h264 @ 0x8336c48]slice type too large (3) at 0 22
[h264 @ 0x8336c48]decode_slice_header error
Error while decoding stream #0.0
[h264 @ 0x8336c48]AVC: Consumed only 1561 bytes instead of 2027593110
[h264 @ 0x8336c48]Unknown NAL code: 15
Error while decoding stream #0.0
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration/s    
[h264 @ 0x8336c48]AVC: Consumed only 3 bytes instead of 1449486700    
Error while decoding stream #0.0
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration/s    
[h264 @ 0x8336c48]AVC: Consumed only 346 bytes instead of 2027568464  
[h264 @ 0x8336c48]Unknown NAL code: 17
Error while decoding stream #0.0
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration/s    
[h264 @ 0x8336c48]AVC: Consumed only 15 bytes instead of 1214344300   
[h264 @ 0x8336c48]Unknown NAL code: 15
Error while decoding stream #0.0
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration/s    
[h264 @ 0x8336c48]AVC: Consumed only 1087 bytes instead of 2027580820 
[h264 @ 0x8336c48]Unknown NAL code: 17
Error while decoding stream #0.0
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration/s    
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration
[h264 @ 0x8336c48]AVC: Consumed only 1877 bytes instead of 2027593046 
[h264 @ 0x8336c48]Unknown NAL code: 13
Error while decoding stream #0.0
[h264 @ 0x8336c48]AVC: Consumed only 55 bytes instead of 1214608416   
Error while decoding stream #0.0
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration/s    
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration
[h264 @ 0x8336c48]AVC: Consumed only 8 bytes instead of 1299149415    
[h264 @ 0x8336c48]concealing 858 DC, 858 AC, 858 MV errors
[h264 @ 0x8336c48]AVC: Consumed only 572 bytes instead of 2027589010  
[h264 @ 0x8336c48]Unknown NAL code: 31
Error while decoding stream #0.0
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration/s    
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration
[h264 @ 0x8336c48]AVC: Consumed only 11 bytes instead of 1113941089   
[h264 @ 0x8336c48]Unknown NAL code: 14
Error while decoding stream #0.0
[h264 @ 0x8336c48]AVC: Consumed only 597 bytes instead of 2027572626  
[h264 @ 0x8336c48]Unknown NAL code: 17
Error while decoding stream #0.0
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration
[matroska @ 0x82c8a80]FIXME: implement support for BlockDuration
[h264 @ 0x8336c48]AVC: Consumed only 51 bytes instead of 1516594976   
[h264 @ 0x8336c48]Unknown NAL code: 13
Error while decoding stream #0.0
[h264 @ 0x8336c48]AVC: Consumed only 1028 bytes instead of 2027582804 
Segmentation fault
steve@laptop:~$ 

```

Am actually getting some output, with sound but the picture is choppy and very blocky especially with movement (an animated film - so easy to see the breakups)

Film is 624 * 352  23 frames/sec and has an ac3 soundtrack with 2 subtitle tracks (vosub), we're using PAL here, but either ntsc or pal wil do.

Unfortunately most of what i'm seeing resembles image 0, thus by movement.
Any ideas?

---

### Post by stoer on 2006-12-18
Me again....my hours now up, so that's it until tonight;) 

Just to see what would happen with the sample created (see above) by applying the 2 passes in mencoder...

```
steve@laptop:~$ mencoder /home/steve/afilm2/by.mpg -ovc xvid -xvidencopts pass=1 -oac mp3lame -lameopts vbr=3 -o /dev/null
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
91 audio & 204 video codecs
success: format: 0  data: 0x0 - 0x7197000
MPEG-PS file format detected.
Detected unknown aspect_ratio_information in mpeg sequence header.
Please report the aspect value (0) along with the movie type (VGA,PAL,NTSC,SECAM) and the movie resolution (720x576,352x240,480x480,...) to the MPlayer developers, so that we can add support for it!
Assuming 1:1 aspect for now.
VIDEO:  MPEG2  720x480  (aspect 0)  29.970 fps  9000.0 kbps (1125.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 5.1 (3f+2r+lfe)  48000 Hz  448.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
xvid: using library version 1.1.0 (build xvid-1.1.0)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
MP3 audio selected
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: XviD (720x480 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=720x480, sampled=720x480
xvid: 2Pass Rate Control -- 1st pass
Writing header...2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.003 [0:0]
ODML: vprp aspect is 16384:10922.
Writing header...
ODML: vprp aspect is 16384:10922.

1 duplicate frame(s)!
Pos:   0.6s     22f ( 0%)  0.00fps Trem:   7min   6mb  A-V:0.070 [0:31]
Skipping frame!
Pos:   0.9s     32f ( 0%)  0.00fps Trem:   8min   7mb  A-V:0.070 [0:32]
Skipping frame!
Pos:   1.2s     42f ( 0%)  0.00fps Trem:   8min   7mb  A-V:0.070 [39:32]
Skipping frame!
Pos:   1.5s     52f ( 0%)  0.00fps Trem:   9min   7mb  A-V:0.070 [34:32]
Skipping frame!
Pos:   1.8s     62f ( 0%) 55.71fps Trem:   9min   7mb  A-V:0.070 [31:32]
Skipping frame!
Pos:   2.2s     74f ( 0%) 57.10fps Trem:  10min   8mb  A-V:0.070 [29:31]
Skipping frame!
Pos:  27.4s    830f (13%) 43.75fps Trem:   1min 107mb  A-V:-0.070 [4550:36]
1 duplicate frame(s)!
Pos:  27.8s    840f (14%) 43.54fps Trem:   1min 106mb  A-V:-0.069 [4595:37]
1 duplicate frame(s)!
Pos:  29.0s    875f (15%) 42.94fps Trem:   1min 105mb  A-V:-0.067 [4721:41]
1 duplicate frame(s)!
a52: CRC check failed!  ) 37.97fps Trem:   0min 104mb  A-V:-0.034 [5940:107]
a52: error at resampling
Pos: 145.9s   4378f (100%) 37.97fps Trem:   0min 105mb  A-V:-0.032 [5945:107]
Flushing video frames
Writing index...
Writing header...
ODML: vprp aspect is 16384:10922.

Video stream: 5945.901 kbit/s  (743237 B/s)  size: 108472401 bytes  145.946 secs  4378 frames

Audio stream:  107.705 kbit/s  (13463 B/s)  size: 1963248 bytes  145.824 secs
steve@laptop:~$ mencoder /home/steve/afilm2/by.mpg -ovc xvid -xvidencopts pass=2:bitrate=800 -oac mp3lame -lameopts vbr=3 -o final.avi
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
91 audio & 204 video codecs
success: format: 0  data: 0x0 - 0x7197000
MPEG-PS file format detected.
Detected unknown aspect_ratio_information in mpeg sequence header.
Please report the aspect value (0) along with the movie type (VGA,PAL,NTSC,SECAM) and the movie resolution (720x576,352x240,480x480,...) to the MPlayer developers, so that we can add support for it!
Assuming 1:1 aspect for now.
VIDEO:  MPEG2  720x480  (aspect 0)  29.970 fps  9000.0 kbps (1125.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 5.1 (3f+2r+lfe)  48000 Hz  448.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
xvid: using library version 1.1.0 (build xvid-1.1.0)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
MP3 audio selected
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: XviD (720x480 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=720x480, sampled=720x480
xvid: 2Pass Rate Control -- 2nd pass -- bitrate=800kbit/s
Writing header...2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.003 [0:0]
ODML: vprp aspect is 16384:10922.
Writing header...
ODML: vprp aspect is 16384:10922.

1 duplicate frame(s)!
Pos:   0.6s     22f ( 0%)  0.00fps Trem:   7min  12mb  A-V:0.070 [0:31]
Skipping frame!
Pos:   0.9s     32f ( 0%)  0.00fps Trem:   8min  12mb  A-V:0.070 [0:32]
Skipping frame!
Pos:   1.2s     42f ( 0%)  0.00fps Trem:   8min  11mb  A-V:0.070 [39:32]
Skipping frame!
Pos:   1.5s     52f ( 0%)  0.00fps Trem:   9min  11mb  A-V:0.070 [34:32]
Skipping frame!
Pos:   1.8s     62f ( 0%) 56.78fps Trem:   9min  10mb  A-V:0.070 [31:32]
Skipping frame!
Pos:   2.2s     74f ( 0%) 58.92fps Trem:   9min  10mb  A-V:0.070 [29:31]
Skipping frame!
Pos:  27.4s    830f (13%) 27.39fps Trem:   3min  14mb  A-V:-0.070 [558:36]
1 duplicate frame(s)!
Pos:  27.8s    840f (14%) 27.20fps Trem:   3min  13mb  A-V:-0.069 [559:37]
1 duplicate frame(s)!
Pos:  29.0s    875f (15%) 26.67fps Trem:   2min  13mb  A-V:-0.067 [562:41]
1 duplicate frame(s)!
a52: CRC check failed!  ) 22.36fps Trem:   0min  14mb  A-V:-0.034 [751:107]
a52: error at resampling
Pos: 145.9s   4378f (100%) 22.36fps Trem:   0min  15mb  A-V:-0.032 [752:107]
Flushing video frames
Writing index...
Writing header...
ODML: vprp aspect is 16384:10922.

Video stream:  752.376 kbit/s  (94046 B/s)  size: 13725762 bytes  145.946 secs  4378 frames

Audio stream:  107.705 kbit/s  (13463 B/s)  size: 1963248 bytes  145.824 secs
steve@laptop:~$ 

```

Ok, that's me done for now.  Anybody with a suggestion or ideas? Appreciate any help you can give.

ps.
Playing the original .mkv in VLC gives the same Blocky quality as the ripped .mpg  Playing the original in either Kaffeine or mplayer gives excellent reproduction.  Is that a clue?

Found the following...
MKVToolnix -- Cross-platform tools for Matroska (mkvtoolnix   mkvmerge   mkvextract) and will try with another thread to find out a bit more about these tools if i can't get any further with the above methods.
[http://ubuntuforums.org/showthread.php?t=321114](http://ubuntuforums.org/showthread.php?t=321114)

---

### Post by netyire on 2006-12-19
[SIZE="2"]
OK, the situation is currently:
1. Mencoder dies with "too many packets in bla bla bla"
2. FFmpeg creates crappy picture

So, so far... the situation can be expressed as: ](*,)  (Why, why why?) ](*,)  All right, but from what I understand playing it under mplayer is ok... Hmm perhaps mplayer can skip the problematic part while mencoder dies. As for ffmpeg making poor quality files, well... :-k (If you find out, please share).

OK, so from what I understand, mencoder and ffmpeg ain't doing it for you but it plays fine. OK, I think you can try this, if it does not work... then well for now I don't think I can think of anything else...

First install VLC (its a media player with the ability to transcode stuff [is transcode the right word?]). To do so type the following:

```
sudo apt-get install vlc
```

Once that is done, run VLC (it should be in the menus under Sound & Video) if not then type

```
vlc
```

from the terminal. Once that is done, click file -> quick open file and then select the problematic file. Does it play properly? If so great, please continue :D .

To transcode the file to (hopefully) something which won't make mencoder choke and die, do the following:

1. Click file -> wizard (as the file is playing)
2. Choose transcode/save to file and click next
3. Select existing playlist item and choose the currently playing file, click next
4. Select both the boxes transcode audio and video
5. Set the video codec to h264 and the audio codec to mp3
6. Put both bitrates to the highest possible and click next
7. Choose ASF and click next
8. Type a filename like /home/name/ihopethisworks.asf
9. Click finish
10. Wait and pray
11. Once it is done (hopefully) use:

```
mencoder input.asf -ovc lavc -oac mp3lame -lameopts vbr=3 -lavcopts vcodec=mpeg4:vpass=1:vbitrate=800 -o /dev/null
```

and then

```
mencoder input.asf -ovc lavc -oac mp3lame -lameopts vbr=3 -lavcopts vcodec=mpeg4:vpass=2:vbitrate=800 -o finally.avi
```

Finally, whether it works or not, please post the results.

Sorry for the long due reply. :( 
[/SIZE]

---

### Post by stoer on 2006-12-19
Hey, nice that you replied at all.
You've at least got some ideas - i've run out of them. That is other than mkvtoolnix.
(To be honest i'd rather try with what i have, seeing that i've lttle information about the use of this set of tools).
Happen to have VLC installed, so i'll take your suggestion for a spin when i get home tonight (that'll be late, after midnight - work getting in the way of all the fun).
Will post what i get back.
Again thanks.

---

### Post by balance07 on 2006-12-19
here's my suggestion: forget about linux for a second. download and fire up "VirtualDubMod" in winxp. drag the .mkv in. set video output to "direct stream copy" and hit F7. change filetype to .avi and hit save. should take only a minute or so to complete the output and you'll have an .avi waiting for you.

if for some reason that don't work, i'd try nixing the subtitles (streams... highlight and delete). if THAT doesn't work, something is seriously whacked and therefore beyond my expertise.

---

### Post by stoer on 2006-12-19
Netyire,
VLC plays the .mkv but the picture is very poor, very choppy and blocky.
Tried your suggestion and created an .asf file (completes in approx 30 seconds or so) and tried the first pass through mencoder...



```
steve@laptop:~$ mencoder /home/steve/afilmrework/letmesee.asf -ovc lavc -oac mp3lame -lameopts vbr=3 -lavcopts vcodec=mpeg4:vpass=1:vbitrate=800 -o /dev/null
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
91 audio & 204 video codecs
success: format: 0  data: 0x0 - 0xe4
ASF file format detected.
ASF: no audio or video headers found - broken file?
ASF: No video stream found.
Video stream is mandatory!

Exiting...
steve@laptop:~$ mencoder /home/steve/afilmrework/letmesee.asf -ovc lavc -oac mp3lame -lameopts vbr=3 -lavcopts vcodec=mpeg4:vpass=1:vbitrate=800 -o /dev/null
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
91 audio & 204 video codecs
success: format: 0  data: 0x0 - 0xe4
ASF file format detected.
ASF: no audio or video headers found - broken file?
ASF: No video stream found.
Video stream is mandatory!

Exiting...

```

1. VLC doesn't like the format or i'm missing a codec, file plays fine in kaffeine.
2. I'm Guessing the creation of the .asf is not working as planned and hence the problems in mencoder.

There's an option to do this all in windows, free and proffessional software.  I've seen a couple of guides for this.   Be nice of course if it were doable from within linux and seeing as how many of these tools began life as open source...
mkvtoolnix is available for linux, and mkvextractor (name says it all) has to be worth a shot.  Just got to see if i can figure out how to install it :-k 

I'll take a look anyway.
Thanks again for the tips, i'll post what i find.
Cheers again.

---

### Post by stoer on 2006-12-19
> **balance07 said:**
> here's my suggestion: forget about linux for a second. download and fire up "VirtualDubMod" in winxp. drag the .mkv in. set video output to "direct stream copy" and hit F7. change filetype to .avi and hit save. should take only a minute or so to complete the output and you'll have an .avi waiting for you.

if for some reason that don't work, i'd try nixing the subtitles (streams... highlight and delete). if THAT doesn't work, something is seriously whacked and therefore beyond my expertise.

Hi, also thanks for the tip.  I downloaded this tool in the weekend, was still figuring it out, will also give it a whirl using your directions.  
If i can i'd like to try to solve it in linux, but i'm also willing to see what windows can deliver :) 
Many thanks.

---

### Post by stoer on 2006-12-19
> **stoer said:**
> Hi, also thanks for the tip.  I downloaded this tool in the weekend, was still figuring it out, will also give it a whirl using your directions.  
If i can i'd like to try to solve it in linux, but i'm also willing to see what windows can deliver :) 
Many thanks.

Tried dragging the .mkv into virtualdubmod, i see the matroska filter parsing, then niks nada.
this ends with a warning over the subs (supported not supported formats),  the streaming option is already selected as default, but then...
F7 remains greyed out and i can't progress further ](*,) 
Sorry, but i don't know enough about this tool to know what i'm doing wrong.

Now 01.15 and i'm knackered, 
Time to call it a day.

Again thanks for the interest and your help.

---

### Post by stoer on 2006-12-20
Ok Guys,

mkvextract (windows version - is also available for linux but i've currently got no time to go researching all the command line possibilites, probably also too little experience](*,) )

This is a pic of what i got.


So, now i have a video, V MPEG4/iso/AVC (track1.h264)    and an audio file,   audio (A_AC3)  (track2.ac3)
The 2 subtitle files, 1. S_VOSUB english and  2. S_TEXT?UTF8  dutch  i didn't bother with.

From your experience have i now got something to work with from within Linux?  Its the .h264 that's throwing me now. What can mux these 2 together and output as a dvd or divx/xvid?

Appreciate any helpyou can give.

Cheers.

---

### Post by stoer on 2006-12-20
Sorry hope this pic is better...;)

---

### Post by netyire on 2006-12-21
Lets hope the extracted video and audio files are error free.  OK, first copy the h.264 video, ac3 audio and the English subtitle files to a folder which can be accessed in Ubuntu. Ok, now boot into Ubuntu.

Right, forget the subtitles for a while and try to get the h.264 and ac3 stuff into a nice avi file. Disclaimer: Get tissuebox ready in case of failure.

```
mencoder -ovc lavc -oac lavc -audiofile myaudio.ac3 myvideo.stuff -lavcopts vcodec=mpeg4:vbitrate=5000:acodec=mp3:abitrate=192 -o movie.avi
```

Ok, (SUPPOSING) it works, use the following to get the subtitles in:

```
mencoder movie.avi -sub <subtitle.srt> -subfont-text-scale 3 -ovc copy -oac copy -ffourcc xvid -o final.avi
```

Does it work? If it does, than ditch the tissue.

---

### Post by stoer on 2006-12-21
Netyire,
(reaches for a tissue, but not quite ready, stops....)

Almost there i think.

```
steve@laptop:~$ mencoder -ovc lavc -oac lavc -audiofile /home/steve/afilm2/Track2.ac3 /home/steve/afilm2/Track1.h264 stuff -lavcopts vcodec=mpeg4:vbitrate=5000:acodec=mp3:abitrate=192 -o movie.avi
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
91 audio & 204 video codecs
success: format: 0  data: 0x0 - 0x34e1e406
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
libavformat file format detected.
[V] filefmt:65536  fourcc:0x44535644  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 5.1 (3f+2r+lfe)  48000 Hz  448.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 UYVY 
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.

SwScaler: BICUBIC scaler, from Packed YUY2 to Planar YV12 using MMX2
videocodec: libavcodec (720x480 fourcc=34504d46 [FMP4])
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
Audio LAVC, couldn't find encoder for codec mp3

Exiting...

```

Missing something....?
.......  Could not find matching colorspace - retrying with -vf scale...

.........Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
         Audio LAVC, couldn't find encoder for codec mp3

---

### Post by stoer on 2006-12-21
Ok...
because i said i wanted to, i've  just done the extraction using the linux version of the tools mkvtoolnix/mkvmerge/mkvextract....
Not that this is the answer, still delivers an h264 file of course, but what the hell we're using Linux, right? (pleased with myself 8) )
see [http://ubuntuforums.org/showthread.php?t=321114](http://ubuntuforums.org/showthread.php?t=321114) for where to download this and for doccumentation.

mkvmerge -i movie.mkv
to identify the contants of the mkv file.

```
steve@laptop:~$ mkvmerge -i /home/steve/afilm/BYMKV/by.mkv

File '/home/steve/afilm/BYMKV/by.mkv': container: Matroska
Track ID 1: video (V_MPEG4/ISO/AVC)
Track ID 2: audio (A_AC3)
Track ID 3: subtitles (S_VOBSUB)
Track ID 4: subtitles (S_TEXT/UTF8)

```

mkvextract tracks movie.mkv 1:by.h264
to extract the video.

```
steve@laptop:~$ mkvextract tracks /home/steve/afilm/BYMKV/by.mkv 1:by.h264

Extracting track 1 with the CodecID 'V_MPEG4/ISO/AVC' to the file 'by.h264'.
progress: 100%
```


mkvextract tracks movie.mkv 2:audio.ac3 3:subtitles.srt
to extract the audio and subtitle track 3

```
steve@laptop:~$ mkvextract tracks /home/steve/afilm/BYMKV/by.mkv 2:audio.ac3 3:subtitles.srt
Extracting track 2 with the CodecID 'A_AC3' to the file 'audio.ac3'.
Extracting track 3 with the CodecID 'S_VOBSUB' to the file 'subtitles.srt'.
Writing the VobSub index file 'subtitles.idx'.
progress: 100%
```

mkvextract tracks movie.mkv 4:subtitles.srt
to extract the last subtitle track

steve@laptop:~$ mkvextract tracks /home/steve/afilm/BYMKV/by.mkv 4:subtitles.srt

```
Extracting track 4 with the CodecID 'S_TEXT/UTF8' to the file 'subtitles.srt'.
progress: 100%
steve@laptop:~$ 
```


Gives me the following...
by.h264
audio.ac3
subtitles.sub
subtitles.srt
subtitles.idx

Just need to be able to mux these together.

---

### Post by netyire on 2006-12-21
[SIZE="2"]

OK... I tried this and it works fine. See if this works for you :D :

```
mencoder -ovc xvid -oac mp3lame -xvidencopts bitrate=5000 -lameopts abr:br=128 -audiofile <audiofile> <videofile> -o nosubtitles.avi
```

Just change <audiofile> and <videofile> accordingly.
Then add in the subtitles (I did not try this on the files):

```
mencoder nosubtitles.avi -sub mysubtitles.srt -subfont-text-scale 3 -ovc copy -oac copy -o subtitled.avi
```

Hopefully this should avoid the "Audio LAVC, couldn't find encoder for codec mp3" problem though the colorspace... hmm. :-k 

[/SIZE]

---

### Post by stoer on 2006-12-22
Hi.
Ok this runs, processes for approx 15 minutes or so....

```
steve@laptop:~$ mencoder -ovc xvid -oac mp3lame -xvidencopts bitrate=5000 -lameopts abr:br=128 -audiofile /home/steve/afilm3/audio.ac3 /home/steve/afilm3/by.h264 -o /home/steve/afilm3/testfilm.avi
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
91 audio & 204 video codecs
success: format: 0  data: 0x0 - 0x34e1e406
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
libavformat file format detected.
[V] filefmt:65536  fourcc:0x44535644  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 5.1 (3f+2r+lfe)  48000 Hz  448.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
xvid: using library version 1.1.0 (build xvid-1.1.0)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 UYVY 
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: XviD (720x480 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=720x480, sampled=720x480
xvid: CBR Rate Control -- bitrate=5000kbit/s
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
MP3 audio selected
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Writing header...
ODML: vprp aspect is 16384:10922.
Writing header...
ODML: vprp aspect is 16384:10922.
Pos:   0.7s     21f ( 0%)  6.66fps Trem:   0min   0mb  A-V:0.067 [0:32]
Skipping frame!
Pos:   1.0s     31f ( 0%)  7.75fps Trem:   0min   0mb  A-V:0.067 [14232:32]
Skipping frame!
Pos:   1.3s     41f ( 0%)  8.46fps Trem:   0min   0mb  A-V:0.067 [13193:32]
Skipping frame!
Pos:   1.6s     51f ( 0%)  8.97fps Trem:   0min   0mb  A-V:0.067 [12520:31]
Skipping frame!
Pos:   1.9s     61f ( 0%)  9.36fps Trem:   0min   0mb  A-V:0.067 [11996:32]
Skipping frame!
Pos:   2.2s     71f ( 0%)  9.76fps Trem:   0min   0mb  A-V:0.067 [11616:31]
Skipping frame!
Pos:   2.6s     84f ( 0%) 10.01fps Trem:  13min 347mb  A-V:0.067 [11141:32]
Skipping frame!
Pos:  27.2s    822f (10%) 10.92fps Trem:  10min 225mb  A-V:-0.068 [7617:34]
1 duplicate frame(s)!
Pos:  27.6s    832f (10%) 10.92fps Trem:  10min 228mb  A-V:-0.068 [7607:35]
1 duplicate frame(s)!
Pos:  28.0s    844f (10%) 10.91fps Trem:  10min 231mb  A-V:-0.068 [7600:36]
1 duplicate frame(s)!
Pos: 246.5s   7393f (100%) 10.85fps Trem:   0min 220mb  A-V:-0.049 [7365:119]
Flushing video frames
Writing index...
Writing header...
ODML: vprp aspect is 16384:10922.

Video stream: 7365.737 kbit/s  (920717 B/s)  size: 226999642 bytes  246.547 secs  7393 frames

Audio stream:  119.611 kbit/s  (14951 B/s)  size: 3693816 bytes  247.056 secs
steve@laptop:~$ 
```


Picture is just coloured blocks, see attachment.

Not sure why this is happening, tried it now 3 or 4 times with the same results. Using the extracted files from 
both the windows version of extractor and then with the files extracted with the linux version.
naturally this means little, and there is a very real chance of something being miss with both sets.  Anyway to check the 
extracted files for faults?  You've tried your coding and it works for you, so maybe there's something i'm missing - codec- or similar?
Sorry that i've come up with such a poser...

---

### Post by netyire on 2006-12-22
OK, (besides the beautifully colored blocks that increase your degree) it seems that that did not work for you ](*,) . I took a look at mencoder's output which you posted and I noticed two things :KS :

1. You are using MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team however I'm using MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team. Perhaps this has some difference?

2. The colorspace is yuv2 (what is yuv2? :confused: ) anyway, maybe you could force using yuv12 instead by using the -vf format=yv12. Perhaps that would remove the (beautifully colored) blocks that (besides increasing your degree) is mostly useless.

So, I think you could try the following:

1. Remove mencoder and install the one in the Ubuntu repos, (Avoiding the third party ones), if you have third party repos, maybe you could remove it first, replace mencoder, and then put the third party repos back.
          -> Step: Remove third party repos which you have added.
          -> Remove mencoder
          -> Reload repos (Synaptic) or apt-get update
          -> Install mencoder (from the ubuntu repos)
          -> Put back the third party repos (however, do not update mencoder to the one provided by the third party repos)

2. If you have tried the above, and it is still yuv2 (WHY!), instead of entering:

```
mencoder -ovc xvid -oac mp3lame -xvidencopts bitrate=5000 -lameopts abr:br=128 -audiofile <audiofile> <videofile> -o nosubtitles.avi
```

Enter:

```
mencoder -ovc xvid -oac mp3lame -xvidencopts bitrate=5000 -lameopts abr:br=128 -audiofile <audiofile> <videofile> -vf format=yv12 -o nosubtitles.avi
```

Perhaps this will solve the problem. Happy holidays and a hopefully bugfree new year ;) !

---

### Post by stoer on 2006-12-24
1. You are using MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team however I'm using MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team. Perhaps this has some difference?

Man.....
been trying for 2 days to find opre8 vs.  tried your suggested sources list tip.
Have just now noticed that you're using Edgy! (he he.....)
I think in Dapper the opre7try is still the official version, because no matter what i do i can't 
find the opre8 version.

hey, anyways.  it's again late here and i'm working tomorrow ( Christmas, i know - still someones got to do it )

Will look at this after the holidays.

Again thanx for all the help to date, really appreciate it.

Happy Christmas.

---

### Post by netyire on 2006-12-26
Ops... (Looks like I jumped the gun) ah well, no harm meant. ;)  Maybe I should have checked if you were using Dapper first... ](*,) Anyway, try forcing the colorspace to yuv12, maybe that works :).

Happy boxing day (Christmas is over :( )

---

### Post by stoer on 2007-01-03
> **netyire said:**
> Ops... (Looks like I jumped the gun) ah well, no harm meant. ;)  Maybe I should have checked if you were using Dapper first... ](*,) Anyway, try forcing the colorspace to yuv12, maybe that works :).

Happy boxing day (Christmas is over :( )


Hi, and a happy new year to you.
I'm still working so not had a chance to try the above as yet.  Hopefully Friday i'll get the chance (tonight, if i can stay awake).
Whatever, will let you know what happens.

(did get my old pc working a few days ago, might try setting edgy up on that - depends on the specs.... sooo much to do and sooo little time).

---

### Post by stoer on 2007-01-04
Ok, ran it again.
Afraid it's still the green blocks, but with sound.

I'm goingto see if i can't download another version of this film, 
I'm starting to doubt the  film segments integrity, it might be interesting to pack and unpack another avi and run mencoder on the resulting files - will at least let me see if the fault lies in my original film or not. 

Keep you posted.

---

### Post by netyire on 2007-01-05
Let me know if it works! (Green Blocks huh...:-k  oh well, sorry my suggestion did not work:-? ) Wonder what the problem is?

---

### Post by stoer on 2007-01-08
Hi Netyire,
It looks like i might have to wait a little for another avi, release date here in Holland is soon.
I did however find a ripped dvd version that works fine...

I've spent several days searching and looking into this and the most probable solution that i can come up with is that there is a encoding fault in the film.

I found a windows program, convertx2dvd [http://www.vso-software.fr/products/convert_x_to_dvd/](http://www.vso-software.fr/products/convert_x_to_dvd/)
That works fine on other mkv packed films, but even this program stumbled on this one ](*,) 

I've enclose a few screenshots showing settings and output from this.
The resulting dvd, yes it did the conversion, stutters and loses sync - sound is poor but the picture quality is good.

Chances are extremely high that by an error free film all your tips would have worked perfectly, sorry about that.

I'll keep an eye out for another avi to try, might be a while though.
Again; many, many thanks for all your help and time. I very much appreciate it.

---

### Post by netyire on 2007-01-10
In the end its a Windows program that does it ([-( ](*,) ). Ah well... really could wonder what the problem was. If you find out, do let me know! ;)

---

