---
title: "Edit MPEG video?"
date: 2005-09-28
forum: General Help
---

### Post by dtessier on 2005-09-28
I have some MPEG clips that I want to edit. I basically want to remove some frames at the beginning and at the end. I know of a few tools that can do it, but I would prefer something that doesn't require to re-render, or transcode, the whole video. Are there any tools to easily do this?

---

### Post by KingBahamut on 2005-09-28
apt-get install kino 


I think kino will do what you need it to do for you. 

[http://www.kinodv.org/](http://www.kinodv.org/)

---

### Post by dtessier on 2005-09-28
Hmmm, that's strange, I tried Kino last night and it would not even open my file. The dialog was only looking for DV files. I guess I'll take a deeper look tonight.

Thanks!

---

### Post by KingBahamut on 2005-09-28
No problem dtess, let us know if you have anymore issues.

---

### Post by davmac on 2005-10-03
I'm trying to do the same thing and am having problems with Kino. When I try to open up the file I get the message "Invalid file specified".

The mpeg plays OK in xine so I'm assuming that the file is OK. I have made sure I've got mjpegtools and ffmpeg installed. What else have I missed or is there another app that you'd recommend that I try?

Thanks in advance,

Dave Mac

---

### Post by miketyson on 2005-10-03
G'day
If you use mencoder with -ss and -endpos, and -acodec copy -vcodec copy, you can crop the middle, while not recompressing - It'll just copy the stream data.
I'm not sure if that's a solution you're after, but it'll do the trick without losing video quality :)

---

### Post by xmastree on 2005-10-03
[QUOTE=dtessier]Hmmm, that's strange, I tried Kino last night and it would not even open my file.[/QUOTE]In my experience, Kino won't open anything.
My other applications, mplayer, totem, gxine can play most video files, but kino won't do a thing. It's a waste of space.
I'd be interested if there is any working program for this. I'm currently downloading a couple of large video files and I'm wondering how to get them on to a VCD or DVD once they're finished.

---

### Post by dtessier on 2005-10-03
[QUOTE=xmastree]In my experience, Kino won't open anything.
My other applications, mplayer, totem, gxine can play most video files, but kino won't do a thing. It's a waste of space.
I'd be interested if there is any working program for this. I'm currently downloading a couple of large video files and I'm wondering how to get them on to a VCD or DVD once they're finished.[/QUOTE]
Kino is meant to work with DV only, as I have found this weekend. It can export other formats, but can only read in DV.
[QUOTE=miketyson]G'day
If you use mencoder with -ss and -endpos, and -acodec copy -vcodec copy, you can crop the middle, while not recompressing - It'll just copy the stream data.
I'm not sure if that's a solution you're after, but it'll do the trick without losing video quality[/QUOTE]
Perfect! I'll try that tonight. Hopefully, the -ss and -endpos can provide frame-level granularity.
One of these days, I will need to learn more about all of that tool's options, it seems very powerful.

---

### Post by ColinG on 2005-10-10
I've just tried Kino but it won't save captured DV as a project. It just says cannot save SMIL. Not sure if there is a library or something missing - I know Kino is pretty heavy on dependencies but I did use the Ununtu deb package via the package manager.

Any ideas out there?

I've used Kino for months now and have found it very reliable. I have nmade severalm dvd's with Edgy and Dapper. I usually install via Automatix but that sid when I have installed from the repos all has been well.

As for Cinelerra mentioned later in this thread, I doubt you'll fins a deb available which is why I boot alongside FC6 - it has an up to date verion of Cinelerra. I stll find Kino is my preferred app though.

---

### Post by smeager on 2005-10-10
You can use cinelerra or lives to do the job.

---

### Post by glug101 on 2005-10-10
[QUOTE=dtessier]Kino is meant to work with DV only, as I have found this weekend. It can export other formats, but can only read in DV.

Perfect! I'll try that tonight. Hopefully, the -ss and -endpos can provide frame-level granularity.
One of these days, I will need to learn more about all of that tool's options, it seems very powerful.[/QUOTE]

Warning!  If you plan to use those files for vcd or similar you will want to use the mencoder -of option and specify that the file should be in an mpeg container.  Mencoder defaults to avi container format which is not compatible with vcd's, svcd's, or (I believe though I have never used it) dvd's.  

Yes, mencoder is a smart piece of software that I turn to for many things, but there are so many gotcha's involved with it (like the one that I just posted).  My experience with it so far has been that the command line is difficult to use, but the gui front ends didn't have the control that I needed.  So, I just typed up templates of functions I use on the command line and copy and paste them in as needed out of a text file.

Wish I knew how to program a gui frontend though.....

---

### Post by xy77 on 2006-02-19
I tried
```
$ mencoder -ss 532 -endpos -oac copy -ovc copy -of mpeg somefile.mpg
```

```
$ mencoder -ss 00:09:03 -endpos -oac copy -ovc copy -of mpeg somefile.mpg
```

[COLOR="Red"]which didn't remove (edit)[/COLOR] anything from the movie. I manage to convert mpg to vob using replex:
```
$ replex -o outputfile.vob -t DVD < somefile.mpg
```

I hope to be able to use kino for editing, because lives is definately too slow in my case. Otherwise, I'll remove bytes until I reach the correct frame which is kind of brute force, but what can I do :-)


Speaking of replex, I found out it's quite useable in combination with qdvdcreator. Short howto for anyone interested.

