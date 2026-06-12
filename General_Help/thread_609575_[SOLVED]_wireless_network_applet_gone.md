---
title: "[SOLVED] wireless network applet gone"
date: 2007-11-11
forum: General Help
---

### Post by occhiso on 2007-11-11
Hi,

Ive been using Ubuntu 7.10 and loving it.
I was customizing my menubar panel across the top of my screen, and (stupidly) removed it by accident :P

So, I went through and added the menu bar, clock, quit, etc. all on to get it close to normal, but I cant find the wireless network applet I had by default! I really liked it because I could swap between wireless networks really easily.

The only thing I can add that is similar is the "network monitor" which gives me signal strength, but no swapping facility. I really want it back and cant work it out.

Any help much appreciated,
cheers,

occhiso

---

### Post by adam.tropics on 2007-11-11
<ALT>F2 nm-applet

---

### Post by occhiso on 2007-11-11
Thanks for your quick reply!
I was going to make that command be executed on startup, but then I found out that I had to add the "notification area" to the panel and it fixed everything :)

Thanks, all back to normal \\:D/

---

### Post by adam.tropics on 2007-11-11
> **occhiso said:**
> Thanks for your quick reply!
I was going to make that command be executed on startup, but then I found out that I had to add the "notification area" to the panel and it fixed everything :)

Thanks, all back to normal \\:D/

No worries. You'll find, just so you know, it's already in startup,under the title 'Network Manager'. Also, if you ever need to restart your panel, killall gnome-panel, the applet will not show up. You can then <ALT>F2 nm-applet if you so wish, but it will startup on next login anyhow, so upto you. Anyway, glad you're sorted.

---

