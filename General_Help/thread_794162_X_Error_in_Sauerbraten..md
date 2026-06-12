---
title: "X Error in Sauerbraten."
date: 2008-05-14
forum: General Help
---

### Post by ibuclaw on 2008-05-14
Hi all.

My son went to play Sauerbraten today, only to get this X-Error message.
The game is a no-starter.
[PHP]
$ sauerbraten >/dev/null
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  2 (X_GLXRenderLarge)
  Serial number of failed request:  2363
  Current serial number in output stream:  2365
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6bed767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6bed81e]
#2 /usr/lib/libX11.so.6 [0xb7948518]
#3 /usr/lib/libX11.so.6(XESetCloseDisplay+0x31) [0xb792b8d1]
#4 /usr/lib/libGL.so.1 [0xb7d2bb69]
[/PHP]
Seems very curious to me.
As Card is working (Compiz runs very well on it).

Could anyone have a guess at what is happening (or a possible workaround/fix)?

Regards
Iain

---

