---
title: "Google Earth, has anyone got it to work well?"
date: 2008-07-03
forum: General Help
---

### Post by Apex-jb on 2008-07-03
Has anyone been able to get Google Earth to actually run smoothly in Ubuntu? I have installed it in previous versions of Ubuntu and it was glitchy. Now I installed it in 8.04 and it uses almost all of my CPU and runs extremely slow. It will not even crawl, it will load in a spurt, then freeze for a second, then load a small spurt again. So I tried using it in vmware server, and again, it is painfully slow to the point where it is unusable. Can it be made to run smoothly?

---

### Post by unseend on 2008-07-03
I have 7.10 and works just great! Maybe you have not your Restricted Drivers Manager enabled to accelerate 3d graphics or something. Or your system can't run GEarth.

---

### Post by Apex-jb on 2008-07-03
I had it running fairly well in 7.10 as well. But in 8.04 its a different story. And the only restricted drivers I have are for my wireless driver. Don't have a restricted driver for graphics.

---

### Post by pferpaddy on 2008-07-03
your best bet is to turn off compiz while using it by instslling the fusion-icon its flickery if you dont

---

### Post by qwallis on 2008-07-03
It runs fine for me in 8.04

---

### Post by unseend on 2008-07-04
i think it's what @pferdaddy said. If you don't have compiz though you need to search for the VGA's driver.

---

### Post by Thanh-BKK on 2008-07-04
Hi :)

I'm on Hardy 8.04 with the first release kernel version (.16?), never updated kernel. Nvidia GeForce 7200 GS, restricted driver from repo, Compiz with all the "bells and whistles" enabled.

Google Earth runs smooth, no stuttering at all, on a 1.5M ADSL connection (the connection speed has a lot to do with how Google Earth performs). 

On another computer (ATI x300, NO restricted driver but Compiz nevertheless working fine) it stutters horribly (same internet connection) so it is definitely the (lack of) driver for the graphics card. That one has the latest kernel.

On a third machine i can't get it to work at all - it opens for a second, then disappears. This one, too, has the latest kernel and it, too, has a "driverless" ATI card (PCI on top of it!) so again i blame it on the (lack of) video driver.... can't find one for that machine for some reason, maybe because it's PCI. Also no Compiz or other desktop effects possible on this one.

Best regards.....

Thanh

---

### Post by Plasma_NZ on 2008-07-04
Im running compiz, with many virtual desktops, and a coupla other xsessions - as im pushing 4 monitors..

Installed google-earth - ran sweet, no glitchs, not slow.. Just chews heaps of ram is all i noticed...

I do not use gfx drivers supplied by ubuntu though, i downloaded my drivers direct from NVIDIA

Im also running Ubuntu Hardy 64bit - compiz - and google-earth, no problems..

I'd question which drivers u are running, and what spec's your pc are..

---

### Post by hyper_ch on 2008-07-04
GE runs fine

---