[LIST=1]
[*]use replex to create the appropriate vob files (see above)
[*]in qdvdcreator add all videos in correct order
[*]create a menu text and make it a button (pointing to the first video)
[*]create a menu.wav using e.g. audiacity (a few seconds silence)
[*]let qdvdcreator generate code for menu creation (make sure to cat menu.wav instead of generating a wav on-the-fly (didn't work for me)) and execute each line one after the other
[*]run the create dvd command generated by qdvdcreator
[*]generate iso using k3b and filling VIDEO_TS with the files generated
[*]burn iso image
[/LIST]

That worked for me, ask if you have questions or something is misunderstandable.

- David (xy77)

---

### Post by xy77 on 2006-02-20
I also managed to crop the vob files without too much hassle. First I tried dd with --skip, but that was more trial-and-error than straight ahead. But split provides the functionality I needed:

```

$ split -b <bytes> file.vob

```

To calculate <bytes> I started the vob with gxine, checked its duration and divided it's size in bytes by its duration (using bc). You will get at least two files (it depends on how much you have to crop) that are vob streams; use the one you need.

Hope this helps someone.

- David (xy77)

PS: had some trouble creating a valid qdvdauthor menu. It worked after I created a new project from scratch and did all steps after another without restart (qdvdauthor crashes sometimes). If anyone knows how to recreate the VIDEO_TS.VOB (which is the menu if I figured it out correctly) without regenerating all the DATA files it would save me some time.

---

### Post by Statik on 2006-03-02
I am struggling to get any video editor working with Breezy. I've tried Kino, Cinelerra and Lives. All are not functioning properly. This is a fairly fresh install of Breezy with automatix used to setup most things. No other tweaking was done. I have several mpgs that were recoded using tovid (which works great) that are not openable in most, or, if they do open, the program crashes quickly. All I need is the ability to load in images and clips, transition between them (x-fade) and add audio to certain still clips. That's it. I can transcode and make DVDs with the working tools I have.

One video is a transcoded clip of the Mars pathfinder. Attempting to load it into Kino (which seems to be most stable, but least cooperative) gives the following output.
```

>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
MEncoder dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags: Type: 8 MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE

86 audio & 200 video codecs
File not found: 'frameno.avi'
Failed to open frameno.avi
success: format: 0  data: 0x0 - 0xb368800
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  7840.0 kbps (980.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 2.0 (stereo)  48000 Hz  224.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [a52] afm:liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [dsize=4:3]
Opening video filter: [expand w=720 h=540]
Expand: 720 x 540, -1 ; -1, osd: 0, aspect: 0.000000, round: 1
Opening video filter: [scale]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred csp: Mpeg PES)
The selected video_out device is incompatible with this codec.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Writing AVI header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
VDec: vo config request - 720 x 480 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4

SwScaler: BICUBIC scaler, from Planar YV12 to Planar YV12 using MMX
videocodec: libavcodec (720x540 fourcc=31564646 [FFV1])
[ffv1 @ 0x858b890]this codec is under development, files encoded with it may not be decodeable with future versions!!!
use vstrict=-2 / -strict -2 to use it anyway
Could not open codec.
FATAL: Cannot initialize video driver.

Exiting...
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Warning: not compiled with thread support, using thread emulation
/home/statik/Desktop/Sojourner1.mpg.avi: could not find codec parameters
>> Leaving Editor
>> Left Editor
>> Starting Editor

```

Attempting to open the un transcoded file gives:

```

>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
MEncoder dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags: Type: 8 MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE

86 audio & 200 video codecs
File not found: 'frameno.avi'
Failed to open frameno.avi
success: format: 0  data: 0x0 - 0x14d4004
MPEG-PS file format detected.
VIDEO:  MPEG1  320x240  (aspect 1)  23.976 fps  250.0 kbps (31.2 kbyte/s)
[V] filefmt:2  fourcc:0x10000001  size:320x240  fps:23.98  ftime:=0.0417
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8000->176400)
Selected audio codec: [mp3] afm:mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [dsize=4:3]
Opening video filter: [expand w=720 h=540]
Expand: 720 x 540, -1 ; -1, osd: 0, aspect: 0.000000, round: 1
Opening video filter: [scale]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 320 x 240 (preferred csp: Mpeg PES)
The selected video_out device is incompatible with this codec.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Writing AVI header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
VDec: vo config request - 320 x 240 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4

SwScaler: BICUBIC scaler, from Planar YV12 to Planar YV12 using MMX
videocodec: libavcodec (720x540 fourcc=31564646 [FFV1])
[ffv1 @ 0x858b890]this codec is under development, files encoded with it may not be decodeable with future versions!!!
use vstrict=-2 / -strict -2 to use it anyway
Could not open codec.
FATAL: Cannot initialize video driver.

Exiting...
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Warning: not compiled with thread support, using thread emulation
/home/statik/Desktop/mer2003-sfx-320x240.mpg.avi: could not find codec parameters
>> Leaving Editor
>> Left Editor
>> Starting Editor

```

I'd really like to get this working for a project at school. Otherwise I'm going to have to resort to *ugh* Windows

Help appreaciated

Statik

---

### Post by charles nicholls on 2006-11-20
You could also try Mainactor not free but a first class app
link for Ubuntu deb:-D  [http://downloads.mainconcept.com/fdl.php?downloads.mainconcept.com+MainActorLinux5.5.36Ubuntu6+mainactor-5.5-36.i386.ubuntu-6.06.deb](http://downloads.mainconcept.com/fdl.php?downloads.mainconcept.com+MainActorLinux5.5.36Ubuntu6+mainactor-5.5-36.i386.ubuntu-6.06.deb)

---

