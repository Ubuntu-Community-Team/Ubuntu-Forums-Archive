---
title: "Build 3d simulator from Source - Help"
date: 2007-08-02
forum: General Help
---

### Post by linuxnovice on 2007-08-02
Hello,

I have to install and run Gazebo/player/stage simulation for my robotics reserach. I have got installation instructions from my university. This was done a while a ago and it seems most of the packages seems to have a newer version. But I would like to try everything in the same version and make it work and then maybe upgrade it. Most of the packages are in Adept but they are the latest ones. So I had to download the source and build it from there.

These are packages that I need:
1) swig-1.3.27
2) proj-4.4.9
3) gdal-1.3.1
4) gsl-1.7
5) ode-0.5
6) opencv-0.9.7
7) wxpython-2.6.2.1
8) Gazebo/Stage
9) Player

All the packages are sequential i.e. every package is a pre-requisite to the next one. I have downloaded all the source tarballs of the correct version of the packages. I have also installed swig and proj. I used checkinstall instead of make install so that I will get a deb package. 

I have run into problems with gdal. I ran the configure scrip and it gave me no dependency errors. However when there is trouble make. When I run make, there is a bunch of thats being displayed (I am not going to show all thing, I think that it is not necessary but please correct me if I am wrong) and I got this error: 

fitdataset.cpp:177: error: extra qualification 'FITRasterBand::' on member 'FITRasterBand'
fitdataset.cpp: In static member function 'static GDALDataset* FITDataset::Open(GDALOpenInfo*)':
fitdataset.cpp:1019: warning: dereferencing type-punned pointer will break strict-aliasing rules
make[2]: *** [../o/fitdataset.o] Error 1
make[2]: Leaving directory `/home/sudarshan/Simulator/gdal-1.3.1/frmts/fit'
make[1]: *** [fit-install-obj] Error 2
make[1]: Leaving directory `/home/sudarshan/Simulator/gdal-1.3.1/frmts'
make: *** [frmts-target] Error 2


I dont know what this error about?

I know this is not a very general requirement but I dont know where else to post this, as this is strictly not an absolute beginer issue. I would very much appreciate any help in installing and running gazebo as it is essential for my research. Please let me know if you need any more information.

Thankyou for your help and patience!

P.S: Just in case to let you know, the installation instructions provided by the manual are for a Red Hat Linux Enterprise Edition, although, I thought this shouldnt matter much as we are dealing with the source files.

---

### Post by linuxnovice on 2007-08-04
Help Please

---

### Post by linuxnovice on 2007-08-04
Update:

So I found a deb file for the exact version of gdal I wanted sitting in the Ubuntu universe resipository pool. So I went to install everything except wxpython.

The instructions I have says that firlst I need to build the wxWidgets and it strongly recommends to do so in a different directory. So I did that and compiled it there and I ran into an error:

