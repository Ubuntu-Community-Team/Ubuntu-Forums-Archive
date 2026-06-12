---
title: "error during installing Jukebox3D"
date: 2007-10-06
forum: General Help
---

### Post by markp1989 on 2007-10-06
following this tutorial [http://www.linuxonfire.org/forum/viewtopic.php?id=26](http://www.linuxonfire.org/forum/viewtopic.php?id=26)

at the part where i have to type 

> make clean && make

i get a error and cannot install it 

> rm -rf ~/.config/jukebox3D*
rm -f src/about.o src/callback.o src/ImgLib.o src/interface.o src/main.o src/model.o src/managecfg.o src/OglLib.o src/OglPanel.o src/player.o src/OptionLib.o src/options.o src/StrLib.o src/trackball.o src/language.o bin/jukebox3D-bin
gcc -Wall `sdl-config --cflags` `pkg-config --cflags gtk+-2.0 gtkglext-1.0 libglade-2.0`  -Wall -c -o src/about.o src/about.c
/bin/sh: sdl-config: not found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtkglext-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkglext-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkglext-1.0' found
Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found
src/about.c:29:21: error: gtk/gtk.h: No such file or directory
src/about.c:30:23: error: gtk/gtkgl.h: No such file or directory
src/about.c:31:25: error: glade/glade.h: No such file or directory
src/about.c:33:19: error: GL/gl.h: No such file or directory
src/about.c:34:20: error: GL/glu.h: No such file or directory
In file included from src/about.c:35:
src/../include/main.h:44: error: expected specifier-qualifier-list before &#8216;gfloat&#8217;
src/../include/main.h:55: error: expected specifier-qualifier-list before &#8216;gfloat&#8217;
src/../include/main.h:67: error: expected specifier-qualifier-list before &#8216;guint&#8217;
src/../include/main.h:73: error: expected specifier-qualifier-list before &#8216;GLuint&#8217;
src/../include/main.h:83: error: expected specifier-qualifier-list before &#8216;GLfloat&#8217;
src/../include/main.h:89: error: expected specifier-qualifier-list before &#8216;gboolean&#8217;
src/../include/main.h:135: error: expected specifier-qualifier-list before &#8216;GLuint&#8217;
src/../include/main.h:149: error: expected specifier-qualifier-list before &#8216;GLfloat&#8217;
src/../include/main.h:166: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from src/about.c:36:
src/../include/about.h:26: error: expected specifier-qualifier-list before &#8216;GtkWidget&#8217;
In file included from src/about.c:37:
src/../include/interface.h:22: error: expected specifier-qualifier-list before &#8216;GtkWidget&#8217;
src/../include/interface.h:35: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
src/../include/interface.h:36: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
src/about.c:38: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
src/about.c: In function &#8216;InitAboutGl&#8217;:
src/about.c:46: error: &#8216;GdkGLConfig&#8217; undeclared (first use in this function)
src/about.c:46: error: (Each undeclared identifier is reported only once
src/about.c:46: error: for each function it appears in.)
src/about.c:46: error: &#8216;glconfig&#8217; undeclared (first use in this function)
src/about.c:47: error: &#8216;gint&#8217; undeclared (first use in this function)
src/about.c:47: error: expected &#8216;;&#8217; before &#8216;major&#8217;
src/about.c:49: warning: implicit declaration of function &#8216;gtk_container_set_reallocate_redraws&#8217;
src/about.c:49: warning: implicit declaration of function &#8216;GTK_CONTAINER&#8217;
src/about.c:49: error: &#8216;AboutGui&#8217; has no member named &#8216;drawingarea1&#8217;
src/about.c:49: error: &#8216;TRUE&#8217; undeclared (first use in this function)
src/about.c:53: warning: implicit declaration of function &#8216;gdk_gl_query_version&#8217;
src/about.c:53: error: &#8216;major&#8217; undeclared (first use in this function)
src/about.c:53: error: &#8216;minor&#8217; undeclared (first use in this function)
src/about.c:54: warning: implicit declaration of function &#8216;g_print&#8217;
src/about.c:59: warning: implicit declaration of function &#8216;gdk_gl_config_new_by_mode&#8217;
src/about.c:59: error: &#8216;GDK_GL_MODE_RGB&#8217; undeclared (first use in this function)
src/about.c:59: error: &#8216;GDK_GL_MODE_DEPTH&#8217; undeclared (first use in this function)
src/about.c:59: error: &#8216;GDK_GL_MODE_DOUBLE&#8217; undeclared (first use in this function)
src/about.c:76: warning: implicit declaration of function &#8216;gtk_widget_set_gl_capability&#8217;
src/about.c:76: error: &#8216;AboutGui&#8217; has no member named &#8216;drawingarea1&#8217;
src/about.c:77: error: &#8216;GDK_GL_RGBA_TYPE&#8217; undeclared (first use in this function)
src/about.c:79: warning: implicit declaration of function &#8216;gtk_widget_show&#8217;
src/about.c:79: error: &#8216;AboutGui&#8217; has no member named &#8216;drawingarea1&#8217;
src/about.c: In function &#8216;Xml_About_load&#8217;:
src/about.c:87: error: &#8216;gui_about_xml&#8217; undeclared (first use in this function)
src/about.c:87: warning: implicit declaration of function &#8216;glade_xml_new&#8217;
src/about.c:90: warning: implicit declaration of function &#8216;Xml_gui_error&#8217;
src/about.c:93: warning: implicit declaration of function &#8216;Xml_widget_load&#8217;
src/about.c:93: error: &#8216;AboutGui&#8217; has no member named &#8216;window&#8217;
src/about.c:94: error: &#8216;AboutGui&#8217; has no member named &#8216;drawingarea1&#8217;
src/about.c:97: warning: implicit declaration of function &#8216;glade_xml_signal_autoconnect&#8217;
make: *** [src/about.o] Error 1
mark@mark-desktop:~/Desktop/jukebox3D$ make clean && make
rm -rf ~/.config/jukebox3D*
rm -f src/about.o src/callback.o src/ImgLib.o src/interface.o src/main.o src/model.o src/managecfg.o src/OglLib.o src/OglPanel.o src/player.o src/OptionLib.o src/options.o src/StrLib.o src/trackball.o src/language.o bin/jukebox3D-bin
gcc -Wall `sdl-config --cflags` `pkg-config --cflags gtk+-2.0 gtkglext-1.0 libglade-2.0`  -Wall -c -o src/about.o src/about.c
/bin/sh: sdl-config: not found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtkglext-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkglext-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkglext-1.0' found
Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found
src/about.c:29:21: error: gtk/gtk.h: No such file or directory
src/about.c:30:23: error: gtk/gtkgl.h: No such file or directory
src/about.c:31:25: error: glade/glade.h: No such file or directory
src/about.c:33:19: error: GL/gl.h: No such file or directory
src/about.c:34:20: error: GL/glu.h: No such file or directory
In file included from src/about.c:35:
src/../include/main.h:44: error: expected specifier-qualifier-list before &#8216;gfloat&#8217;
src/../include/main.h:55: error: expected specifier-qualifier-list before &#8216;gfloat&#8217;
src/../include/main.h:67: error: expected specifier-qualifier-list before &#8216;guint&#8217;
src/../include/main.h:73: error: expected specifier-qualifier-list before &#8216;GLuint&#8217;
src/../include/main.h:83: error: expected specifier-qualifier-list before &#8216;GLfloat&#8217;
src/../include/main.h:89: error: expected specifier-qualifier-list before &#8216;gboolean&#8217;
src/../include/main.h:135: error: expected specifier-qualifier-list before &#8216;GLuint&#8217;
src/../include/main.h:149: error: expected specifier-qualifier-list before &#8216;GLfloat&#8217;
src/../include/main.h:166: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from src/about.c:36:
src/../include/about.h:26: error: expected specifier-qualifier-list before &#8216;GtkWidget&#8217;
In file included from src/about.c:37:
src/../include/interface.h:22: error: expected specifier-qualifier-list before &#8216;GtkWidget&#8217;
src/../include/interface.h:35: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
src/../include/interface.h:36: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
src/about.c:38: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
src/about.c: In function &#8216;InitAboutGl&#8217;:
src/about.c:46: error: &#8216;GdkGLConfig&#8217; undeclared (first use in this function)
src/about.c:46: error: (Each undeclared identifier is reported only once
src/about.c:46: error: for each function it appears in.)
src/about.c:46: error: &#8216;glconfig&#8217; undeclared (first use in this function)
src/about.c:47: error: &#8216;gint&#8217; undeclared (first use in this function)
src/about.c:47: error: expected &#8216;;&#8217; before &#8216;major&#8217;
src/about.c:49: warning: implicit declaration of function &#8216;gtk_container_set_reallocate_redraws&#8217;
src/about.c:49: warning: implicit declaration of function &#8216;GTK_CONTAINER&#8217;
src/about.c:49: error: &#8216;AboutGui&#8217; has no member named &#8216;drawingarea1&#8217;
src/about.c:49: error: &#8216;TRUE&#8217; undeclared (first use in this function)
src/about.c:53: warning: implicit declaration of function &#8216;gdk_gl_query_version&#8217;
src/about.c:53: error: &#8216;major&#8217; undeclared (first use in this function)
src/about.c:53: error: &#8216;minor&#8217; undeclared (first use in this function)
src/about.c:54: warning: implicit declaration of function &#8216;g_print&#8217;
src/about.c:59: warning: implicit declaration of function &#8216;gdk_gl_config_new_by_mode&#8217;
src/about.c:59: error: &#8216;GDK_GL_MODE_RGB&#8217; undeclared (first use in this function)
src/about.c:59: error: &#8216;GDK_GL_MODE_DEPTH&#8217; undeclared (first use in this function)
src/about.c:59: error: &#8216;GDK_GL_MODE_DOUBLE&#8217; undeclared (first use in this function)
src/about.c:76: warning: implicit declaration of function &#8216;gtk_widget_set_gl_capability&#8217;
src/about.c:76: error: &#8216;AboutGui&#8217; has no member named &#8216;drawingarea1&#8217;
src/about.c:77: error: &#8216;GDK_GL_RGBA_TYPE&#8217; undeclared (first use in this function)
src/about.c:79: warning: implicit declaration of function &#8216;gtk_widget_show&#8217;
src/about.c:79: error: &#8216;AboutGui&#8217; has no member named &#8216;drawingarea1&#8217;
src/about.c: In function &#8216;Xml_About_load&#8217;:
src/about.c:87: error: &#8216;gui_about_xml&#8217; undeclared (first use in this function)
src/about.c:87: warning: implicit declaration of function &#8216;glade_xml_new&#8217;
src/about.c:90: warning: implicit declaration of function &#8216;Xml_gui_error&#8217;
src/about.c:93: warning: implicit declaration of function &#8216;Xml_widget_load&#8217;
src/about.c:93: error: &#8216;AboutGui&#8217; has no member named &#8216;window&#8217;
src/about.c:94: error: &#8216;AboutGui&#8217; has no member named &#8216;drawingarea1&#8217;
src/about.c:97: warning: implicit declaration of function &#8216;glade_xml_signal_autoconnect&#8217;
make: *** [src/about.o] Error 1

im kind of new to this sort of stuff, but i would like to be able to use this program, and any help i get will be highly appreciated

edit: abit of topic but im only 1 post away from 100 beans

---

### Post by markp1989 on 2007-10-07
i think it is a problem when i install the dependency 

here is a list of the dependencys i have been told to install 

>  build-essential
libgtk2.0-dev 
libgtkglext1 
libgtkglext1-dev 
libglade2-0 
libglade2-dev 
libsdl-image1.2 
libsdl-image1.2-dev 
libsdl-ttf2.0-0 
libsdl-ttf2.0-dev 
libdevil1c2 
libdevil-dev

this is what i get when i try to install dependencys 

> mark@mark-desktop:~$ sudo apt-get install build-essential libgtk2.0-dev libgtkglext1 libgtkglext1-dev libglade2-0 libglade2-dev libsdl-image1.2 libsdl-image1.2-dev libsdl-ttf2.0-0 libsdl-ttf2.0-dev libdevil1c2 libdevil-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libglade2-0 is already the newest version.
libsdl-image1.2 is already the newest version.
libsdl-image1.2 set to manual installed.
libsdl-ttf2.0-0 is already the newest version.
libsdl-ttf2.0-0 set to manual installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.12) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
  libsdl-image1.2-dev: Depends: libpng12-dev but it is not going to be installed
  libsdl-ttf2.0-dev: Depends: libfreetype6-dev but it is not going to be installed
E: Broken packages
mark@mark-desktop:~$ 



can someone please help me :(

---

### Post by ntetreau on 2007-12-15
Try again using aptitude instead of apt-get

---

### Post by Mentalbug on 2008-06-24
> **ntetreau said:**
> Try again using aptitude instead of apt-get

Thank you, you're my savior! \\:D/


Slightly out of subject but I had some similar apt-get problems trying to install libgtkglextmm-x11-dev and receiving this error message as an answear from synaptics: 
>  Depends: libgtkglext1-dev but it is not going to be installed

"sudo aptitude install libgtkglextmm-x11-dev" offered me to downgrade libgtkglext1 for some reason and it all went right ;)

---

