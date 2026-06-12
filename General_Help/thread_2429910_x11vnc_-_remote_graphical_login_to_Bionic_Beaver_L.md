---
title: "x11vnc - remote graphical login to Bionic Beaver LTS with xubuntu desktop on a Pi3B"
date: 2019-10-24
forum: General Help
---

### Post by makem2 on 2019-10-24
Using this setup:

[https://c-nergy.be/blog/?p=12220](https://c-nergy.be/blog/?p=12220)

At this point I get this error:

```

ubuntu@ubuntu:~$ sudo systemctl status x11vnc.service
&#9679; x11vnc.service - Start x11vnc at startup.
   Loaded: loaded (/lib/systemd/system/x11vnc.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2019-10-24 18:07:43 UTC; 2h 17min ago
 Main PID: 1395 (x11vnc)
    Tasks: 2 (limit: 1051)
   CGroup: /system.slice/x11vnc.service
           &#9500;&#9472;1395 /usr/bin/x11vnc -loop -forever -bg -rfbport 5900 -xkb -noxrecord -noxfix
           &#9492;&#9472;3751 /usr/bin/x11vnc -loop -forever -bg -rfbport 5900 -xkb -noxrecord -noxfix

Oct 24 20:24:51 ubuntu x11vnc[1395]: 24/10/2019 20:24:51 passing arg to libvncserver: -rfb
Oct 24 20:24:51 ubuntu x11vnc[1395]: 24/10/2019 20:24:51 passing arg to libvncserver: 5900
Oct 24 20:24:51 ubuntu x11vnc[1395]: 24/10/2019 20:24:51 passing arg to libvncserver: -rfb
Oct 24 20:24:51 ubuntu x11vnc[1395]: 24/10/2019 20:24:51 passing arg to libvncserver: /etc
Oct 24 20:24:51 ubuntu x11vnc[1395]: 24/10/2019 20:24:51 x11vnc version: 0.9.13 lastmod: 2
Oct 24 20:24:51 ubuntu x11vnc[1395]: 24/10/2019 20:24:51 XOpenDisplay("") failed.
Oct 24 20:24:51 ubuntu x11vnc[1395]: 24/10/2019 20:24:51 Trying again with XAUTHLOCALHOSTN
Oct 24 20:24:51 ubuntu x11vnc[1395]: [21B blob data]
Oct 24 20:24:51 ubuntu x11vnc[1395]: 24/10/2019 20:24:51 *** XOpenDisplay failed. No -disp
Oct 24 20:24:51 ubuntu x11vnc[1395]: 24/10/2019 20:24:51 *** Trying ":0" in 4 seconds.  Pr
ubuntu@ubuntu:~$ 

```

I have the X11 display manager installed on the Pi:

```

ubuntu@ubuntu:~$ dpkg -l | grep xserver-xorg-core
ii  xserver-xorg-core                     2:1.19.6-1ubuntu4.3                  arm64        Xorg X server - core server
ubuntu@ubuntu:~$

```

How can I address the error?

If I run x11vnc -create I can connect using vncviewer 192.168.2.68:0 but with 'No password' warnings.

```

ubuntu@ubuntu:~$ x11vnc -create
###############################################################
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
#@                                                           @#
#@  **  WARNING  **  WARNING  **  WARNING  **  WARNING  **   @#
#@                                                           @#
#@        YOU ARE RUNNING X11VNC WITHOUT A PASSWORD!!        @#
#@                                                           @#
#@  This means anyone with network access to this computer   @#
#@  may be able to view and control your desktop.            @#
#@                                                           @#
#@ >>> If you did not mean to do this Press CTRL-C now!! <<< @#
#@                                                           @#
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
#@                                                           @#
#@  You can create an x11vnc password file by running:       @#
#@                                                           @#
#@       x11vnc -storepasswd password /path/to/passfile      @#
#@  or   x11vnc -storepasswd /path/to/passfile               @#
#@  or   x11vnc -storepasswd                                 @#
#@                                                           @#
#@  (the last one will use ~/.vnc/passwd)                    @#
#@                                                           @#
#@  and then starting x11vnc via:                            @#
#@                                                           @#
#@      x11vnc -rfbauth /path/to/passfile                    @#
#@                                                           @#
#@  an existing ~/.vnc/passwd file from another VNC          @#
#@  application will work fine too.                          @#
#@                                                           @#
#@  You can also use the -passwdfile or -passwd options.     @#
#@  (note -passwd is unsafe if local users are not trusted)  @#
#@                                                           @#
#@  Make sure any -rfbauth and -passwdfile password files    @#
#@  cannot be read by untrusted users.                       @#
#@                                                           @#
#@  Use x11vnc -usepw to automatically use your              @#
#@  ~/.vnc/passwd or ~/.vnc/passwdfile password files.       @#
#@  (and prompt you to create ~/.vnc/passwd if neither       @#
#@  file exists.)  Under -usepw, x11vnc will exit if it      @#
#@  cannot find a password to use.                           @#
#@                                                           @#
#@                                                           @#
#@  Even with a password, the subsequent VNC traffic is      @#
#@  sent in the clear.  Consider tunnelling via ssh(1):      @#
#@                                                           @#
#@    http://www.karlrunge.com/x11vnc/#tunnelling            @#
#@                                                           @#
#@  Or using the x11vnc SSL options: -ssl and -stunnel       @#
#@                                                           @#
#@  Please Read the documention for more info about          @#
#@  passwords, security, and encryption.                     @#
#@                                                           @#
#@    http://www.karlrunge.com/x11vnc/faq.html#faq-passwd    @#
#@                                                           @#
#@  To disable this warning use the -nopw option, or put     @#
#@  'nopw' on a line in your ~/.x11vncrc file.               @#
#@                                                           @#
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
###############################################################
24/10/2019 20:46:01 x11vnc version: 0.9.13 lastmod: 2011-08-10  pid: 4001
24/10/2019 20:46:01 
24/10/2019 20:46:01 wait_for_client: WAIT:cmd=FINDCREATEDISPLAY-Xvfb
24/10/2019 20:46:01 
24/10/2019 20:46:02 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
24/10/2019 20:46:02 
24/10/2019 20:46:02 Autoprobing TCP port 
24/10/2019 20:46:02 Autoprobing selected TCP port 5900
24/10/2019 20:46:02 Autoprobing TCP6 port 
24/10/2019 20:46:02 Autoprobing selected TCP6 port 5900
24/10/2019 20:46:02 listen6: bind: Address already in use
24/10/2019 20:46:02 Not listening on IPv6 interface.
24/10/2019 20:46:02 

The VNC desktop is:      ubuntu:0
PORT=5900
24/10/2019 20:46:56 Got connection from client 192.168.2.33
24/10/2019 20:46:56   other clients:
24/10/2019 20:46:56 Normal socket connection
24/10/2019 20:46:56 incr accepted_client=1 for 192.168.2.33:59166  sock=5
24/10/2019 20:46:56 wait_for_client: got client
24/10/2019 20:46:56 Client Protocol Version 3.8
24/10/2019 20:46:56 Protocol version sent 3.8, using 3.8
24/10/2019 20:46:56 client progressed=1 in 1/6 0.002014 s
24/10/2019 20:46:56 client useCopyRect: 192.168.2.33 0
24/10/2019 20:47:00 client_set_net: 192.168.2.33  3.6613
24/10/2019 20:47:00 wait_for_client: running: env X11VNC_SKIP_DISPLAY=''  /bin/sh /tmp/x11vnc-find_display.VDEVhA

The program "Xvfb" could not be found in PATH and standard locations.
You probably need to install a package that provides the "Xvfb" program.
Without it FINDCREATEDISPLAY mode may not be able to create an X display.

24/10/2019 20:47:05 running: chvt 7 >/dev/null 2>/dev/null &
24/10/2019 20:47:07 Using X display :0
24/10/2019 20:47:07 rootwin: 0x299 reswin: 0x3800001 dpy: 0xd611bd70
24/10/2019 20:47:07 
24/10/2019 20:47:07 ------------------ USEFUL INFORMATION ------------------
24/10/2019 20:47:07 X DAMAGE available on display, using it for polling hints.
24/10/2019 20:47:07   To disable this behavior use: '-noxdamage'
24/10/2019 20:47:07 
24/10/2019 20:47:07   Most compositing window managers like 'compiz' or 'beryl'
24/10/2019 20:47:07   cause X DAMAGE to fail, and so you may not see any screen
24/10/2019 20:47:07   updates via VNC.  Either disable 'compiz' (recommended) or
24/10/2019 20:47:07   supply the x11vnc '-noxdamage' command line option.
24/10/2019 20:47:07 
24/10/2019 20:47:07 Wireframing: -wireframe mode is in effect for window moves.
24/10/2019 20:47:07   If this yields undesired behavior (poor response, painting
24/10/2019 20:47:07   errors, etc) it may be disabled:
24/10/2019 20:47:07    - use '-nowf' to disable wireframing completely.
24/10/2019 20:47:07    - use '-nowcr' to disable the Copy Rectangle after the
24/10/2019 20:47:07      moved window is released in the new position.
24/10/2019 20:47:07   Also see the -help entry for tuning parameters.
24/10/2019 20:47:07   You can press 3 Alt_L's (Left "Alt" key) in a row to 
24/10/2019 20:47:07   repaint the screen, also see the -fixscreen option for
24/10/2019 20:47:07   periodic repaints.
24/10/2019 20:47:07 
24/10/2019 20:47:07 XFIXES available on display, resetting cursor mode
24/10/2019 20:47:07   to: '-cursor most'.
24/10/2019 20:47:07   to disable this behavior use: '-cursor arrow'
24/10/2019 20:47:07   or '-noxfixes'.
24/10/2019 20:47:07 using XFIXES for cursor drawing.
24/10/2019 20:47:07 GrabServer control via XTEST.
24/10/2019 20:47:07 
24/10/2019 20:47:07 Scroll Detection: -scrollcopyrect mode is in effect to
24/10/2019 20:47:07   use RECORD extension to try to detect scrolling windows
24/10/2019 20:47:07   (induced by either user keystroke or mouse input).
24/10/2019 20:47:07   If this yields undesired behavior (poor response, painting
24/10/2019 20:47:07   errors, etc) it may be disabled via: '-noscr'
24/10/2019 20:47:07   Also see the -help entry for tuning parameters.
24/10/2019 20:47:07   You can press 3 Alt_L's (Left "Alt" key) in a row to 
24/10/2019 20:47:07   repaint the screen, also see the -fixscreen option for
24/10/2019 20:47:07   periodic repaints.
24/10/2019 20:47:07 
24/10/2019 20:47:07 XKEYBOARD: number of keysyms per keycode 7 is greater
24/10/2019 20:47:07   than 4 and 51 keysyms are mapped above 4.
24/10/2019 20:47:07   Automatically switching to -xkb mode.
24/10/2019 20:47:07   If this makes the key mapping worse you can
24/10/2019 20:47:07   disable it with the "-noxkb" option.
24/10/2019 20:47:07   Also, remember "-remap DEAD" for accenting characters.
24/10/2019 20:47:07 
24/10/2019 20:47:07 X FBPM extension not supported.
24/10/2019 20:47:07 X display is capable of DPMS.
24/10/2019 20:47:07 --------------------------------------------------------
24/10/2019 20:47:07 
24/10/2019 20:47:07 Default visual ID: 0x21
24/10/2019 20:47:07 Read initial data from X display into framebuffer.
24/10/2019 20:47:07 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/3200
24/10/2019 20:47:07 rfbNewFramebuffer(0xd6109520, 0x0, 800, 480, 8, 1, 4)
24/10/2019 20:47:07 Pixel format for client 192.168.2.33:
24/10/2019 20:47:07   32 bpp, depth 24, little endian
24/10/2019 20:47:07   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
24/10/2019 20:47:07 
24/10/2019 20:47:07 X display :0 is 32bpp depth=24 true color
24/10/2019 20:47:07 
24/10/2019 20:47:07 calling setTranslateFunction()...
24/10/2019 20:47:07 Pixel format for client 192.168.2.33:
24/10/2019 20:47:07   32 bpp, depth 24, little endian
24/10/2019 20:47:07   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
24/10/2019 20:47:07 no translation needed
24/10/2019 20:47:07   done.
24/10/2019 20:47:07 TS_REDIR is empty, restarting...
24/10/2019 20:47:07 
24/10/2019 20:47:07 Xinerama is present and active (e.g. multi-head).
24/10/2019 20:47:07 Xinerama: number of sub-screens: 1
24/10/2019 20:47:07 Xinerama: no blackouts needed (only one sub-screen)
24/10/2019 20:47:07 
24/10/2019 20:47:07 fb read rate: 283 MB/sec
24/10/2019 20:47:07 fast read: reset -wait  ms to: 10
24/10/2019 20:47:07 fast read: reset -defer ms to: 10
24/10/2019 20:47:07 The X server says there are 12 mouse buttons.
24/10/2019 20:47:07 screen setup finished.
24/10/2019 20:47:07 
24/10/2019 20:47:07 WARNING: You are running x11vnc WITHOUT a password.  See
24/10/2019 20:47:07 WARNING: the warning message printed above for more info.
24/10/2019 20:47:07 

The VNC desktop is:      ubuntu:0
PORT=5900

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching

24/10/2019 20:47:07 rfbProcessClientSecurityType: executing handler for type 1
24/10/2019 20:47:07 rfbProcessClientSecurityType: returning securityResult for client rfb version >= 3.8
24/10/2019 20:47:07 client useCopyRect: 192.168.2.33 0
24/10/2019 20:47:07 Battling with something for -norepeat!! (1 resets left)
24/10/2019 20:47:07 Disabled X server key autorepeat.
24/10/2019 20:47:07   to force back on run: 'xset r on' (2 times)
24/10/2019 20:47:07 created   xdamage object: 0x380001d
24/10/2019 20:47:07 Pixel format for client 192.168.2.33:
24/10/2019 20:47:07   32 bpp, depth 24, little endian
24/10/2019 20:47:07   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
24/10/2019 20:47:07 no translation needed
24/10/2019 20:47:07 Using compression level 1 for client 192.168.2.33
24/10/2019 20:47:07 Using image quality level 6 for client 192.168.2.33
24/10/2019 20:47:07 Using JPEG subsampling 0, Q79 for client 192.168.2.33
24/10/2019 20:47:07 Enabling X-style cursor updates for client 192.168.2.33
24/10/2019 20:47:07 Enabling full-color cursor updates for client 192.168.2.33
24/10/2019 20:47:07 Enabling cursor position updates for client 192.168.2.33
24/10/2019 20:47:07 Enabling LastRect protocol extension for client 192.168.2.33
24/10/2019 20:47:07 Using tight encoding for client 192.168.2.33
24/10/2019 20:47:17 created selwin: 0x380001e
24/10/2019 20:47:17 called initialize_xfixes()
24/10/2019 20:48:00 copy_tiles: allocating first_line at size 26
24/10/2019 20:48:07 client_count: 0
24/10/2019 20:48:07 Restored X server key autorepeat to: 1
24/10/2019 20:48:07 viewer exited.
24/10/2019 20:48:07 deleted 25 tile_row polling images.
ubuntu@ubuntu:~$ 


```

---

### Post by makem2 on 2019-10-24
Two errors I found in above:

sudo nano /lib/systemd/system/x11vnc.service

should be:
sudo nano /etc/systemd/system/x11vnc.service

and in this:

Restart-sec=2

should be:

RestartSec=2

---

