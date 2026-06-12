---
title: "Openshot quit work. Running Gnome with Ubuntu 17.10.1"
date: 2018-02-25
forum: General Help
---

### Post by irv on 2018-02-25
If I try running openshot video editor from a command line I get this error, I tried the fix but it did not work. I also tried uninstalling and reinstalling and that didn't help either.
 Here is the error.
```
openshot
Added /usr/share/openshot to system path

------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.4.3)
--------------------------------

Detecting formats, codecs, and filters...
---
video_codecs:
  - a64multi
  - a64multi5
  - alias_pix
  - amv
  - apng
  - asv1
  - asv2
  - avrp
  - avui
  - ayuv
  - bmp
  - cinepak
  - cljr
  - dnxhd
  - dpx
  - dvvideo
  - ffv1
  - ffvhuff
  - flashsv
  - flashsv2
  - flv
  - gif
  - h261
  - h263
  - h263p
  - hap
  - huffyuv
  - jpeg2000
  - jpegls
  - ljpeg
  - mjpeg
  - mpeg1video
  - mpeg2video
  - mpeg4
  - msmpeg4v2
  - msmpeg4
  - msvideo1
  - pam
  - pbm
  - pcx
  - pgm
  - pgmyuv
  - png
  - ppm
  - prores
  - prores_aw
  - prores_ks
  - qtrle
  - r10k
  - r210
  - rawvideo
  - roqvideo
  - rv10
  - rv20
  - sgi
  - snow
  - sunrast
  - svq1
  - targa
  - tiff
  - utvideo
  - v210
  - v308
  - v408
  - v410
  - vc2
  - wrapped_avframe
  - wmv1
  - wmv2
  - xbm
  - xface
  - xwd
  - y41p
  - yuv4
  - zlib
  - zmbv
  - libopenjpeg
  - libtheora
  - libvpx
  - libvpx-vp9
  - libwebp_anim
  - libwebp
  - libx264
  - libx264rgb
  - libx265
  - libxvid
  - h264_nvenc
  - h264_omx
  - h264_vaapi
  - nvenc
  - nvenc_h264
  - nvenc_hevc
  - hevc_nvenc
  - hevc_vaapi
  - mjpeg_vaapi
  - mpeg2_vaapi
  - vp8_vaapi
...
---
audio_codecs:
  - comfortnoise
  - s302m
  - aac
  - ac3
  - ac3_fixed
  - alac
  - dca
  - eac3
  - flac
  - g723_1
  - mlp
  - mp2
  - mp2fixed
  - nellymoser
  - opus
  - real_144
  - sonic
  - sonicls
  - truehd
  - tta
  - vorbis
  - wavpack
  - wmav1
  - wmav2
  - pcm_alaw
  - pcm_f32be
  - pcm_f32le
  - pcm_f64be
  - pcm_f64le
  - pcm_mulaw
  - pcm_s8
  - pcm_s8_planar
  - pcm_s16be
  - pcm_s16be_planar
  - pcm_s16le
  - pcm_s16le_planar
  - pcm_s24be
  - pcm_s24daud
  - pcm_s24le
  - pcm_s24le_planar
  - pcm_s32be
  - pcm_s32le
  - pcm_s32le_planar
  - pcm_s64be
  - pcm_s64le
  - pcm_u8
  - pcm_u16be
  - pcm_u16le
  - pcm_u24be
  - pcm_u24le
  - pcm_u32be
  - pcm_u32le
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
  - libopus
  - libshine
  - libspeex
  - libtwolame
  - libvorbis
  - libwavpack
...
---
formats:
  - a64
  - ac3
  - adts
  - adx
  - aiff
  - amr
  - apng
  - asf
  - ass
  - ast
  - asf_stream
  - au
  - avi
  - avm2
  - bit
  - caf
  - cavsvideo
  - crc
  - dash
  - data
  - daud
  - dirac
  - dnxhd
  - dts
  - dv
  - eac3
  - f4v
  - ffm
  - ffmetadata
  - fifo
  - filmstrip
  - flac
  - flv
  - framecrc
  - framehash
  - framemd5
  - g722
  - g723_1
  - gif
  - gsm
  - gxf
  - h261
  - h263
  - h264
  - hash
  - hds
  - hevc
  - hls
  - ico
  - ilbc
  - image2
  - image2pipe
  - ipod
  - ircam
  - ismv
  - ivf
  - jacosub
  - latm
  - lrc
  - m4v
  - md5
  - matroska
  - matroska
  - microdvd
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
  - mxf_opatom
  - null
  - nut
  - oga
  - ogg
  - ogv
  - oma
  - opus
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
  - roq
  - rso
  - rtp
  - rtp_mpegts
  - rtsp
  - sap
  - scc
  - segment
  - stream_segment,ssegment
  - singlejpeg
  - smjpeg
  - smoothstreaming
  - sox
  - spx
  - spdif
  - srt
  - swf
  - tee
  - 3g2
  - 3gp
  - mkvtimestamp_v2
  - truehd
  - tta
  - uncodedframecrc
  - vc1
  - vc1test
  - voc
  - w64
  - wav
  - webm
  - webm_dash_manifest
  - webm_chunk
  - webp
  - webvtt
  - wtv
  - wv
  - yuv4mpegpipe
  - chromaprint
  - alsa
  - caca
  - fbdev
  - opengl
  - oss
  - pulse
  - sdl,sdl2
  - sndio
  - v4l2
  - xv
...

------------------------- ERROR 2 ------------------------------
Failed to import 'from openshot.openshot import main'
Error Message: 'NoneType' object has no attribute 'set_cursor'
----------------------------------------------------------------

OpenShot has failed to import some of the Python files or libraries 
required for our application to run.  Here are some trouble shooting
tips:

Tip 1) Check if MLT can be successfully imported in Python.  Run the 
 following commands, and see if any errors are displayed.  If you get 
 an error, you need to investigate the correct way to install MLT.
 NOTE:  Do not type the $ or >> characters in the examples below.

       $ python
       >> import mlt
       >> mlt.Factory().init()

Tip 2) If MLT is working from the first example, then the next tip is 
 to look at the above error messages very closely, and google for more 
 help.  It's likely the problem is already reported, and maybe there is
 a simple work-around.  Also, you can search for bugs or report a new 
 bug at [https://bugs.launchpad.net/openshot](https://bugs.launchpad.net/openshot).  Good luck!



```