sudarshan@Lucky-Linux:~/Simulator/wxPython-src-2.6.2.1$ mkdir bld
sudarshan@Lucky-Linux:~/Simulator/wxPython-src-2.6.2.1$ cd bld
sudarshan@Lucky-Linux:~/Simulator/wxPython-src-2.6.2.1/bld$ ../configure --enable-gtk2 --with-opengl
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
loading argument cache configarg.cache
checking for --enable-gui... yes
checking for --enable-monolithic... no
checking for --enable-plugins... no
checking for --enable-universal... no
checking for --enable-nanox... no
checking for --enable-gpe... no
checking for --with-libpng... yes
checking for --with-libjpeg... yes
checking for --with-libtiff... yes
checking for --with-libxpm... yes
checking for --with-libmspack... yes
checking for --with-sdl... no
checking for --with-gnomeprint... no
checking for --with-opengl... yes
checking for --with-dmalloc... no
checking for --with-regex... yes
checking for --with-zlib... yes
checking for --with-odbc... no
checking for --with-expat... yes
checking for --enable-shared... yes
checking for --enable-optimise... yes
checking for --enable-debug... no
checking for --enable-stl... no
checking for --enable-debug_flag... no
checking for --enable-debug_info... no
checking for --enable-debug_gdb... no
checking for --enable-debug_cntxt... no
checking for --enable-mem_tracing... no
checking for --enable-profile... no
checking for --enable-no_rtti... no
checking for --enable-no_exceptions... no
checking for --enable-permissive... no
checking for --enable-no_deps... no
checking for --enable-compat22... no
checking for --disable-compat24... no
checking for --enable-rpath... yes
checking for --enable-intl... yes
checking for --enable-config... yes
checking for --enable-protocols... yes
checking for --enable-ftp... yes
checking for --enable-http... yes
checking for --enable-fileproto... yes
checking for --enable-sockets... yes
checking for --enable-ole... yes
checking for --enable-dataobj... yes
checking for --enable-ipc... yes
checking for --enable-apple_ieee... yes
checking for --enable-arcstream... yes
checking for --enable-backtrace... yes
checking for --enable-catch_segvs... yes
checking for --enable-cmdline... yes
checking for --enable-datetime... yes
checking for --enable-debugreport... yes
checking for --enable-dialupman... yes
checking for --enable-dynlib... yes
checking for --enable-dynamicloader... yes
checking for --enable-exceptions... yes
checking for --enable-ffile... yes
checking for --enable-file... yes
checking for --enable-filesystem... yes
checking for --enable-fontmap... yes
checking for --enable-fs_inet... yes
checking for --enable-fs_zip... yes
checking for --enable-geometry... yes
checking for --enable-log... yes
checking for --enable-longlong... yes
checking for --enable-mimetype... yes
checking for --enable-mslu... yes
checking for --enable-snglinst... yes
checking for --enable-std_iostreams... yes
checking for --enable-std_string... yes
checking for --enable-stdpaths... yes
checking for --enable-stopwatch... yes
checking for --enable-streams... yes
checking for --enable-system_options... yes
checking for --enable-textbuf... yes
checking for --enable-textfile... yes
checking for --enable-timer... yes
checking for --enable-unicode... no
checking for --enable-sound... yes
checking for --enable-mediactrl... no
checking for --enable-wxprintfv... no
checking for --enable-zipstream... yes
checking for --enable-url... yes
checking for --enable-protocol... yes
checking for --enable-protocol_http... yes
checking for --enable-protocol_ftp... yes
checking for --enable-protocol_file... yes
checking for --enable-threads... yes
checking for --enable-docview... yes
checking for --enable-help... yes
checking for --enable-mshtmlhelp... yes
checking for --enable-html... yes
checking for --enable-htmlhelp... yes
checking for --enable-xrc... yes
checking for --enable-constraints... yes
checking for --enable-printarch... yes
checking for --enable-mdi... yes
checking for --enable-mdidoc... yes
checking for --enable-loggui... yes
checking for --enable-logwin... yes
checking for --enable-logdialog... yes
checking for --enable-webkit... yes
checking for --enable-postscript... yes
checking for --enable-prologio... no
checking for --enable-resources... no
checking for --enable-clipboard... yes
checking for --enable-dnd... yes
checking for --enable-metafile... yes
checking for --enable-controls... no
checking for --enable-accel... yes
checking for --enable-button... yes
checking for --enable-bmpbutton... yes
checking for --enable-calendar... yes
checking for --enable-caret... yes
checking for --enable-checkbox... yes
checking for --enable-checklst... yes
checking for --enable-choice... yes
checking for --enable-choicebook... yes
checking for --enable-combobox... yes
checking for --enable-datepick... yes
checking for --enable-display... yes
checking for --enable-gauge... yes
checking for --enable-grid... yes
checking for --enable-imaglist... yes
checking for --enable-listbook... yes
checking for --enable-listbox... yes
checking for --enable-listctrl... yes
checking for --enable-notebook... yes
checking for --enable-radiobox... yes
checking for --enable-radiobtn... yes
checking for --enable-sash... yes
checking for --enable-scrollbar... yes
checking for --enable-slider... yes
checking for --enable-spinbtn... yes
checking for --enable-spinctrl... yes
checking for --enable-splitter... yes
checking for --enable-statbmp... yes
checking for --enable-statbox... yes
checking for --enable-statline... yes
checking for --enable-stattext... yes
checking for --enable-statusbar... yes
checking for --enable-tabdialog... no
checking for --enable-textctrl... yes
checking for --enable-togglebtn... yes
checking for --enable-toolbar... yes
checking for --enable-tbarnative... yes
checking for --enable-tbarsmpl... yes
checking for --enable-treectrl... yes
checking for --enable-tipwindow... yes
checking for --enable-popupwin... yes
checking for --enable-commondlg... yes
checking for --enable-choicedlg... yes
checking for --enable-coldlg... yes
checking for --enable-filedlg... yes
checking for --enable-finddlg... yes
checking for --enable-fontdlg... yes
checking for --enable-dirdlg... yes
checking for --enable-msgdlg... yes
checking for --enable-numberdlg... yes
checking for --enable-splash... yes
checking for --enable-textdlg... yes
checking for --enable-tipdlg... yes
checking for --enable-progressdlg... yes
checking for --enable-wizarddlg... yes
checking for --enable-menus... yes
checking for --enable-miniframe... yes
checking for --enable-tooltips... yes
checking for --enable-splines... yes
checking for --enable-mousewheel... yes
checking for --enable-validators... yes
checking for --enable-busyinfo... yes
checking for --enable-joystick... yes
checking for --enable-metafile... yes
checking for --enable-dragimage... yes
checking for --enable-accessibility... no
checking for --enable-palette... yes
checking for --enable-image... yes
checking for --enable-gif... yes
checking for --enable-pcx... yes
checking for --enable-iff... no
checking for --enable-pnm... yes
checking for --enable-xpm... yes
checking for --enable-ico_cur... yes
checking for --enable-official_build... no
saving argument cache configarg.cache
checking for toolkit... gtk
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking if the C compiler requires -ext o...
checking whether we are using the Metrowerks C compiler... no
checking whether we are using the IBM xlC C compiler... no
checking whether we are using the SGI C compiler... no
checking whether we are using the Sun C compiler... no
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking if the C++ compiler requires -ext o...
checking whether we are using the Metrowerks C++ compiler... no
checking whether we are using the IBM xlC C++ compiler... no
checking whether we are using the SGI C++ compiler... no
checking whether we are using the Sun C++ compiler... no
checking for ranlib... ranlib
checking for ar... ar
checking for a BSD-compatible install... /usr/bin/install -c
checking for strip... strip
checking if make is GNU make... yes
checking whether ln -s works... yes
checking for strcasecmp() in string.h... yes
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for unistd.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking fnmatch.h usability... yes
checking fnmatch.h presence... yes
checking for fnmatch.h... yes
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for char... yes
checking size of char... 1
checking for short... yes
checking size of short... 2
checking for void *... yes
checking size of void *... 4
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for size_t... yes
checking size of size_t... 4
checking for long long... yes
checking size of long long... 8
checking for wchar_t... yes
checking size of wchar_t... 4
checking for va_copy... yes
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking if large file support is available... yes
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for fseeko... yes
checking whether byte ordering is bigendian... no
checking how to run the C++ preprocessor... g++ -E
checking iostream usability... yes
checking iostream presence... yes
checking for iostream... yes
checking if C++ compiler supports bool... yes
checking if C++ compiler supports the explicit keyword... yes
checking whether the compiler supports const_cast<>... yes
checking whether the compiler supports reinterpret_cast<>... yes
checking whether the compiler supports static_cast<>... yes
checking for std::string in <string>... yes
checking for std::istream... yes
checking for std::ostream... yes
checking for libraries directory... lib
checking for glibc 2.1 or later... yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for regcomp... yes
checking for re_search... yes
checking for zlib.h >= 1.1.4... yes
checking for zlib.h... (cached) yes
checking for deflate in -lz... yes
checking for png.h > 0.90... yes
checking for png.h... (cached) yes
checking for png_check_sig in -lpng... yes
checking for jpeglib.h... yes
checking for jpeg_read_header in -ljpeg... yes
checking tiffio.h usability... yes
checking tiffio.h presence... yes
checking for tiffio.h... yes
checking for TIFFError in -ltiff... yes
checking expat.h usability... yes
checking expat.h presence... yes
checking for expat.h... yes
checking if expat.h is valid C++ header... yes
checking for XML_ParserCreate in -lexpat... yes
checking mspack.h usability... no
checking mspack.h presence... no
checking for mspack.h... no
checking for GTK+ version...
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.

