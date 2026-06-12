---
title: "Are you having issues connecting with an Atheros 5005g card?"
date: 2008-06-19
forum: General Help
---

### Post by drjonze on 2008-06-19
Hello,

I have an Acer Aspire 9300, AMD 64 processor and an Atheros 5005g  card.I'm using Hardy Heron 64bit. When I first installed, I did it through Wubi as I just wanted to check Ubuntu out.  Everything was great but I had no wireless. I kept seeing posts about using madwifi but could not figure it out. I found another post (that I have not been able to find since) that had a  fix that worked for me:

-Connect by wired connection
-disable security on router.
-re-connect wirelessly (I finally could!)
-turn on security again on router 
-re-connect wirelessly

It worked! Problem solved!

Later I actually installed Ubuntu (dual booting with Vista). Just as with the Wubi set up, I had no wireless. I followed the same steps but it did not work. I then tried this:

-disabled atheros driver in 'restricted devices'
-Connected by wired connection
-disabled security on router.
-enabled driver again
-re-connected wirelessly (I could!)
-turned on security again on router 
-re-connected wirelessly

It worked and has ever since. Not sure why this did and perhaps something else was happening behind the scenes on my machine I just didn't know about it. All I know is it worked and that's all I care about!

---

### Post by Slim_Jim on 2009-01-01
Thanks DRJONZE,

I had been fighting for hours with my wireless connexion before I read your thread.  I have a Acer TravelMate with a AR5005G Atheros wireless device and a D-Link range booster wireless router.  I tried with the madwifi ,the ATH5K and the windows wireless drivers but it would not work.  Not for long anyway as it would stop working after reboot.  I finally re-installed the Windows wireless drivers and I followed your instruction and it worked !!!

---

### Post by drjonze on 2009-01-14
> **Slim_Jim said:**
> Thanks DRJONZE,

I had been fighting for hours with my wireless connexion before I read your thread.  I have a Acer TravelMate with a AR5005G Atheros wireless device and a D-Link range booster wireless router.  I tried with the madwifi ,the ATH5K and the windows wireless drivers but it would not work.  Not for long anyway as it would stop working after reboot.  I finally re-installed the Windows wireless drivers and I followed your instruction and it worked !!!

Great!

I still have no idea why this worked but who cares, I'll take it!

As a side note for anyone else, I just installed 8.10 on the same machine (brand new install) and my wireless worked flawlessly 'out of the box'.

---

