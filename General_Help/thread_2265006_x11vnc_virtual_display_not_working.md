---
title: "x11vnc virtual display not working"
date: 2015-02-11
forum: General Help
---

### Post by amanda11 on 2015-02-11
Hi, 

Not sure if i selected the right forum or where this thread belongs. 

I have x11vnc install and it works as intended when connecting to the real X-server. But when trying to create a virtual display it seems to be working until i try to connect with a vnc client. I enter the password, the client window seems to open up but instantly closes again. 

I know many people recommend other vnc-server for virtual displays, but since i want to be able to use both real x and virtual it seems x11vnc would be the best alternative. (Often use Plex to watch movies, tv shows etc, don't want to have to close that down when connecting to pc from tablet, hence the virtual display).

I have xvfb installed and when i start it i get this:
```
$ x11vnc -create -rfbauth /home/adamantis/.vnc/passwd 
11/02/2015 23:36:22 passing arg to libvncserver: -rfbauth
11/02/2015 23:36:22 passing arg to libvncserver: /home/adamantis/.vnc/passwd
11/02/2015 23:36:22 x11vnc version: 0.9.13 lastmod: 2011-08-10  pid: 3576
11/02/2015 23:36:22 
11/02/2015 23:36:22 wait_for_client: WAIT:cmd=FINDCREATEDISPLAY-Xvfb
11/02/2015 23:36:22 
11/02/2015 23:36:22 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
11/02/2015 23:36:22 
11/02/2015 23:36:22 Autoprobing TCP port 
11/02/2015 23:36:22 Autoprobing selected TCP port 5901
11/02/2015 23:36:22 Autoprobing TCP6 port 
11/02/2015 23:36:22 rfbListenOnTCP6Port: error in bind IPv6 socket: Address already in use
11/02/2015 23:36:22 Autoprobing selected TCP6 port 5901
11/02/2015 23:36:22 listen6: bind: Address already in use
11/02/2015 23:36:22 Not listening on IPv6 interface.
11/02/2015 23:36:22 


The VNC desktop is:      Silverstone:1
PORT=5901
```

So far it appears to be working, but when connecting this happens:

```
******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?


The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:


    x11vnc -ncache 10 ...


One can also add -ncache_cr for smooth 'copyrect' window motion.
More info: http://www.karlrunge.com/x11vnc/faq.html#faq-client-caching


11/02/2015 23:38:20 rfbProcessClientSecurityType: executing handler for type 2
11/02/2015 23:38:20 Battling with something for -norepeat!! (1 resets left)
11/02/2015 23:38:20 Disabled X server key autorepeat.
11/02/2015 23:38:20   to force back on run: 'xset r on' (2 times)
11/02/2015 23:38:20 created   xdamage object: 0x2800040
11/02/2015 23:38:20 Pixel format for client 192.168.1.100:
11/02/2015 23:38:20   8 bpp, depth 8
11/02/2015 23:38:20   true colour: max r 7 g 7 b 3, shift r 0 g 3 b 6
11/02/2015 23:38:20 rfbProcessClientNormalMessage: ignoring unsupported encoding type ultraZip
11/02/2015 23:38:20 Using compression level 9 for client 192.168.1.100
11/02/2015 23:38:20 Using image quality level 0 for client 192.168.1.100
11/02/2015 23:38:20 Using JPEG subsampling 1, Q15 for client 192.168.1.100
11/02/2015 23:38:20 Enabling X-style cursor updates for client 192.168.1.100
11/02/2015 23:38:20 Enabling full-color cursor updates for client 192.168.1.100
11/02/2015 23:38:20 Enabling cursor position updates for client 192.168.1.100
11/02/2015 23:38:20 Enabling KeyboardLedState protocol extension for client 192.168.1.100
11/02/2015 23:38:20 Enabling NewFBSize protocol extension for client 192.168.1.100
11/02/2015 23:38:20 Enabling LastRect protocol extension for client 192.168.1.100
11/02/2015 23:38:20 Enabling SupportedMessages protocol extension for client 192.168.1.100
11/02/2015 23:38:20 Enabling SupportedEncodings protocol extension for client 192.168.1.100
11/02/2015 23:38:20 Enabling ServerIdentity protocol extension for client 192.168.1.100
11/02/2015 23:38:20 Using tight encoding for client 192.168.1.100
11/02/2015 23:38:20 client useCopyRect: 192.168.1.100 -1
11/02/2015 23:38:20 copy_tiles: allocating first_line at size 61
11/02/2015 23:38:20 rfbProcessClientNormalMessage: read: Connection reset by peer
11/02/2015 23:38:20 client_count: 0
11/02/2015 23:38:20 Restored X server key autorepeat to: 1
11/02/2015 23:38:20 viewer exited.
11/02/2015 23:38:20 deleted 60 tile_row polling images.
```

And after that it dies.

If anyone has any tip or suggestions it would be appreciated.

---

### Post by palmlster on 2015-07-15
I had recently a similar issue after upgrading from Ubuntu 12.04 to Ubuntu 14.04.

Solved by reinstalling from sources x11vnc-0.9.13 and libvncserver-LibVNCServer-0.9.8.2.

Hope this helps

Best

---

