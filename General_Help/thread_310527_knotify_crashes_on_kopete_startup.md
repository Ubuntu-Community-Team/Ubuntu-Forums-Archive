---
title: "knotify crashes on kopete startup"
date: 2006-12-01
forum: General Help
---

### Post by konst88 on 2006-12-01
Hello.
I have gnome, running kopete, and when it tries to play a sound on the first time after login, it is opening knotify, and knotify crashes.
If I close kopete and open it again, or run another application which uses sounds from knotify, knotify starts normally after the crash.
It gives me the following backtrace:
```
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1232202064 (LWP 5029)]
[KCrash handler]
#6  0xb67186eb in KAudioManagerPlay (this=0x815c4b0, server=0x8156e48,
    title=@0xb77499b8) at /usr/include/kde/arts/soundserver.h:1787
#7  0xb67aaa13 in KNotify::restartedArtsd (this=0x8153450)
    at /build/buildd/kdelibs-3.5.5/./arts/knotify/knotify.cpp:754
#8  0xb67aad2d in KNotify (this=0x8153450, useArts=true)
    at /build/buildd/kdelibs-3.5.5/./arts/knotify/knotify.cpp:237
#9  0xb67ab56a in kdemain (argc=1, argv=0x8080bc0)
    at /build/buildd/kdelibs-3.5.5/./arts/knotify/knotify.cpp:206
#10 0x0804e4df in launch (argc=1, _name=0x80a5424 "knotify",
    args=0x80a542c "\001", cwd=0x0, envc=1, envs=0x80a543c "",
    reset_env=false, tty=0x0, avoid_loops=false,
    startup_id_str=0x80a5441 "Home;1163785472;467664;4953_TIME4144299245")
    at /build/buildd/kdelibs-3.5.5/./kinit/kinit.cpp:673
#11 0x0804ed6a in handle_launcher_request (sock=9)
    at /build/buildd/kdelibs-3.5.5/./kinit/kinit.cpp:1240
#12 0x0804f118 in handle_requests (waitForPid=0)
    at /build/buildd/kdelibs-3.5.5/./kinit/kinit.cpp:1443
#13 0x080503ac in main (argc=2, argv=0xbf9ee634, envp=0xbf9ee640)
    at /build/buildd/kdelibs-3.5.5/./kinit/kinit.cpp:1909
#14 0xb7cd78cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#15 0x0804b971 in _start () 
```

---

