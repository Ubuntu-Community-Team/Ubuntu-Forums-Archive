---
title: "OpenShot Won't Start - Python MLT Error"
date: 2012-11-07
forum: General Help
---

### Post by Kirk Schnable on 2012-11-07
I have an end user machine where OpenShot will not launch.

OpenShot version 1.4.0, Python 2.7.3, on Xubuntu 12.04, all updates are installed.

When running OpenShot out of the terminal, I get this output:


```
------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
OpenShot (version 1.4.0)
--------------------------------
Process no longer exists: 13373. Creating new pid lock file.
No LADSPA plugins were found!

Check your LADSPA_PATH environment variable.

Detecting formats, codecs, and filters...
---
video_codecs:
- a64multi
- a64multi5
- asv1
- asv2
- bmp
- cljr
- dnxhd
- dpx
- dvvideo
- ffv1
- ffvhuff
- flashsv
- flv
- gif
- h261
- h263
- h263p
- huffyuv
- jpegls
- ljpeg
- mjpeg
- mpeg1video
- mpeg2video
- mpeg4
- msmpeg4v2
- msmpeg4
- pam
- pbm
- pcx
- pgm
- pgmyuv
- png
- ppm
- qtrle
- rawvideo
- roqvideo
- rv10
- rv20
- sgi
- snow
- svq1
- targa
- tiff
- v210
- v410
- wmv1
- wmv2
- zlib
- zmbv
- libdirac
- libschroedinger
- libtheora
- libvpx
- libx264
- libxvid
...
---
audio_codecs:
- aac
- ac3
- ac3_fixed
- alac
- eac3
- flac
- mp2
- nellymoser
- real_144
- vorbis
- wmav1
- wmav2
- roq_dpcm
- adpcm_adx
- g722
- g726
- adpcm_ima_qt
- adpcm_ima_wav
- adpcm_ms
- adpcm_swf
- adpcm_yamaha
- libgsm
- libgsm_ms
- libmp3lame
- libspeex
- libvo_aacenc
- libvo_amrwbenc
- libvorbis
...
---
formats:
- a64
- ac3
- adts
- adx
- aiff
- amr
- asf
- ***
- asf_stream
- au
- avi
- avm2
- cavsvideo
- crc
- daud
- dirac
- dnxhd
- dts
- dv
- eac3
- ffm
- ffmetadata
- filmstrip
- flac
- flv
- framecrc
- framemd5
- g722
- gif
- gxf
- h261
- h263
- h264
- image2
- image2pipe
- ipod
- ivf
- latm
- m4v
- md5
- matroska
- matroska
- mjpeg
- mlp
- mmf
- mov
- mp2
- mp3
- mp4
- mpeg
- vcd
- mpeg1video
- dvd
- svcd
- mpeg2video
- vob
- mpegts
- mpjpeg
- mxf
- mxf_d10
- null
- nut
- ogg
- oma
- alaw
- mulaw
- f64be
- f64le
- f32be
- f32le
- s32be
- s32le
- s24be
- s24le
- s16be
- s16le
- s8
- u32be
- u32le
- u24be
- u24le
- u16be
- u16le
- u8
- psp
- rawvideo
- rm
- RoQ
- rso
- rtp
- rtsp
- sap
- segment
- smjpeg
- sox
- spdif
- srt
- swf
- 3g2
- 3gp
- truehd
- rcv
- voc
- wav
- webm
- yuv4mpegpipe
- alsa
- oss
...

------------------------- ERROR 2 ------------------------------
Failed to import 'from openshot.openshot import main'
Error Message: 'NoneType' object has no attribute 'set_cursor'
----------------------------------------------------------------

OpenShot has failed to import some of the Python files or libraries
required for our application to run. Here are some trouble shooting
tips:

Tip 1) Check if MLT can be successfully imported in Python. Run the
following commands, and see if any errors are displayed. If you get
an error, you need to investigate the correct way to install MLT.
NOTE: Do not type the $ or >> characters in the examples below.

$ python
>> import mlt
>> mlt.Factory().init()

Tip 2) If MLT is working from the first example, then the next tip is
to look at the above error messages very closely, and google for more
help. It's likely the problem is already reported, and maybe there is
a simple work-around. Also, you can search for bugs or report a new
bug at https://bugs.launchpad.net/openshot. Good luck! 
```

When attempting to run the Python commands suggested, I get this output:

```

Python 2.7.3 (default, Aug 1 2012, 05:16:07)
4.6.3 on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import mlt
>>> mlt.Factory().init()
No LADSPA plugins were found!

Check your LADSPA_PATH environment variable.
<mlt.Repository; proxy of <Swig Object of type 'Mlt::Repository *' at 0xa34da40> >
>>> 
```

Anybody seen this before or have any suggestions?

Thanks
Kirk Schnable

---

### Post by Kirk Schnable on 2012-11-07
I uninstalled and reinstalled OpenShot and Python's MLT libraries...

```
sudo apt-get remove openshot python-mlt3 --purge
```

```
sudo apt-get install python-mlt3
```

```
sudo apt-get install openshot
```

