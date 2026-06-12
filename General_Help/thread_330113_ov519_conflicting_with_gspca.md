---
title: "ov519 conflicting with gspca"
date: 2007-01-02
forum: General Help
---

### Post by invalid on 2007-01-02
Hi,

I have a bit of a delima, trying to use multiple usb video cameras at the same time. The situation is this:

I have a webcam which requires the gspca module. If I load it, and enable the camera, it works lovely. I have a second webcam, which requires the ov519 module. If I load it, and enable the camera, it works lovely.

The problem is, when I have both these modules loaded at the same time. The ov519 camera will work lovely, but the gspca camera refuses to work properly.

At one time, a distribution or two ago, the gspca camera was using the spca5xx module, and the ov519 camera was using the ov51x module. As both of these seem to be pushed into the new ones, and won't build properly any longer, I am unable to use them.

Is there a way that I can load both modules without having them conflict?

---

