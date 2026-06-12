---
title: "Issues build specrtum3d at &quot;make&quot; step"
date: 2021-03-19
forum: General Help
---

### Post by esox13 on 2021-03-19
Hello,

I hope I'm in the right section.

I'm trying to build the 3D realtime spectrum analyzer "spectrum3D", I passed the ./configure step :
```
[FONT=monospace][COLOR=#000000]configure:      ****************************************** [/COLOR]
configure:      *  Gstreamer version ...............1.0  * 
configure:      *  GTK version ....................GTK3  * 
configure:      *  SDL version.....................SDL2  * 
configure:      *  JACK support.....................YES  * 
configure:      ******************************************
[/FONT]
```
 
but make step fails :

```
[FONT=monospace][COLOR=#000000]collect2: error: ld returned 1 exit status [/COLOR]
make[2]: *** [Makefile:361 : spectrum3d] Erreur 1 
make[2] : on quitte le répertoire « /home/jean-martin/Téléchargements/spectrum3d-2.7.2/src » 
make[1]: *** [Makefile:268 : all] Erreur 2

[/FONT]
```

This is an old software (I think the last version is from 2016), but does cool stuff. If someone as ideas...

---

### Post by norobro on 2021-03-19
> **esox13 said:**
> ```
[FONT=monospace][COLOR=#000000]collect2: error: ld returned 1 exit status [/COLOR]
make[2]: *** [Makefile:361 : spectrum3d] Erreur 1 
make[2] : on quitte le répertoire « /home/jean-martin/Téléchargements/spectrum3d-2.7.2/src » 
make[1]: *** [Makefile:268 : all] Erreur 2
[/FONT]
```
Are there any errors printed before the above?

---

### Post by Impavidus on 2021-03-20
I would have expected a more specific error on the line above. ld returns an error and ld is the linker. So the preprocessor works (all header files are available), the compiler works (you get machine code), but the linker fails, which means that either the source code is incomplete or (more likely) some library functions are missing. This may happen if the application was written for an older version of the library than is installed on your system, or if it's simply in a different file than where the linker is told to expect it.

---

### Post by esox13 on 2021-03-20
> **norobro said:**
> Are there any errors printed before the above?

Nothing perticular saying 'error', here is the full print of the make (hope it's not to big, and sorry it's in french...)

```

[FONT=monospace][COLOR=#000000]make  [/COLOR]
Making all in src 
make[1] : on entre dans le répertoire « /home/jean-martin/Téléchargements/spectrum3d-2.7.2/src » 
make  all-am 
make[2] : on entre dans le répertoire « /home/jean-martin/Téléchargements/spectrum3d-2.7.2/src » 
gcc  -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/
cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pi
xbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-l
inux-gnu/glib-2.0/include   -o spectrum3d display.o events.o equalizer.o gstreamer.o main.o menu.o onclick.o preferences.o record.o scale.o typesource.o  -ljack -lGLU -lGL -lSDL2  -lgtk-3 -lgdk-3 -lpangocairo-1.0 -lpango-1.0 -lharfbuzz 
-latk-1.0 -lcairo-gobject -lcairo -lgdk_pixbuf-2.0 -lgio-2.0 -lgobject-2.0 -lglib-2.0 -lgstreamer-1.0 -lgobject-2.0 -lglib-2.0 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « X »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « Y »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:20 : définitions multiples de « newEvent »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la première f
ois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour la p
remière fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « Z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « AngleZ »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première foi
s ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « AngleH »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première foi
s ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « AngleV »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première foi
s ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « x »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:21 : définitions multiples de « bandsNumber »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la premièr
e fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « Xpointer »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première f
ois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « y_2d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois 
ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « Ypointer »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première f
ois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:34 : définitions multiples de « viewType »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:52 : défini pour la première f
ois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.c:43 : définitions multiples de « SDLwindow »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.c:46 : défini pour la première 
fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la première
 fois ici 
/usr/bin/ld : equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:5 : définitions multiples de « playing »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la premiè
re fois ici 
/usr/bin/ld : equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour l
a première fois ici 
/usr/bin/ld : equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la premi
ère fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : définitions multiples de « spect_bands »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:22 : défini pour la p
remière fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.c:34 : définitions multiples de « magnitudes »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:26 : défini pour la pr
emière fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:25 : définitions multiples de « spec_data »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:25 : défini pour la pre
mière fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:42 : définitions multiples de « source »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:33 : défini pour la premiè
re fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:20 : définitions multiples de « analyse_rt »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la pr
emière fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour l
a première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : définitions multiples de « playing »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la premi
ère fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:44 : définitions multiples de « equalizer »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:8 : défini pour la 
première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:44 : définitions multiples de « equalizer2 »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:8 : défini pour la
 première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:44 : définitions multiples de « equalizer3 »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:8 : défini pour la
 première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:44 : définitions multiples de « BP_BRfilter »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:8 : défini pour l
a première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : définitions multiples de « pose »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première
 fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : définitions multiples de « bandsNumber »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la p
remière fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : définitions multiples de « hzStep »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la premiè
re fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:24 : définitions multiples de « BPlowerFreq »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:6 : défini pour l
a première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:24 : définitions multiples de « BPupperFreq »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:6 : défini pour l
a première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la premi
ère fois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.c:38 : définitions multiples de « pScaleStart »; events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.c:39 : défini pour la première fois
 ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:6 : définitions multiples de « hzStep »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:6 : définitions multiples de « zoomFactor »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois
 ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:6 : définitions multiples de « playing »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois ic
i 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.c:38 : définitions multiples de « playButton »; events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.c:39 : défini pour la première fois 
ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:6 : définitions multiples de « pose »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la première f
ois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour la pre
mière fois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:8 : définitions multiples de « scaleSeek »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:28 : défini pour la première f
ois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:24 : définitions multiples de « colorType »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:40 : défini pour la première fois
 ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:17 : définitions multiples de « typeSource »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:35 : défini pour la première
 fois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:5 : définitions multiples de « newEvent »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la première fois i
ci 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:5 : définitions multiples de « jack »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:20 : défini pour la première fois i
ci 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:5 : définitions multiples de « analyse_rt »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la première fois
 ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour la pre
mière fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:38 : définitions multiples de « colorType »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:40 : défini pour la première fois
 ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « X »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « Y »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « Z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « AngleH »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ic
i 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « AngleV »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ic
i 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « AngleZ »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ic
i 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:20 : définitions multiples de « newEvent »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la première fois 
ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:24 : définitions multiples de « loopTestSound »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:26 : défini pour la premi
ère fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:21 : définitions multiples de « prefPath »; main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.c:37 : défini pour la première fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la première f
ois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « playing »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première 
fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:24 : définitions multiples de « spec_data »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:25 : défini pour la premièr
e fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:20 : définitions multiples de « newEvent »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la première
 fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:38 : définitions multiples de « viewType »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:52 : défini pour la première
 fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:20 : définitions multiples de « jack »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:20 : défini pour la première
 fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « X »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois i
ci 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour la 
première fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « Y »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois i
ci 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « Z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois i
ci 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « AngleH »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première f
ois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « AngleV »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première f
ois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « AngleZ »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première f
ois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:40 : définitions multiples de « loop »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:26 : défini pour la première
 fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:20 : définitions multiples de « analyse_rt »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la premiè
re fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:20 : définitions multiples de « loading »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:20 : défini pour la premi
ère fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « hzStep »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première f
ois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « bandsNumber »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la premi
ère fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « zoomFactor »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la premiè
re fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « AUDIOFREQ »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : défini pour la pre
mière fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « zoom »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première foi
s ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:22 : définitions multiples de « showGain »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:23 : défini pour la première
 fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:41 : définitions multiples de « pipeline »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:44 : défini pour la prem
ière fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:31 : définitions multiples de « typeSource »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:35 : défini pour la pr
emière fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois i
ci 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « x »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois i
ci 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « pose »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première foi
s ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la premièr
e fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/preferences.h:7 : définitions multiples de « rcFile »; menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:23 : défini pour la première 
fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour
 la première fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/preferences.h:5 : définitions multiples de « externalWindow »; menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:20 : défini pour la p
remière fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/preferences.c:30 : définitions multiples de « prefPath »; main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.c:37 : défini pour la premiè
re fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la pre
mière fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/preferences.h:14 : définitions multiples de « colorType »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:40 : défini pour la
 première fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/preferences.h:6 : définitions multiples de « policyName »; menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:21 : défini pour la premi
ère fois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:33 : définitions multiples de « typeSource »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:35 : défini pour la prem
ière fois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:21 : définitions multiples de « analyse_rt »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la première
 fois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:20 : définitions multiples de « recording »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:20 : défini pour la premi
ère fois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:21 : définitions multiples de « tmpPath »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:21 : défini pour la premièr
e fois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:21 : définitions multiples de « selected_file »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:21 : défini pour la p
remière fois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:24 : définitions multiples de « loop »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:26 : défini pour la première f
ois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:22 : définitions multiples de « pose »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois 
ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:22 : définitions multiples de « playing »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fo
is ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:31 : définitions multiples de « viewType »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:52 : défini pour la première foi
s ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour la pr
emière fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:21 : définitions multiples de « x »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:21 : définitions multiples de « y_2d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ic
i 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:20 : définitions multiples de « hzStep »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois 
ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:20 : définitions multiples de « zoom »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois ic
i 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:20 : définitions multiples de « bandsNumber »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première 
fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:20 : définitions multiples de « zoomFactor »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première f
ois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:22 : définitions multiples de « pos »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:22 : défini pour la première fois
 ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:22 : définitions multiples de « len »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:22 : défini pour la première fois
 ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:21 : définitions multiples de « x_2d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ic
i 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:24 : définitions multiples de « Xpointer »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première foi
s ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:24 : définitions multiples de « Ypointer »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première foi
s ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:20 : définitions multiples de « storedFreq »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première f
ois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « storedIntensity »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:23 : défini pour la premi
ère fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « gain »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.c:40 : défini pour la première foi
s ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « AngleZ »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois 
ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « AngleV »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois 
ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « AngleH »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois 
ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « Z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « Y »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « X »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la première 
fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:8 : définitions multiples de « pos »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:22 : défini pour la prem
ière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:9 : définitions multiples de « pipeline »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:44 : défini pour la
 première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:5 : définitions multiples de « loading »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:20 : défini pour la 
première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:8 : définitions multiples de « len »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:22 : défini pour la prem
ière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:11 : définitions multiples de « spec_data »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:25 : défini pour la p
remière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:20 : définitions multiples de « typeSource »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:35 : défini pour
 la première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:7 : définitions multiples de « playing »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la prem
ière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:5 : définitions multiples de « analyse_rt »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la p
remière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:6 : définitions multiples de « selected_file »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:21 : défini po
ur la première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la prem
ière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:7 : définitions multiples de « frame_number_counter »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : dé
fini pour la première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour 
la première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:5 : définitions multiples de « newEvent »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la pre
mière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.c:32 : définitions multiples de « timer »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.c:38 : défini pour la p
remière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:10 : définitions multiples de « loop »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:26 : défini pour la pr
emière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:7 : définitions multiples de « spect_bands »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:22 : défini pour la 
première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:6 : définitions multiples de « tmpPath »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:21 : défini pour la 
première fois ici 
collect2: error: ld returned 1 exit status 
make[2]: *** [Makefile:361 : spectrum3d] Erreur 1 
make[2] : on quitte le répertoire « /home/jean-martin/Téléchargements/spectrum3d-2.7.2/src » 
make[1]: *** [Makefile:268 : all] Erreur 2 
make[1] : on quitte le répertoire « /home/jean-martin/Téléchargements/spectrum3d-2.7.2/src » 
make: *** [Makefile:343 : all-recursive] Erreur 1


[/FONT]

```

