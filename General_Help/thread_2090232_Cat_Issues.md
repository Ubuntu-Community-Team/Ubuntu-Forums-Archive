---
title: "Cat Issues"
date: 2012-12-01
forum: General Help
---

### Post by lorderico on 2012-12-01
Hello,

I have an oceanserver os4000 compass which I am trying to read via serial, baud 576000, using cat.  The data stream I get periodiclly stops for a few seconds randomly, then it will resume again.  I think all the data while it is suspended is lost beceause there are jumps in my data.  I'm not sure whether the compass or cat is to blame.  Which is more likely?

Thanks,
Eric

---

### Post by dcstar on 2012-12-01
> **lorderico said:**
> Hello,

I have an oceanserver os4000 compass which I am trying to read via serial, baud 576000, using cat.  The data stream I get periodiclly stops for a few seconds randomly, then it will resume again.  I think all the data while it is suspended is lost beceause there are jumps in my data.  I'm not sure whether the compass or cat is to blame.  Which is more likely?

Thanks,
Eric

If you are outputting Binary data to a console then you risk binary patterns that are interpreted as control characters and "freeze" the screen until another pattern unfreezes things (CTRL/S-CTRL/Q for example).

You should only "cat" to a file and possibly use the "tee" function to divert output to a screen if you need that.

You could also be experiencing a buffer overflow where incoming data is lost while a disk write takes priority. Also check the hardware handshake wiring on the serial connection, people generally stuff this sort of thing up.

---

