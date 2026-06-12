---
title: "can't record sound"
date: 2013-06-09
forum: General Help
---

### Post by JamesTheAwesomeDude on 2013-06-09
I'm trying to record some sound from a flash game that has a rather neat soundtrack, so I start the game up, and then run this in the terminal:
```
arecord -f cd -t raw | oggenc - -r -o out.ogg
```...after about 40 seconds, I press CTRL-C:
```
james@james-OptiPlex-GX620:~$ arecord -f cd -t raw | oggenc - -r -o out.oggEncoding standard input to 
         "out.ogg" 
at quality 3.00
Recording raw data 'stdin' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
    Encoding [ 0m41s so far] \ ^CAborted by signal Interrupt...


james@james-OptiPlex-GX620:~$
```

The sound file is created, it's about 487.4 KB, and the Audio tab of its properties looks like this:
> **General**
[I]Title:            Unknown
Artist:        Unknown
Album:        Unknown
Year:            Unknown
Duration:        Unknown
Comment: [/I]

[B]Audio
[/B][I]Codec:        Vorbis
Channels:        Stereo
Sample rate:    44100 Hz
Bitrate:        112 kbps[/I]

Everything appears to be fine, but when I try to play it, I hear nothing. I've tried Rythmbox, Movie Player, and VLC, and the result is identical.

Perhaps I'm recording the sound from the wrong input device? If so, what is the correct argument to "listen in" to Adobe Flash Player?

---

### Post by HiImTye on 2013-06-09
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
```
sudo apt-get install pavucontrol
pavucontrol
```
start recording then set the input to a mirror of whatever your desktop sounds are

---

