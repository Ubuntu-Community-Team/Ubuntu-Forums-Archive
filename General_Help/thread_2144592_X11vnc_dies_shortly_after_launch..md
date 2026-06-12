---
title: "X11vnc dies shortly after launch."
date: 2013-05-12
forum: General Help
---

### Post by Raduk on 2013-05-12
Hi, 
I'm running 12.04 server headless on a remote VPS and I've set up WINE to manage a app I'm trying to run.  
Due to the nature of windows apps, a bit of a gui is needed, so I've installed Xvfb and X11vnc

$ Xvfb :1 -screen 0 800x600x16 &
$ x11vnc -display :1  -bg -forever -rfbauth ~/.vnc/passwd

All good so far...

```
12/05/2013 23:35:15 passing arg to libvncserver: -rfbauth
12/05/2013 23:35:15 passing arg to libvncserver: /home/nexus-user/.vnc/passwd
12/05/2013 23:35:15 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 31255
12/05/2013 23:35:15 Using X display :1
12/05/2013 23:35:15 rootwin: 0xfe reswin: 0xe00001 dpy: 0x917c648
12/05/2013 23:35:15 
12/05/2013 23:35:15 ------------------ USEFUL INFORMATION ------------------
12/05/2013 23:35:15 X DAMAGE available on display, using it for polling hints.
12/05/2013 23:35:15   To disable this behavior use: '-noxdamage'
12/05/2013 23:35:15 
12/05/2013 23:35:15   Most compositing window managers like 'compiz' or 'beryl'
12/05/2013 23:35:15   cause X DAMAGE to fail, and so you may not see any screen
12/05/2013 23:35:15   updates via VNC.  Either disable 'compiz' (recommended) or
12/05/2013 23:35:15   supply the x11vnc '-noxdamage' command line option.
12/05/2013 23:35:15 
12/05/2013 23:35:15 Wireframing: -wireframe mode is in effect for window moves.
12/05/2013 23:35:15   If this yields undesired behavior (poor response, painting
12/05/2013 23:35:15   errors, etc) it may be disabled:
12/05/2013 23:35:15    - use '-nowf' to disable wireframing completely.
12/05/2013 23:35:15    - use '-nowcr' to disable the Copy Rectangle after the
12/05/2013 23:35:15      moved window is released in the new position.
12/05/2013 23:35:15   Also see the -help entry for tuning parameters.
12/05/2013 23:35:15   You can press 3 Alt_L's (Left "Alt" key) in a row to 
12/05/2013 23:35:15   repaint the screen, also see the -fixscreen option for
12/05/2013 23:35:15   periodic repaints.
12/05/2013 23:35:15 
12/05/2013 23:35:15 XFIXES available on display, resetting cursor mode
12/05/2013 23:35:15   to: '-cursor most'.
12/05/2013 23:35:15   to disable this behavior use: '-cursor arrow'
12/05/2013 23:35:15   or '-noxfixes'.
12/05/2013 23:35:15 using XFIXES for cursor drawing.
12/05/2013 23:35:15 GrabServer control via XTEST.
12/05/2013 23:35:15 
12/05/2013 23:35:15 Scroll Detection: -scrollcopyrect mode is in effect to
12/05/2013 23:35:15   use RECORD extension to try to detect scrolling windows
12/05/2013 23:35:15   (induced by either user keystroke or mouse input).
12/05/2013 23:35:15   If this yields undesired behavior (poor response, painting
12/05/2013 23:35:15   errors, etc) it may be disabled via: '-noscr'
12/05/2013 23:35:15   Also see the -help entry for tuning parameters.
12/05/2013 23:35:15   You can press 3 Alt_L's (Left "Alt" key) in a row to 
12/05/2013 23:35:15   repaint the screen, also see the -fixscreen option for
12/05/2013 23:35:15   periodic repaints.
12/05/2013 23:35:15 
12/05/2013 23:35:15 XKEYBOARD: number of keysyms per keycode 7 is greater
12/05/2013 23:35:15   than 4 and 51 keysyms are mapped above 4.
12/05/2013 23:35:15   Automatically switching to -xkb mode.
12/05/2013 23:35:15   If this makes the key mapping worse you can
12/05/2013 23:35:15   disable it with the "-noxkb" option.
12/05/2013 23:35:15   Also, remember "-remap DEAD" for accenting characters.
12/05/2013 23:35:15 
12/05/2013 23:35:15 X FBPM extension not supported.
Xlib:  extension "DPMS" missing on display ":1".
12/05/2013 23:35:15 X display is not capable of DPMS.
12/05/2013 23:35:15 --------------------------------------------------------
12/05/2013 23:35:15 
12/05/2013 23:35:15 Default visual ID: 0x21
12/05/2013 23:35:15 Read initial data from X display into framebuffer.
12/05/2013 23:35:15 initialize_screen: fb_depth/fb_bpp/fb_Bpl 16/16/1600
12/05/2013 23:35:15 
12/05/2013 23:35:15 X display :1 is 16bpp depth=16 true color
12/05/2013 23:35:15 
12/05/2013 23:35:15 Autoprobing TCP port 
12/05/2013 23:35:15 Autoprobing selected port 5901
12/05/2013 23:35:15 Listening also on IPv6 port 5901 (socket 11)
12/05/2013 23:35:15 fb read rate: 1054 MB/sec
12/05/2013 23:35:15 fast read: reset wait  ms to: 10
12/05/2013 23:35:15 fast read: reset defer ms to: 10
12/05/2013 23:35:15 The X server says there are 10 mouse buttons.
12/05/2013 23:35:15 screen setup finished.
12/05/2013 23:35:15 

The VNC desktop is:      neotox:1
PORT=5901

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching

```

