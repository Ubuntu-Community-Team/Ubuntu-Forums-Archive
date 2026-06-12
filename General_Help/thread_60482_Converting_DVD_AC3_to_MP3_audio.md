---
title: "Converting DVD AC3 to MP3 audio"
date: 2005-08-28
forum: General Help
---

### Post by mpx on 2005-08-28
I used tcextract to produce ac3 files. What tools are available to convert ac3 to mp3 or wav files so that I can burn them to CD?

Thanks.

---

### Post by arnieboy on 2005-08-28
[QUOTE=mpx]I used tcextract to produce ac3 files. What tools are available to convert ac3 to mp3 or wav files so that I can burn them to CD?

Thanks.[/QUOTE]
use ffmpeg
```
sudo apt-get install ffmpeg
```
now convert your ac3 files to mp3 files.
do this:
```
ffmpeg -i input_file.ac3 -target mp3 output.mp3
```
Change "input_file.ac3" and "output.mp3" suitably.
for all additional options of ffmpeg do a :
```
man ffmpeg
```

---

### Post by mpx on 2005-08-28
Thanks arnieboy for the reply. When I try running ffmpeg like below it gives an error.

[INDENT]$ **ffmpeg -i song.ac3 -target mp3 song.mp3**
ffmpeg version cvs, build 4753, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --prefix=/usr --libdir=${prefix}/lib --enable-shared --enable-mp3lame --host=i386-linux --enable-gpl --build=i386-linux --enable-faad --mandir=${prefix}/share/man --enable-vorbis --enable-pthreads --enable-faac --enable-xvid --enable-dts cc --enable-amr_nb --enable-amr_wb --enable-pp --enable-shared-pp --enable-libogg --enable-a52bin --enable-x264
  built on Jun  9 2005 15:41:29, gcc: 3.3.5 (Debian 1:3.3.5-13)
Input #0, ac3, from 'song.ac3':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Audio: 0x0000
Assuming PAL for target.
Unknown target: mp3
[/INDENT]

Next I looked up the help for ffmpeg and ran like this: (it still gives an error). Any ideas?

[INDENT]$ **ffmpeg -i song.ac3 -acodec mp3 -ab 128 song.mp3**
ffmpeg version cvs, build 4753, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --prefix=/usr --libdir=${prefix}/lib --enable-shared --enable-mp3lame --host=i386-linux --enable-gpl --build=i386-linux --enable-faad --mandir=${prefix}/share/man --enable-vorbis --enable-pthreads --enable-faac --enable-xvid --enable-dts cc --enable-amr_nb --enable-amr_wb --enable-pp --enable-shared-pp --enable-libogg --enable-a52bin --enable-x264
  built on Jun  9 2005 15:41:29, gcc: 3.3.5 (Debian 1:3.3.5-13)
Input #0, ac3, from 'song.ac3':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Audio: 0x0000
Output #0, mp3, to 'song.mp3':
  Stream #0.0: Audio: mp3, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
[/INDENT]

---

### Post by arnieboy on 2005-08-28
[QUOTE=mpx]Thanks arnieboy for the reply. When I try running ffmpeg like below it gives an error.

[INDENT]$ **ffmpeg -i song.ac3 -target mp3 song.mp3**
ffmpeg version cvs, build 4753, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --prefix=/usr --libdir=${prefix}/lib --enable-shared --enable-mp3lame --host=i386-linux --enable-gpl --build=i386-linux --enable-faad --mandir=${prefix}/share/man --enable-vorbis --enable-pthreads --enable-faac --enable-xvid --enable-dts cc --enable-amr_nb --enable-amr_wb --enable-pp --enable-shared-pp --enable-libogg --enable-a52bin --enable-x264
  built on Jun  9 2005 15:41:29, gcc: 3.3.5 (Debian 1:3.3.5-13)
Input #0, ac3, from 'song.ac3':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Audio: 0x0000
Assuming PAL for target.
Unknown target: mp3
[/INDENT]
change the bitrate from 128 to something else and try again. u will have to play around with this app and find out what works for u...

Next I looked up the help for ffmpeg and ran like this: (it still gives an error). Any ideas?

[INDENT]$ **ffmpeg -i song.ac3 -acodec mp3 -ab 128 song.mp3**
ffmpeg version cvs, build 4753, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --prefix=/usr --libdir=${prefix}/lib --enable-shared --enable-mp3lame --host=i386-linux --enable-gpl --build=i386-linux --enable-faad --mandir=${prefix}/share/man --enable-vorbis --enable-pthreads --enable-faac --enable-xvid --enable-dts cc --enable-amr_nb --enable-amr_wb --enable-pp --enable-shared-pp --enable-libogg --enable-a52bin --enable-x264
  built on Jun  9 2005 15:41:29, gcc: 3.3.5 (Debian 1:3.3.5-13)
Input #0, ac3, from 'song.ac3':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Audio: 0x0000
Output #0, mp3, to 'song.mp3':
  Stream #0.0: Audio: mp3, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
[/INDENT][/QUOTE]
change the bitrate to something else (right now its 128). u have to play around with this app to find out what works for u. google a bit.. that might give u hints as well.

---

### Post by TheKiteGuy on 2007-12-08
I had the same problem. This worked for me:
```

transcode -i title1.ac3 -y null,wav -o title1.wav

```

---

