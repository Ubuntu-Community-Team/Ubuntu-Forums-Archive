---
title: "Error in K apps"
date: 2007-09-02
forum: General Help
---

### Post by El Potro on 2007-09-02
Hi everyone!

I'm new at Ubuntu and I have this problem.

When running some K applications I get this error message:

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1232922400 (LWP 25837)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb6658a3b in KAudioManagerPlay::KAudioManagerPlay ()
   from /usr/lib/libartskde.so.1
#7  0xb6715d03 in KNotify::restartedArtsd () from /usr/lib/kde3/knotify.so
#8  0xb671601d in KNotify::KNotify () from /usr/lib/kde3/knotify.so
#9  0xb671685a in kdemain () from /usr/lib/kde3/knotify.so
#10 0x0804e6bf in ?? ()
#11 0x00000001 in ?? ()
#12 0x0807cef0 in ?? ()
#13 0x00000001 in ?? ()
#14 0x00000000 in ?? ()
```

I'm reaaally angry with this!

I'm also getting an arts error, in some other K apps. I think that there's something wrong with my K apps support.

Would you please help me?
How can I fix it?

Thank you a lot!

---

### Post by arpan on 2007-09-02
I'm not sure why this happens but probably a bug in multi-threaded application.  Only thing I can suggest is that you report a bug(along with this error output) to the developers of the application that crashes. This way you can have better K apps in next release or updates.

---

