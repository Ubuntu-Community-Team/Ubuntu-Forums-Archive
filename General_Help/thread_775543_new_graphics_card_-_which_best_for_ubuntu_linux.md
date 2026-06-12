---
title: "new graphics card - which best for ubuntu linux?"
date: 2008-04-30
forum: General Help
---

### Post by mandz on 2008-04-30
Hi guys,

I hope this hasn't been asked many times before (I couldn't find any in the search) and I'm sure the answer will come with many qualifications but....

My machine has a motherboard with integrated VIA graphics, which, as VIA refuses to support linux, means I do not have 3D graphics and run into other issues. Therefore I'm looking to purchase a cheap AGP graphics card (i have an AGP motherboard - not ready to upgrade yet) so I can enjoy such luxuries as compiz effects, google earth and other things. Question is which manufacturer/ card best supports linux; which drivers are the best? I can get an Nvidia 6200A for fairly cheap but I've heard the Nvidia drivers are a bit rubbish (although I've seen that card work well in ubuntu before). ATi any better? Any others I should look out for?

I'm not looking for anything at all fancy, just something that is cheap and works reliably.

Thanks in advance,

Mike

---

### Post by rubicon on 2008-04-30
For me nVidia GeForce 2 MX 400 works just fine.

I can even get compiz working. Lagging, but still working :) 

However, both nVidia and ATI card require proprietary drivers. It is not something you should really worry about, since Ubuntu provides package nvidia-glx{-old|-new}, which installs appropriate drivers for you. I guess there is something like that for Radeons too.

---

### Post by effenberg0x0 on 2008-04-30
Even though I'll be the first one to tell you to avoid VIA hardware, they seem to be finally responding to the petition: According to their current press releases, all their sources are finally gonna be released. We are all waiting...
They also started a new website exclusively for Linux users at [http://linux.via.com.tw/](http://linux.via.com.tw/) .

This has happened in the last couple of days so by now you'll only find one new driver at this website. Maybe it fits your needs.

---

### Post by ryanhaigh on 2008-04-30
> **rubicon said:**
> For me nVidia GeForce 2 MX 400 works just fine.

I can even get compiz working. Lagging, but still working :) 


Can you post your configuration here or pm me with it, I have a geforce 2 but was told it would not support compiz because it needs the legacy driver. If I can get it going on my brothers system he will be most impressed. Could ypu please post ubuntu version, nvidia driver version, xorg.conf and anything else you could think of/had to modify to use compiz on that card.

As far as advice on a new card Nvidia is definately the way to go. I would probably recommend an FX5X00 series or even 6 series card if you can get them within budget. As for reliability I try to find cards with passive heatsinks, that way not only do you avoid having the whine of the tiny little fan but you dont have to replace the whole card when it fails...i mean if. I still have a casefan close to the card to keep temps low particularly during heavy gaming (Crysis).

---

### Post by Private_Ops on 2008-04-30
Why not just find an old Geforce FX52/5500 or something? Heck IF you COULD find an AGP 6 series that'd be even better.

---

