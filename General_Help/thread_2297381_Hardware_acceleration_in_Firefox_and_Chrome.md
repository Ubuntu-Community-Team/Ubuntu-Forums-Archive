---
title: "Hardware acceleration in Firefox and Chrome"
date: 2015-10-03
forum: General Help
---

### Post by Alfonsu on 2015-10-03
Hello, I try to use my hardware acceleration of both browsers but still no complete success. Here's what I do in both.
Firefox: about:config
layers.acceleration.force-enabled
layers.offmainthreadcomposition.enabled

sudo bash -c "echo export MOZ_USE_OMTC = 1 >> /etc/X11/Xsession.d/90environment"

media.mediasource.enabled;true
media.mediasource.webm.enabled;true
media.fragmented-mp4.exposed;true
media.fragmented-mp4.ffmpeg.enabled;true
media.fragmented-mp4.gmp.enabled;true

When i check [https://www.youtube.com/html5](https://www.youtube.com/html5) everything is active but when i check
about:support:
Driver Version:                               4.5.0 NVIDIA 352.41
Adapter Description:	                     NVIDIA Corporation -- GeForce GTX 480/PCIe/SSE2
Supports Hardware H264 Decoding: false
WebGL Renderer:	                     NVIDIA Corporation -- GeForce GTX 480/PCIe/SSE2
GPU Accelerated Windows:              1/1 OpenGL (OMTC)

Chrome: chrome://flags/
#ignore-gpu-blacklist;true
#enable-gpu-rasterization;true

Chrome: chrome://gpu/
Graphics Feature Status
Canvas: Software only, hardware acceleration unavailable
Flash: Hardware accelerated
Flash Stage3D: Hardware accelerated
Flash Stage3D Baseline profile: Hardware accelerated
Compositing: Hardware accelerated
Multiple Raster Threads: Enabled
Rasterization: Hardware accelerated
Video Decode: Software only, hardware acceleration unavailable
Video Encode: Hardware accelerated
WebGL: Hardware accelerated

---

### Post by Yellow Pasque on 2015-10-03
It may be related to: [http://ubuntuforums.org/showthread.php?t=2296653](http://ubuntuforums.org/showthread.php?t=2296653)

Check vdpauinfo
```
sudo apt-get install vdpauinfo
vdpauinfo
```

---

### Post by Alfonsu on 2015-10-03
alfonsu@alfonsu-P55-UD4:~$ vdpauinfo 
display: :0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  352.41  Fri Aug 21 22:44:24 PDT 2015

Video surface:

name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 

Decoder capabilities:

name                        level macbs width height
----------------------------------------------------
MPEG1                           0  8192  2048  2048
MPEG2_SIMPLE                    3  8192  2048  2048
MPEG2_MAIN                      3  8192  2048  2048
H264_BASELINE                  --- not supported ---
H264_MAIN                      41  8192  2048  2048
H264_HIGH                      41  8192  2048  2048
VC1_SIMPLE                      1  8190  2048  2048
VC1_MAIN                        2  8190  2048  2048
VC1_ADVANCED                    4  8190  2048  2048
MPEG4_PART2_SP                  3  8192  2048  2048
MPEG4_PART2_ASP                 5  8192  2048  2048
DIVX4_QMOBILE                   0  8192  2048  2048
DIVX4_MOBILE                    0  8192  2048  2048
DIVX4_HOME_THEATER              0  8192  2048  2048
DIVX4_HD_1080P                  0  8192  2048  2048
DIVX5_QMOBILE                   0  8192  2048  2048
DIVX5_MOBILE                    0  8192  2048  2048
DIVX5_HOME_THEATER              0  8192  2048  2048
DIVX5_HD_1080P                  0  8192  2048  2048
H264_CONSTRAINED_BASELINE      --- not supported ---
H264_EXTENDED                  --- not supported ---
H264_PROGRESSIVE_HIGH          --- not supported ---
H264_CONSTRAINED_HIGH          --- not supported ---
H264_HIGH_444_PREDICTIVE       --- not supported ---
HEVC_MAIN                      --- not supported ---                                                                                                                  
HEVC_MAIN_10                   --- not supported ---                                                                                                                  
HEVC_MAIN_STILL                --- not supported ---                                                                                                                  
HEVC_MAIN_12                   --- not supported ---                                                                                                                  
HEVC_MAIN_444                  --- not supported ---                                                                                                                  
                                                                                                                                                                      
Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8         16384 16384    y  Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
R10G10B10A2      16384 16384    y  Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8         16384 16384
R8G8B8A8         16384 16384
R10G10B10A2      16384 16384
B10G10R10A2      16384 16384
A8               16384 16384

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        y
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y

---

### Post by Yellow Pasque on 2015-10-03
Yes, it appears to be the same issue. You can either wait for a fix or use a PPA to upgrade to Nvidia 355.xx driver: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

