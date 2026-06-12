---
title: "Kdenlive no audio"
date: 2014-11-01
forum: General Help
---

### Post by Chelidze on 2014-11-01
After I render a file I only get the video in the file, I do not think it exports audio no matter what format I select 

here is the terminal output 

```
kdenlivekdenlive(14188) MainWindow::parseProfiles: RESULTING MLT PATH:  "/usr/share/mlt/profiles/"
kdenlive(14188) RecMonitor::RecMonitor: /////// BUILDING MONITOR, ID:  58720373
---
formats:
  - a64
  - ac3
  - adts
  - adx
  - aiff
  - amr
  - asf
  - ass
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
  - f4v
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
  - hds
  - hevc
  - hls
  - ilbc
  - image2
  - image2pipe
  - ipod
  - ismv
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
  - roq
  - rso
  - rtp
  - rtsp
  - sap
  - segment
  - smjpeg
  - smoothstreaming
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
  - wv
  - yuv4mpegpipe
  - alsa
  - oss
...
---
audio_codecs:
  - comfortnoise
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
  - pcm_alaw
  - pcm_f32be
  - pcm_f32le
  - pcm_f64be
  - pcm_f64le
  - pcm_mulaw
  - pcm_s8
  - pcm_s16be
  - pcm_s16le
  - pcm_s24be
  - pcm_s24daud
  - pcm_s24le
  - pcm_s32be
  - pcm_s32le
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
  - libspeex
  - libvorbis
...
---
video_codecs:
  - a64multi
  - a64multi5
  - alias_pix
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
  - prores
  - qtrle
  - rawvideo
  - roqvideo
  - rv10
  - rv20
  - sgi
  - sunrast
  - svq1
  - targa
  - tiff
  - utvideo
  - v210
  - v410
  - wmv1
  - wmv2
  - xbm
  - xwd
  - zlib
  - zmbv
  - libopenjpeg
  - libschroedinger
  - libtheora
  - libvpx
  - libvpx-vp9
  - libx264
  - libxvid
...
kdenlive(14188) Wizard::installExtraMimes: EXTS:  ("*.mpeg", "*.mpg", "*.mp2", "*.mpe", "*.vob", "[0-9][0-9][0-9].vdr", "*.ts", "*.m2v")
kdenlive(14188) Wizard::installExtraMimes: INSTALLING NEW MIME TO:  "/home/levan/.local/share/mime/packages/video-mpeg.xml"
kdenlive(14188) MainWindow::loadPlugins: Parsing plugin folder:  "/usr/lib/kde4/"
kdenlive(14188) MainWindow::loadPlugins: Found plugin:  "libkdenlive_sampleplugin.so"
kdenlive(14188) MainWindow::addToMenu: // ADD to MENU ("Countdown", "Noise")
kdenlive(14188) KdenliveDoc::setProfilePath: Kdenlive document, init timecode from path:  "atsc_1080p_30" ,   30
kdenlive(14188) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  4 , DURATION:  0
kdenlive(14188) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  3 , DURATION:  0
kdenlive(14188) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  2 , DURATION:  0
kdenlive(14188) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  1 , DURATION:  0
kdenlive(14188) TrackView::slotAddProjectTrack: *************  ADD DOC TRACK  0 , DURATION:  0
kdenlive(14188) TrackView::parseDocument: ///////////  TOTAL PROJECT DURATION:  1
kdenlive(14188) Render::resetProfile: reset to same profile, nothing to do
kdenlive(14188) Render::checkMaxThreads: // MLT threads updated to:  10
kdenlive(14188) Render::setSceneList: // NEW SCENE LIST DURATION SET TO:  2
kdenlive(14188) MainWindow::connectDocument: ///////////////////   CONNECTING DOC TO PROJECT VIEW ////////////////
Object::connect: No such signal org::freedesktop::UPower::DeviceAdded(QDBusObjectPath)
Object::connect: No such signal org::freedesktop::UPower::DeviceRemoved(QDBusObjectPath)
kdenlive(14188) ClipManager::slotAddClipList: Adding clip:  "/media/levan/BEEA60D8EA608E89/**** all os/Logo 1920 X 1080.mp4 - YouTube [720p].mp4"
kdenlive(14188) AddClipCommand::redo: ----  redoing action
kdenlive(14188) ClipManager::slotGetAudioThumbs: reading audio thumbs from file
"Input and output data arrays overlap. 44100,1470,48000" 
"Input and output data arrays overlap. 44100,1470,48000" 
kdenlive(14188) RenderWidget::parseFile: // Parsing file:  "/usr/share/kde4/apps/kdenlive/export/profiles.xml"
kdenlive(14188) RenderWidget::parseFile: ------------------------------
kdenlive(14188) RenderWidget::startRendering: // Normal process
//STARTING RENDERING:  true , false , "/usr/bin/melt" , "atsc_1080p_30" , "avformat" , "-" , "/tmp/kde-levan/kdenliveZ14188.mlt" , "/home/levan/kdenlive/untitled.mp4" , () , ("properties=MPEG-4-ASP", "ab=128k", "vb=2000k", "aspect=@16/9", "an=1", "threads=1", "real_time=-1") , -1 , -1 
Started render process:  "/usr/bin/melt"   "/tmp/kde-levan/kdenliveZ14188.mlt -profile atsc_1080p_30 -consumer avformat:/home/levan/kdenlive/untitled.mp4 progress=1 properties=MPEG-4-ASP ab=128k vb=2000k aspect=@16/9 an=1 threads=1 real_time=-1" 
Rendering of  "/home/levan/kdenlive/untitled.mp4"  finished 
kdenlive(14188)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kdenlive(14188) KdenliveDoc::~KdenliveDoc: // DEL CLP MAN
kdenlive(14188) KdenliveDoc::~KdenliveDoc: // DEL CLP MAN done
```

Is there a way to fix this ?? Running 14.10

---

### Post by Bartje on 2014-11-17
Hi, 

I had the same problem, the only solution I found was upgrading Kdenlive with the sunab ppa : [https://launchpad.net/~sunab/+archive/ubuntu/kdenlive-release]("https://launchpad.net/~sunab/+archive/ubuntu/kdenlive-release")

I hope this helps, it worked for me, maybe for you too.

grtz,
Bart

---

### Post by eduardomo on 2015-01-23
> **Bartje said:**
> Hi, 

I had the same problem, the only solution I found was upgrading Kdenlive with the sunab ppa : [https://launchpad.net/~sunab/+archive/ubuntu/kdenlive-release](https://launchpad.net/~sunab/+archive/ubuntu/kdenlive-release)

I hope this helps, it worked for me, maybe for you too.

grtz,
Bart

For me too :) 
Ubuntu 14.10 , GNOME fallback.

Many thanks.

---

### Post by jmachynski on 2015-02-18
> **Bartje said:**
> Hi, 

I had the same problem, the only solution I found was upgrading Kdenlive with the sunab ppa : [https://launchpad.net/~sunab/+archive/ubuntu/kdenlive-release](https://launchpad.net/~sunab/+archive/ubuntu/kdenlive-release)

I hope this helps, it worked for me, maybe for you too.

grtz,
Bart

It works for me too.

---