Please help me get rid of this error.
Thanks.

---

### Post by linuxnovice on 2007-08-09
Ok can someone please help me?

I solved the GTK problem. Now I am trying to install wxpython. The instructions that I have told me to build wxwidgets in a separate directly. I did that. From the bld directory I typed the command:

../configure --enable-gtk2 --with-opengl
Everything worked well. Then I had to set the path libraries correct using ldconfig. After that, I had to build the other libraries bundled with wxwidgets needed for wxpython. For this I had to go to /contrib/src inside the bld directory and run a make and make install. I did not have any problems there.

Finally, I had to build wxpython itself from the base directory. There was was python file setup.py and I had to do a ./setup.py build. When I did that I got this:

sudarshan@Lucky-Linux:~/Simulator/wxPython-src-2.6.2.1/wxPython$ ./setup.py build
Found wx-config: /usr/local/bin/wx-config
    Using flags:  --toolkit=gtk2 --unicode=no --version=2.6
Preparing CORE...
Preparing GLCANVAS...
Preparing STC...
Preparing GIZMOS...
Preparing ANIMATE...
running build
running build_py
creating build-gtk2
creating build-gtk2/lib.linux-i686-2.5
creating build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/__init__.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/calendar.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/activex.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/_wx.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/animate.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/stc.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/iewin.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/_windows.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/gizmos.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/_controls.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/grid.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/webkit.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/_gdi.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/xrc.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/media.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/htmlhelp.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/html.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/_core.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/_misc.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/glcanvas.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/wizard.py -> build-gtk2/lib.linux-i686-2.5/wxPython
copying wxPython/help.py -> build-gtk2/lib.linux-i686-2.5/wxPython
creating build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/maskededit.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/shell.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/PythonBitmaps.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/__init__.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/calendar.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/throbber.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/colourselect.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/CDate.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/intctrl.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/timectrl.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/plot.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/newevent.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/activexwrapper.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/dialogs.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/imagebrowser.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/grids.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/ErrorDialogs_wdr.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/fancytext.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/filebrowsebutton.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/colourdb.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/ErrorDialogs.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/vtk.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/rcsizer.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/pubsub.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/anchors.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/scrolledpanel.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/maskednumctrl.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/floatbar.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/sheet.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/foldmenu.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/wxPlotCanvas.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/printout.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/wxpTag.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/multisash.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/ClickableHtmlWindow.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/buttons.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/rightalign.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/stattext.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/splashscreen.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/infoframe.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/maskedctrl.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/mvctree.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/pyshell.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/popupctl.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/layoutf.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/imageutils.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/evtmgr.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/analogclock.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/gridmovers.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
copying wxPython/lib/floatcanvas.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib
creating build-gtk2/lib.linux-i686-2.5/wxPython/lib/colourchooser
copying wxPython/lib/colourchooser/__init__.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/colourchooser
copying wxPython/lib/colourchooser/pycolourchooser.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/colourchooser
copying wxPython/lib/colourchooser/pypalette.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/colourchooser
copying wxPython/lib/colourchooser/intl.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/colourchooser
copying wxPython/lib/colourchooser/pycolourslider.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/colourchooser
copying wxPython/lib/colourchooser/canvas.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/colourchooser
copying wxPython/lib/colourchooser/pycolourbox.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/colourchooser
creating build-gtk2/lib.linux-i686-2.5/wxPython/lib/editor
copying wxPython/lib/editor/images.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/editor
copying wxPython/lib/editor/__init__.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/editor
copying wxPython/lib/editor/selection.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/editor
copying wxPython/lib/editor/editor.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/editor
creating build-gtk2/lib.linux-i686-2.5/wxPython/lib/mixins
copying wxPython/lib/mixins/listctrl.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/mixins
copying wxPython/lib/mixins/__init__.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/mixins
copying wxPython/lib/mixins/grid.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/mixins
copying wxPython/lib/mixins/imagelist.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/mixins
copying wxPython/lib/mixins/rubberband.py -> build-gtk2/lib.linux-i686-2.5/wxPython/lib/mixins
creating build-gtk2/lib.linux-i686-2.5/wxPython/tools
copying wxPython/tools/__init__.py -> build-gtk2/lib.linux-i686-2.5/wxPython/tools
copying wxPython/tools/img2xpm.py -> build-gtk2/lib.linux-i686-2.5/wxPython/tools
copying wxPython/tools/img2img.py -> build-gtk2/lib.linux-i686-2.5/wxPython/tools
copying wxPython/tools/img2py.py -> build-gtk2/lib.linux-i686-2.5/wxPython/tools
copying wxPython/tools/img2png.py -> build-gtk2/lib.linux-i686-2.5/wxPython/tools
copying wxPython/tools/helpviewer.py -> build-gtk2/lib.linux-i686-2.5/wxPython/tools
copying wxPython/tools/dbg.py -> build-gtk2/lib.linux-i686-2.5/wxPython/tools
creating build-gtk2/lib.linux-i686-2.5/wx
copying wx/__init__.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/calendar.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/__version__.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/animate.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/stc.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/_windows.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/gizmos.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/_controls.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/grid.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/webkit.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/_gdi.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/xrc.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/media.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/html.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/_core.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/_misc.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/glcanvas.py -> build-gtk2/lib.linux-i686-2.5/wx
copying wx/wizard.py -> build-gtk2/lib.linux-i686-2.5/wx
creating build-gtk2/lib.linux-i686-2.5/wx/build
copying wx/build/__init__.py -> build-gtk2/lib.linux-i686-2.5/wx/build
copying wx/build/build_options.py -> build-gtk2/lib.linux-i686-2.5/wx/build
copying wx/build/config.py -> build-gtk2/lib.linux-i686-2.5/wx/build
creating build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/shell.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/__init__.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/calendar.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/throbber.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/foldpanelbar.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/flashwin.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/colourselect.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/CDate.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/hyperlink.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/iewin.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/intctrl.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/plot.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/newevent.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/activexwrapper.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/dialogs.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/imagebrowser.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/grids.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/analogclockopts.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/fancytext.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/filebrowsebutton.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/colourdb.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/statbmp.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/ticker_xrc.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/vtk.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/docview.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/rcsizer.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/pubsub.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/rpcMixin.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/anchors.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/scrolledpanel.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/floatbar.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/sheet.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/foldmenu.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/splitter.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/wxPlotCanvas.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/printout.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/wxpTag.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/multisash.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/ClickableHtmlWindow.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/buttons.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/rightalign.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/ticker.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/stattext.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/splashscreen.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/infoframe.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/pdfwin.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/mvctree.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/pyshell.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/popupctl.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/pydocview.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/layoutf.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/imageutils.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/evtmgr.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/analogclock.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/gridmovers.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
copying wx/lib/gestures.py -> build-gtk2/lib.linux-i686-2.5/wx/lib
creating build-gtk2/lib.linux-i686-2.5/wx/lib/colourchooser
copying wx/lib/colourchooser/__init__.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/colourchooser
copying wx/lib/colourchooser/pycolourchooser.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/colourchooser
copying wx/lib/colourchooser/pypalette.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/colourchooser
copying wx/lib/colourchooser/intl.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/colourchooser
copying wx/lib/colourchooser/pycolourslider.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/colourchooser
copying wx/lib/colourchooser/canvas.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/colourchooser
copying wx/lib/colourchooser/pycolourbox.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/colourchooser
creating build-gtk2/lib.linux-i686-2.5/wx/lib/editor
copying wx/lib/editor/images.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/editor
copying wx/lib/editor/__init__.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/editor
copying wx/lib/editor/selection.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/editor
copying wx/lib/editor/editor.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/editor
creating build-gtk2/lib.linux-i686-2.5/wx/lib/floatcanvas
copying wx/lib/floatcanvas/__init__.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/floatcanvas
copying wx/lib/floatcanvas/FloatCanvas.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/floatcanvas
copying wx/lib/floatcanvas/Resources.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/floatcanvas
copying wx/lib/floatcanvas/NavCanvas.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/floatcanvas
creating build-gtk2/lib.linux-i686-2.5/wx/lib/masked
copying wx/lib/masked/maskededit.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/masked
copying wx/lib/masked/__init__.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/masked
copying wx/lib/masked/timectrl.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/masked
copying wx/lib/masked/ipaddrctrl.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/masked
copying wx/lib/masked/ctrl.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/masked
copying wx/lib/masked/numctrl.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/masked
copying wx/lib/masked/combobox.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/masked
copying wx/lib/masked/textctrl.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/masked
creating build-gtk2/lib.linux-i686-2.5/wx/lib/mixins
copying wx/lib/mixins/listctrl.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/mixins
copying wx/lib/mixins/__init__.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/mixins
copying wx/lib/mixins/grid.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/mixins
copying wx/lib/mixins/imagelist.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/mixins
copying wx/lib/mixins/rubberband.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/mixins
creating build-gtk2/lib.linux-i686-2.5/wx/lib/ogl
copying wx/lib/ogl/__init__.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/ogl
copying wx/lib/ogl/_diagram.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/ogl
copying wx/lib/ogl/_oglmisc.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/ogl
copying wx/lib/ogl/_bmpshape.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/ogl
copying wx/lib/ogl/_basic.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/ogl
copying wx/lib/ogl/_drawn.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/ogl
copying wx/lib/ogl/_divided.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/ogl
copying wx/lib/ogl/_canvas.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/ogl
copying wx/lib/ogl/_lines.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/ogl
copying wx/lib/ogl/_composit.py -> build-gtk2/lib.linux-i686-2.5/wx/lib/ogl
creating build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/shell.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/images.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/interpreter.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/__init__.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/filling.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/crust.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/pseudo.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/PyFilling.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/PyShell.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/editwindow.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/document.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/PyAlaMode.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/PyAlaCarte.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/frame.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/dispatcher.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/introspect.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/PyAlaModeTest.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/PyCrust.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/editor.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/PyWrap.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/buffer.py -> build-gtk2/lib.linux-i686-2.5/wx/py
copying wx/py/version.py -> build-gtk2/lib.linux-i686-2.5/wx/py
creating build-gtk2/lib.linux-i686-2.5/wx/tools
copying wx/tools/__init__.py -> build-gtk2/lib.linux-i686-2.5/wx/tools
copying wx/tools/img2xpm.py -> build-gtk2/lib.linux-i686-2.5/wx/tools
copying wx/tools/img2img.py -> build-gtk2/lib.linux-i686-2.5/wx/tools
copying wx/tools/img2py.py -> build-gtk2/lib.linux-i686-2.5/wx/tools
copying wx/tools/pywxrc.py -> build-gtk2/lib.linux-i686-2.5/wx/tools
copying wx/tools/img2png.py -> build-gtk2/lib.linux-i686-2.5/wx/tools
copying wx/tools/helpviewer.py -> build-gtk2/lib.linux-i686-2.5/wx/tools
copying wx/tools/genaxmodule.py -> build-gtk2/lib.linux-i686-2.5/wx/tools
copying wx/tools/dbg.py -> build-gtk2/lib.linux-i686-2.5/wx/tools
creating build-gtk2/lib.linux-i686-2.5/wx/tools/XRCed
copying wx/tools/XRCed/xrced.py -> build-gtk2/lib.linux-i686-2.5/wx/tools/XRCed
copying wx/tools/XRCed/images.py -> build-gtk2/lib.linux-i686-2.5/wx/tools/XRCed
copying wx/tools/XRCed/__init__.py -> build-gtk2/lib.linux-i686-2.5/wx/tools/XRCed
copying wx/tools/XRCed/params.py -> build-gtk2/lib.linux-i686-2.5/wx/tools/XRCed
copying wx/tools/XRCed/globals.py -> build-gtk2/lib.linux-i686-2.5/wx/tools/XRCed
copying wx/tools/XRCed/panel.py -> build-gtk2/lib.linux-i686-2.5/wx/tools/XRCed
copying wx/tools/XRCed/encode_bitmaps.py -> build-gtk2/lib.linux-i686-2.5/wx/tools/XRCed
copying wx/tools/XRCed/tools.py -> build-gtk2/lib.linux-i686-2.5/wx/tools/XRCed
copying wx/tools/XRCed/undo.py -> build-gtk2/lib.linux-i686-2.5/wx/tools/XRCed
copying wx/tools/XRCed/xxx.py -> build-gtk2/lib.linux-i686-2.5/wx/tools/XRCed
copying wx/tools/XRCed/tree.py -> build-gtk2/lib.linux-i686-2.5/wx/tools/XRCed
running build_ext
building '_core_' extension
creating build-gtk2/temp.linux-i686-2.5
creating build-gtk2/temp.linux-i686-2.5/src
creating build-gtk2/temp.linux-i686-2.5/src/gtk
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -DSWIG_TYPE_TABLE=_wxPython_table -DHAVE_CONFIG_H -DWXP_USE_THREAD=1 -UNDEBUG -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA -Iinclude -Isrc -I/usr/local/lib/wx/include/gtk2-ansi-release-2.6 -I/usr/local/include/wx-2.6 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/python2.5 -c src/helpers.cpp -o build-gtk2/temp.linux-i686-2.5/src/helpers.o -O3
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
src/helpers.cpp: In static member function &#8216;static wxPyCBInputStream* wxPyCBInputStream::create(PyObject*, bool)&#8217;:
src/helpers.cpp:1396: warning: &#8216;blocked&#8217; may be used uninitialized in this function
src/helpers.cpp: In destructor &#8216;virtual wxPyCBInputStream::~wxPyCBInputStream()&#8217;:
src/helpers.cpp:1386: warning: &#8216;blocked&#8217; may be used uninitialized in this function
src/helpers.cpp: In destructor &#8216;virtual wxPyCBInputStream::~wxPyCBInputStream()&#8217;:
src/helpers.cpp:1386: warning: &#8216;blocked&#8217; may be used uninitialized in this function
src/helpers.cpp: In destructor &#8216;wxPyCBInputStream::~wxPyCBInputStream()&#8217;:
src/helpers.cpp:1386: warning: &#8216;blocked&#8217; may be used uninitialized in this function
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -DSWIG_TYPE_TABLE=_wxPython_table -DHAVE_CONFIG_H -DWXP_USE_THREAD=1 -UNDEBUG -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA -Iinclude -Isrc -I/usr/local/lib/wx/include/gtk2-ansi-release-2.6 -I/usr/local/include/wx-2.6 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/python2.5 -c src/gtk/_core_wrap.cpp -o build-gtk2/temp.linux-i686-2.5/src/gtk/_core_wrap.o -O3
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
src/gtk/_core_wrap.cpp: In function &#8216;int SWIG_Python_ConvertPtr(PyObject*, void**, swig_type_info*, int)&#8217;:
src/gtk/_core_wrap.cpp:1178: error: invalid conversion from &#8216;const char*&#8217; to &#8216;char*&#8217;
src/gtk/_core_wrap.cpp: In function &#8216;void SWIG_Python_FixMethods(PyMethodDef*, swig_const_info*, swig_type_info**, swig_type_info**)&#8217;:
src/gtk/_core_wrap.cpp:48373: error: invalid conversion from &#8216;const char*&#8217; to &#8216;char*&#8217;
src/gtk/_core_wrap.cpp: At global scope:
src/gtk/_core_wrap.cpp:231: warning: &#8216;swig_type_info* SWIG_TypeDynamicCast(swig_type_info*, void**)&#8217; defined but not used
src/gtk/_core_wrap.cpp:419: warning: &#8216;const char* SWIG_UnpackDataName(const char*, void*, size_t, const char*)&#8217; defined but not used
src/gtk/_core_wrap.cpp:499: warning: &#8216;void SWIG_PropagateClientData(swig_type_info*)&#8217; defined but not used
src/gtk/_core_wrap.cpp:1199: warning: &#8216;void* SWIG_Python_MustGetPtr(PyObject*, swig_type_info*, int, int)&#8217; defined but not used
src/gtk/_core_wrap.cpp:1213: warning: &#8216;int SWIG_Python_ConvertPacked(PyObject*, void*, size_t, swig_type_info*, int)&#8217; defined but not used
error: command 'gcc' failed with exit status 1

