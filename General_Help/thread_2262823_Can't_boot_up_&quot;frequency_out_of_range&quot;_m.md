---
title: "Can't boot up &quot;frequency out of range&quot; message - 12.04"
date: 2015-01-27
forum: General Help
---

### Post by richfaraone on 2015-01-27
Hi,

Even though I have been using Ubuntu for over 6 years now on my desktop, I am a user, not a techie, so please bear with me! :-)

I just got a great deal on some new (old stock) server parts and decided to set it up. 
Board: Intel SE7501BR2 Dual Intel Xeon socket 604 - 2x 3.06GHz processors - 6GB RAM - Ubuntu desktop 12.04 (for testing).

After about an hour and a half of installation (strange) I finally got to the desktop and downloaded all the updates. Everything was running just fine, even after reboots, but when I shut down the server and restart it, I get a message on my monitor that says "frequency out of range" and the monitor goes to sleep - I don't know if it continues to boot or not, I can't tell. I'm using an old Gateway monitor, Native Resolution 1280 x 1024.

So I tried to reinstall from the CD-ROM and that went just fine until I fully shut down the server - same problem happened again. Any help would be greatly appreciated. BTW, I have to use 12.04 because of video chip compatibility.

-Rich

---

### Post by aromo2 on 2015-01-27
That message comes from your monitor.  Either it's not receiving a signal from the video card or the refresh rate on it is not supported by the monitor.  Can you try a known good monitor to determine if the problem is the video card or the monitor?

---

### Post by richfaraone on 2015-01-27
I don't have an extra one. If it were the monitor or video card, why would it work for the install, updates and restarts? It's only on a cold reboot it stops working.

---

