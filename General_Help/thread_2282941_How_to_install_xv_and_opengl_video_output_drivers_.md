---
title: "How to install xv and opengl video output drivers in Ubuntu 14.04?"
date: 2015-06-18
forum: General Help
---

### Post by Daniyal_Javani on 2015-06-18
Could you please help me to install xv and opengl video output drivers? I have just a intel graphic hd 3000. And this is mplayer output.
```
$ mplayer -vo help
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team
Available video output drivers:
    x11 X11 ( XImage/Shm )
    xover   General X11 driver for overlay capable video output drivers
    fbdev   Framebuffer Device
    fbdev2  Framebuffer Device
    v4l2    V4L2 MPEG Video Decoder Output
    xvidix  X11 (VIDIX)
    cvidix  console VIDIX
    null    Null video output
    mpegpes MPEG-PES to DVB card
    yuv4mpeg    yuv4mpeg output for mjpegtools
    png PNG file
    tga Targa output
    pnm PPM/PGM/PGMYUV file
    md5sum  md5sum of each frame
```
There is nothing in "Software & Updates" -> "Additional drivers" !

  Is this problem related to not installed Intel graphic card?

---

### Post by Daniyal_Javani on 2015-06-18
Excuse me, why I have not xv and opengl video output drivers? I check proprietary drivers for devices in Ubuntu software and do apt-get update with US IP (proxychains apt-get update). No idea?

---

### Post by grahammechanical on 2015-06-18
It is my understanding, and I maybe wrong, that Intel video drivers come as kernel modules and that is why Additional Drivers does not offer later versions of Intel video drivers.

If you go to this link and expand the section 2nd Generation Intel Core Processors - with Intel HD Graphics 3000/2000 and look at the chart you will see that Intel HD Graphics 3000 supports OpenGL 3.1.

There is also the section Intel Pentium Processors with Intel HD Graphics which shows that those systems with 3000/G3000 series Graphics have support for OpenGL 4.0.

I suspect that the Intel video drivers that are installed by default when we have an Intel graphic adapter and that come as part of X.Org the video server are capable of outputting to OpenGL specifications. OpenGL is a specification just as DirectX from Microsoft is a specification. I expect Windows video drivers to support DirectX but not OpenGL and I expect Intel Linux drivers to support OpenGL and not DirectX.

Regards.

---

### Post by Daniyal_Javani on 2015-06-19
> **grahammechanical said:**
> It is my understanding, and I maybe wrong, that Intel video drivers come as kernel modules and that is why Additional Drivers does not offer later versions of Intel video drivers.

If you go to this link and expand the section 2nd Generation Intel Core Processors - with Intel HD Graphics 3000/2000 and look at the chart you will see that Intel HD Graphics 3000 supports OpenGL 3.1.

There is also the section Intel Pentium Processors with Intel HD Graphics which shows that those systems with 3000/G3000 series Graphics have support for OpenGL 4.0.

I suspect that the Intel video drivers that are installed by default when we have an Intel graphic adapter and that come as part of X.Org the video server are capable of outputting to OpenGL specifications. OpenGL is a specification just as DirectX from Microsoft is a specification. I expect Windows video drivers to support DirectX but not OpenGL and I expect Intel Linux drivers to support OpenGL and not DirectX.

Regards.

I try to install xv and opengl because have lag in playing 1080p videos, so is there any way to solve this issue?

---

### Post by blm-ubunet on 2015-06-19
What's the output of this ?
```
glxinfo | grep OpenGL
```

---

### Post by Daniyal_Javani on 2015-06-20
> **blm-ubunet said:**
> What's the output of this ?
```
glxinfo | grep OpenGL
```

```
$ glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL core profile version string: 3.1 (Core Profile) Mesa 10.1.3
OpenGL core profile shading language version string: 1.40
OpenGL core profile context flags: (none)
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:


```

