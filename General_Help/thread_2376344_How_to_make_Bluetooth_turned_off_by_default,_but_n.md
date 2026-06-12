---
title: "How to make Bluetooth turned off by default, but not disabled?"
date: 2017-11-02
forum: General Help
---

### Post by &amp;KyT$0P# on 2017-11-02
I rarely use Bluetooth, so I would like to turn it off by default.  So I clicked the Bluetooth icon > Turn Bluetooth Off, and it did.  Until the next reboot, when Bluetooth turned itself back on again.

Search indicated I should try disabling the dconf setting [FONT=Courier New]org.blueman.plugins.powermanager.auto-power-on[/FONT].  Unfortunately that has no effect.

All the other info I get from search results looks like either outdated or would completely disable Bluetooth.  I would like to keep Bluetooth support enabled, as I do use Bluetooth sometimes.  I just don't want Bluetooth on all the time when I'm not using it.

How do I turn off Bluetooth by default, such that when I want to use it, I only need go to Bluetooth icon > Turn Bluetooth On ?

---

### Post by TheFu on 2017-11-02
Use rfkill.

---

### Post by &amp;KyT$0P# on 2017-11-02
Thanks TheFu!  I added
```
rfkill block bluetooth
```
to [FONT=Courier New]/etc/rc.local[/FONT] and it looks to do exactly what I want.  Thanks again! :KS

---

