---
title: "Media sharing files not visible"
date: 2021-01-08
forum: General Help
---

### Post by ploegmma on 2021-01-08
Hi,

I've got a DVD box for Christmas and the only DVD player in my house is in my Ubuntu PC. I can play the content but I would like to view it on TV (LG smart TV). I read about the media sharing feature and turned it on. My TV can see my Ubuntu PC and it can play a file (screen cast) on my TV. So I used handbrake to rip a DVD to see if I could play that also. The ripped file can be played using vlc but my TV doesn't show the file. I made a few copies of the file that does play to see if it has something to do with the file extension (used several extensions) and these all show up and can be played. But the ripped one doesn't show. I also tried with VLC on my laptop and there also only the ripped file does not show (the other does and can be played).

So, what's going on here? Is it protected somehow? Is there a way for me to stream my DVD's using Ubuntu?

Thnx

---

### Post by TheFu on 2021-01-08
Commercial DVD movies have copy protection. In much of the world, it is legal to make a copy provided you retain the physical DVD and DVD license.  Ubuntu addresses this with the non-free media extensions, I think.  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)  I haven't tried to access any DVDs in a few years on my Ubuntu systems, but something like that link is what I did.

I use handbrake a bunch.  It knows to look for some libraries that are part of the restricted-extras and if those exist, it will use them.

File extensions are just that, file extensions.  To Linux, the actual file contents matter more than the extension.  Only some GUI programs care about the extensions.  As for what your TV cares about, I couldn't say.  If you transcode the DVD files into h.264/aac/mp4 containers, those will almost always work.  However, h.264/aac/mkv containers can support much more flexibility, including multiple audio streams, multiple captions, multiple subtitles all in the same MKV container. If your TV supports MKV, use it.  With DVDs, using h.265 is probably a poor choice for video codec. It requires much more powerful processing than what all TVs provide.

To see the details of any video file, inside VLC, open the file, then under Tools --> Codec Information will be the details for each stream inside the file.  Sadly, the VLC team decided that allowing us to copy/paste that data wasn't useful. Too bad.

---

### Post by ploegmma on 2021-01-10
Thank you! I will try with these extensions. The strange thing is that I don't get an error when encoding with handbrake and the resulting file plays fine locally. It just doesn't show up when I access the directory over the local network using my TV or VLC on an other computer. Anyway, I will try these steps and see if that works.

---

### Post by TheFu on 2021-01-10
> **ploegmma said:**
> Thank you! I will try with these extensions. The strange thing is that I don't get an error when encoding with handbrake and the resulting file plays fine locally. It just doesn't show up when I access the directory over the local network using my TV or VLC on an other computer. Anyway, I will try these steps and see if that works.

Without knowing the container and transcoded codecs used, what can I say?  Handbrake can create millions of different types of video files. Saying "handbrake made it" is like saying a car is driving around somewhere on Earth.  Not enough specifics for anyone to guess what you did.

---

### Post by SeijiSensei on 2021-01-10
How are you sharing the files to the TV? Using a DLNA server like minidlna? Plex? I run minidlna and my LG TV can see and play many of the shared files. There are formats it's not happy with like, I believe, H.265 and HEVC. I don't think it likes 10-bit color either.

My older Sony TV is allergic to formats like Matroska and other open technologies.

---

### Post by #&amp;thj^% on 2021-01-10
> **ploegmma said:**
>  Is there a way for me to stream my DVD's using Ubuntu?

Thnx

Along with the great suggestions already mentioned, My wife drove me absolutely crazy over this, instead of going through the motions of teaching/learning all this, I just installed Kodi on her laptop with an HDMI cable to the TV, now plays all that Linux can play, Files, Audio CD's, DVD Movies from a DVD Drive and more. Just A thought.

---

### Post by ploegmma on 2021-01-11
**update**

Thanks for the suggestions. I considered using other ways like Plex or Kodi but was hoping to keep it as basic a possible (I just wanted to use the built-in client in my webos LG TV). I finally got things going. Here's my findings;

It turned out to be the file extension after all (at least partly). I did already rename the files once (to webm as this was the extension of files that were showing) but that didn't work. Handbrake creates M4V files. I renamed it to MP4 and now they show up in both VLC (from another machine on the network) as well as my TV. I do however have to turn off/on media sharing in Ubuntu settings first after new files are created. It seems as if Ubuntu is not indexing new files. Also the files don't show up with their file name, I think it is using the title property.

