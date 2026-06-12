---
title: "Issue with game installation"
date: 2008-06-18
forum: General Help
---

### Post by z00s on 2008-06-18
I have a game, which I have installed at least a dozen times now called Thinktanks.  I recently upgraded to Hardy and now when attempting to install, it goes to a text-based installation rather than a GUI installation, detects glibc-2.1, which it definitely shouldn't.  It says it installs OK, however when I attempt to run the application it gives me:

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c74767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7c748b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7ecf1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8c) [0xb7e4776c]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x156) [0xb7e42896]
#5 ./lib/libSDL-1.2.so.0 [0xb7e445a9]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x24e) [0xb7e39a12]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x43) [0xb7e1a9c7]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x21) [0xb7e1aad1]
#9 ./ThinkTanks.bin [0x818896d]
#10 ./ThinkTanks.bin(XOpenDisplay+0x65) [0x804ea91]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c74767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7c7481e]
#2 /usr/lib/libX11.so.6 [0xb7ece518]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb7ec4f70]
#4 ./lib/libSDL-1.2.so.0 [0xb7e42641]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x3cf) [0xb7e42b0f]
#6 ./lib/libSDL-1.2.so.0 [0xb7e445a9]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x24e) [0xb7e39a12]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x43) [0xb7e1a9c7]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x21) [0xb7e1aad1]
#10 ./ThinkTanks.bin [0x818896d]
#11 ./ThinkTanks.bin(XOpenDisplay+0x65) [0x804ea91]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c74767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7c748b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7ecf1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x75) [0xb7e4df05]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x5d4) [0xb7e42d14]
#5 ./lib/libSDL-1.2.so.0 [0xb7e445a9]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x24e) [0xb7e39a12]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x43) [0xb7e1a9c7]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x21) [0xb7e1aad1]
#9 ./ThinkTanks.bin [0x818896d]
#10 ./ThinkTanks.bin(XOpenDisplay+0x65) [0x804ea91]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c74767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7c7481e]
#2 /usr/lib/libX11.so.6 [0xb7ece518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7ea4e76]
#4 ./lib/libSDL-1.2.so.0 [0xb7e446bc]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x24e) [0xb7e39a12]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x43) [0xb7e1a9c7]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x21) [0xb7e1aad1]
#8 ./ThinkTanks.bin [0x818896d]
#9 ./ThinkTanks.bin(XOpenDisplay+0x65) [0x804ea91]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c74767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7c748b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7ecf1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x93) [0xb7e47a33]
#4 ./lib/libSDL-1.2.so.0 [0xb7e408f7]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x34) [0xb7e409a4]
#6 ./lib/libSDL-1.2.so.0 [0xb7e4472a]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x24e) [0xb7e39a12]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x43) [0xb7e1a9c7]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x21) [0xb7e1aad1]
#10 ./ThinkTanks.bin [0x818896d]
#11 ./ThinkTanks.bin(XOpenDisplay+0x65) [0x804ea91]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c74767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7c7481e]
#2 /usr/lib/libX11.so.6 [0xb7ece518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7ec5616]
#4 ./lib/libSDL-1.2.so.0 [0xb7e4411b]
#5 ./lib/libSDL-1.2.so.0 [0xb7e4474c]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x24e) [0xb7e39a12]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x43) [0xb7e1a9c7]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x21) [0xb7e1aad1]
#9 ./ThinkTanks.bin [0x818896d]
#10 ./ThinkTanks.bin(XOpenDisplay+0x65) [0x804ea91]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c74767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7c748b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7ecf1bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8c) [0xb7e4776c]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x67) [0xb7e47b27]
#5 ./lib/libSDL-1.2.so.0 [0xb7e4248b]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x73) [0xb7e43133]
#7 ./lib/libSDL-1.2.so.0 [0xb7e45503]
#8 ./lib/libSDL-1.2.so.0 [0xb7e456cc]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x199) [0xb7e3a269]
#10 ./ThinkTanks.bin [0x8184071]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7c74767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7c7481e]
#2 /usr/lib/libX11.so.6 [0xb7ece518]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb7ea4165]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xe1) [0xb7e431a1]
#5 ./lib/libSDL-1.2.so.0 [0xb7e45503]
#6 ./lib/libSDL-1.2.so.0 [0xb7e456cc]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x199) [0xb7e3a269]
#8 ./ThinkTanks.bin [0x8184071]
ThinkTanks.bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

---

### Post by ibuclaw on 2008-06-19
My first guess would be "Do you have libSDL and libxcb installed?"
```
sudo apt-get install libsdl1.2debian-alsa libx11-6 libxcb-xlib0
```

Regards
Iain

---