---

### Post by norobro on 2021-03-20
Those errors are due to a change in gcc 10. One of the default CFLAGS was changed from "-fcommon" to "-fno-common".

Try the following:```
make clean
export CFLAGS="-fcommon"
./configure
make
```Or you could add "-fcommon" to the CFLAGS line in your makefile.

From the 9.3 docs: [https://gcc.gnu.org/onlinedocs/gcc-9.3.0/gcc/Code-Gen-Options.html#Code-Gen-Options](https://gcc.gnu.org/onlinedocs/gcc-9.3.0/gcc/Code-Gen-Options.html#Code-Gen-Options)> ... In the table below, only one of the forms is listed&#8212;the one that is not the default ...

-fno-common
In C code, this option controls the placement of global variables defined without an initializer, known as tentative definitions in the C standard. Tentative definitions are distinct from declarations of a variable with the extern keyword, which do not allocate storage.


Unix C compilers have traditionally allocated storage for uninitialized global variables in a common block. This allows the linker to resolve all tentative definitions of the same variable in different compilation units to the same object, or to a non-tentative definition. **This is the behavior specified by -fcommon, and is the default for GCC on most targets**. On the other hand, this behavior is not required by ISO C, and on some targets may carry a speed or code size penalty on variable references.


The -fno-common option specifies that the compiler should instead place uninitialized global variables in the BSS section of the object file. This inhibits the merging of tentative definitions by the linker so you get a multiple-definition error if the same variable is defined in more than one compilation unit. Compiling with -fno-common is useful on targets for which it provides better performance, or if you wish to verify that the program will work on other systems that always treat uninitialized variable definitions this way.
...


The 10.2 docs: [https://gcc.gnu.org/onlinedocs/gcc-10.2.0/gcc/Code-Gen-Options.html#Code-Gen-Options](https://gcc.gnu.org/onlinedocs/gcc-10.2.0/gcc/Code-Gen-Options.html#Code-Gen-Options)> 
-fcommon
In C code, this option controls the placement of global variables defined without an initializer, known as tentative definitions in the C standard. Tentative definitions are distinct from declarations of a variable with the extern keyword, which do not allocate storage.


**The default is -fno-common**, which specifies that the compiler places uninitialized global variables in the BSS section of the object file. This inhibits the merging of tentative definitions by the linker so you get a multiple-definition error if the same variable is accidentally defined in more than one compilation unit.


The -fcommon places uninitialized global variables in a common block. This allows the linker to resolve all tentative definitions of the same variable in different compilation units to the same object, or to a non-tentative definition. This behavior is inconsistent with C++, and on many targets implies a speed and code size penalty on global variable references. It is mainly useful to enable legacy code to link without errors.


---

### Post by esox13 on 2021-03-20
> **norobro said:**
> Those errors are due to a change in gcc 10. One of the default CFLAGS was changed from "-fcommon" to "-fno-common".

Try the following:```
make clean
export CFLAGS="-fcommon"
make
```Or you could add "-fcommon" to the CFLAGS line in your makefile.

From the 9.3 docs: [https://gcc.gnu.org/onlinedocs/gcc-9.3.0/gcc/Code-Gen-Options.html#Code-Gen-Options](https://gcc.gnu.org/onlinedocs/gcc-9.3.0/gcc/Code-Gen-Options.html#Code-Gen-Options)


The 10.2 docs: [https://gcc.gnu.org/onlinedocs/gcc-10.2.0/gcc/Code-Gen-Options.html#Code-Gen-Options](https://gcc.gnu.org/onlinedocs/gcc-10.2.0/gcc/Code-Gen-Options.html#Code-Gen-Options)

Thanks, seems to be different but still having errors.

```

[FONT=monospace][COLOR=#000000]make [/COLOR]
Making all in src 
make[1] : on entre dans le répertoire « /home/jean-martin/Téléchargements/spectrum3d-2.7.2/src » 
make  all-am 
make[2] : on entre dans le répertoire « /home/jean-martin/Téléchargements/spectrum3d-2.7.2/src » 
gcc -DHAVE_CONFIG_H -I.  -DDATADIR='"/usr/local/share"'   -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/includ
e/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/fr
eetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-
linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -MT display.o -MD -MP -MF .deps/display.Tpo -c -o display.o display.c 
mv -f .deps/display.Tpo .deps/display.Po 
gcc -DHAVE_CONFIG_H -I.  -DDATADIR='"/usr/local/share"'   -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/includ
e/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/fr
eetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-
linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -MT events.o -MD -MP -MF .deps/events.Tpo -c -o events.o events.c 
mv -f .deps/events.Tpo .deps/events.Po 
gcc -DHAVE_CONFIG_H -I.  -DDATADIR='"/usr/local/share"'   -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/includ
e/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/fr
eetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-
linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -MT equalizer.o -MD -MP -MF .deps/equalizer.Tpo -c -o equalizer.o equalizer.c 
mv -f .deps/equalizer.Tpo .deps/equalizer.Po 
gcc -DHAVE_CONFIG_H -I.  -DDATADIR='"/usr/local/share"'   -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/includ
e/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/fr
eetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-
linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -MT gstreamer.o -MD -MP -MF .deps/gstreamer.Tpo -c -o gstreamer.o gstreamer.c 
mv -f .deps/gstreamer.Tpo .deps/gstreamer.Po 
gcc -DHAVE_CONFIG_H -I.  -DDATADIR='"/usr/local/share"'   -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/includ
e/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/fr
eetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-
linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c 
mv -f .deps/main.Tpo .deps/main.Po 
gcc -DHAVE_CONFIG_H -I.  -DDATADIR='"/usr/local/share"'   -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/includ
e/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/fr
eetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-
linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -MT menu.o -MD -MP -MF .deps/menu.Tpo -c -o menu.o menu.c 
mv -f .deps/menu.Tpo .deps/menu.Po 
gcc -DHAVE_CONFIG_H -I.  -DDATADIR='"/usr/local/share"'   -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/includ
e/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/fr
eetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-
linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -MT onclick.o -MD -MP -MF .deps/onclick.Tpo -c -o onclick.o onclick.c 
mv -f .deps/onclick.Tpo .deps/onclick.Po 
gcc -DHAVE_CONFIG_H -I.  -DDATADIR='"/usr/local/share"'   -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/includ
e/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/fr
eetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-
linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -MT preferences.o -MD -MP -MF .deps/preferences.Tpo -c -o preferences.o preferences.c 
mv -f .deps/preferences.Tpo .deps/preferences.Po 
gcc -DHAVE_CONFIG_H -I.  -DDATADIR='"/usr/local/share"'   -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/includ
e/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/fr
eetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-
linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -MT record.o -MD -MP -MF .deps/record.Tpo -c -o record.o record.c 
mv -f .deps/record.Tpo .deps/record.Po 
gcc -DHAVE_CONFIG_H -I.  -DDATADIR='"/usr/local/share"'   -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/includ
e/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/fr
eetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-
linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -MT scale.o -MD -MP -MF .deps/scale.Tpo -c -o scale.o scale.c 
mv -f .deps/scale.Tpo .deps/scale.Po 
gcc -DHAVE_CONFIG_H -I.  -DDATADIR='"/usr/local/share"'   -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/includ
e/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/fr
eetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-
linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -MT typesource.o -MD -MP -MF .deps/typesource.Tpo -c -o typesource.o typesource.c 
mv -f .deps/typesource.Tpo .deps/typesource.Po 
gcc  -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/
cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pi
xbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-l
inux-gnu/glib-2.0/include   -o spectrum3d display.o events.o equalizer.o gstreamer.o main.o menu.o onclick.o preferences.o record.o scale.o typesource.o  -ljack -lGLU -lGL -lSDL2  -lgtk-3 -lgdk-3 -lpangocairo-1.0 -lpango-1.0 -lharfbuzz 
-latk-1.0 -lcairo-gobject -lcairo -lgdk_pixbuf-2.0 -lgio-2.0 -lgobject-2.0 -lglib-2.0 -lgstreamer-1.0 -lgobject-2.0 -lglib-2.0 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « X »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « Y »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:20 : définitions multiples de « newEvent »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la première f
ois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour la p
remière fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « Z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « AngleZ »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première foi
s ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « AngleH »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première foi
s ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « AngleV »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première foi
s ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « x »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:21 : définitions multiples de « bandsNumber »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la premièr
e fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « Xpointer »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première f
ois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « y_2d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois 
ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:22 : définitions multiples de « Ypointer »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première f
ois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.h:34 : définitions multiples de « viewType »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:52 : défini pour la première f
ois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.c:43 : définitions multiples de « SDLwindow »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.c:46 : défini pour la première 
fois ici 
/usr/bin/ld : events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la première
 fois ici 
/usr/bin/ld : equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:5 : définitions multiples de « playing »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la premiè
re fois ici 
/usr/bin/ld : equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour l
a première fois ici 
/usr/bin/ld : equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la premi
ère fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : définitions multiples de « spect_bands »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:22 : défini pour la p
remière fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.c:34 : définitions multiples de « magnitudes »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:26 : défini pour la pr
emière fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:25 : définitions multiples de « spec_data »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:25 : défini pour la pre
mière fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:42 : définitions multiples de « source »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:33 : défini pour la premiè
re fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:20 : définitions multiples de « analyse_rt »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la pr
emière fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour l
a première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : définitions multiples de « playing »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la premi
ère fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:44 : définitions multiples de « equalizer »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:8 : défini pour la 
première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:44 : définitions multiples de « equalizer2 »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:8 : défini pour la
 première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:44 : définitions multiples de « equalizer3 »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:8 : défini pour la
 première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:44 : définitions multiples de « BP_BRfilter »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:8 : défini pour l
a première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : définitions multiples de « pose »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première
 fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : définitions multiples de « bandsNumber »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la p
remière fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : définitions multiples de « hzStep »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la premiè
re fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:24 : définitions multiples de « BPlowerFreq »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:6 : défini pour l
a première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:24 : définitions multiples de « BPupperFreq »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.h:6 : défini pour l
a première fois ici 
/usr/bin/ld : gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la premi
ère fois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.c:38 : définitions multiples de « pScaleStart »; events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.c:39 : défini pour la première fois
 ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:6 : définitions multiples de « hzStep »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:6 : définitions multiples de « zoomFactor »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois
 ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:6 : définitions multiples de « playing »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois ic
i 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.c:38 : définitions multiples de « playButton »; events.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/events.c:39 : défini pour la première fois 
ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:6 : définitions multiples de « pose »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la première f
ois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour la pre
mière fois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:8 : définitions multiples de « scaleSeek »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:28 : défini pour la première f
ois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:24 : définitions multiples de « colorType »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:40 : défini pour la première fois
 ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:17 : définitions multiples de « typeSource »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:35 : défini pour la première
 fois ici 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:5 : définitions multiples de « newEvent »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la première fois i
ci 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:5 : définitions multiples de « jack »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:20 : défini pour la première fois i
ci 
/usr/bin/ld : main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.h:5 : définitions multiples de « analyse_rt »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la première fois
 ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour la pre
mière fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:38 : définitions multiples de « colorType »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:40 : défini pour la première fois
 ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « X »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « Y »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « Z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « AngleH »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ic
i 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « AngleV »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ic
i 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:22 : définitions multiples de « AngleZ »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ic
i 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:20 : définitions multiples de « newEvent »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la première fois 
ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:24 : définitions multiples de « loopTestSound »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:26 : défini pour la premi
ère fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:21 : définitions multiples de « prefPath »; main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.c:37 : défini pour la première fois ici 
/usr/bin/ld : menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la première f
ois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « playing »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première 
fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:24 : définitions multiples de « spec_data »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:25 : défini pour la premièr
e fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:20 : définitions multiples de « newEvent »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la première
 fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:38 : définitions multiples de « viewType »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:52 : défini pour la première
 fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:20 : définitions multiples de « jack »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:20 : défini pour la première
 fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « X »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois i
ci 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour la 
première fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « Y »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois i
ci 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « Z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois i
ci 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « AngleH »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première f
ois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « AngleV »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première f
ois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « AngleZ »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première f
ois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:40 : définitions multiples de « loop »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:26 : défini pour la première
 fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:20 : définitions multiples de « analyse_rt »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la premiè
re fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:20 : définitions multiples de « loading »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:20 : défini pour la premi
ère fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « hzStep »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première f
ois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « bandsNumber »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la premi
ère fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « zoomFactor »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la premiè
re fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « AUDIOFREQ »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : défini pour la pre
mière fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « zoom »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première foi
s ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:22 : définitions multiples de « showGain »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:23 : défini pour la première
 fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:41 : définitions multiples de « pipeline »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:44 : défini pour la prem
ière fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:31 : définitions multiples de « typeSource »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:35 : défini pour la pr
emière fois ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois i
ci 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:23 : définitions multiples de « x »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois i
ci 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/onclick.h:21 : définitions multiples de « pose »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première foi
s ici 
/usr/bin/ld : onclick.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la premièr
e fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/preferences.h:7 : définitions multiples de « rcFile »; menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:23 : défini pour la première 
fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour
 la première fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/preferences.h:5 : définitions multiples de « externalWindow »; menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:20 : défini pour la p
remière fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/preferences.c:30 : définitions multiples de « prefPath »; main.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/main.c:37 : défini pour la premiè
re fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la pre
mière fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/preferences.h:14 : définitions multiples de « colorType »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:40 : défini pour la
 première fois ici 
/usr/bin/ld : preferences.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/preferences.h:6 : définitions multiples de « policyName »; menu.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/menu.h:21 : défini pour la premi
ère fois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:33 : définitions multiples de « typeSource »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:35 : défini pour la prem
ière fois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:21 : définitions multiples de « analyse_rt »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la première
 fois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:20 : définitions multiples de « recording »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:20 : défini pour la premi
ère fois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:21 : définitions multiples de « tmpPath »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:21 : défini pour la premièr
e fois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:21 : définitions multiples de « selected_file »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:21 : défini pour la p
remière fois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:24 : définitions multiples de « loop »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:26 : défini pour la première f
ois ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:22 : définitions multiples de « pose »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois 
ici 
/usr/bin/ld : record.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/record.h:22 : définitions multiples de « playing »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fo
is ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:31 : définitions multiples de « viewType »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:52 : défini pour la première foi
s ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour la pr
emière fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:21 : définitions multiples de « x »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:21 : définitions multiples de « y_2d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ic
i 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:20 : définitions multiples de « hzStep »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois 
ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:20 : définitions multiples de « zoom »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première fois ic
i 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:20 : définitions multiples de « bandsNumber »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première 
fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:20 : définitions multiples de « zoomFactor »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première f
ois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:22 : définitions multiples de « pos »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:22 : défini pour la première fois
 ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:22 : définitions multiples de « len »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:22 : défini pour la première fois
 ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:21 : définitions multiples de « x_2d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ic
i 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:24 : définitions multiples de « Xpointer »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première foi
s ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:24 : définitions multiples de « Ypointer »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première foi
s ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:20 : définitions multiples de « storedFreq »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la première f
ois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « storedIntensity »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:23 : défini pour la premi
ère fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « gain »; equalizer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/equalizer.c:40 : défini pour la première foi
s ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « AngleZ »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois 
ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « AngleV »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois 
ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « AngleH »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois 
ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « Z »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « Y »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/scale.h:23 : définitions multiples de « X »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:24 : défini pour la première fois ici 
/usr/bin/ld : scale.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la première 
fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:8 : définitions multiples de « pos »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:22 : défini pour la prem
ière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:9 : définitions multiples de « pipeline »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:44 : défini pour la
 première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:5 : définitions multiples de « loading »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:20 : défini pour la 
première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:8 : définitions multiples de « len »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:22 : défini pour la prem
ière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:11 : définitions multiples de « spec_data »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:25 : défini pour la p
remière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:20 : définitions multiples de « typeSource »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:35 : défini pour
 la première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:7 : définitions multiples de « playing »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:21 : défini pour la prem
ière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:5 : définitions multiples de « analyse_rt »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la p
remière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:6 : définitions multiples de « selected_file »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:21 : défini po
ur la première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : définitions multiples de « debug »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:5 : défini pour la prem
ière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:7 : définitions multiples de « frame_number_counter »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:23 : dé
fini pour la première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : définitions multiples de « spectrum3d »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/spectrum3d.h:65 : défini pour 
la première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:5 : définitions multiples de « newEvent »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:20 : défini pour la pre
mière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.c:32 : définitions multiples de « timer »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.c:38 : défini pour la p
remière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:10 : définitions multiples de « loop »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:26 : défini pour la pr
emière fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:7 : définitions multiples de « spect_bands »; display.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/display.h:22 : défini pour la 
première fois ici 
/usr/bin/ld : typesource.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/typesource.h:6 : définitions multiples de « tmpPath »; gstreamer.o:/home/jean-martin/Téléchargements/spectrum3d-2.7.2/src/gstreamer.h:21 : défini pour la 
première fois ici 
collect2: error: ld returned 1 exit status 
make[2]: *** [Makefile:361 : spectrum3d] Erreur 1 
make[2] : on quitte le répertoire « /home/jean-martin/Téléchargements/spectrum3d-2.7.2/src » 
make[1]: *** [Makefile:268 : all] Erreur 2 
make[1] : on quitte le répertoire « /home/jean-martin/Téléchargements/spectrum3d-2.7.2/src » 
make: *** [Makefile:343 : all-recursive] Erreur 1
[/FONT]

```

The makefile

```

# Makefile.in generated by automake 1.15 from Makefile.am.
# Makefile.  Generated from Makefile.in by configure.

# Copyright (C) 1994-2014 Free Software Foundation, Inc.

# This Makefile.in is free software; the Free Software Foundation
# gives unlimited permission to copy and/or distribute it,
# with or without modifications, as long as this notice is preserved.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY, to the extent permitted by law; without
# even the implied warranty of MERCHANTABILITY or FITNESS FOR A
# PARTICULAR PURPOSE.



am__is_gnu_make = { \
  if test -z '$(MAKELEVEL)'; then \
    false; \
  elif test -n '$(MAKE_HOST)'; then \
    true; \
  elif test -n '$(MAKE_VERSION)' && test -n '$(CURDIR)'; then \
    true; \
  else \
    false; \
  fi; \
}
am__make_running_with_option = \
  case $${target_option-} in \
      ?) ;; \
      *) echo "am__make_running_with_option: internal error: invalid" \
              "target option '$${target_option-}' specified" >&2; \
         exit 1;; \
  esac; \
  has_opt=no; \
  sane_makeflags=$$MAKEFLAGS; \
  if $(am__is_gnu_make); then \
    sane_makeflags=$$MFLAGS; \
  else \
    case $$MAKEFLAGS in \
      *\\[\ \    ]*) \
        bs=\\; \
        sane_makeflags=`printf '%s\n' "$$MAKEFLAGS" \
          | sed "s/$$bs$$bs[$$bs $$bs    ]*//g"`;; \
    esac; \
  fi; \
  skip_next=no; \
  strip_trailopt () \
  { \
    flg=`printf '%s\n' "$$flg" | sed "s/$$1.*$$//"`; \
  }; \
  for flg in $$sane_makeflags; do \
    test $$skip_next = yes && { skip_next=no; continue; }; \
    case $$flg in \
      *=*|--*) continue;; \
        -*I) strip_trailopt 'I'; skip_next=yes;; \
      -*I?*) strip_trailopt 'I';; \
        -*O) strip_trailopt 'O'; skip_next=yes;; \
      -*O?*) strip_trailopt 'O';; \
        -*l) strip_trailopt 'l'; skip_next=yes;; \
      -*l?*) strip_trailopt 'l';; \
      -[dEDm]) skip_next=yes;; \
      -[JT]) skip_next=yes;; \
    esac; \
    case $$flg in \
      *$$target_option*) has_opt=yes; break;; \
    esac; \
  done; \
  test $$has_opt = yes
am__make_dryrun = (target_option=n; $(am__make_running_with_option))
am__make_keepgoing = (target_option=k; $(am__make_running_with_option))
pkgdatadir = $(datadir)/spectrum3d
pkgincludedir = $(includedir)/spectrum3d
pkglibdir = $(libdir)/spectrum3d
pkglibexecdir = $(libexecdir)/spectrum3d
am__cd = CDPATH="$${ZSH_VERSION+.}$(PATH_SEPARATOR)" && cd
install_sh_DATA = $(install_sh) -c -m 644
install_sh_PROGRAM = $(install_sh) -c
install_sh_SCRIPT = $(install_sh) -c
INSTALL_HEADER = $(INSTALL_DATA)
transform = $(program_transform_name)
NORMAL_INSTALL = :
PRE_INSTALL = :
POST_INSTALL = :
NORMAL_UNINSTALL = :
PRE_UNINSTALL = :
POST_UNINSTALL = :
subdir = .
ACLOCAL_M4 = $(top_srcdir)/aclocal.m4
am__aclocal_m4_deps = $(top_srcdir)/configure.ac
am__configure_deps = $(am__aclocal_m4_deps) $(CONFIGURE_DEPENDENCIES) \
    $(ACLOCAL_M4)
DIST_COMMON = $(srcdir)/Makefile.am $(top_srcdir)/configure \
    $(am__configure_deps) $(am__DIST_COMMON)
am__CONFIG_DISTCLEAN_FILES = config.status config.cache config.log \
 configure.lineno config.status.lineno
mkinstalldirs = $(install_sh) -d
CONFIG_HEADER = $(top_builddir)/src/config.h
CONFIG_CLEAN_FILES =
CONFIG_CLEAN_VPATH_FILES =
AM_V_P = $(am__v_P_$(V))
am__v_P_ = $(am__v_P_$(AM_DEFAULT_VERBOSITY))
am__v_P_0 = false
am__v_P_1 = :
AM_V_GEN = $(am__v_GEN_$(V))
am__v_GEN_ = $(am__v_GEN_$(AM_DEFAULT_VERBOSITY))
am__v_GEN_0 = @echo "  GEN     " $@;
am__v_GEN_1 =
AM_V_at = $(am__v_at_$(V))
am__v_at_ = $(am__v_at_$(AM_DEFAULT_VERBOSITY))
am__v_at_0 = @
am__v_at_1 =
SOURCES =
DIST_SOURCES =
RECURSIVE_TARGETS = all-recursive check-recursive cscopelist-recursive \
    ctags-recursive dvi-recursive html-recursive info-recursive \
    install-data-recursive install-dvi-recursive \
    install-exec-recursive install-html-recursive \
    install-info-recursive install-pdf-recursive \
    install-ps-recursive install-recursive installcheck-recursive \
    installdirs-recursive pdf-recursive ps-recursive \
    tags-recursive uninstall-recursive
am__can_run_installinfo = \
  case $$AM_UPDATE_INFO_DIR in \
    n|no|NO) false;; \
    *) (install-info --version) >/dev/null 2>&1;; \
  esac
RECURSIVE_CLEAN_TARGETS = mostlyclean-recursive clean-recursive    \
  distclean-recursive maintainer-clean-recursive
am__recursive_targets = \
  $(RECURSIVE_TARGETS) \
  $(RECURSIVE_CLEAN_TARGETS) \
  $(am__extra_recursive_targets)
AM_RECURSIVE_TARGETS = $(am__recursive_targets:-recursive=) TAGS CTAGS \
    cscope distdir dist dist-all distcheck
am__tagged_files = $(HEADERS) $(SOURCES) $(TAGS_FILES) $(LISP)
# Read a list of newline-separated strings from the standard input,
# and print each of them once, without duplicates.  Input order is
# *not* preserved.
am__uniquify_input = $(AWK) '\
  BEGIN { nonempty = 0; } \
  { items[$$0] = 1; nonempty = 1; } \
  END { if (nonempty) { for (i in items) print i; }; } \
'
# Make sure the list of sources is unique.  This is necessary because,
# e.g., the same source file might be shared among _SOURCES variables
# for different programs/libraries.
am__define_uniq_tagged_files = \
  list='$(am__tagged_files)'; \
  unique=`for i in $$list; do \
    if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
  done | $(am__uniquify_input)`
ETAGS = etags
CTAGS = ctags
CSCOPE = cscope
DIST_SUBDIRS = $(SUBDIRS)
am__DIST_COMMON = $(srcdir)/Makefile.in AUTHORS COPYING ChangeLog \
    INSTALL NEWS README compile depcomp install-sh missing
DISTFILES = $(DIST_COMMON) $(DIST_SOURCES) $(TEXINFOS) $(EXTRA_DIST)
distdir = $(PACKAGE)-$(VERSION)
top_distdir = $(distdir)
am__remove_distdir = \
  if test -d "$(distdir)"; then \
    find "$(distdir)" -type d ! -perm -200 -exec chmod u+w {} ';' \
      && rm -rf "$(distdir)" \
      || { sleep 5 && rm -rf "$(distdir)"; }; \
  else :; fi
am__post_remove_distdir = $(am__remove_distdir)
am__relativize = \
  dir0=`pwd`; \
  sed_first='s,^\([^/]*\)/.*$$,\1,'; \
  sed_rest='s,^[^/]*/*,,'; \
  sed_last='s,^.*/\([^/]*\)$$,\1,'; \
  sed_butlast='s,/*[^/]*$$,,'; \
  while test -n "$$dir1"; do \
    first=`echo "$$dir1" | sed -e "$$sed_first"`; \
    if test "$$first" != "."; then \
      if test "$$first" = ".."; then \
        dir2=`echo "$$dir0" | sed -e "$$sed_last"`/"$$dir2"; \
        dir0=`echo "$$dir0" | sed -e "$$sed_butlast"`; \
      else \
        first2=`echo "$$dir2" | sed -e "$$sed_first"`; \
        if test "$$first2" = "$$first"; then \
          dir2=`echo "$$dir2" | sed -e "$$sed_rest"`; \
        else \
          dir2="../$$dir2"; \
        fi; \
        dir0="$$dir0"/"$$first"; \
      fi; \
    fi; \
    dir1=`echo "$$dir1" | sed -e "$$sed_rest"`; \
  done; \
  reldir="$$dir2"
DIST_ARCHIVES = $(distdir).tar.gz
GZIP_ENV = --best
DIST_TARGETS = dist-gzip
distuninstallcheck_listfiles = find . -type f -print
am__distuninstallcheck_listfiles = $(distuninstallcheck_listfiles) \
  | sed 's|^\./|$(prefix)/|' | grep -v '$(infodir)/dir$$'
distcleancheck_listfiles = find . -type f -print
ACLOCAL = aclocal-1.15
AMTAR = $${TAR-tar}
AM_DEFAULT_VERBOSITY = 1
AUTOCONF = autoconf
AUTOHEADER = autoheader
AUTOMAKE = automake-1.15
AWK = gawk
CC = gcc
CCDEPMODE = depmode=gcc3
CFLAGS = -g -O2 -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -fcommon
CPP = gcc -E
CPPFLAGS =
CYGPATH_W = echo
DEFS = -DHAVE_CONFIG_H
DEPDIR = .deps
ECHO_C =
ECHO_N = -n
ECHO_T =
EGREP = /usr/bin/grep -E
EXEEXT =
GREP = /usr/bin/grep
GSTREAMER_CFLAGS = -pthread -I/usr/include/gstreamer-1.0 -I/usr/include/x86_64-linux-gnu -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include
GSTREAMER_LIBS = -lgstreamer-1.0 -lgobject-2.0 -lglib-2.0
GTK2_CFLAGS =
GTK2_LIBS =
GTK3_CFLAGS = -pthread -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/gtk-3.0 -I/usr/include/gio-unix-2.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/harfbuzz -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/uuid -I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include
GTK3_LIBS = -lgtk-3 -lgdk-3 -lpangocairo-1.0 -lpango-1.0 -lharfbuzz -latk-1.0 -lcairo-gobject -lcairo -lgdk_pixbuf-2.0 -lgio-2.0 -lgobject-2.0 -lglib-2.0
INSTALL = /usr/bin/install -c
INSTALL_DATA = ${INSTALL} -m 644
INSTALL_PROGRAM = ${INSTALL}
INSTALL_SCRIPT = ${INSTALL}
INSTALL_STRIP_PROGRAM = $(install_sh) -c -s
LDFLAGS =
LIBOBJS =
LIBS = -ljack -lGLU -lGL -lSDL2  -lgtk-3 -lgdk-3 -lpangocairo-1.0 -lpango-1.0 -lharfbuzz -latk-1.0 -lcairo-gobject -lcairo -lgdk_pixbuf-2.0 -lgio-2.0 -lgobject-2.0 -lglib-2.0 -lgstreamer-1.0 -lgobject-2.0 -lglib-2.0
LTLIBOBJS =
MAKEINFO = makeinfo
MKDIR_P = /usr/bin/mkdir -p
OBJEXT = o
PACKAGE = spectrum3d
PACKAGE_BUGREPORT = nadaeck@hotmail.com
PACKAGE_NAME = Spectrum3d
PACKAGE_STRING = Spectrum3d 2.7.2
PACKAGE_TARNAME = spectrum3d
PACKAGE_URL = https://sourceforge.net/projects/spectrum3d/
PACKAGE_VERSION = 2.7.2
PATH_SEPARATOR = :
PKG_CONFIG = /usr/bin/pkg-config
PKG_CONFIG_LIBDIR =
PKG_CONFIG_PATH =
SET_MAKE =
SHELL = /bin/bash
STRIP =
VERSION = 2.7.2
abs_builddir = /home/jean-martin/Téléchargements/spectrum3d-2.7.2
abs_srcdir = /home/jean-martin/Téléchargements/spectrum3d-2.7.2
abs_top_builddir = /home/jean-martin/Téléchargements/spectrum3d-2.7.2
abs_top_srcdir = /home/jean-martin/Téléchargements/spectrum3d-2.7.2
ac_ct_CC = gcc
am__include = include
am__leading_dot = .
am__quote =
am__tar = $${TAR-tar} chof - "$$tardir"
am__untar = $${TAR-tar} xf -
bindir = ${exec_prefix}/bin
build_alias =
builddir = .
datadir = ${datarootdir}
datarootdir = ${prefix}/share
docdir = ${datarootdir}/doc/${PACKAGE_TARNAME}
dvidir = ${docdir}
exec_prefix = ${prefix}
host_alias =
htmldir = ${docdir}
includedir = ${prefix}/include
infodir = ${datarootdir}/info
install_sh = ${SHELL} /home/jean-martin/Téléchargements/spectrum3d-2.7.2/install-sh
libdir = ${exec_prefix}/lib
libexecdir = ${exec_prefix}/libexec
localedir = ${datarootdir}/locale
localstatedir = ${prefix}/var
mandir = ${datarootdir}/man
mkdir_p = $(MKDIR_P)
oldincludedir = /usr/include
pdfdir = ${docdir}
prefix = /usr/local
program_transform_name = s,x,x,
psdir = ${docdir}
runstatedir = ${localstatedir}/run
sbindir = ${exec_prefix}/sbin
sharedstatedir = ${prefix}/com
srcdir = .
sysconfdir = ${prefix}/etc
target_alias =
top_build_prefix =
top_builddir = .
top_srcdir = .
SUBDIRS = src data doc
all: all-recursive

.SUFFIXES:
am--refresh: Makefile
    @:
$(srcdir)/Makefile.in:  $(srcdir)/Makefile.am  $(am__configure_deps)
    @for dep in $?; do \
      case '$(am__configure_deps)' in \
        *$$dep*) \
          echo ' cd $(srcdir) && $(AUTOMAKE) --gnu'; \
          $(am__cd) $(srcdir) && $(AUTOMAKE) --gnu \
        && exit 0; \
          exit 1;; \
      esac; \
    done; \
    echo ' cd $(top_srcdir) && $(AUTOMAKE) --gnu Makefile'; \
    $(am__cd) $(top_srcdir) && \
      $(AUTOMAKE) --gnu Makefile
Makefile: $(srcdir)/Makefile.in $(top_builddir)/config.status
    @case '$?' in \
      *config.status*) \
        echo ' $(SHELL) ./config.status'; \
        $(SHELL) ./config.status;; \
      *) \
        echo ' cd $(top_builddir) && $(SHELL) ./config.status $@ $(am__depfiles_maybe)'; \
        cd $(top_builddir) && $(SHELL) ./config.status $@ $(am__depfiles_maybe);; \
    esac;

$(top_builddir)/config.status: $(top_srcdir)/configure $(CONFIG_STATUS_DEPENDENCIES)
    $(SHELL) ./config.status --recheck

$(top_srcdir)/configure:  $(am__configure_deps)
    $(am__cd) $(srcdir) && $(AUTOCONF)
$(ACLOCAL_M4):  $(am__aclocal_m4_deps)
    $(am__cd) $(srcdir) && $(ACLOCAL) $(ACLOCAL_AMFLAGS)
$(am__aclocal_m4_deps):

# This directory's subdirectories are mostly independent; you can cd
# into them and run 'make' without going through this Makefile.
# To change the values of 'make' variables: instead of editing Makefiles,
# (1) if the variable is set in 'config.status', edit 'config.status'
#     (which will cause the Makefiles to be regenerated when you run 'make');
# (2) otherwise, pass the desired values on the 'make' command line.
$(am__recursive_targets):
    @fail=; \
    if $(am__make_keepgoing); then \
      failcom='fail=yes'; \
    else \
      failcom='exit 1'; \
    fi; \
    dot_seen=no; \
    target=`echo $@ | sed s/-recursive//`; \
    case "$@" in \
      distclean-* | maintainer-clean-*) list='$(DIST_SUBDIRS)' ;; \
      *) list='$(SUBDIRS)' ;; \
    esac; \
    for subdir in $$list; do \
      echo "Making $$target in $$subdir"; \
      if test "$$subdir" = "."; then \
        dot_seen=yes; \
        local_target="$$target-am"; \
      else \
        local_target="$$target"; \
      fi; \
      ($(am__cd) $$subdir && $(MAKE) $(AM_MAKEFLAGS) $$local_target) \
      || eval $$failcom; \
    done; \
    if test "$$dot_seen" = "no"; then \
      $(MAKE) $(AM_MAKEFLAGS) "$$target-am" || exit 1; \
    fi; test -z "$$fail"

ID: $(am__tagged_files)
    $(am__define_uniq_tagged_files); mkid -fID $$unique
tags: tags-recursive
TAGS: tags

tags-am: $(TAGS_DEPENDENCIES) $(am__tagged_files)
    set x; \
    here=`pwd`; \
    if ($(ETAGS) --etags-include --version) >/dev/null 2>&1; then \
      include_option=--etags-include; \
      empty_fix=.; \
    else \
      include_option=--include; \
      empty_fix=; \
    fi; \
    list='$(SUBDIRS)'; for subdir in $$list; do \
      if test "$$subdir" = .; then :; else \
        test ! -f $$subdir/TAGS || \
          set "$$@" "$$include_option=$$here/$$subdir/TAGS"; \
      fi; \
    done; \
    $(am__define_uniq_tagged_files); \
    shift; \
    if test -z "$(ETAGS_ARGS)$$*$$unique"; then :; else \
      test -n "$$unique" || unique=$$empty_fix; \
      if test $$# -gt 0; then \
        $(ETAGS) $(ETAGSFLAGS) $(AM_ETAGSFLAGS) $(ETAGS_ARGS) \
          "$$@" $$unique; \
      else \
        $(ETAGS) $(ETAGSFLAGS) $(AM_ETAGSFLAGS) $(ETAGS_ARGS) \
          $$unique; \
      fi; \
    fi
ctags: ctags-recursive

CTAGS: ctags
ctags-am: $(TAGS_DEPENDENCIES) $(am__tagged_files)
    $(am__define_uniq_tagged_files); \
    test -z "$(CTAGS_ARGS)$$unique" \
      || $(CTAGS) $(CTAGSFLAGS) $(AM_CTAGSFLAGS) $(CTAGS_ARGS) \
         $$unique

GTAGS:
    here=`$(am__cd) $(top_builddir) && pwd` \
      && $(am__cd) $(top_srcdir) \
      && gtags -i $(GTAGS_ARGS) "$$here"
cscope: cscope.files
    test ! -s cscope.files \
      || $(CSCOPE) -b -q $(AM_CSCOPEFLAGS) $(CSCOPEFLAGS) -i cscope.files $(CSCOPE_ARGS)
clean-cscope:
    -rm -f cscope.files
cscope.files: clean-cscope cscopelist
cscopelist: cscopelist-recursive

cscopelist-am: $(am__tagged_files)
    list='$(am__tagged_files)'; \
    case "$(srcdir)" in \
      [\\/]* | ?:[\\/]*) sdir="$(srcdir)" ;; \
      *) sdir=$(subdir)/$(srcdir) ;; \
    esac; \
    for i in $$list; do \
      if test -f "$$i"; then \
        echo "$(subdir)/$$i"; \
      else \
        echo "$$sdir/$$i"; \
      fi; \
    done >> $(top_builddir)/cscope.files

