---
title: "MP4 to MP3"
date: 2014-05-10
forum: General Help
---

### Post by Nigel_Storm on 2014-05-10
G'day,

Just wondering if there is a nice, clean but efficient converter package out there that I can use to convert from MP4 format to MP3 format? 

I know of K3b package to burn them onto CD's etc but not sure if this comes with a converter as well?

Many thanks guyss.
Nigel.

---

### Post by monkeybrain20122 on 2014-05-10
ffmpeg. For a easy to use gui get winff from the repository.

---

### Post by Yellow Pasque on 2014-05-10
mp4 is video and mp3 is audio (unless you're talking about m4a audio, which is really AAC inside an mpeg4 container).

Ubuntu uses avconv by default as opposed to ffmpeg.
```
avconv -i <inputfile> <options> <outputfile>
```

---

### Post by Nigel_Storm on 2014-05-10
> 
ffmpeg version 0.8.10-4:0.8.10-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:56:59 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/thor/Downloads/[HD] 2014 Proggresive House Mix 4 - melodical_chill house.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    creation_time   : 2014-03-09 22:24:04
  Duration: 01:04:54.45, start: 0.000000, bitrate: 949 kb/s
    Stream #0.0(und): Video: h264 (High), yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 755 kb/s, 23.98 fps, 23.98 tbr, 24k tbn, 47.95 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 192 kb/s
    Metadata:
      creation_time   : 2014-03-09 22:25:12
Unknown encoder 'libmp3lame'
Press Enter to Continue


Wow.... help please :(

"avconv" maybe better but not exactly sure what the synthax is.. I mean i can see your synthax.. but what to write in real life, I wouldn't have a clue.....

Yes trying to convert mp4 video format into mp3 so that i can listen to it in my car/mp3 player etc...

Thanks in advance.

---

### Post by Nigel_Storm on 2014-05-11
aha never mind!! I did a little research on this forum and installed 
> 
sudo apt-get install ubuntu-restricted-extras

and the problem was solved!! Amazing.. file encoding in process as we speak! :D

---

### Post by Yellow Pasque on 2014-05-11
Instead of converting to mp3, I would encode to flac and then burn that. You're going to lose audio quality converting from AAC to mp3.

---

