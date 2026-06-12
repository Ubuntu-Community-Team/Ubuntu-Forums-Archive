---
title: "Glslideshow stutter"
date: 2007-05-30
forum: General Help
---

### Post by niko7865 on 2007-05-30
glslideshow stutters (hangs for a fraction of a second) about one second in to a two second fade change between pictures. It does this every time it changes pictures regardless of file size. Anything I can do to solve this?

Ubuntu Fiesty 32bit
nVidia 6800GS, binary drivers, running beryl
2GB ram, AMD Athlon 64 X2 3800+

---

### Post by bharani on 2007-09-11
[SIZE="5"][COLOR="Red"]please some body help..I am having the same issue...[/COLOR][/SIZE]

---

### Post by bl1rt on 2007-11-06
A comment in the source code of GLSlideshow states that it would be impossible to avoid that stutter for some xserver architecture reason or something, but that the gap gets shorter the better your hardware. Hmm...
Here is what it says:

> 
 *
 * TODO:
 *
 * - When a new image is loaded, there is a glitch: animation pauses during
 *   the period when we're loading the image-to-fade-in.  On fast (2GHz)
 *   machines, this stutter is short but noticable (usually around 1/10th
 *   second.)  On slower machines, it can be much more pronounced.
 *   This turns out to be hard to fix...
 *
 *   Image loading happens in three stages:
 *
 *    1: Fork a process and run xscreensaver-getimage in the background.
 *       This writes image data to a server-side X pixmap.
 *
 *    2: When that completes, a callback informs us that the pixmap is ready.
 *       We must then download the pixmap data from the server with XGetImage
 *       (or XShmGetImage.)
 *
 *    3: Once we have the bits, we must convert them from server-native bitmap
 *       layout to 32 bit RGBA in client-endianness, to make them usable as
 *       OpenGL textures.
 *
 *    4: We must actually construct a texture.
 *
 *   So, the speed of step 1 doesn't really matter, since that happens in
 *   the background.  But steps 2, 3, and 4 happen in *this* process, and
 *   cause the visible glitch.
 *
 *   Step 2 can't be moved to another process without opening a second
 *   connection to the X server, which is pretty heavy-weight.  (That would
 *   be possible, though; the other process could open an X connection,
 *   retrieve the pixmap, and feed it back to us through a pipe or
 *   something.)
 *
 *   Step 3 might be able to be optimized by coding tuned versions of
 *   grab-ximage.c:copy_ximage() for the most common depths and bit orders.
 *   (Or by moving it into the other process along with step 2.)
 *
 *   Step 4 is the hard one, though.  It might be possible to speed up this
 *   step if there is some way to allow two GL processes share texture
 *   data.  Unless, of course, all the time being consumed by step 4 is
 *   because the graphics pipeline is flooded, in which case, that other
 *   process would starve the screen anyway.
 *
 *   Is it possible to use a single GLX context in a multithreaded way?
 *   Or use a second GLX context, but allow the two contexts to share data?
 *   I can't find any documentation about this.
 *
 *   How does Apple do this with their MacOSX slideshow screen saver?
 *   Perhaps it's easier for them because their OpenGL libraries have
 *   thread support at a lower level?
 */
 

Unsatisfying, isn't it? And that with everybodys favourite screensaver...
The latest version of the program seems to be written in february 2005, so maybe it's time for some ultramegasuperdude to rewrite this marvelous thing using some new tricks.
Come on, C-Kids out there, its a chalenge! Amaze us! Pretty please?

---

### Post by djtm on 2007-11-22
Hey,

you may want to check out "Smooth Slide Saver"

[http://web.inf.tu-dresden.de/~cw183155/smoothslidesaver](http://web.inf.tu-dresden.de/~cw183155/smoothslidesaver)
[http://www.kde-apps.org/content/show.php?content=33197](http://www.kde-apps.org/content/show.php?content=33197)

It fixes the problem for me.

Some Problems though:
1. The package does not work under feisty, I had to unpack it and manually install the screensaver by copying the relevant files. This might work with some dpkg override as well.
2. The screensaver relies on some kde libraries.
3. It will probably not show up under xscreensaver/Gnome, but then maybe it will.
4. Sometimes there still is some stuttering.

Good Luck ;)

---

