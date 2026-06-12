---
title: "kernel 4.2, intel gpu and vaapi"
date: 2015-11-09
forum: General Help
---

### Post by monkeybrain20122 on 2015-11-09
Seems that vaapi is working less efficiently with kernels 4.2 and 4.3 then 4.1 and before. Using mpv with vaapi the same 1080p videos use ~ 15% cpu in 4.1 and before but goes up tp ~ 25% in 4.2 and 4.3. Tried that with Ubuntu 15.10 and 15.04 (tested with mainline kernels 4.1 and 4.3 on 15.10, 4.2, 4.1 on 15.04) The ~10 -15% cpu increases are consistent for all videos I have tested.

On this computer this is no big deal, it can handle an increase of 10% cpu with no sweat, but I still think it is a regression.  Not sure what to look at if I want to file a bug and where to. Any suggestion?

```
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_38
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.38 (libva 1.6.1)
vainfo: Driver version: Intel i965 driver for Intel(R) Ironlake Mobile - 1.6.1
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc
```

---