This is not a dependency error..its some error in the code itself. I have no idea of how to get rid of this. I have been searching the internet for 4 days now..but no solution. Please someone help me...

Thanks.

---

### Post by apetresc on 2007-08-09
Is there any reason why you do not simply do ```
sudo apt-get install python-wxgtk2.6
```
It is the same thing as the package you are trying to install, except it is 2.6.3 instead of 2.6.2 but for point-point releases the API should be exactly identical, so this would still work.

Try that, it is always recommended to get packages from apt if possible, and use source tarballs only if there's no alternative.

Once you have that you should be okay to compile gazebo.

---

### Post by linuxnovice on 2007-08-09
Ok I did that. In the instructions that I have a, there is a test to determine whether everything is ready for building gazebo. Bascially I need to go into python mode and type "from wxPython.wx import *" and get no errors. But I got this:

>>> from wxPython.wx import *
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "wxPython/__init__.py", line 10, in <module>
    import _wx
  File "wxPython/_wx.py", line 3, in <module>
    from _core import *
  File "wxPython/_core.py", line 15, in <module>
    import wx._core
  File "wx/__init__.py", line 42, in <module>
    from wx._core import *
  File "wx/_core.py", line 4, in <module>
    import _core_
ImportError: No module named _core_

The problem, the instructions that I have are for specific versions of the packages and they have managed to get it to work...