distclean-tags:
    -rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags
    -rm -f cscope.out cscope.in.out cscope.po.out cscope.files

distdir: $(DISTFILES)
    $(am__remove_distdir)
    test -d "$(distdir)" || mkdir "$(distdir)"
    @srcdirstrip=`echo "$(srcdir)" | sed 's/[].[^$$\\*]/\\\\&/g'`; \
    topsrcdirstrip=`echo "$(top_srcdir)" | sed 's/[].[^$$\\*]/\\\\&/g'`; \
    list='$(DISTFILES)'; \
      dist_files=`for file in $$list; do echo $$file; done | \
      sed -e "s|^$$srcdirstrip/||;t" \
          -e "s|^$$topsrcdirstrip/|$(top_builddir)/|;t"`; \
    case $$dist_files in \
      */*) $(MKDIR_P) `echo "$$dist_files" | \
               sed '/\//!d;s|^|$(distdir)/|;s,/[^/]*$$,,' | \
               sort -u` ;; \
    esac; \
    for file in $$dist_files; do \
      if test -f $$file || test -d $$file; then d=.; else d=$(srcdir); fi; \
      if test -d $$d/$$file; then \
        dir=`echo "/$$file" | sed -e 's,/[^/]*$$,,'`; \
        if test -d "$(distdir)/$$file"; then \
          find "$(distdir)/$$file" -type d ! -perm -700 -exec chmod u+rwx {} \;; \
        fi; \
        if test -d $(srcdir)/$$file && test $$d != $(srcdir); then \
          cp -fpR $(srcdir)/$$file "$(distdir)$$dir" || exit 1; \
          find "$(distdir)/$$file" -type d ! -perm -700 -exec chmod u+rwx {} \;; \
        fi; \
        cp -fpR $$d/$$file "$(distdir)$$dir" || exit 1; \
      else \
        test -f "$(distdir)/$$file" \
        || cp -p $$d/$$file "$(distdir)/$$file" \
        || exit 1; \
      fi; \
    done
    @list='$(DIST_SUBDIRS)'; for subdir in $$list; do \
      if test "$$subdir" = .; then :; else \
        $(am__make_dryrun) \
          || test -d "$(distdir)/$$subdir" \
          || $(MKDIR_P) "$(distdir)/$$subdir" \
          || exit 1; \
        dir1=$$subdir; dir2="$(distdir)/$$subdir"; \
        $(am__relativize); \
        new_distdir=$$reldir; \
        dir1=$$subdir; dir2="$(top_distdir)"; \
        $(am__relativize); \
        new_top_distdir=$$reldir; \
        echo " (cd $$subdir && $(MAKE) $(AM_MAKEFLAGS) top_distdir="$$new_top_distdir" distdir="$$new_distdir" \\"; \
        echo "     am__remove_distdir=: am__skip_length_check=: am__skip_mode_fix=: distdir)"; \
        ($(am__cd) $$subdir && \
          $(MAKE) $(AM_MAKEFLAGS) \
            top_distdir="$$new_top_distdir" \
            distdir="$$new_distdir" \
        am__remove_distdir=: \
        am__skip_length_check=: \
        am__skip_mode_fix=: \
            distdir) \
          || exit 1; \
      fi; \
    done
    -test -n "$(am__skip_mode_fix)" \
    || find "$(distdir)" -type d ! -perm -755 \
        -exec chmod u+rwx,go+rx {} \; -o \
      ! -type d ! -perm -444 -links 1 -exec chmod a+r {} \; -o \
      ! -type d ! -perm -400 -exec chmod a+r {} \; -o \
      ! -type d ! -perm -444 -exec $(install_sh) -c -m a+r {} {} \; \
    || chmod -R a+r "$(distdir)"
dist-gzip: distdir
    tardir=$(distdir) && $(am__tar) | GZIP=$(GZIP_ENV) gzip -c >$(distdir).tar.gz
    $(am__post_remove_distdir)

dist-bzip2: distdir
    tardir=$(distdir) && $(am__tar) | BZIP2=$${BZIP2--9} bzip2 -c >$(distdir).tar.bz2
    $(am__post_remove_distdir)

dist-lzip: distdir
    tardir=$(distdir) && $(am__tar) | lzip -c $${LZIP_OPT--9} >$(distdir).tar.lz
    $(am__post_remove_distdir)

dist-xz: distdir
    tardir=$(distdir) && $(am__tar) | XZ_OPT=$${XZ_OPT--e} xz -c >$(distdir).tar.xz
    $(am__post_remove_distdir)

dist-tarZ: distdir
    @echo WARNING: "Support for distribution archives compressed with" \
               "legacy program 'compress' is deprecated." >&2
    @echo WARNING: "It will be removed altogether in Automake 2.0" >&2
    tardir=$(distdir) && $(am__tar) | compress -c >$(distdir).tar.Z
    $(am__post_remove_distdir)

dist-shar: distdir
    @echo WARNING: "Support for shar distribution archives is" \
                   "deprecated." >&2
    @echo WARNING: "It will be removed altogether in Automake 2.0" >&2
    shar $(distdir) | GZIP=$(GZIP_ENV) gzip -c >$(distdir).shar.gz
    $(am__post_remove_distdir)

dist-zip: distdir
    -rm -f $(distdir).zip
    zip -rq $(distdir).zip $(distdir)
    $(am__post_remove_distdir)

dist dist-all:
    $(MAKE) $(AM_MAKEFLAGS) $(DIST_TARGETS) am__post_remove_distdir='@:'
    $(am__post_remove_distdir)

# This target untars the dist file and tries a VPATH configuration.  Then
# it guarantees that the distribution is self-contained by making another
# tarfile.
distcheck: dist
    case '$(DIST_ARCHIVES)' in \
    *.tar.gz*) \
      GZIP=$(GZIP_ENV) gzip -dc $(distdir).tar.gz | $(am__untar) ;;\
    *.tar.bz2*) \
      bzip2 -dc $(distdir).tar.bz2 | $(am__untar) ;;\
    *.tar.lz*) \
      lzip -dc $(distdir).tar.lz | $(am__untar) ;;\
    *.tar.xz*) \
      xz -dc $(distdir).tar.xz | $(am__untar) ;;\
    *.tar.Z*) \
      uncompress -c $(distdir).tar.Z | $(am__untar) ;;\
    *.shar.gz*) \
      GZIP=$(GZIP_ENV) gzip -dc $(distdir).shar.gz | unshar ;;\
    *.zip*) \
      unzip $(distdir).zip ;;\
    esac
    chmod -R a-w $(distdir)
    chmod u+w $(distdir)
    mkdir $(distdir)/_build $(distdir)/_build/sub $(distdir)/_inst
    chmod a-w $(distdir)
    test -d $(distdir)/_build || exit 0; \
    dc_install_base=`$(am__cd) $(distdir)/_inst && pwd | sed -e 's,^[^:\\/]:[\\/],/,'` \
      && dc_destdir="$${TMPDIR-/tmp}/am-dc-$$$$/" \
      && am__cwd=`pwd` \
      && $(am__cd) $(distdir)/_build/sub \
      && ../../configure \
        $(AM_DISTCHECK_CONFIGURE_FLAGS) \
        $(DISTCHECK_CONFIGURE_FLAGS) \
        --srcdir=../.. --prefix="$$dc_install_base" \
      && $(MAKE) $(AM_MAKEFLAGS) \
      && $(MAKE) $(AM_MAKEFLAGS) dvi \
      && $(MAKE) $(AM_MAKEFLAGS) check \
      && $(MAKE) $(AM_MAKEFLAGS) install \
      && $(MAKE) $(AM_MAKEFLAGS) installcheck \
      && $(MAKE) $(AM_MAKEFLAGS) uninstall \
      && $(MAKE) $(AM_MAKEFLAGS) distuninstallcheck_dir="$$dc_install_base" \
            distuninstallcheck \
      && chmod -R a-w "$$dc_install_base" \
      && ({ \
           (cd ../.. && umask 077 && mkdir "$$dc_destdir") \
           && $(MAKE) $(AM_MAKEFLAGS) DESTDIR="$$dc_destdir" install \
           && $(MAKE) $(AM_MAKEFLAGS) DESTDIR="$$dc_destdir" uninstall \
           && $(MAKE) $(AM_MAKEFLAGS) DESTDIR="$$dc_destdir" \
                distuninstallcheck_dir="$$dc_destdir" distuninstallcheck; \
          } || { rm -rf "$$dc_destdir"; exit 1; }) \
      && rm -rf "$$dc_destdir" \
      && $(MAKE) $(AM_MAKEFLAGS) dist \
      && rm -rf $(DIST_ARCHIVES) \
      && $(MAKE) $(AM_MAKEFLAGS) distcleancheck \
      && cd "$$am__cwd" \
      || exit 1
    $(am__post_remove_distdir)
    @(echo "$(distdir) archives ready for distribution: "; \
      list='$(DIST_ARCHIVES)'; for i in $$list; do echo $$i; done) | \
      sed -e 1h -e 1s/./=/g -e 1p -e 1x -e '$$p' -e '$$x'
distuninstallcheck:
    @test -n '$(distuninstallcheck_dir)' || { \
      echo 'ERROR: trying to run $@ with an empty' \
           '$$(distuninstallcheck_dir)' >&2; \
      exit 1; \
    }; \
    $(am__cd) '$(distuninstallcheck_dir)' || { \
      echo 'ERROR: cannot chdir into $(distuninstallcheck_dir)' >&2; \
      exit 1; \
    }; \
    test `$(am__distuninstallcheck_listfiles) | wc -l` -eq 0 \
       || { echo "ERROR: files left after uninstall:" ; \
            if test -n "$(DESTDIR)"; then \
              echo "  (check DESTDIR support)"; \
            fi ; \
            $(distuninstallcheck_listfiles) ; \
            exit 1; } >&2
distcleancheck: distclean
    @if test '$(srcdir)' = . ; then \
      echo "ERROR: distcleancheck can only run from a VPATH build" ; \
      exit 1 ; \
    fi
    @test `$(distcleancheck_listfiles) | wc -l` -eq 0 \
      || { echo "ERROR: files left in build directory after distclean:" ; \
           $(distcleancheck_listfiles) ; \
           exit 1; } >&2
check-am: all-am
check: check-recursive
all-am: Makefile
installdirs: installdirs-recursive
installdirs-am:
install: install-recursive
install-exec: install-exec-recursive
install-data: install-data-recursive
uninstall: uninstall-recursive

install-am: all-am
    @$(MAKE) $(AM_MAKEFLAGS) install-exec-am install-data-am

installcheck: installcheck-recursive
install-strip:
    if test -z '$(STRIP)'; then \
      $(MAKE) $(AM_MAKEFLAGS) INSTALL_PROGRAM="$(INSTALL_STRIP_PROGRAM)" \
        install_sh_PROGRAM="$(INSTALL_STRIP_PROGRAM)" INSTALL_STRIP_FLAG=-s \
          install; \
    else \
      $(MAKE) $(AM_MAKEFLAGS) INSTALL_PROGRAM="$(INSTALL_STRIP_PROGRAM)" \
        install_sh_PROGRAM="$(INSTALL_STRIP_PROGRAM)" INSTALL_STRIP_FLAG=-s \
        "INSTALL_PROGRAM_ENV=STRIPPROG='$(STRIP)'" install; \
    fi
mostlyclean-generic:

clean-generic:

distclean-generic:
    -test -z "$(CONFIG_CLEAN_FILES)" || rm -f $(CONFIG_CLEAN_FILES)
    -test . = "$(srcdir)" || test -z "$(CONFIG_CLEAN_VPATH_FILES)" || rm -f $(CONFIG_CLEAN_VPATH_FILES)

maintainer-clean-generic:
    @echo "This command is intended for maintainers to use"
    @echo "it deletes files that may require special tools to rebuild."
clean: clean-recursive

clean-am: clean-generic mostlyclean-am

distclean: distclean-recursive
    -rm -f $(am__CONFIG_DISTCLEAN_FILES)
    -rm -f Makefile
distclean-am: clean-am distclean-generic distclean-tags

dvi: dvi-recursive

dvi-am:

html: html-recursive

html-am:

info: info-recursive

info-am:

install-data-am:

install-dvi: install-dvi-recursive

install-dvi-am:

install-exec-am:

install-html: install-html-recursive

install-html-am:

install-info: install-info-recursive

install-info-am:

install-man:

install-pdf: install-pdf-recursive

install-pdf-am:

install-ps: install-ps-recursive

install-ps-am:

installcheck-am:

maintainer-clean: maintainer-clean-recursive
    -rm -f $(am__CONFIG_DISTCLEAN_FILES)
    -rm -rf $(top_srcdir)/autom4te.cache
    -rm -f Makefile
maintainer-clean-am: distclean-am maintainer-clean-generic

mostlyclean: mostlyclean-recursive

mostlyclean-am: mostlyclean-generic

pdf: pdf-recursive

pdf-am:

ps: ps-recursive

ps-am:

uninstall-am:
    @$(NORMAL_INSTALL)
    $(MAKE) $(AM_MAKEFLAGS) uninstall-hook
.MAKE: $(am__recursive_targets) install-am install-strip uninstall-am

.PHONY: $(am__recursive_targets) CTAGS GTAGS TAGS all all-am \
    am--refresh check check-am clean clean-cscope clean-generic \
    cscope cscopelist-am ctags ctags-am dist dist-all dist-bzip2 \
    dist-gzip dist-lzip dist-shar dist-tarZ dist-xz dist-zip \
    distcheck distclean distclean-generic distclean-tags \
    distcleancheck distdir distuninstallcheck dvi dvi-am html \
    html-am info info-am install install-am install-data \
    install-data-am install-dvi install-dvi-am install-exec \
    install-exec-am install-html install-html-am install-info \
    install-info-am install-man install-pdf install-pdf-am \
    install-ps install-ps-am install-strip installcheck \
    installcheck-am installdirs installdirs-am maintainer-clean \
    maintainer-clean-generic mostlyclean mostlyclean-generic pdf \
    pdf-am ps ps-am tags tags-am uninstall uninstall-am \
    uninstall-hook

.PRECIOUS: Makefile


.PHONY: INSTALL

uninstall-hook:
    rm -f $(HOME)/.$(PACKAGE)/spectrum3d.pref

# Tell versions [3.59,3.63) of GNU make to not export all variables.
# Otherwise a system limit (for SysV at least) may be exceeded.
.NOEXPORT:



```
-fcommon at the right pl
I have the same result no matter I don the first commands you indicated me or if I change the makefile file. Hoping I added -fcommon at the right place

---

### Post by norobro on 2021-03-20
Are there makefiles in subdirectories? If so you need to add -fcommon to all CFLAG lines.

Did you try using export?

EDIT:  Please provide a link to the source code.

---

### Post by norobro on 2021-03-20
Sorry, the instructions I gave for using export are incorrect. You need to rerun configure:```
[COLOR=#000000][FONT=&amp]make clean
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]export CFLAGS="-fcommon" 
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]./configure
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]make[/FONT][/COLOR]
```

---

