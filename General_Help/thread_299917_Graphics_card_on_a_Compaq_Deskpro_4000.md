---
title: "Graphics card on a Compaq Deskpro 4000"
date: 2006-11-14
forum: General Help
---

### Post by lemonsCC on 2006-11-14
I posted about this earlier but the thread was probably in the wrong place and since then I have more information...

I am trying to get the graphics card working on a Compaq Deskpro 4000.  The graphics card is possibly: ```
Video driver: Compaq S3 ViRGE/GX Enhanced 64-bit Graphics
```

I did find this [Linux on the Compaq DeskPro 4000]("http://www.dsm.fordham.edu/~moniot/linux-compaq/Xwindows.html") but he used Fedora, and I am installing Ubuntu + IceWM.  The documentation is also at least 4 years old.  So I am not sure how relevant it would be, or what is different between Fedora and Ubuntu + IceWM.

It appears that the driver being used on his box was the **XF86_SVGA** and that produced bad results (the same as I am getting.)  He changed it to the **XF86_S3V** driver and all went well.

Thank you very very much for any help! :mrgreen:

---

