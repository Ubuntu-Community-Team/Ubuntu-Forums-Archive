---
title: "Mplayer,Freezes and FATAL: Cannot initialize video driver on Optimus Notebook"
date: 2013-09-09
forum: General Help
---

### Post by fallout4all on 2013-09-09
i have a problem with VLC 2.0.8 and mplayer(smplayer) on my optimus notebook(Intel® Core™ i3-2310M CPU @ 2.10GHz , 8GB RAM 1333Mhz, Nvidia GT540M), all videos is freezing(lags) and overlay frame. I have installed mplayer-vaapi and enable all hardware acceleration but it dont help.


in mplayer(smplayer) error:
```
VO: [vaapi] 720x304 => 720x304 MPEG-4 VA-API Acceleration 
FATAL: Cannot initialize video driver.

```

In VLC :
```
avcodec decoder debug: allowing 2 thread(s) for decoding
[0x7f6470c02dd8] avcodec decoder warning: threaded frame decoding is not compatible with ffmpeg-hw, disabled
[0x7f6470c02dd8] avcodec decoder debug: Available decoder output format 61 (dxva2_vld)
[0x7f6470c02dd8] avcodec decoder debug: Available decoder output format 53 (vaapi_vld)
[0x7f6470c02dd8] avcodec decoder debug: Trying VA API
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
[0x7f6470c02dd8] avcodec decoder warning: Failed to open VA API
[0x7f6470c02dd8] avcodec decoder debug: Available decoder output format 81 (vda_vld)
[0x7f6470c02dd8] avcodec decoder debug: Available decoder output format 0 (yuv420p)
[0x7f6470c02dd8] avcodec decoder debug: ffmpeg codec (MPEG-4 Video) started

```

My distro is xUbuntu 13.04. And i dont use optirun...because wanna play videos on intel HD 3000 card.

---

### Post by Linuxisfast on 2013-09-10
> **fallout4all said:**
> i have a problem with VLC 2.0.8 and mplayer(smplayer) on my optimus notebook(Intel® Core&#8482; i3-2310M CPU @ 2.10GHz , 8GB RAM 1333Mhz, Nvidia GT540M), all videos is freezing(lags) and overlay frame. I have installed mplayer-vaapi and enable all hardware acceleration but it dont help.


in mplayer(smplayer) error:
```
VO: [vaapi] 720x304 => 720x304 MPEG-4 VA-API Acceleration 
FATAL: Cannot initialize video driver.

```

In VLC :
```
avcodec decoder debug: allowing 2 thread(s) for decoding
[0x7f6470c02dd8] avcodec decoder warning: threaded frame decoding is not compatible with ffmpeg-hw, disabled
[0x7f6470c02dd8] avcodec decoder debug: Available decoder output format 61 (dxva2_vld)
[0x7f6470c02dd8] avcodec decoder debug: Available decoder output format 53 (vaapi_vld)
[0x7f6470c02dd8] avcodec decoder debug: Trying VA API
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
[0x7f6470c02dd8] avcodec decoder warning: Failed to open VA API
[0x7f6470c02dd8] avcodec decoder debug: Available decoder output format 81 (vda_vld)
[0x7f6470c02dd8] avcodec decoder debug: Available decoder output format 0 (yuv420p)
[0x7f6470c02dd8] avcodec decoder debug: ffmpeg codec (MPEG-4 Video) started

```

My distro is xUbuntu 13.04. And i dont use optirun...because wanna play videos on intel HD 3000 card.

If you have disabled the nvidia card with Bumblebee, you need to install intel-vaapi driver to get hardware acceleration with VLC. Make sure to tick hardware acceleration under VLC>Inputs and codecs option. Alternatively if you are using Bumblebee you can give optirun vlc command to run it with nvidia.

---

### Post by fallout4all on 2013-09-10
> **Linuxisfast said:**
> install intel-vaapi driver to get hardware acceleration with VLC. Make sure to tick hardware acceleration under VLC>Inputs and codecs option. 
This all done, but not help

---

