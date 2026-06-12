---
title: "Netflix Desktop a bit chuppy"
date: 2012-12-12
forum: General Help
---

### Post by SteveDeFacto on 2012-12-12
If I could make the frame rate more consistent it would be decent. I've tried disabling compositing and turning down video quality through netflix but it did nothing and I don't seem many other ways I can improve performance. I have a Geforce 8800 GT with a duel core x64 bit AMD processor running Xubuntu 12.10. Any thing else I can try to improve the frame rate?

---

### Post by evilsoup on 2012-12-12
I don't think you can do anything more after disabling compositing, and even that actually shouldn't make a difference. Netflix-Desktop uses a customised version of wine with support for SIlverlight 4 - which unfortunately doesn't support putting the video to GPU, so everything is done on the CPU. Hopefully we'll get support for Silverlight 5 (which *does* support video on the GPU) sooner rather than later.

---

