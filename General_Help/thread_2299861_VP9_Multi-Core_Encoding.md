---
title: "VP9 Multi-Core Encoding"
date: 2015-10-21
forum: General Help
---

### Post by tristan16 on 2015-10-21
I want to use the WebM format and the VP9 codec for YouTube videos. The problem is that when I use FFmpeg, the VP9 encoder only uses 1 core, resulting in a very slow encoding process. A 10-minute video at 60 FPS 720p takes about 2 hours to convert. According to [this guide]("http://wiki.webmproject.org/ffmpeg/vp9-encoding-guide"), Multi-threaded encoding may be used if [COLOR=#006000]-threads [/COLOR]> 1 and [COLOR=#006000]-tile-columns [/COLOR]> 0. Yet when I specify these options in FFmpeg, it still encodes very slowly and only uses 1 of my 8 cores (12% according to System Monitor).

So there's my problem and what I've already found. Can anyone help me find how to get multi-threaded encoding to work? Do I have to use 2-pass to enable this feature, or am I doing something else wrong? Everything I've found so far tells me to use -tile-columns and -threads, but when I do that it still only uses 1 core.

Thank you in advance for any help concerning this issue. Worst comes to worst, I'll just script my video conversions to run overnight, or just let YouTube re-convert my "incompatible MP4 video even though I followed the recommended settings."

---

### Post by mc4man on 2015-10-22
multi-thread encoding of vp9 works here but vp9 is very slow, using 8 threads actually works out to be about 2.5 times faster than 1 thread. 
ex. from mpstat (8 threads) - 
```
01:17:38 AM  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest  %gnice   %idle
01:17:58 AM  all   35.70    0.00    0.23    0.01    0.00    0.00    0.00    0.00    0.00   64.06
01:17:58 AM    0   36.50    0.00    0.30    0.00    0.00    0.00    0.00    0.00    0.00   63.20
01:17:58 AM    1   25.80    0.00    0.20    0.00    0.00    0.00    0.00    0.00    0.00   73.99
01:17:58 AM    2   20.73    0.00    0.35    0.00    0.00    0.00    0.00    0.00    0.00   78.92
01:17:58 AM    3   16.41    0.00    0.20    0.00    0.00    0.00    0.00    0.00    0.00   83.39
01:17:58 AM    4   39.45    0.00    0.15    0.05    0.00    0.00    0.00    0.00    0.00   60.35
01:17:58 AM    5   44.09    0.00    0.20    0.00    0.00    0.00    0.00    0.00    0.00   55.71
01:17:58 AM    6   43.21    0.00    0.15    0.05    0.00    0.00    0.00    0.00    0.00   56.59
01:17:58 AM    7   59.44    0.00    0.25    0.00    0.00    0.00    0.00    0.00    0.00   40.31

```
screen is generally the same as reflected in sys monitor

---

### Post by tristan16 on 2015-10-22
> **mc4man said:**
> multi-thread encoding of vp9 works here but vp9 is very slow, using 8 threads actually works out to be about 2.5 times faster than 1 thread. 
ex. from mpstat (8 threads) - 
```
01:17:38 AM  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest  %gnice   %idle
01:17:58 AM  all   35.70    0.00    0.23    0.01    0.00    0.00    0.00    0.00    0.00   64.06
01:17:58 AM    0   36.50    0.00    0.30    0.00    0.00    0.00    0.00    0.00    0.00   63.20
01:17:58 AM    1   25.80    0.00    0.20    0.00    0.00    0.00    0.00    0.00    0.00   73.99
01:17:58 AM    2   20.73    0.00    0.35    0.00    0.00    0.00    0.00    0.00    0.00   78.92
01:17:58 AM    3   16.41    0.00    0.20    0.00    0.00    0.00    0.00    0.00    0.00   83.39
01:17:58 AM    4   39.45    0.00    0.15    0.05    0.00    0.00    0.00    0.00    0.00   60.35
01:17:58 AM    5   44.09    0.00    0.20    0.00    0.00    0.00    0.00    0.00    0.00   55.71
01:17:58 AM    6   43.21    0.00    0.15    0.05    0.00    0.00    0.00    0.00    0.00   56.59
01:17:58 AM    7   59.44    0.00    0.25    0.00    0.00    0.00    0.00    0.00    0.00   40.31

```
screen is generally the same as reflected in sys monitor

Well can you please tell me how to use multi-thread encoding? My system monitor shows 1 core at 100% and the other 7 cores idling.

---

### Post by FakeOutdoorsman on 2015-10-22
YouTube is going to re-encode anything you give it. So currently, when compared to x264, the only advantage for you to use VP9 is the *potential* for a resulting smaller file size and therefore less wait to upload to YouTube. Of course this **really** depends on the encoding options you use.

According to [VP9 encoding/decoding performance vs. HEVC/H.264](https://blogs.gnome.org/rbultje/2015/09/28/vp9-encodingdecoding-performance-vs-hevch-264/):
> ...if your CPU usage target for x264 is anything faster than veryslow, you basically want to keep using x264, since at that same CPU usage target, x265 will give worse quality for the same bitrate than x264. The story for libvpx is slightly better than for x265, but it’s clear that these next-gen codecs have a lot of work left in this area. This isn’t surprising, x264 is a lot more mature software than x265/libvpx.

Personally, I would just use x264 until/if libvpx-vp9 matures more. A few tips are at [FFwiki: YouTube](https://trac.ffmpeg.org/wiki/EncodeforYouTube).

---

### Post by tristan16 on 2015-10-22
> **FakeOutdoorsman said:**
> YouTube is going to re-encode anything you give it. So currently, when compared to x264, the only advantage for you to use VP9 is the *potential* for a resulting smaller file size and therefore less wait to upload to YouTube. Of course this **really** depends on the encoding options you use.

According to [VP9 encoding/decoding performance vs. HEVC/H.264](https://blogs.gnome.org/rbultje/2015/09/28/vp9-encodingdecoding-performance-vs-hevch-264/):


Personally, I would just use x264 until/if libvpx-vp9 matures more. A few tips are at [FFwiki: YouTube](https://trac.ffmpeg.org/wiki/EncodeforYouTube).

Clearly this is not the correct forum since you are not answering my question. For the record, I already encoded several videos with VP9 in the WebM format, and YouTube was able to instantly play them without re-encoding. 


I've also been using H.265 for my media server, and the movies have the same visual quality at half the size. 

I only posted here because using x264 works fine on Windows, but on Ubuntu, YouTube says it's incompatible. Looks like it's on to the Google forums, since they're the ones that invented VP9.

---

### Post by FakeOutdoorsman on 2015-10-22
> I've also been using H.265 for my media server, and the movies have the same visual quality at half the size. 

Clearly, you're ignoring encoding speed. 10-20x slower is not a good trade off in my opinion.

> I only posted here because using x264 works fine on Windows, but on Ubuntu, YouTube says it's incompatible. Looks like it's on to the Google forums, since they're the ones that invented VP9.
Have fun with that.

---

### Post by mc4man on 2015-10-23
> **tristan16 said:**
> Well can you please tell me how to use multi-thread encoding? My system monitor shows 1 core at 100% and the other 7 cores idling.
you would need to post your ffmpeg, libvpx versions & command used.

---

### Post by Yellow Pasque on 2015-10-23
While you're at it, you may want to post the command you're running to encode h264. If its filesize is acceptable to you, then it's obviously a lot faster to encode that than h265 or vp9.

---

### Post by tristan16 on 2015-10-26
> **FakeOutdoorsman said:**
> Clearly, you're ignoring encoding speed. 10-20x slower is not a good trade off in my opinion.


Have fun with that.

Clearly, you're ignoring the file size. 50% smaller file is an amazing trade off in my opinion, especially since I'm blessed with very, very slow upload speed.

> **Temüjin said:**
> While you're at it, you may want to post the command you're running to encode h264. If its filesize is acceptable to you, then it's obviously a lot faster to encode that than h265 or vp9.

This is why I hate forums somedays. Instead of giving me an answer, everyone is telling me to not do it. There's a reason I'm using H.265 and VP9. If filesize didn't matter, I'd leave everything in the original MKV, where every 20 minute video is 2GB.

---

### Post by Yellow Pasque on 2015-10-26
> **tristan16 said:**
> Instead of giving me an answer, everyone is telling me to not do it.

I only asked because you said, "or just let YouTube re-convert my "incompatible MP4 video even though I followed the recommended settings."
So I thought maybe h264 was your first choice.

> This is why I hate forums somedays. 
Please give the information mc4man asked for. Help us help you.

---

