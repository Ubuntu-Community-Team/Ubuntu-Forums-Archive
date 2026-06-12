---
title: "Wine apps won't recognize DirectX drivers"
date: 2007-02-09
forum: General Help
---

### Post by Rippy on 2007-02-09
[http://www.ubuntuforums.org/showthread.php?t=29996&highlight=cedega+cvs](http://www.ubuntuforums.org/showthread.php?t=29996&highlight=cedega+cvs)

I followed that guide to install Wine on my Edgy 6.10. It took a long time to get it working, but I finally finished.

However, I install Starcraft and try to run it, but it says it "failed to initialize the Directx drivers for my card". When I installed wine through automatix, it ran Starcraft at a crappy frame rate, but this doesn't seem to run it at all.

Anywhere I could have gone wrong, to cause this? Any way to fix it?

Thanks!

-Rippy

---

### Post by Rippy on 2007-02-10
Oh, also, I couldn't do the step where he says to install a package "to have OpenGL support", because the package couldn't be found in the repository, and a manual install showed that it had several other dependencies that either weren't found in the repository, or were superceded by different packages.

The package the guide wants you to install is xlibmesa-glu-dev.

Are there any alternatives to that? Or any other way I can get it? Because I have a feeling that's my problem..

---

### Post by Maestro23 on 2007-02-10
You need to enable extra repositories.  Read this link: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Rippy on 2007-02-10
Nope, with all repositories enabled:

```
Package xlibmesa-glu-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xlibmesa-glu-dev has no installation candidate
```

edit: agh, accidentally pressed "reply" to send my edit, have to rewrite it now.

anyway, xlibmesa-glu-dev has 3 dependencies, one of them being xfree86-common. When I try to install that, it says that X11-common replaces it, and apparently I already have X11-common. However, the other dependencies still insist on having xfree86-common, so I'm kind of stuck.

---

### Post by lleberg on 2007-03-02
i'm really stuck in the same seat..

So i'd really like this to be answered..
I soo want my starcraft going.

---

