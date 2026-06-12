---
title: "OpenGL Development using ATI card"
date: 2012-12-25
forum: General Help
---

### Post by rollexus on 2012-12-25
Hello Everyone,

Not sure if this is possible but I am currently running Ubuntu:

```

Linux oakville 2.6.32-5-686 #1 SMP Sun Sep 23 09:49:36 UTC 2012 i686 GNU/Linux

```And using the following graphics card

```

03:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary):

```During installation I recall not having ATI driver support for the X1300. I think I am just using the generic driver. Moving forward, I would like to do some OpenGL development using emacs+SLIME+sbcl. That end of the spectrum is all setup however, when running a test app I am getting the following error:

```

;     package "GL" not found

```I do have "libgl1-mesa-dev" installed to no success.

Any help is greatly appreciated.

Thanks in Advance,

Nick,

---

### Post by Mark Phelps on 2012-12-25
Just to confirm, there hasn't been a working AMD Linux driver for that card since AMD dropped support for it years ago.  You are using the default open-source Radeon driver.

---

### Post by rollexus on 2012-12-25
Thank you so much for your response Mark. The question is now, do I need to go out and by and NVIDIA card to be able to work with the OpenGL library? I sure hope not...


PS If I am not mistaken, it should be  a library/classpath issue.

Still Googling,

Nick.

---

### Post by rollexus on 2012-12-25
Update: Just found that I can indeed develop OpenGL applications using an ATI card. Did a quick c++ application where I know how to link the needed library (i.e., gl, glut).
The problem now is to be able to link my original Lisp application.

PS Can someone please shift this topic over to the programming section.

Thanks in Advance,

Nick.

---