---

### Post by wildmanne39 on 2018-02-25
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by irv on 2018-02-25
I am using the code tag, let me try it again.
```
openshot
Added /usr/share/openshot to system path

------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.4.3)
--------------------------------

Detecting formats, codecs, and filters...
---
video_codecs:
  - a64multi
  - a64multi5
  - alias_pix
  - amv
  - apng
  - asv1
  - asv2
  - avrp
  - avui
  - ayuv
  - bmp
  - cinepak
  - cljr
  - dnxhd
  - dpx
  - dvvideo
  - ffv1
  - ffvhuff
  - flashsv
  - flashsv2
  - flv
  - gif
  - h261
  - h263
  - h263p
  - hap
  - huffyuv
  - jpeg2000
  - jpegls
  - ljpeg
  - mjpeg
  - mpeg1video
  - mpeg2video
  - mpeg4
  - msmpeg4v2
  - msmpeg4
  - msvideo1
  - pam
  - pbm
  - pcx
  - pgm
  - pgmyuv
  - png
  - ppm
  - prores
  - prores_aw
  - prores_ks
  - qtrle
  - r10k
  - r210
  - rawvideo
  - roqvideo
  - rv10
  - rv20
  - sgi
  - snow
  - sunrast
  - svq1
  - targa
  - tiff
  - utvideo
  - v210
  - v308
  - v408
  - v410
  - vc2
  - wrapped_avframe
  - wmv1
  - wmv2
  - xbm
  - xface
  - xwd
  - y41p
  - yuv4
  - zlib
  - zmbv
  - libopenjpeg
  - libtheora
  - libvpx
  - libvpx-vp9
  - libwebp_anim
  - libwebp
  - libx264
  - libx264rgb
  - libx265
  - libxvid
  - h264_nvenc
  - h264_omx
  - h264_vaapi
  - nvenc
  - nvenc_h264
  - nvenc_hevc
  - hevc_nvenc
  - hevc_vaapi
  - mjpeg_vaapi
  - mpeg2_vaapi
  - vp8_vaapi
...
---
audio_codecs:
  - comfortnoise
  - s302m
  - aac
  - ac3
  - ac3_fixed
  - alac
  - dca
  - eac3
  - flac
  - g723_1
  - mlp
  - mp2
  - mp2fixed
  - nellymoser
  - opus
  - real_144
  - sonic
  - sonicls
  - truehd
  - tta
  - vorbis
  - wavpack
  - wmav1
  - wmav2
  - pcm_alaw
  - pcm_f32be
  - pcm_f32le
  - pcm_f64be
  - pcm_f64le
  - pcm_mulaw
  - pcm_s8
  - pcm_s8_planar
  - pcm_s16be
  - pcm_s16be_planar
  - pcm_s16le
  - pcm_s16le_planar
  - pcm_s24be
  - pcm_s24daud
  - pcm_s24le
  - pcm_s24le_planar
  - pcm_s32be
  - pcm_s32le
  - pcm_s32le_planar
  - pcm_s64be
  - pcm_s64le
  - pcm_u8
  - pcm_u16be
  - pcm_u16le
  - pcm_u24be
  - pcm_u24le
  - pcm_u32be
  - pcm_u32le
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
  - libopus
  - libshine
  - libspeex
  - libtwolame
  - libvorbis
  - libwavpack
...
---
formats:
  - a64
  - ac3
  - adts
  - adx
  - aiff
  - amr
  - apng
  - asf
  - ass
  - ast
  - asf_stream
  - au
  - avi
  - avm2
  - bit
  - caf
  - cavsvideo
  - crc
  - dash
  - data
  - daud
  - dirac
  - dnxhd
  - dts
  - dv
  - eac3
  - f4v
  - ffm
  - ffmetadata
  - fifo
  - filmstrip
  - flac
  - flv
  - framecrc
  - framehash
  - framemd5
  - g722
  - g723_1
  - gif
  - gsm
  - gxf
  - h261
  - h263
  - h264
  - hash
  - hds
  - hevc
  - hls
  - ico
  - ilbc
  - image2
  - image2pipe
  - ipod
  - ircam
  - ismv
  - ivf
  - jacosub
  - latm
  - lrc
  - m4v
  - md5
  - matroska
  - matroska
  - microdvd
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
  - mxf_opatom
  - null
  - nut
  - oga
  - ogg
  - ogv
  - oma
  - opus
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
  - roq
  - rso
  - rtp
  - rtp_mpegts
  - rtsp
  - sap
  - scc
  - segment
  - stream_segment,ssegment
  - singlejpeg
  - smjpeg
  - smoothstreaming
  - sox
  - spx
  - spdif
  - srt
  - swf
  - tee
  - 3g2
  - 3gp
  - mkvtimestamp_v2
  - truehd
  - tta
  - uncodedframecrc
  - vc1
  - vc1test
  - voc
  - w64
  - wav
  - webm
  - webm_dash_manifest
  - webm_chunk
  - webp
  - webvtt
  - wtv
  - wv
  - yuv4mpegpipe
  - chromaprint
  - alsa
  - caca
  - fbdev
  - opengl
  - oss
  - pulse
  - sdl,sdl2
  - sndio
  - v4l2
  - xv
...

------------------------- ERROR 2 ------------------------------
Failed to import 'from openshot.openshot import main'
Error Message: 'NoneType' object has no attribute 'set_cursor'
----------------------------------------------------------------

OpenShot has failed to import some of the Python files or libraries 
required for our application to run.  Here are some trouble shooting
tips:

Tip 1) Check if MLT can be successfully imported in Python.  Run the 
 following commands, and see if any errors are displayed.  If you get 
 an error, you need to investigate the correct way to install MLT.
 NOTE:  Do not type the $ or >> characters in the examples below.

       $ python
       >> import mlt
       >> mlt.Factory().init()

Tip 2) If MLT is working from the first example, then the next tip is 
 to look at the above error messages very closely, and google for more 
 help.  It's likely the problem is already reported, and maybe there is
 a simple work-around.  Also, you can search for bugs or report a new 
 bug at https://bugs.launchpad.net/openshot.  Good luck!
```

---

### Post by monkeybrain20122 on 2018-02-25
Seems to be same problem [https://ubuntuforums.org/showthread.php?t=2081636](https://ubuntuforums.org/showthread.php?t=2081636)

---

### Post by irv on 2018-02-25
> **monkeybrain20122 said:**
> Seems to be same problem [https://ubuntuforums.org/showthread.php?t=2081636](https://ubuntuforums.org/showthread.php?t=2081636)

Yes, it was, and the fix worked for me.
Thanks for pointing this out to me.

---

