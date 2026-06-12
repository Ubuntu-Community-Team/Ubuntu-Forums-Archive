---
title: "Screen resolution problem"
date: 2008-04-29
forum: General Help
---

### Post by K.Morgan on 2008-04-29
Since upgrading to Hardy i have been having huge problems with blurry fonts, i tried absolutely everything read every forum and every blog on making fonts look less blurry but nothing made any difference.  

Hardy Heron has setup my screen as 1024 x 768 at 75hz which is the maximum resolution available, i then remembered that in Ubuntu 7.10 the Hz was 60 not 70.  Unfortunately Hardy doesn't allow me to change the Hz when the resolution is 1024 x 768, but it does allow me to go to 60Hz in 1024 x 768 resolution ( the next res down).  

So i tried at the lower resolution and this has sorted my fonts issue out, with everything looking sharp and crisp, the problem now though is that everything is too big.  Is there any way of getting 60HZ on my maximum resolution.

Kristian

---

### Post by K.Morgan on 2008-04-30
Ubuntu 8.10 doesn't allow me to keep the new resolution now, every time i start up the computer it reverts to what it thinks are the best settings.

Is there a file somewhere that will allow me to change the refresh rate from 70Hz down to 60Hz, as the resolution is fine but the resolution at 70Hz makes everything blurry, going into sudo displayconfig-gtk the only refresh rate that Ubuntu will give me at my chosen resolution is 70Hz.  I know that 60Hz is possible as that's what i had in 7.10

Kristian

---

### Post by Nunu on 2008-04-30
> **K.Morgan said:**
> Ubuntu 8.10 doesn't allow me to keep the new resolution now, every time i start up the computer it reverts to what it thinks are the best settings.

Is there a file somewhere that will allow me to change the refresh rate from 70Hz down to 60Hz, as the resolution is fine but the resolution at 70Hz makes everything blurry, going into sudo displayconfig-gtk the only refresh rate that Ubuntu will give me at my chosen resolution is 70Hz.  I know that 60Hz is possible as that's what i had in 7.10

Kristian

You could edit the XORG.CONF file but this is risky. What graphics card do you have?

---

### Post by K.Morgan on 2008-04-30
All i know about the graphics card is that it's a Savage4.  I don't have any more details than that.

Kristian

---