So for me the procedure now is to use handbrake to rip (just the defaults, H.264 I think), change the file extension from M4V to MP4 after encoding, switch off/on media sharing and that's it, the new file shows up in VLC on a device or in my LG webos TV.

Again, thnx for your input.

---

### Post by TheFu on 2021-01-11
handbake can create h.264/aac/mp4 files directly. There are slight-to-huge differences inside these media files. They can't just be renamed always and keep working, always.

The dlna server that canonical installs by default is called Rygel. it isn't very good. [https://wiki.gnome.org/Projects/Rygel](https://wiki.gnome.org/Projects/Rygel)
[https://ubuntuhandbook.org/index.php/2020/04/home-media-server-ubuntu-2004/](https://ubuntuhandbook.org/index.php/2020/04/home-media-server-ubuntu-2004/)

---

### Post by ajgreeny on 2021-01-11
I use minidlna on my laptop to share video, music and images to an LG Smart Tv with no problems except for a very few media files with unplayable codecs, and I don't have any of those any more as I converted them all to playable types with ffmpeg.

I tried rygel in my Xubuntu but it was hopeless when compared with minidlna as it did not even show many of the files. I didn't bother to investigate that, I'm afraid, but simply moved back to minidlna which I knew worked fine.

To see exactly what the codecs in your video (or music) file is you can install and use mediainfo ```
mediainfo /path/to/filename
```
It will output lots of information as I show below.
```
mediainfo StreetFair1.mp4 
General
Complete name                            : StreetFair1.mp4
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42 (mp42/mp41/isom/avc1)
File size                                : 19.5 MiB
Duration                                 : 3 min 22 s
Overall bit rate mode                    : Variable
Overall bit rate                         : 807 kb/s
Encoded date                             : UTC 2013-09-22 15:38:07
Tagged date                              : UTC 2013-09-22 15:38:07

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L3.1
Format settings                          : CABAC / 4 Ref Frames
Format settings, CABAC                   : Yes
Format settings, Reference frames        : 4 frames
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 3 min 22 s
Bit rate                                 : 750 kb/s
Width                                    : 640 pixels
Height                                   : 360 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 23.976 (24000/1001) FPS
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.136
Stream size                              : 18.1 MiB (93%)
Writing library                          : x264 core 129 r2245 bc13772
Encoding settings                        : cabac=1 / ref=3 / deblock=1:0:0 / analyse=0x3:0x113 / me=hex / subme=7 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=12 / lookahead_threads=2 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=3 / b_pyramid=2 / b_adapt=1 / b_bias=0 / direct=1 / weightb=1 / open_gop=0 / weightp=2 / keyint=72 / keyint_min=24 / scenecut=40 / intra_refresh=0 / rc_lookahead=40 / rc=2pass / mbtree=1 / bitrate=750 / ratetol=1.0 / qcomp=0.60 / qpmin=5 / qpmax=69 / qpstep=4 / cplxblur=20.0 / qblur=0.5 / vbv_maxrate=1125 / vbv_bufsize=3750 / nal_hrd=none / ip_ratio=1.40 / aq=1:1.00
Encoded date                             : UTC 2013-09-22 15:38:07
Tagged date                              : UTC 2013-09-22 15:38:07
Codec configuration box                  : avcC

Audio
ID                                       : 2
Format                                   : AAC LC
Format/Info                              : Advanced Audio Codec Low Complexity
Codec ID                                 : mp4a-40-2
Duration                                 : 3 min 22 s
Source duration                          : 3 min 22 s
Bit rate mode                            : Variable
Bit rate                                 : 53.4 kb/s
Channel(s)                               : 1 channel
Channel layout                           : C
Sampling rate                            : 48.0 kHz
Frame rate                               : 46.875 FPS (1024 SPF)
Compression mode                         : Lossy
Stream size                              : 1.29 MiB (7%)
Source stream size                       : 1.29 MiB (7%)
Encoded date                             : UTC 2013-09-22 15:38:07
Tagged date                              : UTC 2013-09-22 15:38:07


```

---