Thanks for your attention,
If I have opengl, why I have no image with this command?
```
$ mplayer /media/vahid/Data/01\ From\ Pole\ to\ Pole\ 2006_HD.1080p.mp4  -vo opengl
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team

Playing /media/vahid/Data/01 From Pole to Pole 2006_HD.1080p.mp4.
libavformat version 54.6.100 (internal)
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang eng
[lavf] stream 2: audio (aac), -aid 1, -alang eng
VIDEO:  [H264]  1920x1080  24bpp  23.976 fps  2103.4 kbps (256.8 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 1
 compatible_brands: isomavc1
 creation_time: 2013-10-09 20:30:13
Load subtitles in /media/vahid/Data/
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.23.100 (internal)
AUDIO: 48000 Hz, 6 ch, s16le, 379.3 kbit/8.23% (ratio: 47409->576000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
DVB card number must be between 1 and 4
AO: [null] 48000Hz 2ch floatle (4 bytes per sample)
Video: no video
Starting playback...
A:   4.9 (04.9) of 3200.7 (53:20.6)  1.1%                                       


MPlayer interrupted by signal 2 in module: play_audio
A:   4.9 (04.9) of 3200.7 (53:20.6)  1.1%                                       

Exiting... (Quit)
```

Output of xv
```
$ mplayer /media/vahid/Data/01\ From\ Pole\ to\ Pole\ 2006_HD.1080p.mp4  -vo xv
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team

Playing /media/vahid/Data/01 From Pole to Pole 2006_HD.1080p.mp4.
libavformat version 54.6.100 (internal)
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang eng
[lavf] stream 2: audio (aac), -aid 1, -alang eng
VIDEO:  [H264]  1920x1080  24bpp  23.976 fps  2103.4 kbps (256.8 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 1
 compatible_brands: isomavc1
 creation_time: 2013-10-09 20:30:13
Load subtitles in /media/vahid/Data/
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.23.100 (internal)
AUDIO: 48000 Hz, 6 ch, s16le, 379.3 kbit/8.23% (ratio: 47409->576000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
DVB card number must be between 1 and 4
AO: [null] 48000Hz 2ch floatle (4 bytes per sample)
Video: no video
Starting playback...
A:   3.9 (03.9) of 3200.7 (53:20.6)  0.9%                                       


MPlayer interrupted by signal 2 in module: play_audio
A:   3.9 (03.9) of 3200.7 (53:20.6)  0.9%                                       

Exiting... (Quit)
```

---

### Post by blm-ubunet on 2015-06-20
Don't know why xv rendering is broken on your system.. could be clues in /var/log/Xorg.0.log..

To use openGL rendering in mplayer the cmd is:
```
-vo gl
or
-vo gl2
```

You could try to use GPU decoding as well by installing the vdpau interface for your VAAPI capable h/w.
Mplayer (this version with SMPlayer ??) does not seem to support VAAPI directly.

```
sudo apt-get install i965-va-driver vainfo
sudo apt-get install vdpau-va-driver vdpauinfo
```

then check with
```
vainfo
vdpauinfo
mplayer -vc ffh264vdpau -vo vdpau <your h264 mpeg4-layer10 file>
```
Note you have to use vdpau rendering if you use vdpau decoding.
The stock packages in 14.04 may or may not be satisfactory. May need to use xorg-edgers ppa.

---

