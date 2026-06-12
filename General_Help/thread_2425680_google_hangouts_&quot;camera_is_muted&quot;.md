---
title: "google hangouts &quot;camera is muted&quot;"
date: 2019-08-28
forum: General Help
---

### Post by jgw on 2019-08-28
I have been trying to make google hangouts work.  It was working fine a couple of months ago.  Now, however, I am told "camera is muted".  I have tried everything I could think of.  I have tried to make it run not only on firefox but google chrome.  Same problem.  I have been over the settings until blue in the face to no avail.  The camera itself works fine in guvcview.  Here is the basic info on the camera:
```

greg@gregdown:~$ v4l2-ctl --list-devices
UVC Camera (046d:0809) (usb-0000:00:12.0-3.2):
	/dev/video0
	/dev/video1
greg@gregdown:~$ lsusb -s 003:005
Bus 003 Device 005: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
greg@gregdown:~$ ls -ltrh /dev/video*
crw-rw----+ 1 root video 81, 1 Aug 28 09:16 /dev/video1
crw-rw----+ 1 root video 81, 0 Aug 28 09:16 /dev/video0

```

I was hoping somebody could help me here.  I have been to the hangouts forum but there was no help there.  Here is all the information I could find on the camera:

```
greg@gregdown:~$ v4l2-ctl --all
Driver Info (not using libv4l2):
	Driver name   : uvcvideo
	Card type     : UVC Camera (046d:0809)
	Bus info      : usb-0000:00:12.0-3.2
	Driver version: 5.0.18
	Capabilities  : 0x84A00001
		Video Capture
		Metadata Capture
		Streaming
		Extended Pix Format
		Device Capabilities
	Device Caps   : 0x04200001
		Video Capture
		Streaming
		Extended Pix Format
Priority: 2
Video input : 0 (Camera 1: ok)
Format Video Capture:
	Width/Height      : 160/120
	Pixel Format      : 'MJPG'
	Field             : None
	Bytes per Line    : 0
	Size Image        : 12800
	Colorspace        : sRGB
	Transfer Function : Default (maps to sRGB)
	YCbCr/HSV Encoding: Default (maps to ITU-R 601)
	Quantization      : Default (maps to Full Range)
	Flags             : 
Crop Capability Video Capture:
	Bounds      : Left 0, Top 0, Width 160, Height 120
	Default     : Left 0, Top 0, Width 160, Height 120
	Pixel Aspect: 1/1
Selection: crop_default, Left 0, Top 0, Width 160, Height 120
Selection: crop_bounds, Left 0, Top 0, Width 160, Height 120
Streaming Parameters Video Capture:
	Capabilities     : timeperframe
	Frames per second: 30.000 (30/1)
	Read buffers     : 0
                     brightness 0x00980900 (int)    : min=0 max=255 step=1 default=128 value=128
                       contrast 0x00980901 (int)    : min=0 max=255 step=1 default=32 value=32
                     saturation 0x00980902 (int)    : min=0 max=255 step=1 default=28 value=28
 white_balance_temperature_auto 0x0098090c (bool)   : default=1 value=1
                           gain 0x00980913 (int)    : min=0 max=255 step=1 default=0 value=178
           power_line_frequency 0x00980918 (menu)   : min=0 max=2 default=2 value=2
      white_balance_temperature 0x0098091a (int)    : min=0 max=10000 step=10 default=4000 value=5740 flags=inactive
                      sharpness 0x0098091b (int)    : min=0 max=255 step=1 default=191 value=191
         backlight_compensation 0x0098091c (int)    : min=0 max=1 step=1 default=1 value=1
                  exposure_auto 0x009a0901 (menu)   : min=0 max=3 default=3 value=3
              exposure_absolute 0x009a0902 (int)    : min=1 max=10000 step=1 default=166 value=305 flags=inactive
         exposure_auto_priority 0x009a0903 (bool)   : default=0 value=1
                   pan_absolute 0x009a0908 (int)    : min=-36000 max=36000 step=3600 default=0 value=0
                  tilt_absolute 0x009a0909 (int)    : min=-36000 max=36000 step=3600 default=0 value=0
                          focus 0x009a090a (int)    : min=0 max=255 step=1 default=0 value=0
                      led1_mode 0x0a046d05 (menu)   : min=0 max=3 default=3 value=3
                 led1_frequency 0x0a046d06 (int)    : min=0 max=255 step=1 default=0 value=0
       disable_video_processing 0x0a046d71 (bool)   : default=0 value=0
             raw_bits_per_pixel 0x0a046d72 (int)    : min=0 max=1 step=1 default=0 value=0
greg@gregdown:~$ v4l2-ctl --list-devices
UVC Camera (046d:0809) (usb-0000:00:12.0-3.2):
	/dev/video0
	/dev/video1

greg@gregdown:~$ lsusb -s 003:005
Bus 003 Device 005: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
greg@gregdown:~$ ls -ltrh /dev/video*
crw-rw----+ 1 root video 81, 1 Aug 28 09:16 /dev/video1
crw-rw----+ 1 root video 81, 0 Aug 28 09:16 /dev/video0

greg@gregdown:~$ ffmpeg -f v4l2 -list_formats all -i /dev/video0
ffmpeg version 3.4.6-0ubuntu0.18.04.1 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  WARNING: library configuration mismatch
  avcodec     configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
[video4linux2,v4l2 @ 0x557526b7d8c0] Raw       :     yuyv422 :           YUYV 4:2:2 : 160x120 176x144
[video4linux2,v4l2 @ 0x557526b7d8c0] Compressed:       mjpeg :          Motion-JPEG : 640x480 160x120 176x144 320x240 352x288 640x360 640x400 768x480 800x456 800x504 800x600
/dev/video0: Immediate exit requested
greg@gregdown:~$ ffmpeg -f v4l2 -list_formats all -i /dev/video1
ffmpeg version 3.4.6-0ubuntu0.18.04.1 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  WARNING: library configuration mismatch
  avcodec     configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
[video4linux2,v4l2 @ 0x559cf7e508c0] ioctl(VIDIOC_G_INPUT): Inappropriate ioctl for device
/dev/video1: Inappropriate ioctl for device
greg@gregdown:~$ 

```

---

