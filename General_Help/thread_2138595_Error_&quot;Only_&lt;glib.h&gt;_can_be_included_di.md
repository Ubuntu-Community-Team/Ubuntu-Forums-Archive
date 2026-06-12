---
title: "Error: &quot;Only &lt;glib.h&gt; can be included directly.&quot;"
date: 2013-04-24
forum: General Help
---

### Post by mabtifro2 on 2013-04-24
ive spent hours trying to install opensync (which is no longer available in repositories for some reason) from a tar.gz package on 12.10 with an annoying error every step of the way. finally when i thought i had it all figured out, im getting this error i cant solve. i tried googling the hell out of it. im not good at building packages, i always have to use instructions. pleeeeeeeease help!


[PHP]...@...-V5-171:~$ cmake -DCMAKE_INSTALL_PREFIX=$prefix //home/.../Desktop/libopensync-0.39
-- checking for one of the modules 'check'
-- ==================================================
-- enable testing				OFF
-- build wrapper				OFF
-- build documentation				OFF
-- Configuring done
-- Generating done
-- Build files have been written to: /home/...
...@...-V5-171:~$ make
[  1%] Building C object opensync/CMakeFiles/opensync.dir/common/opensync_list.o
In file included from //home/.../Desktop/libopensync-0.39/opensync/common/opensync_list.c:33:0:
/usr/include/glib-2.0/glib/gmem.h:28:2: error: #error "Only <glib.h> can be included directly."
In file included from /usr/include/glib-2.0/glib/gmem.h:34:0,
                 from //home/.../Desktop/libopensync-0.39/opensync/common/opensync_list.c:33:
/usr/include/glib-2.0/glib/gtypes.h:28:2: error: #error "Only <glib.h> can be included directly."
In file included from /usr/lib/x86_64-linux-gnu/glib-2.0/include/glibconfig.h:9:0,
                 from /usr/include/glib-2.0/glib/gtypes.h:34,
                 from /usr/include/glib-2.0/glib/gmem.h:34,
                 from //home/.../Desktop/libopensync-0.39/opensync/common/opensync_list.c:33:
/usr/include/glib-2.0/glib/gmacros.h:32:2: error: #error "Only <glib.h> can be included directly."
In file included from /usr/include/glib-2.0/glib/gtypes.h:35:0,
                 from /usr/include/glib-2.0/glib/gmem.h:34,
                 from //home/.../Desktop/libopensync-0.39/opensync/common/opensync_list.c:33:
/usr/include/glib-2.0/glib/gmacros.h:32:2: error: #error "Only <glib.h> can be included directly."
In file included from /usr/include/glib-2.0/glib/gtypes.h:36:0,
                 from /usr/include/glib-2.0/glib/gmem.h:34,
                 from //home/.../Desktop/libopensync-0.39/opensync/common/opensync_list.c:33:
/usr/include/glib-2.0/glib/gversionmacros.h:28:2: error: #error "Only <glib.h> can be included directly."
make[2]: *** [opensync/CMakeFiles/opensync.dir/common/opensync_list.o] Error 1
make[1]: *** [opensync/CMakeFiles/opensync.dir/all] Error 2
make: *** [all] Error 2
...@...-V5-171:~$ 
[/PHP]

---