### Post by Daniyal_Javani on 2015-06-21
> **blm-ubunet said:**
> Don't know why xv rendering is broken on your system.. could be clues in /var/log/Xorg.0.log..  To use openGL rendering in mplayer the cmd is: ```
-vo gl or -vo gl2
```  You could try to use GPU decoding as well by installing the vdpau interface for your VAAPI capable h/w. Mplayer (this version with SMPlayer ??) does not seem to support VAAPI directly.  ```
sudo apt-get install i965-va-driver vainfo sudo apt-get install vdpau-va-driver vdpauinfo
```  then check with ```
vainfo vdpauinfo mplayer -vc ffh264vdpau -vo vdpau 
``` Note you have to use vdpau rendering if you use vdpau decoding. The stock packages in 14.04 may or may not be satisfactory. May need to use xorg-edgers ppa.  Thanks but also have no video with gl or gl2 ```
$ mplayer  /media/vahid/Data/01\ From\ Pole\ to\ Pole\ 2006_HD.1080p.mp4  -vo gl2 MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team  Playing /media/vahid/Data/01 From Pole to Pole 2006_HD.1080p.mp4. libavformat version 54.6.100 (internal) libavformat file format detected. [lavf] stream 0: video (h264), -vid 0 [lavf] stream 1: audio (aac), -aid 0, -alang eng [lavf] stream 2: audio (aac), -aid 1, -alang eng VIDEO:  [H264]  1920x1080  24bpp  23.976 fps  2103.4 kbps (256.8 kbyte/s) Clip info:  major_brand: isom  minor_version: 1  compatible_brands: isomavc1  creation_time: 2013-10-09 20:30:13 Load subtitles in /media/vahid/Data/ Error opening/initializing the selected video_out (-vo) device. ========================================================================== Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders libavcodec version 54.23.100 (internal) AUDIO: 48000 Hz, 6 ch, s16le, 379.3 kbit/8.23% (ratio: 47409->576000) Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio)) ========================================================================== [AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory DVB card number must be between 1 and 4 AO: [null] 48000Hz 2ch floatle (4 bytes per sample) Video: no video Starting playback... A:   3.0 (02.9) of 3200.7 (53:20.6)  0.9%                                          MPlayer interrupted by signal 2 in module: play_audio A:   3.0 (02.9) of 3200.7 (53:20.6)  0.9%                                         Exiting... (Quit)
``` ```
$ mplayer  /media/vahid/Data/01\ From\ Pole\ to\ Pole\ 2006_HD.1080p.mp4  -vo gl MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team  Playing /media/vahid/Data/01 From Pole to Pole 2006_HD.1080p.mp4. libavformat version 54.6.100 (internal) libavformat file format detected. [lavf] stream 0: video (h264), -vid 0 [lavf] stream 1: audio (aac), -aid 0, -alang eng [lavf] stream 2: audio (aac), -aid 1, -alang eng VIDEO:  [H264]  1920x1080  24bpp  23.976 fps  2103.4 kbps (256.8 kbyte/s) Clip info:  major_brand: isom  minor_version: 1  compatible_brands: isomavc1  creation_time: 2013-10-09 20:30:13 Load subtitles in /media/vahid/Data/ Error opening/initializing the selected video_out (-vo) device. ========================================================================== Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders libavcodec version 54.23.100 (internal) AUDIO: 48000 Hz, 6 ch, s16le, 379.3 kbit/8.23% (ratio: 47409->576000) Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio)) ========================================================================== [AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory DVB card number must be between 1 and 4 AO: [null] 48000Hz 2ch floatle (4 bytes per sample) Video: no video Starting playback... A:   2.7 (02.6) of 3200.7 (53:20.6)  1.2%                                          MPlayer interrupted by signal 2 in module: play_audio A:   2.7 (02.6) of 3200.7 (53:20.6)  1.2%                                         Exiting... (Quit)  
```  OMG! I try installing vdpau but fall in this bug [https://bugs.launchpad.net/ubuntu/+source/libvdpau/+bug/1300215](https://bugs.launchpad.net/ubuntu/+source/libvdpau/+bug/1300215) ```
$ vdpauinfo display: :0 screen: 0 Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory Error creating VDPAU device: 1
``` So I try  ```
cd /usr/lib/x86_64-linux-gnu/vdpau/ sudo ln -s libvdpau_va_gl.so.1 libvdpau_i965.so.1
``` but still have no video! ```
$ mplayer -vc ffh264vdpau -vo vdpau /media/vahid/Data/01\ From\ Pole\ to\ Pole\ 2006_HD.1080p.mp4  MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team  Playing /media/vahid/Data/01 From Pole to Pole 2006_HD.1080p.mp4. libavformat version 54.6.100 (internal) libavformat file format detected. [lavf] stream 0: video (h264), -vid 0 [lavf] stream 1: audio (aac), -aid 0, -alang eng [lavf] stream 2: audio (aac), -aid 1, -alang eng VIDEO:  [H264]  1920x1080  24bpp  23.976 fps  2103.4 kbps (256.8 kbyte/s) Clip info:  major_brand: isom  minor_version: 1  compatible_brands: isomavc1  creation_time: 2013-10-09 20:30:13 Load subtitles in /media/vahid/Data/ Error opening/initializing the selected video_out (-vo) device. ========================================================================== Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders libavcodec version 54.23.100 (internal) AUDIO: 48000 Hz, 6 ch, s16le, 379.3 kbit/8.23% (ratio: 47409->576000) Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio)) ========================================================================== [AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory DVB card number must be between 1 and 4 AO: [null] 48000Hz 2ch floatle (4 bytes per sample) Video: no video Starting playback... A:   2.5 (02.5) of 3200.7 (53:20.6)  1.3%                                          MPlayer interrupted by signal 2 in module: play_audio A:   2.6 (02.5) of 3200.7 (53:20.6)  1.3%                                         Exiting... (Quit)
``` Do you have any idea to fix this?

---

### Post by blm-ubunet on 2015-06-21
I would forget about trying to use VDPAU indirectly..
If your video requires de-interlacing or other post processing then the VAAPI-->VDPAU is not going to work well.

Your sample video is relatively low bitrate so should be playable on one CPU core. 

FWIU For VAAPI to work you have to have functioning openGL for rendering.
VDPAU will not work unless VAAPI is working.
VAAPI will not work unless openGL rendering is working.
So back to the actual problem.. why is xv & opengl broken?

Post your /var/log/Xorg.0.log file as attachment.

Try running & post any errors for these (2) commands:
glxgears
vainfo

And please stop quoting the entire post & pasting std-out that is all one long line..

---

### Post by Daniyal_Javani on 2015-06-21
> **blm-ubunet said:**
> 
Post your /var/log/Xorg.0.log file as attachment.

The file attached.

> **blm-ubunet said:**
> 
Try running & post any errors for these (2) commands:
glxgears
vainfo

```
$ glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
305 frames in 5.0 seconds = 60.891 FPS
300 frames in 5.0 seconds = 59.879 FPS
300 frames in 5.0 seconds = 59.880 FPS
300 frames in 5.0 seconds = 59.880 FPS
300 frames in 5.0 seconds = 59.877 FPS
300 frames in 5.0 seconds = 59.882 FPS
300 frames in 5.0 seconds = 59.880 FPS
300 frames in 5.0 seconds = 59.876 FPS
300 frames in 5.0 seconds = 59.879 FPS
300 frames in 5.0 seconds = 59.879 FPS
300 frames in 5.0 seconds = 59.878 FPS
300 frames in 5.0 seconds = 59.879 FPS
300 frames in 5.0 seconds = 59.880 FPS
```
```
$ vainfo
libva info: VA-API version 0.35.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_35
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.35 (libva 1.3.0)
vainfo: Driver version: Intel i965 driver - 1.3.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSlice
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSlice
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSlice
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc
```

> **blm-ubunet said:**
> 
And please stop quoting the entire post & pasting std-out that is all one long line..
Sorry, it won't happen again.

Thanks...

---

### Post by blm-ubunet on 2015-06-22
Well glxgears (basic opengl) is okay, vainfo is okay & your X server log is okay/fine..

Try this cmd as well:
```
xvinfo | grep -i video
```

I think using mplayer as a debugging tool is flawed & should give up on mplayer & find a maintained media player vlc or mpv.
VLC (later versions) support VAAPI.

You do realize that you are disabling intel pstate cpu/gpu frequency/power control in grub kernel load cmd options ?

---

### Post by Daniyal_Javani on 2015-06-22
> **blm-ubunet said:**
> 
Try this cmd as well:
```
xvinfo | grep -i video
```

```

$ xvinfo | grep -i video
X-Video Extension version 2.2
  Adaptor #0: "Intel(R) Textured Video"
  Adaptor #1: "Intel(R) Video Sprite"
```

> **blm-ubunet said:**
> 
You do realize that you are disabling intel pstate cpu/gpu frequency/power control in grub kernel load cmd options ?
Yes I do it because want to change frequency wtih indicator-cpufreq.

---

### Post by Daniyal_Javani on 2015-06-22
So if you were me, what would you do?

---

### Post by Daniyal_Javani on 2015-06-24
How about installing xbmcbuntu on virtualbox?
Is it a good idea to solve this issue?

---

### Post by Daniyal_Javani on 2015-08-28
My problem solved in this topic
[http://ubuntuforums.org/showthread.php?t=2292408](http://ubuntuforums.org/showthread.php?t=2292408)

---

