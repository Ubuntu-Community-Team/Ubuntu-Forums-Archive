---
title: "Beryl problems"
date: 2007-01-20
forum: General Help
---

### Post by kilroy4231 on 2007-01-20
I am running Beryl-core 0.2.0-svn and whenever I start it the borders around my active windows disappear as well as it leaving the terminal where i start beryl on top of all other windows....here is the terminal output after it is started

```
$ beryl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Reloading options
Initiating splash
beryl: unsupported window depth for thumbnail

```

thanks for any help

---

### Post by allwin on 2007-01-20
My experience is that Beryl quit when that happens.  Try reloading the windows manager, right click on the red jewel.  Also try reloading the Windows Decorator, which I believe adds the borders and things.  It's buggy (for me), almost moreso than it's worth in terms of eyecandy, and I've tried it on a box with nVidia and another with ATI.  Try adding beryl properly to the session startup program list on whatever desktop you are using.  That way, it blows up and you get plain old windows upon starting, and then can more controllably turn it back on and not get stuck with unmoveable windows.

---

