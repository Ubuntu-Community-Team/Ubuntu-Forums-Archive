---
title: "Aplay to play mp3"
date: 2019-04-05
forum: General Help
---

### Post by raleigh3 on 2019-04-05
I am trying to get aplay to play an mp3 at 44100 Hz.

It's confusing.

Like trying to find what channel to use.

a```
play -c 1 -t wav -r 44100 -f Relax_6_Seconds.wav
aplay: main:604: wrong extended format 'Relax_6_Seconds.wav'
```

---

### Post by raleigh3 on 2019-04-05
I guess aplay is not very popular.

---

### Post by #&amp;thj^% on 2019-04-05
> **raleigh3 said:**
> I guess aplay is not very popular.

Well I would like to kindly :) point out:
> I am trying to get aplay to play an [COLOR="#FF0000"]mp3 [/COLOR]at 44100 Hz.
But your asking aplay to:
```
play -c 1 -t wav -r 44100 -f Relax_6_Seconds[COLOR="#FF0000"].wav[/COLOR]
**_EDIT: Can you see anything wrong there?_**
**Is the file really a ".wav" **might be the root of the problem, just a guess though.
aplay: main:604: wrong extended format 'Relax_6_Seconds.wav'
```
ffmpeg will work with right code, example:
```
ffplay '/home/me/Music/Atomic Bride - Radio Recession.mp3' 
```
Output from that results in:
```

ffplay version n4.1.2 Copyright (c) 2003-2019 the FFmpeg developers
  built with gcc 8.2.1 (GCC) 20181127
  configuration: --prefix=/usr --disable-debug --disable-static --disable-stripping --enable-fontconfig --enable-gmp --enable-gnutls --enable-gpl --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libdrm --enable-libfreetype --enable-libfribidi --enable-libgsm --enable-libiec61883 --enable-libjack --enable-libmodplug --enable-libmp3lame --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libv4l2 --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx264 --enable-libx265 --enable-libxcb --enable-libxml2 --enable-libxvid --enable-nvdec --enable-nvenc --enable-omx --enable-shared --enable-version3
  libavutil      56. 22.100 / 56. 22.100
  libavcodec     58. 35.100 / 58. 35.100
  libavformat    58. 20.100 / 58. 20.100
  libavdevice    58.  5.100 / 58.  5.100
  libavfilter     7. 40.101 /  7. 40.101
  libswscale      5.  3.100 /  5.  3.100
  libswresample   3.  3.100 /  3.  3.100
  libpostproc    55.  3.100 / 55.  3.100
[mp3 @ 0x6c8bd8000b80] Estimating duration from bitrate, this may be inaccurate
Input #0, mp3, from '/home/me/Music/Atomic Bride - Radio Recession.mp3':
  Metadata:
    artist          : Atomic Bride
    title           : Radio Recession
    encoded_by      : Ripped with Streamripper
    track           : 24
  Duration: 00:02:52.61, start: 0.000000, bitrate: 128 kb/s
    Stream #0:0: Audio: mp3, 44100 Hz, stereo, fltp, 128 kb/s

```
Give it a whirl, maybe this will work well enough for you.
BTW The only use aplay for me is a speaker test.

---

### Post by raleigh3 on 2019-04-05
I found the problem. 

I used vlc to convert the mp3 to wav.

aplay could not play that wav file.

I used mpg321 to convert the file.

```
aplay /usr/share/sounds/My_Sounds/Relax.wav
```

---

### Post by #&amp;thj^% on 2019-04-05
There you go, Nicely Done.;)
Just a couple more choices to consider.
The play command from the sox package will play any file format supported by sox

To install sox open terminal and run:
```

sudo apt-get install sox
sudo apt-get install sox libsox-fmt-all
```

To use play command:
```

play file-name.extension
```

See "man" sox for more information.
my favorite is using Audacious:
```
audacious -Hq your.mp3
```
A couple more worth noting is "[cmus]("https://cmus.github.io/")" and "[moc]("http://moc.daper.net/")"
my favorite is using Audacious:
```
audacious -Hq your.mp3
```

---

