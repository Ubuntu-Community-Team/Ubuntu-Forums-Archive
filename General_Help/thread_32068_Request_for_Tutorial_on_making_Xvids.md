---
title: "Request for Tutorial on making Xvids"
date: 2005-05-06
forum: General Help
---

### Post by delltony on 2005-05-06
I have read several pages on various forums and even tried to understand the man page for ffmpeg but I can not seem to figure out how to make xvids from DVD's (Yes I own them). See here is the reason I wish to do this. I am a traveling Field Tech and I like to watch dvds and what have you in my hotel room or even on the planes for that matter however it becomes a major hassel luggin around tons of dvds where i could put around 4 or so on a single dvdr if they are in xvid format.  With this being said here as what I have tried and has failed. 

```
making backups of dvds to xvid (ffmeg, mpgtx, xvid,dvdback)
  1) add ffmeg,mpgtx,dvdbackup to system
  2) rip the dvd first
  3) then join the vobs
     get the biggest set of the VTS_NN* FILES
     usually NN=01
     actually joining:
      shell:/my/ripped/dvd/folder> mpgtx join -o VTS_ALL.VOB VTS_NN_1.VOB VTS_NN_2.VOB...

  4) choosing encoding options vidbitsrateskpbs and audiobitrate
     **this is the complex part**
      first need to figure out what your output bitrate(s) will be
      audio sounds good at 128kbps or 160 for hi-fi mp3s = AUDIOBITRATE
      get the lenth of the movie by using mpginfo VTS_ALL.VOB
      change that length to seconds
      usually movie is between 4800 and 9600 secs
      if you need a formula for that 
      totalsec = sec + ((hr*60)+min)*60)
      kilobits per second = kibibits /sec
      choose your output size.
      you can do 700 meg if you want.
      but find kibibits
      kibibis = megabytes * 1024 * 8
          (e.g. for 700 meg its 700 * 1024 * 8 )
      now you need the actual rates
          easy: size / time
                 example: (700 * 1024 * 8) / (9600) = VIDEOBITRATE but take 98 percent of that
           videobitrate - audiorate = total


   5) find the frame size 
         for widescreen:
           width = vidbitratekbps / 1.5
         for fullscreen:
            width = vidbitratekbps / 2.2
          round to the nearest multiple of 8
            perl -e '$br = widthreplaceme;print $br - ($br % 8)."\n'\"'  = WIDTH
         
         now find the height (use a cover if possible to get the ratio)
           height = originalwidth/orginalheight * newwidth (use only if can't find cover)
           if have box use exact ratio (example 2.34 )
           round to the nearist multiple of 8
             perl -e '$br = heightreplaceme;print $br - ($br % 8)."\n'\"' = HEIGHT
    6) now encode
            ffmpeg -i VTS_ALL.VOB -f avi -b VIDEOBITRATE -s WIDTHxHEIGHT -vcodec xvid -acodec mp3 -ab AUDIOBITRATE my_rip.avi
```

However when I try this method after doing all the math and what have you I get the following results.

[color=#FF0000]Output #0, avi, to 'my_rip.avi':
  Stream #0.0: Video: mpeg4, 370x51882, 25.00 fps, q=2-31, 654 kb/s
  Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0x82d0e1c]removing common factors from framerate
Unsupported codec for output stream #0.1[/color]

I then tried mencoder with the following syntax:
mencoder allvobs.vob -ovc xvid -oac mp3lame -xvidencopts pass=1 -o xviddvd.avi

and i get the following results:

[b]MEncoder 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Intel Pentium 4/Xeon/Celeron Northwood (Family: 8, Stepping: 4)
Detected cache-line size is 64 bytes
CPUflags: Type: 8 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

77 audio & 188 video codecs
File not found: 'frameno.avi'
Failed to open frameno.avi
MPlayer was compiled without libmp3lame support.[/b]

Help would be greatly appreciated and a step by step tutorial would be even better. Thanks in advance.
-Tony-

---

### Post by deathbyswiftwind on 2006-03-20
Tony have you tried using acid rip? Thats what I use to make up all backup copies of my movies They look great and are in great sizes

---

### Post by art2003 on 2006-06-11
in your last line change -acodec mp3

for -acodec mp2
or
-acodec vorbis

those two are built-in the ffmpeg distributed with ubuntu.

---

### Post by linuchsan on 2006-06-11
Are you sure you are on (k)ubuntu? Cause MPlayer was compiled without libmp3lame support, sounds like a mandrake install.

---