---

### Post by apetresc on 2007-08-09
Hmm, you must've done something strange to your Python installation. I did the exact thing you just did, and no problems:
```
adrian@rootbeer:~$ sudo apt-get install python-wxgtk2.6
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  python-wxversion
Suggested packages:
  wx2.6-doc wx2.6-examples python-xml
The following NEW packages will be installed:
  python-wxgtk2.6 python-wxversion
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2610kB of archives.
After unpacking, 11.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ca.archive.ubuntu.com feisty/universe python-wxversion 2.6.3.2.1.5ubuntu6 [22.2kB]
Get:2 http://ca.archive.ubuntu.com feisty/universe python-wxgtk2.6 2.6.3.2.1.5ubuntu6 [2588kB]
Fetched 2610kB in 14m51s (2928B/s)
Selecting previously deselected package python-wxversion.
(Reading database ... 257976 files and directories currently installed.)
Unpacking python-wxversion (from .../python-wxversion_2.6.3.2.1.5ubuntu6_all.deb) ...
Selecting previously deselected package python-wxgtk2.6.
Unpacking python-wxgtk2.6 (from .../python-wxgtk2.6_2.6.3.2.1.5ubuntu6_i386.deb) ...
Setting up python-wxversion (2.6.3.2.1.5ubuntu6) ...

Setting up python-wxgtk2.6 (2.6.3.2.1.5ubuntu6) ...

adrian@rootbeer:~$ python
Python 2.5.1 (r251:54863, May  2 2007, 16:56:35)
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from wxPython.wx import *
>>>

```

Can you think of anything you've done to Python that you can undo?

---

### Post by linuxnovice on 2007-08-10
The only thing I can think of is that I never did a make clean after I manually tried to install wxpython. Maybe that screwed up something on my system. Is there anything that I can do to negate that?

---

