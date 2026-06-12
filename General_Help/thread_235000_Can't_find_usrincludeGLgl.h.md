---
title: "Can't find /usr/include/GL/gl.h"
date: 2006-08-12
forum: General Help
---

### Post by Gustav on 2006-08-12
Hi, I'm trying to compile the game X-Moto (version 0.2.0). But I can't get it to compile.

After some researching it seems to me that it can't find the file /usr/include/GL/gl.h. I have searched for packages where it could possibly be but I haven't found any.

If anyone of you knows the solution for this I will be very glad.

---

### Post by VirtuAlex on 2006-08-12
i think it is libgl1-mesa-dev

---

### Post by Gustav on 2006-08-12
Nope, that's installed, and it just has the files:
```
/.
/usr
/usr/lib
/usr/include
/usr/include/GL
/usr/include/GL/glx.h
/usr/include/GL/glxext.h
/usr/include/GL/glx_mangle.h
/usr/share
/usr/share/doc
/usr/share/doc/libgl1-mesa-dev
/usr/share/doc/libgl1-mesa-dev/changelog.gz
/usr/share/doc/libgl1-mesa-dev/copyright
/usr/share/doc/libgl1-mesa-dev/changelog.Debian.gz
/usr/lib/libGL.so
```

---

### Post by VirtuAlex on 2006-08-12
what about mesa-common-dev?

---

### Post by Gustav on 2006-08-12
Have that one to, it inclused these files:
```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/mesa-common-dev
/usr/share/doc/mesa-common-dev/changelog.gz
/usr/share/doc/mesa-common-dev/RELNOTES-3.3.gz
/usr/share/doc/mesa-common-dev/bugs.html
/usr/share/doc/mesa-common-dev/debugging.html
/usr/share/doc/mesa-common-dev/envvars.html
/usr/share/doc/mesa-common-dev/faq.html
/usr/share/doc/mesa-common-dev/osmesa.html
/usr/share/doc/mesa-common-dev/RELNOTES-3.1
/usr/share/doc/mesa-common-dev/RELNOTES-3.2
/usr/share/doc/mesa-common-dev/RELNOTES-3.2.1
/usr/share/doc/mesa-common-dev/RELNOTES-3.4
/usr/share/doc/mesa-common-dev/RELNOTES-3.4.1
/usr/share/doc/mesa-common-dev/RELNOTES-3.4.2
/usr/share/doc/mesa-common-dev/RELNOTES-4.1.gz
/usr/share/doc/mesa-common-dev/RELNOTES-4.0.1
/usr/share/doc/mesa-common-dev/RELNOTES-4.0.2
/usr/share/doc/mesa-common-dev/RELNOTES-4.0.3
/usr/share/doc/mesa-common-dev/RELNOTES-5.0
/usr/share/doc/mesa-common-dev/RELNOTES-5.0.1
/usr/share/doc/mesa-common-dev/RELNOTES-5.0.2
/usr/share/doc/mesa-common-dev/RELNOTES-6.0
/usr/share/doc/mesa-common-dev/RELNOTES-6.0.1
/usr/share/doc/mesa-common-dev/RELNOTES-6.1
/usr/share/doc/mesa-common-dev/RELNOTES-6.2
/usr/share/doc/mesa-common-dev/RELNOTES-6.2.1
/usr/share/doc/mesa-common-dev/RELNOTES-6.3
/usr/share/doc/mesa-common-dev/RELNOTES-6.3.1
/usr/share/doc/mesa-common-dev/RELNOTES-6.3.2
/usr/share/doc/mesa-common-dev/RELNOTES-6.4
/usr/share/doc/mesa-common-dev/RELNOTES-6.4.1
/usr/share/doc/mesa-common-dev/MESA_agp_offset.spec
/usr/share/doc/mesa-common-dev/MESA_copy_sub_buffer.spec
/usr/share/doc/mesa-common-dev/MESA_pack_invert.spec
/usr/share/doc/mesa-common-dev/MESA_program_debug.spec.gz
/usr/share/doc/mesa-common-dev/MESA_pixmap_colormap.spec
/usr/share/doc/mesa-common-dev/MESA_trace.spec.gz
/usr/share/doc/mesa-common-dev/MESA_release_buffers.spec
/usr/share/doc/mesa-common-dev/MESA_resize_buffers.spec
/usr/share/doc/mesa-common-dev/MESA_set_3dfx_mode.spec
/usr/share/doc/mesa-common-dev/MESA_swap_control.spec
/usr/share/doc/mesa-common-dev/MESA_ycbcr_texture.spec.gz
/usr/share/doc/mesa-common-dev/MESA_window_pos.spec
/usr/share/doc/mesa-common-dev/copyright
/usr/share/doc/mesa-common-dev/changelog.Debian.gz
/usr/share/doc/mesa-common-dev/RELNOTES-3.5.gz
/usr/share/doc/mesa-common-dev/RELNOTES-4.0.gz
/usr/share/doc/mesa-common-dev/RELNOTES-5.1.gz
/usr/share/doc/mesa-common-dev/MESA_packed_depth_stencil.spec.gz
/usr/share/doc/mesa-common-dev/MESA_sprite_point.spec.gz
/usr/share/doc/mesa-common-dev/MESA_swap_frame_usage.spec.gz
/usr/include
/usr/include/GL
```

---

### Post by VirtuAlex on 2006-08-12
it should be there... try this
```
sudo apt-get --reinstall install mesa-common-dev
```

---

### Post by Gustav on 2006-08-14
You're right that will probably work.

I'm not at home for the moment but will try as soon as I get there.

Thank you!

---

### Post by alraz on 2007-11-04
I had the same problem. I noticed (thanks to all the posts here) that my IDE (Code::blocks) was taking /usr/bin/include as standar include dir, but my includes seem to be under /usr/include/

so, i just added /usr/include to code:blocks include dirs and it seems to work now.

by the way, I also instaled mesa libs

---

### Post by leonardodinnouti on 2008-02-01
I've installed the package:

```
sudo apt-get install x11proto-gl-dev
```

Or trying more automatically:

```
sudo apt-get build-dep xserver-xorg-video-via
```

---

