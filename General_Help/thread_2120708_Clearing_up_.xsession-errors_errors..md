---
title: "Clearing up .xsession-errors errors."
date: 2013-02-27
forum: General Help
---

### Post by ATLChris on 2013-02-27
I have an xsession-errors file that keeps growing large (90G at one point). I have read countless thread that have instructed how to delete the file via cron every few hours. I am on an SSD and would prefer to clear up the errors so I don't was drive i/o writes on something I don't need.

I tailed the fail and found it is mostly status messages associated with when I connect via VNC. I didn't really see many errors. How can I make this file less active? 

Note, I customized the VNC port to be 5901. I am also using an NVIDA GPU with the latest NVIDIA drivers.

Here is the last few lines of the xsession-errors file:
```

compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
** Message: applet now removed from the notification area
I/O warning : failed to load external entity "/home/***username-removed***/.compiz/session/10d1589466316ef3d3136197524428150500000015980033"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (expo) - Warn: failed to bind image to texture
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
** Message: using fallback from indicator to GtkStatusIcon
27/02/2013 09:27:24 AM Autoprobing TCP port in (all) network interface
27/02/2013 09:27:24 AM Listening IPv6://[::]:5900
27/02/2013 09:27:24 AM Listening IPv4://0.0.0.0:5900
27/02/2013 09:27:24 AM Autoprobing selected port 5900
27/02/2013 09:27:24 AM Advertising security type: 'TLS' (18)
27/02/2013 09:27:24 AM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
27/02/2013 09:27:24 AM Listening IPv6://[::]:5900
27/02/2013 09:27:24 AM Listening IPv4://0.0.0.0:5900
27/02/2013 09:27:24 AM Clearing securityTypes
27/02/2013 09:27:24 AM Advertising security type: 'TLS' (18)
27/02/2013 09:27:24 AM Clearing securityTypes
27/02/2013 09:27:24 AM Advertising security type: 'TLS' (18)
27/02/2013 09:27:24 AM Advertising authentication type: 'No Authentication' (1)
27/02/2013 09:27:24 AM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
27/02/2013 09:27:24 AM Listening IPv6://[::]:5900
27/02/2013 09:27:24 AM Listening IPv4://0.0.0.0:5900
27/02/2013 09:27:24 AM Listening for VNC connections on TCP port 5900 in (all) network interface
27/02/2013 09:27:24 AM Listening IPv6://[::]:5900
27/02/2013 09:27:24 AM Listening IPv4://0.0.0.0:5900
27/02/2013 09:27:24 AM Listening for VNC connections on TCP port 5901 in (all) network interface
27/02/2013 09:27:24 AM Listening IPv6://[::]:5901
27/02/2013 09:27:24 AM Listening IPv4://0.0.0.0:5901
27/02/2013 09:27:24 AM Clearing securityTypes
27/02/2013 09:27:24 AM Clearing authTypes
27/02/2013 09:27:24 AM Advertising security type: 'TLS' (18)
27/02/2013 09:27:24 AM Advertising authentication type: 'VNC Authentication' (2)
27/02/2013 09:27:24 AM Clearing securityTypes
27/02/2013 09:27:24 AM Clearing authTypes
27/02/2013 09:27:24 AM Advertising security type: 'TLS' (18)
27/02/2013 09:27:24 AM Advertising authentication type: 'VNC Authentication' (2)
27/02/2013 09:27:24 AM Advertising security type: 'VNC Authentication' (2)

(vino-server:1880): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(vino-server:1880): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture

(gnome-settings-daemon:1661): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed
** Message: moving back from GtkStatusIcon to indicator

** (gnome-screensaver:2409): WARNING **: screensaver already running in this session
27/02/2013 09:28:13 AM [IPv4] Got connection from client ***client-removed***
27/02/2013 09:28:13 AM   other clients:
27/02/2013 09:28:13 AM Client Protocol Version 3.7
27/02/2013 09:28:13 AM Advertising security type 18
27/02/2013 09:28:13 AM Advertising security type 2
27/02/2013 09:28:13 AM Client returned security type 2
27/02/2013 09:28:13 AM Pixel format for client ***client-removed***:
27/02/2013 09:28:13 AM   16 bpp, depth 15, little endian
27/02/2013 09:28:13 AM   true colour: max r 31 g 31 b 31, shift r 10 g 5 b 0
27/02/2013 09:28:13 AM rfbProcessClientNormalMessage: ignoring unknown encoding type 9
27/02/2013 09:28:13 AM rfbProcessClientNormalMessage: ignoring unknown encoding type -65527
27/02/2013 09:28:13 AM Using compression level 7 for client ***client-removed***
27/02/2013 09:28:13 AM Using image quality level 7 for client ***client-removed***
27/02/2013 09:28:13 AM rfbProcessClientNormalMessage: ignoring unknown encoding type -131072
27/02/2013 09:28:13 AM Enabling NewFBSize protocol extension for client ***client-removed***
27/02/2013 09:28:13 AM Enabling LastRect protocol extension for client ***client-removed***
27/02/2013 09:28:13 AM rfbProcessClientNormalMessage: ignoring unknown encoding type -131071
27/02/2013 09:28:13 AM rfbProcessClientNormalMessage: ignoring unknown encoding type -131070
27/02/2013 09:28:13 AM rfbProcessClientNormalMessage: ignoring unknown encoding type -131069
27/02/2013 09:28:13 AM Enabling cursor position and shape (rich encoding) updates for client ***client-removed***
27/02/2013 09:30:52 AM rfbSendUpdateBuf: write: Broken pipe
27/02/2013 09:30:52 AM Client ***client-removed*** gone
27/02/2013 09:30:52 AM Statistics:
27/02/2013 09:30:52 AM   key events received 0, pointer events 49
27/02/2013 09:30:52 AM   framebuffer updates 12, rectangles 332, bytes 4574461
27/02/2013 09:30:52 AM     LastRect and NewFBSize markers 9, bytes 108
27/02/2013 09:30:52 AM     cursor position updates 6, bytes 72
27/02/2013 09:30:52 AM     tight rectangles 317, bytes 4574281
27/02/2013 09:30:52 AM   raw bytes equivalent 41418138, compression ratio 9.054568
27/02/2013 09:31:05 AM [IPv4] Got connection from client ***client-removed***
27/02/2013 09:31:05 AM   other clients:
27/02/2013 09:31:06 AM Client Protocol Version 3.7
27/02/2013 09:31:06 AM Advertising security type 18
27/02/2013 09:31:06 AM Advertising security type 2
27/02/2013 09:31:06 AM Client returned security type 2
27/02/2013 09:31:06 AM Pixel format for client ***client-removed***:
27/02/2013 09:31:06 AM   16 bpp, depth 15, little endian
27/02/2013 09:31:06 AM   true colour: max r 31 g 31 b 31, shift r 10 g 5 b 0
27/02/2013 09:31:06 AM rfbProcessClientNormalMessage: ignoring unknown encoding type 9
27/02/2013 09:31:06 AM rfbProcessClientNormalMessage: ignoring unknown encoding type -65527
27/02/2013 09:31:06 AM Using compression level 7 for client ***client-removed***
27/02/2013 09:31:06 AM Using image quality level 7 for client ***client-removed***
27/02/2013 09:31:06 AM rfbProcessClientNormalMessage: ignoring unknown encoding type -131072
27/02/2013 09:31:06 AM Enabling NewFBSize protocol extension for client ***client-removed***
27/02/2013 09:31:06 AM Enabling LastRect protocol extension for client ***client-removed***
27/02/2013 09:31:06 AM rfbProcessClientNormalMessage: ignoring unknown encoding type -131071
27/02/2013 09:31:06 AM rfbProcessClientNormalMessage: ignoring unknown encoding type -131070
27/02/2013 09:31:06 AM rfbProcessClientNormalMessage: ignoring unknown encoding type -131069
27/02/2013 09:31:06 AM Enabling cursor position and shape (rich encoding) updates for client ***client-removed***

```

---

### Post by dino99 on 2013-02-27
is it a genuine installation ? (vnc should not log all that stuff)
maybe purge then reinstall vnc.

---

### Post by steeldriver on 2013-02-27
^^^ I see quite a bit of xsession-errors traffic like that from the default vino-server (aka 'Desktop Sharing')

You could try actually looking for repeated messages - I posted this one-liner a couple of days ago for someone in a similar situation:

```
tail -n 100000 ~/.xsession-errors 
| sed -re '/^$/d' -e 's|([0-9]+/?){3} ([0-9]+:?){3} [AP]M||' -e 's|([0-9]+-?){3} ([0-9]+[:,]?){3}[0-9]*||' 
| sort | uniq -c | sort -hr | head -10
```You may need to adjust the tail -n number to get a representative sample of the file

---

### Post by Bobhuber on 2013-02-27
Delete the .xsession-errors file thru nautilus or terminal.
From a terminal in your home directory do the following.

```
touch .xsession-errors
sudo chattr +i .xsession-errors
```The first command creates an empty file. 
The second command changes the file attributes so that it cannot be modified.

---

