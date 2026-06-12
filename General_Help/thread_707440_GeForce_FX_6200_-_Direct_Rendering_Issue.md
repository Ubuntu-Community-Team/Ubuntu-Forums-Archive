---
title: "GeForce FX 6200 - Direct Rendering Issue"
date: 2008-02-25
forum: General Help
---

### Post by fgl82 on 2008-02-25
Hi!

This is my first post, so I hope I can make myself clear.

I recently installed Ubuntu 7.10 (Gutsy Gibbon) and activated Compiz Fusion. When I did this, it prompted me to instal the nvidia propietary drivers which I think are contained in the package nvidia-glx-new.

After this, compiz fusion was up and running, but some applications that use direct rendering (from instance sdlmame) started running very slowly.

I then checked the glxinfo and, to my surprise, direct rendering was disabled (direct rendering = no).

I also noticed a discrepancy between the vendor and the client information. The vendor was SGI and the client was Nvidia.

My question is: Is there a way to enable direct rendering while keeping compiz fusion and the new Nvidia driver?

Thanks in advance

---

### Post by taurus on 2008-02-25
What driver did you use in /etc/X11/xorg.conf?  

```
cat /etc/X11/xorg.conf
```
Also, look in System -> Administration -> Restricted Drivers Manager to be sure the nvidia is enable.  Make sure you reboot.

---

### Post by fgl82 on 2008-02-25
I use the "nvidia"  driver

and the propietary driver is enabled, I checked already.

any more ideas? (and thanks for the quick answer!!!)

---

### Post by taurus on 2008-02-25
Did you reboot your machine?  What happens if you turn off compiz-fusion, do those 3D apps run at all?

---

### Post by fgl82 on 2008-02-25
Yes, of course.

I'm very curious about the discrepancy between the vendor and the client name when running glxinfo...

---

### Post by fgl82 on 2008-02-25
If I turn off compiz fusion, glxinfo keeps saying that direct rendering is disabled.

And the problem are not 3d apps, but sdlmame, which should use direct rendering to run smoothly but is unable to.

---

