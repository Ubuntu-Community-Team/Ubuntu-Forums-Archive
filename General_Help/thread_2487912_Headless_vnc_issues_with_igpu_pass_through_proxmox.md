---
title: "Headless vnc issues with igpu pass through proxmox"
date: 2023-06-17
forum: General Help
---

### Post by frennic on 2023-06-17
I have ubuntu 22.04.2 running in proxmox on a i3 1215u box. I followed a guide [https://github.com/strongtz/i915-sriov-dkms](https://github.com/strongtz/i915-sriov-dkms) to Virtualize the Intel iGPU for multiple VMs for hardware accelerated graphics and media encode/decode.

That worked fine and the virtualized igpu shows up in ubuntu now as long as I disable the the display hardware in proxmox. SSH in and vainfo

```
Trying display: waylandTrying display: x11
error: can't connect to X server!
Trying display: drm
libva info: VA-API version 1.18.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
libva info: Found init function __vaDriverInit_1_18
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.18 (libva 2.18.0)
vainfo: Driver version: Intel iHD driver for Intel(R) Gen Graphics - 23.1.6 ()
vainfo: Supported profile and entrypoints
      VAProfileNone                   : VAEntrypointVideoProc
      VAProfileNone                   : VAEntrypointStats
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Simple            : VAEntrypointEncSlice
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointEncSlice
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointEncSlice
      VAProfileH264Main               : VAEntrypointFEI
      VAProfileH264Main               : VAEntrypointEncSliceLP
      VAProfileH264High               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointEncSlice
      VAProfileH264High               : VAEntrypointFEI
      VAProfileH264High               : VAEntrypointEncSliceLP
      VAProfileVC1Simple              : VAEntrypointVLD
      VAProfileVC1Main                : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD
      VAProfileJPEGBaseline           : VAEntrypointVLD
      VAProfileJPEGBaseline           : VAEntrypointEncPicture
      VAProfileH264ConstrainedBaseline: VAEntrypointVLD
      VAProfileH264ConstrainedBaseline: VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline: VAEntrypointFEI
      VAProfileH264ConstrainedBaseline: VAEntrypointEncSliceLP
      VAProfileVP8Version0_3          : VAEntrypointVLD
      VAProfileHEVCMain               : VAEntrypointVLD
      VAProfileHEVCMain               : VAEntrypointEncSlice
      VAProfileHEVCMain               : VAEntrypointFEI
      VAProfileHEVCMain               : VAEntrypointEncSliceLP
      VAProfileHEVCMain10             : VAEntrypointVLD
      VAProfileHEVCMain10             : VAEntrypointEncSlice
      VAProfileHEVCMain10             : VAEntrypointEncSliceLP
      VAProfileVP9Profile0            : VAEntrypointVLD
      VAProfileVP9Profile0            : VAEntrypointEncSliceLP
      VAProfileVP9Profile1            : VAEntrypointVLD
      VAProfileVP9Profile1            : VAEntrypointEncSliceLP
      VAProfileVP9Profile2            : VAEntrypointVLD
      VAProfileVP9Profile2            : VAEntrypointEncSliceLP
      VAProfileVP9Profile3            : VAEntrypointVLD
      VAProfileVP9Profile3            : VAEntrypointEncSliceLP
      VAProfileHEVCMain12             : VAEntrypointVLD
      VAProfileHEVCMain12             : VAEntrypointEncSlice
      VAProfileHEVCMain422_10         : VAEntrypointVLD
      VAProfileHEVCMain422_10         : VAEntrypointEncSlice
      VAProfileHEVCMain422_12         : VAEntrypointVLD
      VAProfileHEVCMain422_12         : VAEntrypointEncSlice
      VAProfileHEVCMain444            : VAEntrypointVLD
      VAProfileHEVCMain444            : VAEntrypointEncSliceLP
      VAProfileHEVCMain444_10         : VAEntrypointVLD
      VAProfileHEVCMain444_10         : VAEntrypointEncSliceLP
      VAProfileHEVCMain444_12         : VAEntrypointVLD
      VAProfileHEVCSccMain            : VAEntrypointVLD
      VAProfileHEVCSccMain            : VAEntrypointEncSliceLP
      VAProfileHEVCSccMain10          : VAEntrypointVLD
      VAProfileHEVCSccMain10          : VAEntrypointEncSliceLP
      VAProfileHEVCSccMain444         : VAEntrypointVLD
      VAProfileHEVCSccMain444         : VAEntrypointEncSliceLP
      VAProfileAV1Profile0            : VAEntrypointVLD
      VAProfileHEVCSccMain444_10      : VAEntrypointVLD
      VAProfileHEVCSccMain444_10      : VAEntrypointEncSliceLP
```
So I am now trying to get RealVNC to work. I had to disable wayland as apparently RealVNC doesn't play nice with it. After disabling wayland, RealVNC worked fine. When I disabled the display in proxmox to allow the virtualized igpu to work I can no longer use RealVNC as it says "Currently cannot display desktop". I am only able to use it if the display is enabled in proxmox. If there is a display set proxmox then the intel doesn't work. So I am assuming I need some type of virtual display within Ubuntu so that RealVNC will work as intended. I see on their site it list installing a dummy driver but that would knock out my intel driver. So what I am trying to accomplish is having the virtualized igpu to function in ubuntu for transcoding etc, but also be able to use RealVNC on it headless. Is this achievable? Where am I going wrong?

Is there a way to force xorg into a fake/virtualized monitor output so I can get this going?

---

### Post by frennic on 2023-06-19
I thought I had it. By enabling the full function and primary gpu boxes in proxmox I had RealVNC working headless with a hardware edid plug. Unfortunately that knocked out the virtual igpus I created and just handed over the actual igpu. I can still set primary gpu in prox without it deselecting my virtual igpu, but that doesn't solve my need for some sort of forced virtual display in ubuntu for RealVNC to work. I'm banging my head on the wall. I could really use some guidance.

---