$ export DISPLAY=:1   (x11vnc dies anyway, nomatter if I add this command or not)

Now, I am able to connect and move the mouse about, but after about 30 seconds (sometimes a little more, sometimes a little less), the x11vnc process will exit. No more info is generated in the terminal I launched it from.
If I don't connect, its a 50/50 job. Half of the time it will stay running until I connect, then around 30 seconds later x11vnc will die. The other half of the time it will die after about 30 seconds regardless....

Also, when x11vnc dies, the following gets flooded in the ssh session that Xvfb was launched from, I've no idea if its related.

```
5 XSELINUXs still allocated at reset
SCREEN: 0 objects of 88 bytes = 0 total bytes 0 private allocs
DEVICE: 4 objects of 64 bytes = 256 total bytes 0 private allocs
CLIENT: 0 objects of 120 bytes = 0 total bytes 0 private allocs
WINDOW: 0 objects of 24 bytes = 0 total bytes 0 private allocs
PIXMAP: 1 objects of 8 bytes = 8 total bytes 0 private allocs
GC: 0 objects of 44 bytes = 0 total bytes 0 private allocs
CURSOR: 0 objects of 4 bytes = 0 total bytes 0 private allocs
CURSOR_BITS: 0 objects of 4 bytes = 0 total bytes 0 private allocs
DBE_WINDOW: 0 objects of 12 bytes = 0 total bytes 0 private allocs
TOTAL: 5 objects, 264 bytes, 0 allocs
4 DEVICEs still allocated at reset
DEVICE: 4 objects of 64 bytes = 256 total bytes 0 private allocs
CLIENT: 0 objects of 120 bytes = 0 total bytes 0 private allocs
WINDOW: 0 objects of 24 bytes = 0 total bytes 0 private allocs
PIXMAP: 1 objects of 8 bytes = 8 total bytes 0 private allocs
GC: 0 objects of 44 bytes = 0 total bytes 0 private allocs
CURSOR: 0 objects of 4 bytes = 0 total bytes 0 private allocs
CURSOR_BITS: 0 objects of 4 bytes = 0 total bytes 0 private allocs
DBE_WINDOW: 0 objects of 12 bytes = 0 total bytes 0 private allocs
TOTAL: 5 objects, 264 bytes, 0 allocs
1 PIXMAPs still allocated at reset
PIXMAP: 1 objects of 8 bytes = 8 total bytes 0 private allocs
GC: 0 objects of 44 bytes = 0 total bytes 0 private allocs
CURSOR: 0 objects of 4 bytes = 0 total bytes 0 private allocs
CURSOR_BITS: 0 objects of 4 bytes = 0 total bytes 0 private allocs
DBE_WINDOW: 0 objects of 12 bytes = 0 total bytes 0 private allocs
TOTAL: 1 objects, 8 bytes, 0 allocs
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/100dpi/:unscaled, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/75dpi/:unscaled, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/Type1, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/100dpi, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/75dpi, removing from list!
[dix] Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!

```

I'm far from knowledgeable on these things, so if someone can point me the right way to solving this, that would be great :)

---

