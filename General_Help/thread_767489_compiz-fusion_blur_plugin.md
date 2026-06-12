---
title: "compiz-fusion blur plugin"
date: 2008-04-25
forum: General Help
---

### Post by napsy on 2008-04-25
Hello.

I have Ubuntu 8.04 and an Intel GMA X3100 graphics chip. Compiz works but I can't get the blug plugin working. I installed emerald and played with the blur settings in CCSM but nothing worked. Any ideas?

Some say that for blur to work your dravers must support fragment_program. I have this:

$ glxinfo | grep fragment
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,

---

### Post by minisori on 2008-05-02
Same here, it's not working.

---

### Post by cgrenier on 2008-05-16
Blur doesn't work for me either, and hasn't since I first installed Hardy.  Everything else works great.

---

### Post by bittergourd on 2008-06-02
doesnt work on my laptop either.  waiting for a working driver...

---

### Post by Forlong on 2008-06-02
Yep, it's definitely a driver issue.
I have an ATI card and blur works for me on the proprietary fglrx but not on the OS ati/radeon driver (which I otherwise prefer, because Compiz is much smoother with it).

---

### Post by bittergourd on 2008-08-15
does intel 2.4.0 solve this problem?  any luck?
> **Forlong said:**
> Yep, it's definitely a driver issue.
I have an ATI card and blur works for me on the proprietary fglrx but not on the OS ati/radeon driver (which I otherwise prefer, because Compiz is much smoother with it).

---

