---
title: "Hardware Accelerated VP9"
date: 2021-06-28
forum: General Help
---

### Post by Shibblet on 2021-06-28
Can anyone tell me if they have Hardware VP9 Acceleration in Ubuntu/Kubuntu/Etc?

If so, what kind of Video Card and/or Processor are you running?

---

### Post by Frogs Hair on 2021-06-28
It's not supported here.


```
vdpauinfo
```
```
Decoder capabilities:

name                        level macbs width height
----------------------------------------------------
MPEG1                           0  8192  2048  2048
MPEG2_SIMPLE                    3  8192  2048  2048
MPEG2_MAIN                      3  8192  2048  2048
H264_BASELINE                  41  8192  2048  2048
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
H264_CONSTRAINED_BASELINE      41  8192  2048  2048
H264_EXTENDED                  41  8192  2048  2048
H264_PROGRESSIVE_HIGH          41  8192  2048  2048
H264_CONSTRAINED_HIGH          41  8192  2048  2048
H264_HIGH_444_PREDICTIVE       41  8192  2048  2048
VP9_PROFILE_0                  --- not supported ---
VP9_PROFILE_1                  --- not supported ---
VP9_PROFILE_2                  --- not supported ---
VP9_PROFILE_3                  --- not supported ---
HEVC_MAIN                      --- not supported ---
HEVC_MAIN_10                   --- not supported ---
HEVC_MAIN_STILL                --- not supported ---
HEVC_MAIN_12                   --- not supported ---
HEVC_MAIN_444                  --- not supported ---
HEVC_MAIN_444_10               --- not supported ---
HEVC_MAIN_444_12               --- not supported ---


```

---

### Post by Shibblet on 2021-06-28
> **Frogs Hair said:**
> It's not supported here.


```
vdpauinfo
```
```
Decoder capabilities:

name                        level macbs width height
----------------------------------------------------
MPEG1                           0  8192  2048  2048
MPEG2_SIMPLE                    3  8192  2048  2048
MPEG2_MAIN                      3  8192  2048  2048
H264_BASELINE                  41  8192  2048  2048
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
H264_CONSTRAINED_BASELINE      41  8192  2048  2048
H264_EXTENDED                  41  8192  2048  2048
H264_PROGRESSIVE_HIGH          41  8192  2048  2048
H264_CONSTRAINED_HIGH          41  8192  2048  2048
H264_HIGH_444_PREDICTIVE       41  8192  2048  2048
VP9_PROFILE_0                  --- not supported ---
VP9_PROFILE_1                  --- not supported ---
VP9_PROFILE_2                  --- not supported ---
VP9_PROFILE_3                  --- not supported ---
HEVC_MAIN                      --- not supported ---
HEVC_MAIN_10                   --- not supported ---
HEVC_MAIN_STILL                --- not supported ---
HEVC_MAIN_12                   --- not supported ---
HEVC_MAIN_444                  --- not supported ---
HEVC_MAIN_444_10               --- not supported ---
HEVC_MAIN_444_12               --- not supported ---


```

What video processor are you using?

---

### Post by Shibblet on 2021-06-28
I guess what I am asking is...  If I buy a new CPU that does VP9 onboard (Like a Ryzen 3000 or higher), will it be supported in Linux.  i.e. Will I be able to decode YouTube Video, and/or Stadia in Hardware... or will VP9 just be "Hardware Assisted" like H.264 is currently in the Browser?

---

### Post by Frogs Hair on 2021-06-28
I have a Nvidia 730 GT and Athlon x IV. You would have to ask someone with a newer CPU & GPU.

