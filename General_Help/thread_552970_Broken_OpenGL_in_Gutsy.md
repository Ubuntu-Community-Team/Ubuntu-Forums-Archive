---
title: "Broken OpenGL in Gutsy"
date: 2007-09-17
forum: General Help
---

### Post by ravon on 2007-09-17
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/xorg-server/+bug/60288](https://launchpad.net/ubuntu/+source/xorg-server/+bug/60288) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Has anyone else gotten any OpenGL problems in Gutsy (Intel GMA) after the updates released from sep14 to sep17? _Some_ OpenGL in my program causes X to crash with the following backtrace:

```

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c9561]
1: [0xffffe420]
2: /usr/lib/xorg/modules/extensions//libglx.so [0xb7bdb31c]
3: /usr/lib/xorg/modules/extensions//libglx.so [0xb7bdeb2c]
4: /usr/bin/X [0x815741e]
5: /usr/bin/X(Dispatch+0x1aa) [0x808f45a]
6: /usr/bin/X(main+0x495) [0x8076ee5]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d3f050]
8: /usr/bin/X(FontFileCompleteXLFD+0x1e9) [0x8076221]
```

I can also get it to segfault in a Mesa _swrast[something] function (don't have the backtrace anymore due to yet another xorg crash). There are some similar issues on the bugtracker, but all of them seems to be either ignored or closed prematurely:

[https://launchpad.net/ubuntu/+source/xorg-server/+bug/60288](https://launchpad.net/ubuntu/+source/xorg-server/+bug/60288)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/71913](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/71913)

Edit: I just realized that this one belongs in the development section. Sorry about that :(

---

