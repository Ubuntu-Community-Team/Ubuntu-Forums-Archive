---
title: "MPEG sound is crackly"
date: 2007-04-17
forum: General Help
---

### Post by Higgo on 2007-04-17
I have been using ffmpeg and devede to convert my avi files to mpegs however the play back of mpeg files sound crackly but not the orginal avi files.  This is for both ALSA and OSD. 

ffmpeg -version
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
ffmpeg      SVN-rUNKNOWN
libavutil   3211264
libavcodec  3345152
libavformat 3278080


I'm running feisty beta up to date.

Is there another program to convert my avi's to mpegs that can help me bypass this issue?
Thanks for any help.

---

### Post by Higgo on 2007-04-17
Ok. I googled and found another app called tovid.

I will see if this works for me.

---

### Post by Higgo on 2007-04-17
No still sounds crackly. Actually my avi's are also crackly.

Has anyone else experienced this with feisty?

---

### Post by muximus on 2007-04-19
m also experiencing the same problem.. can it b solved by upgrading alsa, or maybe by installing xine??

in fact, now tht i check it, i get no sound frm the built in speakers (altec lansing) and this horrible noise with the headphones

plzz help

---

### Post by der_joachim on 2007-04-19
If you open an equalizer app, at what level is your PCM? It should be at around 60-70%.

---

