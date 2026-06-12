---
title: "Problem using make with Mplayer 1.0 pre7"
date: 2005-08-18
forum: General Help
---

### Post by pedromdsantos on 2005-08-18
I try to install MPlayer 1.0 pre7 and get some errors with dependencies. I solve all of them except this one and have no idea how to do it.
I used ./configure --enable-gui and then make. The list below cames from using the make command.
Does anyone knows how to solve this. In previous versions i never get this error.
Thanks


make[1]: Leaving directory `/home/pedromdsantos/mplayer-1.0pre7/MPlayer-1.0pre7/libmpdvdkit2'
make -C Gui
make[1]: Entering directory `/home/pedromdsantos/mplayer-1.0pre7/MPlayer-1.0pre7/Gui'
rm -f libgui.a
ar rc libgui.a wm/ws.o wm/wsxdnd.o app.o interface.o cfg.o bitmap.o skin/skin.o skin/font.o skin/cut.o mplayer/widgets.o mplayer/play.o mplayer/mw.o mplayer/sw.o mplayer/menu.o mplayer/pb.o mplayer/common.o mplayer/gtk/menu.o mplayer/gtk/mb.o mplayer/gtk/about.o mplayer/gtk/pl.o mplayer/gtk/sb.o mplayer/gtk/fs.o mplayer/gtk/opts.o mplayer/gtk/url.o mplayer/gtk/eq.o mplayer/gtk/common.o
true libgui.a
make[1]: Leaving directory `/home/pedromdsantos/mplayer-1.0pre7/MPlayer-1.0pre7/Gui'
cc -I../libvo -I../../libvo -I/usr/X11R6/include -fno-PIC -O4 -march=pentium3 -mcpu=pentium3 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I.  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include   -I/usr/X11R6/include       -o mplayer mplayer.o mp_msg.o cpudetect.o codec-cfg.o spudec.o playtree.o playtreeparser.o asxparser.o vobsub.o subreader.o sub_cc.o find_sub.o m_config.o m_option.o parser-cfg.o m_struct.o edl.o unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o libvo/libvo.a libao2/libao2.a  vidix/libvidix.a Gui/libgui.a libmpcodecs/libmpcodecs.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dmo/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a input/libinput.a postproc/libswscale.a osdep/libosdep.a -Llibmpdvdkit2 -lmpdvdkit libavcodec/libavcodec.a libavformat/libavformat.a          -lpng -lz -lz  -lasound -ldl -lpthread      -lnsl        libfaad2/libfaad2.a  mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a -L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -L/usr/lib -lglib  -lGL  -lXv  -lXxf86vm  -L/usr/X11R6/lib -lXext -lX11 -lnsl -lnsl                  -lpthread -ldl -rdynamic   -lm
Gui/libgui.a(interface.o)(.text+0xae5): In function `guiLoadFont':
: undefined reference to `vo_image_height'
Gui/libgui.a(interface.o)(.text+0xaef): In function `guiLoadFont':
: undefined reference to `vo_image_width'
Gui/libgui.a(interface.o)(.text+0xaf7): In function `guiLoadFont':
: undefined reference to `load_font_ft'
Gui/libgui.a(interface.o)(.text+0x1e76): In function `gtkSet':
: undefined reference to `subtitle_font_thickness'
Gui/libgui.a(interface.o)(.text+0x1e92): In function `gtkSet':
: undefined reference to `subtitle_font_radius'
Gui/libgui.a(interface.o)(.text+0x1e9a): In function `gtkSet':
: undefined reference to `text_font_scale_factor'
Gui/libgui.a(interface.o)(.text+0x1ea2): In function `gtkSet':
: undefined reference to `osd_font_scale_factor'
Gui/libgui.a(interface.o)(.text+0x1eab): In function `gtkSet':
: undefined reference to `subtitle_font_encoding'
Gui/libgui.a(interface.o)(.text+0x1eca): In function `gtkSet':
: undefined reference to `subtitle_font_encoding'
Gui/libgui.a(interface.o)(.text+0x1edc): In function `gtkSet':
: undefined reference to `subtitle_font_encoding'
Gui/libgui.a(interface.o)(.text+0x1ef2): In function `gtkSet':
: undefined reference to `subtitle_autoscale'
Gui/libgui.a(cfg.o)(.data+0x50c): undefined reference to `subtitle_font_encoding'
Gui/libgui.a(cfg.o)(.data+0x530): undefined reference to `text_font_scale_factor'
Gui/libgui.a(cfg.o)(.data+0x554): undefined reference to `osd_font_scale_factor'
Gui/libgui.a(cfg.o)(.data+0x578): undefined reference to `subtitle_font_radius'
Gui/libgui.a(cfg.o)(.data+0x59c): undefined reference to `subtitle_font_thickness'
Gui/libgui.a(cfg.o)(.data+0x5c0): undefined reference to `subtitle_autoscale'
Gui/libgui.a(opts.o)(.text+0x5ec): In function `ShowPreferences':
: undefined reference to `subtitle_font_radius'
Gui/libgui.a(opts.o)(.text+0x610): In function `ShowPreferences':
: undefined reference to `subtitle_font_thickness'
Gui/libgui.a(opts.o)(.text+0x622): In function `ShowPreferences':
: undefined reference to `text_font_scale_factor'
Gui/libgui.a(opts.o)(.text+0x63a): In function `ShowPreferences':
: undefined reference to `osd_font_scale_factor'
Gui/libgui.a(opts.o)(.text+0x652): In function `ShowPreferences':
: undefined reference to `subtitle_font_encoding'
Gui/libgui.a(opts.o)(.text+0x692): In function `ShowPreferences':
: undefined reference to `subtitle_font_encoding'
Gui/libgui.a(opts.o)(.text+0x6c2): In function `ShowPreferences':
: undefined reference to `subtitle_autoscale'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

---

### Post by arnieboy on 2005-08-18
do a :
```
sudo apt-get install mplayer-fonts
``` 
and then try compiling mplayer again.

---

### Post by pedromdsantos on 2005-08-19
[QUOTE=arnieboy]do a :
```
sudo apt-get install mplayer-fonts
``` 
and then try compiling mplayer again.[/QUOTE]


Doesn't work, and i still don't know how to solve it.

---