[https://linuxreviews.org/VP9](https://linuxreviews.org/VP9)

---

### Post by Shibblet on 2021-06-28
> **Frogs Hair said:**
> I have a Nvidia 730 GT and Athlon x IV. You would have to ask someone with a newer CPU & GPU.

[https://linuxreviews.org/VP9](https://linuxreviews.org/VP9)

Thanks for that link!  That helps a lot.

I do find it funny, however, this chart shows that Chrome supports Hardware H.264 in Linux, and it clearly does not.

---

### Post by Frogs Hair on 2021-06-29
As for browsers, only opera on Linux has playback issues with [COLOR=#000000]H.264 in my experience . [/COLOR]

---

### Post by Yellow Pasque on 2021-06-29
Ryzen 2400G

```
$ vainfo 
libva info: VA-API version 1.10.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/radeonsi_drv_video.so
libva info: Found init function __vaDriverInit_1_10
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.10 (libva 2.10.0)
vainfo: Driver version: Mesa Gallium driver 21.1.3 for AMD Radeon(TM) Vega 11 Graphics (RAVEN, DRM 3.40.0, 5.12.13-3-siduction-amd64, LLVM 12.0.1)
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileVC1Simple              : VAEntrypointVLD
      VAProfileVC1Main                : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD
      VAProfileH264ConstrainedBaseline: VAEntrypointVLD
      VAProfileH264ConstrainedBaseline: VAEntrypointEncSlice
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointEncSlice
      VAProfileH264High               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointEncSlice
      VAProfileHEVCMain               : VAEntrypointVLD
      VAProfileHEVCMain               : VAEntrypointEncSlice
      VAProfileHEVCMain10             : VAEntrypointVLD
      VAProfileJPEGBaseline           : VAEntrypointVLD
      VAProfileVP9Profile0            : VAEntrypointVLD
      VAProfileVP9Profile2            : VAEntrypointVLD
      VAProfileNone                   : VAEntrypointVideoProc
```


```
Graphics Feature Status
...
Video Decode: Hardware accelerated
...
```

---

### Post by Frogs Hair on 2021-06-29
Chromium snap playing H.264 sample. Newer hardware above looks promising.

---

### Post by Shibblet on 2021-06-29
> **Frogs Hair said:**
> Chromium snap playing H.264 sample. Newer hardware above looks promising.

I can get VA-API working in Chromium.  And it works as "Hardware Assisted" video playback.  But what I want to see is VDPAU, which actually uses the Hardware Decoder to playback video.  In other words, I want it to use the GPU, and not the CPU.

No matter what I do, I cannot get YouTube, Stadia, XCloud, and GeForce Now to use the H.264 Hardware Decoder.  They default to VP9.  And VP9 works, for the most part.  The games stream in 1080p, but then drop to 720p, because my computer cannot decode the stream "fast enough."  

These services work flawlessly in Windows 10 (on lesser hardware) though.  (I tried out YouTube, Stadia, XCloud, and GeForce Now on a friends PC.  i5-2600 / GTX 660)
YouTube required a Chrome Extension called h264ify, but Stadia, XCloud, and GeForce Now all adjusted to H.264 automatically.

And I know you can get most things to work in Linux with a little "elbow-grease" and some time... However, at this point, I feel like I am losing the fight.

I am planning on getting a new computer soon anyway, and before I buy one, I'd like to know if Hardware Acceleration works with these services in Linux.

It's a tough question to ask, I know...  But I don't know any other way to go with this.

I am even going to ask a second question here:  **Does anyone have a Hardware Based VP9 decoder (whether it's a dGPU or iGPU) that actually does Hardware Acceleration for YouTube / Stadia / XCloud / GeForce Now, in Linux?**

---

### Post by Yellow Pasque on 2021-06-29
> **Shibblet said:**
> I can get VA-API working in Chromium.  And it works as "Hardware Assisted" video playback.  But what I want to see is VDPAU, which actually uses the Hardware Decoder to playback video.

That doesn't make any sense. The video acceleration in chromium (and Firefox) is based on libva (VA-API). There is no direct VDPAU acceleration. I'm not aware of any attempt for those browsers to use VDPAU.

---

### Post by Shibblet on 2021-06-29
> **Yellow Pasque said:**
> That doesn't make any sense. The video acceleration in chromium (and Firefox) is based on libva (VA-API). There is no direct VDPAU acceleration. I'm not aware of any attempt for those browsers to use VDPAU.

It's possible that I don't quite understand how this all works... but I see VA-API as "Hardware Assisted," and VDPAU as "Hardware Accelerated."

The reason I see it that way, is because Video Acceleration doesn't seem to work for YouTube / Stadia / XCloud / GeForce Now, etc... as denoted in this post:
[https://ubuntuforums.org/showthread.php?t=2463888]("https://ubuntuforums.org/showthread.php?t=2463888")

YouTube is not really an issue.  But the Cloud Gaming Apps (Stadia / XCloud / GeForce Now) do not have a sufficient "Decode" time to keep my stream at 1080p... it always drops to 720p with a lot of block noise.  

When I see this in on a friends computer, that runs Windows 10, and has lesser hardware... There are no issues at all.  So, if it's not Video Acceleration, what is causing it?

And to get back to the main topic... I'd like to know if current hardware (capable of VP9 decoding, either/or dGPU or iGPU) actually works with acceleration in Linux, and not just "Hardware Assisted" acceleration.

---

### Post by Yellow Pasque on 2021-06-29
> but I see VA-API as "Hardware Assisted," and VDPAU as "Hardware Accelerated."

Huh? They are two competing standards.

---

### Post by Shibblet on 2021-06-29
> **Yellow Pasque said:**
> Huh? They are two competing standards.

Ok.  So, I don't quite understand how they work.  But VA-API doesn't seem to use the video-card's on-board accelerator.  

I've tested this in VLC and MPV (SMPlayer).  So, is it configured correctly?  Am I doing something wrong?  How can I fix this?

---

