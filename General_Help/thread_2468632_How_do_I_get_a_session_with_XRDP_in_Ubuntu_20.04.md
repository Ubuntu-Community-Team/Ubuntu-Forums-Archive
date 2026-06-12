---
title: "How do I get a session with XRDP in Ubuntu 20.04"
date: 2021-11-05
forum: General Help
---

### Post by ski-brimson on 2021-11-05
I was using XFCE4 with an older version of UBUNTU, but it appears this no longer works:

```

Nov 05 21:54:09 jklugDesk kernel: xfsettingsd[249915]: segfault at 21 ip 00007fbc76098420 sp 00007ffdaa979590 error 4 in libX11.so.6.3.0[7fbc76087000+8b000]
Nov 05 21:54:09 jklugDesk kernel: Code: 64 48 8b 04 25 28 00 00 00 48 89 44 24 48 31 c0 48 8d 05 fb 9a 08 00 48 85 f6 4c 0f 44 e0 48 8b 87 68 09 00 00 48 85 c0 74 02 <ff> 10 48 8d 4c 2>
Nov 05 21:54:09 jklugDesk kernel: xfce4-panel[249918]: segfault at e4 ip 00007f959568fa64 sp 00007ffd11d35948 error 4 in libX11.so.6.3.0[7f959567b000+8b000]
Nov 05 21:54:09 jklugDesk kernel: Code: 84 00 00 00 00 00 f3 0f 1e fa 48 63 f6 48 c1 e6 07 48 03 b7 e8 00 00 00 48 8b 46 40 8b 40 34 c3 66 0f 1f 44 00 00 f3 0f 1e fa <8b> 87 e4 00 00 0>
Nov 05 21:54:09 jklugDesk kernel: xfce4-panel[249934]: segfault at e4 ip 00007efc77809a64 sp 00007fffdb9590b8 error 4 in libX11.so.6.3.0[7efc777f5000+8b000]
Nov 05 21:54:09 jklugDesk kernel: Code: 84 00 00 00 00 00 f3 0f 1e fa 48 63 f6 48 c1 e6 07 48 03 b7 e8 00 00 00 48 8b 46 40 8b 40 34 c3 66 0f 1f 44 00 00 f3 0f 1e fa <8b> 87 e4 00 00 0>
Nov 05 21:54:09 jklugDesk kernel: xfdesktop[249944]: segfault at e4 ip 00007fec886b3a64 sp 00007fff8f75d798 error 4 in libX11.so.6.3.0[7fec8869f000+8b000]
Nov 05 21:54:09 jklugDesk kernel: Code: 84 00 00 00 00 00 f3 0f 1e fa 48 63 f6 48 c1 e6 07 48 03 b7 e8 00 00 00 48 8b 46 40 8b 40 34 c3 66 0f 1f 44 00 00 f3 0f 1e fa <8b> 87 e4 00 00 0>
Nov 05 21:54:09 jklugDesk kernel: xfce4-session[249893]: segfault at 0 ip 00007fc97b9e3b7e sp 00007ffc60b37568 error 4 in libc-2.31.so[7fc97b882000+178000]

```

So what should I be using as a Windows manager for xrdp in Ubuntu 20.04?  Or am I setting this up incorrectly?

---

### Post by TheFu on 2021-11-07
xrdp is a poor choice.  So is VNC, for most uses.

x2go is more secure, more convenient, and 2-3x faster.  People who switch say it is like comparing night-to-day for remote connections.

As to which DE?  Anything except Gnome3+.  XFCE4 should be fine with x2go.

However, when connections are on the same LAN, I just use X11 ssh forwarding.  It is very convenient and fast. It isn't like we don't need ssh anyway.

---

### Post by bunny9000 on 2021-11-07
Agree. I discovered x2go several months ago and it has been one of of those 'where has this been all my life' scenarios. 

Just install x2go server on the computer you're connecting to and the client either on linux or windows machines. You can also pull specific applications like the web browser or an installed video editing software.

---

### Post by ActionParsnip on 2021-11-07
What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve? Why use xRDP at all?

---