Then I got rid of the old profile settings for the user.

```
mv ~/.openshot/ ~/.openshot-old/
```

After doing this, OpenShot still throws an error, but apparently this is normal (?) because OpenShot still successfully starts.  I believe this issue has been resolved.

Output from OpenShot now:
```
------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.4.0)
--------------------------------
Process no longer exists: 5431.  Creating new pid lock file.
No LADSPA plugins were found!

Check your LADSPA_PATH environment variable.

Detecting formats, codecs, and filters...
---
video_codecs:
  - a64multi
  - a64multi5
  - asv1
  - asv2
  - bmp
  - cljr
  - dnxhd
  - dpx
  - dvvideo
  - ffv1
  - ffvhuff
  - flashsv
  - flv
  - gif
  - h261
  - h263
  - h263p
  - huffyuv
  - jpegls
  - ljpeg
  - mjpeg
  - mpeg1video
  - mpeg2video
  - mpeg4
  - msmpeg4v2
  - msmpeg4
  - pam
  - pbm
  - pcx
  - pgm
  - pgmyuv
  - png
  - ppm
  - qtrle
  - rawvideo
  - roqvideo
  - rv10
  - rv20
  - sgi
  - snow
  - svq1
  - targa
  - tiff
  - v210
  - v410
  - wmv1
  - wmv2
  - zlib
  - zmbv
  - libdirac
  - libschroedinger
  - libtheora
  - libvpx
  - libx264
  - libxvid
...
---
audio_codecs:
  - aac
  - ac3
  - ac3_fixed
  - alac
  - eac3
  - flac
  - mp2
  - nellymoser
  - real_144
  - vorbis
  - wmav1
  - wmav2
  - roq_dpcm
  - adpcm_adx
  - g722
  - g726
  - adpcm_ima_qt
  - adpcm_ima_wav
  - adpcm_ms
  - adpcm_swf
  - adpcm_yamaha
  - libgsm
  - libgsm_ms
  - libmp3lame
  - libspeex
  - libvo_aacenc
  - libvo_amrwbenc
  - libvorbis
...
---
formats:
  - a64
  - ac3
  - adts
  - adx
  - aiff
  - amr
  - asf
  - ***
  - asf_stream
  - au
  - avi
  - avm2
  - cavsvideo
  - crc
  - daud
  - dirac
  - dnxhd
  - dts
  - dv
  - eac3
  - ffm
  - ffmetadata
  - filmstrip
  - flac
  - flv
  - framecrc
  - framemd5
  - g722
  - gif
  - gxf
  - h261
  - h263
  - h264
  - image2
  - image2pipe
  - ipod
  - ivf
  - latm
  - m4v
  - md5
  - matroska
  - matroska
  - mjpeg
  - mlp
  - mmf
  - mov
  - mp2
  - mp3
  - mp4
  - mpeg
  - vcd
  - mpeg1video
  - dvd
  - svcd
  - mpeg2video
  - vob
  - mpegts
  - mpjpeg
  - mxf
  - mxf_d10
  - null
  - nut
  - ogg
  - oma
  - alaw
  - mulaw
  - f64be
  - f64le
  - f32be
  - f32le
  - s32be
  - s32le
  - s24be
  - s24le
  - s16be
  - s16le
  - s8
  - u32be
  - u32le
  - u24be
  - u24le
  - u16be
  - u16le
  - u8
  - psp
  - rawvideo
  - rm
  - RoQ
  - rso
  - rtp
  - rtsp
  - sap
  - segment
  - smjpeg
  - sox
  - spdif
  - srt
  - swf
  - 3g2
  - 3gp
  - truehd
  - rcv
  - voc
  - wav
  - webm
  - yuv4mpegpipe
  - alsa
  - oss
...
state saved

```

Kirk Schnable

---

### Post by ibnub on 2013-01-15
Many thanks for posting this solution.  It was painful looking for the right solution to this problem.

---

### Post by sideburnie on 2013-10-03
^ This guy. 

Thank you for a quick, detailed, working solution, good sir.

---

### Post by theller on 2013-12-22
Thanks, this worked for me. Fixing my friends laptop with Ubuntu 13.04 and OpenShot just would not open. It does now.

---

### Post by barbarapao2003 on 2014-10-24
Aunque sé, que algunos ya lo han solucionado.. Ofrezco una alternativa rápida y muy sencilla.. Solo tenéis que entrar en los archivos ocultos de vuestro home => Ctrl +H buscar openshot y renombrarlo, por ejemplo así: openshot1 luego id a la terminal y escribid openshot y listo! os abrirá openshot, luego ya podréis abrirla de manera normal o por la terminal.. Saludos ;)

---

### Post by Sasha_in_Sydney on 2014-11-03
For starters, I simply renamed .openshot in my personal folder. Nothing else was required.

---

### Post by adokuyucu on 2015-06-10
I experienced this problem in 15.04 after a short while I installed OpenShot. I resolved this by removing the contents of " ***~/.openshot/ *** " .I believe this was caused by me deleting the default project file which seems to be a bug

---

