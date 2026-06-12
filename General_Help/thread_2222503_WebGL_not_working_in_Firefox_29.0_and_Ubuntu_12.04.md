---
title: "WebGL not working in Firefox 29.0 and Ubuntu 12.04"
date: 2014-05-06
forum: General Help
---

### Post by msousa on 2014-05-06
Hi

My laptop has Ubuntu 12.04 and firefox v29.0. I have not been able to get WebGL to work on it. I suspect that my graphics card is blacklisted. I have tried a number of fixes described in the forums for older versions, like using libosmesa6 (about:config doesn't show webgl.osmesalib as suggested) and setting about:config -> webgl.force-enabled to True caused firefox to crash. Any other tricks I might try to view WebGL content?

Thanks...

---

### Post by monkeybrain20122 on 2014-05-06
To enable webgl for "unsupported" drivers you need to go to about:config and set layers.acceleration.force-enabled=true

Since FF28 because of switching to off-mainthread-composting you need to do two additional things.
1) In about:config set layers.offmainthreadcomposition-enabled=true
and
2) put the line "export MOZ_USE_OMTC=1" (without quotations) in your .profile, then logout and login again.

[http://featherweightmusings.blogspot.ca/2013/11/no-more-main-thread-opengl-in-firefox.html](http://featherweightmusings.blogspot.ca/2013/11/no-more-main-thread-opengl-in-firefox.html)

If Firefox crashes as a result just remove the line 2) from .profile, logout and log in again. Step 2) is hopefully only temporary, I checked that it not necessary in FF31 nightly build.

You can check if webgl is working by visiting [https://webglsamples.googlecode.com/hg/aquarium/aquarium.html](https://webglsamples.googlecode.com/hg/aquarium/aquarium.html)

---

### Post by msousa on 2014-05-06
Thanks monkeybrain.

Just to try it, I did this:
1) about:config->layers.acceleration.force-enabled=true 
2) about:config->layers.offmainthreadcomposition.enabled=true
3) In terminal
```

$ export MOZ_USE_OMTC=1
$ echo MOZ_USE_OMTC
      MOZ_USE_OMTC
$ firefox &

```

I then went to the website you suggested ([https://webglsamples.googlecode.com/hg/aquarium/aquarium.html](https://webglsamples.googlecode.com/hg/aquarium/aquarium.html)) and was able to view a column of numbers with fps as title. I then took a look at [http://doesmybrowsersupportwebgl.com/](http://doesmybrowsersupportwebgl.com/) and got a NAY and the website [http://get.webgl.org/](http://get.webgl.org/) told me:
"Hmm.  While your browser seems to support WebGL, it is disabled or  unavailable.  If possible, please ensure that you are running the latest  drivers for your video card."

It still looks like my firefox doesn't show WebGL content (at least it hasn't crashed through this process :)

---

### Post by monkeybrain20122 on 2014-05-06
I don't know, I went to your links and got yay and saw a rotating cube. All I did was those three things I told you. Intel graphic with i915 driver here (and i965 for hwacceleration)

Check about:support , go to graphics, I have these

 ```
Graphics
Adapter Description    Intel Open Source Technology Center -- Mesa DRI Intel(R) Ironlake Mobile
Device ID    Mesa DRI Intel(R) Ironlake Mobile
Driver Version    2.1 Mesa 10.3.0-devel (git-2484daa trusty-oibaf-ppa)
GPU Accelerated Windows    1/1 OpenGL (OMTC)
Vendor ID    Intel Open Source Technology Center
WebGL Renderer    Intel Open Source Technology Center -- Mesa DRI Intel(R) Ironlake Mobile
windowLayerManagerRemote    true
AzureCanvasBackend    cairo
AzureContentBackend    cairo
AzureFallbackCanvasBackend    none
AzureSkiaAccelerated    0
JavaScript
```

---

### Post by msousa on 2014-05-06
Is there a way to tell which graphic my system is using and its driver?

---

### Post by monkeybrain20122 on 2014-05-06
See my edit.

Also post the outputs of 
lshw -C display

---

### Post by msousa on 2014-05-06
It does show some issues:

```

Adapter Description    GLXtest process failed (exited with status 1): X error occurred in GLX probe, error_code=1, request_code=153, minor_code=19
GPU Accelerated Windows    0/8 Basic Blocked for your graphics driver version. Try updating your graphics driver to version <Anything with EXT_texture_from_pixmap support> or newer.
WebGL Renderer    Blocked for your graphics card because of unresolved driver issues.
windowLayerManagerRemote    false
AzureCanvasBackend    cairo
AzureContentBackend    cairo
AzureFallbackCanvasBackend    none
AzureSkiaAccelerated    0

```

I then tried this:
```

$ lspci | grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780M [Mobility Radeon HD 3200]
$ 

```

Here's lshw:
```

$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RS780M [Mobility Radeon HD 3200]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff ioport:9000(size=256) memory:cfdf0000-cfdfffff memory:cfe00000-cfefffff
$

```

---

### Post by monkeybrain20122 on 2014-05-06
Hmm the hd 3200 is rather old. I am not sure I know how to advise you, I am sorry.

Edited: You may try to update your driver with [https://launchpad.net/~pali/+archive/graphics-drivers](https://launchpad.net/~pali/+archive/graphics-drivers), but not sure if it will do a lot of good and it may be kind of risky, so be warned.

---

### Post by msousa on 2014-05-06
Thanks for your time monkeybrain, guess I'm stuck.

I took a look at that driver before and in a different discussion here was also warned and so I have decided that I will stick with the driver that came with Ubuntu. It has worked until coming upon this WebGL stuff. -- thanks.

---

### Post by monkeybrain20122 on 2014-05-06
Did you try chrome or chromium? You may have better luck.. On those, go to about:flag and enable override software rendering, then restart browser and go to about:gpu and see if it looks encouraging..

---

### Post by msousa on 2014-05-06
Same outcome with chrome. The WebGL sites failed.

from about:gpu (after enabling about:flags->override software rendering)
```

[COLOR=#000000][FONT=sans-serif]**Graphics Feature Status**


[LIST]
[*]Canvas: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR] 
[*]3D CSS: [COLOR=#FF0000]Unavailable. Hardware acceleration unavailable[/COLOR] 
[*]Compositing: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR] 
[*]CSS Animation: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR] 
[*]Flash 3D: [COLOR=#FF0000]Unavailable. Hardware acceleration unavailable[/COLOR] 
[*]Flash Stage3D: [COLOR=#FF0000]Unavailable. Hardware acceleration unavailable[/COLOR] 
[*]Flash Stage3D Baseline profile: [COLOR=#FF0000]Unavailable. Hardware acceleration unavailable[/COLOR] 
[*]Video: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR] 
[*]Video Decode: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR] 
[*]Video Encode: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR] 
[*]WebGL: [COLOR=#FF0000]Unavailable. Hardware acceleration unavailable[/COLOR] 
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Problems Detected**


[LIST]
[*]GPU process was unable to boot: GPU process launch failed. 
[/LIST]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]**Driver Bug Workarounds**


[LIST]
[*]clear_alpha_in_readpixels 
[*]clear_uniforms_before_first_program_use 
[*]set_texture_filter_before_generating_mipmap 
[/LIST]
[/FONT][/COLOR]

```[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2014-05-07
Hmm.. Just look over this [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature) Seems that quite a bit of work has been done on your card since 12.04, so upgrading your driver with the ppa would be a nice performance boost. But do back up your important data and install ppa-purge just in case.

[https://launchpad.net/~pali/+archive/graphics-drivers](https://launchpad.net/~pali/+archive/graphics-drivers)

---

