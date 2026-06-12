---
title: "kdm crashes randomly"
date: 2008-05-28
forum: General Help
---

### Post by Mystiko on 2008-05-28
I'm using Kubuntu Hardy on an Abit IP35 Pro/Q6600 system.

About once per day, I'm spontaneously logged out - the current session is destroyed (but if there are other persons logged in, their sessions are left intact). 

/var/kdm.log says:

```
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f0f420]
2: /usr/bin/X(ValidateGC+0x25) [0x809b7e5]
3: /usr/bin/X(ProcPolySegment+0x100) [0x808a7b0]
4: /usr/bin/X [0x815075e]
5: /usr/bin/X(Dispatch+0x2cf) [0x808d8df]
6: /usr/bin/X(main+0x48b) [0x807471b]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ca5450]
8: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting
```

I've ran some memtest and encountered no errors. I can't reproduce the problem and I'm not doing anything in particular when it happens. Is there something I can do to troubleshoot this further or should I just file a bug report? I had the same problem previously with Gutsy.

---

