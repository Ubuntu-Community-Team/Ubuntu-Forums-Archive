---
title: "[SOLVED] More trouble with ATI driver"
date: 2008-01-17
forum: General Help
---

### Post by Ozor Mox on 2008-01-17
So I was having problems with 3D acceleration not working very well on my ATI Radeon X800 graphics card, using the driver installed by the restricted drivers manager. It meant that, although a select few 3D games were working fine, most were slow or had corrupted graphics. I just got ET: QW and that wouldn't even start at all. So I tried installing the newest ATI drivers from their site, but that left me unable to login except in safe mode. Trried again using [this  guide](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a). I could login, and the checks said the drivers are installed, but 3D acceleration is much worse than with the respository driver. Uninstalled, and tried again using Envy, exactly the same result even though the script says my card is supported. Even typing in here is very laggy.

Is my card not supported by this driver, or have I done something wrong? Are there any other methods I can use to try and get the latest driver working for 3D stuff?

If not I'm going to have to restore the old driver somehow. I am starting to consider buying a Nvidia card.

---

### Post by iowa on 2008-01-17
Give Envy a try, [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by ugm6hr on 2008-01-17
I am not sure what is causing your problem, and I don't play games on my laptop (ATI Radeon Xpress 1100 card), but this might help:
[http://ubuntuforums.org/showpost.php?p=3950616&postcount=3](http://ubuntuforums.org/showpost.php?p=3950616&postcount=3)

Essentially, I was only concerned with getting Compiz to work properly, but presumably 3D acceleration for games is similar?

The main issue for me was ensuring I uninstalled xserver-xgl (and edited the compiz settings).

---

### Post by Ozor Mox on 2008-01-17
> Give Envy a try, [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I had already installed the drivers using Envy, but I wanted to thank you for your reply.

> I am not sure what is causing your problem, and I don't play games on my laptop (ATI Radeon Xpress 1100 card), but this might help:
[http://ubuntuforums.org/showpost.php...16&postcount=3](http://ubuntuforums.org/showpost.php...16&postcount=3)

Essentially, I was only concerned with getting Compiz to work properly, but presumably 3D acceleration for games is similar?

The main issue for me was ensuring I uninstalled xserver-xgl (and edited the compiz settings).

Oh my god you're a genius! I removed the xserver-xgl package, rebooted, and everything is working perfectly! Please mark this as solved. Now for some 3D gaming!

:guitar:

---

### Post by ugm6hr on 2008-01-17
> **Ozor Mox said:**
> Oh my god you're a genius! I removed the xserver-xgl package, rebooted, and everything is working perfectly! Please mark this as solved. Now for some 3D gaming!


Errmmmm.... You'd be surprised how long it took for me to work out that was the problem on my laptop :lolflag:

PS: You have to mark it as solved - click Thread tools near the top of the page.

---

### Post by Ozor Mox on 2008-01-17
> PS: You have to mark it as solved - click Thread tools near the top of the page.

Done and done :)

---

