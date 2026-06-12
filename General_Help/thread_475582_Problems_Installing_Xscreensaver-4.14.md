---
title: "Problems Installing Xscreensaver-4.14"
date: 2007-06-16
forum: General Help
---

### Post by ForzaItalia250 on 2007-06-16
I had originally posted this in the Abosulte Beginner Talk session, as I'm just three days into Linux, after being up for over a day, it didn't get any replies, so I thought I'd try posting my issue in a different part of the forums.

Initially, I was having problems getting ./configure to work, but after better aquainting myself with the Terminal command-line interface, to which I'm very new (command-line interface in general) I was able to get ./configure to work. Once it ran though, I recieved this message.

[I]Warning: The GTK libraries do not seem to be available; the
`xscreensaver-demo' program requires them.

You can use Motif or Lesstif instead of GTK (use the
`--with-motif' option) but that is NOT recommended.
Though the Motif front-end to xscreensaver is still
maintained, it is no longer being updated with new
features: all new development on the xscreensaver-demo
program is happening in the GTK version, and not in the
Motif version. It is recommended that you build against
GTK instead of Motif. See <http://www.gtk.org/>.

Note: The JPEG library was not found.
This means that it won't be possible for the image-manipulating
display modes to load files from disk; and it also means that
the `webcollage' program will be much slower.

Note: The OpenGL 3D library was not found.

Those demos which use 3D will not be built or installed.
You might want to consider installing OpenGL and
re-running configure. If your vendor doesn't ship
their own implementation of OpenGL, you can get a free
version at <http://www.mesa3d.org/>. For general OpenGL
info, see <http://www.opengl.org/>.
[/I]
I've tried installing first GTK and its dependencies, but while attempting to install ATK-1.9.1, one of the dependencies, I received this message
[I]
checking for GLIB - version >= 2.5.7... 
*** 'pkg-config --modversion glib-2.0' returned 2.12.0, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.
[/I]
I've already installed glib-2.12.0, and I followed the instructions by typing in

pkg-config PKG_CONFIG_PATH /home/*****/glib-2.12.0/glib--2.0.pc

I than re-ran ./configure and received the same message

I don't know what this message means, or how I would do anything about it.
[I]
You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.[/I]

Also, in terms of the other two error messages with xscreensaver regarding jpegs and OpenGL, how do I go about fixing that? Is it something to do with my videocard (OpenGL) (ATI Mobility 9600)?

Any input would be appreciated

---

### Post by llamakc on 2007-06-16
On Debian-based distros (like Ubuntu) when one is trying to manually install software with the "configure/make/make install" routine and the script barfs at some missing dependency, you need to install it. 

The easiest way to do this is either a) use apt-get to grab the *-dev package from the repositories [so if the script complains about packageA you would need packageA-dev] and install it; or b) build the dependency from source also. I strongly recommend a) though.

So what if you don't know the name of the package? You use the tools provided like this (in the terminal prompt):

```

ken@llamakc 09:23:56:~$ apt-cache search jpeg | grep dev
libdjvulibre-dev - Development files for the DjVu image format
libjasper-1.701-dev - Development files for the JasPer JPEG-2000 library
libjpeg62-dev - Development files for the IJG JPEG library
libmng-dev - M-N-G library (Development headers)
libsdl-image1.2-dev - development files for SDL 1.2 image loading libray
libwmf-dev - Windows metafile conversion development
graphicsmagick-libmagick-dev-compat - image processing libraries providing ImageMagick interface
libexif-gtk-dev - Library providing GTK+ widgets to display/edit EXIF tags (development files)
libg2-dev - g2 2D graphics library (development files)
libgdal1-1.3.2-dev - Geospatial Data Abstraction Library - Development files
libgraphicsmagick++1-dev - format-independent image processing - C++ development files
libgraphicsmagick1-dev - format-independent image processing - C development files
liblivemedia-dev - multimedia RTSP streaming library
paintlib-dev - C++ class library for image manipulation
scribus-ng - Open Source Desktop Page Layout - developmental branch
libmjpegtools-dev - MJPEG video capture/editting/playback MPEG encoding
libexif-dev - library to parse EXIF files (development files)

```Above, I did `apt-cache search jpeg | grep dev` which means I used the tool apt-cache with the option of 'search' to look for 'jpeg'. Doing that alone would return many, many more results so I then used the pipe | character to "pipe" the results to the next command of `grep` which took the argument of "dev" to search for  the results above.

And I would guesstimate from those results that you would want to install libjpeg62-dev with `sudo apt-get install libjpeg62-dev` and so on for anything else it errors out on.

If you haven't done it yet, run `sudo apt-get install build-essential`.

Lastly, why are trying to build XScreensaver-4.14 from source when 4.24 is in the repositories? What functionality/compatibility do you need or think you require the older version for?

---

### Post by ForzaItalia250 on 2007-06-16
Thanks for the advice, I'm going to see how it works... 

I wasn't aware there was a newer one. I was looking up the Maxtrix 3D screensaver and this is what I downloaded.

---

### Post by ForzaItalia250 on 2007-06-16
EDIT: Solved GTK problems... moving onto openGL

---

### Post by ForzaItalia250 on 2007-06-16
I'm coming up with a new error message after installing mutlilpe openGL files
[I]
       Note: The OpenGL 3D library was not found.

             More specifically, we found the headers, but not the
             libraries; so either GL is half-installed on this
             system, or something else went wrong.  The `config.log'
             file might contain some clues.

             Those demos which use 3D will not be built or installed.
             You might want to consider installing OpenGL and
             re-running configure.  If your vendor doesn't ship
             their own implementation of OpenGL, you can get a free
             version at <http://www.mesa3d.org/>.  For general OpenGL
             info, see <http://www.opengl.org/>.
[/I]

I've installed:
libglitz-glx1-dev - Glitz OpenGL library GLX backend development libraries and headers
libglitz1-dev - OpenGL image compositing library development libraries and headers

Which both say libararies and headers, but the error message says that only the headers are there.

Then I installed freeglut3-dev and libglut3-dev and recieved this message
  
 [I] Warning: Unable to determine the MesaGL version number!
             Make sure you are using version 3.4 or newer.[/I]

---

