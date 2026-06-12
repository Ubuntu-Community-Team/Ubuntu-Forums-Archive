---
title: "Compiling xine-lib 1.1.4"
date: 2007-03-01
forum: General Help
---

### Post by konst88 on 2007-03-01
Hello.
I am trying to compile xine-lib.
The configure script finished successfully, without errors.
During the make proccess, I got the following error:
```
h264.c:2249: warning: no previous prototype for 'ff_pred16x16_vertical_c'
h264.c:2264: warning: no previous prototype for 'ff_pred16x16_horizontal_c'
h264.c:2275: warning: no previous prototype for 'ff_pred16x16_dc_c'
h264.c:2329: warning: no previous prototype for 'ff_pred16x16_128_dc_c'
h264.c:2380: warning: no previous prototype for 'ff_pred16x16_plane_c'
h264.c:2384: warning: no previous prototype for 'ff_pred8x8_vertical_c'
h264.c:2395: warning: no previous prototype for 'ff_pred8x8_horizontal_c'
h264.c:2404: warning: no previous prototype for 'ff_pred8x8_128_dc_c'
h264.c:2458: warning: no previous prototype for 'ff_pred8x8_dc_c'
h264.c:2483: warning: no previous prototype for 'ff_pred8x8_plane_c'
h264.c: In function 'hl_decode_mb':
h264.c:3550: warning: suggest parentheses around arithmetic in operand of ^
h264.c:3556: warning: suggest parentheses around arithmetic in operand of ^
h264.c: In function 'decode_mb_cavlc':
h264.c:5236: warning: pointer targets in passing argument 2 of 'pred_direct_motion' differ in signedness
h264.c:5326: warning: pointer targets in passing argument 2 of 'pred_direct_motion' differ in signedness
h264.c: In function 'decode_unregistered_user_data':
h264.c:7550: warning: pointer targets in passing argument 1 of 'sscanf' differ in signedness
h264.c: In function 'decode_scaling_matrices':
h264.c:7715: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
The bug is not reproducible, so it is likely a hardware or OS problem.
make[5]: *** [h264.lo] Error 1
make[5]: Leaving directory `/home/kon/xine-lib-1.1.4/src/libffmpeg/libavcodec'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/kon/xine-lib-1.1.4/src/libffmpeg/libavcodec'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/kon/xine-lib-1.1.4/src/libffmpeg'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kon/xine-lib-1.1.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kon/xine-lib-1.1.4'
make: *** [all] Error 2

```

---

