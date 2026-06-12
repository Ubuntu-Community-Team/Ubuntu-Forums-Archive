---
title: "MPlayer make error"
date: 2005-10-12
forum: General Help
---

### Post by the__collector on 2005-10-12
After configuring Mplayer with --enable-gui I receive the following errors when I run a make:

```
libvo/libvo.a(vo_yuv4mpeg.o)(.text+0xa4): In function `config':
: undefined reference to `sws_rgb2rgb_init'
libvo/libvo.a(vo_yuv4mpeg.o)(.text+0x4f1): In function `flip_page':
: undefined reference to `rgb24toyv12'
libvo/libvo.a(vo_yuv4mpeg.o)(.text+0x550): In function `flip_page':
: undefined reference to `rgb24toyv12'
libvo/libvo.a(vo_yuv4mpeg.o)(.text+0x817): In function `flip_page':
: undefined reference to `rgb24toyv12'
Gui/libgui.a(ws.o)(.text+0x294): In function `wsXInit':
: undefined reference to `sws_rgb2rgb_init'
Gui/libgui.a(ws.o)(.text+0x2c7): In function `wsXInit':
: undefined reference to `rgb32tobgr32'
Gui/libgui.a(ws.o)(.text+0x2ce): In function `wsXInit':
: undefined reference to `rgb32to24'
Gui/libgui.a(ws.o)(.text+0x2d5): In function `wsXInit':
: undefined reference to `rgb32tobgr24'
Gui/libgui.a(ws.o)(.text+0x2e2): In function `wsXInit':
: undefined reference to `rgb32to16'
Gui/libgui.a(ws.o)(.text+0x2e9): In function `wsXInit':
: undefined reference to `rgb32tobgr16'
Gui/libgui.a(ws.o)(.text+0x2f0): In function `wsXInit':
: undefined reference to `rgb32to15'
Gui/libgui.a(ws.o)(.text+0x2f7): In function `wsXInit':
: undefined reference to `rgb32tobgr15'
libmpcodecs/libmpcodecs.a(vf_yuy2.o)(.text+0x5c): In function `config':
: undefined reference to `sws_rgb2rgb_init'
libmpcodecs/libmpcodecs.a(vf_yuy2.o)(.text+0x16d): In function `put_image':
: undefined reference to `yv12toyuy2'
libmpcodecs/libmpcodecs.a(vf_yuy2.o)(.text+0x1d0): In function `put_image':
: undefined reference to `yuv422ptoyuy2'
libmpcodecs/libmpcodecs.a(vf_rgb2bgr.o)(.text+0x206): In function `put_image':
: undefined reference to `rgb24tobgr24'
libmpcodecs/libmpcodecs.a(vf_rgb2bgr.o)(.text+0x251): In function `put_image':
: undefined reference to `rgb32tobgr32'
libmpcodecs/libmpcodecs.a(vf_rgb2bgr.o)(.text+0x29e): In function `put_image':
: undefined reference to `rgb24tobgr24'
libmpcodecs/libmpcodecs.a(vf_rgb2bgr.o)(.text+0x2c8): In function `put_image':
: undefined reference to `rgb32tobgr32'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x424): In function `put_image':
: undefined reference to `palette8tobgr15'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x44b): In function `put_image':
: undefined reference to `palette8torgb15'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x477): In function `put_image':
: undefined reference to `palette8tobgr32'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x493): In function `put_image':
: undefined reference to `palette8torgb32'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x4bc): In function `put_image':
: undefined reference to `palette8tobgr24'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x4db): In function `put_image':
: undefined reference to `palette8torgb24'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x500): In function `put_image':
: undefined reference to `palette8tobgr16'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x526): In function `put_image':
: undefined reference to `palette8torgb16'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x585): In function `put_image':
: undefined reference to `palette8tobgr15'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x5ad): In function `put_image':
: undefined reference to `palette8torgb15'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x5e9): In function `put_image':
: undefined reference to `palette8tobgr32'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x611): In function `put_image':
: undefined reference to `palette8torgb32'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x63f): In function `put_image':
: undefined reference to `palette8tobgr24'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x667): In function `put_image':
: undefined reference to `palette8torgb24'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x695): In function `put_image':
: undefined reference to `palette8tobgr16'
libmpcodecs/libmpcodecs.a(vf_palette.o)(.text+0x6bd): In function `put_image':
: undefined reference to `palette8torgb16'
libmpcodecs/libmpcodecs.a(vf_halfpack.o)(.text+0x3fb): In function `put_image':
: undefined reference to `yuv422ptoyuy2'
postproc/libswscale.a(swscale.o)(.text+0x80f): In function `sws_getContext':
: undefined reference to `rgb15to16'
postproc/libswscale.a(swscale.o)(.text+0x1f9e): In function `sws_getContext':
: undefined reference to `sws_rgb2rgb_init'
postproc/libswscale.a(swscale.o)(.text+0x5ca6): In function `PlanarToNV12Wrapper':
: undefined reference to `interleaveBytes'
postproc/libswscale.a(swscale.o)(.text+0x5d99): In function `PlanarToYuy2Wrapper':
: undefined reference to `yv12toyuy2'
postproc/libswscale.a(swscale.o)(.text+0x5e19): In function `PlanarToUyvyWrapper':
: undefined reference to `yv12touyvy'
postproc/libswscale.a(swscale.o)(.text+0x5fb2): In function `rgb2rgbWrapper':
: undefined reference to `rgb15tobgr15'
postproc/libswscale.a(swscale.o)(.text+0x5fc0): In function `rgb2rgbWrapper':
: undefined reference to `rgb16tobgr15'
postproc/libswscale.a(swscale.o)(.text+0x5fce): In function `rgb2rgbWrapper':
: undefined reference to `rgb24tobgr15'
postproc/libswscale.a(swscale.o)(.text+0x5fd6): In function `rgb2rgbWrapper':
: undefined reference to `rgb32tobgr15'
postproc/libswscale.a(swscale.o)(.text+0x5fe4): In function `rgb2rgbWrapper':
: undefined reference to `rgb15tobgr16'
postproc/libswscale.a(swscale.o)(.text+0x5ff2): In function `rgb2rgbWrapper':
: undefined reference to `rgb16tobgr16'
postproc/libswscale.a(swscale.o)(.text+0x6001): In function `rgb2rgbWrapper':
: undefined reference to `rgb24tobgr16'
postproc/libswscale.a(swscale.o)(.text+0x600f): In function `rgb2rgbWrapper':
: undefined reference to `rgb32tobgr16'
postproc/libswscale.a(swscale.o)(.text+0x6016): In function `rgb2rgbWrapper':
: undefined reference to `rgb15tobgr24'
postproc/libswscale.a(swscale.o)(.text+0x601d): In function `rgb2rgbWrapper':
: undefined reference to `rgb16tobgr24'
postproc/libswscale.a(swscale.o)(.text+0x6025): In function `rgb2rgbWrapper':
: undefined reference to `rgb24tobgr24'
postproc/libswscale.a(swscale.o)(.text+0x602c): In function `rgb2rgbWrapper':
: undefined reference to `rgb32tobgr24'
postproc/libswscale.a(swscale.o)(.text+0x6033): In function `rgb2rgbWrapper':
: undefined reference to `rgb15tobgr32'
postproc/libswscale.a(swscale.o)(.text+0x603a): In function `rgb2rgbWrapper':
: undefined reference to `rgb16tobgr32'
postproc/libswscale.a(swscale.o)(.text+0x6041): In function `rgb2rgbWrapper':
: undefined reference to `rgb24tobgr32'
postproc/libswscale.a(swscale.o)(.text+0x6049): In function `rgb2rgbWrapper':
: undefined reference to `rgb32tobgr32'
postproc/libswscale.a(swscale.o)(.text+0x6094): In function `rgb2rgbWrapper':
: undefined reference to `rgb16to15'
postproc/libswscale.a(swscale.o)(.text+0x609f): In function `rgb2rgbWrapper':
: undefined reference to `rgb24to15'
postproc/libswscale.a(swscale.o)(.text+0x60aa): In function `rgb2rgbWrapper':
: undefined reference to `rgb32to15'
postproc/libswscale.a(swscale.o)(.text+0x60b4): In function `rgb2rgbWrapper':
: undefined reference to `rgb15to16'
postproc/libswscale.a(swscale.o)(.text+0x60bf): In function `rgb2rgbWrapper':
: undefined reference to `rgb24to16'
postproc/libswscale.a(swscale.o)(.text+0x60ca): In function `rgb2rgbWrapper':
: undefined reference to `rgb32to16'
postproc/libswscale.a(swscale.o)(.text+0x60d4): In function `rgb2rgbWrapper':
: undefined reference to `rgb15to24'
postproc/libswscale.a(swscale.o)(.text+0x60df): In function `rgb2rgbWrapper':
: undefined reference to `rgb16to24'
postproc/libswscale.a(swscale.o)(.text+0x60ea): In function `rgb2rgbWrapper':
: undefined reference to `rgb32to24'
postproc/libswscale.a(swscale.o)(.text+0x60f4): In function `rgb2rgbWrapper':
: undefined reference to `rgb15to32'
postproc/libswscale.a(swscale.o)(.text+0x60ff): In function `rgb2rgbWrapper':
: undefined reference to `rgb16to32'
postproc/libswscale.a(swscale.o)(.text+0x610a): In function `rgb2rgbWrapper':
: undefined reference to `rgb24to32'
postproc/libswscale.a(swscale.o)(.text+0x61a0): In function `bgr24toyv12Wrapper':
: undefined reference to `rgb24toyv12'
postproc/libswscale.a(swscale.o)(.text+0x625e): In function `yvu9toyv12Wrapper':: undefined reference to `planar2x'
postproc/libswscale.a(swscale.o)(.text+0x629d): In function `yvu9toyv12Wrapper':: undefined reference to `planar2x'
postproc/libswscale.a(swscale.o)(.text+0x62e8): In function `yvu9toyv12Wrapper':: undefined reference to `planar2x'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

How can I solve this?

---

